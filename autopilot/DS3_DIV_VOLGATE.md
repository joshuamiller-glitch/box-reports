# DS3_DIV_VOLGATE - volatility-regime ON/OFF gates (ATR / VIX / first-hour-range terciles) on the live stack's own entries (D3DVG, T-DIVERSIFY section 4), 2026-10-28
Research only; no live / execution / chart change; nothing here is a recommendation to change anything live. Prereg `l2vast/ds3/prereg/D3DVG_prereg.md` sha256 10875cf1c0d28397938aff42357099d020c7e736c187ec5a73c53cde81876720 (DECISIONS.md, before any gate cell was scored), 21 cells in 4 groups (GA ATR, GV VIX, GF first-hour range, GC combos + reference), F = 21. Pre-holdout texts `autopilot/DS3_DIV_VOLGATE_G{A,V,F,C}_PREHOLD.md` (PRE only; 8 looks logged: tracks D3DVG_G*, D3DVG_G*_SPAN2; HOLD and 2023-04..2024-01 read once per group, not re-read). Code `l2vast/ds3/code/dvg/` (dvg_lib, dvg_cells, dvg_run, dvg_gates, dvg_report, dvg_series, dvg_diag, dvg_prereg, dvg_pretext); outputs `l2vast/ds3/out/dvg/` (pre_results.json, final_results.json, series.pkl, report_tables.md). Fees: the stack's live cost (4.84 RT NQ, 0.5 pt slippage per side, engine convention of D3VS/D3BK); 2x cost = engine 2x slippage + commission and 2x sweep cost. Tier words: CONFIRMED = PASS, LEAD = CANDIDATE, DEAD.

## Verdict
**0 CONFIRMED, 0 LEAD, 20 DEAD (+ the VS_ref reference). No ATR, VIX or first-hour-range on/off or 0.5x/1.5x gate improves the live stack; nothing is live-eligible and no rule is written to the line.** Only one cell (A_up, 1.5x in the top ATR tercile) has a positive lot-matched mean delta in both PRE (+190) and HOLD (+7,047), and it is a zero in PRE, its HOLD CI [-7,548, +20,227] spans 0, it fails G3 (maxDD / worst week), and its placebo ranks are 0.69/0.65 in PRE; no cell beats both label placebos at 0.95 in both windows (G4). What the data show is the opposite of the prior: the stack earns its money in the LOW-volatility regimes, so the "trade only mid+top" and "0.5x bottom" gates cut income roughly in proportion to what they remove and are significantly negative.

Headline numbers (weekly $, WF = 2024-02-01..2026-10-16, 142 wk, paired by week vs the unscaled stack, base mean 45,947, SD 136,281, maxDD 601,016, worst week -318,557; base peak 50.0 weighted lots):
- ATR skip-bottom (A_skipB): raw -25,067/wk [-39,455, -11,731] (MDE 19,752), Sharpe -1.13 (annualised delta), maxDD +232,797, trades/wk x0.68. Skip-bottom VIX (V_skipB) -19,412 [-32,779, -6,858], maxDD +211,563. First-hour (F_skipB) -3,536 [-8,778, +1,550] (MDE 7,390), the only one inside its MDE because only 7% of entries are touched. 0.5x bottom: A_half -10,438 [-17,137, -4,166] (MDE 9,219), V_half -8,923 [-15,970, -2,196], F_half -1,367 [-3,838, +1,069].
- 1.5x top under the 50-contract cap: A_up +3,504 [-5,044, +11,822] (MDE 12,099), Sharpe +0.069, maxDD +2,644, SD +6,348, 2,007 entries cut by the cap; V_up +312 [-6,969, +7,289]; F_up -1,880 [-4,583, +721]. Because the base already peaks at exactly 50 weighted lots, every concurrent up-sized entry is cut back, so the cap removes most of the intended leverage (disclosed below); these are inside their MDE and are not distinguishable from zero.
- Combined 0.5x/1.5x (A_hu, V_hu, F_hu): -6,934, -8,611, -3,246 per week raw, all CIs include 0 or are negative.
- Worst-20-weeks: the stack's 20 worst weeks sum to -3,432,946. A_up -3,652,700 (6% worse), V_up -3,414,524, A_half -3,238,515, A_skipB -3,233,400 (A_skipB and A_half shave the worst-20 sum by only ~200k, 6%, while giving up 25k and 10k per week, i.e. 3.6M and 1.5M over the 142 weeks). No gate removes the tail: see the per-cell tables (worst-20 cell / base, and the cell's P&L inside the base's 20 worst weeks).
- Reverse controls (skip TOP tercile): A_skipT lot-matched HOLD +34,473 [+5,586, +62,952] looks like a hit but it is a leverage artifact (c_LM x1.73, peak 86.7 weighted lots, maxDD +447,121, worst week -235,802; raw WF d_Sharpe -0.024; PRE +1,814, placebo PRE 0.55/0.49); V_skipT flips sign between PRE (-12,832) and HOLD (+13,209). They show the gate family does not carry a consistent sign.
- Second holdout (2023-04..2024-01): the lot-matched mean delta is negative for every primary skip/half cell and about zero for the up cells (A_up -87, V_up -1,170); F_up +7,337 is a 44-week reading with MDE 4-8k and F is largely ungated in early 2023.
- 2x cost: the only sign change versus the 1x reading is F_skipB (WF LM -279 -> +57, a zero effect); G8 fails for the cells that were already negative.

## Verdict table (all 21 cells; G1..G8 definitions below)
| cell | what it is | tier | failed gates | gates passed | WF raw d_mean/wk [CI] (MDE) | WF raw d_Sharpe | HOLD LM d_mean (MDE) |
|---|---|---|---|---|---|---|---|
| A_skipB | primary: trade only mid+top | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | 0/8 | -25,067 [-39,455,-11,731] (19,752) | -1.130 | -28,658 (36,875) |
| A_half | primary: 0.5x bottom tercile | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | 0/8 | -10,438 [-17,137,-4,166] (9,219) | -0.350 | -9,399 (15,147) |
| A_up | primary: 1.5x top tercile (50-contract cap) | DEAD | G2,G3,G4,G5,G6,G7 | 2/8 | +3,504 [-5,044,+11,822] (12,099) | +0.069 | +7,047 (19,936) |
| A_hu | primary: 0.5x bottom and 1.5x top | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | 0/8 | -6,934 [-17,828,+3,810] (15,349) | -0.272 | -1,976 (26,972) |
| A_skipT | reverse control: skip TOP tercile | DEAD | G3,G4,G6,G7 | 4/8 | -8,399 [-23,313,+6,003] (20,906) | -0.024 | +34,473 (40,952) |
| V_skipB | primary: trade only mid+top | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | 0/8 | -19,412 [-32,779,-6,858] (18,707) | -0.716 | -18,866 (35,935) |
| V_half | primary: 0.5x bottom tercile | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | 0/8 | -8,923 [-15,970,-2,196] (9,861) | -0.278 | -6,269 (18,147) |
| V_up | primary: 1.5x top tercile (50-contract cap) | DEAD | G1,G2,G3,G4,G5,G6,G7 | 1/8 | +312 [-6,969,+7,289] (10,045) | -0.012 | -363 (14,769) |
| V_hu | primary: 0.5x bottom and 1.5x top | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | 0/8 | -8,611 [-18,549,+1,153] (13,980) | -0.287 | -7,052 (24,224) |
| V_skipT | reverse control: skip TOP tercile | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | 0/8 | -18,562 [-33,328,-4,849] (20,190) | -0.764 | +13,209 (38,766) |
| F_skipB | primary: trade only mid+top | DEAD | G1,G2,G3,G4,G5,G6,G7 | 1/8 | -3,536 [-8,778,+1,550] (7,390) | -0.119 | +4,622 (9,631) |
| F_half | primary: 0.5x bottom tercile | DEAD | G1,G2,G3,G4,G5,G6,G7 | 1/8 | -1,367 [-3,838,+1,069] (3,535) | -0.018 | +2,989 (4,573) |
| F_up | primary: 1.5x top tercile (50-contract cap) | DEAD | G1,G2,G3,G4,G5,G7,G8 | 1/8 | -1,880 [-4,583,+721] (3,839) | -0.143 | -387 (3,886) |
| F_hu | primary: 0.5x bottom and 1.5x top | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | 0/8 | -3,246 [-6,824,+332] (5,159) | -0.164 | +2,562 (5,956) |
| F_skipT | reverse control: skip TOP tercile | DEAD | G1,G3,G4,G5,G6,G7 | 2/8 | -1,482 [-7,146,+4,013] (7,931) | +0.016 | +6,460 (8,758) |
| A_skipB_126 | sensitivity: trailing-126 cut points | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | 0/8 | -21,922 [-35,835,-9,014] (19,435) | -0.923 | -20,559 (36,319) |
| A_hu_126 | sensitivity: trailing-126 cut points | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | 0/8 | -11,699 [-22,252,-1,442] (14,749) | -0.530 | -9,197 (25,788) |
| VS_ref | reference: D3VS S_V8 rule reproduced in this framework (no gate) | REFERENCE | G3,G4,G6,G7 | 4/8 | -2,652 [-5,648,+262] (4,215) | +0.084 | +4,694 (5,556) |
| A_hu_vs | gate x vol-scaled lots (does on/off add to the continuous rule?) | DEAD | G2,G3,G4,G6,G7 | 3/8 | -9,192 [-20,420,+1,632] (15,694) | -0.013 | +20,384 (33,946) |
| V_hu_vs | gate x vol-scaled lots (does on/off add to the continuous rule?) | DEAD | G2,G3,G4,G5,G6,G7 | 2/8 | -13,893 [-25,488,-2,765] (16,055) | -0.218 | +10,720 (40,407) |
| F_hu_vs | gate x vol-scaled lots (does on/off add to the continuous rule?) | DEAD | G1,G3,G4,G5,G6,G7 | 2/8 | -5,077 [-9,475,-683] (6,252) | -0.055 | +8,432 (8,647) |

Gates (prereg; never softened; D3VS gate set with the placebo gate stricter and G8 added): G1 LM mean delta > 0 in PRE and HOLD; G2 HOLD paired CI low > 0; G3 LM maxDD delta <= 0 and worst-week delta >= 0 in PRE and HOLD; G4 shift-label rank AND random-label rank of the LM mean delta >= 0.95 in PRE and HOLD; G5 positive in >= 2 of 2024/25/26 and no year > 60% of WF; G6 second holdout LM mean >= 0, maxDD <= 0, worst >= 0; G7 mean-matched SD, maxDD <= 0 and worst >= 0 in PRE and HOLD; G8 2x-cost WF LM mean > 0. Best-of-F bar: HOLD p <= 0.05/21 = 0.00238. LM = lot-matched (c from PRE lot-second exposure), MM = mean-matched. F_hu_vs has HOLD p 0.002 (below 0.00238) but it is a gate x vol-scaling cell that is DEAD on 6 gates (G1 PRE -4,090, G3, G4, G5, G6, G7), so the best-of-F note is moot.

## Top-10 cells regardless of verdict (failed gates and MDE beside each)
No cell is better than DEAD, so the ranking is by fewest failed gates then WF LM d_Sharpe. The table follows in the embedded tables below under 'Top 10'; the MDE is the HOLD paired MDE of the lot-matched delta (68 weeks). In every row where the CI includes 0 the cell is not distinguishable from zero at its MDE, i.e. inconclusive rather than proof of no effect; in the skip/half cells with CI entirely below 0 (A_skipB, V_skipB, A_half, V_half raw WF) the effect is negative and larger than the MDE, i.e. a real negative.

## What the regimes look like (descriptive, post-look, not gated)
Base stack net P&L per filled entry by tercile of the entry's regime variable, WF window, weighted by W_k (report $; lot-seconds in thousands):
| variable | tercile | entries | net $ / entry | net $ per 1,000 lot-seconds |
|---|---|---|---|---|
| ATR(14)/close | bottom | 4,829 | 737 | 20.1 |
| ATR(14)/close | mid | 5,910 | 220 | 7.3 |
| ATR(14)/close | top | 9,934 | 120 | 5.5 |
| ATR(14)/close | ungated/undefined | 704 | 668 | 28.3 |
| VIX | bottom | 5,741 | 480 | 13.5 |
| VIX | mid | 6,502 | 174 | 6.0 |
| VIX | top | 9,134 | 289 | 13.6 |
| first-hour range (10:30-17:00 entries only) | bottom | 1,349 | 369 | 10.6 |
| first-hour range (10:30-17:00 entries only) | mid | 1,435 | 34 | 1.3 |
| first-hour range (10:30-17:00 entries only) | top | 1,740 | 131 | 7.1 |
| first-hour range (10:30-17:00 entries only) | ungated/undefined | 16,853 | 341 | 12.2 |

Reading: with ATR the bottom tercile holds 27% of entries and earns 55% of the stack's P&L ($737 per entry vs $120 in the top tercile; per lot-second 20.1 vs 5.5). VIX shows the same direction but weaker (bottom $480 vs top $289 per entry; per lot-second 13.5 / 6.0 / 13.6 for bottom / mid / top, i.e. not monotone). The first-hour range is mostly ungated and its terciles are non-monotone (bottom $369, mid $34, top $131 per entry on the ~33% of entries it covers). The stack is a set of breakout / supertrend / Keltner entries: it makes its money when a quiet stretch resolves into a move, and the heavy entry count in the top ATR tercile (44% of entries) is churn with a low edge per entry. That is why "skip bottom" and "0.5x bottom" are the wrong sign, and it is a post-hoc hypothesis (NOT tested here) that the reverse direction (1.5x bottom / 0.5x top) is the one with edge; it needs its own prereg with the placebo and cap tests before anything is believed (see structural question below).

## Difference vs the vol-scaled lots (D3VS, DS3_SIZING_VOLSCALE.md, DEAD)
1. What each one conditions on. D3VS: the book's OWN trailing 8-week P&L standard deviation (a backward-looking realised-P&L statistic), continuous multiplier clip(median-so-far SD / current SD, 0.5, 2), constant for the week, per book. D3DVG: an EXTERNAL market-regime state known before the entry (prior-day ATR, prior-day-close VIX, first-hour range), discrete tercile action per ENTRY (day-level for ATR/VIX), trailing-252-day cut points, 0 / 0.5x / 1x / 1.5x, with a 50-contract cap on the up-sizing.
2. Same footing. VS_ref re-runs the D3VS S_V8 rule in the D3DVG pipeline and reproduces it exactly in raw terms (WFPRE raw -3,664.1 in both; WF raw -2,652/wk, SD -12,170); the lot-matched HOLD delta is +4,694 here vs +4,737 in D3VS only because LM here equalises lot-seconds rather than day-lots. It fails the same gates (G3, G6, G7; here also G4 is n/a for the reference): leverage-after-calm, not risk reduction (HOLD LM SD +9,994, maxDD +80,868, worst -35,355).
3. Does on/off add anything beyond the continuous scaling? No. The gate-on-top cells measured against VS_ref on the same weeks (paired; raw / lot-matched): A_hu_vs - VS_ref WF raw -6,540 [-16,344, +3,184] (SD -14,492, maxDD -172,990 but mean down), LM +6,824 [-6,280, +20,444] with SD +28,972, worst -28,391; V_hu_vs - VS_ref WF raw -11,241 [-21,487, -1,513], LM +4,652 [-10,436, +19,427] with SD +40,891 and maxDD +324,156; F_hu_vs - VS_ref WF raw -2,425 [-5,713, +802], LM -1,325 [-5,150, +2,476]. Every lot-matched increment is inside its MDE (19k-21k, 5.5k) and buys its mean with a larger SD and worse worst week; the raw (capital-neutral) increments are negative. On/off gates add a second layer of the same leverage trade the continuous rule already makes, and the continuous rule is itself DEAD on tails.
4. They overlap: in the weeks where D3VS is active its mean multiplier is 0.96 / 0.92 / 0.86 for bottom / mid / top ATR-tercile weeks (VIX 0.95 / 0.92 / 0.87; first-hour 0.93 / 0.91 / 0.90): the vol-scaler already trims lots in high-vol regimes, the opposite direction to the "1.5x top" gate, and in the direction the per-tercile P&L profile above supports. So the continuous rule captures the little that is capturable and the discrete gates add noise.
5. Scale of evidence. The strongest continuous result (S_V8 HOLD LM +4,737, placebo rank 1.00, p 0.0073) is still not best-of-F. The best gate lot-matched readings (A_up HOLD +7,047 [-7,548, +20,227]; A_skipT +34,473) are respectively inside the MDE and a leverage artifact.

## NT8 terms (for the record; nothing is live-eligible)
A gate-off for an entry would be implemented as: at the signal bar, look up the tercile of the regime variable (ATR: SMA of the prior 14 label-day high-low ranges / prior close, ranked against the prior 252 values; VIX: the prior-day close of the VIX index, ranked against the prior 252 closes - requires an external index feed in NT8; first-hour range: 09:30-10:30 ET high-low / 09:30 open, only for entries from 10:30 ET) and either skip `EnterLong/Short` (gate off), or submit it with Quantity x0.5 / x1.5 (rounded, capped so the account's open contracts stay <= 50). Because no cell passed, no rule is specified to the line.

## Disclosures (read before trusting any number)
1. PB (PB3B_R5_P1) cannot be regenerated: skip-cell PB rows are masked after generation, so a skipped PB entry does not free the book for a later signal (the same shadowing the D3BK report found: it makes PB skip cells slightly pessimistic). ST, HM, WT, KB, SM are regenerated with the correct busy chain. Size cells (0.5x/1.5x) do not touch the chain.
2. 50-contract cap pass is sequential in entry-time order across all six books using pre-lock scheduled rows (conservative: locks may later cancel rows); the base peak is exactly 50.0, so up-sized entries are always cut back (A_up: 2,007 rows, V_up 1,862, F_up 460), later base-size entries can be cut to near zero when earlier up-sized positions are open (crowd-out, part of the rule). The vol-scaled combination cells do NOT enforce the cap (as D3VS; peaks 54-67 weighted lots raw). Lot-matched and mean-matched bases ignore the cap (c_LM x peak up to 87 for A_skipT, 117 for V_hu_vs): they are research comparisons, not tradable at 50 contracts.
3. The first-hour gate touches only entries between 10:30 and 17:00 ET of the same label day (about 21-36% of entries by book); entries before 10:30 and the 18:00+ sessions are ungated. F terciles are undefined before 2023-04-06 (needs 40 days of history), so early X weeks are ungated for F. ATR and VIX have full history (ATR from days_NQ.csv 2013+, VIX 2009+). Label days after 2026-10-16 get no label and no bars after 2026-10-16 were used.
4. The expanding-window cut-point variant was examined for degeneracy BEFORE scoring (no bottom-tercile days in 2023+ since ATR% rose against a 2013+ history) and replaced in the prereg by a trailing-126 sensitivity (A_skipB_126, A_hu_126). This used only label counts, no P&L.
5. Mean-matched basis: c_MM could not be solved inside [0.2, 3.0] for V_skipT (marked n/a, G7 fails); c_MM for the other cells is 0.97-1.82. LM c ranges x1.00-x1.74.
6. LM equalises PRE lot-seconds (sum of weighted lots x holding seconds), not D3VS's day-lots; VS_ref raw is identical, LM differs by ~1% (+4,694 vs +4,737 HOLD).
7. Bug (disclosed, fixed): the first `dvg_run.py final` launch ran as stage 'pre' because an imported module resets `sys.argv` and the stage was read after the imports. It recomputed WFPRE only (seeded, same definitions) and overwrote pre_results.json with identical numbers; no HOLD/X/WF number was computed or read before the real final run. STAGE is now read before the imports. Log line in DECISIONS.md.
8. The per-tercile descriptive table and the vol-scaler/tercile overlap were computed after the logged looks and are descriptive; they did not select, change or add any cell. The reverse-direction idea (1.5x bottom) is NOT scored here.
9. Gates differ from D3VS in two prereg'd ways: G4 requires both placebos (shift and random) separately instead of the pooled rank; G8 (2x cost) added. VS_ref is not placebo-gated (no label); its D3VS placebo result stands.
10. Terciles use trailing windows, so the share of entries per tercile is not 1/3 (ATR: 27% / 25% / 44% of entries bottom / mid / top; more signals fire on high-ATR days).
11. Weekly paired MDEs are large relative to the skip/half effects of this size (MDE 5k-20k lot-matched, 3.5k-20k raw); where a cell's CI includes 0 it is inconclusive, not a proven null. The raw WF CIs of A_skipB, V_skipB, A_half, V_half, V_skipT exclude 0 on the negative side.

## Structural question for MORNING (not blocking)
Should a pre-registered follow-up test the reverse direction suggested by the descriptive table (1.5x in the BOTTOM ATR tercile / 0.5x in the top, under the 50-contract cap, with the same placebos), given it was suggested by post-look data and therefore needs the full gate set and a fresh second-holdout look? Default if no answer: not run.

## All 21 cells (LM = lot-matched; weekly $; PRE 75 wk, HOLD 68 wk, X 44 wk)

| cell | tier | failed gates | c_LM | LM d_mean PRE / HOLD / X | HOLD CI iid (MDE) | HOLD p | placebo shift/random PRE / HOLD | HOLD LM d_SD | HOLD LM d_maxDD | HOLD LM d_worst | WF LM d_mean | WF LM d_mean at 2x cost |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_skipB | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | x1.25 | -11,750 / -28,658 / -6,987 | [-54,535,-3,522] (36,875) | 0.988 | 0.24/0.17 / 0.07/0.05 | -11,338 | +437,944 | +2,121 | -19,929 | -18,121 |
| A_half | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | x1.09 | -4,935 / -9,399 / -7,537 | [-20,235,+777] (15,147) | 0.964 | 0.39/0.27 / 0.11/0.08 | -8,280 | -90,843 | +40,781 | -7,108 | -6,042 |
| A_up | DEAD | G2,G3,G4,G5,G6,G7 | x1.00 | +190 / +7,047 / -87 | [-7,548,+20,227] (19,936) | 0.157 | 0.69/0.65 / 0.82/0.95 | +11,456 | +2,232 | +202 | +3,475 | +4,024 |
| A_hu | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | x1.09 | -5,059 / -1,976 / -7,631 | [-21,285,+16,513] (26,972) | 0.584 | 0.43/0.51 / 0.47/0.35 | +6,872 | -17,071 | +3,967 | -3,618 | -2,271 |
| A_skipT | DEAD | G3,G4,G6,G7 | x1.73 | +1,814 / +34,473 / +12,047 | [+5,586,+62,952] (40,952) | 0.008 | 0.55/0.49 / 0.97/1.00 | +76,074 | +447,121 | -235,802 | +17,466 | +16,101 |
| V_skipB | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | x1.38 | -758 / -18,866 / -12,805 | [-43,940,+5,691] (35,935) | 0.934 | 0.58/0.51 / 0.33/0.13 | -3,985 | -68,419 | -30,893 | -9,435 | -8,563 |
| V_half | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | x1.14 | -1,598 / -6,269 / -8,728 | [-18,712,+6,236] (18,147) | 0.837 | 0.58/0.59 / 0.37/0.23 | +781 | +50,267 | +13,629 | -3,846 | -3,318 |
| V_up | DEAD | G1,G2,G3,G4,G5,G6,G7 | x1.01 | +1,557 / -363 / -1,170 | [-10,961,+9,585] (14,769) | 0.524 | 0.85/0.71 / 0.31/0.33 | +5,659 | +27,558 | -2,468 | +648 | +1,317 |
| V_hu | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | x1.15 | -401 / -7,052 / -10,166 | [-24,251,+9,696] (24,224) | 0.798 | 0.82/0.71 / 0.34/0.20 | +7,389 | +122,102 | +10,940 | -3,589 | -2,740 |
| V_skipT | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | x1.72 | -12,832 / +13,209 / +8,773 | [-13,907,+39,776] (38,766) | 0.170 | 0.14/0.15 / 0.65/0.85 | +87,202 | +441,544 | -232,884 | -452 | -1,800 |
| F_skipB | DEAD | G1,G2,G3,G4,G5,G6,G7 | x1.08 | -4,719 / +4,622 / -8,124 | [-2,245,+11,453] (9,631) | 0.088 | 0.05/0.13 / 0.63/0.59 | +5,984 | +7,605 | +1,325 | -279 | +57 |
| F_half | DEAD | G1,G2,G3,G4,G5,G6,G7 | x1.03 | -2,434 / +2,989 / -4,705 | [-278,+6,220] (4,573) | 0.036 | 0.11/0.13 / 0.71/0.75 | +2,033 | +1,390 | +2,066 | +146 | +243 |
| F_up | DEAD | G1,G2,G3,G4,G5,G7,G8 | x1.00 | -3,400 / -387 / +7,337 | [-3,104,+2,271] (3,886) | 0.603 | 0.15/0.15 / 0.63/0.74 | +289 | -4,228 | +745 | -1,981 | -1,575 |
| F_hu | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | x1.03 | -5,973 / +2,562 / +2,869 | [-1,588,+6,743] (5,956) | 0.111 | 0.09/0.03 / 0.76/0.82 | +2,292 | -2,976 | +2,832 | -1,927 | -1,430 |
| F_skipT | DEAD | G1,G3,G4,G5,G6,G7 | x1.07 | -2,357 / +6,460 / -7,133 | [+448,+12,517] (8,758) | 0.017 | 0.36/0.33 / 0.79/0.84 | +10,685 | +28,865 | -23,866 | +1,849 | +1,649 |
| A_skipB_126 | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | x1.31 | -8,634 / -20,559 / -5,868 | [-46,094,+4,169] (36,319) | 0.950 | 0.23/0.35 / 0.08/0.07 | -9,317 | +11,333 | -14,851 | -14,405 | -13,543 |
| A_hu_126 | DEAD | G1,G2,G3,G4,G5,G6,G7,G8 | x1.12 | -7,065 / -9,197 / -11 | [-27,797,+8,353] (25,788) | 0.845 | 0.30/0.33 / 0.05/0.09 | +6,328 | +178,674 | -2,532 | -8,135 | -7,563 |
| VS_ref | REFERENCE | G3,G4,G6,G7 | x1.14 | +1,807 / +4,694 / +3,577 | [+919,+8,571] (5,556) | 0.007 | nan/nan / nan/nan | +9,994 | +80,868 | -35,355 | +3,202 | +3,013 |
| A_hu_vs | DEAD | G2,G3,G4,G6,G7 | x1.55 | +502 / +20,384 / -5,822 | [-3,366,+43,453] (33,946) | 0.046 | 0.78/0.65 / 0.95/1.00 | +55,973 | +71,777 | -63,745 | +10,027 | +9,344 |
| V_hu_vs | DEAD | G2,G3,G4,G5,G6,G7 | x1.74 | +5,152 / +10,720 / -7,197 | [-18,220,+37,989] (40,407) | 0.229 | 0.95/0.89 / 0.87/0.88 | +76,781 | +405,024 | -74,902 | +7,855 | +3,760 |
| F_hu_vs | DEAD | G1,G3,G4,G5,G6,G7 | x1.17 | -4,090 / +8,432 / +6,629 | [+2,677,+14,624] (8,647) | 0.002 | 0.08/0.05 / 0.91/0.95 | +14,481 | +94,210 | -46,453 | +1,877 | +2,199 |

## Top 10 by tier, then fewest failed gates, then WF LM d_Sharpe (regardless of verdict)

| cell | tier | failed gates | c_LM | LM d_mean PRE / HOLD / X | HOLD CI iid (MDE) | HOLD p | placebo shift/random PRE / HOLD | HOLD LM d_SD | HOLD LM d_maxDD | HOLD LM d_worst | WF LM d_mean | WF LM d_mean at 2x cost |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_skipT | DEAD | G3,G4,G6,G7 | x1.73 | +1,814 / +34,473 / +12,047 | [+5,586,+62,952] (40,952) | 0.008 | 0.55/0.49 / 0.97/1.00 | +76,074 | +447,121 | -235,802 | +17,466 | +16,101 |
| A_hu_vs | DEAD | G2,G3,G4,G6,G7 | x1.55 | +502 / +20,384 / -5,822 | [-3,366,+43,453] (33,946) | 0.046 | 0.78/0.65 / 0.95/1.00 | +55,973 | +71,777 | -63,745 | +10,027 | +9,344 |
| A_up | DEAD | G2,G3,G4,G5,G6,G7 | x1.00 | +190 / +7,047 / -87 | [-7,548,+20,227] (19,936) | 0.157 | 0.69/0.65 / 0.82/0.95 | +11,456 | +2,232 | +202 | +3,475 | +4,024 |
| F_skipT | DEAD | G1,G3,G4,G5,G6,G7 | x1.07 | -2,357 / +6,460 / -7,133 | [+448,+12,517] (8,758) | 0.017 | 0.36/0.33 / 0.79/0.84 | +10,685 | +28,865 | -23,866 | +1,849 | +1,649 |
| F_hu_vs | DEAD | G1,G3,G4,G5,G6,G7 | x1.17 | -4,090 / +8,432 / +6,629 | [+2,677,+14,624] (8,647) | 0.002 | 0.08/0.05 / 0.91/0.95 | +14,481 | +94,210 | -46,453 | +1,877 | +2,199 |
| V_hu_vs | DEAD | G2,G3,G4,G5,G6,G7 | x1.74 | +5,152 / +10,720 / -7,197 | [-18,220,+37,989] (40,407) | 0.229 | 0.95/0.89 / 0.87/0.88 | +76,781 | +405,024 | -74,902 | +7,855 | +3,760 |
| V_up | DEAD | G1,G2,G3,G4,G5,G6,G7 | x1.01 | +1,557 / -363 / -1,170 | [-10,961,+9,585] (14,769) | 0.524 | 0.85/0.71 / 0.31/0.33 | +5,659 | +27,558 | -2,468 | +648 | +1,317 |
| F_half | DEAD | G1,G2,G3,G4,G5,G6,G7 | x1.03 | -2,434 / +2,989 / -4,705 | [-278,+6,220] (4,573) | 0.036 | 0.11/0.13 / 0.71/0.75 | +2,033 | +1,390 | +2,066 | +146 | +243 |
| F_skipB | DEAD | G1,G2,G3,G4,G5,G6,G7 | x1.08 | -4,719 / +4,622 / -8,124 | [-2,245,+11,453] (9,631) | 0.088 | 0.05/0.13 / 0.63/0.59 | +5,984 | +7,605 | +1,325 | -279 | +57 |
| F_up | DEAD | G1,G2,G3,G4,G5,G7,G8 | x1.00 | -3,400 / -387 / +7,337 | [-3,104,+2,271] (3,886) | 0.603 | 0.15/0.15 / 0.63/0.74 | +289 | -4,228 | +745 | -1,981 | -1,575 |

## Full tables


#### A_skipT  (reverse control: skip TOP tercile) - DEAD; failed gates: G3,G4,G6,G7
c_LM 1.733, c_MM 1.653, raw peak weighted lots 50.0 (x c_LM = 86.7), entries cut by the 50-cap 0, trades per book (cell / base): ST 2836/4506, HM 2563/4129, WT 4181/6636, KB 3036/4809, SM 1296/2037, PB 2836/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -16,845 [-39,768,+5,124] (32,539) | -34,038 | -103,125 | +29,946 | -0.401 | -1,233,864 / -2,304,797 | -1,089,876 (base -2,304,797) |  |
|  |  |  | LM | +1,814 [-27,086,+30,459] (41,955) | +36,936 | +178,528 | -176,356 | -0.455 | -2,173,644 / -2,304,797 | -1,915,677 (base -2,304,797) | 0.55/0.49 |
|  |  |  | MM | +0 [-27,906,+27,547] (40,419) | +29,214 | +146,400 | -153,220 | -0.442 | -2,064,862 / -2,304,797 | -1,820,835 (base -2,304,797) | 0.87/0.88 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | +1,041 [-16,640,+17,727] (24,726) | -15,462 | +0 | +0 | +0.358 | -1,499,643 / -2,193,122 | -1,362,058 (base -2,193,122) |  |
|  |  |  | LM | +34,473 [+5,586,+62,952] (40,952) | +76,074 | +447,121 | -235,802 | +0.298 | -2,638,701 / -2,193,122 | -2,391,062 (base -2,193,122) | 0.97/1.00 |
|  |  |  | MM | +31,159 [+3,931,+57,754] (38,315) | +66,149 | +397,134 | -209,635 | +0.312 | -2,507,431 / -2,193,122 | -2,273,359 (base -2,193,122) | 0.96/0.98 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -605 [-1,815,+0] (1,694) | -207 | +0 | +0 | -0.036 | -1,677,814 / -1,677,814 | -1,677,814 (base -1,677,814) |  |
|  |  |  | LM | +12,047 [-12,235,+36,134] (34,764) | +82,188 | +418,644 | -117,388 | -0.110 | -2,945,490 / -1,677,814 | -2,945,490 (base -1,677,814) | 0.81/0.87 |
|  |  |  | MM | +11,019 [-10,664,+32,494] (30,976) | +73,202 | +370,418 | -104,154 | -0.092 | -2,800,202 / -1,677,814 | -2,800,202 (base -1,677,814) | 0.80/0.87 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -8,399 [-23,313,+6,003] (20,906) | -23,809 | -0 | +0 | -0.024 | -2,378,978 / -3,432,946 | -1,921,004 (base -3,432,946) |  |
|  |  |  | LM | +17,466 [-3,481,+38,005] (29,790) | +58,238 | +447,121 | -235,802 | -0.080 | -4,169,390 / -3,432,946 | -3,364,142 (base -3,432,946) | 0.95/0.97 |
|  |  |  | MM | +14,921 [-5,129,+34,401] (28,335) | +49,335 | +397,134 | -209,635 | -0.067 | -3,965,761 / -3,432,946 | -3,200,459 (base -3,432,946) | 0.96/0.98 |

By year (summed weekly deltas, weeks): raw {2024: -63,596 (49), 2025: -1,083,532 (52), 2026: -45,461 (41)}; LM {2024: +1,247,536, 2025: +91,769, 2026: +1,140,900}; 2023 (X weeks) raw -26,619 (39 wk), LM +308,635.
2x cost (WF, vs the 2x-cost base): raw -1,545/wk (maxDD -71,732), LM +16,101/wk (maxDD +402,891); HOLD raw +6,895, LM +30,879.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -3,133, HM -244, WT -60, KB -2,219, SM -1,254, PB -1,489; HOLD: ST -995, HM -132, WT +1,433, KB +1,898, SM -381, PB -783


#### A_hu_vs  (gate x vol-scaled lots (does on/off add to the continuous rule?)) - DEAD; failed gates: G2,G3,G4,G6,G7
c_LM 1.551, c_MM 1.532, raw peak weighted lots 64.9 (x c_LM = 100.6), entries cut by the 50-cap 2007, trades per book (cell / base): ST 4350/4506, HM 4022/4129, WT 6361/6636, KB 4641/4809, SM 1883/2037, PB 4282/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -14,951 [-29,561,-626] (20,685) | -40,570 | -165,354 | +86,994 | -0.104 | -1,640,665 / -2,304,797 | -1,384,525 (base -2,304,797) |  |
|  |  |  | LM | +502 [-13,124,+14,657] (20,072) | +9,115 | +7,969 | -34,845 | -0.132 | -2,555,767 / -2,304,797 | -2,152,931 (base -2,304,797) | 0.78/0.65 |
|  |  |  | MM | +0 [-13,528,+13,958] (19,879) | +7,403 | +1,860 | -30,595 | -0.130 | -2,523,484 / -2,304,797 | -2,125,876 (base -2,304,797) | 0.63/0.60 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -2,705 [-19,005,+12,909] (23,135) | -13,973 | -173,344 | +72,195 | +0.112 | -1,855,355 / -2,193,122 | -1,276,684 (base -2,193,122) |  |
|  |  |  | LM | +20,384 [-3,366,+43,453] (33,946) | +55,973 | +71,777 | -63,745 | +0.059 | -2,912,718 / -2,193,122 | -2,014,521 (base -2,193,122) | 0.95/1.00 |
|  |  |  | MM | +19,638 [-3,673,+42,357] (33,349) | +53,546 | +62,919 | -59,008 | +0.062 | -2,874,749 / -2,193,122 | -1,987,733 (base -2,193,122) | 0.83/0.85 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -11,012 [-27,520,+5,241] (23,826) | -41,663 | -173,034 | +3,346 | -0.344 | -1,099,350 / -1,677,814 | -1,036,798 (base -1,677,814) |  |
|  |  |  | LM | -5,822 [-19,556,+8,121] (20,004) | -2,543 | +37,342 | -82,337 | -0.350 | -1,706,547 / -1,677,814 | -1,609,772 (base -1,677,814) | 0.24/0.25 |
|  |  |  | MM | -5,995 [-19,646,+7,900] (19,921) | -3,902 | +29,954 | -79,280 | -0.350 | -1,685,358 / -1,677,814 | -1,589,744 (base -1,677,814) | 0.25/0.25 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -9,192 [-20,420,+1,632] (15,694) | -26,661 | -173,344 | +72,195 | -0.013 | -2,644,239 / -3,432,946 | -2,290,522 (base -3,432,946) |  |
|  |  |  | LM | +10,027 [-3,693,+24,039] (19,535) | +33,585 | +71,777 | -63,745 | -0.055 | -4,132,048 / -3,432,946 | -3,571,853 (base -3,432,946) | 0.97/0.97 |
|  |  |  | MM | +9,404 [-4,141,+23,192] (19,243) | +31,500 | +62,919 | -59,008 | -0.052 | -4,079,203 / -3,432,946 | -3,526,648 (base -3,432,946) | 0.83/0.85 |

By year (summed weekly deltas, weeks): raw {2024: -635,222 (49), 2025: -557,810 (52), 2026: -112,187 (41)}; LM {2024: +58,614, 2025: +623,382, 2026: +741,768}; 2023 (X weeks) raw -446,327 (39 wk), LM -369,234.
2x cost (WF, vs the 2x-cost base): raw -3,324/wk (maxDD -128,559), LM +9,344/wk (maxDD +203,591); HOLD raw +2,192, LM +17,551.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -845, HM -3,821, WT +213, KB -2,880, SM -855, PB -970; HOLD: ST -452, HM -2,406, WT +1,448, KB -174, SM -1,038, PB -26


#### A_up  (primary: 1.5x top tercile (50-contract cap)) - DEAD; failed gates: G2,G3,G4,G5,G6,G7
c_LM 0.999, c_MM 0.995, raw peak weighted lots 50.0 (x c_LM = 50.0), entries cut by the 50-cap 2007, trades per book (cell / base): ST 3958/4506, HM 3746/4129, WT 5683/6636, KB 4203/4809, SM 1865/2037, PB 3963/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | +216 [-9,583,+9,636] (14,110) | +1,004 | +45,933 | +2,603 | -0.007 | -2,494,508 / -2,304,797 | -2,295,302 (base -2,304,797) |  |
|  |  |  | LM | +190 [-9,607,+9,612] (14,105) | +920 | +45,590 | +2,799 | -0.007 | -2,492,890 / -2,304,797 | -2,293,811 (base -2,304,797) | 0.69/0.65 |
|  |  |  | MM | -0 [-9,778,+9,425] (14,069) | +311 | +43,087 | +4,225 | -0.006 | -2,481,086 / -2,304,797 | -2,282,940 (base -2,304,797) | 0.17/0.14 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | +7,080 [-7,529,+20,280] (19,948) | +11,553 | +2,644 | +0 | +0.152 | -2,438,802 / -2,193,122 | -1,703,780 (base -2,193,122) |  |
|  |  |  | LM | +7,047 [-7,548,+20,227] (19,936) | +11,456 | +2,232 | +202 | +0.152 | -2,437,212 / -2,193,122 | -1,702,655 (base -2,193,122) | 0.82/0.95 |
|  |  |  | MM | +6,809 [-7,718,+19,953] (19,847) | +10,750 | -777 | +1,672 | +0.152 | -2,425,618 / -2,193,122 | -1,694,452 (base -2,193,122) | 0.71/0.79 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -74 [-221,+0] (206) | -33 | +0 | +0 | -0.004 | -1,677,814 / -1,677,814 | -1,677,814 (base -1,677,814) |  |
|  |  |  | LM | -87 [-247,+5] (210) | -104 | -350 | +100 | -0.004 | -1,676,752 / -1,677,814 | -1,676,752 (base -1,677,814) | 0.47/0.50 |
|  |  |  | MM | -181 [-426,+41] (334) | -625 | -2,904 | +826 | -0.004 | -1,669,005 / -1,677,814 | -1,669,005 (base -1,677,814) | 0.41/0.43 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | +3,504 [-5,044,+11,822] (12,099) | +6,348 | +2,644 | +0 | +0.069 | -3,652,700 / -3,432,946 | -3,288,684 (base -3,432,946) |  |
|  |  |  | LM | +3,475 [-5,066,+11,788] (12,093) | +6,258 | +2,232 | +202 | +0.069 | -3,650,340 / -3,432,946 | -3,286,567 (base -3,432,946) | 0.84/0.89 |
|  |  |  | MM | +3,261 [-5,256,+11,541] (12,048) | +5,599 | -777 | +1,672 | +0.070 | -3,633,136 / -3,432,946 | -3,271,133 (base -3,432,946) | 0.71/0.79 |

By year (summed weekly deltas, weeks): raw {2024: +26,637 (49), 2025: -183,393 (52), 2026: +654,366 (41)}; LM {2024: +25,469, 2025: -184,967, 2026: +652,939}; 2023 (X weeks) raw -3,241 (39 wk), LM -3,612.
2x cost (WF, vs the 2x-cost base): raw +4,041/wk (maxDD +167,950), LM +4,024/wk (maxDD +167,339); HOLD raw +7,472, LM +7,451.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST +2,096, HM -1,004, WT +409, KB +173, SM +644, PB +1,390; HOLD: ST +2,261, HM +1,935, WT -66, KB +1,299, SM -80, PB +1,919


#### F_skipT  (reverse control: skip TOP tercile) - DEAD; failed gates: G1,G3,G4,G5,G6,G7
c_LM 1.075, c_MM 1.136, raw peak weighted lots 50.0 (x c_LM = 53.7), entries cut by the 50-cap 0, trades per book (cell / base): ST 4144/4506, HM 3765/4129, WT 6119/6636, KB 4352/4809, SM 1881/2037, PB 4234/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -5,268 [-14,606,+4,016] (13,236) | -10,976 | +82,263 | +63,797 | -0.095 | -2,216,468 / -2,304,797 | -2,100,031 (base -2,304,797) |  |
|  |  |  | LM | -2,357 [-11,579,+6,590] (13,236) | -1,970 | +124,215 | +45,602 | -0.095 | -2,382,522 / -2,304,797 | -2,257,362 (base -2,304,797) | 0.36/0.33 |
|  |  |  | MM | +0 [-9,544,+9,202] (13,697) | +5,321 | +158,177 | +30,872 | -0.095 | -2,516,950 / -2,304,797 | -2,384,728 (base -2,304,797) | 0.85/0.78 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | +2,715 [-2,614,+8,057] (7,689) | +114 | -15,036 | +0 | +0.137 | -2,149,882 / -2,193,122 | -2,093,294 (base -2,193,122) |  |
|  |  |  | LM | +6,460 [+448,+12,517] (8,758) | +10,685 | +28,865 | -23,866 | +0.137 | -2,310,948 / -2,193,122 | -2,250,120 (base -2,193,122) | 0.79/0.84 |
|  |  |  | MM | +9,492 [+2,278,+16,780] (10,479) | +19,243 | +64,404 | -43,186 | +0.137 | -2,441,338 / -2,193,122 | -2,377,078 (base -2,193,122) | 0.81/0.85 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -8,073 [-21,329,+4,945] (19,268) | +5,277 | +167,175 | -69,531 | -0.552 | -1,853,757 / -1,677,814 | -1,779,806 (base -1,677,814) |  |
|  |  |  | LM | -7,133 [-21,169,+6,983] (20,719) | +14,122 | +221,137 | -86,525 | -0.552 | -1,992,638 / -1,677,814 | -1,913,146 (base -1,677,814) | 0.07/0.11 |
|  |  |  | MM | -6,372 [-21,374,+8,649] (22,286) | +21,282 | +264,821 | -100,282 | -0.552 | -2,105,068 / -1,677,814 | -2,021,091 (base -1,677,814) | 0.07/0.11 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -1,482 [-7,146,+4,013] (7,931) | -5,248 | -15,036 | +0 | +0.016 | -3,237,193 / -3,432,946 | -3,027,027 (base -3,432,946) |  |
|  |  |  | LM | +1,849 [-3,971,+7,464] (8,194) | +4,568 | +28,865 | -23,866 | +0.016 | -3,479,718 / -3,432,946 | -3,253,807 (base -3,432,946) | 0.58/0.57 |
|  |  |  | MM | +4,546 [-1,768,+10,689] (8,852) | +12,515 | +64,404 | -43,186 | +0.016 | -3,676,053 / -3,432,946 | -3,437,396 (base -3,432,946) | 0.81/0.85 |

By year (summed weekly deltas, weeks): raw {2024: -142,020 (49), 2025: -119,977 (52), 2026: +51,497 (41)}; LM {2024: -6,654, 2025: +81,612, 2026: +187,577}; 2023 (X weeks) raw -373,537 (39 wk), LM -357,325.
2x cost (WF, vs the 2x-cost base): raw -558/wk (maxDD +42,695), LM +1,649/wk (maxDD +98,447); HOLD raw +3,396, LM +5,978.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -1,172, HM +551, WT +1,258, KB -1,552, SM +65, PB -633; HOLD: ST -1,790, HM +1,378, WT +1,797, KB -404, SM +893, PB +840


#### F_hu_vs  (gate x vol-scaled lots (does on/off add to the continuous rule?)) - DEAD; failed gates: G1,G3,G4,G5,G6,G7
c_LM 1.172, c_MM 1.295, raw peak weighted lots 57.6 (x c_LM = 67.5), entries cut by the 50-cap 460, trades per book (cell / base): ST 4469/4506, HM 4122/4129, WT 6582/6636, KB 4751/4809, SM 2023/2037, PB 4543/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -9,899 [-16,592,-3,260] (9,678) | -16,840 | -92,851 | +23,463 | -0.267 | -2,023,036 / -2,304,797 | -1,985,155 (base -2,304,797) |  |
|  |  |  | LM | -4,090 [-10,085,+1,835] (8,711) | +2,816 | -26,254 | -25,441 | -0.271 | -2,372,166 / -2,304,797 | -2,327,631 (base -2,304,797) | 0.08/0.05 |
|  |  |  | MM | -0 [-7,265,+7,297] (10,612) | +16,866 | +21,536 | -60,523 | -0.276 | -2,623,017 / -2,304,797 | -2,573,481 (base -2,304,797) | 0.12/0.11 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | +317 [-4,650,+5,337] (7,158) | -8,342 | -8,079 | +7,153 | +0.169 | -1,924,806 / -2,193,122 | -1,901,101 (base -2,193,122) |  |
|  |  |  | LM | +8,432 [+2,677,+14,624] (8,647) | +14,481 | +94,210 | -46,453 | +0.166 | -2,257,452 / -2,193,122 | -2,229,451 (base -2,193,122) | 0.91/0.95 |
|  |  |  | MM | +14,161 [+5,582,+23,182] (12,853) | +30,793 | +168,143 | -84,866 | +0.161 | -2,497,127 / -2,193,122 | -2,465,966 (base -2,193,122) | 0.96/0.99 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | +2,742 [-7,903,+11,994] (14,475) | -3,415 | -30,719 | +0 | +0.222 | -1,556,293 / -1,677,814 | -1,449,696 (base -1,677,814) |  |
|  |  |  | LM | +6,629 [-5,638,+17,781] (16,874) | +15,369 | +59,881 | -27,078 | +0.215 | -1,826,066 / -1,677,814 | -1,701,674 (base -1,677,814) | 0.59/0.68 |
|  |  |  | MM | +9,330 [-5,271,+22,941] (20,366) | +28,756 | +124,938 | -46,441 | +0.208 | -2,020,080 / -1,677,814 | -1,883,071 (base -1,677,814) | 0.85/0.81 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -5,077 [-9,475,-683] (6,252) | -12,269 | -8,079 | +7,153 | -0.055 | -2,946,032 / -3,432,946 | -2,911,494 (base -3,432,946) |  |
|  |  |  | LM | +1,877 [-2,596,+6,459] (6,372) | +9,060 | +94,210 | -46,453 | -0.058 | -3,454,095 / -3,432,946 | -3,413,421 (base -3,432,946) | 0.41/0.45 |
|  |  |  | MM | +6,781 [+905,+12,980] (8,512) | +24,304 | +168,143 | -84,866 | -0.063 | -3,818,795 / -3,432,946 | -3,773,981 (base -3,432,946) | 0.96/0.99 |

By year (summed weekly deltas, weeks): raw {2024: -497,325 (49), 2025: -200,354 (52), 2026: -23,194 (41)}; LM {2024: -251,698, 2025: +244,421, 2026: +273,870}; 2023 (X weeks) raw +172,693 (39 wk), LM +298,860.
2x cost (WF, vs the 2x-cost base): raw -2,408/wk (maxDD -86,013), LM +2,199/wk (maxDD +20,067); HOLD raw +1,427, LM +6,886.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -1,604, HM -1,080, WT +183, KB -1,467, SM -515, PB -578; HOLD: ST -382, HM -253, WT +1,163, KB -206, SM -630, PB +638


#### V_hu_vs  (gate x vol-scaled lots (does on/off add to the continuous rule?)) - DEAD; failed gates: G2,G3,G4,G5,G6,G7
c_LM 1.743, c_MM 1.546, raw peak weighted lots 67.0 (x c_LM = 116.7), entries cut by the 50-cap 1862, trades per book (cell / base): ST 4566/4506, HM 4130/4129, WT 6574/6636, KB 4788/4809, SM 1901/2037, PB 4510/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -15,368 [-30,397,-324] (21,219) | -49,689 | -161,224 | +91,269 | +0.119 | -1,352,382 / -2,304,797 | -1,260,646 (base -2,304,797) |  |
|  |  |  | LM | +5,152 [-7,677,+18,219] (18,583) | +10,543 | +74,509 | -68,757 | +0.082 | -2,372,799 / -2,304,797 | -2,204,174 (base -2,304,797) | 0.95/0.89 |
|  |  |  | MM | -0 [-12,142,+12,225] (17,302) | -5,303 | +11,868 | -26,368 | +0.102 | -2,098,517 / -2,304,797 | -1,951,607 (base -2,304,797) | 0.08/0.12 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -12,062 [-28,752,+3,989] (23,921) | -15,974 | -24,164 | +92,985 | -0.387 | -2,191,572 / -2,193,122 | -1,654,930 (base -2,193,122) |  |
|  |  |  | LM | +10,720 [-18,220,+37,989] (40,407) | +76,781 | +405,024 | -74,902 | -0.498 | -3,895,484 / -2,193,122 | -2,949,948 (base -2,193,122) | 0.87/0.88 |
|  |  |  | MM | +5,283 [-19,093,+28,423] (34,069) | +52,315 | +291,272 | -30,211 | -0.457 | -3,432,296 / -2,193,122 | -2,595,878 (base -2,193,122) | 0.43/0.52 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -12,805 [-30,627,+5,101] (25,587) | -46,696 | -213,473 | +58,080 | -0.466 | -999,423 / -1,677,814 | -972,190 (base -1,677,814) |  |
|  |  |  | LM | -7,197 [-21,611,+8,028] (21,491) | +2,243 | +38,713 | -16,162 | -0.477 | -1,745,331 / -1,677,814 | -1,695,138 (base -1,677,814) | 0.17/0.23 |
|  |  |  | MM | -8,624 [-22,893,+6,025] (20,740) | -10,672 | -27,991 | +3,680 | -0.471 | -1,547,102 / -1,677,814 | -1,503,582 (base -1,677,814) | 0.11/0.19 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -13,893 [-25,488,-2,765] (16,055) | -31,852 | -24,164 | +92,985 | -0.218 | -2,653,736 / -3,432,946 | -2,347,697 (base -3,432,946) |  |
|  |  |  | LM | +7,855 [-7,565,+23,083] (21,615) | +45,503 | +405,024 | -74,902 | -0.297 | -4,691,201 / -3,432,946 | -4,121,663 (base -3,432,946) | 0.93/0.97 |
|  |  |  | MM | +2,530 [-10,958,+15,533] (18,652) | +25,119 | +291,272 | -30,211 | -0.265 | -4,142,546 / -3,432,946 | -3,646,445 (base -3,432,946) | 0.43/0.52 |

By year (summed weekly deltas, weeks): raw {2024: -691,765 (49), 2025: -1,049,342 (52), 2026: -231,746 (41)}; LM {2024: +209,726, 2025: +131,154, 2026: +774,477}; 2023 (X weeks) raw -529,707 (39 wk), LM -491,140.
2x cost (WF, vs the 2x-cost base): raw -8,345/wk (maxDD -51,272), LM +3,760/wk (maxDD +436,547); HOLD raw -7,996, LM +2,672.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -2,664, HM -2,179, WT +143, KB -4,424, SM -679, PB -4,020; HOLD: ST -4,359, HM -504, WT +1,580, KB -2,138, SM -262, PB -6,241


#### V_up  (primary: 1.5x top tercile (50-contract cap)) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7
c_LM 1.008, c_MM 0.971, raw peak weighted lots 50.0 (x c_LM = 50.4), entries cut by the 50-cap 1862, trades per book (cell / base): ST 4016/4506, HM 3731/4129, WT 5731/6636, KB 4241/4809, SM 1882/2037, PB 4039/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | +1,232 [-8,339,+10,700] (13,683) | -1,275 | +58,356 | +0 | +0.092 | -2,345,274 / -2,304,797 | -2,237,370 (base -2,304,797) |  |
|  |  |  | LM | +1,557 [-8,016,+11,048] (13,731) | -270 | +62,648 | -2,376 | +0.091 | -2,363,866 / -2,304,797 | -2,255,148 (base -2,304,797) | 0.85/0.71 |
|  |  |  | MM | +0 [-9,472,+9,351] (13,574) | -5,085 | +42,113 | +9,001 | +0.098 | -2,274,900 / -2,304,797 | -2,170,081 (base -2,304,797) | 0.97/0.89 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -708 [-11,216,+9,165] (14,668) | +4,530 | +22,647 | +0 | -0.110 | -2,320,848 / -2,193,122 | -2,010,324 (base -2,193,122) |  |
|  |  |  | LM | -363 [-10,961,+9,585] (14,769) | +5,659 | +27,558 | -2,468 | -0.111 | -2,339,224 / -2,193,122 | -2,026,207 (base -2,193,122) | 0.31/0.33 |
|  |  |  | MM | -2,020 [-12,376,+7,617] (14,370) | +253 | +4,053 | +9,350 | -0.107 | -2,251,291 / -2,193,122 | -1,950,192 (base -2,193,122) | 0.10/0.22 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -1,318 [-4,936,+1,481] (4,767) | -1,093 | +0 | +0 | -0.072 | -1,648,767 / -1,677,814 | -1,648,767 (base -1,677,814) |  |
|  |  |  | LM | -1,170 [-4,829,+1,589] (4,767) | -228 | +4,285 | -1,219 | -0.072 | -1,661,550 / -1,677,814 | -1,661,550 (base -1,677,814) | 0.33/0.38 |
|  |  |  | MM | -1,879 [-5,659,+1,205] (5,018) | -4,372 | -16,234 | +4,617 | -0.072 | -1,600,340 / -1,677,814 | -1,600,340 (base -1,677,814) | 0.21/0.28 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | +312 [-6,969,+7,289] (10,045) | +1,604 | +22,647 | +0 | -0.012 | -3,414,524 / -3,432,946 | -3,333,973 (base -3,432,946) |  |
|  |  |  | LM | +648 [-6,699,+7,651] (10,097) | +2,672 | +27,558 | -2,468 | -0.013 | -3,441,344 / -3,432,946 | -3,360,145 (base -3,432,946) | 0.59/0.53 |
|  |  |  | MM | -967 [-8,159,+5,945] (9,906) | -2,445 | +4,053 | +9,350 | -0.008 | -3,312,966 / -3,432,946 | -3,234,870 (base -3,432,946) | 0.10/0.22 |

By year (summed weekly deltas, weeks): raw {2024: +22,376 (49), 2025: -217,148 (52), 2026: +239,032 (41)}; LM {2024: +36,526, 2025: -198,171, 2026: +253,731}; 2023 (X weeks) raw -58,001 (39 wk), LM -53,942.
2x cost (WF, vs the 2x-cost base): raw +1,119/wk (maxDD +45,537), LM +1,317/wk (maxDD +51,512); HOLD raw +763, LM +979.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST +878, HM -445, WT -110, KB -791, SM +1,168, PB -204; HOLD: ST -671, HM +1,379, WT +47, KB -339, SM +1,248, PB -2,245


#### F_half  (primary: 0.5x bottom tercile) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7
c_LM 1.034, c_MM 1.094, raw peak weighted lots 50.0 (x c_LM = 51.7), entries cut by the 50-cap 0, trades per book (cell / base): ST 4532/4506, HM 4160/4129, WT 6687/6636, KB 4845/4809, SM 2038/2037, PB 4629/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -3,802 [-7,512,-300] (5,156) | -3,827 | -16,902 | +0 | -0.142 | -2,238,826 / -2,304,797 | -2,238,826 (base -2,304,797) |  |
|  |  |  | LM | -2,434 [-6,097,+1,020] (5,092) | +493 | -1,271 | -10,403 | -0.142 | -2,314,772 / -2,304,797 | -2,314,772 (base -2,304,797) | 0.11/0.13 |
|  |  |  | MM | +0 [-4,222,+4,002] (5,866) | +8,181 | +26,545 | -28,914 | -0.142 | -2,449,914 / -2,304,797 | -2,449,914 (base -2,304,797) | 0.47/0.51 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | +1,339 [-1,892,+4,529] (4,536) | -2,660 | -18,375 | +12,450 | +0.116 | -2,067,774 / -2,193,122 | -2,051,336 (base -2,193,122) |  |
|  |  |  | LM | +2,989 [-278,+6,220] (4,573) | +2,033 | +1,390 | +2,066 | +0.116 | -2,137,918 / -2,193,122 | -2,120,923 (base -2,193,122) | 0.71/0.75 |
|  |  |  | MM | +5,923 [+1,870,+10,029] (5,836) | +10,383 | +36,560 | -16,411 | +0.116 | -2,262,735 / -2,193,122 | -2,244,747 (base -2,193,122) | 0.88/0.88 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -5,227 [-12,505,+1,407] (10,051) | -3,842 | +50,874 | +0 | -0.300 | -1,716,866 / -1,677,814 | -1,643,385 (base -1,677,814) |  |
|  |  |  | LM | -4,705 [-12,030,+1,949] (10,086) | -147 | +71,362 | -5,336 | -0.300 | -1,775,107 / -1,677,814 | -1,699,133 (base -1,677,814) | 0.07/0.09 |
|  |  |  | MM | -3,776 [-11,560,+3,385] (10,725) | +6,429 | +107,819 | -14,831 | -0.300 | -1,878,742 / -1,677,814 | -1,798,333 (base -1,677,814) | 0.15/0.13 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -1,367 [-3,838,+1,069] (3,535) | -3,077 | -18,375 | +11,894 | -0.018 | -3,284,813 / -3,432,946 | -3,254,691 (base -3,432,946) |  |
|  |  |  | LM | +146 [-2,336,+2,611] (3,534) | +1,442 | +1,390 | +1,491 | -0.018 | -3,396,243 / -3,432,946 | -3,365,099 (base -3,432,946) | 0.22/0.32 |
|  |  |  | MM | +2,837 [-119,+5,840] (4,250) | +9,483 | +36,560 | -17,020 | -0.018 | -3,594,523 / -3,432,946 | -3,561,561 (base -3,432,946) | 0.88/0.88 |

By year (summed weekly deltas, weeks): raw {2024: -270,377 (49), 2025: -16,384 (52), 2026: +92,679 (41)}; LM {2024: -213,438, 2025: +78,408, 2026: +155,692}; 2023 (X weeks) raw -159,313 (39 wk), LM -144,705.
2x cost (WF, vs the 2x-cost base): raw -749/wk (maxDD -85,577), LM +243/wk (maxDD -64,685); HOLD raw +1,790, LM +2,905.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -1,110, HM +499, WT +222, KB -263, SM -203, PB -513; HOLD: ST -399, HM +1,572, WT +496, KB +202, SM -277, PB -255


#### F_skipB  (primary: trade only mid+top) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7
c_LM 1.077, c_MM 1.206, raw peak weighted lots 50.0 (x c_LM = 53.8), entries cut by the 50-cap 0, trades per book (cell / base): ST 4187/4506, HM 3811/4129, WT 6194/6636, KB 4433/4809, SM 1905/2037, PB 4233/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -7,529 [-15,480,+73] (11,082) | -4,292 | -5,832 | +0 | -0.346 | -2,272,213 / -2,304,797 | -2,228,305 (base -2,304,797) |  |
|  |  |  | LM | -4,719 [-13,055,+3,141] (11,544) | +5,452 | +30,401 | -23,547 | -0.346 | -2,446,683 / -2,304,797 | -2,399,404 (base -2,304,797) | 0.05/0.13 |
|  |  |  | MM | -0 [-10,085,+9,570] (13,982) | +21,813 | +91,244 | -63,089 | -0.346 | -2,739,666 / -2,304,797 | -2,686,725 (base -2,304,797) | 0.05/0.07 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | +921 [-5,630,+7,438] (9,200) | -4,496 | -35,795 | +23,946 | +0.128 | -2,016,292 / -2,193,122 | -1,931,962 (base -2,193,122) |  |
|  |  |  | LM | +4,622 [-2,245,+11,453] (9,631) | +5,984 | +7,605 | +1,325 | +0.128 | -2,171,111 / -2,193,122 | -2,080,306 (base -2,193,122) | 0.63/0.59 |
|  |  |  | MM | +10,837 [+1,965,+19,953] (12,782) | +23,584 | +80,485 | -36,663 | +0.128 | -2,431,095 / -2,193,122 | -2,329,417 (base -2,193,122) | 0.89/0.90 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -9,015 [-23,520,+4,781] (20,461) | -3,659 | +105,479 | -3,319 | -0.552 | -1,771,395 / -1,677,814 | -1,547,346 (base -1,677,814) |  |
|  |  |  | LM | -8,124 [-23,413,+6,110] (21,265) | +4,720 | +156,046 | -15,652 | -0.552 | -1,907,410 / -1,677,814 | -1,666,158 (base -1,677,814) | 0.09/0.07 |
|  |  |  | MM | -6,628 [-23,544,+9,338] (23,766) | +18,791 | +240,964 | -36,362 | -0.552 | -2,135,816 / -1,677,814 | -1,865,676 (base -1,677,814) | 0.14/0.15 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -3,536 [-8,778,+1,550] (7,390) | -4,019 | -35,795 | +11,894 | -0.119 | -3,258,495 / -3,432,946 | -3,114,425 (base -3,432,946) |  |
|  |  |  | LM | -279 [-5,691,+5,060] (7,741) | +6,137 | +7,605 | -11,653 | -0.119 | -3,508,695 / -3,432,946 | -3,353,563 (base -3,432,946) | 0.15/0.21 |
|  |  |  | MM | +5,190 [-1,497,+11,938] (9,720) | +23,191 | +80,485 | -51,195 | -0.119 | -3,928,851 / -3,432,946 | -3,755,142 (base -3,432,946) | 0.89/0.90 |

By year (summed weekly deltas, weeks): raw {2024: -592,680 (49), 2025: -6,967 (52), 2026: +97,584 (41)}; LM {2024: -488,546, 2025: +208,320, 2026: +240,591}; 2023 (X weeks) raw -226,967 (39 wk), LM -199,096.
2x cost (WF, vs the 2x-cost base): raw -2,087/wk (maxDD -105,031), LM +57/wk (maxDD -59,234); HOLD raw +1,973, LM +4,510.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -2,186, HM +78, WT +267, KB -451, SM -468, PB -775; HOLD: ST -951, HM +1,512, WT +767, KB +375, SM -529, PB -254


#### F_up  (primary: 1.5x top tercile (50-contract cap)) - DEAD; failed gates: G1,G2,G3,G4,G5,G7,G8
c_LM 0.998, c_MM 1.083, raw peak weighted lots 50.0 (x c_LM = 49.9), entries cut by the 50-cap 460, trades per book (cell / base): ST 4443/4506, HM 4091/4129, WT 6531/6636, KB 4715/4809, SM 2022/2037, PB 4524/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -3,306 [-7,576,+990] (6,345) | +4,418 | -15,926 | -40,827 | -0.255 | -2,433,235 / -2,304,797 | -2,413,648 (base -2,304,797) |  |
|  |  |  | LM | -3,400 [-7,665,+878] (6,316) | +4,101 | -17,026 | -40,010 | -0.255 | -2,427,507 / -2,304,797 | -2,407,970 (base -2,304,797) | 0.15/0.15 |
|  |  |  | MM | +0 [-5,537,+5,591] (8,185) | +15,646 | +23,093 | -69,770 | -0.258 | -2,636,256 / -2,304,797 | -2,614,873 (base -2,304,797) | 0.65/0.59 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -278 [-2,996,+2,387] (3,895) | +620 | -2,828 | +0 | -0.025 | -2,218,381 / -2,193,122 | -2,194,581 (base -2,193,122) |  |
|  |  |  | LM | -387 [-3,104,+2,271] (3,886) | +289 | -4,228 | +745 | -0.025 | -2,213,172 / -2,193,122 | -2,189,429 (base -2,193,122) | 0.63/0.74 |
|  |  |  | MM | +3,567 [-337,+7,520] (5,827) | +12,352 | +46,756 | -26,394 | -0.027 | -2,402,973 / -2,193,122 | -2,377,126 (base -2,193,122) | 0.89/0.89 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | +7,401 [+1,503,+13,526] (8,816) | -697 | -67,090 | +0 | +0.484 | -1,542,151 / -1,677,814 | -1,504,000 (base -1,677,814) |  |
|  |  |  | LM | +7,337 [+1,433,+13,446] (8,811) | -959 | -68,233 | +368 | +0.484 | -1,538,520 / -1,677,814 | -1,500,455 (base -1,677,814) | 1.00/1.00 |
|  |  |  | MM | +9,664 [+3,034,+16,592] (9,846) | +8,573 | -26,587 | -13,033 | +0.481 | -1,670,844 / -1,677,814 | -1,629,660 (base -1,677,814) | 1.00/1.00 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -1,880 [-4,583,+721] (3,839) | +2,581 | -2,828 | -28,933 | -0.143 | -3,512,665 / -3,432,946 | -3,491,513 (base -3,432,946) |  |
|  |  |  | LM | -1,981 [-4,673,+602] (3,823) | +2,256 | -4,228 | -28,116 | -0.143 | -3,504,421 / -3,432,946 | -3,483,319 (base -3,432,946) | 0.29/0.30 |
|  |  |  | MM | +1,708 [-1,893,+5,223] (5,149) | +14,082 | +46,756 | -57,876 | -0.146 | -3,804,743 / -3,432,946 | -3,781,838 (base -3,432,946) | 0.89/0.89 |

By year (summed weekly deltas, weeks): raw {2024: -195,508 (49), 2025: -107,875 (52), 2026: +36,485 (41)}; LM {2024: -199,518, 2025: -114,111, 2026: +32,329}; 2023 (X weeks) raw +334,614 (39 wk), LM +332,513.
2x cost (WF, vs the 2x-cost base): raw -1,511/wk (maxDD -25,027), LM -1,575/wk (maxDD -26,612); HOLD raw -935, LM -1,003.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -539, HM -1,126, WT -109, KB -481, SM +179, PB +243; HOLD: ST +129, HM -1,053, WT +353, KB -437, SM +204, PB +563


#### F_hu  (primary: 0.5x bottom and 1.5x top) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7,G8
c_LM 1.031, c_MM 1.197, raw peak weighted lots 50.0 (x c_LM = 51.6), entries cut by the 50-cap 460, trades per book (cell / base): ST 4469/4506, HM 4122/4129, WT 6582/6636, KB 4751/4809, SM 2023/2037, PB 4543/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -7,108 [-12,549,-1,535] (8,015) | +624 | -16,617 | -40,827 | -0.400 | -2,380,273 / -2,304,797 | -2,347,677 (base -2,304,797) |  |
|  |  |  | LM | -5,973 [-11,645,-189] (8,281) | +4,763 | -1,855 | -51,801 | -0.402 | -2,455,560 / -2,304,797 | -2,421,892 (base -2,304,797) | 0.09/0.03 |
|  |  |  | MM | +0 [-8,508,+8,544] (12,287) | +26,633 | +76,436 | -109,849 | -0.409 | -2,854,005 / -2,304,797 | -2,814,690 (base -2,304,797) | 0.88/0.91 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | +1,061 [-3,041,+5,182] (5,857) | -2,073 | -21,203 | +12,450 | +0.091 | -2,096,775 / -2,193,122 | -2,052,796 (base -2,193,122) |  |
|  |  |  | LM | +2,562 [-1,588,+6,743] (5,956) | +2,292 | -2,976 | +2,832 | +0.090 | -2,162,942 / -2,193,122 | -2,117,558 (base -2,193,122) | 0.76/0.82 |
|  |  |  | MM | +10,474 [+3,394,+17,982] (10,706) | +25,358 | +93,355 | -47,999 | +0.085 | -2,513,041 / -2,193,122 | -2,460,093 (base -2,193,122) | 0.93/0.97 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | +2,174 [-8,237,+11,457] (14,461) | -3,779 | -30,719 | +0 | +0.190 | -1,585,214 / -1,677,814 | -1,469,572 (base -1,677,814) |  |
|  |  |  | LM | +2,869 [-7,666,+12,321] (14,595) | -360 | -14,204 | -4,943 | +0.188 | -1,635,318 / -1,677,814 | -1,516,127 (base -1,677,814) | 0.65/0.73 |
|  |  |  | MM | +6,516 [-6,015,+17,903] (17,392) | +17,699 | +73,255 | -31,063 | +0.181 | -1,900,433 / -1,677,814 | -1,762,616 (base -1,677,814) | 0.88/0.92 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -3,246 [-6,824,+332] (5,159) | -478 | -21,203 | -28,933 | -0.164 | -3,343,873 / -3,432,946 | -3,313,258 (base -3,432,946) |  |
|  |  |  | LM | -1,927 [-5,588,+1,729] (5,313) | +3,787 | -2,976 | -39,907 | -0.165 | -3,449,415 / -3,432,946 | -3,417,744 (base -3,432,946) | 0.23/0.30 |
|  |  |  | MM | +5,016 [-693,+11,001] (8,374) | +26,330 | +93,355 | -97,955 | -0.171 | -4,007,715 / -3,432,946 | -3,970,368 (base -3,432,946) | 0.93/0.97 |

By year (summed weekly deltas, weeks): raw {2024: -465,885 (49), 2025: -124,259 (52), 2026: +129,164 (41)}; LM {2024: -420,547, 2025: -41,032, 2026: +187,881}; 2023 (X weeks) raw +175,302 (39 wk), LM +198,493.
2x cost (WF, vs the 2x-cost base): raw -2,260/wk (maxDD -91,192), LM -1,430/wk (maxDD -71,168); HOLD raw +856, LM +1,827.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -1,648, HM -627, WT +113, KB -744, SM -24, PB -270; HOLD: ST -270, HM +519, WT +849, KB -235, SM -73, PB +308


#### V_half  (primary: 0.5x bottom tercile) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7,G8
c_LM 1.137, c_MM 1.180, raw peak weighted lots 50.0 (x c_LM = 56.9), entries cut by the 50-cap 0, trades per book (cell / base): ST 5056/4506, HM 4528/4129, WT 7479/6636, KB 5356/4809, SM 2056/2037, PB 5081/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -6,727 [-13,306,-687] (9,026) | -7,595 | -60,658 | -10,770 | -0.243 | -2,176,615 / -2,304,797 | -2,160,403 (base -2,304,797) |  |
|  |  |  | LM | -1,598 [-8,658,+4,976] (9,743) | +9,353 | -3,468 | -54,301 | -0.243 | -2,475,101 / -2,304,797 | -2,456,666 (base -2,304,797) | 0.58/0.59 |
|  |  |  | MM | -0 [-7,572,+7,161] (10,554) | +14,634 | +14,354 | -67,866 | -0.243 | -2,568,116 / -2,304,797 | -2,548,987 (base -2,304,797) | 0.15/0.17 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -11,214 [-23,544,+894] (17,895) | -16,316 | -28,275 | +50,402 | -0.332 | -2,206,808 / -2,193,122 | -1,942,771 (base -2,193,122) |  |
|  |  |  | LM | -6,269 [-18,712,+6,236] (18,147) | +781 | +50,267 | +13,629 | -0.332 | -2,509,434 / -2,193,122 | -2,209,190 (base -2,193,122) | 0.37/0.23 |
|  |  |  | MM | -4,727 [-17,557,+8,156] (18,599) | +6,108 | +74,742 | +2,170 | -0.332 | -2,603,739 / -2,193,122 | -2,292,211 (base -2,193,122) | 0.29/0.23 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -10,162 [-26,634,+6,509] (23,751) | -45,028 | -213,473 | +59,091 | -0.205 | -1,036,352 / -1,677,814 | -1,002,037 (base -1,677,814) |  |
|  |  |  | LM | -8,728 [-23,584,+6,251] (21,406) | -35,736 | -166,900 | +45,623 | -0.205 | -1,178,471 / -1,677,814 | -1,139,449 (base -1,677,814) | 0.19/0.11 |
|  |  |  | MM | -8,281 [-22,730,+6,186] (20,772) | -32,840 | -152,387 | +41,426 | -0.205 | -1,222,758 / -1,677,814 | -1,182,270 (base -1,677,814) | 0.21/0.10 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -8,923 [-15,970,-2,196] (9,861) | -12,276 | -28,275 | +1,124 | -0.278 | -3,325,932 / -3,432,946 | -3,210,011 (base -3,432,946) |  |
|  |  |  | LM | -3,846 [-11,091,+3,175] (10,117) | +4,729 | +50,267 | -42,407 | -0.278 | -3,782,028 / -3,432,946 | -3,650,210 (base -3,432,946) | 0.43/0.28 |
|  |  |  | MM | -2,264 [-9,752,+4,996] (10,511) | +10,028 | +74,742 | -55,972 | -0.278 | -3,924,157 / -3,432,946 | -3,787,385 (base -3,432,946) | 0.29/0.23 |

By year (summed weekly deltas, weeks): raw {2024: -458,127 (49), 2025: -515,442 (52), 2026: -293,525 (41)}; LM {2024: -253,696, 2025: -200,677, 2026: -91,753}; 2023 (X weeks) raw -364,800 (39 wk), LM -333,926.
2x cost (WF, vs the 2x-cost base): raw -6,537/wk (maxDD -52,525), LM -3,318/wk (maxDD +36,466); HOLD raw -8,690, LM -5,622.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -2,389, HM -970, WT +535, KB -2,435, SM -690, PB -2,975; HOLD: ST -3,076, HM +171, WT +999, KB -2,581, SM -1,387, PB -5,339


#### A_hu  (primary: 0.5x bottom and 1.5x top) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7,G8
c_LM 1.093, c_MM 1.253, raw peak weighted lots 50.0 (x c_LM = 54.7), entries cut by the 50-cap 2007, trades per book (cell / base): ST 4350/4506, HM 4022/4129, WT 6361/6636, KB 4641/4809, SM 1883/2037, PB 4282/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -8,081 [-19,798,+3,405] (17,043) | -5,431 | +45,933 | +2,603 | -0.359 | -2,483,265 / -2,304,797 | -2,146,933 (base -2,304,797) |  |
|  |  |  | LM | -5,059 [-17,327,+6,957] (17,824) | +6,234 | +96,545 | -26,171 | -0.376 | -2,720,671 / -2,304,797 | -2,352,750 (base -2,304,797) | 0.43/0.51 |
|  |  |  | MM | +0 [-14,369,+14,088] (20,765) | +26,329 | +184,534 | -75,948 | -0.405 | -3,133,017 / -2,304,797 | -2,710,513 (base -2,304,797) | 0.70/0.74 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -5,567 [-23,944,+11,965] (25,806) | -5,736 | -71,266 | +31,397 | -0.194 | -2,160,307 / -2,193,122 | -1,386,577 (base -2,193,122) |  |
|  |  |  | LM | -1,976 [-21,285,+16,513] (26,972) | +6,872 | -17,071 | +3,967 | -0.209 | -2,368,781 / -2,193,122 | -1,523,053 (base -2,193,122) | 0.47/0.35 |
|  |  |  | MM | +4,085 [-17,467,+24,904] (30,317) | +28,619 | +78,279 | -43,585 | -0.234 | -2,731,627 / -2,193,122 | -1,761,434 (base -2,193,122) | 0.52/0.41 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -8,733 [-23,739,+6,288] (21,816) | -36,643 | -146,032 | +3,346 | -0.193 | -1,181,717 / -1,677,814 | -1,117,087 (base -1,677,814) |  |
|  |  |  | LM | -7,631 [-21,623,+6,379] (20,356) | -29,562 | -108,158 | -10,978 | -0.193 | -1,291,668 / -1,677,814 | -1,221,024 (base -1,677,814) | 0.27/0.17 |
|  |  |  | MM | -5,736 [-18,362,+7,267] (18,714) | -17,362 | -42,892 | -35,662 | -0.194 | -1,481,138 / -1,677,814 | -1,400,132 (base -1,677,814) | 0.33/0.22 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -6,934 [-17,828,+3,810] (15,349) | -5,977 | -71,266 | +14,497 | -0.272 | -3,488,115 / -3,432,946 | -3,041,506 (base -3,432,946) |  |
|  |  |  | LM | -3,618 [-15,057,+7,611] (16,028) | +6,142 | -17,071 | -14,277 | -0.288 | -3,820,688 / -3,432,946 | -3,330,041 (base -3,432,946) | 0.48/0.40 |
|  |  |  | MM | +1,956 [-11,017,+14,625] (18,208) | +27,033 | +78,279 | -64,054 | -0.316 | -4,397,634 / -3,432,946 | -3,829,945 (base -3,432,946) | 0.52/0.41 |

By year (summed weekly deltas, weeks): raw {2024: -514,850 (49), 2025: -685,426 (52), 2026: +215,650 (41)}; LM {2024: -394,781, 2025: -502,074, 2026: +383,050}; 2023 (X weeks) raw -289,079 (39 wk), LM -261,282.
2x cost (WF, vs the 2x-cost base): raw -4,056/wk (maxDD +44,955), LM -2,271/wk (maxDD +124,118); HOLD raw -2,533, LM -461.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -907, HM -3,207, WT +407, KB -1,851, SM -392, PB -778; HOLD: ST -1,829, HM -78, WT +887, KB -1,210, SM -1,736, PB -1,413


#### V_hu  (primary: 0.5x bottom and 1.5x top) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7,G8
c_LM 1.147, c_MM 1.159, raw peak weighted lots 50.0 (x c_LM = 57.4), entries cut by the 50-cap 1862, trades per book (cell / base): ST 4566/4506, HM 4130/4129, WT 6574/6636, KB 4788/4809, SM 1901/2037, PB 4510/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -5,495 [-17,123,+5,931] (16,394) | -8,948 | +58,356 | -10,770 | -0.147 | -2,238,307 / -2,304,797 | -2,092,976 (base -2,304,797) |  |
|  |  |  | LM | -401 [-12,591,+11,574] (17,505) | +8,986 | +140,260 | -57,484 | -0.176 | -2,577,821 / -2,304,797 | -2,410,736 (base -2,304,797) | 0.82/0.71 |
|  |  |  | MM | -0 [-12,311,+12,176] (17,673) | +10,421 | +146,849 | -61,223 | -0.179 | -2,605,132 / -2,304,797 | -2,436,301 (base -2,304,797) | 0.03/0.06 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -11,923 [-27,760,+3,966] (22,855) | -11,651 | +27,645 | +50,402 | -0.447 | -2,319,328 / -2,193,122 | -1,759,974 (base -2,193,122) |  |
|  |  |  | LM | -7,052 [-24,251,+9,696] (24,224) | +7,389 | +122,102 | +10,940 | -0.463 | -2,667,535 / -2,193,122 | -2,025,672 (base -2,193,122) | 0.34/0.20 |
|  |  |  | MM | -6,667 [-23,992,+10,211] (24,404) | +8,913 | +129,703 | +7,781 | -0.464 | -2,695,508 / -2,193,122 | -2,047,022 (base -2,193,122) | 0.17/0.15 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -11,480 [-28,294,+5,499] (24,277) | -46,754 | -213,473 | +59,091 | -0.320 | -1,007,305 / -1,677,814 | -972,990 (base -1,677,814) |  |
|  |  |  | LM | -10,166 [-25,436,+5,206] (21,775) | -37,037 | -163,494 | +44,638 | -0.323 | -1,155,745 / -1,677,814 | -1,116,380 (base -1,677,814) | 0.19/0.16 |
|  |  |  | MM | -10,061 [-25,200,+5,187] (21,596) | -36,260 | -159,493 | +43,481 | -0.324 | -1,167,630 / -1,677,814 | -1,127,860 (base -1,677,814) | 0.19/0.13 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -8,611 [-18,549,+1,153] (13,980) | -10,711 | +27,645 | +1,124 | -0.287 | -3,315,467 / -3,432,946 | -3,111,039 (base -3,432,946) |  |
|  |  |  | LM | -3,589 [-14,125,+6,791] (14,827) | +7,742 | +122,102 | -45,590 | -0.310 | -3,812,353 / -3,432,946 | -3,576,336 (base -3,432,946) | 0.48/0.43 |
|  |  |  | MM | -3,193 [-13,828,+7,236] (14,947) | +9,219 | +129,703 | -49,330 | -0.312 | -3,852,251 / -3,432,946 | -3,613,678 (base -3,432,946) | 0.17/0.15 |

By year (summed weekly deltas, weeks): raw {2024: -435,751 (49), 2025: -732,589 (52), 2026: -54,493 (41)}; LM {2024: -237,627, 2025: -451,260, 2026: +179,279}; 2023 (X weeks) raw -422,801 (39 wk), LM -399,558.
2x cost (WF, vs the 2x-cost base): raw -5,418/wk (maxDD -52,525), LM -2,740/wk (maxDD +42,974); HOLD raw -7,928, LM -5,188.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -1,510, HM -1,414, WT +424, KB -3,227, SM +478, PB -3,179; HOLD: ST -3,747, HM +1,550, WT +1,046, KB -2,920, SM -139, PB -7,584


#### A_half  (primary: 0.5x bottom tercile) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7,G8
c_LM 1.094, c_MM 1.232, raw peak weighted lots 50.0 (x c_LM = 54.7), entries cut by the 50-cap 0, trades per book (cell / base): ST 4898/4506, HM 4405/4129, WT 7314/6636, KB 5247/4809, SM 2055/2037, PB 4929/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -8,296 [-15,272,-1,948] (9,512) | -6,522 | +33,641 | +0 | -0.353 | -2,293,554 / -2,304,797 | -2,156,428 (base -2,304,797) |  |
|  |  |  | LM | -4,935 [-12,068,+1,604] (9,843) | +5,172 | +81,605 | -28,765 | -0.353 | -2,508,691 / -2,304,797 | -2,358,702 (base -2,304,797) | 0.39/0.27 |
|  |  |  | MM | +0 [-8,885,+8,533] (12,575) | +22,343 | +152,039 | -71,007 | -0.353 | -2,824,616 / -2,304,797 | -2,655,738 (base -2,304,797) | 0.97/0.99 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -12,647 [-23,836,-2,033] (15,719) | -19,661 | -134,594 | +64,603 | -0.360 | -1,914,626 / -2,193,122 | -1,875,919 (base -2,193,122) |  |
|  |  |  | LM | -9,399 [-20,235,+777] (15,147) | -8,280 | -90,843 | +40,781 | -0.360 | -2,094,219 / -2,193,122 | -2,051,881 (base -2,193,122) | 0.11/0.08 |
|  |  |  | MM | -4,628 [-15,889,+6,390] (16,050) | +8,432 | -26,596 | +5,800 | -0.360 | -2,357,949 / -2,193,122 | -2,310,280 (base -2,193,122) | 0.24/0.21 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -8,659 [-23,689,+6,362] (21,820) | -36,586 | -146,032 | +3,346 | -0.187 | -1,181,717 / -1,677,814 | -1,117,087 (base -1,677,814) |  |
|  |  |  | LM | -7,537 [-21,506,+6,435] (20,355) | -29,438 | -107,850 | -11,095 | -0.187 | -1,292,563 / -1,677,814 | -1,221,870 (base -1,677,814) | 0.22/0.15 |
|  |  |  | MM | -5,890 [-18,647,+7,226] (18,883) | -18,942 | -51,779 | -32,301 | -0.187 | -1,455,338 / -1,677,814 | -1,375,743 (base -1,677,814) | 0.21/0.21 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -10,438 [-17,137,-4,166] (9,219) | -13,268 | -89,674 | +11,894 | -0.350 | -3,238,515 / -3,432,946 | -3,185,769 (base -3,432,946) |  |
|  |  |  | LM | -7,108 [-13,646,-929] (9,082) | -1,729 | -41,710 | -16,871 | -0.350 | -3,542,289 / -3,432,946 | -3,484,596 (base -3,432,946) | 0.15/0.06 |
|  |  |  | MM | -2,216 [-9,535,+4,908] (10,270) | +15,215 | +28,725 | -59,113 | -0.350 | -3,988,378 / -3,432,946 | -3,923,419 (base -3,432,946) | 0.24/0.21 |

By year (summed weekly deltas, weeks): raw {2024: -541,487 (49), 2025: -502,033 (52), 2026: -438,717 (41)}; LM {2024: -409,473, 2025: -285,473, 2026: -314,322}; 2023 (X weeks) raw -285,837 (39 wk), LM -257,312.
2x cost (WF, vs the 2x-cost base): raw -8,097/wk (maxDD -57,104), LM -6,042/wk (maxDD +3,337); HOLD raw -10,004, LM -8,028.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -3,003, HM -2,203, WT -3, KB -2,024, SM -1,037, PB -2,168; HOLD: ST -4,089, HM -2,012, WT +953, KB -2,510, SM -1,656, PB -3,332


#### A_hu_126  (sensitivity: trailing-126 cut points) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7,G8
c_LM 1.115, c_MM 1.359, raw peak weighted lots 50.0 (x c_LM = 55.8), entries cut by the 50-cap 2189, trades per book (cell / base): ST 4417/4506, HM 4049/4129, WT 6417/6636, KB 4652/4809, SM 1873/2037, PB 4279/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -10,555 [-22,018,+646] (16,674) | -3,152 | +45,933 | -33,339 | -0.535 | -2,477,269 / -2,304,797 | -2,157,170 (base -2,304,797) |  |
|  |  |  | LM | -7,065 [-19,591,+4,923] (17,958) | +11,527 | +108,550 | -73,182 | -0.553 | -2,769,353 / -2,304,797 | -2,412,063 (base -2,304,797) | 0.30/0.33 |
|  |  |  | MM | +0 [-16,523,+15,881] (23,770) | +42,581 | +243,418 | -158,132 | -0.594 | -3,394,617 / -2,304,797 | -2,958,126 (base -2,304,797) | 0.62/0.66 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -12,789 [-30,248,+3,835] (24,535) | -8,870 | +94,272 | +31,397 | -0.536 | -2,305,354 / -2,193,122 | -1,609,065 (base -2,193,122) |  |
|  |  |  | LM | -9,197 [-27,797,+8,353] (25,788) | +6,328 | +178,674 | -2,532 | -0.554 | -2,578,413 / -2,193,122 | -1,801,667 (base -2,193,122) | 0.05/0.09 |
|  |  |  | MM | -1,934 [-24,013,+19,380] (31,209) | +38,528 | +361,059 | -75,060 | -0.597 | -3,164,238 / -2,193,122 | -2,216,535 (base -2,193,122) | 0.18/0.21 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -1,973 [-17,324,+13,666] (22,512) | -21,143 | -93,697 | -12,158 | +0.149 | -1,226,411 / -1,677,814 | -1,091,681 (base -1,677,814) |  |
|  |  |  | LM | -11 [-14,926,+15,601] (22,248) | -10,639 | -38,387 | -32,331 | +0.137 | -1,369,329 / -1,677,814 | -1,219,582 (base -1,677,814) | 0.67/0.64 |
|  |  |  | MM | +3,969 [-12,468,+21,355] (24,459) | +11,566 | +80,766 | -75,586 | +0.108 | -1,673,504 / -1,677,814 | -1,492,702 (base -1,677,814) | 0.73/0.72 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -11,699 [-22,252,-1,442] (14,749) | -6,361 | +94,272 | -21,446 | -0.530 | -3,639,533 / -3,432,946 | -3,227,504 (base -3,432,946) |  |
|  |  |  | LM | -8,135 [-19,209,+2,592] (15,616) | +8,559 | +178,674 | -61,288 | -0.549 | -4,066,301 / -3,432,946 | -3,604,026 (base -3,432,946) | 0.06/0.09 |
|  |  |  | MM | -926 [-14,626,+12,609] (19,509) | +40,147 | +361,059 | -146,238 | -0.591 | -4,977,959 / -3,432,946 | -4,406,282 (base -3,432,946) | 0.18/0.21 |

By year (summed weekly deltas, weeks): raw {2024: -544,157 (49), 2025: -768,508 (52), 2026: -348,633 (41)}; LM {2024: -397,285, 2025: -554,059, 2026: -203,888}; 2023 (X weeks) raw -70,105 (39 wk), LM -18,307.
2x cost (WF, vs the 2x-cost base): raw -9,204/wk (maxDD +254,650), LM -7,563/wk (maxDD +373,356); HOLD raw -11,105, LM -9,563.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -189, HM -4,038, WT -963, KB -2,848, SM -809, PB -2,661; HOLD: ST -787, HM -2,013, WT -646, KB -3,031, SM -2,287, PB -3,834


#### V_skipB  (primary: trade only mid+top) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7,G8
c_LM 1.376, c_MM 1.400, raw peak weighted lots 50.0 (x c_LM = 68.8), entries cut by the 50-cap 0, trades per book (cell / base): ST 2774/4506, HM 2651/4129, WT 4108/6636, KB 3005/4809, SM 1235/2037, PB 2888/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -12,609 [-25,394,-685] (17,666) | -9,944 | -88,248 | +2,981 | -0.551 | -2,159,279 / -2,304,797 | -2,017,416 (base -2,304,797) |  |
|  |  |  | LM | -758 [-17,410,+15,214] (23,410) | +35,646 | +58,198 | -111,213 | -0.551 | -2,971,291 / -2,304,797 | -2,776,037 (base -2,304,797) | 0.58/0.51 |
|  |  |  | MM | -0 [-17,014,+16,429] (24,042) | +38,571 | +67,598 | -118,541 | -0.551 | -3,023,467 / -2,304,797 | -2,824,740 (base -2,304,797) | 0.06/0.05 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -26,631 [-49,746,-3,557] (33,689) | -41,424 | -213,963 | +64,603 | -0.923 | -1,688,579 / -2,193,122 | -1,222,310 (base -2,193,122) |  |
|  |  |  | LM | -18,866 [-43,940,+5,691] (35,935) | -3,985 | -68,419 | -30,893 | -0.923 | -2,323,539 / -2,193,122 | -1,681,938 (base -2,193,122) | 0.33/0.13 |
|  |  |  | MM | -18,369 [-43,746,+6,316] (36,226) | -1,583 | -59,073 | -37,022 | -0.923 | -2,364,301 / -2,193,122 | -1,711,448 (base -2,193,122) | 0.33/0.23 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -14,939 [-46,059,+16,387] (45,321) | -79,191 | -386,613 | +87,847 | -0.100 | -142,666 / -1,677,814 | -132,164 (base -1,677,814) |  |
|  |  |  | LM | -12,805 [-44,292,+18,461] (45,587) | -66,559 | -324,013 | +61,731 | -0.100 | -196,313 / -1,677,814 | -181,861 (base -1,677,814) | 0.35/0.22 |
|  |  |  | MM | -12,668 [-44,103,+18,697] (45,625) | -65,749 | -319,995 | +60,054 | -0.100 | -199,757 / -1,677,814 | -185,052 (base -1,677,814) | 0.36/0.27 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -19,412 [-32,779,-6,858] (18,707) | -24,702 | -211,563 | +14,875 | -0.716 | -2,954,303 / -3,432,946 | -2,373,870 (base -3,432,946) |  |
|  |  |  | LM | -9,435 [-24,601,+5,111] (21,252) | +17,255 | -65,116 | -99,319 | -0.716 | -4,065,223 / -3,432,946 | -3,266,521 (base -3,432,946) | 0.43/0.21 |
|  |  |  | MM | -8,796 [-24,176,+5,999] (21,559) | +19,946 | -55,717 | -106,647 | -0.716 | -4,136,535 / -3,432,946 | -3,323,816 (base -3,432,946) | 0.33/0.23 |

By year (summed weekly deltas, weeks): raw {2024: -906,566 (49), 2025: -952,782 (52), 2026: -897,215 (41)}; LM {2024: -514,709, 2025: -254,123, 2026: -570,945}; 2023 (X weeks) raw -485,464 (39 wk), LM -446,178.
2x cost (WF, vs the 2x-cost base): raw -14,422/wk (maxDD -180,286), LM -8,563/wk (maxDD +15,694); HOLD raw -20,046, LM -15,901.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -6,283, HM -3,151, WT -276, KB -4,081, SM -1,307, PB -4,314; HOLD: ST -8,648, HM -2,159, WT -831, KB -4,306, SM -2,518, PB -8,168


#### V_skipT  (reverse control: skip TOP tercile) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7,G8
c_LM 1.724, c_MM nan, raw peak weighted lots 50.0 (x c_LM = 86.2), entries cut by the 50-cap 0, trades per book (cell / base): ST 2968/4506, HM 2633/4129, WT 4301/6636, KB 3129/4809, SM 1343/2037, PB 3007/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -25,297 [-49,088,-1,762] (33,975) | -28,673 | +27,276 | +0 | -1.101 | -1,655,701 / -2,304,797 | -1,246,267 (base -2,304,797) |  |
|  |  |  | LM | -12,832 [-44,356,+19,756] (45,284) | +45,345 | +411,264 | -224,930 | -1.147 | -2,886,994 / -2,304,797 | -2,175,041 (base -2,304,797) | 0.14/0.15 |
|  | | | MM | n/a (c_MM outside 0.2..3) | | | | | | | |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -10,860 [-25,324,+1,776] (19,315) | -8,506 | +0 | +0 | -0.436 | -2,086,074 / -2,193,122 | -1,870,744 (base -2,193,122) |  |
|  |  |  | LM | +13,209 [-13,907,+39,776] (38,766) | +87,202 | +441,544 | -232,884 | -0.507 | -3,646,678 / -2,193,122 | -3,269,166 (base -2,193,122) | 0.65/0.85 |
|  | | | MM | n/a (c_MM outside 0.2..3) | | | | | | | |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -2,471 [-6,346,+0] (4,814) | -677 | +0 | +0 | -0.151 | -1,686,025 / -1,677,814 | -1,684,552 (base -1,677,814) |  |
|  |  |  | LM | +8,773 [-14,764,+32,795] (34,495) | +80,371 | +413,216 | -115,903 | -0.221 | -2,941,463 / -1,677,814 | -2,940,485 (base -1,677,814) | 0.76/0.79 |
|  | | | MM | n/a (c_MM outside 0.2..3) | | | | | | | |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -18,562 [-33,328,-4,849] (20,190) | -17,808 | +141,950 | +0 | -0.764 | -2,852,015 / -3,432,946 | -2,418,994 (base -3,432,946) |  |
|  |  |  | LM | -452 [-22,486,+20,990] (30,379) | +67,716 | +709,712 | -232,884 | -0.823 | -4,961,863 / -3,432,946 | -4,209,177 (base -3,432,946) | 0.53/0.49 |
|  | | | MM | n/a (c_MM outside 0.2..3) | | | | | | | |

By year (summed weekly deltas, weeks): raw {2024: -464,701 (49), 2025: -1,793,366 (52), 2026: -377,720 (41)}; LM {2024: +548,396, 2025: -1,142,297, 2026: +529,757}; 2023 (X weeks) raw -108,719 (39 wk), LM +167,028.
2x cost (WF, vs the 2x-cost base): raw -11,710/wk (maxDD +213,833), LM -1,800/wk (maxDD +933,180); HOLD raw -5,806, LM +8,011.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -1,853, HM -3,969, WT -2,412, KB -4,458, SM -3,485, PB -2,385; HOLD: ST -421, HM -4,308, WT -242, KB -2,161, SM -2,310, PB -1,419


#### A_skipB_126  (sensitivity: trailing-126 cut points) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7,G8
c_LM 1.313, c_MM 1.707, raw peak weighted lots 50.0 (x c_LM = 65.6), entries cut by the 50-cap 0, trades per book (cell / base): ST 3014/4506, HM 2815/4129, WT 4603/6636, KB 3311/4809, SM 1384/2037, PB 3173/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -17,092 [-30,951,-4,523] (19,019) | -4,592 | +39,148 | +0 | -0.886 | -2,376,706 / -2,304,797 | -2,007,923 (base -2,304,797) |  |
|  |  |  | LM | -8,634 [-26,301,+7,840] (24,498) | +35,014 | +200,853 | -95,944 | -0.886 | -3,120,294 / -2,304,797 | -2,636,132 (base -2,304,797) | 0.23/0.35 |
|  |  |  | MM | +0 [-25,981,+25,127] (36,835) | +84,593 | +422,140 | -219,331 | -0.951 | -4,096,764 / -2,304,797 | -3,466,860 (base -2,304,797) | 0.80/0.81 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -26,926 [-50,498,-3,658] (34,468) | -40,695 | -134,594 | +64,603 | -0.955 | -1,566,824 / -2,193,122 | -1,284,416 (base -2,193,122) |  |
|  |  |  | LM | -20,559 [-46,094,+4,169] (36,319) | -9,317 | +11,333 | -14,851 | -0.955 | -2,057,028 / -2,193,122 | -1,686,264 (base -2,193,122) | 0.08/0.07 |
|  |  |  | MM | -14,556 [-43,970,+14,766] (42,353) | +30,023 | +202,225 | -117,995 | -1.038 | -2,729,314 / -2,193,122 | -2,233,934 (base -2,193,122) | 0.21/0.26 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -9,383 [-35,088,+16,500] (37,541) | -32,208 | +9,555 | +3,346 | -0.313 | -910,076 / -1,677,814 | -708,337 (base -1,677,814) |  |
|  |  |  | LM | -5,868 [-33,389,+22,238] (40,203) | -6,999 | +185,588 | -44,820 | -0.313 | -1,194,806 / -1,677,814 | -929,950 (base -1,677,814) | 0.37/0.31 |
|  |  |  | MM | -2,342 [-34,170,+30,506] (46,850) | +24,648 | +420,675 | -107,296 | -0.359 | -1,565,930 / -1,677,814 | -1,223,763 (base -1,677,814) | 0.46/0.47 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -21,922 [-35,835,-9,014] (19,435) | -21,401 | -84,166 | +11,894 | -0.923 | -3,084,150 / -3,432,946 | -2,475,946 (base -3,432,946) |  |
|  |  |  | LM | -14,405 [-30,221,+76] (21,780) | +14,541 | +77,538 | -84,050 | -0.923 | -4,049,072 / -3,432,946 | -3,250,582 (base -3,432,946) | 0.03/0.10 |
|  |  |  | MM | -6,970 [-27,208,+12,222] (28,163) | +59,561 | +298,826 | -207,437 | -0.996 | -5,311,086 / -3,432,946 | -4,262,582 (base -3,432,946) | 0.21/0.26 |

By year (summed weekly deltas, weeks): raw {2024: -1,109,926 (49), 2025: -870,306 (52), 2026: -1,132,676 (41)}; LM {2024: -847,449, 2025: -263,206, 2026: -934,882}; 2023 (X weeks) raw -377,046 (39 wk), LM -310,439.
2x cost (WF, vs the 2x-cost base): raw -17,467/wk (maxDD +5,093), LM -13,543/wk (maxDD +226,150); HOLD raw -21,492, LM -18,496.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -5,119, HM -5,043, WT -1,063, KB -4,029, SM -2,785, PB -3,884; HOLD: ST -7,013, HM -6,033, WT +663, KB -4,602, SM -4,352, PB -5,589


#### A_skipB  (primary: trade only mid+top) - DEAD; failed gates: G1,G2,G3,G4,G5,G6,G7,G8
c_LM 1.246, c_MM 1.820, raw peak weighted lots 50.0 (x c_LM = 62.3), entries cut by the 50-cap 0, trades per book (cell / base): ST 2977/4506, HM 2799/4129, WT 4528/6636, KB 3272/4809, SM 1353/2037, PB 3124/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -18,143 [-31,797,-5,758] (19,012) | -6,074 | +39,148 | +0 | -0.928 | -2,528,249 / -2,304,797 | -2,072,139 (base -2,304,797) |  |
|  |  |  | LM | -11,750 [-27,856,+3,071] (22,570) | +24,708 | +166,312 | -75,450 | -0.928 | -3,150,287 / -2,304,797 | -2,581,959 (base -2,304,797) | 0.24/0.17 |
|  |  |  | MM | +0 [-27,997,+27,688] (40,128) | +96,199 | +489,683 | -255,381 | -1.026 | -4,664,807 / -2,304,797 | -3,835,723 (base -2,304,797) | 0.81/0.78 |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -32,335 [-56,799,-8,677] (35,167) | -36,938 | +232,797 | +64,603 | -1.382 | -1,703,169 / -2,193,122 | -1,307,725 (base -2,193,122) |  |
|  |  |  | LM | -28,658 [-54,535,-3,522] (36,875) | -11,338 | +437,944 | +2,121 | -1.382 | -2,122,209 / -2,193,122 | -1,629,471 (base -2,193,122) | 0.07/0.05 |
|  |  |  | MM | -23,137 [-56,016,+9,532] (47,031) | +48,109 | +934,565 | -148,255 | -1.498 | -3,176,656 / -2,193,122 | -2,442,415 (base -2,193,122) | 0.16/0.09 |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | -9,678 [-39,627,+19,583] (43,021) | -57,079 | -244,782 | +3,346 | +0.098 | -489,625 / -1,677,814 | -330,088 (base -1,677,814) |  |
|  |  |  | LM | -6,987 [-37,550,+23,245] (43,795) | -43,374 | -168,927 | -34,532 | +0.098 | -610,090 / -1,677,814 | -411,301 (base -1,677,814) | 0.43/0.39 |
|  |  |  | MM | -1,576 [-35,311,+31,702] (48,242) | -11,666 | +17,984 | -125,615 | +0.040 | -901,777 / -1,677,814 | -612,607 (base -1,677,814) | 0.54/0.61 |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -25,067 [-39,455,-11,731] (19,752) | -20,578 | +232,797 | +11,894 | -1.130 | -3,233,400 / -3,432,946 | -2,745,709 (base -3,432,946) |  |
|  |  |  | LM | -19,929 [-35,631,-5,554] (21,457) | +7,888 | +437,944 | -63,556 | -1.130 | -4,028,930 / -3,432,946 | -3,421,251 (base -3,432,946) | 0.01/0.03 |
|  |  |  | MM | -11,080 [-33,339,+10,486] (31,033) | +74,002 | +934,565 | -243,488 | -1.236 | -5,952,943 / -3,432,946 | -5,057,999 (base -3,432,946) | 0.16/0.09 |

By year (summed weekly deltas, weeks): raw {2024: -1,158,903 (49), 2025: -1,341,865 (52), 2026: -1,058,716 (41)}; LM {2024: -964,542, 2025: -980,465, 2026: -884,975}; 2023 (X weeks) raw -241,469 (39 wk), LM -155,733.
2x cost (WF, vs the 2x-cost base): raw -20,468/wk (maxDD +150,044), LM -18,121/wk (maxDD +359,545); HOLD raw -26,328, LM -25,163.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -7,699, HM -5,727, WT -1,323, KB -3,909, SM -2,336, PB -4,073; HOLD: ST -10,934, HM -5,885, WT -511, KB -4,648, SM -3,862, PB -6,495


#### VS_ref  (reference: D3VS S_V8 rule reproduced in this framework (no gate)) - REFERENCE; failed gates: G3,G4,G6,G7
c_LM 1.135, c_MM 1.091, raw peak weighted lots 54.0 (x c_LM = 61.4), entries cut by the 50-cap 0, trades per book (cell / base): ST 4506/4506, HM 4129/4129, WT 6636/6636, KB 4809/4809, SM 2037/2037, PB 4610/4610

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD | d maxDD | d worst | d Sharpe | worst-20 cell / base | cell P&L in base's 20 worst | placebo rank mean (shift/random) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -3,664 [-8,308,+896] (6,612) | -16,424 | -86,639 | +24,923 | +0.117 | -1,987,398 / -2,304,797 | -1,987,398 (base -2,304,797) |  |
|  |  |  | LM | +1,807 [-1,163,+4,766] (4,208) | -905 | -33,759 | -13,174 | +0.117 | -2,256,136 / -2,304,797 | -2,256,136 (base -2,304,797) | nan/nan |
|  |  |  | MM | -0 [-3,211,+3,096] (4,553) | -6,031 | -51,226 | -590 | +0.117 | -2,167,368 / -2,304,797 | -2,167,368 (base -2,304,797) | nan/nan |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -1,497 [-4,974,+1,850] (4,940) | -7,990 | -354 | +6,801 | +0.064 | -2,025,206 / -2,193,122 | -2,025,206 (base -2,193,122) |  |
|  |  |  | LM | +4,694 [+919,+8,571] (5,556) | +9,994 | +80,868 | -35,355 | +0.064 | -2,299,057 / -2,193,122 | -2,299,057 (base -2,193,122) | nan/nan |
|  |  |  | MM | +2,649 [-478,+5,817] (4,526) | +4,053 | +54,039 | -21,430 | +0.064 | -2,208,600 / -2,193,122 | -2,208,600 (base -2,193,122) | nan/nan |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | +696 [-986,+2,425] (2,509) | +591 | +0 | +0 | +0.037 | -1,661,801 / -1,677,814 | -1,661,801 (base -1,677,814) |  |
|  |  |  | LM | +3,577 [-1,314,+8,684] (7,228) | +15,921 | +74,790 | -21,270 | +0.037 | -1,886,512 / -1,677,814 | -1,886,512 (base -1,677,814) | nan/nan |
|  |  |  | MM | +2,626 [-896,+6,394] (5,273) | +10,857 | +50,085 | -14,244 | +0.037 | -1,812,287 / -1,677,814 | -1,812,287 (base -1,677,814) | nan/nan |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -2,652 [-5,648,+262] (4,215) | -12,170 | -354 | +6,801 | +0.084 | -3,044,698 / -3,432,946 | -3,022,211 (base -3,432,946) |  |
|  |  |  | LM | +3,202 [+748,+5,723] (3,473) | +4,613 | +80,868 | -35,355 | +0.084 | -3,456,406 / -3,432,946 | -3,430,878 (base -3,432,946) | nan/nan |
|  |  |  | MM | +1,269 [-1,051,+3,556] (3,241) | -931 | +54,039 | -21,430 | +0.084 | -3,320,412 / -3,432,946 | -3,295,889 (base -3,432,946) | nan/nan |

By year (summed weekly deltas, weeks): raw {2024: -96,583 (49), 2025: -144,447 (52), 2026: -135,549 (41)}; LM {2024: +153,886, 2025: +216,095, 2026: +84,771}; 2023 (X weeks) raw +13,722 (39 wk), LM +95,349.
2x cost (WF, vs the 2x-cost base): raw -920/wk (maxDD -72,231), LM +3,013/wk (maxDD +12,855); HOLD raw -240, LM +3,929.
Per-book raw weekly delta (nominal, before sweep cost) WF: ST -363, HM -479, WT +44, KB -1,000, SM -451, PB -403; HOLD: ST -656, HM -562, WT +219, KB +107, SM -578, PB -26

