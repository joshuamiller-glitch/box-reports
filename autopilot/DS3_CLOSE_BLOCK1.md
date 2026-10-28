# DS3_CLOSE_BLOCK1 - T-CLOSE block 1 (families 3.1 MOC-reaction proxy, 3.2 last-hour continuation, 3.3 last-hour reversal) + 14:30 predictors - D3CL1, 2026-10-27
Research only. NQ direct 1-s path via the shared harness (open2, patched in-process by l2vast/ds3/code/close3/c3_patch.py; open2 untouched). Fees 4.84 RT (NQ exchange fee a PROXY). Verdict = lower tier of basis M (mapped conservative) and T (tape-direct-style).

## Verdict
**Close block 1: 0 PASS, 1 CANDIDATE, 200 DEAD** of 201 scored cells (17 signals x 12 CLOSE12 brackets = 204 prereg'd; 3 empty: C1530|VWAP, CTR|VWAP, RSTR|DAYHL had no valid trades). The CANDIDATE is **RVW1|F30** (VWAP reversion >= 1 sigma at 15:30, target/stop 30/30). It fails ONLY best-of-N. Three more cells (RVW1|BE10, RVW2|F30, RVW2|BE10) are CANDIDATE on basis M but DEAD on basis T (beats_b / stack_add_pre / year_share), so DEAD by the lower-tier rule.
30 gating cells (CLP1/CLP2, 14:30 classifier): 0 PASS, 0 CANDIDATE, 30 DEAD (x2 bases = 60 rows: 34 FILTER-ONLY, 26 NO EFFECT, 0 PREDICTOR).
Placebo (b) at the prereg draw count (64): 27 of 402 cell-bases beat (b) (the prereg gate: CI lower > 0 and rank >= .95); 375 fail (b). [Corrected 2026-10-27 in block 2: the earlier text said '5 on M and 1 on T', a substring-count slip.]

**Best NQ close book: RVW1|F30** (1-sigma VWAP reversion at 15:30, 30/30), 3.19 trades/wk, own +$2,144/wk WF (M; SD 9,585, win 60% vs required 54%, PF 1.31, 2x cost PRE +1,487/wk), **vs same-rule-random-clock +6.84 pts/trade [CI 3.06, 10.40] (rank 1.00; basis T +5.37 [1.24, 9.31])**, also beats bracket-beta (d) +7.0 [3.5, 10.2] and random-in-regime (c) +6.1 [2.5, 9.6]. Stack-add (WF, vs live stack): d mean +$2,144/wk [CI 560, 3,774], d SD -298, **d Sharpe +0.12 (T +0.09), d maxDD -$6,220 (T -$3,614)**; PRE +$3,243/wk, HOLD +$900/wk (d Sharpe +0.07), 2023-04..2024-01 +$1,107/wk; mirror -$5,107/wk. **MDE: weekly paired MDE $2,252/wk > d mean $2,144/wk, so the effect is not distinguishable from zero at the weekly level; ~157 forward weeks would be needed to settle (T: 278).** Per-trade the effect vs (b) is significant; per-week-on-the-stack it is within MDE. Best by stack-add Sharpe: RVW1|BE10 (M +0.19 WF, HOLD +$2,582/wk) but DEAD on basis T. Un-block comparison: **NOT COMPUTED in block 1** (see deviations); best overnight-hold cell: none positive worth naming (MOC10|H0930 +0.31 PRE d Sharpe on M fails beats_b rank .56, beta, year_share; H0930/H1805 rows fail every placebo).

## Why nothing is PASS: best-of-N gate behaviour (disclosed, not softened)
The family best-of-N null (201 cells, 64 (b) draws) has a p95 of 128.8 pts (M) / 123.0 (T) because tiny-n structural-target cells (C1500|VWAP, n valid small) and the overnight holds (H1805/H0930, durations not comparable under a shifted clock) produce enormous draw means. The best (b)-effect cell is C1500|VWAP (48.6 pts, rank 0.55 of its own null). Informational only: with the overnight cells removed the p95 is 72.7 (M) / 89.1 (T), still far above RVW1's 6.8. So under the harness rule NO cell can pass best-of-N in this block; the gate is uninformative here (a null maximum dominated by low-n/high-variance cells), and CANDIDATE (= fails only best-of-N) is the highest tier reachable. I did not alter the harness. The stricter-but-sensible reading is a per-bracket-class null; a lead decision item.

## Per-cell verdicts (worst of M/T; b# = number of bases, of 2, on which the cell beats placebo (b)); all 201 scored cells, full table in out/tclose_b1/cells_final.csv (402 rows with every gate, effects, MDE)
| signal | F15 | F30 | F60 | VWAP | DAYHL | T1600 | T1614 | H1805 | H0930 | STRAIL | BE10 | NOSTOP |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C1500 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| C1530 | D/b0 | D/b0 | D/b0 | empty | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| CTR | D/b0 | D/b0 | D/b0 | empty | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| FAD1 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| FAD15 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| LEXT | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| MOC10 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b1 | D/b0 |
| MOC5 | D/b0 | D/b0 | D/b0 | D/b0 | D/b1 | D/b0 | D/b0 | D/b0 | D/b0 | D/b2 | D/b1 | D/b2 |
| PIV | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| R330 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| RFAD | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| RPIN | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| RSTR | D/b0 | D/b0 | D/b0 | D/b0 | empty | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| RVW1 | D/b1 | CAND/b2 | D/b2 | D/b1 | D/b0 | D/b2 | D/b2 | D/b0 | D/b0 | D/b2 | D/b1 | D/b0 |
| RVW2 | D/b1 | D/b2 | D/b0 | D/b0 | D/b0 | D/b1 | D/b1 | D/b0 | D/b0 | D/b1 | D/b1 | D/b0 |
| U55 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| U58 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |

Gate-failure counts over 402 cell-bases: best_of_N 402, beats_beta 392, stack_add_pre 380, beats_b 375, year_share 369, cost2x_pre 287, hold 266, mean_up 248, span2 229, neighbours 133.

## Top 15 by stack-add Sharpe delta (WF 2024-02..2026-10-16, 142 wk) regardless of verdict (d mean in $/wk at fixed 10 lots; MDE and fwd weeks from the harness paired weekly difference; EVERY top cell has |d mean| at or below its MDE)
| cell | verdict (worst M/T) | trades/wk | stack-add dSharpe (WF, min M/T) | d mean $/wk (M / T) | MDE $/wk (M) | fwd weeks to settle (M) | d maxDD $ (M) | HOLD mean (M) | 2023-24 mean (M) | failed gates (M ; T) |
|---|---|---|---|---|---|---|---|---|---|---|
| RVW1|T1600 | DEAD | 3.19 | +0.13 | +3,844 / +3,086 | 4,194 | 169 | -4,275 | +2,576 | +1,092 | beats_beta,year_share,best_of_N ; beats_beta,stack_add_pre,year_share,best_of_N |
| MOC10|NOSTOP | DEAD | 2.20 | +0.13 | +2,351 / +2,579 | 2,754 | 195 | -11,942 | +1,611 | -641 | beats_b,span2,best_of_N ; beats_b,span2,best_of_N |
| MOC5|NOSTOP | DEAD | 3.40 | +0.13 | +2,046 / +2,388 | 3,268 | 362 | -13,477 | +1,384 | -1,165 | beats_beta,stack_add_pre,span2,best_of_N ; beats_beta,stack_add_pre,span2,best_of_N |
| RVW1|NOSTOP | DEAD | 3.19 | +0.13 | +3,654 / +3,109 | 4,782 | 243 | -4,275 | +3,232 | +1,187 | beats_b,beats_beta,stack_add_pre,year_share,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,best_of_N |
| MOC5|T1600 | DEAD | 3.40 | +0.12 | +1,754 / +2,047 | 3,276 | 496 | -13,477 | +1,507 | -971 | beats_b,beats_beta,stack_add_pre,year_share,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,span2,best_of_N |
| MOC10|T1600 | DEAD | 2.20 | +0.12 | +1,966 / +2,141 | 2,746 | 277 | -11,942 | +1,720 | -448 | beats_b,beats_beta,stack_add_pre,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,span2,best_of_N |
| MOC10|H0930 | DEAD | 2.20 | +0.11 | +4,175 / +4,132 | 7,490 | 457 | -18,102 | +1,760 | -2,329 | beats_b,beats_beta,stack_add_pre,year_share,hold,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,hold,span2,best_of_N |
| MOC10|STRAIL | DEAD | 2.20 | +0.11 | +2,016 / +1,993 | 2,492 | 217 | -11,942 | +1,237 | -511 | beats_b,span2,best_of_N ; beats_b,beats_beta,span2,best_of_N |
| RVW1|STRAIL | DEAD | 3.19 | +0.10 | +4,085 / +2,673 | 3,669 | 115 | -6,860 | +2,584 | +1,335 | beats_beta,year_share,best_of_N ; beats_beta,year_share,best_of_N |
| RVW1|T1614 | DEAD | 3.19 | +0.10 | +3,941 / +3,111 | 4,963 | 225 | +3,417 | +2,351 | +1,445 | beats_beta,year_share,best_of_N ; beats_beta,stack_add_pre,year_share,hold,best_of_N |
| RFAD|H0930 | DEAD | 1.37 | +0.10 | +1,911 / +2,268 | 5,576 | 1,210 | +24,097 | +740 | +497 | beats_b,beats_beta,stack_add_pre,year_share,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,best_of_N |
| RVW2|NOSTOP | DEAD | 1.56 | +0.10 | +2,471 / +1,999 | 3,787 | 334 | +6,708 | +1,988 | +1,050 | beats_b,beats_beta,stack_add_pre,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,best_of_N |
| RVW2|STRAIL | DEAD | 1.56 | +0.10 | +2,991 / +2,076 | 2,914 | 135 | +1,797 | +3,182 | +911 | beats_beta,stack_add_pre,year_share,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,best_of_N |
| RVW1|F30 | CANDIDATE | 3.19 | +0.09 | +2,144 / +1,725 | 2,252 | 157 | -6,220 | +900 | +1,107 | best_of_N ; best_of_N |
| RVW2|T1600 | DEAD | 1.56 | +0.09 | +2,489 / +1,814 | 3,332 | 254 | +6,708 | +1,992 | +1,017 | beats_beta,stack_add_pre,year_share,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,best_of_N |

Bracket-beta warning (README_OPEN2): time-exit / hold cells (T1600, T1614, NOSTOP, H*) earn a positive stack-add from convexity even for random direction; they only matter if they beat (b) AND beta (d). RVW1|T1600 and RVW1|NOSTOP beat (b) but fail beta (d).

## Family read
- 3.1 MOC-reaction proxy (MOC5, MOC10, FAD1, FAD15, U55, U58): continuation of the 15:50:30 reaction shows positive raw stack-add on the long exits (NOSTOP, T1600) but fails beta (d) and the 2023-24 second holdout (span2) everywhere; the 15:50 reaction explains the 16:00 print only weakly (below). Fades (FAD1/FAD15) have n=109/41 and nothing. U55/U58 (n 584/463): DEAD, below MDE.
- 3.2 continuation (C1500, C1530, CTR, PIV, LEXT): all DEAD, 0 cells beat (b). Directional days do not continue in the last hour at these thresholds; C1530 (VWAP-side continuation) is negative (-$12 to -14 pts/trade ungated).
- 3.3 reversal: VWAP reversion is the only live thing: RVW1 (>= 1 sigma, n=621) and RVW2 (>= 2 sigma, n=319) beat (b), beta and (c) on the F30 / BE10 / T1600 / T1614 / STRAIL brackets on basis M, positive on HOLD and on 2023-24 on all, mirror strongly negative. They die on basis T (the 15:30 entry uses the NO-QUOTE FALLBACK fill, +-1 tick and no spread model, so the T basis is the harsher and less measured one) or on year_share / beta for the time-exit variants. RSTR (n=75), R330 (n=91), RPIN (n=18, opex only), RFAD (n=242): DEAD, RSTR/R330/RPIN underpowered by construction.
- Day-type / conditioning tables (RVW1|F30, M): by year 2023 +$359, 2024 +$821, 2025 +$795, 2026 +$296 per trade (CIs include 0 in 2023 and 2026); Mon/Tue weak (+425/-31), Wed-Fri +820 to +916; VIX terciles +564/+715/+474; shorts +448, longs +793; opening type OD -1,543 (n=14, noise). All interaction tables for every cell are in out/topen_b2/grp_TCLOSE_B1/<signal>.pkl key cells[(basis,bracket)]['cond'] (year, dow, 09:35/10:00 opening type, gap class, VIX tercile, release, FOMC, opex, month-end, side).
- Power: signal counts PRE (74 wk) range 6 (RPIN) to 248 (MOC5); most per-trade MDEs (prereg tables) are 3-15 pts on 15-60 pt brackets, above any plausible edge; the nulls are "could not see an effect smaller than the MDE", not "no effect".

## 14:30 predictor tables (T-CLOSE addendum 4)
Table: out/tclose_b1/table_1430.parquet = 49 features known at 14:30 (morning path, opening type, IB, VWAP relation at 12:00 and 14:29, day range vs median, afternoon/morning volume, 1-min aggressor-delta shares, release/FOMC/opex/month-end/roll/AMC-earnings flags, prior-day type and close location, 3-day direction, week position, SMA200 distance, VIX tercile, compression forecaster); 921 full-session days. Poison audit: 40 days, bars idx >= 300 randomised: 0 changes (control poisoning from idx 290 changed 240 cells in 6 features). Labels: y1 = direction 15:00->16:00, y2 = 15:50->16:00, y3 = sign of the 15:50:00->15:50:30 reaction, y4 = 15:50:30->16:00.
Univariate tables (terciles/categories, PRE 2024-02..2025-06): out/tclose_b1/pred1430_univariate_PRE.csv; Spearman IC with Benjamini-Hochberg q: pred1430_ic_PRE.csv. Features with q < 0.10: vs the 15:00-16:00 move 0 of 49; vs the 15:50:30->16:00 move 1 (after_long_weekend, rho .19, n small); vs the 15:50:30 reaction 6 (best: 3-day direction dir3_atr rho +0.197 q .010; prior-day close location +.17 q .035; month_end +.15; day delta share -.15; compression forecaster +.14).
Classifier (LightGBM + isotonic in-window, monthly walk-forward from 2023-02, embargo 7 d, noise columns, label-permutation x100, purged 12-block OOF, no-tape control) AUC, PRE / HOLD(one look): y1 (last-hour direction) 0.442 / 0.450, permutation p 0.93; y2 0.481 / 0.447; y4 (post-reaction 15:50:30->16:00) 0.470 / 0.452, perm p 0.74; y3 (MOC-reaction direction) 0.541 / 0.533, perm p 0.02 (hit rate at P >= 0.60: 58.3% on n=144 PRE vs 53.0% base, 58.3% HOLD n=72; no-tape control 0.552, i.e. the tape features add nothing). Logistic baseline ~0.51 on y1/y2/y4. Calibration slope negative on y1/y2/y4 (the model is anti-predictive out of sample), 0.29 on y3. Features above the max noise-column importance: 0 (y1, y4).
**Honest-null statement:** nothing known at 14:30 predicts the last-hour direction or the move after the MOC reaction (AUC <= 0.51, below the permutation null, calibration slope negative, no feature above the noise columns). The only signal is the sign of the 15:50:00-15:50:30 reaction (AUC ~0.54, permutation p 0.02, 0.05-0.07 after a 4-label Bonferroni; 3-day trend is the lead feature): it is a weak lead about the reaction, not tradable at 14:30 and not a predictor of the P&L target. The family gates therefore have no predictor to gate with.
Gating test (P_side >= 0.55 / 0.60 on T1600, 10 + 5 signals x 2 thresholds x 2 bases): 0 PREDICTOR, 34 FILTER-ONLY, 26 NO EFFECT, all DEAD; gated-in means exceed the ungated means in places (e.g. U58 0.55: +0.98 vs -1.88 pts) but the random-subset p is 0.06-0.47 and the PRE CI of in-minus-out always includes 0; most gated cells are UNDERPOWERED (n_in < 40). Consistent with the addendum rule: improvements are reported as filters (trade removal), not predictors.

## MOC-proxy validity (preview of FINAL item 5)
15:50:30 reaction sign vs the 16:00 print: continuation of the reaction to 16:00 hits 55.5% (PRE n=346), 57.1% when |reaction| >= 5 pts (n=247), 53.7% on 2023-24 (50.0% for >= 5 pts, n=112). The reaction sign agrees with the day's direction only 46%/42% of days (anti-aligned, not aligned); continuation after agreement with the day direction 58.1% vs 53.2% after disagreement (PRE). The reaction sign vs the whole 15:50->16:00 move agrees 66% (mechanical: it is 30 s of that 10-minute window). A real imbalance feed would plausibly sharpen these cells (the proxy is mostly a price impulse) but nothing here indicates the proxy cells were close to a verdict.

## Deviations and disclosures (every shortcut)
1. Harness reuse via in-process monkeypatch (entries, legs, attach_levels, CORE12 replaced by c3_patch.py); the open2 kernel / lock engine / placebos / finalize are unchanged. Quote tape only 15:45-16:15 (tape_close.npz); entries earlier (C1500, C1530, CTR, PIV, LEXT, RSTR, RVW1/2, R330, RPIN) use the no-quote fallback (1-s close of the entry second; T basis +-1 tick). The RVW1/RVW2 candidates are fallback-fill cells. Bars: 1-min signals; 15:50/55/58 cells use the 1-s path. Entry/stop-entry/limit order types, bars other than 1-min/1-s, instruments other than NQ: NOT in this block.
2. FAD thresholds (1.0, 1.5)x the 20-day median 15:50 one-minute range instead of the directive's (2, 3)x (those give n = 13 and 2 over 921 days, counted without outcomes before the prereg).
3. Sizing: fixed 10 lots only (R12k/R6k/equal-risk sweep deferred to block 2). Brackets: the directive's 12-cell core; the full section-4 grid on the top 3 per family, bars x order types, day-type interactions as separate cells, footprint and L2 families: later blocks.
4. UN-BLOCK baseline (existing books flipping 15:00-16:54) NOT scored: the books' trade lists contain no entries in 15:00-17:59 (5-22 stray hour-15 rows, WINMASK false), so it needs a regeneration of the ST/KB/SM flips in the window (block 2). Stack line is cell vs LIVE stack (09:00-09:59 entries removed, flat 15:00-16:54 as live) with the harness paired bootstrap.
5. Best-of-N: harness rule applied unchanged over the 201-cell family (one pooled dir, 64 draws); its p95 is inflated by low-n and overnight cells (see above). Placebo (b) for H1805/H0930 is not like-for-like (duration-preserving shift); (d) is the operative control there.
6. Placebo (b) clock: rule anchor uniform in 11:00-13:00 (>= 60 min from the 10:00 and 14:00 releases and from 15:50/16:00), 64 draws; (a), (c), (d) 16 draws. Rules re-anchored include their normalisations (ATR20; 20-day medians at the shifted clock).
7. Classifier: SPAN2 (2023-02..2024-01) is TRAINING data for the walk-forward, so the second holdout is non-temporal OOS (purged blocks) for gating; a gated cell cannot be PASS (no placebo (b) for a 14:30-conditioned gate). Perm p for y2/y3 were added at the final stage (y1/y4 pre-planned): y3's p=0.02 is one of 4 labels.
8. Holdout: ONE logged look per prereg group (CL1-CL9, CLP1-CLP2; pre-holdout text sha256 2ee7c3543b705180f106cecfd538975f4737c38063e101b92679074b76c6302e), then HOLD read. Looks logged before HOLD was read; trials appended to the ledger (+234 cells). Memory gate: launched only with >= 32 GB available (waited); the predictor and gate jobs (light, ~4 GB) were gated identically. Slots via corepool (12 workers, waited for slots ~1h). No kills/retries, no deletions, UNTOUCHED never read, no downloads (NEEDS line appended to NEEDS.md; MOC feed not bought).
9. Data end 2026-10-16 (stack days); calendar earnings column ends ~2026-10-15.

## Preregs (sha256, all appended to DECISIONS.md before scoring)
- CL1: 0c546c6b6ab2c64f61832f12751081af5ecaeb16801725b220d84295b492c73d
- CL2: 29ba5b28d9fc96e684bd7ccde3c0765a7af9ac23efcbedf119be45a484ebf84b
- CL3: 85188e469f81a573b545000fa3e289f29c4cf69ca046e0abd91596476c674d38
- CL4: fefa833c17658e801315c9c52b6853c7e3f6398c1e6d1b5125ef4c675be1c6b9
- CL5: 1cdbdcbe8ea42d36e4c9953b2e4752999380471ee1722a3605b1158181737562
- CL6: a0bd17d3611cbb209807bbc6d9fa84e6a912b2eac01bf50a86117cd6c3476fce
- CL7: 40b745dafa43c032f43168f176ddf415f1a977e10e801086661b8935c8d4d947
- CL8: 934bdfc03ed80888561cac24977e1a753efe3d08c5740cfdbd7ca508ebb8b4fd
- CL9: 10073e539023f0ab7f6c596f8ed7140a3bb5d8b02c8bab4d1b7f9f7b6d28fe5a
- CLP1: 6b028b31fee840ae99d9fde88a8781fe597e5b6c30fb97d26eb1cdb4d0ed434c
- CLP2: c61d0ced03516f29be6793df90b3d4725254d68928ced4f5720d177edb086f12
Files: l2vast/ds3/prereg/TCLOSE_B1_CL1..9 and CLP1..2 (.md/.sha256); code l2vast/ds3/code/close3/ (c3_data, c3_patch, c3_signals, c3_audit, c3_prereg, c3_run, c3_final, c3_pred_build/_audit/_run, c3_gate_prereg, c3_gate); results l2vast/ds3/out/tclose_b1/ (cells_final.csv, tclose_b1_final.pkl, gate_final.csv, pred1430_final.json, preds_y*.parquet, audit_asof.csv, audit_pred1430.txt); per-variant pickles out/topen_b2/grp_TCLOSE_B1/. As-of audits: 17 signals x 40 days poison test 0 mismatches, positive controls flag all 17. No series produced for the sim (no PASS); RVW1|F30 spec not written (a CANDIDATE that fails best-of-N; recommended for SIM-forward only by the lead's call).

## ETA for the remaining T-CLOSE blocks (compute: each prereg group ~1-2 min per variant once slots are held; the bottleneck was slot/memory wait ~1 h)
- Block 2 (3.4 range breaks, 3.5 dip-buy/overnight-drift, 3.6 post-close/earnings, 3.7 levels, + the un-block baseline from regenerated ST/KB/SM flips, fixed-R sizing, stop-entry/limit fills): ~4-5 h of agent time.
- Block 3 (3.8 cross-asset/other closes CL/GC/ZN/6E, 3.9 footprint, 3.10 L2 mbp-10 ES/NQ at the close): ~6-8 h (needs a 15:45-16:15 mbp-10 extraction pass for the book families).
- Block 4 (full grid on top 3 per family, bars x order types, RVW1/RVW2 robustness incl. 15:30 quote-fill check, learned classifier 3.11, closes sleeve, MOC proxy validity, K4 overlap) then DS3_CLOSE_FINAL: ~8-10 h. Total ~18-23 h elapsed if slots/memory stay available.
