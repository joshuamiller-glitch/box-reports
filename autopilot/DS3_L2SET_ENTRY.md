# DS3_L2SET_ENTRY - best entry settings per book: finer dip grid, chase, split, dip basis, resting limit, per-session/regime, learned (T-L2-SETTINGS section 1), 2026-10-30
Research only; no live/execution/chart change; UNTOUCHED (label day > 2026-02-06) never read. Prereg `l2vast/ds3/prereg/L2SET_ENTRY_prereg.md` sha256 0e5ea9c72dff2d9ee014e0edb250fdfc6cd5809101eec02933330e9519b2ab6d (DECISIONS.md), cells.csv sha256 7e030bbd035f9c7ca1c380bba0aff6f5ef8a138195f0f6bcc10fe9a7fe59399b, **2,179 cells**; PRE-only selection file autopilot/DS3_L2SET_ENTRY_PREHOLD.md (sha256 of pre_sel.json c6de4933...); one logged look at 2026 / last 6 months / HOLD / X' (out/l2set/entry/looks.jsonl). Own masks capped at 20260206 (not s48score.WINMASK / vs_lib.WINS): **2026 = 20260101..20260206, about 5 real weeks (huge MDE: read it as a sign, not a size)**, last 6 m (L6M) = 20250801..20260206, HOLD = 20250701..20260206, PRE = 20240201..20250630, X' = 20230401..20240131; every frame filtered to label day <= 20260206. Units: Delta $/week vs the market entry on the SAME signals, lot-matched at live lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6, PB DN MV MA 10), MEASURED fills (market = close + 1 tick, limit = touch; stop 1.01, time 0.995, target 1.4/1.5/4.2/4.3 pt, 0.242 pt fee per lot-fill). ST HM WT KB SM PE (and STACK = their sum) go through the EXACT lock engine (sl_lib.run_book BASE spec) for ALL 2,179 cells; PB DN MV MA are trade-level (no engine), ALL = STACK + those four. Every number is followed by its MDE80 in k$ (2.8 SD / sqrt(weeks)).
**SELECTION ON LOOKED DATA, stated on every ranked line:** the user-requested ranking by last 6 months (HOLD tie-break) selects on windows that have already been looked at (this look, DIPENTRY, ADDUW). Rows labelled 'PRE-selected' are the honest out-of-sample rows (chosen on 2024-02..2025-06 only). Rows labelled 'L6M-ranked' are best-in-hindsight and are published as such.
Cadence actually available: gate inputs are mbp-10 1-s table rows (state at the end of each 1-s bin; abs/iceberg/sweep/print/delta are windows of 1-s bins, imbalance/microprice/pulled depth are instantaneous 1-s states) and every decision is evaluated each 1-s print second. **250 ms is not possible at fill resolution:** a 100 ms book table exists but carries 5 levels only (no imb10, no depth-8) and the price path (hi/lo/close for fills and stops) is 1-s; not run.

## 0. Verdict (plain)
* **0 PASS / 0 CANDIDATE** at book or stack level for any family. Best-of-N White reality check over all cells (stack): PRE t 1.90 p 0.77; L6M t 3.64 p 0.11; HOLD t 3.33 p 0.18 (per book: ST .72/.87, HM .91/.88, WT .48/.23, KB .30/.41, SM .23/.28, PE .70/.91 L6M/HOLD). CANDIDATE-RECENT cells on the stack: 612 of 2099 eligible vs 570 expected by chance (sign-flip null, p95 1561): the count is what chance gives.
* **Dip entry alone still loses** (D6-LIVE-like anchor: dip 10, 3 of 8, veto -0.40, basis i): stack PRE -19.1k (29.3k), HOLD -11.2k (53.6k), L6M -14.7k (57.5k), 2026 +46.1k (164.1k). Averaged over 288 matched dip cells: raising N, going strict, or deeper X only makes it worse; the veto does nothing (fires on 0.1-5% of seconds); no single gate or class pair beats an ungated dip; learned gate and walk-forward re-selection are negative (PRE and recent).
* **The one thing that works is not a gate: a SPLIT.** Pooled PRE-selected cell `fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4` (70% at the signal at market as today, 30% on a dip of 3 pt confirmed by 1 of 8 default gates, remainder sized risk-capped to the original stop, stop at the ORIGINAL level, target re-based on the average): stack Delta +19.5k (41.7k) 2026, +13.3k (14.5k) L6M, +11.6k (14.0k) HOLD, +7.6k (11.2k) PRE, +2.8k (8.4k) X' - positive in all five windows, positive in 6/6 engine books in L6M and HOLD. It sits on a broad plateau: all 20 cells with F=0.7 (X 3,5,8,10,15 x N 0-3, no chase) are positive on the stack in all five windows, so neighbours agree, but the gate adds nothing (placebo gates at the same fill rate rank 0.79 PRE / 1.00 HOLD), CI(PRE) includes 0, the best-of-N RC is not significant, and it is cost-fragile (+1 pt per remainder lot-fill removes PRE and X'; HOLD survives to about +2.5 pt). Tier: **CANDIDATE-RECENT** (failed: placebo>=0.95, CI(PRE lo>0), maxDD(engine), RC_p<=0.05). Stack tail HOLD: mean +20.2k vs +8.6k, SD 164.9k vs 162.5k, maxDD 698k vs 696k, worst-20 weeks -1.56M vs -1.78M.
* **Chase** (price runs Y in favour without the dip, or book-confirmed): every chase row is negative in PRE (-3k to -17k/wk) and in HOLD except one (imb-confirmed Y10, +2.6k, MDE 28k); chase-only (never buy a dip) is the worst family (HOLD mostly -20k to -38k/wk, MDE 30-90k); the stop at the ORIGINAL level is ~10k/wk better than the control stop 60 from the fill; the best chase rows are book-confirmed (imb5>=.2 / print>=25 with, Y 8-10), ~0 inside MDE. **Resting limit** instead of market on the confirmation (join best for 5 / 10 s, then market): +2.9k (MDE 3.5k) / +1.9k HOLD vs the same cell at market, positive in L6M, HOLD, PRE and X' (2026 about 0, MDE 7-9k), same fill rate, a few hundredths of a point per fill (touch-fill convention is optimistic). **Dip basis:** (ii) pullback from the running favourable extreme fills with P(target) 0.552 (vs 0.522 all signals) but at a worse price and loses -37.0k/wk HOLD; (iii) either is the best basis (HOLD -2.7k vs -4.9k for (i); PRE -7.6k vs -18.5k), with 30% of its fills coming from (ii) (HOLD).

## 1. SETTINGS TABLE per book and pooled (recent windows first; MDE in parentheses; 2026 = ~5 weeks)
Row types per unit: **CR-best** = best CANDIDATE-RECENT cell (2026 >= 0 and L6M > 0 on the unit's engine/stack delta) ranked by L6M with HOLD tie-break - SELECTED ON LOOKED DATA, best-in-hindsight; **PRE-sel** = chosen on PRE only (honest); **pooled split** = the single plateau cell above applied to every unit (placebo run for STACK only; per-book rows have placebo = not run = fail); **WF-12m** = the walk-forward policy re-fit from the trailing 12 months (what the adaptive variant would run); **D6-LIVE-like** = the entry as on the chart. Tier uses the V2 gates (prereg section 4), never softened.

| unit | row | cell (registered name) | 2026 (~5 wk) $/wk (MDE) | last 6 m | HOLD | PRE | X' | HOLD fills / rate | P(target\|fill) vs all | tier | failed gates |
|--|--|--|--|--|--|--|--|--|--|--|--|
| STACK | CR-best (L6M-ranked, looked) | fam=F1|X=3|b=i|prof=dflt|N=1|veto=v3 | +58.0k (111.6k) | +25.8k (38.4k) | +23.3k (35.1k) | -9.8k (20.1k) | -3.4k (19.6k) | 6746 / 0.92 | 0.508 vs 0.522 | CANDIDATE-RECENT | mean_up, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| STACK | PRE-sel (honest) | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +19.5k (41.7k) | +13.3k (14.5k) | +11.6k (14.0k) | +7.6k (11.2k) | +2.8k (8.4k) | 6749 / 0.92 | 0.574 vs 0.522 | CANDIDATE-RECENT | placebo>=0.95, CI(PRE lo>0), maxDD(engine), RC_p<=0.05 |
| STACK | pooled split cell | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +19.5k (41.7k) | +13.3k (14.5k) | +11.6k (14.0k) | +7.6k (11.2k) | +2.8k (8.4k) | 6749 / 0.92 | 0.574 vs 0.522 | CANDIDATE-RECENT | placebo>=0.95, CI(PRE lo>0), maxDD(engine), RC_p<=0.05 |
| STACK | WF-12m (last re-fit policy) | per-book re-fit, see section 4 | +10.2k (86.2k) | -14.1k (40.6k) | -7.5k (40.3k) | -17.1k (27.8k) | -28.7k (32.9k) (from 2023-07) | | | adaptive | n/a |
| STACK | D6-LIVE-like (on chart) | fam=F1|X=10|b=i|prof=dflt|N=3|veto=v4 | +46.1k (164.1k) | -14.7k (57.5k) | -11.2k (53.6k) | -19.1k (29.3k) | -10.1k (34.1k) | 5278 / 0.72 | 0.451 vs 0.522 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| ALL | CR-best (L6M-ranked, looked) | fam=F5|F=0.7|X=5|N=1|chase=none|veto=v4 | +41.3k (51.8k) | +20.7k (23.0k) | +17.3k (21.7k) | -0.1k (13.2k) | +3.5k (15.0k) | 9575 / 0.89 | 0.597 vs 0.520 | CANDIDATE-RECENT | mean_up, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| ALL | PRE-sel (honest) | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +23.9k (54.9k) | +14.0k (20.2k) | +11.3k (19.3k) | +1.7k (12.5k) | +4.4k (11.5k) | 9990 / 0.92 | 0.569 vs 0.520 | CANDIDATE-RECENT | placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| ALL | pooled split cell | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +23.9k (54.9k) | +14.0k (20.2k) | +11.3k (19.3k) | +1.7k (12.5k) | +4.4k (11.5k) | 9990 / 0.92 | 0.569 vs 0.520 | CANDIDATE-RECENT | placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| ALL | WF-12m (last re-fit policy) | per-book re-fit, see section 4 | -42.3k (112.6k) | -45.4k (66.4k) | -31.0k (64.9k) | -27.9k (43.0k) | -34.7k (53.0k) (from 2023-07) | | | adaptive | n/a |
| ALL | D6-LIVE-like (on chart) | fam=F1|X=10|b=i|prof=dflt|N=3|veto=v4 | -13.0k (151.1k) | -48.1k (79.9k) | -35.3k (79.2k) | -35.5k (45.8k) | -18.8k (44.8k) | 8030 / 0.74 | 0.450 vs 0.520 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| ST | CR-best (L6M-ranked, looked) | fam=F1|X=3|b=i|prof=dflt|N=1|veto=v3 | +13.2k (47.0k) | +9.4k (20.8k) | +9.7k (20.0k) | -5.0k (11.4k) | -8.3k (10.6k) | 1289 / 0.93 | 0.501 vs 0.507 | CANDIDATE-RECENT | mean_up, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| ST | PRE-sel (honest) | fam=F5|F=0.7|X=5|N=0|chase=px5|veto=v4 | -7.4k (18.2k) | +0.9k (8.5k) | +1.5k (7.7k) | +5.1k (6.5k) | -3.5k (6.3k) | 1381 / 1.00 | 0.510 vs 0.507 | DEAD | SPAN2, placebo>=0.95, year_share, neighbours, RC_p<=0.05 |
| ST | pooled split cell | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +10.6k (25.4k) | +2.2k (9.3k) | +1.6k (9.0k) | +3.9k (7.6k) | +0.1k (4.1k) | 1290 / 0.93 | 0.551 vs 0.507 | CANDIDATE-RECENT | placebo>=0.95, CI(PRE lo>0), year_share, RC_p<=0.05 |
| ST | WF-12m (last re-fit policy) | per-book re-fit, see section 4 | -8.4k (54.0k) | -13.3k (24.9k) | -8.2k (22.5k) | -9.8k (15.7k) | -11.1k (23.1k) (from 2023-07) | | | adaptive | n/a |
| ST | D6-LIVE-like (on chart) | fam=F1|X=10|b=i|prof=dflt|N=3|veto=v4 | +0.0k (79.2k) | -17.0k (28.8k) | -13.3k (26.4k) | -5.1k (14.8k) | -5.9k (15.9k) | 1009 / 0.73 | 0.429 vs 0.507 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| HM | CR-best (L6M-ranked, looked) | fam=F2|gate=PRINT50|X=5|b=iii|veto=v4 | +34.8k (47.9k) | +10.1k (26.4k) | +12.0k (25.2k) | -5.2k (16.1k) | -1.8k (18.2k) | 185 / 0.18 | 0.524 vs 0.506 | CANDIDATE-RECENT | mean_up, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| HM | PRE-sel (honest) | fam=F1|X=3|b=iii|prof=dflt|N=4|veto=v3 | -10.2k (38.8k) | -10.0k (16.5k) | -9.8k (14.7k) | +9.4k (13.2k) | -6.3k (16.9k) | 933 / 0.93 | 0.491 vs 0.506 | DEAD | holdout_sign, SPAN2, placebo>=0.95, maxDD(engine), cost, year_share, RC_p<=0.05 |
| HM | pooled split cell | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +6.5k (20.6k) | +3.1k (6.0k) | +3.0k (5.5k) | +1.9k (4.6k) | +1.7k (3.7k) | 932 / 0.92 | 0.549 vs 0.506 | CANDIDATE-RECENT | placebo>=0.95, CI(PRE lo>0), RC_p<=0.05 |
| HM | WF-12m (last re-fit policy) | per-book re-fit, see section 4 | +10.8k (38.7k) | -5.0k (17.7k) | -1.1k (17.6k) | -3.6k (13.5k) | -5.0k (12.6k) (from 2023-07) | | | adaptive | n/a |
| HM | D6-LIVE-like (on chart) | fam=F1|X=10|b=i|prof=dflt|N=3|veto=v4 | +28.6k (54.7k) | +0.9k (19.1k) | +1.1k (18.4k) | -2.5k (14.6k) | -5.4k (16.1k) | 750 / 0.74 | 0.439 vs 0.506 | CANDIDATE-RECENT | mean_up, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| WT | CR-best (L6M-ranked, looked) | fam=F4|X=5|N=3|chase=dlt3|stop=orig|veto=v4 | +9.3k (36.0k) | +8.9k (11.2k) | +8.1k (9.9k) | -0.3k (5.4k) | +0.4k (6.8k) | 1807 / 0.95 | 0.584 vs 0.587 | CANDIDATE-RECENT | mean_up, placebo>=0.95, CI(PRE lo>0), cost, neighbours, RC_p<=0.05 |
| WT | PRE-sel (honest) | fam=F1|X=15|b=iii|prof=dflt|N=2|veto=none | -6.7k (31.6k) | -2.6k (15.4k) | +0.5k (15.4k) | +6.7k (8.4k) | -3.7k (11.3k) | 1299 / 0.69 | 0.532 vs 0.587 | DEAD | SPAN2, placebo>=0.95, cost, year_share, RC_p<=0.05 |
| WT | pooled split cell | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +5.0k (10.9k) | +2.7k (4.7k) | +2.6k (4.2k) | +1.1k (4.7k) | -1.7k (3.2k) | 1686 / 0.89 | 0.670 vs 0.587 | CANDIDATE-RECENT | SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, RC_p<=0.05 |
| WT | WF-12m (last re-fit policy) | per-book re-fit, see section 4 | -3.4k (36.5k) | -6.0k (19.1k) | -2.6k (18.6k) | +1.6k (9.6k) | -2.4k (10.2k) (from 2023-07) | | | adaptive | n/a |
| WT | D6-LIVE-like (on chart) | fam=F1|X=10|b=i|prof=dflt|N=3|veto=v4 | -1.1k (26.9k) | +0.0k (13.0k) | +2.3k (13.1k) | -0.9k (8.2k) | -0.1k (11.9k) | 1150 / 0.61 | 0.509 vs 0.587 | DEAD | mean_up, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| KB | CR-best (L6M-ranked, looked) | fam=F1|X=8|b=ii|M=10|prof=dflt|N=3|veto=v4 | +9.4k (42.2k) | +9.5k (14.4k) | +7.4k (13.9k) | +0.5k (8.4k) | -2.1k (8.5k) | 1063 / 0.77 | 0.520 vs 0.490 | CANDIDATE-RECENT | SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| KB | PRE-sel (honest) | fam=F1|X=5|b=ii|M=10|prof=dflt|N=3|veto=v4 | +14.6k (39.2k) | +8.7k (14.7k) | +6.4k (14.2k) | +2.4k (8.1k) | -2.8k (8.3k) | 1080 / 0.79 | 0.520 vs 0.490 | CANDIDATE-RECENT | SPAN2, placebo>=0.95, CI(PRE lo>0), year_share, RC_p<=0.05 |
| KB | pooled split cell | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +1.1k (4.7k) | +1.5k (5.4k) | +1.1k (5.3k) | -0.9k (2.2k) | +1.0k (3.3k) | 1273 / 0.93 | 0.533 vs 0.490 | CANDIDATE-RECENT | mean_up, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| KB | WF-12m (last re-fit policy) | per-book re-fit, see section 4 | +6.9k (18.8k) | +4.3k (9.9k) | +1.8k (11.5k) | -0.0k (6.0k) | -8.7k (9.8k) (from 2023-07) | | | adaptive | n/a |
| KB | D6-LIVE-like (on chart) | fam=F1|X=10|b=i|prof=dflt|N=3|veto=v4 | +7.2k (35.4k) | +0.2k (11.7k) | +0.7k (11.2k) | -3.5k (8.0k) | -2.1k (9.4k) | 1029 / 0.75 | 0.437 vs 0.490 | CANDIDATE-RECENT | mean_up, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| SM | CR-best (L6M-ranked, looked) | fam=F5|F=0.3|X=10|N=1|chase=none|veto=v4 | +5.7k (16.3k) | +6.7k (7.1k) | +5.7k (6.5k) | -2.4k (4.5k) | -1.0k (4.3k) | 301 / 0.83 | 0.664 vs 0.521 | CANDIDATE-RECENT | mean_up, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| SM | PRE-sel (honest) | fam=F4|X=10|N=1|chase=imb8|stop=orig|veto=v4 | +0.2k (32.1k) | -0.6k (9.2k) | -0.4k (8.3k) | +2.5k (5.2k) | -0.9k (6.0k) | 363 / 1.00 | 0.510 vs 0.521 | DEAD | holdout_sign, SPAN2, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| SM | pooled split cell | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +1.7k (6.8k) | +2.8k (4.3k) | +3.1k (4.2k) | -0.0k (1.5k) | -0.8k (1.3k) | 341 / 0.94 | 0.569 vs 0.521 | CANDIDATE-RECENT | mean_up, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| SM | WF-12m (last re-fit policy) | per-book re-fit, see section 4 | +3.1k (5.8k) | +5.7k (5.5k) | +5.0k (5.5k) | -1.8k (8.0k) | -0.8k (7.1k) (from 2023-07) | | | adaptive | n/a |
| SM | D6-LIVE-like (on chart) | fam=F1|X=10|b=i|prof=dflt|N=3|veto=v4 | +10.8k (29.0k) | +3.7k (9.9k) | +1.2k (9.4k) | -2.9k (5.4k) | -0.2k (6.5k) | 286 / 0.79 | 0.472 vs 0.521 | CANDIDATE-RECENT | mean_up, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| PE | CR-best (L6M-ranked, looked) | fam=F5|F=0.5|X=15|N=2|chase=none|veto=v4 | +17.7k (38.5k) | +8.4k (12.1k) | +5.3k (11.4k) | +1.5k (4.9k) | +3.2k (5.7k) | 1004 / 0.77 | 0.673 vs 0.488 | CANDIDATE-RECENT | placebo>=0.95, CI(PRE lo>0), neighbours, RC_p<=0.05 |
| PE | PRE-sel (honest) | fam=F5|F=0.3|X=10|N=3|chase=px10|veto=v4 | +10.5k (30.9k) | +0.7k (9.8k) | -1.5k (9.3k) | +3.4k (6.8k) | +2.2k (5.9k) | 1272 / 0.97 | 0.498 vs 0.488 | CANDIDATE-RECENT | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| PE | pooled split cell | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | -5.3k (18.3k) | +0.9k (4.9k) | +0.2k (4.5k) | +1.7k (3.0k) | +2.6k (2.9k) | 1227 / 0.94 | 0.528 vs 0.488 | DEAD | placebo>=0.95, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| PE | WF-12m (last re-fit policy) | per-book re-fit, see section 4 | +1.1k (16.7k) | +0.2k (10.3k) | -2.4k (10.5k) | -3.5k (7.1k) | -0.6k (9.2k) (from 2023-07) | | | adaptive | n/a |
| PE | D6-LIVE-like (on chart) | fam=F1|X=10|b=i|prof=dflt|N=3|veto=v4 | +0.7k (21.3k) | -2.5k (11.0k) | -3.3k (10.1k) | -4.1k (6.9k) | +3.5k (7.2k) | 1054 / 0.80 | 0.423 vs 0.488 | DEAD | mean_up, holdout_sign, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| PB | CR-best (L6M-ranked, looked) | fam=F5|F=0.3|X=3|N=0|chase=px10|veto=v4 | +10.0k (16.6k) | +5.6k (9.4k) | +4.8k (8.6k) | -0.3k (5.3k) | +0.4k (5.4k) | 965 / 1.00 | 0.533 vs 0.526 | CANDIDATE-RECENT | mean_up, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| PB | PRE-sel (honest) | fam=F4|X=inf|chase=nextbar|stop=fill | -15.7k (30.6k) | -26.7k (22.9k) | -18.5k (23.1k) | +13.8k (14.9k) | +0.4k (14.3k) | 489 / 0.51 | 0.501 vs 0.526 | DEAD | holdout_sign, placebo>=0.95, cost, year_share, neighbours, RC_p<=0.05 |
| PB | pooled split cell | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +3.6k (11.4k) | +3.4k (7.0k) | +3.0k (6.1k) | -0.5k (2.1k) | +1.5k (4.1k) | 902 / 0.93 | 0.572 vs 0.526 | CANDIDATE-RECENT | mean_up, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| PB | WF-12m (last re-fit policy) | per-book re-fit, see section 4 | -18.6k (56.9k) | -14.5k (22.5k) | -13.9k (21.3k) | +6.7k (15.2k) | -6.2k (7.6k) (from 2023-07) | | | adaptive | n/a |
| PB | D6-LIVE-like (on chart) | fam=F1|X=10|b=i|prof=dflt|N=3|veto=v4 | -20.7k (38.8k) | -24.7k (21.8k) | -20.2k (20.9k) | +2.5k (13.1k) | +0.7k (12.0k) | 737 / 0.76 | 0.436 vs 0.526 | DEAD | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| DN | CR-best (L6M-ranked, looked) | fam=F5|F=0.5|X=15|N=2|chase=none|veto=v4 | +23.9k (39.7k) | +3.2k (15.1k) | +3.4k (13.8k) | -7.1k (7.0k) | -3.4k (8.5k) | 596 / 0.76 | 0.735 vs 0.527 | CANDIDATE-RECENT | mean_up, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| DN | PRE-sel (honest) | fam=F5|F=0.7|X=5|N=1|chase=imb5|veto=v4 | +0.3k (2.5k) | -2.2k (3.1k) | -1.1k (3.6k) | -2.2k (3.6k) | -1.6k (3.2k) | 780 / 1.00 | 0.528 vs 0.527 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| DN | pooled split cell | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +0.8k (9.0k) | -3.1k (2.9k) | -3.2k (2.6k) | -5.1k (2.2k) | -1.3k (2.4k) | 717 / 0.92 | 0.576 vs 0.527 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| DN | WF-12m (last re-fit policy) | per-book re-fit, see section 4 | +0.0k (0.0k) | -1.3k (2.7k) | -1.2k (2.4k) | -8.6k (11.9k) | -4.7k (14.9k) (from 2023-07) | | | adaptive | n/a |
| DN | D6-LIVE-like (on chart) | fam=F1|X=10|b=i|prof=dflt|N=3|veto=v4 | +0.7k (38.4k) | -4.5k (16.0k) | -2.5k (15.0k) | -15.1k (12.5k) | -4.0k (11.8k) | 618 / 0.79 | 0.471 vs 0.527 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| MV | CR-best (L6M-ranked, looked) | fam=F2|gate=PRINT50|X=5|b=iii|veto=v4 | +2.6k (65.2k) | +20.9k (31.1k) | +23.7k (32.9k) | -8.2k (18.5k) | +18.3k (17.9k) | 348 / 0.28 | 0.520 vs 0.497 | CANDIDATE-RECENT | mean_up, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| MV | PRE-sel (honest) | fam=F4|X=5|N=3|chase=px10|stop=orig|veto=v4 | -14.0k (13.9k) | -1.2k (14.9k) | -0.6k (13.3k) | +5.8k (12.2k) | +2.6k (9.6k) | 1210 / 0.97 | 0.485 vs 0.497 | DEAD | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| MV | pooled split cell | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +0.8k (11.9k) | +1.2k (5.1k) | +0.7k (4.6k) | -0.2k (3.9k) | +0.6k (3.7k) | 1186 / 0.95 | 0.529 vs 0.497 | CANDIDATE-RECENT | mean_up, placebo>=0.95, CI(PRE lo>0), cost, neighbours, RC_p<=0.05 |
| MV | WF-12m (last re-fit policy) | per-book re-fit, see section 4 | -24.5k (34.4k) | -8.0k (28.8k) | -6.2k (25.4k) | -7.9k (15.0k) | +8.3k (26.4k) (from 2023-07) | | | adaptive | n/a |
| MV | D6-LIVE-like (on chart) | fam=F1|X=10|b=i|prof=dflt|N=3|veto=v4 | -28.9k (22.5k) | +6.6k (20.4k) | +8.3k (18.8k) | +2.2k (13.1k) | +1.4k (12.1k) | 1028 / 0.82 | 0.446 vs 0.497 | DEAD | placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| MA | CR-best (L6M-ranked, looked) | fam=F5|F=0.3|X=5|N=2|chase=none|veto=v4 | +1.9k (17.4k) | +1.0k (7.9k) | +0.3k (7.3k) | -0.7k (4.6k) | -0.6k (6.1k) | 425 / 0.90 | 0.609 vs 0.530 | CANDIDATE-RECENT | mean_up, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| MA | PRE-sel (honest) | fam=F1|X=15|b=iii|prof=strict|N=2|veto=v3 | -17.9k (27.3k) | -5.7k (14.2k) | -5.2k (12.7k) | +2.8k (10.1k) | +1.2k (9.1k) | 451 / 0.95 | 0.492 vs 0.530 | DEAD | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| MA | pooled split cell | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | -0.8k (13.0k) | -0.8k (3.9k) | -0.9k (3.5k) | -0.1k (2.2k) | +0.8k (3.6k) | 436 / 0.92 | 0.580 vs 0.530 | DEAD | mean_up, holdout_sign, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| MA | WF-12m (last re-fit policy) | per-book re-fit, see section 4 | -9.4k (50.3k) | -7.5k (19.6k) | -2.3k (19.2k) | -1.0k (7.0k) | -3.4k (13.7k) (from 2023-07) | | | adaptive | n/a |
| MA | D6-LIVE-like (on chart) | fam=F1|X=10|b=i|prof=dflt|N=3|veto=v4 | -10.2k (18.5k) | -10.9k (9.8k) | -9.6k (9.5k) | -6.0k (7.9k) | -6.7k (9.4k) | 369 / 0.78 | 0.447 vs 0.530 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |

### 1b. PRE-selected cell per family group (G1 dip grid+single gates+pairs, G4 chase, G5 split, G6 resting limit, G7 learned), every unit

| unit | row | cell (registered name) | 2026 (~5 wk) $/wk (MDE) | last 6 m | HOLD | PRE | X' | HOLD fills / rate | P(target\|fill) vs all | tier | failed gates |
|--|--|--|--|--|--|--|--|--|--|--|--|
| STACK | G1 | fam=F1|X=3|b=iii|prof=dflt|N=4|veto=v3 | -9.8k (138.0k) | -11.5k (47.9k) | -18.2k (45.5k) | +4.2k (26.9k) | -27.5k (32.3k) | 6482 / 0.88 | 0.501 vs 0.522 | DEAD | holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| STACK | G4 | fam=F4|X=10|N=1|chase=2of810|stop=orig|veto=v4 | +11.8k (120.3k) | -6.6k (42.3k) | -7.4k (38.0k) | +7.0k (23.3k) | -10.2k (23.3k) | 7221 / 0.98 | 0.512 vs 0.522 | DEAD | holdout_sign, SPAN2, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| STACK | G5 | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +19.5k (41.7k) | +13.3k (14.5k) | +11.6k (14.0k) | +7.6k (11.2k) | +2.8k (8.4k) | 6749 / 0.92 | 0.574 vs 0.522 | CANDIDATE-RECENT | placebo>=0.95, CI(PRE lo>0), maxDD(engine), RC_p<=0.05 |
| STACK | G6 | fam=F6|X=0|N=1|T=10|veto=v4 | +8.2k (44.1k) | -3.0k (21.6k) | -0.9k (19.1k) | -1.3k (12.0k) | +5.8k (8.9k) | 7136 / 0.97 | 0.516 vs 0.522 | DEAD | mean_up, holdout_sign, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| STACK | G7 | fam=F7|lgb_th=0.0|X=0 | +36.6k (161.3k) | -0.8k (50.6k) | -7.0k (46.8k) | -7.6k (28.1k) | +1.0k (40.7k) | 5406 / 0.74 | 0.473 vs 0.522 | DEAD | mean_up, holdout_sign, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| ALL | G1 | fam=F1|X=5|b=iii|prof=dflt|N=2|veto=none | -34.8k (164.8k) | -19.0k (64.8k) | -16.3k (58.3k) | -3.9k (26.8k) | -8.2k (31.1k) | 10623 / 0.98 | 0.510 vs 0.520 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| ALL | G4 | fam=F4|X=inf|chase=prt3|stop=orig | -71.1k (282.4k) | -37.1k (133.3k) | -15.2k (131.3k) | -3.1k (61.0k) | -27.0k (56.1k) | 5476 / 0.51 | 0.553 vs 0.520 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| ALL | G5 | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | +23.9k (54.9k) | +14.0k (20.2k) | +11.3k (19.3k) | +1.7k (12.5k) | +4.4k (11.5k) | 9990 / 0.92 | 0.569 vs 0.520 | CANDIDATE-RECENT | placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| ALL | G6 | fam=F6|X=0|N=2|T=10|veto=v4 | +7.6k (82.2k) | -10.0k (34.2k) | -4.8k (31.2k) | -12.8k (15.9k) | +0.9k (12.2k) | 10355 / 0.96 | 0.509 vs 0.520 | DEAD | mean_up, holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| ALL | G7 | fam=F7|lgb_th=0.0|X=0 | +29.5k (202.8k) | -13.7k (77.8k) | -16.9k (72.5k) | -25.0k (41.7k) | +15.6k (70.0k) | 8386 / 0.78 | 0.475 vs 0.520 | DEAD | mean_up, holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| ST | G1 | fam=F1|X=0|b=i|prof=loose|N=3|veto=v3 | -3.5k (49.6k) | +2.3k (17.4k) | +3.0k (15.5k) | +1.0k (9.4k) | -1.2k (6.2k) | 1308 / 0.95 | 0.498 vs 0.507 | DEAD | SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| ST | G4 | fam=F4|X=inf|chase=prt5|stop=orig | -3.6k (115.4k) | -11.9k (41.4k) | -8.1k (39.3k) | +2.5k (16.9k) | -13.2k (16.8k) | 676 / 0.49 | 0.546 vs 0.507 | DEAD | holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| ST | G5 | fam=F5|F=0.7|X=5|N=0|chase=px5|veto=v4 | -7.4k (18.2k) | +0.9k (8.5k) | +1.5k (7.7k) | +5.1k (6.5k) | -3.5k (6.3k) | 1381 / 1.00 | 0.510 vs 0.507 | DEAD | SPAN2, placebo>=0.95, year_share, neighbours, RC_p<=0.05 |
| ST | G6 | fam=F6|X=0|N=2|T=10|veto=v4 | -0.2k (46.0k) | +3.0k (14.4k) | +4.2k (12.9k) | +0.6k (9.6k) | -0.2k (5.3k) | 1323 / 0.96 | 0.501 vs 0.507 | DEAD | SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| ST | G7 | fam=F7|lgb_th=0.0|X=0 | -4.5k (86.9k) | -15.7k (27.0k) | -14.5k (24.4k) | -4.1k (13.4k) | -5.3k (17.5k) | 1064 / 0.77 | 0.457 vs 0.507 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| HM | G1 | fam=F1|X=3|b=iii|prof=dflt|N=4|veto=v3 | -10.2k (38.8k) | -10.0k (16.5k) | -9.8k (14.7k) | +9.4k (13.2k) | -6.3k (16.9k) | 933 / 0.93 | 0.491 vs 0.506 | DEAD | holdout_sign, SPAN2, placebo>=0.95, maxDD(engine), cost, year_share, RC_p<=0.05 |
| HM | G4 | fam=F4|X=5|N=2|chase=px20|stop=fill|veto=v4 | +26.0k (30.0k) | +2.2k (16.2k) | +2.6k (16.4k) | +8.0k (13.7k) | -2.0k (11.5k) | 988 / 0.98 | 0.496 vs 0.506 | CANDIDATE-RECENT | SPAN2, placebo>=0.95, CI(PRE lo>0), year_share, neighbours, RC_p<=0.05 |
| HM | G5 | fam=F5|F=0.5|X=15|N=0|chase=imb5|veto=v4 | -3.3k (27.2k) | -2.7k (15.2k) | -1.6k (13.5k) | +3.3k (9.8k) | -2.1k (11.5k) | 1000 / 0.99 | 0.509 vs 0.506 | DEAD | holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, RC_p<=0.05 |
| HM | G6 | fam=F6|X=0|N=1|T=10|veto=v4 | +2.0k (13.7k) | -3.4k (6.2k) | -2.5k (5.6k) | +3.3k (6.1k) | +1.2k (4.7k) | 984 / 0.98 | 0.500 vs 0.506 | DEAD | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| HM | G7 | fam=F7|lgb_th=0.0|X=0 | +20.6k (43.8k) | +2.8k (15.6k) | +2.8k (14.1k) | +1.8k (12.8k) | -0.9k (15.4k) | 767 / 0.76 | 0.456 vs 0.506 | CANDIDATE-RECENT | SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| WT | G1 | fam=F1|X=15|b=iii|prof=dflt|N=2|veto=none | -6.7k (31.6k) | -2.6k (15.4k) | +0.5k (15.4k) | +6.7k (8.4k) | -3.7k (11.3k) | 1299 / 0.69 | 0.532 vs 0.587 | DEAD | SPAN2, placebo>=0.95, cost, year_share, RC_p<=0.05 |
| WT | G4 | fam=F4|X=inf|chase=prt8|stop=orig | -7.8k (33.0k) | -1.0k (14.0k) | +1.6k (14.9k) | +5.9k (9.9k) | -0.7k (10.8k) | 486 / 0.26 | 0.654 vs 0.587 | DEAD | SPAN2, placebo>=0.95, CI(PRE lo>0), year_share, RC_p<=0.05 |
| WT | G5 | fam=F5|F=0.3|X=5|N=0|chase=px20|veto=v4 | +13.8k (30.8k) | +2.6k (10.6k) | +3.7k (9.9k) | +5.0k (7.0k) | +1.8k (7.2k) | 1865 / 0.99 | 0.597 vs 0.587 | CANDIDATE-RECENT | placebo>=0.95, year_share, RC_p<=0.05 |
| WT | G6 | fam=F6|X=5|N=2|T=10|veto=v4 | +4.2k (21.3k) | +3.0k (10.9k) | +4.1k (9.8k) | +3.8k (7.5k) | +1.4k (8.4k) | 1521 / 0.80 | 0.560 vs 0.587 | CANDIDATE-RECENT | placebo>=0.95, CI(PRE lo>0), year_share, neighbours, RC_p<=0.05 |
| WT | G7 | fam=F7|lgb_th=0.0|X=10 | +6.7k (29.5k) | +0.6k (12.3k) | +0.9k (12.3k) | +1.0k (8.5k) | +2.4k (12.8k) | 810 / 0.43 | 0.468 vs 0.587 | CANDIDATE-RECENT | placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| KB | G1 | fam=F1|X=5|b=ii|M=10|prof=dflt|N=3|veto=v4 | +14.6k (39.2k) | +8.7k (14.7k) | +6.4k (14.2k) | +2.4k (8.1k) | -2.8k (8.3k) | 1080 / 0.79 | 0.520 vs 0.490 | CANDIDATE-RECENT | SPAN2, placebo>=0.95, CI(PRE lo>0), year_share, RC_p<=0.05 |
| KB | G4 | fam=F4|X=5|N=3|chase=dlt3|stop=orig|veto=v4 | +8.2k (16.9k) | -0.2k (7.8k) | -1.9k (7.4k) | +1.9k (7.2k) | +0.1k (6.1k) | 1330 / 0.97 | 0.470 vs 0.490 | DEAD | holdout_sign, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, neighbours, RC_p<=0.05 |
| KB | G5 | fam=F5|F=0.3|X=15|N=1|chase=imb10|veto=v4 | +7.5k (13.9k) | +3.5k (7.2k) | +1.8k (6.9k) | +0.9k (6.7k) | +0.1k (6.7k) | 1342 / 0.98 | 0.488 vs 0.490 | CANDIDATE-RECENT | placebo>=0.95, CI(PRE lo>0), year_share, neighbours, RC_p<=0.05 |
| KB | G6 | fam=F6|X=0|N=1|T=5|veto=v4 | +0.3k (2.0k) | -0.4k (4.6k) | -0.0k (4.2k) | -0.9k (3.7k) | +0.5k (1.7k) | 1338 / 0.97 | 0.481 vs 0.490 | DEAD | mean_up, holdout_sign, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| KB | G7 | fam=F7|lgb_th=2.0|X=0 | +6.4k (26.9k) | -0.4k (10.2k) | -2.0k (10.7k) | -3.5k (7.6k) | +2.7k (8.5k) | 970 / 0.71 | 0.431 vs 0.490 | DEAD | mean_up, holdout_sign, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| SM | G1 | fam=F1|X=3|b=iii|M=10|prof=dflt|N=3|veto=v4 | -6.5k (14.7k) | +0.6k (6.2k) | -0.2k (5.6k) | +2.4k (4.0k) | -0.4k (4.6k) | 361 / 0.99 | 0.518 vs 0.521 | DEAD | holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| SM | G4 | fam=F4|X=10|N=1|chase=imb8|stop=orig|veto=v4 | +0.2k (32.1k) | -0.6k (9.2k) | -0.4k (8.3k) | +2.5k (5.2k) | -0.9k (6.0k) | 363 / 1.00 | 0.510 vs 0.521 | DEAD | holdout_sign, SPAN2, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| SM | G5 | fam=F5|F=0.3|X=15|N=2|chase=imb10|veto=v4 | -3.7k (23.0k) | -5.4k (7.2k) | -5.4k (6.4k) | +1.1k (4.7k) | -0.5k (5.0k) | 358 / 0.99 | 0.506 vs 0.521 | DEAD | holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| SM | G6 | fam=F6|X=0|N=2|T=10|veto=v4 | -3.5k (16.0k) | +0.3k (5.0k) | +1.1k (4.9k) | -0.4k (3.2k) | -0.7k (2.7k) | 353 / 0.97 | 0.516 vs 0.521 | DEAD | mean_up, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| SM | G7 | fam=F7|lgb_th=0.0|X=0 | +6.2k (26.4k) | +5.0k (8.3k) | +1.9k (9.0k) | +0.7k (4.9k) | -1.0k (7.8k) | 289 / 0.80 | 0.478 vs 0.521 | CANDIDATE-RECENT | SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| PE | G1 | fam=F1|X=5|b=ii|prof=dflt|N=4|veto=v3 | -15.0k (20.1k) | +0.4k (12.4k) | -5.5k (13.9k) | +1.9k (9.6k) | -1.7k (9.8k) | 885 / 0.68 | 0.520 vs 0.488 | DEAD | holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| PE | G4 | fam=F4|X=10|N=2|chase=2of810|stop=orig|veto=v4 | +9.1k (33.2k) | -4.2k (9.7k) | -6.6k (9.3k) | +3.2k (7.2k) | +3.8k (6.7k) | 1289 / 0.98 | 0.466 vs 0.488 | DEAD | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| PE | G5 | fam=F5|F=0.3|X=10|N=3|chase=px10|veto=v4 | +10.5k (30.9k) | +0.7k (9.8k) | -1.5k (9.3k) | +3.4k (6.8k) | +2.2k (5.9k) | 1272 / 0.97 | 0.498 vs 0.488 | CANDIDATE-RECENT | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| PE | G6 | fam=F6|X=0|N=1|T=10|veto=v4 | +0.9k (16.3k) | -0.2k (6.2k) | -0.2k (5.4k) | -1.2k (3.6k) | +1.6k (3.6k) | 1286 / 0.98 | 0.484 vs 0.488 | DEAD | mean_up, holdout_sign, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| PE | G7 | fam=F7|lgb_th=0.0|X=0 | +9.1k (29.8k) | +3.9k (10.4k) | +2.0k (10.3k) | -2.6k (7.8k) | +3.7k (9.0k) | 1095 / 0.84 | 0.450 vs 0.488 | CANDIDATE-RECENT | mean_up, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| PB | G1 | fam=F2|gate=ABS3|X=10|b=i|veto=none | -18.9k (72.2k) | -28.8k (35.9k) | -20.2k (34.9k) | +9.4k (21.9k) | -3.4k (15.0k) | 35 / 0.04 | 0.286 vs 0.526 | DEAD | holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| PB | G4 | fam=F4|X=inf|chase=nextbar|stop=fill | -15.7k (30.6k) | -26.7k (22.9k) | -18.5k (23.1k) | +13.8k (14.9k) | +0.4k (14.3k) | 489 / 0.51 | 0.501 vs 0.526 | DEAD | holdout_sign, placebo>=0.95, cost, year_share, neighbours, RC_p<=0.05 |
| PB | G5 | fam=F5|F=0.5|X=8|N=1|chase=none|veto=v4 | -6.9k (17.5k) | -4.2k (11.6k) | -3.0k (10.7k) | +2.5k (6.5k) | +1.2k (8.0k) | 820 / 0.85 | 0.639 vs 0.526 | DEAD | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| PB | G6 | fam=F6|X=10|N=1|T=5|veto=v4 | -9.7k (42.9k) | -18.9k (19.8k) | -16.2k (18.2k) | +5.1k (12.3k) | +1.5k (12.9k) | 782 / 0.81 | 0.458 vs 0.526 | DEAD | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| PB | G7 | fam=F7|lgb_th=2.0|X=10 | -15.6k (73.4k) | -23.9k (25.3k) | -18.9k (24.1k) | +6.2k (15.4k) | -4.2k (15.5k) | 666 / 0.69 | 0.422 vs 0.526 | DEAD | holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| DN | G1 | fam=F2|gate=IMBF20|X=5|b=iii|veto=v4 | -40.5k (57.4k) | -22.3k (17.4k) | -17.7k (16.7k) | -5.5k (8.8k) | -1.0k (9.1k) | 774 / 0.99 | 0.494 vs 0.527 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| DN | G4 | fam=F4|X=5|N=2|chase=px20|stop=fill|veto=v4 | -7.6k (49.2k) | -13.2k (14.1k) | -9.0k (13.8k) | -2.5k (10.9k) | -4.9k (12.3k) | 771 / 0.99 | 0.508 vs 0.527 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| DN | G5 | fam=F5|F=0.7|X=5|N=1|chase=imb5|veto=v4 | +0.3k (2.5k) | -2.2k (3.1k) | -1.1k (3.6k) | -2.2k (3.6k) | -1.6k (3.2k) | 780 / 1.00 | 0.528 vs 0.527 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| DN | G6 | fam=F6|X=0|N=1|T=5|veto=v4 | -4.4k (14.7k) | -6.2k (6.1k) | -5.2k (6.2k) | -9.8k (5.8k) | -2.2k (3.0k) | 758 / 0.97 | 0.513 vs 0.527 | DEAD | mean_up, holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| DN | G7 | fam=F7|lgb_th=1.0|X=5 | -20.5k (32.9k) | -15.0k (16.9k) | -11.9k (16.5k) | -12.4k (11.7k) | +0.9k (16.8k) | 552 / 0.71 | 0.422 vs 0.527 | DEAD | mean_up, holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| MV | G1 | fam=F1|X=3|b=iii|prof=strict|N=1|veto=v3 | -10.3k (29.0k) | -6.1k (18.2k) | -5.3k (16.1k) | +5.4k (10.2k) | -2.8k (11.1k) | 1250 / 1.00 | 0.490 vs 0.497 | DEAD | holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, neighbours, RC_p<=0.05 |
| MV | G4 | fam=F4|X=5|N=3|chase=px10|stop=orig|veto=v4 | -14.0k (13.9k) | -1.2k (14.9k) | -0.6k (13.3k) | +5.8k (12.2k) | +2.6k (9.6k) | 1210 / 0.97 | 0.485 vs 0.497 | DEAD | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, RC_p<=0.05 |
| MV | G5 | fam=F5|F=0.3|X=3|N=0|chase=px20|veto=v4 | -4.1k (14.2k) | -1.1k (11.8k) | -1.7k (10.5k) | +3.9k (7.5k) | -2.3k (7.8k) | 1251 / 1.00 | 0.491 vs 0.497 | DEAD | holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), maxDD(engine), cost, year_share, RC_p<=0.05 |
| MV | G6 | fam=F6|X=10|N=3|T=10|veto=v4 | -18.1k (33.3k) | +7.5k (19.3k) | +9.2k (17.9k) | +3.2k (12.8k) | +1.6k (12.7k) | 1028 / 0.82 | 0.446 vs 0.497 | DEAD | placebo>=0.95, CI(PRE lo>0), year_share, neighbours, RC_p<=0.05 |
| MV | G7 | fam=F7|lgb_th=0.0|X=0 | +11.6k (31.5k) | +11.5k (17.7k) | +10.3k (16.1k) | +1.4k (8.8k) | +14.3k (20.6k) | 1136 / 0.91 | 0.477 vs 0.497 | CANDIDATE-RECENT | CI(PRE lo>0), cost, neighbours, RC_p<=0.05 |
| MA | G1 | fam=F1|X=15|b=iii|prof=strict|N=2|veto=v3 | -17.9k (27.3k) | -5.7k (14.2k) | -5.2k (12.7k) | +2.8k (10.1k) | +1.2k (9.1k) | 451 / 0.95 | 0.492 vs 0.530 | DEAD | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| MA | G4 | fam=F4|X=5|N=2|chase=nextbar|stop=orig|veto=v4 | +3.2k (34.0k) | -4.3k (10.4k) | -4.5k (9.3k) | +1.2k (5.8k) | -1.8k (5.3k) | 465 / 0.98 | 0.516 vs 0.530 | DEAD | holdout_sign, SPAN2, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| MA | G5 | fam=F5|F=0.5|X=3|N=2|chase=px20|veto=v4 | +1.1k (13.5k) | -1.2k (5.8k) | -1.1k (5.1k) | +0.9k (3.2k) | +0.4k (3.5k) | 471 / 0.99 | 0.531 vs 0.530 | DEAD | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, neighbours, RC_p<=0.05 |
| MA | G6 | fam=F6|X=0|N=3|T=10|veto=v4 | -7.2k (31.0k) | -3.1k (8.7k) | -3.4k (7.7k) | +0.8k (5.9k) | +2.0k (5.9k) | 440 / 0.93 | 0.505 vs 0.530 | DEAD | holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |
| MA | G7 | fam=F7|lgb_th=1.0|X=0 | -5.8k (29.1k) | -3.7k (10.1k) | -4.2k (9.0k) | -1.4k (6.4k) | +0.8k (12.8k) | 423 / 0.89 | 0.494 vs 0.530 | DEAD | mean_up, holdout_sign, placebo>=0.95, CI(PRE lo>0), cost, year_share, neighbours, RC_p<=0.05 |

### 1c. Top 12 stack cells by L6M (HOLD tie-break) - SELECTED ON LOOKED DATA; stack Delta $/wk, exact lock engine

| cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| fam=F1|X=3|b=i|prof=dflt|N=1|veto=v3 | +58.0k (111.6k) | +25.8k (38.4k) | +23.3k (35.1k) | -9.8k (20.1k) | -3.4k (19.6k) |
| fam=F1|X=3|b=i|prof=dflt|N=1|veto=v4 | +58.1k (112.1k) | +25.0k (38.8k) | +22.6k (35.4k) | -10.2k (20.4k) | -3.4k (19.6k) |
| fam=F1|X=3|b=i|prof=dflt|N=1|veto=v6 | +58.1k (112.1k) | +25.0k (38.7k) | +22.5k (35.4k) | -10.1k (20.3k) | -3.4k (19.6k) |
| fam=F1|X=3|b=i|prof=dflt|N=1|veto=none | +58.1k (112.1k) | +25.0k (38.7k) | +22.5k (35.4k) | -9.9k (20.3k) | -3.4k (19.6k) |
| fam=F2|gate=MICRO10|X=3|b=i|veto=v4 | +55.4k (135.0k) | +24.1k (42.4k) | +21.1k (38.3k) | -12.1k (20.4k) | -3.4k (19.6k) |
| fam=F2|gate=MICRO10|X=3|b=i|veto=none | +55.4k (135.0k) | +24.1k (42.4k) | +21.1k (38.3k) | -11.8k (20.4k) | -3.4k (19.6k) |
| fam=F1|X=3|b=i|prof=loose|N=1|veto=v3 | +60.3k (117.5k) | +23.1k (37.3k) | +20.9k (34.1k) | -6.9k (19.6k) | -2.8k (18.7k) |
| fam=F5|F=0.7|X=8|N=1|chase=none|veto=v4 | +48.4k (45.9k) | +23.0k (21.0k) | +19.0k (19.6k) | +2.5k (14.2k) | +4.4k (14.7k) |
| fam=F5|F=0.7|X=8|N=0|chase=none|veto=v4 | +42.7k (42.7k) | +22.7k (19.8k) | +18.7k (18.6k) | +2.7k (14.9k) | +3.7k (14.3k) |
| fam=F2|gate=IMBF10|X=3|b=i|veto=v4 | +60.9k (133.8k) | +22.7k (43.0k) | +19.7k (39.3k) | -8.9k (19.4k) | -6.2k (22.0k) |
| fam=F2|gate=IMBF10|X=3|b=i|veto=none | +60.9k (133.8k) | +22.7k (43.0k) | +19.7k (39.3k) | -8.9k (19.4k) | -6.2k (22.0k) |
| fam=F1|X=3|b=i|prof=loose|N=1|veto=v4 | +60.4k (118.0k) | +22.2k (37.5k) | +20.2k (34.3k) | -6.9k (19.6k) | -2.8k (18.7k) |

Best cell per family on the stack by L6M (looked data):

| family | cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| F1 | fam=F1|X=3|b=i|prof=dflt|N=1|veto=v3 | +58.0k (111.6k) | +25.8k (38.4k) | +23.3k (35.1k) | -9.8k (20.1k) | -3.4k (19.6k) |
| F2 | fam=F2|gate=MICRO10|X=3|b=i|veto=v4 | +55.4k (135.0k) | +24.1k (42.4k) | +21.1k (38.3k) | -12.1k (20.4k) | -3.4k (19.6k) |
| F3 | fam=F3|pair=PULL+MICRO|X=0|prof=dflt|veto=v4 | +12.4k (118.2k) | +11.1k (33.5k) | +11.9k (29.7k) | -13.9k (15.7k) | +2.9k (14.5k) |
| F4 | fam=F4|X=5|N=1|chase=px20|stop=orig|veto=v4 | +19.4k (89.9k) | +8.1k (39.7k) | +4.3k (35.3k) | -2.6k (22.2k) | -2.7k (27.9k) |
| F5 | fam=F5|F=0.7|X=8|N=1|chase=none|veto=v4 | +48.4k (45.9k) | +23.0k (21.0k) | +19.0k (19.6k) | +2.5k (14.2k) | +4.4k (14.7k) |
| F6 | fam=F6|X=0|N=2|T=5|veto=v4 | +18.8k (75.8k) | +10.2k (26.7k) | +11.4k (23.9k) | -5.2k (13.0k) | -0.0k (11.1k) |
| F7 | fam=F7|lgb_th=2.0|X=0 | +53.7k (178.7k) | +6.7k (53.5k) | +0.0k (49.7k) | -16.4k (32.9k) | +0.1k (41.2k) |

Cells positive on the stack in ALL of 2026, L6M, HOLD, PRE: 50 (sign-flip null mean 110, p95 545); by family {'F1': 9, 'F2': 2, 'F3': 0, 'F4': 3, 'F5': 36, 'F6': 0, 'F7': 0} - 36 of them are splits.

## 2. (a) finer settings grid, (d') dip basis - averages over matched cells, stack Delta $/wk (MDE of the average)

**Dip X (basis i, all gated cells, averaged over N/profile/veto):** (X=0 is 'first confirmation after the signal')

| X | 2026 | L6M | HOLD | PRE |
|--|--|--|--|--|
| 0 | +17.0k (77.2k) | +0.1k (24.3k) | +1.5k (21.8k) | -12.5k (10.2k) |
| 2 | +39.9k (103.5k) | +6.8k (35.9k) | +4.9k (33.1k) | -14.5k (18.4k) |
| 3 | +44.9k (113.4k) | +8.8k (40.9k) | +8.4k (37.5k) | -15.8k (19.8k) |
| 5 | +41.1k (107.3k) | -2.1k (44.5k) | -1.5k (41.0k) | -15.9k (22.1k) |
| 8 | +37.9k (132.2k) | -13.1k (51.4k) | -11.7k (48.0k) | -19.6k (25.5k) |
| 10 | +44.5k (133.7k) | -16.3k (52.7k) | -13.2k (50.6k) | -18.1k (28.0k) |
| 15 | +35.0k (127.7k) | -20.1k (55.5k) | -16.2k (56.1k) | -27.3k (31.3k) |

**Confirmations N of 8 (basis i, X>0):**

| N | 2026 | L6M | HOLD | PRE |
|--|--|--|--|--|
| 1 | +42.2k (100.6k) | -2.0k (40.7k) | -1.8k (37.6k) | -12.1k (21.2k) |
| 2 | +40.7k (115.1k) | -4.9k (44.4k) | -4.3k (40.8k) | -15.6k (21.7k) |
| 3 | +44.0k (122.4k) | -6.0k (47.3k) | -5.2k (43.9k) | -20.2k (24.0k) |
| 4 | +35.3k (140.8k) | -11.1k (51.7k) | -8.2k (51.2k) | -26.3k (26.9k) |

**Threshold profile (basis i):** loose: HOLD -4.0k (41.7k), PRE -15.7k (21.9k); default: HOLD -5.0k (41.9k), PRE -17.3k (22.6k); strict: HOLD -5.6k (44.8k), PRE -22.6k (24.3k)

**Veto imb5 sided:** none: HOLD -4.9k (42.6k), PRE -18.6k (22.7k); <=-0.30: HOLD -4.9k (42.6k), PRE -18.4k (22.7k); <=-0.40: HOLD -4.9k (42.6k), PRE -18.5k (22.7k); <=-0.60: HOLD -4.9k (42.6k), PRE -18.5k (22.7k) -> the veto changes nothing (it fires on 0.1-5% of seconds).

**Ungated dip (N=0, basis i) for comparison - stack Delta (2026 / L6M / HOLD / PRE / X' in k$/wk):** X=0 +1.6/-2.7/-0.4/-6.4/-0.3; X=2 +32.6/+4.6/+2.3/-6.7/-9.2; X=3 +33.9/+13.3/+12.8/-7.5/-3.5; X=5 +32.9/+6.3/+6.6/-9.7/+1.6; X=8 +38.7/-8.4/-7.3/-15.1/-5.2; X=10 +49.8/-14.5/-10.8/-11.5/+1.8; X=15 +37.6/-19.3/-16.1/-18.0/-14.9. The ungated dip is at least as good as every gated average above in PRE: gates only skip more trades (post-look read).

**(d') Dip basis, 288 matched (X, profile, N, veto) keys:**

| basis | 2026 | L6M | HOLD | PRE | X' | HOLD fills | share of fills from (ii) | P(target) fills from (ii) | P(target) fills from (i) | P(target) all signals |
|--|--|--|--|--|--|--|--|--|--|--|
| (i) from signal | +40.5k (115.9k) | -6.0k (45.3k) | -4.9k (42.6k) | -18.5k (22.7k) | -7.6k (24.8k) | 1577700 | 0.000 | 0.000 | 0.471 | 0.522 |
| (ii) from running favourable extreme (run-up >= 20) | -52.1k (96.8k) | -33.7k (53.3k) | -37.0k (51.9k) | -10.7k (26.8k) | -32.4k (35.8k) | 1215799 | 0.983 | 0.552 | 0.379 | 0.522 |
| (iii) either, first | +11.5k (98.7k) | +0.9k (38.0k) | -2.7k (34.7k) | -7.6k (18.9k) | -16.2k (25.4k) | 1892268 | 0.298 | 0.567 | 0.476 | 0.522 |

Plain answer to 'can something go positive, then negative, then enter': yes, and it is a good dip to buy by hit rate (P(target) from a (ii) fill is above the all-signal rate in every window) but in dollars (ii) alone loses heavily; the likely reason (not separately tested) is that you enter ABOVE the signal price with the stop still at the original level (stop distance far larger than the 60-pt target distance). (iii) is less negative than (i) in every window except 2026 (HOLD and PRE above), because (ii) fills some of the straight-up winners after a pullback. With min run-up 10 instead of 20: (ii) HOLD -23.8k (41.0k), (iii) HOLD -0.0k (29.9k).

**Single gates (each threshold alone, averaged over X in {0,3,5,10} x veto, basis i), HOLD fill rate and P(target|fill) - stack Delta:**

| gate | 2026 | L6M | HOLD | PRE | HOLD fill rate | P(target\|fill) |
|--|--|--|--|--|--|--|
| ABS>=2x | +31.3k (222.7k) | -10.3k (74.2k) | -3.4k (81.2k) | -30.2k (40.3k) | 0.045 | 0.438 |
| ABS>=3x | +24.2k (204.1k) | -17.0k (70.4k) | -8.8k (78.5k) | -30.4k (41.3k) | 0.015 | 0.400 |
| ABS>=5x | +17.7k (208.7k) | -16.5k (69.5k) | -7.5k (78.0k) | -29.1k (41.8k) | 0.006 | 0.469 |
| ABS>=10x | +18.7k (211.8k) | -18.7k (71.4k) | -8.5k (80.5k) | -28.9k (41.9k) | 0.001 | 0.520 |
| ICEBERG | +15.3k (216.2k) | -16.5k (73.1k) | -5.2k (80.3k) | -25.8k (40.2k) | 0.047 | 0.388 |
| IMB5 flip>=+0.10 | +34.0k (86.7k) | +2.1k (35.5k) | +2.6k (32.2k) | -11.0k (16.3k) | 0.876 | 0.496 |
| IMB5 flip>=+0.20 | +41.5k (97.4k) | -1.5k (38.9k) | -1.3k (35.1k) | -13.6k (18.1k) | 0.851 | 0.488 |
| IMB5 flip>=+0.30 | +29.0k (104.7k) | -3.0k (43.9k) | -2.7k (39.4k) | -22.3k (22.7k) | 0.782 | 0.475 |
| PRINT>=10 | +58.2k (164.9k) | +12.0k (70.6k) | +13.6k (67.9k) | -18.4k (31.3k) | 0.613 | 0.456 |
| PRINT>=25 | +45.6k (174.4k) | +5.2k (75.3k) | +10.6k (75.6k) | -23.6k (39.6k) | 0.267 | 0.423 |
| PRINT>=50 | +48.4k (204.9k) | -0.2k (72.8k) | +7.1k (81.1k) | -27.1k (40.2k) | 0.100 | 0.439 |
| PULL>=10% | +44.3k (91.6k) | +2.3k (36.8k) | +2.4k (33.6k) | -10.4k (17.7k) | 0.872 | 0.495 |
| PULL>=20% | +35.9k (92.3k) | +0.3k (37.4k) | +0.7k (33.8k) | -11.6k (18.0k) | 0.859 | 0.491 |
| PULL>=30% | +25.9k (88.1k) | -2.5k (38.6k) | -1.2k (35.4k) | -16.8k (19.5k) | 0.832 | 0.485 |
| MICRO>0.10tick | +35.3k (99.1k) | +3.7k (35.5k) | +3.6k (32.0k) | -9.7k (17.3k) | 0.881 | 0.497 |
| MICRO>0.25tick | +34.3k (99.1k) | +2.8k (35.6k) | +2.7k (32.1k) | -10.5k (17.4k) | 0.879 | 0.497 |
| DELTA 5s/10s | +39.2k (116.2k) | +1.3k (40.6k) | +0.6k (36.8k) | -15.1k (21.0k) | 0.850 | 0.488 |
| DELTA 10s/30s | +30.8k (138.3k) | +3.7k (42.7k) | +2.2k (38.5k) | -16.9k (21.2k) | 0.840 | 0.488 |
| DELTA 30s/60s | +19.7k (127.8k) | -3.7k (45.9k) | -2.2k (41.8k) | -20.2k (22.4k) | 0.804 | 0.480 |
| SWEEP reclaim | +37.1k (111.4k) | -2.7k (41.9k) | -3.6k (37.6k) | -12.6k (20.5k) | 0.841 | 0.488 |

Absorption and iceberg fire on 0.02% / 0.12% of seconds at 1-s cadence (ABS5 ~0): they fill only 0.1-4.7% of signals, so they skip nearly every trade (skipped winners). The print gates (10/25/50) are the only ones with a positive recent mean, but PRE is negative for all of them.

**Class pairs (28, default thresholds, both required, avg over X 0/5/10):** best 6 by L6M (looked data)

| pair | 2026 | L6M | HOLD | PRE |
|--|--|--|--|--|
| pair=PRINT+SWEEP | +51.2k (174.8k) | +0.1k (76.6k) | +6.5k (79.2k) | -22.8k (40.5k) |
| pair=PRINT+MICRO | +45.5k (193.7k) | -0.1k (77.7k) | +6.2k (78.6k) | -26.4k (39.4k) |
| pair=PRINT+PULL | +34.0k (187.9k) | -2.6k (75.0k) | +5.7k (76.9k) | -24.6k (40.0k) |
| pair=PULL+DELTA | +18.3k (102.8k) | -5.1k (43.9k) | -4.6k (40.4k) | -20.9k (25.6k) |
| pair=PULL+MICRO | +22.9k (112.1k) | -5.9k (40.3k) | -3.3k (36.8k) | -12.8k (19.4k) |
| pair=DELTA+SWEEP | +25.3k (125.8k) | -6.2k (46.1k) | -4.9k (42.9k) | -21.8k (25.2k) |

## 3. (b) CHASE, (c) SPLIT, (d) resting limit

**Chase (stack, averaged over the 11 dip bases; HOLD chase share of fills and P(target) of chase fills):** stop = original level unless marked 'fill' (control: 60 from the fill)

| chase rule | stop | 2026 | L6M | HOLD | PRE | X' | share of fills that are chase (HOLD) | P(target) chase fills | P(target) dip fills |
|--|--|--|--|--|--|--|--|--|--|
| price 3 pt | orig | +1.8k (79.4k) | -11.9k (23.8k) | -13.4k (21.6k) | -7.0k (12.8k) | -5.6k (13.0k) | 0.54 | 0.535 | 0.490 |
| price 5 pt | orig | +9.6k (69.6k) | -7.7k (27.0k) | -7.4k (23.9k) | -8.7k (14.2k) | -6.6k (15.4k) | 0.46 | 0.545 | 0.489 |
| price 8 pt | orig | +13.8k (77.6k) | -8.5k (28.3k) | -8.3k (24.9k) | -4.0k (15.0k) | -8.4k (15.2k) | 0.37 | 0.554 | 0.488 |
| price 10 pt | orig | -0.3k (81.4k) | -7.8k (29.6k) | -8.1k (26.2k) | -5.3k (15.1k) | -9.2k (14.9k) | 0.33 | 0.564 | 0.487 |
| price 15 pt | orig | +6.8k (94.1k) | -4.9k (30.2k) | -4.9k (27.0k) | -8.7k (14.9k) | -11.0k (19.2k) | 0.26 | 0.578 | 0.489 |
| price 20 pt | orig | +10.3k (98.4k) | +0.4k (32.6k) | -2.9k (29.4k) | -5.3k (17.3k) | -9.2k (22.7k) | 0.21 | 0.589 | 0.492 |
| next 60-s bar closes in favour | orig | +42.2k (105.3k) | -7.6k (36.3k) | -8.2k (32.5k) | -12.2k (14.8k) | +2.1k (15.4k) | 0.34 | 0.553 | 0.485 |
| 3 pt + imb5>=.2 | orig | +3.2k (83.0k) | -7.5k (25.2k) | -7.5k (22.2k) | -8.8k (14.0k) | -6.3k (15.9k) | 0.44 | 0.546 | 0.488 |
| 5 pt + imb5>=.2 | orig | +17.7k (65.5k) | -3.0k (25.5k) | -1.9k (22.7k) | -6.7k (13.4k) | -6.9k (15.8k) | 0.38 | 0.554 | 0.487 |
| 8 pt + imb5>=.2 | orig | +18.2k (79.1k) | -0.3k (28.6k) | -0.4k (25.3k) | -3.8k (13.9k) | -5.9k (16.4k) | 0.32 | 0.567 | 0.487 |
| 10 pt + imb5>=.2 | orig | +18.4k (93.5k) | +2.6k (31.6k) | +2.6k (28.1k) | -3.8k (15.0k) | -7.3k (16.8k) | 0.29 | 0.574 | 0.488 |
| 3 pt + delta10>0&30>0 | orig | +7.0k (73.0k) | -11.1k (23.8k) | -12.1k (21.5k) | -5.7k (14.0k) | -4.7k (12.8k) | 0.52 | 0.540 | 0.489 |
| 5 pt + delta10>0&30>0 | orig | +5.4k (61.6k) | -9.6k (25.8k) | -9.1k (22.8k) | -7.5k (14.8k) | -6.7k (15.7k) | 0.44 | 0.546 | 0.489 |
| 8 pt + delta10>0&30>0 | orig | +13.3k (69.8k) | -9.0k (28.1k) | -8.7k (24.7k) | -5.0k (15.0k) | -8.0k (15.4k) | 0.36 | 0.555 | 0.487 |
| 10 pt + delta10>0&30>0 | orig | -3.7k (80.5k) | -6.9k (30.0k) | -7.0k (26.6k) | -5.7k (14.9k) | -8.7k (15.0k) | 0.33 | 0.566 | 0.486 |
| 3 pt + print>=25 | orig | +29.0k (122.0k) | -2.5k (41.8k) | -1.3k (37.0k) | -6.7k (18.3k) | -4.9k (20.5k) | 0.16 | 0.562 | 0.491 |
| 5 pt + print>=25 | orig | +31.3k (122.4k) | -1.9k (41.9k) | -1.3k (37.6k) | -8.0k (18.5k) | -4.9k (21.1k) | 0.15 | 0.574 | 0.490 |
| 8 pt + print>=25 | orig | +29.4k (121.7k) | -3.0k (41.7k) | -1.9k (37.5k) | -8.4k (18.6k) | -6.3k (21.1k) | 0.14 | 0.580 | 0.490 |
| 10 pt + print>=25 | orig | +34.4k (114.4k) | -1.3k (41.2k) | -0.3k (37.0k) | -8.9k (18.8k) | -4.6k (20.6k) | 0.13 | 0.590 | 0.490 |
| 3 pt + >=2of8 | orig | +16.6k (90.7k) | -9.5k (27.5k) | -11.5k (24.3k) | -6.4k (12.8k) | -4.6k (14.2k) | 0.50 | 0.540 | 0.489 |
| 5 pt + >=2of8 | orig | +11.2k (61.4k) | -6.9k (25.5k) | -6.8k (22.5k) | -8.6k (14.0k) | -7.3k (15.6k) | 0.42 | 0.548 | 0.489 |
| 8 pt + >=2of8 | orig | +13.8k (80.9k) | -6.9k (29.0k) | -5.8k (25.6k) | -4.0k (15.1k) | -8.8k (15.6k) | 0.35 | 0.562 | 0.486 |
| 10 pt + >=2of8 | orig | +18.1k (91.6k) | -3.4k (31.0k) | -3.5k (27.7k) | -2.9k (14.9k) | -7.8k (15.0k) | 0.31 | 0.570 | 0.487 |
| price 3 pt | fill | -15.1k (82.6k) | -18.4k (28.6k) | -20.2k (26.1k) | -9.1k (13.2k) | -12.8k (15.6k) | 0.54 | 0.517 | 0.512 |
| price 5 pt | fill | -12.0k (68.2k) | -19.9k (31.2k) | -19.3k (28.5k) | -10.4k (14.7k) | -11.8k (17.8k) | 0.46 | 0.520 | 0.513 |
| price 8 pt | fill | -12.5k (90.4k) | -23.1k (35.2k) | -21.2k (32.7k) | -12.3k (16.7k) | -12.1k (18.3k) | 0.37 | 0.520 | 0.514 |
| price 10 pt | fill | -28.3k (97.7k) | -22.1k (34.9k) | -19.7k (31.8k) | -14.8k (16.3k) | -14.6k (17.8k) | 0.33 | 0.525 | 0.514 |
| price 15 pt | fill | -5.9k (95.6k) | -12.8k (37.4k) | -11.8k (34.6k) | -9.3k (17.2k) | -14.1k (22.1k) | 0.26 | 0.528 | 0.517 |
| price 20 pt | fill | +3.9k (106.4k) | -11.6k (38.6k) | -12.7k (35.8k) | -9.8k (18.9k) | -10.8k (23.7k) | 0.21 | 0.526 | 0.519 |
| next 60-s bar closes in favour | fill | +8.8k (109.5k) | -18.7k (36.9k) | -18.4k (33.0k) | -15.2k (15.6k) | -6.2k (19.3k) | 0.34 | 0.527 | 0.513 |
| 3 pt + imb5>=.2 | fill | -16.1k (78.3k) | -26.5k (29.1k) | -24.6k (26.9k) | -12.4k (15.1k) | -10.1k (18.2k) | 0.44 | 0.519 | 0.512 |
| 5 pt + imb5>=.2 | fill | -9.1k (72.5k) | -22.1k (33.2k) | -19.3k (30.8k) | -12.4k (14.9k) | -9.6k (18.6k) | 0.38 | 0.523 | 0.513 |
| 8 pt + imb5>=.2 | fill | -11.9k (92.5k) | -16.3k (36.0k) | -15.1k (33.4k) | -11.6k (16.0k) | -9.4k (17.7k) | 0.32 | 0.527 | 0.514 |
| 10 pt + imb5>=.2 | fill | -15.5k (98.9k) | -14.5k (37.2k) | -13.4k (34.5k) | -10.6k (16.1k) | -10.3k (19.1k) | 0.29 | 0.525 | 0.514 |
| 3 pt + delta10>0&30>0 | fill | -13.2k (68.8k) | -19.6k (27.6k) | -20.2k (25.6k) | -6.9k (14.8k) | -12.1k (15.1k) | 0.52 | 0.520 | 0.512 |
| 5 pt + delta10>0&30>0 | fill | -15.5k (64.1k) | -20.6k (29.8k) | -19.9k (27.3k) | -9.8k (15.3k) | -12.7k (18.6k) | 0.44 | 0.519 | 0.514 |
| 8 pt + delta10>0&30>0 | fill | -12.9k (84.0k) | -22.0k (34.3k) | -20.2k (31.9k) | -13.9k (16.6k) | -11.8k (18.3k) | 0.36 | 0.521 | 0.514 |
| 10 pt + delta10>0&30>0 | fill | -32.1k (99.3k) | -20.9k (35.3k) | -18.6k (32.1k) | -13.8k (17.0k) | -14.2k (17.7k) | 0.33 | 0.526 | 0.513 |
| 3 pt + print>=25 | fill | -6.9k (102.1k) | -24.8k (39.1k) | -20.9k (35.4k) | -10.2k (18.6k) | -8.6k (23.3k) | 0.16 | 0.511 | 0.519 |
| 5 pt + print>=25 | fill | -6.0k (102.2k) | -26.0k (39.0k) | -21.2k (36.0k) | -11.2k (19.5k) | -8.1k (23.3k) | 0.15 | 0.521 | 0.518 |
| 8 pt + print>=25 | fill | -2.7k (99.5k) | -25.0k (39.5k) | -20.7k (36.4k) | -11.0k (19.6k) | -8.5k (24.2k) | 0.14 | 0.523 | 0.518 |
| 10 pt + print>=25 | fill | -4.0k (93.3k) | -22.4k (39.2k) | -18.8k (35.9k) | -11.6k (19.7k) | -8.2k (23.7k) | 0.13 | 0.528 | 0.518 |
| 3 pt + >=2of8 | fill | -12.6k (87.6k) | -23.3k (30.2k) | -23.7k (27.5k) | -7.6k (13.5k) | -9.3k (17.1k) | 0.50 | 0.518 | 0.512 |
| 5 pt + >=2of8 | fill | -14.7k (67.3k) | -24.9k (30.2k) | -23.9k (27.7k) | -12.7k (15.5k) | -13.0k (17.2k) | 0.42 | 0.519 | 0.513 |
| 8 pt + >=2of8 | fill | -18.3k (96.5k) | -23.2k (34.4k) | -19.6k (31.9k) | -12.9k (16.7k) | -12.6k (17.8k) | 0.35 | 0.529 | 0.512 |
| 10 pt + >=2of8 | fill | -21.7k (96.5k) | -17.5k (36.6k) | -15.2k (33.4k) | -11.5k (16.2k) | -14.9k (18.1k) | 0.31 | 0.527 | 0.513 |

Chase-only (X = infinity, buy only strength; stop orig): HOLD price 5 -30.5k; price 10 -25.2k; next bar -5.6k; print>=25 Y10 -2.5k (MDE 30-90k): the straight-up winners are a minority of the volume you would buy; chase-only is the worst family.

**Split (stack, group averages; F = share at the signal at market, remainder on the confirmed dip, ADDUW B2 risk-capped, target re-based):**

| group | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| F=0.3 | +14.5k (61.1k) | -3.2k (29.0k) | -3.5k (25.8k) | -7.0k (14.7k) | -7.7k (16.6k) |
| F=0.5 | +8.6k (47.8k) | -2.8k (23.3k) | -3.3k (20.9k) | -5.5k (12.9k) | -6.5k (14.0k) |
| F=0.7 | +3.3k (33.9k) | +0.9k (16.6k) | -0.2k (15.1k) | -4.4k (10.5k) | -3.9k (10.7k) |
| dip X=3 | +17.9k (37.8k) | +3.8k (15.2k) | +4.2k (13.5k) | -1.8k (11.1k) | -4.0k (9.4k) |
| dip X=5 | +15.9k (42.1k) | +3.4k (21.2k) | +3.1k (18.8k) | -3.1k (12.1k) | -4.4k (12.9k) |
| dip X=8 | +6.4k (52.3k) | -1.1k (26.9k) | -1.4k (23.7k) | -7.4k (13.6k) | -5.7k (14.6k) |
| dip X=10 | +3.5k (51.6k) | -5.0k (27.6k) | -5.5k (24.6k) | -7.8k (14.0k) | -6.0k (15.8k) |
| dip X=15 | +0.2k (67.8k) | -9.4k (27.5k) | -12.0k (25.7k) | -8.0k (15.3k) | -10.2k (19.2k) |
| chase (type,Y)=0,0 | +36.1k (56.7k) | +11.4k (24.4k) | +9.4k (22.2k) | -1.6k (14.0k) | +2.7k (15.6k) |
| chase (type,Y)=1,5 | -12.2k (34.7k) | -6.2k (22.1k) | -7.2k (20.1k) | -5.4k (12.8k) | -5.8k (12.3k) |
| chase (type,Y)=1,10 | +2.2k (46.5k) | -9.6k (25.0k) | -8.5k (22.2k) | -6.9k (13.5k) | -9.1k (13.3k) |
| chase (type,Y)=1,20 | +19.1k (67.2k) | +4.5k (28.9k) | +2.4k (25.7k) | -7.8k (13.3k) | -9.5k (16.1k) |
| chase (type,Y)=3,5 | -4.6k (41.4k) | -7.7k (22.1k) | -7.9k (19.9k) | -6.4k (13.4k) | -5.4k (14.4k) |
| chase (type,Y)=3,10 | +12.2k (56.4k) | -2.5k (27.0k) | -2.1k (24.0k) | -5.5k (13.7k) | -9.1k (15.3k) |
| N=0 | +5.0k (42.1k) | -2.5k (20.9k) | -2.6k (18.6k) | -4.4k (12.1k) | -6.1k (12.7k) |
| N=1 | +8.7k (42.4k) | -1.1k (21.5k) | -1.7k (19.2k) | -5.1k (12.2k) | -6.1k (12.9k) |
| N=2 | +11.4k (50.4k) | -2.0k (23.2k) | -2.8k (20.8k) | -5.9k (12.4k) | -5.8k (13.1k) |
| N=3 | +10.1k (57.4k) | -1.1k (25.1k) | -2.1k (22.3k) | -7.0k (13.1k) | -6.2k (15.1k) |

The no-chase split rows (F x X x N) are listed in full in out/l2set/entry (look3). Short form, stack Delta HOLD/PRE $/wk: F=0.7 with X 3/5/8/10 and N=0: +7.0/+7.1, +14.1/+5.3, +18.7/+2.7, +17.7/+1.1 (k, MDE 12-22k); F=0.5 X=5 N=1 +18.3/+2.5; F=0.3 X=3 N=1 +17.5/+1.2. Chasing the remainder makes every split worse (px5 -7.2k HOLD, px10 -8.5k) except price 20 (+2.4k) because the original stop plus a chase is a bigger bet.

**Pooled split cell: cost sensitivity (extra cost per remainder lot-fill, stack Delta $/wk), exposure:**

| extra cost (pt) | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| 0 | +19.5k | +13.3k | +11.6k | +7.6k | +2.8k |
| 0.25 | +19.3k | +12.0k | +10.2k | +5.8k | +2.4k |
| 0.5 | +18.3k | +10.5k | +8.8k | +3.0k | +1.3k |
| 1 | +18.5k | +8.1k | +6.4k | -0.3k | -0.6k |
| 2 | +12.1k | +3.9k | +2.1k | -8.1k | -5.5k |
| 3 | +4.8k | -1.5k | -3.7k | -13.7k | -9.9k |

Average total lots when the remainder fills: 1.023 x live lots (risk-matched, cap 2.0); remainder fills 92% of trades. Other plateau cells (F.7 X5 N0, F.7 X8 N1, F.5 X5 N1) have the same shape: HOLD +14.1k/+19.0k/+18.3k, PRE +5.3k/+2.5k/+2.5k, break-even extra cost 1.9-2.6 pt in HOLD and 0.2-1.0 pt in PRE (pooled cell: 2.6 / 1.0).

**Resting limit instead of market (join best for T s, then market), stack Delta vs the SAME cell at market (matched pairs, 14 base cells):**

| T | 2026 | L6M | HOLD | PRE | X' | fill rate limit / market (HOLD) | timed out into market | mean dip depth at fill (pt, limit / market) | P(target) limit / market |
|--|--|--|--|--|--|--|--|--|--|
| 5 s | +0.4k (7.4k) | +3.4k (3.8k) | +2.9k (3.5k) | +1.6k (2.2k) | +2.1k (1.5k) | 0.804 / 0.805 | 25% | 8.82 / 8.75 | 0.478 / 0.478 |
| 10 s | -0.8k (9.4k) | +1.9k (3.9k) | +1.9k (3.5k) | +2.3k (2.7k) | +2.7k (1.5k) | 0.804 / 0.805 | 18% | 8.83 / 8.75 | 0.478 / 0.478 |

The limit saves about 0.07 pt per fill on average (the touch-fill convention is optimistic and 18-25% of limits time out into the market order); it is positive in L6M, HOLD, PRE and X' (2026 about 0, MDE 7-9k) and the X' mean (+2.1k / +2.7k) exceeds its MDE (1.5k), but it is a +2 to +3k/wk refinement, not an entry rule on its own.

## 4. (e) per book / session / regime, learned gate, walk-forward, placebo, four-way split

**Learned gate (F7, walk-forward LightGBM, 60-s cadence, quarterly re-fit from 2023-10):** top features at every re-fit are the path variables (dip depth, run-up, time since arm) then book and session; book-gate features rank below them. Stack Delta:

| cell | 2026 | L6M | HOLD | PRE | X' (from 2023-10) |
|--|--|--|--|--|--|
| fam=F7|lgb_th=0.0|X=0 | +36.6k (161.3k) | -0.8k (50.6k) | -7.0k (46.8k) | -7.6k (28.1k) | +1.0k (40.7k) |
| fam=F7|lgb_th=0.0|X=3 | +52.5k (180.9k) | -0.6k (60.4k) | -2.4k (55.0k) | -21.7k (31.2k) | -4.5k (40.9k) |
| fam=F7|lgb_th=0.0|X=5 | +52.9k (179.7k) | +2.7k (61.7k) | +1.0k (57.7k) | -21.1k (32.0k) | -4.5k (41.9k) |
| fam=F7|lgb_th=0.0|X=10 | +76.5k (156.5k) | -7.2k (59.4k) | -8.4k (58.1k) | -17.7k (34.2k) | -4.0k (42.8k) |
| fam=F7|lgb_th=1.0|X=0 | +37.1k (163.0k) | +0.6k (50.8k) | -5.8k (47.2k) | -12.4k (29.3k) | +2.2k (40.7k) |
| fam=F7|lgb_th=1.0|X=3 | +41.9k (186.7k) | -4.6k (59.6k) | -6.3k (54.7k) | -22.4k (31.5k) | -2.8k (40.8k) |
| fam=F7|lgb_th=1.0|X=5 | +39.3k (186.9k) | -3.4k (60.9k) | -4.7k (57.4k) | -21.9k (32.4k) | -3.2k (41.8k) |
| fam=F7|lgb_th=1.0|X=10 | +70.6k (163.1k) | -8.9k (59.5k) | -9.0k (58.5k) | -21.5k (34.7k) | -4.2k (43.4k) |
| fam=F7|lgb_th=2.0|X=0 | +53.7k (178.7k) | +6.7k (53.5k) | +0.0k (49.7k) | -16.4k (32.9k) | +0.1k (41.2k) |
| fam=F7|lgb_th=2.0|X=3 | +53.6k (179.4k) | -2.0k (58.0k) | -4.0k (53.5k) | -22.1k (34.5k) | -4.5k (41.6k) |
| fam=F7|lgb_th=2.0|X=5 | +46.9k (177.4k) | -2.7k (59.1k) | -3.4k (55.5k) | -23.3k (35.0k) | -4.0k (42.0k) |
| fam=F7|lgb_th=2.0|X=10 | +71.8k (165.1k) | -11.7k (60.4k) | -10.8k (59.3k) | -22.0k (36.4k) | -6.4k (44.0k) |

All 12 are negative or inside MDE in PRE and HOLD; the model learns 'enter later = enter where the base would have been stopped'. DEAD.

**Walk-forward policies on the exact lock engine (stack Delta $/wk; MDE):**

| policy | 2026 | L6M | HOLD | PRE | X' (from 2023-07) | fill rate |
|--|--|--|--|--|--|--|
| per-book PRE-selected | +0.9k (103.4k) | -2.8k (38.3k) | -3.4k (35.0k) | +29.5k (21.0k) | -15.0k (25.6k) | 0.85 |
| pooled STACK PRE-selected | +19.5k (41.7k) | +13.3k (14.5k) | +11.6k (14.0k) | +7.6k (11.2k) | +2.8k (8.4k) | 0.92 |
| book x session PRE-selected | +3.1k (120.1k) | -17.4k (45.3k) | -23.8k (44.6k) | +39.6k (25.3k) | -21.0k (34.2k) | 0.73 |
| book x vol-tercile PRE-selected | +9.5k (111.0k) | -17.9k (46.4k) | -14.6k (44.1k) | +29.8k (24.7k) | -9.2k (28.9k) | 0.68 |
| WF 12m trailing, quarterly | +10.2k (86.2k) | -14.1k (40.6k) | -7.5k (40.3k) | -17.1k (27.8k) | -28.7k (32.9k) | 0.69 |
| WF 3m trailing, quarterly | +48.5k (142.1k) | -3.7k (60.5k) | -4.3k (54.1k) | -21.6k (25.4k) | -19.9k (32.6k) | 0.71 |
| WF 12m dip-only (F1,F2,F3) | +8.8k (84.9k) | -5.7k (39.0k) | -1.4k (39.7k) | -14.4k (29.8k) | -21.7k (36.5k) | 0.65 |
| WF 12m chase-only (F4) | +17.8k (113.6k) | -18.9k (53.3k) | -14.3k (52.9k) | -24.2k (24.3k) | -32.5k (35.7k) | 0.80 |

The adaptive variants (per-book trailing re-selection over all 2,179 cells) are negative in PRE, L6M and HOLD: the best trailing cell does not persist. Per-book PRE-selected cells fade out of sample (stack PRE +29.5k -> HOLD -3.4k). Subgroup policies (book x session 49 cells, book x vol tercile 30) are worse still (HOLD -23.8k / -14.6k).

**LAST walk-forward re-fit in full (12 m trailing, refit 2026-01-01 - the one live today; scores are in-sample trailing-12m lot-matched $):**

| book | cell chosen | D6 group-05 settings | fills | in-sample $ |
|--|--|--|--|--|
| ST | fam=F1|X=2|b=iii|prof=strict|N=4|veto=v3 | dip_X=2pt basis=iii(either, run-up>=20) ; confirmations_N=4 of 8 gate_list=[absorption >=10x median level hit at my best in 10 s, best never cleared; iceberg refill (best consumed <50% then refilled >=80%, 10 s); imb5 flip (<=-0.10 within 30 s -> >=+0.30); large print >=50 with the trade (10 s); other side 5-level depth pulled >=30% (10 s), mine not; microprice >0.25 tick with the trade; delta 30 s with / 60 s against; sweep >=2 ticks reclaimed (10 s)] ; veto=imb5<=-0.30 ; chase_Y=off ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | 1841 | +707048 |
| HM | fam=F1|X=0|b=i|prof=dflt|N=4|veto=v3 | dip_X=0pt basis=i(from signal) ; confirmations_N=4 of 8 gate_list=[absorption >=5x median level hit at my best in 10 s, best never cleared; iceberg refill (best consumed <50% then refilled >=80%, 10 s); imb5 flip (<=-0.10 within 30 s -> >=+0.20); large print >=25 with the trade (10 s); other side 5-level depth pulled >=20% (10 s), mine not; microprice >0.10 tick with the trade; delta 10 s with / 30 s against; sweep >=2 ticks reclaimed (10 s)] ; veto=imb5<=-0.30 ; chase_Y=off ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | 1458 | +285750 |
| WT | fam=F2|gate=ICE|X=0|b=i|veto=v4 | dip_X=0pt basis=i(from signal) ; confirmations_N=1 gate_list=[ICEBERG] ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | 109 | +1005024 |
| KB | fam=F1|X=8|b=iii|prof=loose|N=4|veto=v3 | dip_X=8pt basis=iii(either, run-up>=20) ; confirmations_N=4 of 8 gate_list=[absorption >=2x median level hit at my best in 10 s, best never cleared; iceberg refill (best consumed <50% then refilled >=80%, 10 s); imb5 flip (<=-0.10 within 30 s -> >=+0.10); large print >=10 with the trade (10 s); other side 5-level depth pulled >=10% (10 s), mine not; microprice >0.10 tick with the trade; delta 5 s with / 10 s against; sweep >=2 ticks reclaimed (10 s)] ; veto=imb5<=-0.30 ; chase_Y=off ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | 2321 | +412870 |
| SM | fam=F4|X=0|N=3|chase=px15|stop=fill|veto=v4 | dip_X=0pt basis=i(from signal) ; confirmations_N=3 of 8 gate_list=[absorption >=5x median level hit at my best in 10 s, best never cleared; iceberg refill (best consumed <50% then refilled >=80%, 10 s); imb5 flip (<=-0.10 within 30 s -> >=+0.20); large print >=25 with the trade (10 s); other side 5-level depth pulled >=20% (10 s), mine not; microprice >0.10 tick with the trade; delta 10 s with / 30 s against; sweep >=2 ticks reclaimed (10 s)] ; veto=imb5<=-0.40 ; chase_Y=15pt (price) chase_stop=from fill ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | 622 | +364757 |
| PE | fam=F1|X=8|b=ii|prof=strict|N=4|veto=v3 | dip_X=8pt basis=ii(from running favourable extreme, run-up>=20) ; confirmations_N=4 of 8 gate_list=[absorption >=10x median level hit at my best in 10 s, best never cleared; iceberg refill (best consumed <50% then refilled >=80%, 10 s); imb5 flip (<=-0.10 within 30 s -> >=+0.30); large print >=50 with the trade (10 s); other side 5-level depth pulled >=30% (10 s), mine not; microprice >0.25 tick with the trade; delta 30 s with / 60 s against; sweep >=2 ticks reclaimed (10 s)] ; veto=imb5<=-0.30 ; chase_Y=off ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | 1245 | +677020 |
| PB | fam=F1|X=8|b=ii|M=10|prof=dflt|N=3|veto=v4 | dip_X=8pt basis=ii(from running favourable extreme, run-up>=10) ; confirmations_N=3 of 8 gate_list=[absorption >=5x median level hit at my best in 10 s, best never cleared; iceberg refill (best consumed <50% then refilled >=80%, 10 s); imb5 flip (<=-0.10 within 30 s -> >=+0.20); large print >=25 with the trade (10 s); other side 5-level depth pulled >=20% (10 s), mine not; microprice >0.10 tick with the trade; delta 10 s with / 30 s against; sweep >=2 ticks reclaimed (10 s)] ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | 1469 | +395327 |
| DN | MARKET (no positive cell) | market entry | 0 | +0 |
| MV | fam=F1|X=10|b=iii|prof=dflt|N=3|veto=v4 | dip_X=10pt basis=iii(either, run-up>=20) ; confirmations_N=3 of 8 gate_list=[absorption >=5x median level hit at my best in 10 s, best never cleared; iceberg refill (best consumed <50% then refilled >=80%, 10 s); imb5 flip (<=-0.10 within 30 s -> >=+0.20); large print >=25 with the trade (10 s); other side 5-level depth pulled >=20% (10 s), mine not; microprice >0.10 tick with the trade; delta 10 s with / 30 s against; sweep >=2 ticks reclaimed (10 s)] ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | 2249 | +768194 |
| MA | fam=F1|X=15|b=ii|prof=dflt|N=3|veto=v3 | dip_X=15pt basis=ii(from running favourable extreme, run-up>=20) ; confirmations_N=3 of 8 gate_list=[absorption >=5x median level hit at my best in 10 s, best never cleared; iceberg refill (best consumed <50% then refilled >=80%, 10 s); imb5 flip (<=-0.10 within 30 s -> >=+0.20); large print >=25 with the trade (10 s); other side 5-level depth pulled >=20% (10 s), mine not; microprice >0.10 tick with the trade; delta 10 s with / 30 s against; sweep >=2 ticks reclaimed (10 s)] ; veto=imb5<=-0.30 ; chase_Y=off ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | 539 | +255271 |

**Drift by quarter - cell the 12 m walk-forward chose per book (family|X|basis or gate), one column per refit:**

| book | 2023-07 | 2023-10 | 2024-01 | 2024-04 | 2024-07 | 2024-10 | 2025-01 | 2025-04 | 2025-07 | 2025-10 | 2026-01 |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ST | F3:X10 | F2:X0 | F4:X10 | F2:X0 | F2:X0 | F1:X3 | F4:chase | F4:chase | F1:X2 | F1:X2 | F1:X2 |
| HM | F4:X5 | F4:X5 | F2:X10 | F2:X10 | F4:X5 | F4:X5 | F4:X5 | F4:chase | F4:X10 | F4:X10 | F1:X0 |
| WT | F3:X0 | F3:X0 | F3:X0 | F3:X5 | F3:X5 | F1:X15 | F1:X3 | F1:X8 | F1:X10 | F1:X15 | F2:X0 |
| KB | F1:X10 | F3:X10 | F2:X3 | F7:X0 | F4:chase | F4:chase | F4:X5 | F4:X5 | F1:X8 | F1:X15 | F1:X8 |
| SM | F1:X15 | F1:X15 | F4:X5 | F1:X15 | F1:X15 | F1:X15 | F1:X15 | F4:chase | F4:X0 | F4:X0 | F4:X0 |
| PE | F2:X3 | F4:X5 | F4:X5 | F4:X5 | F4:X10 | F4:X10 | F4:X10 | F4:X10 | F4:chase | F1:X5 | F1:X8 |
| PB | F5:X15 | F4:X5 | F1:X8 | F1:X8 | F4:chase | F1:X15 | F4:chase | F4:chase | F1:X5 | F4:X5 | F1:X8 |
| DN | F4:chase | F3:X5 | F3:X5 | F3:X0 | F3:X0 | MKT | F4:X10 | MKT | MKT | F5:X10 | MKT |
| MV | F2:X0 | F2:X3 | F2:X5 | F7:X3 | F4:chase | F5:X15 | F1:X3 | F4:chase | F4:X5 | F4:chase | F1:X10 |
| MA | F4:chase | F4:chase | F4:chase | F1:X2 | F1:X2 | F1:X2 | F1:X2 | F1:X3 | F1:X15 | F1:X15 | F1:X15 |

Family mix by quarter: 2023-07 {'F3': 2, 'F4': 3, 'F1': 2, 'F2': 2, 'F5': 1}; 2023-10 {'F2': 2, 'F4': 4, 'F3': 3, 'F1': 1}; 2024-01 {'F4': 4, 'F2': 3, 'F3': 2, 'F1': 1}; 2024-04 {'F2': 2, 'F3': 2, 'F7': 2, 'F1': 3, 'F4': 1}; 2024-07 {'F2': 1, 'F4': 5, 'F3': 2, 'F1': 2}; 2024-10 {'F1': 5, 'F4': 3, 'MKT': 1, 'F5': 1}; 2025-01 {'F4': 6, 'F1': 4}; 2025-04 {'F4': 7, 'F1': 2, 'MKT': 1}; 2025-07 {'F1': 5, 'F4': 4, 'MKT': 1}; 2025-10 {'F1': 5, 'F4': 4, 'F5': 1}; 2026-01 {'F1': 7, 'F2': 1, 'F4': 1, 'MKT': 1}. The chosen gate/threshold/X changes almost every quarter for every book: there is no stable setting to track. WT's picks are often 'almost never fill' cells (e.g. iceberg only, 109 fills, +1.0M in-sample) because WT's own market-entry P&L is negative in the trailing year: that is skip-the-book, not an entry rule. The refit date 2026-01-01 is the last one possible under the 2026-02-06 cap.

**Per-session and per-regime PRE-selected cell, evaluated later (trade-level lot-matched, each subgroup alone; $/wk of the whole-window week count):** share of subgroups positive: 
- session: 49 subgroups, positive in PRE 49 (by construction), L6M 15, HOLD 17, X' 20; sum over subgroups L6M -56.5k, HOLD -51.4k, PRE +142.2k, X' -19.7k.
- vol: 30 subgroups, positive in PRE 29 (by construction), L6M 7, HOLD 7, X' 14; sum over subgroups L6M -79.6k, HOLD -50.7k, PRE +116.9k, X' -2.1k.

Best recent subgroup rows (looked data; trade-level, no engine):

| book | subgroup | PRE-selected cell | PRE | X' | HOLD | L6M | 2026 |
|--|--|--|--|--|--|--|--|
| MV | vol 1 | fam=F3|pair=IMB+PULL|X=10|prof=dflt|veto=v4 | +5.2k | +3.7k | +8.1k | +7.2k | +3.0k |
| ST | session asia | fam=F2|gate=SWEEP|X=5|b=iii|veto=v4 | +2.8k | -1.4k | +6.8k | +6.9k | +13.7k |
| WT | session nypm | fam=F3|pair=IMB+PRINT|X=10|prof=dflt|veto=v4 | +3.9k | +0.4k | +6.6k | +5.7k | +7.7k |
| MV | session london | fam=F2|gate=PRINT10|X=10|b=iii|veto=v4 | +7.5k | +0.1k | +3.3k | +5.5k | +16.8k |
| WT | session london | fam=F1|X=8|b=ii|prof=dflt|N=3|veto=v3 | +4.5k | +0.3k | +6.2k | +4.6k | +5.2k |
| WT | vol 1 | fam=F2|gate=ICE|X=0|b=i|veto=v4 | +4.9k | +3.3k | +9.6k | +4.3k | +2.1k |
| WT | vol 2 | fam=F1|X=15|b=ii|prof=dflt|N=4|veto=v3 | +4.1k | -0.9k | +2.7k | +3.0k | +2.0k |
| HM | session asia | fam=F4|X=5|N=3|chase=imb8|stop=fill|veto=v4 | +2.8k | -0.5k | +1.2k | +2.5k | +8.0k |
| PE | session nyam | fam=F4|X=10|N=2|chase=prt3|stop=orig|veto=v4 | +3.3k | -3.2k | +0.7k | +2.0k | +6.6k |
| KB | session nyam | fam=F4|X=10|N=0|chase=2of85|stop=fill|veto=v4 | +0.9k | -1.8k | +0.5k | +1.8k | +13.6k |

**Placebo gates at the same fill rate (100 draws per cell and unit; rank of the real cell, PRE / HOLD; 1.0 = real beats all):** STACK F5 0.79/1.00; HM F1 1.00/0.07; WT F1 0.98/0.06; KB F1 1.00/0.79; SM F4 1.00/0.97; PE F5 0.80/1.00 (cells without a gate, chase-only and limit cells have no placebo = fail by prereg). The pooled split cell: its HOLD rank is 1.00 (the real cell beats all 100 placebos in HOLD) but PRE 0.79, so the gate itself is not what earns it; ungated N=0 variants are as good.

**Four-way dollar split vs market entry (trade-level, lot-matched $; count in parentheses) for each unit's PRE-selected cell, HOLD:**

| unit | cell | skipped winners | skipped losers | cheaper losers | converted loss->win | other filled | total |
|--|--|--|--|--|--|--|--|
| STACK | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | -1133.2k (558) | +65.9k (24) | +17.7k (140) | +653.6k (49) | +560.4k (6560) | +164.4k |
| ALL | fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | -1900.7k (789) | +65.9k (24) | +30.9k (232) | +1008.9k (65) | +948.9k (9693) | +153.8k |
| ST | fam=F5|F=0.7|X=5|N=0|chase=px5|veto=v4 | -3.3k (1) | +0.0k (0) | +5.2k (283) | +213.5k (10) | -123.6k (1088) | +91.6k |
| HM | fam=F1|X=3|b=iii|prof=dflt|N=4|veto=v3 | -464.0k (44) | +367.7k (31) | +797.9k (324) | +452.7k (22) | -1197.0k (587) | -42.8k |
| WT | fam=F1|X=15|b=iii|prof=dflt|N=2|veto=none | -1993.2k (488) | +657.0k (106) | +1081.5k (455) | +874.6k (86) | -405.9k (758) | +214.0k |
| KB | fam=F1|X=5|b=ii|M=10|prof=dflt|N=3|veto=v4 | -352.4k (61) | +1456.1k (233) | +28.4k (48) | +24.3k (2) | -1019.8k (1030) | +136.6k |
| SM | fam=F4|X=10|N=1|chase=imb8|stop=orig|veto=v4 | +0.0k (0) | +0.0k (0) | +144.3k (88) | +141.8k (9) | -326.0k (266) | -39.8k |
| PE | fam=F5|F=0.3|X=10|N=3|chase=px10|veto=v4 | -161.1k (37) | +9.6k (2) | +16.8k (235) | +310.5k (27) | -295.4k (1010) | -119.6k |
| PB | fam=F4|X=inf|chase=nextbar|stop=fill | -2686.5k (247) | +2673.4k (229) | +0.0k (0) | +0.0k (0) | -580.3k (489) | -593.3k |
| DN | fam=F5|F=0.7|X=5|N=1|chase=imb5|veto=v4 | -6.7k (2) | +0.0k (0) | +5.1k (150) | +48.2k (3) | -83.2k (627) | -36.6k |
| MV | fam=F4|X=5|N=3|chase=px10|stop=orig|veto=v4 | -433.2k (39) | +24.5k (2) | +723.7k (407) | +512.7k (29) | -845.7k (774) | -18.0k |
| MA | fam=F1|X=15|b=iii|prof=strict|N=2|veto=v3 | -255.4k (23) | +0.0k (0) | +488.4k (145) | +166.5k (8) | -567.4k (298) | -167.8k |

Pooled split cell, four-way split by session (HOLD, 6 engine books, trade level):

| session | skipped winners | skipped losers | cheaper losers | converted | other filled | total |
|--|--|--|--|--|--|--|
| asia | -309.7k (149) | +65.9k (24) | +0.4k (5) | +161.6k (10) | +133.0k (1821) | +51.2k |
| close | +0.0k (0) | +0.0k (0) | +1.0k (5) | +0.0k (0) | +0.8k (12) | +1.8k |
| london | -186.8k (95) | +0.0k (0) | +0.5k (5) | +92.3k (6) | +108.7k (1398) | +14.7k |
| nyam | -432.8k (210) | +0.0k (0) | +3.2k (27) | +212.9k (16) | +182.5k (1870) | -34.3k |
| nypm | -154.5k (79) | +0.0k (0) | +11.1k (96) | +141.3k (13) | +111.5k (1127) | +109.3k |
| pre | -49.4k (25) | +0.0k (0) | +1.4k (2) | +45.5k (4) | +24.1k (332) | +21.6k |

(Because the pooled split keeps 70% of every trade at the signal, almost nothing is 'skipped'; the dollars sit in 'other filled' = the remainder bought cheaper and the re-based target.)

## 5. Caveats and what was not done
- 250 ms evaluation not possible (see header). Gate cadence is 1 s; the learned gate only 60 s. Absorption (hit >= k x median level and the best never cleared) and iceberg are almost never true at 1-s aggregation (tape-level order data would be needed); the 'N of 8' rule therefore behaves roughly like N of 6 in practice.
- The signal series is the TAKEN-signal series (signals the base blocked while in a position are not modelled); the lock engine re-applies the per-book busy rule on modified rows. A split trade enters the engine as ONE row (first fill at the signal, net pts per planned lot); the extra order's slippage beyond the 1 tick is NOT in the engine (see the cost-sensitivity table: each +0.25 pt per remainder lot-fill removes about 1.3-2.0k/wk in HOLD).
- Cost basis: ADDUW's finding that the sign of add results flips with the cost basis applies here: basis B2 (V0 measured fills; slice 1 at the library entry, remainder market +1 tick, 0.242 pt fee per lot-fill, target year correction) is what these numbers use.
- Chase with the original stop risks stop+Y per trade at live lots (not risk-matched); the 'fill' stop rows are the control.
- PB DN MV MA rows are trade-level (no lock engine); ALL mixes engine and trade-level books.
- Selection on looked data: the CR-best and L6M-ranked rows; PRE-selected rows are the honest ones. One look per group was used; the cost gate of split cells was re-implemented once after the look (the +2-tick stress now charges the remainder fill only; slice 1 is the base-convention fill) - an implementation fix, not a parameter change.
- The CANDIDATE-RECENT label is mechanical (2026 >= 0 and L6M > 0); with a 5-week 2026 window and MDE 18-160k per unit it carries almost no information on its own.

## 6. Files
- cells/prereg: l2vast/ds3/prereg/L2SET_ENTRY_prereg.md, L2SET_ENTRY_cells.csv; PRE file autopilot/DS3_L2SET_ENTRY_PREHOLD.md
- code l2vast/ds3/code/l2set/ (ls_build.py gate bits, ls_glob.py, ls_sim.py kernel, ls_cells.py, ls_grid.py, ls_engrun.py, ls_pre.py, ls_look1/1b/1c/2/3/4/5.py, ls_report.py, l2set_refit.sh); outputs l2vast/ds3/out/l2set/entry/ (grid_*.npz, engine_*.npz, pre_sel.json, look*.pkl, lgb_pred.npy)
- settings for D6 group 05: l2vast/ds3/out/l2set/entry_policy_candidate.txt; nightly one-command re-fit: `sh l2vast/ds3/code/l2set/l2set_refit.sh` (rebuilds the learned gate, the grid, the engine table and prints the walk-forward last re-fit).