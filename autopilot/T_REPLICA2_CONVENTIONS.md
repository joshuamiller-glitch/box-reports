# T_REPLICA2_CONVENTIONS (CONV-ENGINE, PRE-PROOF; no PASS claim; Gate 0 not passed; A-G not launched; no gate0 JSON promoted)
2026-11-07. Code /mnt/l2/l2vast/_replica2/code/ (r2_extract, r2_merge, r2_gen = generator, r2_labels, r2_run, r2_score, fit_report, hold_report, r2_validate); caches /mnt/l2/l2vast/_replica2/cache/ (blind_all 135,325,221 records = ZL-3 count; oct_all Oct 28-30 89.5 M); outputs /mnt/l2/l2vast/_replica2/out/. Seal: ds3_all_ea/manifest_after.json sha 759f2258... before and after; only _replica2/ written; frozen blind file only (labels.parquet from the LABELS agent).
## 1. Validation
Convention A=P0 (book on the T record), B=0 per fill, clock ts_recv, C0 F0 D0 M0 reproduces ZL-3 S0P0C0G0 trigger times on the blind week EXACTLY: 187/187 trades identical (85 fires, same ns timestamps; /mnt/l2/l2vast/_replica2/validate_S0P0C0G0.csv). One FIT-label job (130 stream jobs x 40 labels x 189 variants) takes minutes on 20 workers.
## 2. Pre-registered grid (prereg l2vast/ds3/prereg/T_REPLICA2_prereg.md, sha256 c83bb59c3ed7f558c0781565765a32845c89d703d97b4c112d4076647812998e, appended to DECISIONS.md before the first scoring)
24,840 conventions: cadence A in {P0, P1 (packet-end book), REC (every record), conflated 50/100/250/500/1000 ms, each also lagged one interval} x Med cadence (per callback / per conflation snapshot) x print B in {per fill, per aggressor order, order+price, 100 ms, 500 ms} x clock {ts_recv, ts_event} x vanish C {0 code, 1 unchanged, 2 all=0} x traded F {print price, none, traded-through} x Med seed D {first, per-session, 1000-mean} x latency {0, 0.175, 0.675, 1.175 s}. Rule fixed. Match = fire+latency within +-2.0 s of exit second+0.5; false = fire on HELD or >2 s before a CUT.
## 3. Split (lead ruling: no live L2 label before 10-29, FIT Feb-Sep empty)
FIT = DS7 entries to Tue 11-03 17:00 ET: 33 CUT + 7 HELD. HOLDOUT-1 = rest of blind week: 59 CUT + 6 HELD. HOLDOUT-2 = DS6 Oct 29-30: 17 CUT + 1 HELD (v2.0 3x/10 s and v2.1 30x/5 s, panel rule only). Counts are small; one label is 3% of FIT.
## 4. FIT result (selection)
Baseline (code reading P0/B0/clk0/C0/F0/D0/M0): 15 of 33 CUT matched (45%), 18 false of 33 fired (55%) at lat 0.175 (16 / 17 at lat 1.175): it cuts too early or on held trades (same picture as ZL-3). Unconstrained best matched (not eligible, false > 10%): 21 of 33 with 13 false (e.g. C250 B4 C2).
Selection (false <= 10% of fired, 6,573 feasible conventions, most of them near-silent): max matched = 9 of 33 (27%). Best feasible matched by cadence: C50_L 9, C50 8, C100/C100_L 6, P0 7, P1 2, C250+ 0, REC none feasible. Finalists (sha256 268dd0df... of out/finalists.csv):
| # | convention | FIT matched | false | fired |
|--|--|--|--|--|
| 1 | C50_L, B0, clk0, D0, M1, C1, F1, lat 1.175 | 9 | 1 | 10 |
| 2 | C50, B0, clk0, D0, M0, C1, F0, lat 1.175 | 8 | 0 | 8 |
| 3 | C50_L, B0, clk1, D0, M1, C1, F0, lat 1.175 | 8 | 0 | 8 |
Finalist 1 FIT by book (CUT/matched/false): K7 11/3/0, M7 5/2/0, P7 7/1/1, H7 2/1/0, O7 1/1/0, X3 2/1/0, A7 2/0/0, U7 1/0/0, X4 1/0/0, X5 1/0/0.
## 5. HOLDOUT (scored once, finalists only)
| convention | set | CUT | matched | rate | false | fired |
|--|--|--|--|--|--|--|
| 1 | H1 | 59 | 8 | 13.6% | 0 | 8 |
| 2 | H1 | 59 | 5 | 8.5% | 0 | 5 |
| 3 | H1 | 59 | 4 | 6.8% | 0 | 4 |
| 1 | H2 v2.0 (3x,10 s) | 17 | 8 | 47% | 8 | 16 (50% false) |
| 1 | H2 v2.1 (30x,5 s) | 17 | 3 | 17.6% | 0 | 3 |
Bar (>= 85% reproduced, <= 10% false) NOT met: best H1 reproduction 13.6%. Finalist 1 H1 by book (CUT/matched): K7 19/5, A7 12/0, P7 17/1, M7 8/1, O7 1/1, U7 2/0. No convention reaches the bar on FIT either (best feasible 27%, best unconstrained 64% at 38% false).
## 6. Failure cases (finalist 1, H1; full per-trade file out/holdout_finalist1_cases.csv)
All 65 H1 labels reached the arm. 51 CUT labels never fire (rule silent in the +-2 s window and through exit+1 s): e.g. idx 112/113 P7/M7 11-05 03:48:37 (adverse 32.4/32.5), 117 M7 11-05 07:22:47 (39.8), 120 M7 11-05 08:04:50 (37.3), 106 P7 11-05 01:47:21 (45.5), 84-86 K7/P7/M7 11-04 04:02:07 (56/52/45 pt adverse, PolicyCut). Fires that match have pm 30-84 with Med 1.6-2.9 (pulled 59-191 contracts) at unreal -31..-37; e.g. 91 K7 11-04 11:08:05 pm 75.3, 122 O7 11-05 09:43:07 pm 84.6, 101 P7 pm 30.04 (borderline). Held labels (78, 98, 103, 109, 110, 116) are all correctly silent under finalist 1: the low false rate is bought by silence, not by agreement. Finding: the 1-s-granular conflated books do not carry the live pulled_mult; the rule's pulled quantity is mostly below 30 x Med on the owned stream for the cuts it misses, as in ZL-3 (pm 9-15 on 11-05 03:48:37), and conventions that make it fire more (per print, per record, coarse conflation) fire on the held trades just as often.
## 7. Conclusion for the lead
No feed-delivery convention in the 24,840 grid reproduces the live cuts at the bar. FIT-selected best = C50_L finalist, 14% (H1) / 47% with 50% false (H2, v2.0). For T-TH-REDO use of "best convention + fragile-cut addendum": measured cut agreement is 14% of held-out cuts at 0% false (finalist 1) or, unconstrained, up to ~64% (FIT) at ~38% false; the labelled number must be one of those, not an assumption. Caveats: tiny label counts, FIT/HOLDOUT-1 are the same week (the holdout is not independent of feed behaviour that week), entry price is the lot-averaged fill (adds not modelled), policy stop distances for X3/X4/X5/A7 assumed, O7 panel arm 30 (policy 20).
