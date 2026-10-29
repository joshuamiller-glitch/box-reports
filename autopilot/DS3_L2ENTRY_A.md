# DS3_L2ENTRY_A - book state at the signal second: filters and sizers on live signals (L2EA, 2026-10-29)

Prereg: autopilot/L2ENTRY_A_prereg.md sha256 335650bf3bfe06a3d59d3cdc83c6abf0f79d22b9cdec4261ddd0be26945997f8 (logged in DECISIONS.md before any statistic). Research only; UNTOUCHED never read (all windows capped 2026-02-06; vs_lib HOLD has NO upper bound and was not used). Trades: 47,131 ABR trade rows (11 books, MEASURED live pts at live lots), features = l2f_at.features_at at entry_ts (sided). **2026 window = 2026-01-01..2026-02-06 = ~5 weeks (6 label weeks, n tiny): read it as a sign only.** D6 session cells and O6 are NOT scored: no signal-second trade list for them is on disk (scope gap).

Lot matching: every multiplier is divided by the book's pre-HOLD (<=2025-06-30) mean multiplier, so average risk is unchanged; rules that keep <20% of trades need >5x lots (not executable under the 50-contract cap) and are flagged NON-EXEC. E = lot-matched pts/signal added; Y = mean(kept) - mean(all) pts/trade; $/wk at live lots.

## Verdict lines (thick-book skip rel_tot8 >= 1.5; last 6 months 2025-08..2026-02-06; MDE 80% power 5% two-sided)

- **ST**: skipping signals into a thick book (rel_tot8>=1.5) keeps 96.8% of trades and adds -0.581 pts/trade in the last 6 months (MDE 0.820; n=1256; removed trades averaged +19.37 pts); HOLD -0.421; 2026 (~5 wk) +0.037. Inside the MDE: null.
- **HM**: skipping signals into a thick book (rel_tot8>=1.5) keeps 96.3% of trades and adds +0.005 pts/trade in the last 6 months (MDE 1.041; n=909; removed trades averaged +2.42 pts); HOLD -0.020; 2026 (~5 wk) -1.145. Inside the MDE: null.
- **WT**: skipping signals into a thick book (rel_tot8>=1.5) keeps 96.8% of trades and adds -0.052 pts/trade in the last 6 months (MDE 0.455; n=1706; removed trades averaged +0.83 pts); HOLD +0.020; 2026 (~5 wk) +0.312. Inside the MDE: null.
- **KB**: skipping signals into a thick book (rel_tot8>=1.5) keeps 96.7% of trades and adds +0.378 pts/trade in the last 6 months (MDE 0.843; n=1257; removed trades averaged -11.41 pts); HOLD +0.412; 2026 (~5 wk) +0.269. Inside the MDE: null.
- **SM**: skipping signals into a thick book (rel_tot8>=1.5) keeps 95.9% of trades and adds +0.538 pts/trade in the last 6 months (MDE 1.892; n=314; removed trades averaged -12.25 pts); HOLD +0.596; 2026 (~5 wk) +0.129. Inside the MDE: null.
- **PE**: skipping signals into a thick book (rel_tot8>=1.5) keeps 96.3% of trades and adds -0.447 pts/trade in the last 6 months (MDE 0.910; n=1194; removed trades averaged +10.28 pts); HOLD -0.590; 2026 (~5 wk) -0.465. Inside the MDE: null.
- **PB**: skipping signals into a thick book (rel_tot8>=1.5) keeps 97.0% of trades and adds +0.026 pts/trade in the last 6 months (MDE 0.950; n=866; removed trades averaged +3.86 pts); HOLD +0.214; 2026 (~5 wk) +0.469. Inside the MDE: null.
- **DN**: skipping signals into a thick book (rel_tot8>=1.5) keeps 90.0% of trades and adds -0.018 pts/trade in the last 6 months (MDE 2.007; n=701; removed trades averaged +4.13 pts); HOLD +0.301; 2026 (~5 wk) -1.370. Inside the MDE: null.
- **MV**: skipping signals into a thick book (rel_tot8>=1.5) keeps 96.4% of trades and adds +0.267 pts/trade in the last 6 months (MDE 0.925; n=1133; removed trades averaged -6.98 pts); HOLD +0.301; 2026 (~5 wk) -0.045. Inside the MDE: null.
- **MA**: skipping signals into a thick book (rel_tot8>=1.5) keeps 98.0% of trades and adds -0.832 pts/trade in the last 6 months (MDE 1.127; n=407; removed trades averaged +45.97 pts); HOLD -0.500; 2026 (~5 wk) -1.094. Inside the MDE: null.
- **CR**: skipping signals into a thick book (rel_tot8>=1.5) keeps 96.5% of trades and adds +0.363 pts/trade in the last 6 months (MDE 0.761; n=509; removed trades averaged -12.22 pts); HOLD +0.333; 2026 (~5 wk) +0.000. Inside the MDE: null.
- **ALL**: skipping signals into a thick book (rel_tot8>=1.5) keeps 96.2% of trades and adds -0.065 pts/trade in the last 6 months (MDE 0.294; n=10252; removed trades averaged +2.47 pts); HOLD +0.004; 2026 (~5 wk) -0.206. Inside the MDE: null.

The skipped set is only ~4-5% of signals in every book, so MDE (about 4x the effect sizes seen) rules out anything but a large thick-book effect; the pooled answer (ALL) is the line to trust.

Same with skip >=2.0 (L6M):  ST keep 99.3% Y -0.11 (MDE 0.38); HM keep 99.8% Y +0.01 (MDE 0.25); WT keep 99.5% Y -0.01 (MDE 0.17); KB keep 99.4% Y +0.06 (MDE 0.34); SM keep 99.7% Y -0.18 (MDE 0.51); PE keep 99.4% Y -0.04 (MDE 0.36); PB keep 99.4% Y -0.16 (MDE 0.41); DN keep 97.7% Y -0.10 (MDE 0.92); MV keep 99.3% Y +0.13 (MDE 0.40); MA keep 99.8% Y -0.13 (MDE 0.39); CR keep 99.6% Y -0.00 (MDE 0.25); ALL keep 99.4% Y -0.03 (MDE 0.12)

## Headline (plain)
1. **No book-state filter or sizer passes V2.** 0 PASS. Pooled over all books the thick-book skip (rel_tot8>=1.5, ~4% of signals) is -0.07 pts/trade in the last 6 months (MDE 0.29), flat in HOLD (+0.00) and 2026 (-0.21): null. Skip >=2.0 removes <1%: null. Per book every verdict line is inside its MDE (see above; MDE 0.2-2.0 pts/trade).
2. **Best-of-N (RC, ~11,000 cells per window): the only cell that clears is learned-filter CR|asia, and a shuffled-feature placebo reproduces it** (the model sees book and session ids and learned that CR in ASIA has been losing). That is session gating, not order-book content: DEAD as an L2 rule, noted for the D6 session table (CR ASIA: L6M -4.89 pts/trade).
3. **Many single rules are positive in the last 6 months (pooled CANDIDATE-RECENT: skip the top tercile of distance to the next 100-round number ahead [rnd100_ahead], of pulled_sup10, of spread_t, of pulled_opp10; skip the bottom tercile of depth_rel / vpin50)**, but all have adj RC p ~1.0, most are negative in PRE or X', and on the exact lock engine every one lowers the stack mean in the last 6 months and HOLD (-3.7k to -14.7k $/wk; inside the stack MDE ~65k). skipTop3_rnd100_ahead is the only one positive in all five of 2026/L6M/HOLD/PRE/X' pooled (E +1.80/+0.79/+0.68/+0.08/+0.49) and still fails G5 (RC) and G7 (engine -9.9k L6M, -9.0k HOLD): V2 DEAD on G7, CANDIDATE-RECENT label.
4. Thick-book skip on the engine is flat (L6M -494 $/wk, HOLD +159) with a lower L6M maxDD (277,624 vs 466,422) and SD (115.6k vs 123.0k): a tail effect inside noise, not an edge. The explicit 'book agrees' and 'thin ahead thick behind' keep-only rules give the largest pts/trade only because they keep 5-12% of trades (lot scale 8-20x): NON-EXEC.
5. Learned filter pooled: ~0 to negative L6M/HOLD (L_skip33 ALL is shown below); the walk-forward top feature is vpin50 in all 9 quarters (gain share ~5%): the book content the model finds is flow toxicity, but it does not pay. POST-HOC (read after the placebo): without id columns PE-book L_skip33 is +2.05 pts L6M / +1.61 HOLD / +0.66 PRE / +5.2 in 2026 (a lead in one of 11 books; shuffled-feature placebos for the same PE unit give +0.93 / -1.67 / +1.08 L6M, so +2.05 is not outside the placebo range; no RC credit).
6. 'Last 6 months >= 0' holds for many cells, so an entry-section candidate was written (l2vast/ds3/out/l2entry/policy_entry_candidate.txt); it is explicitly NOT live-ready (stack line negative).

## Ranked cells (RECENT FIRST: 2026 ~5 wk, last 6 months, HOLD, PRE, X', pooled history last; rank = L6M, HOLD tie-break; cells keeping <50% of trades dropped as NON-EXEC (lot scale >2x))

### Pooled all books

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| skipTop3_rnd100_ahead | ALL | 66% | 10252 | +1.80 | +0.79 | +0.84 | 1.06 | +66,789 | -37,152 | +0.68 | +0.08 | +0.49 | +0.31 | 1.9 / 1.00 | DEAD / CANDIDATE-RECENT; fails G5_RC,G7_stack(d mean L6M -9856, HOLD -9024 $/wk) |
| skipTop3_pulled_sup10 | ALL | 62% | 10252 | +0.30 | +0.73 | +0.83 | 1.16 | +37,629 | -15,312 | +0.38 | -0.16 | -0.09 | -0.01 | 0.9 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC,G7_stack(d mean L6M -6917, HOLD -8729 $/wk) |
| skipTop3_spread_t | ALL | 70% | 10252 | +1.46 | +0.69 | +0.57 | 0.97 | +54,986 | -25,856 | +0.56 | +0.04 | -0.58 | +0.04 | 1.3 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC,G7_stack(d mean L6M -3710, HOLD -2454 $/wk) |
| skipTop3_pulled_opp10 | ALL | 62% | 10252 | +0.02 | +0.63 | +0.73 | 1.15 | +26,775 | -8,157 | +0.30 | -0.22 | -0.10 | -0.07 | 0.6 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC,G7_stack(d mean L6M -9504, HOLD -9848 $/wk) |
| skipBot3_depth_rel | ALL | 60% | 10252 | +0.90 | +0.46 | +0.50 | 1.20 | +32,625 | -9,844 | +0.34 | +0.35 | -0.13 | +0.25 | 0.6 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC,G7_stack(d mean L6M -5424, HOLD -1843 $/wk) |
| skipBot3_vpin50 | ALL | 62% | 10252 | -1.42 | +0.44 | +0.39 | 1.16 | +36,245 | -8,844 | +0.18 | -0.19 | -0.50 | -0.16 | 0.7 / 1.00 | DEAD; fails G3_PRE,G4_X',G5_RC |
| PAIRx[skipBot10_rel_ahead8*doubleBot3_rnd100_ahead] | ALL | 89% | 10252 | +0.07 | +0.33 | +0.19 | 0.53 | +26,938 | -10,482 | +0.26 | +0.43 | +0.90 | +0.49 | 0.8 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| doubleTop3_rel_tot8 | ALL | 100% | 10252 | +0.02 | +0.32 | -0.00 | nan | +30,791 | +0 | +0.12 | +0.16 | +0.04 | +0.13 | 1.6 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| halveTop3_rnd100_ahead | ALL | 100% | 10252 | +0.72 | +0.32 | -0.00 | nan | +26,944 | +0 | +0.27 | +0.03 | +0.20 | +0.12 | 1.9 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipBot10_maxlv_ahead_rel | ALL | 84% | 10252 | +0.10 | +0.30 | +0.37 | 0.65 | +5,862 | -1,859 | +0.29 | -0.07 | -0.33 | -0.04 | 0.2 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| halveTop3_pulled_sup10 | ALL | 100% | 10252 | +0.12 | +0.29 | -0.00 | nan | +14,657 | +0 | +0.15 | -0.06 | -0.03 | -0.01 | 0.9 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| skipBot10_maxlv_behind_rel | ALL | 86% | 10252 | +0.13 | +0.28 | +0.33 | 0.60 | +23,123 | -18,315 | +0.27 | +0.18 | -0.22 | +0.12 | 1.2 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| halveTop3_spread_t | ALL | 100% | 10252 | +0.57 | +0.27 | -0.00 | nan | +21,510 | +0 | +0.22 | +0.01 | -0.22 | +0.01 | 1.2 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| doubleBot3_pulled_opp10 | ALL | 100% | 10252 | +0.06 | +0.25 | -0.00 | nan | +5,862 | +0 | +0.11 | +0.12 | +0.23 | +0.14 | 0.3 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| halveTop3_pulled_opp10 | ALL | 100% | 10252 | +0.01 | +0.25 | -0.00 | nan | +10,315 | +0 | +0.12 | -0.09 | -0.04 | -0.03 | 0.6 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| PAIRx[doubleTop3_rel_behind8*doubleBot3_rnd100_ahead] | ALL | 100% | 10252 | -0.63 | +0.25 | -0.00 | nan | +21,920 | +0 | +0.12 | +0.54 | +0.67 | +0.46 | 0.6 / 1.00 | CANDIDATE (G7 engine not run: tier pending); fails G5_RC |
| doubleTop3_rel_ahead8 | ALL | 100% | 10252 | +0.22 | +0.23 | -0.00 | nan | +22,604 | +0 | +0.08 | +0.12 | +0.14 | +0.11 | 0.9 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipBot3_rel_ahead8 | ALL | 61% | 10252 | +1.19 | +0.23 | +0.24 | 1.17 | +13,549 | +2,443 | +0.05 | +0.38 | -0.20 | +0.18 | 0.3 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| PAIRs[skipBot10_rel_ahead8|doubleTop3_rel_behind8] | ALL | 89% | 10252 | +0.16 | +0.22 | +0.19 | 0.53 | +16,563 | -10,482 | +0.09 | +0.28 | +0.32 | +0.24 | 0.8 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| PAIRs[skipBot10_rel_ahead8|doubleBot3_rnd100_ahead] | ALL | 89% | 10252 | +0.16 | +0.22 | +0.19 | 0.53 | +16,563 | -10,482 | +0.09 | +0.28 | +0.32 | +0.24 | 0.8 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipBot10_rel_ahead8 | ALL | 89% | 10252 | +0.16 | +0.22 | +0.19 | 0.53 | +16,563 | -10,482 | +0.09 | +0.28 | +0.32 | +0.24 | 0.8 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| PAIRx[doubleBot3_rnd100_ahead*skipBot10_rel_tot8] | ALL | 89% | 10252 | -0.05 | +0.21 | +0.04 | 0.52 | +15,749 | +830 | +0.11 | +0.51 | +0.64 | +0.44 | 0.4 / 1.00 | CANDIDATE (G7 engine not run: tier pending); fails G5_RC |
| PAIRx[skipBot10_rel_ahead8*doubleTop3_rel_behind8] | ALL | 89% | 10252 | -0.41 | +0.21 | +0.19 | 0.53 | +19,219 | -10,482 | -0.09 | +0.54 | +0.42 | +0.36 | 0.6 / 1.00 | DEAD; fails G2_HOLD,G5_RC |
| PAIRx[skipBot3_rel_behind8*doubleBot3_rnd100_ahead] | ALL | 64% | 10252 | +0.87 | +0.20 | -0.11 | 1.12 | +34,079 | +4,239 | +0.02 | +0.91 | +0.06 | +0.52 | 0.6 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| doubleBot3_pulled_sup10 | ALL | 100% | 10252 | -0.28 | +0.20 | -0.00 | nan | +9,947 | +0 | +0.08 | +0.11 | +0.32 | +0.14 | 0.5 / 1.00 | CANDIDATE (G7 engine not run: tier pending); fails G5_RC |

### Book ST

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| skipTop3_imb10 | ST | 64% | 1256 | +2.51 | +1.92 | +1.89 | 3.36 | +17,234 | -5,485 | +1.78 | -0.04 | -1.78 | +0.11 | 1.7 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| skipTop3_intens_rel | ST | 65% | 1256 | +2.43 | +1.81 | +1.96 | 3.33 | +16,258 | -6,043 | +1.40 | -0.40 | -0.19 | +0.10 | 1.5 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| skipTop3_spread_t | ST | 67% | 1256 | +5.39 | +1.18 | +1.00 | 3.18 | +10,607 | -912 | +1.41 | +0.45 | -1.61 | +0.32 | 0.9 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipBot3_maxlv_ahead_rel | ST | 54% | 1256 | +0.22 | +1.02 | +1.63 | 4.17 | +9,175 | -859 | +1.36 | +0.74 | -1.47 | +0.49 | 0.7 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| agree_double0.2 | ST | 100% | 1256 | -0.37 | +1.00 | +0.00 | nan | +8,997 | +0 | +0.87 | +0.02 | -0.27 | +0.18 | 1.9 / 1.00 | DEAD; fails G4_X',G5_RC |
| skipTop3_rnd100_ahead | ST | 66% | 1256 | +2.03 | +0.97 | +1.04 | 3.26 | +8,741 | -921 | +0.93 | -0.28 | +0.74 | +0.22 | 1.0 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |

### Book HM

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| skipTop3_spread_t | HM | 69% | 909 | +2.18 | +2.55 | +2.26 | 3.53 | +16,573 | -5,005 | +1.77 | -0.11 | -1.31 | +0.10 | 2.4 / 0.96 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| skipTop3_depth_rel | HM | 72% | 909 | +2.83 | +1.75 | +1.64 | 3.32 | +11,343 | -2,931 | +1.62 | -0.25 | +0.80 | +0.42 | 1.6 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| skipBot3_pulled_sup10 | HM | 72% | 909 | +2.47 | +1.64 | +1.58 | 3.27 | +10,635 | -2,833 | +1.31 | -0.41 | +0.56 | +0.21 | 1.5 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| skipBot3_intens_rel | HM | 69% | 909 | +5.34 | +1.32 | +1.07 | 3.53 | +8,558 | +305 | +0.90 | +0.37 | +0.59 | +0.55 | 0.9 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| doubleTop3_maxlv_behind_rel | HM | 100% | 909 | -0.89 | +1.27 | +0.00 | nan | +8,231 | +0 | +1.35 | +0.15 | -0.32 | +0.35 | 1.9 / 1.00 | DEAD; fails G4_X',G5_RC |
| skipBot3_pulled_opp10 | HM | 73% | 909 | +2.88 | +1.26 | +1.15 | 3.20 | +8,164 | -1,001 | +0.97 | -0.43 | +0.41 | +0.08 | 1.0 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |

### Book WT

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| skipBot3_depth_rel | WT | 59% | 1706 | +1.92 | +1.27 | +1.30 | 2.06 | +20,168 | -17,007 | +1.04 | +0.04 | +0.88 | +0.45 | 2.1 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipBot3_vpin50 | WT | 61% | 1706 | -0.61 | +1.06 | +1.04 | 1.98 | +16,767 | -14,645 | +0.74 | +0.37 | -0.15 | +0.36 | 1.6 / 1.00 | DEAD; fails G4_X',G5_RC |
| PAIRx[skipBot3_rel_behind8*doubleBot3_rnd100_ahead] | WT | 61% | 1706 | +2.86 | +0.86 | +0.51 | 1.98 | +13,545 | -9,494 | +0.72 | +0.69 | +1.41 | +0.84 | 1.1 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipTop10_pulled_opp10 | WT | 85% | 1706 | +1.37 | +0.79 | +0.79 | 1.04 | +12,507 | -12,418 | +0.52 | -0.20 | +0.46 | +0.10 | 1.8 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| PAIRx[doubleBot3_rnd100_ahead*skipBot10_rel_tot8] | WT | 88% | 1706 | +1.83 | +0.78 | +0.57 | 0.91 | +12,313 | -9,276 | +0.70 | +0.68 | +1.00 | +0.75 | 1.6 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| PAIRs[skipBot10_rel_behind8|skipBot10_rel_tot8] | WT | 85% | 1706 | +0.82 | +0.58 | +0.58 | 1.03 | +9,113 | -9,553 | +0.41 | +0.27 | +0.10 | +0.27 | 1.3 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |

### Book KB

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| skipBot3_es_imb5 | KB | 67% | 1257 | +2.56 | +1.99 | +2.09 | 3.16 | +17,856 | -13,992 | +2.09 | +1.13 | +0.32 | +1.22 | 1.7 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipTop3_rnd100_ahead | KB | 65% | 1257 | +1.50 | +1.78 | +1.83 | 3.32 | +15,943 | -12,124 | +1.51 | +1.23 | -1.92 | +0.71 | 1.5 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipBot3_vpin50 | KB | 61% | 1257 | -2.24 | +1.43 | +1.38 | 3.66 | +12,853 | -9,122 | +1.27 | +0.09 | +0.75 | +0.51 | 1.0 / 1.00 | CANDIDATE (G7 engine not run: tier pending); fails G5_RC |
| doubleTop3_es_imb5 | KB | 100% | 1257 | +2.59 | +1.41 | +0.00 | nan | +12,625 | +0 | +1.26 | +0.09 | +1.01 | +0.55 | 2.6 / 0.92 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipTop3_pulled_opp10 | KB | 60% | 1257 | +3.98 | +1.32 | +1.39 | 3.67 | +11,832 | -9,145 | +1.16 | -0.28 | +0.94 | +0.31 | 1.1 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| skipTop3_pulled_sup10 | KB | 60% | 1257 | +3.95 | +1.31 | +1.37 | 3.67 | +11,806 | -9,061 | +1.27 | -0.15 | +0.57 | +0.34 | 1.1 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |

### Book SM

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| skipTop3_depth_rel | SM | 71% | 314 | +3.98 | +3.38 | +3.38 | 5.77 | +7,570 | -5,271 | +2.78 | -0.45 | +4.53 | +1.52 | 1.6 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| skipTop3_imb10 | SM | 65% | 314 | +3.88 | +2.39 | +2.45 | 6.68 | +5,370 | -3,411 | +2.73 | -1.92 | -0.79 | -0.64 | 0.8 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| PAIRx[skipBot10_rel_ahead8*skipBot10_rel_tot8] | SM | 84% | 314 | +1.94 | +2.32 | +2.35 | 3.96 | +5,195 | -4,358 | +2.43 | +0.40 | -0.54 | +0.59 | 1.8 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| PAIRs[skipBot10_rel_ahead8|skipBot10_rel_tot8] | SM | 84% | 314 | +1.94 | +2.32 | +2.35 | 3.96 | +5,195 | -4,358 | +2.43 | +0.40 | -0.54 | +0.59 | 1.8 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipBot3_intens_rel | SM | 70% | 314 | +0.22 | +2.26 | +2.16 | 5.90 | +5,064 | -3,277 | +0.69 | -0.71 | +3.12 | +0.58 | 1.2 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| PAIRx[skipBot10_rel_ahead8*doubleBot3_rnd100_ahead] | SM | 88% | 314 | -1.94 | +2.21 | +1.92 | 3.43 | +4,948 | -3,717 | +2.58 | -0.80 | +1.52 | +0.52 | 1.2 / 1.00 | DEAD; fails G3_PRE,G5_RC |

### Book PE

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| skipBot3_depth_rel | PE | 61% | 1194 | +3.57 | +3.32 | +3.33 | 3.70 | +28,298 | -22,078 | +3.38 | +0.83 | -3.10 | +0.72 | 2.2 / 0.99 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipTop3_pulled_opp10 | PE | 60% | 1194 | +1.76 | +3.01 | +3.13 | 3.76 | +25,671 | -20,923 | +2.38 | -0.56 | -2.99 | -0.30 | 2.5 / 0.94 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| skipTop3_pulled_sup10 | PE | 59% | 1194 | +2.73 | +2.98 | +3.14 | 3.86 | +25,433 | -20,772 | +2.43 | -0.18 | -2.98 | -0.07 | 2.6 / 0.92 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| PAIRx[skipBot3_rel_behind8*doubleTop3_rel_behind8] | PE | 65% | 1194 | +3.46 | +2.49 | +1.08 | 3.44 | +21,201 | -10,195 | +2.32 | +0.14 | -1.76 | +0.32 | 1.9 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipBot3_rel_ahead8 | PE | 62% | 1194 | +5.66 | +2.24 | +2.24 | 3.63 | +19,107 | -16,426 | +2.63 | +0.44 | -1.80 | +0.56 | 1.5 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| PAIRx[skipBot10_rel_ahead8*doubleTop3_rel_behind8] | PE | 89% | 1194 | +1.49 | +2.22 | +1.18 | 1.67 | +18,915 | -10,282 | +2.15 | +0.60 | -0.20 | +0.83 | 3.0 / 0.71 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |

### Book PB

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| skipBot3_imb5 | PB | 67% | 866 | +3.36 | +4.21 | +4.06 | 3.79 | +26,062 | -7,257 | +3.75 | +1.12 | +1.27 | +1.78 | 2.4 / 0.97 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipTop3_rnd50_ahead | PB | 70% | 866 | +2.51 | +2.85 | +2.59 | 3.53 | +17,640 | -2,573 | +3.18 | +0.43 | -0.79 | +0.84 | 2.2 / 0.99 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipTop3_maxlv_ahead_rel | PB | 81% | 866 | +2.58 | +1.85 | +0.92 | 2.63 | +11,424 | +941 | +1.19 | +0.51 | -0.98 | +0.37 | 2.1 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| halveBot3_imb5 | PB | 100% | 866 | +1.34 | +1.67 | +0.00 | nan | +10,348 | +0 | +1.49 | +0.44 | +0.50 | +0.70 | 2.4 / 0.97 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipBot3_vpin50 | PB | 64% | 866 | -5.69 | +1.66 | +1.27 | 4.08 | +10,239 | +5,544 | +0.78 | -0.87 | -1.40 | -0.58 | 1.0 / 1.00 | DEAD; fails G3_PRE,G4_X',G5_RC |
| skipTop10_rnd50_ahead | PB | 91% | 866 | +1.59 | +1.53 | +1.45 | 1.69 | +9,479 | -5,585 | +1.46 | +0.42 | +0.64 | +0.71 | 2.3 / 0.98 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |

### Book DN

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| skipBot3_imb10 | DN | 81% | 701 | +7.48 | +2.58 | +1.61 | 2.96 | +12,897 | -2,663 | +1.85 | -0.04 | -1.81 | +0.02 | 1.9 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| skipTop3_spread_t | DN | 79% | 701 | +7.94 | +2.51 | +1.41 | 3.08 | +12,550 | -1,501 | +1.86 | -0.76 | -0.26 | -0.02 | 1.5 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| skipTop3_pulled_opp10 | DN | 61% | 701 | +3.08 | +2.12 | +2.74 | 4.86 | +10,603 | -499 | +1.27 | -1.26 | +0.08 | -0.36 | 1.2 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| skipTop3_rnd100_ahead | DN | 68% | 701 | +9.08 | +1.82 | +1.75 | 4.12 | +9,132 | +356 | +1.61 | -0.89 | +2.23 | +0.40 | 1.2 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| PAIRx[skipBot3_rel_behind8*doubleBot3_rnd100_ahead] | DN | 65% | 701 | +9.45 | +1.72 | +1.08 | 4.40 | +8,614 | +3,402 | +0.64 | +0.54 | +0.22 | +0.49 | 0.9 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| PAIRx[skipBot3_rel_behind8*skipBot10_rel_ahead8] | DN | 62% | 701 | +6.61 | +1.46 | +1.34 | 4.67 | +7,294 | +3,261 | +0.60 | +0.79 | +0.50 | +0.68 | 1.0 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |

### Book MV

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| skipTop3_es_imb5 | MV | 68% | 1133 | +5.83 | +2.49 | +2.53 | 3.30 | +20,138 | -13,532 | +2.37 | +0.06 | -1.61 | +0.30 | 2.0 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipTop3_rnd100_ahead | MV | 66% | 1133 | +5.36 | +2.34 | +2.42 | 3.46 | +18,958 | -12,501 | +1.85 | -0.35 | -0.27 | +0.20 | 2.2 / 0.99 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| skipTop3_depth_rel | MV | 70% | 1133 | +2.05 | +1.94 | +1.93 | 3.11 | +15,688 | -10,653 | +2.57 | -1.46 | +0.56 | -0.09 | 2.3 / 0.98 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| skipTop3_rel_behind8 | MV | 66% | 1133 | +2.79 | +1.30 | +1.35 | 3.43 | +10,525 | -6,827 | +2.05 | -1.14 | -0.21 | -0.19 | 1.1 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| doubleBot3_imb10 | MV | 100% | 1133 | -0.06 | +1.19 | +0.00 | nan | +9,604 | +0 | +1.26 | -0.87 | +0.96 | +0.00 | 1.6 / 1.00 | DEAD; fails G3_PRE,G5_RC |
| skipTop10_rel_tot8 | MV | 92% | 1133 | +0.60 | +1.18 | +1.16 | 1.44 | +9,550 | -8,487 | +1.24 | +0.11 | +0.01 | +0.36 | 2.1 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |

### Book MA

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L_skip33 | MA | 78% | 407 | +3.04 | +3.17 | +3.27 | 4.18 | +9,215 | -4,643 | +3.92 | -1.68 | +0.08 | +0.03 | 1.9 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| PAIRx[skipBot3_rel_behind8*doubleTop3_rel_behind8] | MA | 64% | 407 | +6.66 | +2.81 | +1.22 | 6.02 | +8,171 | +2,472 | +1.85 | +1.15 | -0.54 | +0.89 | 1.2 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| PAIRx[skipBot10_rel_ahead8*doubleTop3_rel_behind8] | MA | 88% | 407 | +2.12 | +2.51 | +1.16 | 2.98 | +7,286 | -1,368 | +1.90 | +1.19 | -1.71 | +0.63 | 1.6 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| PAIRx[doubleTop3_rel_behind8*doubleBot3_rnd100_ahead] | MA | 100% | 407 | +1.87 | +2.50 | +0.00 | nan | +7,279 | +0 | +1.83 | +0.07 | +0.13 | +0.49 | 2.0 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipTop3_intens_rel | MA | 64% | 407 | +3.43 | +2.44 | +2.78 | 6.02 | +7,100 | -409 | +2.04 | +0.67 | +0.74 | +1.00 | 1.0 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipBot3_depth_rel | MA | 56% | 407 | +3.69 | +2.38 | +3.55 | 7.02 | +6,929 | -123 | +1.67 | +0.62 | +2.20 | +1.25 | 1.2 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |

### Book CR

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| skipBot3_imb10 | CR | 70% | 509 | +1.42 | +1.90 | +1.92 | 2.63 | +18,144 | -26,299 | +1.59 | +1.21 | +0.43 | +1.07 | 1.4 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipBot3_imb5 | CR | 68% | 509 | +1.29 | +1.52 | +1.53 | 2.73 | +6,585 | -18,503 | +0.94 | +0.71 | +0.91 | +0.82 | 0.5 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipTop3_depth_rel | CR | 68% | 509 | +0.78 | +1.25 | +1.25 | 2.72 | +9,547 | -20,028 | +0.94 | +0.14 | -0.33 | +0.18 | 0.6 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipBot3_pulled_opp10 | CR | 70% | 509 | +0.86 | +1.19 | +1.18 | 2.59 | +26,766 | -31,486 | +1.04 | +0.80 | -0.20 | +0.56 | 2.4 / 0.96 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipTop3_intens_rel | CR | 65% | 509 | +7.85 | +1.13 | +1.04 | 2.90 | +3,924 | -15,723 | +0.88 | +0.06 | +0.39 | +0.33 | 0.3 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipBot3_maxlv_behind_rel | CR | 53% | 509 | -2.82 | +1.12 | +0.81 | 3.71 | +6,022 | -18,159 | +0.89 | +0.78 | +0.40 | +0.70 | 0.3 / 1.00 | CANDIDATE (G7 engine not run: tier pending); fails G5_RC |

### Session column: book x entry session cells (n L6M >= 100, keep >= 50%), top 25 by L6M E

### Session cells

| rule | unit | keep L6M | n L6M | 2026 E | L6M E | L6M Y | MDE(Y) | L6M $/wk | removed $/wk | HOLD E | PRE E | X' E | pooled E | t L6M / adj p | tier / failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| skipBot3_imb10 | DN|asia | 72% | 180 | +16.37 | +8.42 | +7.73 | 7.49 | +10,831 | -3,960 | +7.18 | -0.64 | -1.21 | +1.13 | 3.1 / 0.61 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| skipTop3_maxlv_ahead_rel | PB|asia | 74% | 247 | +12.14 | +7.71 | +6.67 | 6.03 | +13,609 | -4,642 | +5.97 | +1.27 | -1.68 | +1.81 | 2.7 / 0.89 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipBot3_imb5 | DN|nypm | 85% | 104 | +7.10 | +7.53 | +4.77 | 6.27 | +5,591 | -2,169 | +7.78 | -1.62 | +0.04 | +0.74 | 2.6 / 0.89 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| PAIRx[skipBot3_rel_behind8*skipBot10_rel_ahead8] | DN|asia | 66% | 180 | +18.94 | +7.37 | +6.16 | 8.53 | +9,476 | -1,453 | +6.46 | -3.84 | +5.05 | +0.88 | 2.0 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| PAIRs[skipBot3_rel_behind8|skipBot10_rel_ahead8] | DN|asia | 66% | 180 | +18.94 | +7.37 | +6.16 | 8.53 | +9,476 | -1,453 | +6.46 | -3.84 | +5.05 | +0.88 | 2.0 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| skipBot3_vpin50 | KB|asia | 64% | 335 | +2.15 | +7.35 | +6.63 | 6.63 | +17,596 | -10,946 | +7.07 | +0.27 | +1.43 | +2.28 | 2.6 / 0.91 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipBot3_rel_ahead8 | MA|asia | 59% | 145 | +15.87 | +7.29 | +7.92 | 11.21 | +7,553 | -5,243 | +4.18 | -1.92 | +1.70 | +0.56 | 2.1 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| skipTop3_es_imb5 | MV|london | 68% | 230 | +7.09 | +6.88 | +6.95 | 7.31 | +11,298 | -6,629 | +6.41 | -0.36 | -5.14 | +0.66 | 2.9 / 0.73 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| skipBot3_rel_ahead8 | ST|asia | 66% | 311 | +12.62 | +6.45 | +6.00 | 6.71 | +14,321 | -9,275 | +4.48 | +0.45 | -5.29 | +0.45 | 2.0 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipBot3_rel_ahead8 | PE|asia | 63% | 327 | +5.50 | +6.38 | +6.24 | 6.86 | +14,908 | -8,293 | +5.67 | +0.97 | -5.86 | +0.94 | 2.3 / 0.98 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| PAIRx[skipBot3_rel_behind8*doubleBot3_rnd100_ahead] | PE|london | 63% | 221 | +8.97 | +6.32 | +3.91 | 8.42 | +9,976 | -2,681 | +7.05 | +0.15 | +3.38 | +2.30 | 1.9 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| PAIRx[skipBot3_rel_behind8*doubleTop3_rel_behind8] | DN|asia | 69% | 180 | +20.25 | +5.85 | +3.09 | 8.01 | +7,518 | +734 | +4.28 | -3.36 | +3.74 | +0.26 | 1.3 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| skipTop3_spread_t | DN|london | 69% | 150 | -1.76 | +5.83 | +5.34 | 8.79 | +6,251 | -2,609 | +4.04 | -2.04 | +1.22 | -0.01 | 1.5 / 1.00 | DEAD; fails G3_PRE,G5_RC |
| PAIRx[skipBot3_rel_behind8*doubleTop3_rel_behind8] | MV|asia | 72% | 305 | +0.61 | +5.83 | +3.41 | 5.86 | +12,698 | -5,662 | +4.07 | +1.05 | +1.01 | +1.81 | 2.1 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipTop3_imb10 | DN|nyam | 52% | 229 | +8.54 | +5.64 | +6.38 | 10.29 | +9,226 | -7,593 | +7.34 | +0.66 | +0.63 | +2.40 | 1.8 / 1.00 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipBot3_intens_rel | DN|asia | 69% | 180 | +8.44 | +5.63 | +5.04 | 7.91 | +7,238 | -1,090 | +4.68 | +0.03 | -1.28 | +0.85 | 2.0 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipBot3_imb5 | PB|nypm | 63% | 163 | +2.17 | +5.57 | +5.84 | 9.11 | +6,480 | -3,921 | +4.49 | +4.34 | -1.49 | +3.02 | 1.8 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| PAIRx[skipBot3_rel_behind8*doubleBot3_rnd100_ahead] | DN|asia | 69% | 180 | +22.80 | +5.45 | +3.09 | 8.01 | +7,012 | +734 | +4.90 | -4.74 | +5.90 | +0.24 | 1.3 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G5_RC |
| skipBot3_maxlv_behind_rel | DN|asia | 78% | 180 | +10.86 | +5.44 | +4.13 | 6.37 | +6,996 | -1,651 | +3.77 | +1.40 | -1.94 | +1.15 | 1.9 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| skipBot3_vpin50 | PB|nyam | 73% | 221 | -4.15 | +5.38 | +3.94 | 6.54 | +8,489 | -3,383 | +3.78 | +1.23 | +0.39 | +1.64 | 1.9 / 1.00 | CANDIDATE (G7 engine not run: tier pending); fails G5_RC |
| skipBot3_depth_rel | PE|asia | 64% | 327 | +3.07 | +5.35 | +5.16 | 6.82 | +12,492 | -6,741 | +4.95 | -1.13 | -6.43 | -0.50 | 2.0 / 1.00 | DEAD / CANDIDATE-RECENT; fails G3_PRE,G4_X',G5_RC |
| skipBot3_es_imb5 | DN|asia | 55% | 180 | -1.54 | +5.34 | +8.85 | 10.78 | +6,860 | -1,236 | +4.14 | -0.39 | -1.11 | +0.54 | 2.1 / 1.00 | DEAD; fails G3_PRE,G4_X',G5_RC |
| skipBot3_intens_rel | HM|nypm | 76% | 178 | +12.84 | +5.30 | +4.65 | 6.25 | +6,744 | -4,749 | +4.01 | +1.84 | -1.80 | +1.53 | 1.8 / 1.00 | DEAD / CANDIDATE-RECENT; fails G4_X',G5_RC |
| PAIRx[skipBot3_rel_behind8*doubleBot3_rnd100_ahead] | MV|asia | 72% | 305 | +0.71 | +5.23 | +3.41 | 5.86 | +11,396 | -5,662 | +4.61 | +4.36 | +0.88 | +3.77 | 2.2 / 0.99 | CANDIDATE (G7 engine not run: tier pending) / CANDIDATE-RECENT; fails G5_RC |
| skipBot3_rnd50_ahead | KB|nypm | 68% | 235 | -0.83 | +5.22 | +5.12 | 6.89 | +8,761 | -5,454 | +6.12 | -2.69 | +4.83 | +0.79 | 1.5 / 1.00 | DEAD; fails G3_PRE,G5_RC |

A session cell is registered as a session book only if it clears RC: the largest studentised mean over the whole family (L6M weeks) is t=5.33 against a bootstrap-max 95% of 4.13; HOLD t=6.44 vs 4.19. Cells at t=3.0-3.6 (e.g. PB|nyam doubleBot3_maxlv_behind_rel, KB|london doubleTop3_rnd50_ahead) have adj p 0.3-0.6, and a SHUFFLED-FEATURE placebo reaches t=3.6 (ST|nyam PL103_L_skip20): noise level.

Best-of-N White RC (eligible cells: unit>=100 trades and >=8 non-zero weeks; first pass without eligibility floor was degenerate and replaced, ea_rc.py): L6M 10972 cells, HOLD 12027 cells. Only the CR|asia learned-filter cell clears it (below); everything else adj p >= 0.13.

## F4 learned filter (LightGBM, walk-forward quarterly re-fit) vs shuffled-feature placebo

| variant | unit | 2026 E | L6M E | HOLD E | PRE E | pooled E | keep L6M | L6M $/wk | HOLD $/wk |
|---|---|---|---|---|---|---|---|---|---|
| L_skip20 | ALL | +0.29 | -0.18 | -0.15 | +0.06 | -0.00 | 90% | -9,924 | -6,760 |
| PL101_L_skip20 | ALL | +0.62 | +0.32 | +0.36 | -0.23 | -0.04 | 88% | +29,986 | +34,031 |
| PL102_L_skip20 | ALL | +0.26 | +0.02 | -0.00 | +0.03 | +0.01 | 90% | -6,617 | -5,338 |
| PL103_L_skip20 | ALL | +0.03 | +0.04 | -0.05 | +0.19 | +0.11 | 91% | +1,518 | -5,647 |
| L_skip20 | CR|asia | +2.91 | +0.93 | +0.94 | +0.69 | +0.64 | 91% | +5,284 | +5,886 |
| PL101_L_skip20 | CR|asia | +3.04 | +1.13 | +1.12 | -0.28 | +0.24 | 86% | +3,657 | +5,013 |
| PL102_L_skip20 | CR|asia | +0.57 | -0.20 | -0.01 | +1.73 | +0.92 | 93% | -3,217 | -1,882 |
| PL103_L_skip20 | CR|asia | -2.13 | -1.28 | -1.06 | +0.24 | -0.15 | 93% | -2,616 | -1,501 |
| L_skip20 | CR | +2.60 | +0.50 | +0.47 | -0.52 | -0.16 | 90% | +5,665 | +6,008 |
| PL101_L_skip20 | CR | +2.27 | +0.57 | +0.61 | -1.01 | -0.42 | 86% | +7,618 | +9,430 |
| PL102_L_skip20 | CR | -0.04 | -0.67 | -0.47 | +1.07 | +0.42 | 91% | -11,988 | -7,958 |
| PL103_L_skip20 | CR | -2.83 | -0.95 | -0.84 | +0.15 | -0.12 | 92% | -5,108 | -4,974 |
| L_skip33 | ALL | +1.71 | +0.07 | +0.29 | -0.11 | -0.04 | 72% | +14,173 | +36,053 |
| PL101_L_skip33 | ALL | +0.38 | +0.45 | +0.55 | -0.32 | -0.06 | 70% | +30,922 | +39,317 |
| PL102_L_skip33 | ALL | +0.09 | +0.04 | +0.03 | -0.21 | -0.11 | 75% | +1,443 | -2,720 |
| PL103_L_skip33 | ALL | +0.22 | +0.50 | +0.39 | +0.19 | +0.19 | 78% | +47,993 | +38,792 |
| L_skip33 | CR|asia | +6.54 | +3.06 | +3.11 | -0.52 | +0.67 | 68% | +18,935 | +21,626 |
| PL101_L_skip33 | CR|asia | +4.05 | +3.00 | +2.50 | +0.03 | +0.78 | 68% | +14,014 | +12,359 |
| PL102_L_skip33 | CR|asia | -5.42 | -0.25 | -0.41 | +0.43 | +0.22 | 70% | -42 | -3,198 |
| PL103_L_skip33 | CR|asia | +1.36 | -0.34 | -0.18 | +1.31 | +0.70 | 82% | -267 | +1,264 |
| L_skip33 | CR | +2.90 | +0.61 | +0.85 | -0.78 | -0.22 | 68% | +9,532 | +16,365 |
| PL101_L_skip33 | CR | +2.18 | +0.52 | +0.49 | -1.25 | -0.59 | 68% | -3,500 | -642 |
| PL102_L_skip33 | CR | -1.74 | -0.41 | -0.38 | +0.14 | -0.06 | 72% | -5,148 | -8,493 |
| PL103_L_skip33 | CR | +0.43 | +0.49 | +0.48 | +0.40 | +0.20 | 80% | +11,374 | +11,391 |
| L_hd33 | ALL | +0.96 | +0.02 | +0.13 | +0.13 | +0.14 | 100% | +10,796 | +20,377 |
| PL101_L_hd33 | ALL | +0.31 | +0.21 | +0.25 | -0.16 | +0.00 | 100% | +11,230 | +12,911 |
| PL102_L_hd33 | ALL | -0.35 | -0.05 | -0.13 | -0.16 | -0.07 | 100% | -12,546 | -19,725 |
| PL103_L_hd33 | ALL | +0.33 | +0.11 | +0.14 | +0.28 | +0.23 | 100% | +1,678 | +4,582 |
| L_hd33 | CR|asia | +0.60 | +1.61 | +1.67 | -0.45 | +0.19 | 100% | +8,044 | +9,617 |
| PL101_L_hd33 | CR|asia | +2.33 | +0.87 | +0.51 | -1.12 | -0.46 | 100% | +2,627 | +609 |
| PL102_L_hd33 | CR|asia | -3.31 | -0.89 | -0.63 | +1.01 | +0.43 | 100% | -5,346 | -4,542 |
| PL103_L_hd33 | CR|asia | -0.69 | -1.72 | -1.46 | +0.94 | +0.02 | 100% | -8,906 | -7,921 |
| L_hd33 | CR | -0.34 | +0.77 | +0.78 | -0.46 | -0.01 | 100% | +11,868 | +13,153 |
| PL101_L_hd33 | CR | +1.71 | +0.13 | +0.07 | -1.01 | -0.48 | 100% | -4,886 | -5,418 |
| PL102_L_hd33 | CR | -0.60 | -0.36 | -0.36 | +0.81 | +0.39 | 100% | -11,617 | -12,199 |
| PL103_L_hd33 | CR | -1.92 | +0.44 | +0.46 | +0.66 | +0.41 | 100% | -5,054 | -4,151 |
| L_hd20 | ALL | +0.46 | +0.03 | -0.01 | +0.32 | +0.21 | 100% | +7,199 | +4,064 |
| PL101_L_hd20 | ALL | -0.10 | +0.15 | +0.22 | -0.02 | +0.07 | 100% | +8,931 | +12,031 |
| PL102_L_hd20 | ALL | -0.47 | -0.24 | -0.31 | +0.13 | +0.03 | 100% | -21,898 | -26,989 |
| PL103_L_hd20 | ALL | +0.12 | -0.20 | -0.19 | +0.18 | +0.08 | 100% | -20,091 | -20,030 |
| L_hd20 | CR|asia | +0.86 | +0.36 | +0.39 | +1.16 | +0.67 | 100% | +2,710 | +3,339 |
| PL101_L_hd20 | CR|asia | -0.94 | -0.57 | -0.46 | -0.31 | -0.29 | 100% | -3,166 | -2,860 |
| PL102_L_hd20 | CR|asia | -0.10 | -0.54 | -0.48 | +0.54 | +0.14 | 100% | -2,423 | -2,697 |
| PL103_L_hd20 | CR|asia | -1.66 | -1.36 | -1.21 | +0.14 | -0.30 | 100% | -5,056 | -5,468 |
| L_hd20 | CR | +0.49 | +0.48 | +0.42 | -0.22 | +0.01 | 100% | +6,505 | +6,572 |
| PL101_L_hd20 | CR | -0.07 | -0.10 | -0.12 | -0.93 | -0.50 | 100% | -2,724 | -4,134 |
| PL102_L_hd20 | CR | -0.36 | +0.04 | -0.06 | +0.84 | +0.39 | 100% | -4,907 | -5,755 |
| PL103_L_hd20 | CR | -1.52 | -0.60 | -0.56 | +0.19 | -0.04 | 100% | -8,004 | -8,906 |

Pooled learned filter is ~0 or negative (L6M/HOLD); the one significant cell, CR|asia L_skip33 (t=5.3 L6M, 6.4 HOLD, adj p 0.00), is reproduced by the placebo PL101 (+3.0 vs +3.1 pts/signal L6M) because the model keeps book and session id columns and learned "CR in ASIA has been losing" = book-session gating (the D6 mechanism, CR asia L6M mean -4.89 pts/trade, n=176), NOT order-book content. G8 (beats shuffled placebo) fails -> DEAD as an L2 filter; as a session switch it is a D6-style fact, registered as a NOTE for the session table (CR ASIA 0 lots), not a book-state rule.

Last walk-forward re-fit (the one live today, trained on all trades closed before 2026-01-01, 44,816 rows). Full gain importance (ID columns included):

Last re-fit (with book/session/side ids), top 20 features by gain share: vpin50 0.053, svpin50 0.026, d_imb5_60 0.023, ofi1_10 0.022, refill_t10_ms 0.021, delta30 0.020, d_imb5_30 0.020, rnd100_ahead 0.018, rnd50_ahead 0.017, ob_age_s 0.017, can_ahead10 0.016, delta120 0.016, big10_net30 0.015, rnd100_behind 0.015, delta60 0.015, rel_ahead8 0.014, d_imb10_5 0.014, t_since_big_with 0.013, d_imb10_60 0.013, t_since_big_against 0.013. Features used (non-zero gain): 121 of 129; tree settings = 8 leaves x 150 rounds; action tonight = skip when the causal rank of the predicted pts among all prior OOS predictions is in the bottom 33% (variant L_skip33).

Last re-fit (no ids (L2 features + side only)), top 20 features by gain share: vpin50 0.053, svpin50 0.030, d_imb5_60 0.029, d_imb5_30 0.021, refill_t10_ms 0.021, rnd100_ahead 0.019, ofi1_10 0.017, can_ahead10 0.016, big10_net30 0.016, intens_rel 0.015, delta30 0.015, rnd100_behind 0.014, delta120 0.014, ofi1_30 0.014, maxlv_behind_rel 0.013, depth10 0.013, delta5 0.013, ofi1_60 0.012, t_since_big_with 0.012, delta10 0.012. Features used (non-zero gain): 119 of 127; tree settings = 8 leaves x 150 rounds; action tonight = skip when the causal rank of the predicted pts among all prior OOS predictions is in the bottom 33% (variant L_skip33).

Chosen (top-gain) feature by quarter, with ids:
```
2024-01-01 ntrain=8609 top=[('vpin50', 0.04), ('svpin50', 0.026), ('delta5', 0.026), ('d_imb10_30', 0.026), ('cum_behind5', 0.021)]
2024-04-01 ntrain=11700 top=[('vpin50', 0.045), ('refill_ratio_behind10', 0.032), ('d_imb10_30', 0.028), ('delta5', 0.022), ('rnd50_ahead', 0.022)]
2024-07-01 ntrain=14936 top=[('vpin50', 0.051), ('d_imb10_30', 0.027), ('delta120', 0.023), ('d_imb5_60', 0.021), ('nclr_ahead10', 0.021)]
2024-10-01 ntrain=20207 top=[('vpin50', 0.054), ('rnd100_ahead', 0.03), ('refill_t10_ms', 0.028), ('t_since_big_with', 0.025), ('d_imb10_30', 0.023)]
2025-01-01 ntrain=24138 top=[('vpin50', 0.048), ('rnd100_ahead', 0.025), ('t_since_big_with', 0.024), ('d_imb5_60', 0.023), ('nclr_ahead10', 0.022)]
2025-04-01 ntrain=29564 top=[('vpin50', 0.052), ('svpin50', 0.026), ('ob_age_s', 0.021), ('refill_t10_ms', 0.019), ('rnd100_ahead', 0.019)]
2025-07-01 ntrain=35735 top=[('vpin50', 0.061), ('svpin50', 0.023), ('rnd100_ahead', 0.022), ('refill_t10_ms', 0.02), ('d_imb10_30', 0.019)]
2025-10-01 ntrain=39355 top=[('vpin50', 0.058), ('svpin50', 0.032), ('rnd100_ahead', 0.023), ('t_since_big_with', 0.022), ('d_imb5_30', 0.021)]
2026-01-01 ntrain=44816 top=[('vpin50', 0.053), ('svpin50', 0.026), ('d_imb5_60', 0.023), ('ofi1_10', 0.022), ('refill_t10_ms', 0.021)]
```
Chosen by quarter, no ids:
```
2024-01-01 ntrain=8609 top=[('vpin50', 0.039), ('t_since_big_against', 0.028), ('svpin50', 0.027), ('refill_t10_ms', 0.026), ('d_imb10_30', 0.024)]
2024-04-01 ntrain=11700 top=[('vpin50', 0.052), ('d_imb10_30', 0.031), ('rnd100_ahead', 0.026), ('delta5', 0.025), ('refill_ratio_behind10', 0.024)]
2024-07-01 ntrain=14936 top=[('vpin50', 0.053), ('rnd100_ahead', 0.027), ('d_imb10_30', 0.025), ('delta120', 0.021), ('ofi1_60', 0.021)]
2024-10-01 ntrain=20207 top=[('vpin50', 0.043), ('rnd100_ahead', 0.027), ('t_since_big_with', 0.025), ('delta120', 0.022), ('intens_rel', 0.022)]
2025-01-01 ntrain=24138 top=[('vpin50', 0.052), ('refill_ratio_behind10', 0.022), ('rnd100_ahead', 0.02), ('refill_t10_ms', 0.019), ('nclr_ahead10', 0.019)]
2025-04-01 ntrain=29564 top=[('vpin50', 0.048), ('rnd100_ahead', 0.028), ('d_imb5_30', 0.023), ('refill_ratio_behind10', 0.02), ('rnd100_behind', 0.019)]
2025-07-01 ntrain=35735 top=[('vpin50', 0.052), ('svpin50', 0.025), ('delta30', 0.018), ('t_since_big_against', 0.018), ('rnd100_ahead', 0.018)]
2025-10-01 ntrain=39355 top=[('vpin50', 0.043), ('d_imb5_30', 0.027), ('ofi1_10', 0.023), ('svpin50', 0.023), ('delta60', 0.02)]
2026-01-01 ntrain=44816 top=[('vpin50', 0.053), ('svpin50', 0.03), ('d_imb5_60', 0.029), ('d_imb5_30', 0.021), ('refill_t10_ms', 0.021)]
```

### POST-HOC amendment A1 (read after the CR|asia placebo result; not in the prereg family, LEAD at best): learned filter WITHOUT book/session id columns

| variant | unit | 2026 E | L6M E | HOLD E | PRE E | pooled E | keep L6M | L6M $/wk | HOLD $/wk |
|---|---|---|---|---|---|---|---|---|---|
| L_skip20 | ALL | +0.50 | -0.16 | -0.20 | -0.05 | -0.10 | 89% | -10,486 | -11,239 |
| L_skip20 | CR|asia | +0.80 | +0.41 | +0.56 | -0.44 | -0.21 | 93% | +3,825 | +5,495 |
| L_skip33 | ALL | +1.00 | +0.05 | -0.03 | +0.02 | -0.02 | 71% | +5,740 | -68 |
| L_skip33 | CR|asia | -6.08 | +0.16 | +0.18 | +0.02 | -0.04 | 72% | +8,341 | +8,291 |
| L_skip33 | ST | -1.08 | -1.10 | -0.80 | +0.31 | +0.01 | 71% | -9,891 | -6,870 |
| L_skip33 | HM | -0.25 | -1.12 | -1.50 | +1.28 | +0.24 | 69% | -7,294 | -9,434 |
| L_skip33 | WT | +0.93 | -0.25 | -0.20 | +0.25 | +0.04 | 72% | -3,915 | -3,013 |
| L_skip33 | KB | +0.28 | +0.04 | -0.43 | -0.99 | -0.69 | 70% | +358 | -3,656 |
| L_skip33 | SM | -4.13 | -0.69 | -1.02 | -1.10 | -0.78 | 77% | -1,556 | -2,314 |
| L_skip33 | PE | +5.19 | +2.05 | +1.61 | +0.66 | +0.88 | 71% | +17,473 | +13,192 |
| L_skip33 | PB | -2.11 | -1.71 | -0.99 | +1.41 | +0.68 | 68% | -10,582 | -5,941 |
| L_skip33 | DN | +6.89 | +1.24 | +0.89 | -0.54 | -0.15 | 69% | +6,233 | +4,340 |
| L_skip33 | MV | +0.46 | +0.82 | +0.74 | -0.86 | -0.55 | 72% | +6,605 | +5,763 |
| L_skip33 | MA | +5.70 | +1.71 | +1.72 | -1.17 | -0.14 | 77% | +4,984 | +5,109 |
| L_skip33 | CR | -2.19 | +0.07 | -0.02 | -0.60 | -0.35 | 71% | +3,326 | +2,756 |
| L_hd33 | ALL | +0.68 | -0.10 | -0.03 | +0.23 | +0.14 | 100% | -7,872 | -3,023 |
| L_hd33 | CR|asia | -3.49 | +0.63 | +0.58 | -0.39 | -0.14 | 100% | +4,967 | +4,341 |
| L_hd20 | ALL | +0.41 | -0.14 | -0.12 | +0.13 | +0.05 | 100% | -7,249 | -4,606 |
| L_hd20 | CR|asia | -0.04 | +0.33 | +0.47 | -0.60 | -0.27 | 100% | +4,116 | +5,121 |
| PL101_L_skip33 | ALL | -0.35 | +0.14 | +0.21 | -0.41 | -0.18 | 70% | -6,849 | +778 |
| PL101_L_skip33 | CR|asia | -0.27 | +0.54 | +0.72 | -0.19 | +0.19 | 79% | -7,516 | -3,980 |
| PL101_L_skip33 | PE | +5.63 | +0.93 | +0.70 | -0.50 | -0.01 | 68% | +7,896 | +5,748 |
| PL102_L_skip33 | ALL | -0.43 | +0.18 | +0.13 | +0.02 | +0.04 | 75% | +22,532 | +19,513 |
| PL102_L_skip33 | CR|asia | -6.17 | -0.69 | -0.33 | -1.03 | -0.65 | 73% | -2,952 | +644 |
| PL102_L_skip33 | PE | -1.87 | -1.67 | -1.05 | -0.82 | -0.78 | 74% | -14,211 | -8,577 |
| PL103_L_skip33 | ALL | +0.37 | +0.17 | +0.25 | +0.05 | +0.08 | 77% | -1,657 | +5,074 |
| PL103_L_skip33 | CR|asia | -3.18 | -0.97 | -0.79 | +1.07 | +0.42 | 78% | -11,209 | -8,852 |
| PL103_L_skip33 | PE | +1.95 | +1.08 | +1.08 | -0.27 | +0.22 | 77% | +9,193 | +8,860 |

## F5 adaptive chain: rule chosen each quarter (best trailing-4-quarter lot-matched sum on trades closed before the re-fit, pooled books)

| quarter start | chosen rule | trailing score | train n |
|---|---|---|---|
| 2024-01-01 | agree_keep0.2 | 30,601 | 8609 |
| 2024-04-01 | thinAhThickBh_keep | 102,822 | 11700 |
| 2024-07-01 | thinAhThickBh_keep | 184,928 | 12262 |
| 2024-10-01 | thinAhThickBh_keep | 173,588 | 14335 |
| 2025-01-01 | thinAhThickBh_keep | 248,798 | 15523 |
| 2025-04-01 | thinAhThickBh_keep | 76,484 | 17859 |
| 2025-07-01 | skipBot3_rel_behind8 | 16,482 | 20793 |
| 2025-10-01 | agree_keep0.3 | 14,964 | 19141 |
| 2026-01-01 | agree_keep0.2 | 16,357 | 20678 |

ADAPT_chain pooled: 2026 E -4.16, L6M -0.58, HOLD -0.74, PRE +2.24; keep L6M 23%; L6M $/wk -108,834. The chosen rule is mostly a keep-only 'book agrees / thin-ahead-thick-behind' rule that keeps <15% of trades (NON-EXEC: 7-20x lots). Last re-fit (live today, 2026-01-01): agree_keep0.2.

## Stack line on the exact lock engine (6 engine books ST HM WT KB SM PE/PB mapped as e2_joint; PB/DN/MV/MA/CR unchanged; weekly $ at 10-lot nominal; skipped signals removed BEFORE the busy chain; multiplier = lot-matched; 50-contract cap not enforced for sizers)

| rule | window | weeks | mean $/wk (base) | d mean | SD (base) | maxDD (base) | worst-20 sum (base) |
|---|---|---|---|---|---|---|---|
| BASE (stack as is) | 2026 (6 wk) | 6 | 46,187 | - | 146,009 | 276,732 | 277,121 |
| BASE (stack as is) | last 6 months | 28 | 65,679 | - | 123,009 | 466,422 | 204,018 |
| BASE (stack as is) | HOLD | 32 | 52,448 | - | 151,891 | 601,016 | -742,938 |
| BASE (stack as is) | PRE | 75 | 44,127 | - | 131,184 | 477,701 | -2,304,797 |
| BASE (stack as is) | X'(2023-07..2024-01) | 31 | 39,145 | - | 108,679 | 460,909 | -465,686 |
| skipTop3_rnd100_ahead | 2026 (6 wk) | 6 | 2,913 (46,187) | -43,274 | 194,535 (146,009) | 380,216 (276,732) | 17,480 (277,121) |
| skipTop3_rnd100_ahead | last 6 months | 28 | 55,823 (65,679) | -9,856 | 133,813 (123,009) | 467,526 (466,422) | -268 (204,018) |
| skipTop3_rnd100_ahead | HOLD | 32 | 43,424 (52,448) | -9,024 | 153,260 (151,891) | 490,386 (601,016) | -814,543 (-742,938) |
| skipTop3_rnd100_ahead | PRE | 75 | 36,908 (44,127) | -7,219 | 134,740 (131,184) | 525,458 (477,701) | -2,518,208 (-2,304,797) |
| skipTop3_rnd100_ahead | X' | 31 | 38,613 (39,145) | -532 | 117,107 (108,679) | 559,860 (460,909) | -515,097 (-465,686) |
| skipTop3_pulled_sup10 | 2026 (6 wk) | 6 | 45,861 (46,187) | -325 | 179,077 (146,009) | 290,954 (276,732) | 275,168 (277,121) |
| skipTop3_pulled_sup10 | last 6 months | 28 | 58,761 (65,679) | -6,917 | 137,954 (123,009) | 307,066 (466,422) | -63,340 (204,018) |
| skipTop3_pulled_sup10 | HOLD | 32 | 43,718 (52,448) | -8,729 | 167,593 (151,891) | 657,712 (601,016) | -1,026,108 (-742,938) |
| skipTop3_pulled_sup10 | PRE | 75 | 38,662 (44,127) | -5,465 | 146,475 (131,184) | 650,812 (477,701) | -3,088,587 (-2,304,797) |
| skipTop3_pulled_sup10 | X' | 31 | 52,480 (39,145) | +13,334 | 124,657 (108,679) | 469,392 (460,909) | -413,308 (-465,686) |
| skipTop3_spread_t | 2026 (6 wk) | 6 | 114,128 (46,187) | +67,941 | 159,214 (146,009) | 176,401 (276,732) | 684,767 (277,121) |
| skipTop3_spread_t | last 6 months | 28 | 61,969 (65,679) | -3,710 | 138,941 (123,009) | 608,810 (466,422) | -62,771 (204,018) |
| skipTop3_spread_t | HOLD | 32 | 49,994 (52,448) | -2,454 | 166,089 (151,891) | 643,348 (601,016) | -973,537 (-742,938) |
| skipTop3_spread_t | PRE | 75 | 32,901 (44,127) | -11,226 | 131,350 (131,184) | 503,217 (477,701) | -2,787,927 (-2,304,797) |
| skipTop3_spread_t | X' | 31 | 37,029 (39,145) | -2,116 | 103,283 (108,679) | 460,883 (460,909) | -448,173 (-465,686) |
| skipTop3_pulled_opp10 | 2026 (6 wk) | 6 | 36,089 (46,187) | -10,098 | 178,589 (146,009) | 279,854 (276,732) | 216,534 (277,121) |
| skipTop3_pulled_opp10 | last 6 months | 28 | 56,175 (65,679) | -9,504 | 139,674 (123,009) | 305,144 (466,422) | -128,138 (204,018) |
| skipTop3_pulled_opp10 | HOLD | 32 | 42,599 (52,448) | -9,848 | 166,065 (151,891) | 621,500 (601,016) | -1,076,253 (-742,938) |
| skipTop3_pulled_opp10 | PRE | 75 | 44,212 (44,127) | +85 | 146,448 (131,184) | 612,864 (477,701) | -2,985,224 (-2,304,797) |
| skipTop3_pulled_opp10 | X' | 31 | 54,659 (39,145) | +15,514 | 126,716 (108,679) | 511,084 (460,909) | -372,435 (-465,686) |
| skipBot3_depth_rel | 2026 (6 wk) | 6 | 60,528 (46,187) | +14,341 | 223,169 (146,009) | 332,780 (276,732) | 363,169 (277,121) |
| skipBot3_depth_rel | last 6 months | 28 | 60,255 (65,679) | -5,424 | 135,960 (123,009) | 339,844 (466,422) | -1,305 (204,018) |
| skipBot3_depth_rel | HOLD | 32 | 50,605 (52,448) | -1,843 | 164,276 (151,891) | 576,549 (601,016) | -835,637 (-742,938) |
| skipBot3_depth_rel | PRE | 75 | 31,712 (44,127) | -12,415 | 141,277 (131,184) | 686,747 (477,701) | -3,020,690 (-2,304,797) |
| skipBot3_depth_rel | X' | 31 | 38,827 (39,145) | -318 | 105,808 (108,679) | 633,926 (460,909) | -423,469 (-465,686) |
| thick_skip15 | 2026 (6 wk) | 6 | 37,320 (46,187) | -8,867 | 157,419 (146,009) | 277,624 (276,732) | 223,918 (277,121) |
| thick_skip15 | last 6 months | 28 | 65,184 (65,679) | -494 | 115,609 (123,009) | 277,624 (466,422) | 240,553 (204,018) |
| thick_skip15 | HOLD | 32 | 52,607 (52,448) | +159 | 145,665 (151,891) | 573,236 (601,016) | -635,150 (-742,938) |
| thick_skip15 | PRE | 75 | 34,176 (44,127) | -9,951 | 127,259 (131,184) | 511,282 (477,701) | -2,268,661 (-2,304,797) |
| thick_skip15 | X' | 31 | 38,318 (39,145) | -827 | 107,035 (108,679) | 465,443 (460,909) | -461,922 (-465,686) |
| L_skip33 | 2026 (6 wk) | 6 | 74,044 (46,187) | +27,857 | 219,440 (146,009) | 323,925 (276,732) | 444,263 (277,121) |
| L_skip33 | last 6 months | 28 | 50,949 (65,679) | -14,729 | 150,396 (123,009) | 526,057 (466,422) | -332,700 (204,018) |
| L_skip33 | HOLD | 32 | 40,442 (52,448) | -12,006 | 182,668 (151,891) | 659,178 (601,016) | -1,341,776 (-742,938) |
| L_skip33 | PRE | 75 | 41,991 (44,127) | -2,136 | 138,228 (131,184) | 808,818 (477,701) | -2,526,031 (-2,304,797) |
| L_skip33 | X' | 31 | 48,096 (39,145) | +8,951 | 117,247 (108,679) | 523,697 (460,909) | -496,435 (-465,686) |

MDE of a stack mean difference over the 28-week L6M window is of the order of the SD/sqrt(28)*2.8 = ~65,000 $/wk (HOLD ~75,000): every d mean above is inside it. No rule improves the stack line (d mean L6M and HOLD) except thick_skip15 which is flat (-494 / +159 $/wk, maxDD 277,624 vs 466,422 in L6M, SD 115,609 vs 123,009).
