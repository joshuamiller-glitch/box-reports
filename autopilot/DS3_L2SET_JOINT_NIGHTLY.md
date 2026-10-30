# DS3_L2SET_JOINT - entry + profit + loss settings run TOGETHER on the stack (exact lock engine), agent L2SJ, 2026-10-30T01:40Z
Research only; no live/execution/chart change; UNTOUCHED (label day > 2026-02-06) never read. Prereg `l2vast/ds3/prereg/L2SET_JOINT_prereg.md` sha256 cd0f70a17a2c2e93b824737cf7cc52d094ea6e699e2524da36c47245d01984b1 and spec.json sha256 cbc42ed54f147c22b6168dcfbf2b92c73230b2374eeb92f445b87cb4121ff9fc (DECISIONS.md, before any joint statistic), 38 stack variants + 40 placebo runs, one look logged (out/l2set/joint/looks.jsonl). Own masks capped at 20260206 (not s48score.WINMASK / vs_lib.WINS, which have no upper bound): **2026 = 20260101..20260206, about 5 real weeks (6 ISO week keys; huge MDE: read as a sign, not a size)**, last 6 months (L6M) 20250801..20260206, HOLD 20250701..20260206, PRE 20240201..20250630, X' 20230401..20240131; every frame filtered to label day <= 20260206.
Units: STACK $/week = sum of the six engine books ST HM WT KB SM PE (the book set of L2SE) through `sl_lib.run_book` (BASE spec: day entry test -2R/+5R, give-back arm, week floor 12R) at live lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6) via the L2SE engine wrapper; busy rule re-applied on the modified rows, so blocked entries and occupancy are real. Delta = variant minus the stack as it is, same basis. MDE80 = 2.8 x SD(weekly paired delta)/sqrt(weeks) in parentheses. **Engine note:** this is the L2SE engine (plain sum at live lots), not the e2_joint/dvg WDAY-weighted stack with sweep costs used by the L2SP/L2SL stack lines, so stack baselines differ from those two reports; the check: E alone reproduces the published L2SE stack deltas to the dollar (+19.5k / +13.3k / +11.6k / +7.6k / +2.8k) and P alone / L alone reproduce the sections' per-trade pts per book (REF L6M ST +2.05 HM -0.31 WT +1.68 KB +0.88 SM +1.52 PE +0.66; L2SL RANK L6M ST +1.41 HM +1.00 WT +0.43 KB +1.20 SM +2.88 PE +0.93). PB DN MV MA have no lock engine and are not in the joint.
**Bases:** M = measured (the target-fill correction 1.4/1.5/4.2/4.3 pt is charged on every target fill, an early market exit does not pay it); N = no target-fill correction (target fills cost 0; early exits unchanged); each variant is compared with the stack as it is on the SAME basis (BASE|M, BASE|N).
**Precedence on one trade (fixed in the prereg, implemented in l2vast/ds3/code/l2set_joint/lj_kernel.py):** (1) ENTRY decides what is bought and when: lots, fills, stop at the ORIGINAL level, target re-based on the average price when the remainder fills. (2) The profit and loss rules are an EXIT overlay on the signal-price (E) clock exactly as L2SP/L2SL defined them (earliest of the two fires). (3) A rule firing at or before the second a pending add/dip would fill CANCELS that fill (single dip entry: no trade); open slices are flattened at the rule exit (rule exit pts, plus side*(E - fill) for the add). (4) The bracket (original stop / re-based target) stays live; earlier second exits, bracket wins ties. The rule clocks come from the baseline path (pct measured from the signal price); on a trade whose entry moved, the rule's exit price is the baseline-path exit price - an approximation, stated.

## 0. Verdicts (one line each)
* **H EPL** [honest PRE-selected]: **CANDIDATE-RECENT**; L6M +25.8k (56.3k), HOLD +20.5k (49.7k), 2026 +69.0k (182.4k), PRE +8.0k (23.6k), X' +10.8k (26.6k); N basis L6M -14.6k (60.3k) HOLD -17.2k (52.8k); failed: N-basis, CI(PRE lo>0), placebo>=0.95, RC: upstream cell search not in joint N (L2SE RC p(L6M) 0.11)
* **H E** [honest PRE-selected]: **CANDIDATE**; L6M +13.3k (14.5k), HOLD +11.6k (14.0k), 2026 +19.5k (41.7k), PRE +7.6k (11.2k), X' +2.8k (8.4k); failed: CI(PRE lo>0), placebo n/r, RC: upstream cell search not in joint N (L2SE RC p(L6M) 0.11), maxDD(HOLD)
* **H P** [honest PRE-selected]: **CANDIDATE-RECENT**; L6M +29.6k (46.7k), HOLD +30.0k (41.3k), 2026 +59.6k (148.3k), PRE -4.1k (21.6k), X' +4.5k (26.1k); N basis L6M -9.0k (50.0k) HOLD -6.1k (44.4k); failed: PRE, N-basis, CI(PRE lo>0), cost n/r, placebo n/r
* **H L** [honest PRE-selected]: **DEAD**; L6M -0.2k (32.7k), HOLD -4.3k (29.4k), 2026 +52.8k (70.8k), PRE +8.5k (14.0k), X' +2.2k (14.7k); failed: L6M, HOLD, CI(PRE lo>0), cost n/r, placebo n/r, RC: upstream cell search not in joint N (L2SE RC p(L6M) 0.11), maxDD(HOLD)
* **B EPL** [best-available, looked data]: **CANDIDATE-RECENT**; L6M +53.5k (59.2k), HOLD +52.7k (54.8k), 2026 +107.0k (181.6k), PRE -30.0k (32.7k), X' -4.4k (32.7k); N basis L6M +17.1k (59.7k) HOLD +18.9k (55.4k); failed: PRE, X, CI(PRE lo>0), RC invalid (upstream L6M search not counted)
* **B E** [best-available, looked data]: **CANDIDATE-RECENT**; L6M +53.0k (46.0k), HOLD +48.2k (43.6k), 2026 +90.1k (163.5k), PRE -11.0k (26.7k), X' -9.7k (23.9k); failed: PRE, X, CI(PRE lo>0), placebo n/r, RC invalid (upstream L6M search not counted)
* **B P** [best-available, looked data]: **CANDIDATE-RECENT**; L6M +26.8k (37.6k), HOLD +27.1k (33.3k), 2026 +41.5k (108.4k), PRE -1.8k (19.2k), X' +7.6k (20.7k); N basis L6M -4.9k (39.3k) HOLD -2.1k (35.0k); failed: PRE, N-basis, CI(PRE lo>0), cost n/r, placebo n/r, RC invalid (upstream L6M search not counted)
* **B L** [best-available, looked data]: **CANDIDATE-RECENT**; L6M +24.0k (32.5k), HOLD +22.0k (29.7k), 2026 +52.4k (92.5k), PRE -15.2k (20.1k), X' -3.1k (17.6k); failed: PRE, X, CI(PRE lo>0), cost n/r, placebo n/r, RC invalid (upstream L6M search not counted)
* Tier note: CANDIDATE here = all five windows >= 0 (and N basis for variants with P) with only statistical gates failing (prereg definition); the same pooled split was labelled CANDIDATE-RECENT in DS3_L2SET_ENTRY.md under its stricter placebo/RC set; no variant is PASS.
* Tier counts over the 14 stack variants: {'CANDIDATE': 2, 'CANDIDATE-RECENT': 11, 'DEAD': 1}. White reality check (weekly deltas, 2000 draws), set H (7 variants, honest): PRE p 0.01, L6M t 2.57 p 0.03, HOLD t 2.32 p 0.05; set B (7 variants): PRE p 0.91, L6M p 0.01, HOLD p 0.01 - set B's RC is NOT valid evidence (its cells were picked by L6M out of 2,179 entry and 7,840 loss cells; that search is not in N); all 14: L6M p 0.01.
* **Bottom line (honest set H):** E alone is the only component positive in all five windows on the M basis AND on the N basis (E: L6M +13.3k, HOLD +11.6k; N basis L6M +17.6k, HOLD +18.4k); P (plain 70% take) gains on M only through the target-fill correction (M L6M +29.6k, N L6M -9.0k, N PRE -31.7k); L adds nothing out of sample (L6M -0.2k, HOLD -4.3k); all three together are +25.8k L6M on M but -14.6k on N, and -16.8k versus the sum of the three alones (interaction: the re-based lower target is reached sooner, so the 70% overlay and the cuts fire on fewer, different trades). Joint worst-20 weeks and SD (HOLD): see section 2.
* **Tail (HOLD, M basis; SD / maxDD / worst-20 sum):** base 163k / 696k / -1.78M; H E 165k / 698k / -1.56M; H EPL 149k / 676k / -1.25M; B EPL 106k / 371k / -0.02M (the P overlay takes winners early and shortens exposure, which is where the SD and drawdown reductions come from on the M basis).
* **Best-available set B** (cells and books chosen on the same windows): EPL L6M +53.5k, HOLD +52.7k but PRE -30.0k and X' -4.4k; N basis L6M +17.1k but PRE -55.5k; +1 pt per fill cuts L6M to +36.8k. Placebo says the book-matching is real in-sample (rank 1.00) and wrong out of sample (PRE rank 0.00): tuned to the recent months.
* Placebo H EPL (same cells assigned to the wrong books, 20 draws): L6M real +25.8k vs placebo mean +25.5k (SD 3.6k), rank 0.65; HOLD real +20.5k vs +22.5k, rank 0.10; PRE real +8.0k vs -8.8k, rank 1.00. (set H shares one pooled entry cell and one take rule across books, so only the loss cells differ between placebo and real.)
* Placebo B EPL (same cells assigned to the wrong books, 20 draws): L6M real +53.5k vs placebo mean +7.3k (SD 10.5k), rank 1.00; HOLD real +52.7k vs +6.1k, rank 1.00; PRE real -30.0k vs -21.4k, rank 0.00.

## 1. SETTINGS TABLE per book (entry / profit / loss), joint EPL on the stack engine, recent windows first
Per-book delta $/wk = the book's own engine P&L in the joint run minus the same book in the stack as it is (books are additive in the plain-sum stack; each book's lock engine is its own). MDE in parentheses. Tier per book: CANDIDATE-RECENT = 2026 >= 0 and L6M > 0 on the M basis, else DEAD; per-book placebo / RC were not run (that gate fails), so no book can be PASS/CANDIDATE. P column: the plain take at 70% of target (D6: `profit <tag> * pct >= 0.7 take`) with its N-basis L6M/HOLD.
### Set H: PRE-selected cells only (honest)
| book | entry settings (D6 group 05 vocabulary) | profit | loss | 2026 | L6M | HOLD | PRE | X' | N-basis L6M / HOLD | alone L6M: E / P / L | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ST (S6) | dip_X=3pt basis=i(from signal) ; confirmations_N=1 of 8 gate_list=default-8 (abs>=5x, iceberg refill, imb5 flip to +0.20, print>=25, pull>=20%, micro>0.10 tick, delta 10s/30s, sweep reclaim) ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=0.7 at signal, remainder risk-capped on confirmed dip, target re-based ; limit_join_s=0 (market +1 tick) ; eval=1 s | `profit S6 * pct >= 0.7 take` | `loss S6 * pct <= -0.250 pulled_sup10 >= 100*medOwnLevel ownDepth10Rel <= 0.5 cut` (A15|mult100@10s|ne0|WG|cut) | +38.6k (106.6k) | +14.7k (33.0k) | +10.4k (29.7k) | +0.9k (11.7k) | -6.0k (16.0k) | +6.1k / +3.8k | +2.2k / +12.1k / -2.4k | **CANDIDATE-RECENT** |
| HM (H6) | dip_X=3pt basis=i(from signal) ; confirmations_N=1 of 8 gate_list=default-8 (abs>=5x, iceberg refill, imb5 flip to +0.20, print>=25, pull>=20%, micro>0.10 tick, delta 10s/30s, sweep reclaim) ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=0.7 at signal, remainder risk-capped on confirmed dip, target re-based ; limit_join_s=0 (market +1 tick) ; eval=1 s | `profit H6 * pct >= 0.7 take` | `loss H6 * pct <= -0.500 pulled_sup30 >= 100*medOwnLevel sweepAgainst10 >= 1 tighten mae+10` (A30|mult100@30s|ne0|SWP|t10) | +12.4k (50.9k) | -0.2k (20.3k) | -2.9k (18.1k) | +4.5k (12.3k) | -0.1k (13.5k) | -7.1k / -9.7k | +3.1k / +2.8k / +3.5k | **DEAD** |
| WT (W6) | dip_X=3pt basis=i(from signal) ; confirmations_N=1 of 8 gate_list=default-8 (abs>=5x, iceberg refill, imb5 flip to +0.20, print>=25, pull>=20%, micro>0.10 tick, delta 10s/30s, sweep reclaim) ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=0.7 at signal, remainder risk-capped on confirmed dip, target re-based ; limit_join_s=0 (market +1 tick) ; eval=1 s | `profit W6 * pct >= 0.7 take` | `loss W6 * pct <= -0.593 pulled_sup30 >= 500*medOwnLevel newAdvExt30 == 1 tighten mae+5` (A20|mult500@30s|ne1|none|t5) | +1.6k (17.9k) | +7.4k (10.8k) | +8.7k (10.1k) | +2.8k (7.4k) | +3.3k (8.3k) | +0.1k / +1.0k | +2.7k / +6.0k / +0.7k | **CANDIDATE-RECENT** |
| KB (K6) | dip_X=3pt basis=i(from signal) ; confirmations_N=1 of 8 gate_list=default-8 (abs>=5x, iceberg refill, imb5 flip to +0.20, print>=25, pull>=20%, micro>0.10 tick, delta 10s/30s, sweep reclaim) ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=0.7 at signal, remainder risk-capped on confirmed dip, target re-based ; limit_join_s=0 (market +1 tick) ; eval=1 s | `profit K6 * pct >= 0.7 take` | `loss K6 * pct <= -0.750 pulled_sup10 >= 20*medOwnLevel newAdvExt10 == 1 sweepAgainst10 >= 1 tighten mae+5` (A45|mult20@10s|ne1|SWP|t5) | -4.1k (26.8k) | -1.5k (10.3k) | -1.1k (9.9k) | -0.3k (7.0k) | +2.8k (9.4k) | -11.2k / -10.3k | +1.5k / +4.0k / -0.4k | **DEAD** |
| SM (U6) | dip_X=3pt basis=i(from signal) ; confirmations_N=1 of 8 gate_list=default-8 (abs>=5x, iceberg refill, imb5 flip to +0.20, print>=25, pull>=20%, micro>0.10 tick, delta 10s/30s, sweep reclaim) ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=0.7 at signal, remainder risk-capped on confirmed dip, target re-based ; limit_join_s=0 (market +1 tick) ; eval=1 s | `profit U6 * pct >= 0.7 take` | `loss U6 * pct <= -0.333 pulled_sup30 >= 500*medOwnLevel newAdvExt30 == 1 icebergAgainst == 1 tighten mae+10` (A20|mult500@30s|ne1|ICE|t10) | +14.0k (27.0k) | +3.7k (9.1k) | +3.5k (8.0k) | +0.8k (5.4k) | +3.7k (5.6k) | +0.8k / +0.4k | +2.8k / +3.0k / +0.2k | **CANDIDATE-RECENT** |
| PE (P6) | dip_X=3pt basis=i(from signal) ; confirmations_N=1 of 8 gate_list=default-8 (abs>=5x, iceberg refill, imb5 flip to +0.20, print>=25, pull>=20%, micro>0.10 tick, delta 10s/30s, sweep reclaim) ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=0.7 at signal, remainder risk-capped on confirmed dip, target re-based ; limit_join_s=0 (market +1 tick) ; eval=1 s | `profit P6 * pct >= 0.7 take` | `loss P6 * pct <= -0.500 pulledZ30 >= 1 newAdvExt30 == 1 sweepAgainst10 >= 1 tighten mae+10` (A30|z1@30s|ne1|SWP|t10) | +6.6k (28.8k) | +1.7k (11.1k) | +2.0k (10.0k) | -0.6k (8.5k) | +7.1k (8.8k) | -3.3k / -2.4k | +0.9k / +1.6k / -1.9k | **CANDIDATE-RECENT** |
| **STACK** | | | | +69.0k (182.4k) | +25.8k (56.3k) | +20.5k (49.7k) | +8.0k (23.6k) | +10.8k (26.6k) | -14.6k / -17.2k | +13.3k / +29.6k / -0.2k | **CANDIDATE-RECENT** (failed: N-basis, CI(PRE lo>0), placebo>=0.95, RC: upstream cell search not in joint N (L2SE RC p(L6M) 0.11)) |

### Set B: best-available per book (selected on looked data)
| book | entry settings (D6 group 05 vocabulary) | profit | loss | 2026 | L6M | HOLD | PRE | X' | N-basis L6M / HOLD | alone L6M: E / P / L | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ST (S6) | dip_X=3pt basis=i(from signal) ; confirmations_N=1 of 8 gate_list=default-8 (abs>=5x, iceberg refill, imb5 flip to +0.20, print>=25, pull>=20%, micro>0.10 tick, delta 10s/30s, sweep reclaim) ; veto=imb5<=-0.30 ; chase_Y=off ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | `profit S6 * pct >= 0.7 take` | `loss S6 * pct <= -0.500 pulled_sup10 >= 100*medOwnLevel newAdvExt10 == 1 sweepAgainst10 >= 1 tighten mae+10` (A30|mult100@10s|ne1|SWP|t10) | +35.3k (74.3k) | +19.2k (25.5k) | +17.5k (22.9k) | -5.8k (13.9k) | -8.6k (16.1k) | +10.8k / +11.1k | +9.4k / +12.1k / +8.8k | **CANDIDATE-RECENT** |
| HM (H6) | dip_X=5pt basis=iii(either, run-up>=20) ; confirmations_N=1 gate_list=[PRINT>=50] ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | none | `loss H6 * pct <= -0.250 pulled_sup30 >= 20*medOwnLevel newAdvExt30 == 1 imb10 <= -0.3 tighten mae+5` (A15|mult20@30s|ne1|IMB|t5) | +32.6k (49.9k) | +9.7k (25.9k) | +11.6k (24.8k) | -6.2k (17.2k) | -1.0k (18.5k) | +4.0k / +6.0k | +10.1k / +0.0k / +7.0k | **CANDIDATE-RECENT** |
| WT (W6) | dip_X=5pt basis=i(from signal) ; confirmations_N=3 of 8 gate_list=default-8 (abs>=5x, iceberg refill, imb5 flip to +0.20, print>=25, pull>=20%, micro>0.10 tick, delta 10s/30s, sweep reclaim) ; veto=imb5<=-0.40 ; chase_Y=3pt + book confirmation (delta10>0 & delta30>0) chase_stop=original level ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | `profit W6 * pct >= 0.7 take` | `loss W6 * pct <= -0.444 pulledZ30 >= 2 newAdvExt30 == 1 icebergAgainst == 1 tighten mae+10` (A15|z2@30s|ne1|ICE|t10) | +4.9k (42.2k) | +7.8k (15.9k) | +8.6k (14.0k) | -4.9k (7.6k) | +0.4k (9.0k) | +2.2k / +2.7k | +8.9k / +6.0k / +0.2k | **CANDIDATE-RECENT** |
| KB (K6) | dip_X=8pt basis=ii(from running favourable extreme, run-up>=10) ; confirmations_N=3 of 8 gate_list=default-8 (abs>=5x, iceberg refill, imb5 flip to +0.20, print>=25, pull>=20%, micro>0.10 tick, delta 10s/30s, sweep reclaim) ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=off ; limit_join_s=0 (market +1 tick) ; eval=1 s | `profit K6 * pct >= 0.7 take` | `loss K6 * pct <= -0.500 pulled_sup5 >= 100*medOwnLevel icebergAgainst == 1 tighten mae+5` (A30|mult100@5s|ne0|ICE|t5) | +4.6k (18.0k) | +6.8k (11.1k) | +6.9k (10.9k) | -4.6k (9.5k) | +0.7k (10.5k) | -2.4k / -1.9k | +9.5k / +4.0k / +0.6k | **CANDIDATE-RECENT** |
| SM (U6) | dip_X=10pt basis=i(from signal) ; confirmations_N=1 of 8 gate_list=default-8 (abs>=5x, iceberg refill, imb5 flip to +0.20, print>=25, pull>=20%, micro>0.10 tick, delta 10s/30s, sweep reclaim) ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=0.3 at signal, remainder risk-capped on confirmed dip, target re-based ; limit_join_s=0 (market +1 tick) ; eval=1 s | `profit U6 * pct >= 0.7 take` | `loss U6 * pct <= -0.250 pulled_sup5 >= 20*medOwnLevel imb10 <= -0.3 cut` (A15|mult20@5s|ne0|IMB|cut) | +17.9k (35.9k) | +8.7k (12.5k) | +7.4k (11.1k) | -4.5k (6.9k) | +1.3k (7.4k) | +6.1k / +4.8k | +6.7k / +3.0k / +5.0k | **CANDIDATE-RECENT** |
| PE (P6) | dip_X=15pt basis=i(from signal) ; confirmations_N=2 of 8 gate_list=default-8 (abs>=5x, iceberg refill, imb5 flip to +0.20, print>=25, pull>=20%, micro>0.10 tick, delta 10s/30s, sweep reclaim) ; veto=imb5<=-0.40 ; chase_Y=off ; split_F=0.5 at signal, remainder risk-capped on confirmed dip, target re-based ; limit_join_s=0 (market +1 tick) ; eval=1 s | `profit P6 * pct >= 0.7 take` | `loss P6 * pct <= -0.250 pulled_sup5 >= 100*medOwnLevel newAdvExt5 == 1 icebergAgainst == 1 cut` (A15|mult100@5s|ne1|ICE|cut) | +11.7k (27.8k) | +1.4k (10.9k) | +0.6k (9.9k) | -4.1k (7.8k) | +2.9k (8.9k) | -3.7k / -3.9k | +8.4k / +1.6k / +2.4k | **CANDIDATE-RECENT** |
| **STACK** | | | | +107.0k (181.6k) | +53.5k (59.2k) | +52.7k (54.8k) | -30.0k (32.7k) | -4.4k (32.7k) | +17.1k / +18.9k | +53.0k / +26.8k / +24.0k | **CANDIDATE-RECENT** (failed: PRE, X, CI(PRE lo>0), RC invalid (upstream L6M search not counted)) |

Settings were chosen as follows. Set H (honest): entry = the pooled PRE-selected 70/30 risk-capped split on every book, profit = the plain 70% take on every book (a pre-specified reference rule, not selected), loss = the L2SL cell chosen on PRE only for each book. Set B (best available per book, SELECTED ON LOOKED DATA): entry = each book's own best L6M cell with 2026 >= 0, profit = the plain 70% take on ST WT KB SM PE (the books where it is CANDIDATE-RECENT on the measured basis; HM is not), loss = each book's L6M-ranked L2SL cell. Entries of set B are tuned on the same last-6-months that the table reports: in-sample by construction.

## 2. STACK lines: weekly mean, SD, maxDD, worst-20-weeks and $/wk delta (MDE), recent windows first
Base = the stack as it is. Worst-20 = sum of the 20 worst weeks (windows with fewer weeks: all weeks; 2026 has 6 week keys).
### 2026 (~5 wk)  (6 weeks)
| variant | basis | mean $/wk | SD | maxDD | worst-20 sum | delta vs base $/wk (MDE) | delta 95% CI |
|--|--|--|--|--|--|--|--|
| BASE (stack as it is) | M | -18.7k | 185k | 457k | -112k | - | - |
| BASE (stack as it is) | N | +18.9k | 186k | 346k | 114k | - | - |
| H E | M | +0.8k | 183k | 348k | 5k | +19.5k (41.7k) | [-9.6k, +48.7k] |
| H P | M | +40.9k | 96k | 197k | 245k | +59.6k (148.3k) | [-44.2k, +163.5k] |
| H P | N | +44.0k | 100k | 196k | 264k | +25.0k (159.2k) | [-86.5k, +136.5k] |
| H L | M | +34.1k | 156k | 208k | 204k | +52.8k (70.8k) | [+3.3k, +102.4k] |
| H EP | M | +43.6k | 91k | 174k | 262k | +62.4k (162.0k) | [-51.0k, +175.8k] |
| H EP | N | +51.6k | 98k | 174k | 310k | +32.7k (157.2k) | [-77.3k, +142.7k] |
| H EL | M | +39.2k | 166k | 235k | 235k | +58.0k (72.9k) | [+7.0k, +109.0k] |
| H PL | M | +57.0k | 167k | 220k | 342k | +75.8k (180.6k) | [-50.6k, +202.2k] |
| H PL | N | +58.6k | 171k | 222k | 352k | +39.6k (207.4k) | [-105.5k, +184.8k] |
| H EPL | M | +50.2k | 166k | 207k | 301k | +69.0k (182.4k) | [-58.7k, +196.7k] |
| H EPL | N | +57.0k | 164k | 203k | 342k | +38.1k (203.0k) | [-104.0k, +180.2k] |
| B E | M | +71.3k | 74k | 132k | 428k | +90.1k (163.5k) | [-24.4k, +204.5k] |
| B P | M | +22.8k | 114k | 245k | 137k | +41.5k (108.4k) | [-34.4k, +117.4k] |
| B P | N | +30.1k | 118k | 242k | 180k | +11.1k (117.0k) | [-70.8k, +93.0k] |
| B L | M | +33.7k | 141k | 220k | 202k | +52.4k (92.5k) | [-12.3k, +117.2k] |
| B EP | M | +84.1k | 83k | 83k | 505k | +102.9k (182.5k) | [-24.9k, +230.6k] |
| B EP | N | +99.6k | 88k | 78k | 598k | +80.7k (165.8k) | [-35.4k, +196.7k] |
| B EL | M | +68.2k | 92k | 99k | 409k | +87.0k (154.5k) | [-21.2k, +195.1k] |
| B PL | M | +72.9k | 122k | 159k | 437k | +91.6k (162.9k) | [-22.4k, +205.7k] |
| B PL | N | +79.7k | 125k | 155k | 478k | +60.7k (162.9k) | [-53.3k, +174.8k] |
| B EPL | M | +88.3k | 91k | 70k | 530k | +107.0k (181.6k) | [-20.1k, +234.1k] |
| B EPL | N | +102.4k | 96k | 68k | 615k | +83.5k (174.6k) | [-38.7k, +205.7k] |

### last 6 mo  (28 weeks)
| variant | basis | mean $/wk | SD | maxDD | worst-20 sum | delta vs base $/wk (MDE) | delta 95% CI |
|--|--|--|--|--|--|--|--|
| BASE (stack as it is) | M | +18.8k | 135k | 608k | -882k | - | - |
| BASE (stack as it is) | N | +61.5k | 146k | 372k | -153k | - | - |
| H E | M | +32.1k | 139k | 537k | -639k | +13.3k (14.5k) | [+3.2k, +23.4k] |
| H P | M | +48.4k | 103k | 436k | -62k | +29.6k (46.7k) | [-3.1k, +62.3k] |
| H P | N | +52.5k | 103k | 429k | 21k | -9.0k (50.0k) | [-44.0k, +26.0k] |
| H L | M | +18.6k | 118k | 654k | -762k | -0.2k (32.7k) | [-23.1k, +22.6k] |
| H EP | M | +51.5k | 100k | 450k | 0k | +32.7k (50.8k) | [-2.9k, +68.3k] |
| H EP | N | +54.0k | 102k | 444k | 53k | -7.5k (51.5k) | [-43.5k, +28.6k] |
| H EL | M | +29.8k | 130k | 661k | -665k | +10.9k (36.9k) | [-14.9k, +36.8k] |
| H PL | M | +44.9k | 122k | 601k | -244k | +26.1k (58.0k) | [-14.5k, +66.6k] |
| H PL | N | +46.1k | 123k | 596k | -240k | -15.4k (62.1k) | [-58.9k, +28.1k] |
| H EPL | M | +44.7k | 119k | 592k | -236k | +25.8k (56.3k) | [-13.5k, +65.2k] |
| H EPL | N | +46.8k | 120k | 597k | -206k | -14.6k (60.3k) | [-56.9k, +27.6k] |
| B E | M | +71.8k | 91k | 216k | 491k | +53.0k (46.0k) | [+20.7k, +85.2k] |
| B P | M | +45.6k | 111k | 436k | -191k | +26.8k (37.6k) | [+0.4k, +53.1k] |
| B P | N | +56.6k | 113k | 421k | -3k | -4.9k (39.3k) | [-32.4k, +22.7k] |
| B L | M | +42.9k | 127k | 471k | -203k | +24.0k (32.5k) | [+1.3k, +46.8k] |
| B EP | M | +68.2k | 96k | 290k | 433k | +49.4k (57.9k) | [+8.9k, +89.9k] |
| B EP | N | +76.8k | 95k | 253k | 604k | +15.4k (56.7k) | [-24.3k, +55.0k] |
| B EL | M | +70.7k | 94k | 262k | 469k | +51.9k (49.1k) | [+17.5k, +86.2k] |
| B PL | M | +62.3k | 112k | 500k | 144k | +43.5k (47.5k) | [+10.2k, +76.8k] |
| B PL | N | +73.8k | 112k | 469k | 378k | +12.3k (48.2k) | [-21.4k, +46.1k] |
| B EPL | M | +72.3k | 83k | 289k | 633k | +53.5k (59.2k) | [+12.1k, +95.0k] |
| B EPL | N | +78.6k | 81k | 273k | 755k | +17.1k (59.7k) | [-24.7k, +58.9k] |

### HOLD  (32 weeks)
| variant | basis | mean $/wk | SD | maxDD | worst-20 sum | delta vs base $/wk (MDE) | delta 95% CI |
|--|--|--|--|--|--|--|--|
| BASE (stack as it is) | M | +8.6k | 163k | 696k | -1777k | - | - |
| BASE (stack as it is) | N | +48.3k | 173k | 651k | -1095k | - | - |
| H E | M | +20.2k | 165k | 698k | -1559k | +11.6k (14.0k) | [+1.8k, +21.4k] |
| H P | M | +38.6k | 133k | 524k | -922k | +30.0k (41.3k) | [+1.1k, +58.9k] |
| H P | N | +42.2k | 133k | 523k | -844k | -6.1k (44.4k) | [-37.2k, +24.9k] |
| H L | M | +4.2k | 155k | 802k | -1710k | -4.3k (29.4k) | [-24.9k, +16.2k] |
| H EP | M | +39.8k | 133k | 565k | -862k | +31.2k (44.7k) | [-0.1k, +62.5k] |
| H EP | N | +42.1k | 134k | 563k | -841k | -6.2k (45.4k) | [-38.0k, +25.6k] |
| H EL | M | +14.5k | 161k | 778k | -1641k | +5.9k (33.7k) | [-17.7k, +29.4k] |
| H PL | M | +30.9k | 150k | 639k | -1218k | +22.3k (50.9k) | [-13.3k, +57.9k] |
| H PL | N | +32.0k | 151k | 639k | -1223k | -16.4k (54.3k) | [-54.4k, +21.6k] |
| H EPL | M | +29.1k | 149k | 676k | -1247k | +20.5k (49.7k) | [-14.3k, +55.3k] |
| H EPL | N | +31.1k | 150k | 673k | -1221k | -17.2k (52.8k) | [-54.2k, +19.8k] |
| B E | M | +56.7k | 118k | 529k | -286k | +48.2k (43.6k) | [+17.7k, +78.7k] |
| B P | M | +35.7k | 140k | 560k | -1075k | +27.1k (33.3k) | [+3.8k, +50.5k] |
| B P | N | +46.2k | 142k | 548k | -887k | -2.1k (35.0k) | [-26.6k, +22.4k] |
| B L | M | +30.6k | 151k | 612k | -1053k | +22.0k (29.7k) | [+1.2k, +42.8k] |
| B EP | M | +57.8k | 118k | 405k | -274k | +49.2k (52.9k) | [+12.1k, +86.2k] |
| B EP | N | +65.8k | 118k | 396k | -107k | +17.5k (52.2k) | [-19.0k, +54.1k] |
| B EL | M | +56.5k | 116k | 464k | -269k | +47.9k (47.3k) | [+14.8k, +81.0k] |
| B PL | M | +50.5k | 140k | 533k | -701k | +41.9k (42.6k) | [+12.1k, +71.7k] |
| B PL | N | +61.3k | 141k | 522k | -482k | +13.0k (43.1k) | [-17.2k, +43.2k] |
| B EPL | M | +61.2k | 106k | 371k | -21k | +52.7k (54.8k) | [+14.3k, +91.0k] |
| B EPL | N | +67.2k | 105k | 362k | 106k | +18.9k (55.4k) | [-19.9k, +57.7k] |

### PRE  (75 weeks)
| variant | basis | mean $/wk | SD | maxDD | worst-20 sum | delta vs base $/wk (MDE) | delta 95% CI |
|--|--|--|--|--|--|--|--|
| BASE (stack as it is) | M | +27.7k | 130k | 746k | -2817k | - | - |
| BASE (stack as it is) | N | +58.0k | 139k | 704k | -2418k | - | - |
| H E | M | +35.4k | 137k | 756k | -2788k | +7.6k (11.2k) | [-0.2k, +15.5k] |
| H P | M | +23.6k | 121k | 435k | -2636k | -4.1k (21.6k) | [-19.3k, +11.0k] |
| H P | N | +26.3k | 120k | 418k | -2541k | -31.7k (24.7k) | [-49.0k, -14.4k] |
| H L | M | +36.2k | 128k | 559k | -2396k | +8.5k (14.0k) | [-1.3k, +18.3k] |
| H EP | M | +26.3k | 119k | 486k | -2535k | -1.4k (22.6k) | [-17.2k, +14.4k] |
| H EP | N | +29.0k | 120k | 475k | -2491k | -29.1k (25.0k) | [-46.6k, -11.6k] |
| H EL | M | +45.2k | 126k | 539k | -2247k | +17.5k (16.3k) | [+6.1k, +28.9k] |
| H PL | M | +32.7k | 105k | 417k | -1950k | +5.0k (23.0k) | [-11.1k, +21.1k] |
| H PL | N | +34.7k | 104k | 402k | -1893k | -23.3k (25.4k) | [-41.2k, -5.5k] |
| H EPL | M | +35.7k | 104k | 436k | -1935k | +8.0k (23.6k) | [-8.5k, +24.5k] |
| H EPL | N | +38.4k | 103k | 436k | -1875k | -19.7k (25.5k) | [-37.5k, -1.8k] |
| B E | M | +16.8k | 106k | 587k | -2281k | -11.0k (26.7k) | [-29.7k, +7.7k] |
| B P | M | +25.9k | 125k | 476k | -2634k | -1.8k (19.2k) | [-15.3k, +11.6k] |
| B P | N | +34.6k | 126k | 467k | -2464k | -23.4k (21.1k) | [-38.2k, -8.6k] |
| B L | M | +12.5k | 128k | 698k | -2899k | -15.2k (20.1k) | [-29.2k, -1.1k] |
| B EP | M | +15.9k | 100k | 494k | -2211k | -11.9k (31.1k) | [-33.6k, +9.9k] |
| B EP | N | +21.2k | 101k | 475k | -2117k | -36.9k (34.5k) | [-61.1k, -12.7k] |
| B EL | M | -0.6k | 98k | 773k | -2457k | -28.3k (27.3k) | [-47.3k, -9.2k] |
| B PL | M | +10.3k | 118k | 466k | -2692k | -17.4k (26.9k) | [-36.2k, +1.4k] |
| B PL | N | +17.7k | 119k | 423k | -2547k | -40.3k (29.4k) | [-60.9k, -19.7k] |
| B EPL | M | -2.3k | 91k | 663k | -2429k | -30.0k (32.7k) | [-52.9k, -7.1k] |
| B EPL | N | +2.5k | 91k | 567k | -2315k | -55.5k (35.9k) | [-80.7k, -30.4k] |

### X'  (44 weeks)
| variant | basis | mean $/wk | SD | maxDD | worst-20 sum | delta vs base $/wk (MDE) | delta 95% CI |
|--|--|--|--|--|--|--|--|
| BASE (stack as it is) | M | +5.2k | 102k | 567k | -1653k | - | - |
| BASE (stack as it is) | N | +16.0k | 104k | 490k | -1457k | - | - |
| H E | M | +8.0k | 99k | 520k | -1559k | +2.8k (8.4k) | [-3.1k, +8.7k] |
| H P | M | +9.7k | 96k | 376k | -1542k | +4.5k (26.1k) | [-13.8k, +22.7k] |
| H P | N | +9.9k | 96k | 375k | -1541k | -6.1k (26.6k) | [-24.8k, +12.5k] |
| H L | M | +7.4k | 102k | 575k | -1649k | +2.2k (14.7k) | [-8.0k, +12.5k] |
| H EP | M | +9.4k | 95k | 387k | -1533k | +4.2k (26.3k) | [-14.3k, +22.6k] |
| H EP | N | +9.7k | 95k | 384k | -1529k | -6.4k (26.9k) | [-25.2k, +12.4k] |
| H EL | M | +8.5k | 99k | 520k | -1493k | +3.4k (14.4k) | [-6.7k, +13.5k] |
| H PL | M | +15.4k | 95k | 417k | -1334k | +10.2k (27.1k) | [-8.7k, +29.2k] |
| H PL | N | +15.5k | 94k | 417k | -1324k | -0.5k (27.1k) | [-19.5k, +18.5k] |
| H EPL | M | +16.0k | 91k | 391k | -1220k | +10.8k (26.6k) | [-7.9k, +29.4k] |
| H EPL | N | +16.3k | 91k | 390k | -1215k | +0.2k (26.8k) | [-18.5k, +19.0k] |
| B E | M | -4.5k | 85k | 744k | -1606k | -9.7k (23.9k) | [-26.5k, +7.0k] |
| B P | M | +12.8k | 95k | 383k | -1487k | +7.6k (20.7k) | [-6.9k, +22.0k] |
| B P | N | +16.2k | 96k | 344k | -1429k | +0.2k (20.8k) | [-14.3k, +14.7k] |
| B L | M | +2.1k | 98k | 591k | -1616k | -3.1k (17.6k) | [-15.4k, +9.3k] |
| B EP | M | +1.2k | 77k | 393k | -1357k | -4.0k (29.8k) | [-24.9k, +16.9k] |
| B EP | N | +2.0k | 77k | 385k | -1336k | -14.0k (30.3k) | [-35.2k, +7.2k] |
| B EL | M | -3.3k | 83k | 660k | -1551k | -8.5k (29.6k) | [-29.3k, +12.2k] |
| B PL | M | +8.7k | 90k | 410k | -1431k | +3.5k (24.5k) | [-13.7k, +20.7k] |
| B PL | N | +12.1k | 90k | 371k | -1370k | -3.9k (24.4k) | [-21.0k, +13.2k] |
| B EPL | M | +0.8k | 75k | 438k | -1327k | -4.4k (32.7k) | [-27.3k, +18.5k] |
| B EPL | N | +1.8k | 75k | 426k | -1309k | -14.3k (33.0k) | [-37.4k, +8.8k] |

## 3. Tiers and failed gates (stack variants, M basis; N-basis gate applies where P is in)
| variant | tier | failed sign gates | failed statistical gates |
|--|--|--|--|
| H E | **CANDIDATE** | - | CI(PRE lo>0), placebo n/r, RC: upstream cell search not in joint N (L2SE RC p(L6M) 0.11), maxDD(HOLD) |
| H P | **CANDIDATE-RECENT** | PRE, N-basis | CI(PRE lo>0), cost n/r, placebo n/r |
| H L | **DEAD** | L6M, HOLD | CI(PRE lo>0), cost n/r, placebo n/r, RC: upstream cell search not in joint N (L2SE RC p(L6M) 0.11), maxDD(HOLD) |
| H EP | **CANDIDATE-RECENT** | PRE, N-basis | CI(PRE lo>0), cost n/r, placebo n/r, RC: upstream cell search not in joint N (L2SE RC p(L6M) 0.11) |
| H EL | **CANDIDATE** | - | cost n/r, placebo n/r, RC: upstream cell search not in joint N (L2SE RC p(L6M) 0.11), maxDD(HOLD) |
| H PL | **CANDIDATE-RECENT** | N-basis | CI(PRE lo>0), cost n/r, placebo n/r, RC: upstream cell search not in joint N (L2SE RC p(L6M) 0.11) |
| H EPL | **CANDIDATE-RECENT** | N-basis | CI(PRE lo>0), placebo>=0.95, RC: upstream cell search not in joint N (L2SE RC p(L6M) 0.11) |
| B E | **CANDIDATE-RECENT** | PRE, X | CI(PRE lo>0), placebo n/r, RC invalid (upstream L6M search not counted) |
| B P | **CANDIDATE-RECENT** | PRE, N-basis | CI(PRE lo>0), cost n/r, placebo n/r, RC invalid (upstream L6M search not counted) |
| B L | **CANDIDATE-RECENT** | PRE, X | CI(PRE lo>0), cost n/r, placebo n/r, RC invalid (upstream L6M search not counted) |
| B EP | **CANDIDATE-RECENT** | PRE, X | CI(PRE lo>0), cost n/r, placebo n/r, RC invalid (upstream L6M search not counted) |
| B EL | **CANDIDATE-RECENT** | PRE, X | CI(PRE lo>0), cost n/r, placebo n/r, RC invalid (upstream L6M search not counted) |
| B PL | **CANDIDATE-RECENT** | PRE | CI(PRE lo>0), cost n/r, placebo n/r, RC invalid (upstream L6M search not counted) |
| B EPL | **CANDIDATE-RECENT** | PRE, X | CI(PRE lo>0), RC invalid (upstream L6M search not counted) |
Gates: signs 2026 >= 0, L6M > 0, HOLD > 0, PRE >= 0, X' >= 0, (P in: N-basis L6M and HOLD >= 0); statistical: PRE CI lo > 0, +1 pt cost keeps HOLD >= 0 (run for E and EPL only), placebo rank >= 0.95 (EPL only), RC p(L6M) <= 0.05, maxDD(HOLD) <= base. 'n/r' = not run = fail.

## 4. Interaction with the lock engine (joint is not additive)
| set | window | E | P | L | E+P+L (sum of alones) | joint EPL | joint - sum | EP vs E+P | EL vs E+L | PL vs P+L |
|--|--|--|--|--|--|--|--|--|--|--|
| H | 2026 (~5 wk) | +19.5k | +59.6k | +52.8k | +132.0k | +69.0k | -63.0k | -16.8k | -14.4k | -36.7k |
| H | last 6 mo | +13.3k | +29.6k | -0.2k | +42.7k | +25.8k | -16.8k | -10.2k | -2.1k | -3.3k |
| H | HOLD | +11.6k | +30.0k | -4.3k | +37.3k | +20.5k | -16.7k | -10.4k | -1.4k | -3.4k |
| H | PRE | +7.6k | -4.1k | +8.5k | +12.0k | +8.0k | -4.1k | -4.9k | +1.3k | +0.6k |
| H | X' | +2.8k | +4.5k | +2.2k | +9.5k | +10.8k | +1.3k | -3.1k | -1.7k | +3.5k |
| B | 2026 (~5 wk) | +90.1k | +41.5k | +52.4k | +184.0k | +107.0k | -77.0k | -28.7k | -55.5k | -2.3k |
| B | last 6 mo | +53.0k | +26.8k | +24.0k | +103.8k | +53.5k | -50.3k | -30.3k | -25.1k | -7.3k |
| B | HOLD | +48.2k | +27.1k | +22.0k | +97.3k | +52.7k | -44.7k | -26.1k | -22.2k | -7.3k |
| B | PRE | -11.0k | -1.8k | -15.2k | -28.0k | -30.0k | -2.0k | +0.9k | -2.1k | -0.4k |
| B | X' | -9.7k | +7.6k | -3.1k | -5.2k | -4.4k | +0.8k | -1.9k | +4.2k | -1.0k |

Trade-level mechanics in last 6 months (engine books; counts of trades from the joint kernel output; lot-hours from fill to exit):
| set | variant | trades filled | entry-delayed or split trades | add/dip fills | rule exits | adds cancelled by a rule (vs E alone) | lot-hours per week | engine blocked entries (full span, 6 books) | engine kept |
|--|--|--|--|--|--|--|--|--|--|
| H | BASE | 6636 | 0 | 0 | 0 | 0 | 3,158 | 0 | 18752 |
| H | E | 6636 | 6115 | 6115 | 0 | 0 | 3,130 | 0 | 18910 |
| H | P | 6636 | 0 | 0 | 3770 | 0 | 2,453 | 0 | 21103 |
| H | L | 6636 | 0 | 0 | 2357 | 0 | 2,756 | 0 | 21222 |
| H | EPL | 6636 | 5984 | 5984 | 5486 | 131 | 2,151 | 0 | 22827 |
| B | BASE | 6636 | 0 | 0 | 0 | 0 | 3,158 | 0 | 18752 |
| B | E | 5451 | 5127 | 5127 | 0 | 0 | 2,293 | 726 | 16373 |
| B | P | 6636 | 0 | 0 | 3258 | 0 | 2,606 | 0 | 20805 |
| B | L | 6636 | 0 | 0 | 2139 | 0 | 2,802 | 0 | 21240 |
| B | EPL | 5350 | 4764 | 4764 | 4051 | 363 | 1,588 | 48 | 19101 |

## 5. Cost fragility: +1 / +2 pt per add / remainder lot-fill (adverse, M basis)
| variant | extra pt | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| H E | +0 | +19.5k (41.7k) | +13.3k (14.5k) | +11.6k (14.0k) | +7.6k (11.2k) | +2.8k (8.4k) |
| H E | +1 | +18.5k (43.7k) | +8.1k (14.9k) | +6.4k (14.4k) | -0.3k (11.8k) | -0.6k (8.4k) |
| H E | +2 | +12.1k (39.2k) | +3.9k (13.8k) | +2.1k (13.7k) | -8.1k (12.3k) | -5.5k (8.5k) |
| H E | break-even HOLD / L6M | 2.5 pt / 2.9 pt | | | | |
| H EPL | +0 | +69.0k (182.4k) | +25.8k (56.3k) | +20.5k (49.7k) | +8.0k (23.6k) | +10.8k (26.6k) |
| H EPL | +1 | +65.4k (181.6k) | +19.5k (56.1k) | +13.6k (49.8k) | +0.7k (23.3k) | +5.8k (26.6k) |
| H EPL | +2 | +57.3k (175.6k) | +11.4k (56.2k) | +5.5k (49.9k) | -7.3k (23.2k) | +0.8k (26.8k) |
| H EPL | break-even HOLD / L6M | 2.7 pt / 3.4 pt | | | | |
| B E | +0 | +90.1k (163.5k) | +53.0k (46.0k) | +48.2k (43.6k) | -11.0k (26.7k) | -9.7k (23.9k) |
| B E | +1 | +80.2k (154.5k) | +37.1k (45.6k) | +31.5k (43.2k) | -24.5k (25.2k) | -20.5k (24.6k) |
| B E | +2 | +49.6k (149.3k) | +18.4k (45.7k) | +14.0k (43.4k) | -37.0k (24.5k) | -28.4k (23.9k) |
| B E | break-even HOLD / L6M | 2.8 pt / 3.0 pt | | | | |
| B EPL | +0 | +107.0k (181.6k) | +53.5k (59.2k) | +52.7k (54.8k) | -30.0k (32.7k) | -4.4k (32.7k) |
| B EPL | +1 | +89.6k (173.2k) | +36.8k (60.6k) | +36.4k (55.9k) | -46.6k (32.8k) | -16.4k (32.6k) |
| B EPL | +2 | +81.4k (180.6k) | +19.9k (61.7k) | +20.7k (57.0k) | -64.1k (33.0k) | -29.4k (32.8k) |
| B EPL | break-even HOLD / L6M | 3.3 pt / 3.2 pt | | | | |
In set B several entry cells are single dip entries (every dip fill is a full lot-fill), so +1 pt costs far more than for the pooled split where only 30% of the lots carry it.

## 6. Placebo and reality check
* H EPL placebo draws (L6M delta, $/wk): +25.3k, +31.3k, +28.2k, +17.8k, +28.0k, +26.1k, +25.0k, +32.7k, +25.6k, +24.7k, +21.3k, +24.2k, +25.4k, +25.4k, +31.4k, +27.6k, +25.7k, +22.2k, +20.7k, +21.8k
* B EPL placebo draws (L6M delta, $/wk): +0.9k, +13.9k, -9.9k, +1.5k, +1.0k, -6.3k, +1.1k, +8.3k, +3.2k, +1.0k, +9.7k, +18.3k, -0.9k, +25.6k, +9.0k, +21.7k, +29.8k, +13.9k, -5.9k, +9.7k
* White RC set H (7 variants): PRE t 3.01 p 0.01; L6M t 2.57 p 0.03; HOLD t 2.32 p 0.05
* White RC set B (7 variants): PRE t -0.27 p 0.91; L6M t 3.22 p 0.01; HOLD t 3.09 p 0.01
* White RC all 14 variants: PRE p 0.01; L6M p 0.01; HOLD p 0.02.

## 7. Selection and reading notes
* Set B is selected on looked data (the entry cells, the P book list and the loss cells were each ranked by L6M in their own sections; DIPENTRY, ADDUW and the three L2SET sections have all read these windows): its L6M/HOLD/2026 numbers are in-sample and its PRE/X' numbers are the only out-of-sample hint. Set H is selected on PRE only for E and L; its L6M/HOLD are the honest numbers.
* The profit rule's gain on the M basis is the target-fill correction artefact (an early market exit does not pay the 1.4-4.3 pt that target fills pay); the N-basis rows are the ones to believe, and they are negative for P wherever P is in.
* 2026 has about 5 real weeks: MDEs of 40-180k per week mean its sign is not information.
* Not run: DualStrat2 and DS5 books, PB/DN/MV/MA (trade-level only), the learned entry gates (dead in L2SE), thick-book profit cells beyond the plain 70% take (fail N basis in L2SP), the e2_joint WDAY-weighted stack.
