# DS3_INST_C - cross-market state at minutes-to-hours (T-INSTITUTIONAL section C, INST-3, 2026-10-31 16:38Z)

**DATA line.** On disk and used: back-adjusted 1-min bars NQ ES RTY YM ZN GC CL 6E 6J 6B 6C (Databento GLBX, `/mnt/l2/l2vast/ds3/cache_te2`, 2022-06..2026-02-06 after the cut; coverage of the NQ minute grid 89-100%, RTH 98-100%); RTY also has 1-s and mbp on disk (`s1/RTY`, `raw/RTY`) but minutes-to-hours needs only the minute bars. DXY is DERIVABLE as a proxy (6E/6J/6B/6C basket, 92.2% of the index weight, SEK and CHF absent), labelled DXYp. Nothing to buy for C; no purchase, no download. Fee grade: signals filters carry no new fee; the pair book uses NQ/ES $4.84 RT and micros $1.78 RT (NQ and micros are PROXY grade in FEES.md, so a pair verdict is capped at CANDIDATE).

## Page 1 - the answer

**Plain sentence.** Of 693 pre-registered cross-market state cells (30 / 60 / 120 min; ES, RTY, YM, ZN, gold, oil, DXYp and their residuals against NQ; NQ-led vs ES/YM-led; risk-on agreement counts; NY-open day type), 141 were positive in both PRE and X' on measured AND no-correction fills, 57 were selected on PRE+X' alone and looked at once on the recent windows; only 8 are positive in both L3M and L6M (per contract and on the stack), 1 STRICT, **0 TOLERANT (literal gate, headline)**; post-hoc readings: 1 under TOL-B (PRE gain > -1.0 x L6M gain) and 2 with clause 5 dropped (TOL-nc). The best cell by stack, TOLERANT only under the post-hoc readings, is `xm.led_YM_60.ge+0.0` (keep a signal unless NQ has NOT out-run YM beta-adjusted over the last 60 min in the signal's direction; keeps 81% of signals): kept signals pay +2.65 pts per contract more than the skipped ones (L6M, MDE 6.7, CI [-2.03, +7.32]), PRE +1.77 (MDE 4.4), X' +3.26; on the one-convention stack the filter is +7.3k/wk L6M (MDE +12.8), -2.2 PRE, -1.3 X': inside MDE in every window, and it fails the placebos (cell placebo p 0.32; the program-level selection placebo p = 0.41). The selected set as a whole earned a mean L6M lift of +0.00 pts per contract (45% of cells positive), while selecting the same way on cross-market series shifted by whole weeks gives -0.96 (5-95%: -4.23 to +1.98, 38% positive): the real selected set is inside the null. The NQ/ES residual as a pair book is tradeable at NO cost grade: gross +$9 per trade (micros) against $52 of fees and slippage, break-even cost multiple 0.16-0.27; every one of the 8 cells is DEAD in every fold. Persistence score 0.50 (entry-filter base rate; t6 of its weekly stack delta 1.6), shrunk size 0.00 (OOS/IS ratio of the family is 0.00): shadow only. **Verdict: DEAD for cross-market state at the hour scale on these books; no cell passes the literal TOLERANT gate; the YM-beyond-NQ filter is a post-hoc LEAD (TOL-B), nothing promoted.**

### The three T-SIXTY columns (per cell, headline = TOLERANT)

| column | cells of 57 selected | of 693 in the grid | walk-forward persistence over 2024-26 |
|---|---|---|---|
| STRICT (positive in L3M, L6M, PRE, X', per contract and stack) | 1 | 1 | not computable (n too small; cross-market filters are in the entry-filter family: 50% base rate, DS3_PERSISTENCE) |
| TOLERANT literal (headline: clause 5 = L6M->PRE drop < 100% of L6M gain, i.e. PRE gain > 0) | 0 | 0 | same |
| TOL-B (post-hoc, looser: PRE gain > -1.0 x L6M gain) | 1 | 1 | same |
| TOL-nc (post-hoc, no clause 5) | 2 | 2 | same |
| NOW-ONLY (L3M and L6M positive) | 8 | 8 | same; the family base rate is 50% and the walk-forward t-stat model adds ~1% Brier skill |

The count of cells outside the selected set is not applicable: their recent columns are sealed by the ONE-look rule (the other 636 cells have PRE and X' numbers only).

**Status line.** The two LEADs of INST-3 (`xm.led_YM_60.ge+0.0` skip in C, `fl.ROLLPRE.RTH.up` in F) are shadow-only and not independent evidence (cell placebo p 0.32 / 0.16; program placebo 0.41 / 0.83).

## 1. Method in one paragraph (prereg `l2vast/ds3/prereg/INST_C_prereg.md`, sha256 `3bae519f46efbdc7dd3513555376a97bf76b776ab0f354fe27f35155e45fa30b`; selection file sha256 `5ff381f7ad2fff7a198f2be3762cb741b232973aa99a32bf45d2b734b136fe1b`, both logged in DECISIONS.md before the recent look)

States are as-of the last completed 1-min bar (data at least 60 s old; bars are minute-quantised, so a 3-s older state is one whole bar older for nearly all signals that fire in the first 3 s of a minute: re-running every selected cell that way moves the L6M lift by 0.838 pts on average, max 5.847 - the cells are sensitive to staleness, which a live feed must not add). Return over w = 30 / 60 / 120 min in bps, risk-on positive (nZN = -ZN, nDXYp = -DXYp), side-aligned. raw = the market's own aligned move; res = the market's move BEYOND NQ (trailing 20-label-day beta of 5-min returns, prior days only); led = NQ's move beyond that market (led_ES is the beta-adjusted NQ-vs-ES residual of the directive); risk = mean of ES, RTY, YM, nZN, nDXYp; agree = how many of ES, RTY, nZN, nDXYp point the signal's way; div = NQ and ES sign agree / differ; nq = NQ's own aligned move (CONTROL). NY-open day type = aligned 08:30->09:30 and prior-16:00->09:30 returns of NQ, ES, RTY, YM, nZN, GC, CL, nDXYp for signals at/after 09:30. A cell keeps a signal when its state passes a threshold c (per-session scale fixed on PRE+X'), 'ge' = cross-market confirms, 'le' = the contrarian reading. Per contract = held-signal market trade at the signal second on the 6 live D6 books (K6 P6 U6 H6 M6 A6, 25,941 signals, 2023-04..2026-02-06), M = measured fills (headline), N = no target-fill correction, LC = live-cal (M less 1.17 on even-label-day stops). Lift = kept minus skipped, stratified by book, week-clustered SE, MDE = 2.8 SE. Stack line = the ONE-CONVENTION composite (oneconv/oc_lib.py: 70/30 split, PE 45-s, zone skip, Asia-stop cut, ER sizer, running-max SizeMult, live lots K6 2 / P6 7 / U6 4 / H6 4 Asia + 2 NY-AM / M6 2 / A6 1, parity stop, slip +0.25), skipped signals OR-ed into the zone skip; base ties out to Table A2 (34.4 / 41.1 / 38.6 / 23.1 / 8.0 $k/wk).

## 2. Answer to the directive's question - do NQ signals pay more when the others agree at the HOUR scale? (PRE and X' only for the unselected cells; recent columns are sealed)

Lift of KEEPING the signals whose side-aligned state is >= 0 (the market moved the signal's way or beyond NQ's move) minus skipping them, pts per contract M; PRE / X' (MDE in brackets). Positive = agreement pays more.

| market | 30 min | 60 min | 120 min |
|---|---|---|---|
| raw ES | -3.72 / -0.59 (4.5 / 7.8) | -0.88 / +3.22 (4.7 / 8.5) | -0.34 / +0.89 (5.1 / 8.2) |
| raw RTY | -1.40 / -2.89 (4.3 / 6.6) | -1.21 / +3.30 (3.9 / 7.0) | -1.29 / +3.25 (4.5 / 7.7) |
| raw YM | -2.26 / -1.75 (4.2 / 6.6) | -3.18 / +1.61 (4.0 / 6.2) | -2.02 / +1.25 (4.4 / 6.6) |
| raw nZN | -1.16 / +2.05 (3.6 / 5.7) | -0.67 / -2.84 (4.2 / 6.3) | +0.32 / -4.31 (4.5 / 5.9) |
| raw GC | +0.67 / +0.85 (3.6 / 6.0) | +0.42 / +2.29 (3.6 / 6.5) | -0.79 / +3.30 (4.2 / 7.2) |
| raw CL | -0.73 / +0.35 (3.7 / 6.0) | -1.07 / -2.91 (3.6 / 7.5) | +0.06 / -1.10 (3.8 / 8.1) |
| raw nDXY | +0.25 / +0.45 (3.4 / 6.0) | +1.63 / -3.59 (3.7 / 7.1) | +0.68 / -1.62 (4.0 / 7.1) |
| res ES | -1.30 / -0.73 (3.4 / 5.5) | -1.02 / +0.83 (3.4 / 7.3) | -1.87 / -0.36 (3.8 / 6.8) |
| res RTY | -0.54 / -1.60 (3.1 / 5.1) | -2.04 / +2.43 (3.6 / 7.0) | +0.18 / +0.66 (3.8 / 6.0) |
| res YM | -1.04 / -2.03 (3.5 / 5.3) | -1.15 / -0.97 (3.5 / 6.9) | -1.15 / -2.39 (3.5 / 5.9) |
| res nZN | -0.69 / +2.83 (4.0 / 5.5) | -0.25 / -1.52 (4.3 / 6.2) | +0.20 / -4.01 (4.7 / 5.6) |
| res GC | +0.55 / +1.02 (3.7 / 6.1) | +0.54 / +1.86 (3.7 / 6.5) | -0.43 / +2.28 (3.9 / 7.1) |
| res CL | -0.10 / +2.63 (3.5 / 5.7) | -0.85 / -3.62 (3.6 / 7.6) | +0.76 / -2.33 (3.9 / 8.2) |
| res nDXY | +0.70 / -0.84 (3.3 / 6.2) | +1.30 / -0.76 (4.1 / 7.2) | +0.40 / -1.26 (4.1 / 7.4) |
| NQ-led vs ES | +1.30 / +2.76 (3.4 / 5.4) | +1.81 / +2.27 (3.5 / 7.0) | +2.21 / +1.80 (3.7 / 5.1) |
| NQ-led vs RTY | -1.02 / -0.17 (3.8 / 6.7) | -0.38 / +0.24 (4.6 / 6.3) | +1.15 / -2.79 (4.2 / 5.9) |
| NQ-led vs YM | +0.17 / +3.06 (3.0 / 6.4) | +1.77 / +3.26 (4.2 / 7.0) | +1.69 / +4.57 (4.1 / 6.5) |
| risk-on composite | -2.03 / -2.03 (4.2 / 7.2) | -3.51 / -0.32 (3.8 / 7.7) | -0.81 / -1.22 (4.8 / 7.1) |
| CONTROL: NQ own move | -2.08 / -0.86 (4.9 / 8.1) | +0.61 / -0.66 (5.0 / 7.2) | +1.71 / +0.90 (5.6 / 6.6) |

Reading: the signed lifts of simple agreement are small, mixed in sign across markets and horizons, and almost all inside their own MDE (the typical PRE MDE is 3-5 pts per contract and X' 6-9); ES agreement adds nothing beyond NQ's own move (the control row is the same order), and the residual versions (the market's move NOT explained by NQ) are where the selected cells come from.

## 3. Cell families (PRE+X' eligibility, selection, recent look)

| family | cells | eligible (PRE & X', M & N) | selected | mean L6M lift of selected | share L6M > 0 | NOW-ONLY | TOLERANT |
|---|---|---|---|---|---|---|---|
| agree | 21 | 2 | 0 | +0.00 | 0% | 0 | 0 |
| div | 6 | 0 | 0 | +0.00 | 0% | 0 | 0 |
| led | 90 | 24 | 18 | -0.12 | 39% | 6 | 0 |
| nq | 30 | 1 | 1 | -0.17 | 0% | 0 | 0 |
| nyo | 96 | 16 | 3 | -1.27 | 33% | 0 | 0 |
| raw | 210 | 42 | 13 | -0.53 | 31% | 0 | 0 |
| res | 210 | 50 | 19 | +1.11 | 68% | 2 | 0 |
| risk | 30 | 6 | 3 | -1.87 | 0% | 0 | 0 |

Pure chance would make about 1/16 of cells eligible (43 of 693); 141 passed, but the 693 cells are heavy neighbours of each other (3 horizons x 5 thresholds x 2 directions of the same state), so the count is not evidence. The selected cells' mean L6M lift is +0.00; PRE and X' means of the same cells are +2.0 and +3.0 (the selection windows, optimistic by construction).

## 4. Selected cells, ranked by stack L6M (all 57 in `out/recent_wins/inst_C.csv`; top 20 here)

Per contract M pts (kept - skipped) with MDE; stack = C1 no combined lock, $k/wk delta vs the composite with MDE; keep = share of signals kept in L6M; plc = cell placebo rank among ~200 week-shifted cross series.

| cell | keep | X' | PRE | HOLD | L6M [MDE] | L3M | N L6M | LC L6M | stack L3M | L6M [MDE] | HOLD | PRE | X' | 12R L6M | 20R L6M | plc p | STRICT/TOL/NOW | failed gates | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| xm.led_YM_60.ge+0.0 | 81% | +3.26 | +1.77 | +0.75 | +2.65 [6.7] | +2.23 | +2.83 | +2.65 | +2.5 | +7.3 [+12.8] | +4.0 | -2.2 | -1.3 | +3.1 | +7.5 | 0.32 | n/n/Y | - | DEAD |
| xm.led_YM_120.ge+0.0 | 80% | +4.57 | +1.69 | +0.76 | +0.27 [7.5] | +2.51 | +0.32 | +0.26 | +5.7 | +6.2 [+7.5] | +5.6 | -2.7 | +0.5 | +4.4 | +6.3 | 0.42 | n/n/Y | PRE_worst20 | DEAD |
| xm.led_YM_120.ge+0.5 | 65% | +3.20 | +1.45 | +1.41 | +1.28 [6.1] | +2.89 | +1.37 | +1.26 | +4.1 | +3.1 [+9.6] | +1.1 | -3.2 | -3.9 | +8.0 | +5.6 | 0.38 | n/n/Y | PRE_worst20,drop<100% | DEAD |
| xm.led_YM_120.ge-1.0 | 94% | +5.74 | -0.93 | -1.63 | -2.21 [11.1] | -0.56 | -2.28 | -2.23 | +2.3 | +2.5 [+6.2] | +2.7 | -0.3 | +0.6 | +2.4 | +2.9 | 0.63 | n/n/n | L3M_pc,L6M_pc,N_L6M,N_L3M,PRE_worst20 | DEAD |
| xm.res_YM_120.le+0.5 | 66% | +4.31 | +1.56 | +3.90 | +3.96 [7.5] | +4.51 | +4.11 | +3.98 | +4.7 | +2.1 [+17.8] | +1.7 | -5.3 | -0.1 | +3.0 | +3.3 | 0.18 | n/n/Y | PRE_stack_tol,drop<100% | DEAD |
| xm.led_YM_60.ge+0.5 | 66% | +3.84 | +1.06 | +0.69 | +1.35 [5.8] | +2.63 | +1.48 | +1.36 | +0.7 | +1.8 [+15.2] | -0.4 | -2.6 | -1.5 | +3.5 | +4.0 | 0.65 | n/n/Y | PRE_worst20,drop<100% | DEAD |
| xm.led_YM_60.ge-1.0 | 96% | +11.94 | +3.97 | +2.70 | +3.92 [13.0] | +5.70 | +4.09 | +3.95 | +1.0 | +1.3 [+5.7] | +1.5 | +0.5 | +0.4 | +1.4 | +2.3 | 0.13 | Y/n/Y | PRE_worst20 | DEAD |
| xm.led_YM_120.ge+1.0 | 49% | +0.27 | +2.09 | +3.90 | +4.34 [6.8] | +6.70 | +4.55 | +4.34 | +4.9 | +1.1 [+12.1] | -0.5 | -1.1 | -7.2 | +1.7 | +0.7 | 0.06 | n/n/Y | X_stack_tol | DEAD |
| xm.raw_ES_60.ge-1.0 | 98% | +7.50 | +5.10 | +0.35 | -1.55 [16.5] | +0.60 | -1.68 | -1.57 | +1.1 | +1.1 [+2.1] | +1.1 | +0.6 | +0.1 | +0.4 | +0.7 | 0.64 | n/n/n | L6M_pc,N_L6M,PRE_worst20 | DEAD |
| xm.res_YM_120.le+0.0 | 53% | +2.63 | +1.20 | +3.77 | +3.97 [7.5] | +5.66 | +4.13 | +4.00 | +6.4 | +0.9 [+18.0] | +0.3 | -5.5 | -2.5 | +2.6 | +0.5 | 0.17 | n/n/Y | drop<100% | DEAD |
| xm.led_ES_60.ge-1.0 | 89% | +6.34 | +2.39 | -2.75 | -1.61 [9.3] | +0.75 | -1.68 | -1.63 | -0.1 | -0.9 [+10.4] | -0.8 | -5.6 | +2.4 | -2.4 | +4.2 | 0.77 | n/n/n | L6M_pc,L3M_stack,L6M_stack,N_L6M,PRE_stack_tol,PRE_worst20,drop<100% | DEAD |
| xm.led_ES_120.ge-0.5 | 81% | +3.71 | +2.93 | -0.71 | -2.15 [9.3] | -1.29 | -2.23 | -2.18 | -1.0 | -1.8 [+11.2] | +0.2 | -2.0 | -0.3 | -0.7 | +1.0 | 0.67 | n/n/n | L3M_pc,L6M_pc,L3M_stack,L6M_stack,N_L6M,N_L3M,PRE_worst20,drop<100% | DEAD |
| xm.led_ES_60.ge-0.5 | 81% | +3.27 | +1.76 | -3.96 | -3.49 [7.3] | -2.44 | -3.57 | -3.49 | -11.1 | -3.3 [+16.1] | -3.4 | -5.4 | +0.3 | -2.6 | -1.5 | 0.87 | n/n/n | L3M_pc,L6M_pc,L3M_stack,L6M_stack,N_L6M,N_L3M,PRE_stack_tol,PRE_worst20,drop<100% | DEAD |
| xm.res_ES_30.le+1.0 | 80% | +4.20 | +1.27 | -0.92 | -0.06 [6.5] | +0.87 | -0.07 | -0.02 | -3.7 | -4.3 [+13.0] | -4.7 | -7.4 | +5.5 | -4.5 | +1.4 | 0.55 | n/n/n | L6M_pc,L3M_stack,L6M_stack,N_L6M,PRE_stack_tol,PRE_worst20,drop<100% | DEAD |
| xm.res_YM_120.le+1.0 | 77% | +4.22 | +1.52 | +1.30 | +1.53 [7.9] | +2.28 | +1.59 | +1.54 | -3.0 | -4.4 [+15.0] | -4.0 | -4.4 | +0.5 | -4.1 | -0.6 | 0.41 | n/n/n | L3M_stack,L6M_stack,PRE_stack_tol,PRE_worst20,drop<100% | DEAD |
| xm.res_YM_60.le+1.0 | 77% | +3.15 | +2.45 | +2.11 | +2.68 [7.5] | +2.23 | +2.76 | +2.71 | -7.3 | -4.9 [+14.3] | -3.5 | -5.9 | +2.2 | -13.5 | +0.3 | 0.29 | n/n/n | L3M_stack,L6M_stack,PRE_stack_tol,PRE_worst20,drop<100% | DEAD |
| xm.ny_ZN_ov.le+0.0 | 54% | +7.11 | +2.11 | +0.83 | +3.10 [9.0] | +8.54 | +3.28 | +3.10 | +2.9 | -5.7 [+20.9] | -8.9 | -8.5 | -0.4 | +3.5 | +0.5 | 0.35 | n/n/n | L6M_stack,PRE_stack_tol,PRE_worst20,drop<100% | DEAD |
| xm.res_YM_60.le+0.5 | 64% | +1.56 | +2.08 | +1.75 | +2.66 [6.8] | +2.40 | +2.77 | +2.69 | -4.0 | -5.8 [+15.2] | -5.3 | -4.5 | +0.4 | -5.9 | -1.0 | 0.29 | n/n/n | L3M_stack,L6M_stack,drop<100% | DEAD |
| xm.led_ES_120.ge+0.0 | 67% | +1.80 | +2.21 | +0.02 | -0.55 [7.3] | +0.85 | -0.53 | -0.55 | -6.0 | -6.3 [+11.8] | -5.2 | -5.4 | +0.6 | -10.2 | -7.7 | 0.58 | n/n/n | L6M_pc,L3M_stack,L6M_stack,N_L6M,PRE_stack_tol,PRE_worst20,drop<100% | DEAD |
| xm.res_YM_30.le+1.0 | 75% | +4.61 | +1.09 | +0.01 | +0.75 [6.5] | +0.60 | +0.77 | +0.78 | -11.5 | -6.4 [+16.3] | -6.4 | -8.0 | +1.3 | -6.3 | -5.5 | 0.43 | n/n/n | L3M_stack,L6M_stack,PRE_stack_tol,PRE_worst20,drop<100% | DEAD |

The stack deltas are mostly NEGATIVE: skipping 15-60 percent of the signals of a composite that earns $41k/wk costs more volume than the skipped signals' lower expectation saves (mean stack L6M delta across the 57 selected cells -14.9 k/wk; 10 of 57 positive).

## 5. The one TOLERANT cell and the YM cluster, by session

`xm.led_YM_60.ge+0.0` lift by session, pts per contract M (MDE in brackets), n kept in L6M:

| session | PRE | X' | HOLD | L6M [MDE] | n kept L6M |
|---|---|---|---|---|---|
| asia | +2.78 | +0.40 | +8.34 | +10.00 [13.2] | 1320 |
| london | -0.54 | +4.53 | -4.44 | -2.41 [17.4] | 1005 |
| nyam | +2.58 | +4.29 | -1.52 | +1.08 [12.8] | 1263 |
| nypm | +2.05 | +5.11 | +0.74 | +2.36 [13.4] | 779 |
| pre | -1.37 | +1.42 | -7.28 | -9.27 [35.8] | 235 |

The L6M gain is concentrated in Asia (+10.0, MDE 11.8) and fades or flips in London and the pre-open; no session is beyond its MDE. The related YM-residual cells (`res_YM_60/120.le*`, `led_YM_*`) point the same way (YM has NOT confirmed NQ's move = the NQ move is idiosyncratic = the signal pays more), all positive in PRE, X', HOLD and L3M at +1 to +5 per contract, but their stack lines are negative in PRE and none is beyond MDE; with the cell placebo p of 0.07-0.32 and the program placebo at 0.41 I do not read it as a state, only as the best-looking neighbourhood in a grid whose selected average is zero.

## 6. Placebos, multiplicity, delay

* Cell placebo (cross series read 7k days earlier, 200 draws, NQ real): best selected cell p = 0.06; share of selected cells with p <= 0.05: 0% (chance 5%).
* Program placebo (the WHOLE selection re-run on week-shifted cross series, 200 draws): the null selects 132 eligible cells on average (real: 141), the mean L6M lift of its top 40 is -0.96 (HOLD +0.59); the real top 40 is +0.00, p = 0.41. The real cross-market series carry no more selectable recent information than a week-shifted one.
* Decision delay: states from data 3 s (= one bar) older: mean abs change in L6M lift 0.838 pts (max 5.847); the TOLERANT cell's L6M lift becomes +1.45 (from +2.65). Capacity: the filters remove orders, they add none.

## 7. NQ/ES residual as a standalone pair book (cells C2, prereg section 10)

Fade the beta-adjusted NQ-vs-ES residual at |z| >= 2.0 / 2.5 over 60 / 120 min (RTH signal bars 09:45-15:30, exit z through 0.5 / 90 min / z 4 stop / 15:55), beta-sized dollar-neutral legs (micro: 5 MNQ + beta-sized MES at $1.78 RT each; standard: 3 NQ + beta-sized ES at $4.84 RT each), entry and exit next-minute open one tick adverse on EACH leg, 2023-04-03..2026-02-06. $ per trade; MDE = 2.8 x day-clustered SE; purged 5-fold CV (1-day embargo, overlap purge) with the nested best-of-8 choice per fold; placebo = ES read k trading days earlier (200 draws, gross P&L rank).

| cell | trades/wk | net $/trade | gross | cost | L6M | HOLD | PRE | X' | MDE L6M | break-even cost x | placebo rank (gross) | purged CV mean (folds >0) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| pair/z2.0/w60/micro | 9.5 | -43.3 | +8.6 | 51.9 | -52.5 | -56.6 | -30.3 | -54.0 | 30.6 | 0.16 | 7/201 | -43.8 (0/5) |
| pair/z2.5/w60/micro | 6.1 | -42.8 | +9.2 | 52.0 | -52.7 | -62.4 | -23.4 | -57.1 | 35.5 | 0.18 | 7/201 | -43.0 (0/5) |
| pair/z2.0/w120/micro | 7.2 | -50.3 | +1.6 | 51.9 | -56.0 | -57.2 | -41.6 | -59.2 | 36.9 | 0.03 | 80/201 | -50.6 (0/5) |
| pair/z2.5/w120/micro | 5.0 | -53.8 | -1.8 | 51.9 | -61.6 | -63.0 | -43.6 | -62.5 | 38.1 | -0.04 | 140/201 | -53.7 (0/5) |
| pair/z2.0/w60/std | 9.5 | -149.9 | +51.2 | 201.1 | -210.2 | -231.7 | -67.6 | -218.8 | 185.6 | 0.25 | 9/201 | -154.7 (0/5) |
| pair/z2.5/w60/std | 6.1 | -147.6 | +53.7 | 201.3 | -202.8 | -257.6 | -31.8 | -239.7 | 211.7 | 0.27 | 7/201 | -151.6 (0/5) |
| pair/z2.0/w120/std | 7.2 | -190.0 | +10.8 | 200.8 | -218.5 | -223.9 | -134.9 | -256.7 | 232.0 | 0.05 | 108/201 | -194.2 (0/5) |
| pair/z2.5/w120/std | 5.0 | -205.1 | -5.0 | 200.2 | -238.3 | -250.9 | -141.2 | -272.0 | 240.7 | -0.02 | 134/201 | -209.0 (0/5) |

Nested best-of-8 on the training folds: OOS net per trade -66, -49, -29, -35, -54 per fold (mean -47); no fold is positive. The 60-minute residual has a REAL but tiny gross edge (placebo rank 7/201: better than 97% of week-shifted ES legs; +$8.6 per trade on micros, +$51 on standard contracts) which is 6x smaller than the all-in cost of two legs entered and exited at conservative fills; a cost multiple of 0.16-0.27 would be needed to break even, i.e. only a market-making fee/slippage structure we do not have. Tradeable at our costs: **no** (DEAD, all 8; ceiling CANDIDATE because NQ/micro fees are proxy grade). Consistent with DS3_DIV2_B_PAIRS (47 cells all DEAD, gross about 0 on index pairs); same sample, so not independent evidence.

## 8. Flags and questions
* TOLERANT clause 3 ("the drop from L6M to PRE is less than 100% of the L6M gain") taken literally means PRE gain > 0, which contradicts clause 2 (a small PRE loss inside the noise is fine). The HEADLINE is now the literal gate (as SIXTY-1); my looser reading (TOL-B) and the no-clause-5 reading (TOL-nc) are shown beside it as post-hoc. Under the literal gate 0 cells pass (the best cell has stack PRE -2.2k). Which reading did you mean? (open)
* The cross-market states are tested as FILTERS on signals that already exist; on the stack a filter must beat the volume it removes, and no cell did beyond MDE. A sizing form (x0.5 / x1.5 on the agreement state) was not pre-registered and is not scored.
* ZN is thin overnight (93% of NQ minutes); stale (> 60 min) states are untouched.
* Not scored here: second-scale NQ/ES lead-lag (already in the ledger), options and vol state (INST-4).

## 9. Files
Code `l2vast/ds3/code/inst/C/` (c_feat, c_cells, c_prereg, c_score, c_look, c_stack, c_rows, c_pair, c_pair_stats, c_report) and `inst/common/` (ic_data, ic_sig, ic_prog, ic_stack, ic_tier, ic_rows); outputs `l2vast/ds3/out/inst/C/` (C_cells.csv, C_prex.parquet, C_selection.json, C_look*.parquet, C_stack.pkl, C_rows.parquet, C_program_placebo.json, plc_*.pkl, C_pair*.parquet); rows `l2vast/ds3/out/recent_wins/inst_C.csv`; dead cells appended to `out/uf/DEAD_CELLS.csv` (program INST3C).
