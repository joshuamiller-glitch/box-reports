# DS3_CONFIRM_SUBMIN - sub-minute MA / VWAP / price-movement events as the confirmation (T-CONFIRM-LAYER addendum 3)

Agent CF-SUBMIN. Prereg autopilot/CONFIRM_SUBMIN_prereg.md sha256 2371d005156e8a0692ed58fc812e2888f0614bf6c82048175fbc0d001b2a5225; S1 selection sha a34d5904f735e398771ea37a08a1b4bb19664bbb34e00eb54785a03369652010 (PRE+X' only); S2 selection sha 1fe5239a81af3100e00bbeabd6873d8a8cf81837069b78ded8737235899476d5 (PRE+X' only); ONE recent look on the 67 selected cells. Code l2vast/ds3/code/confirm/submin/, outputs l2vast/ds3/out/confirm/submin/ (report_look_with_pc.csv, report_program.csv, named_ema8_21_15s.csv, s1/, s2/, look/). Windows own masks capped 20260206; UNTOUCHED never read; L3M (20251106..20260206) is a VIEW column only.

## 1. Verdict

Sub-minute MA, VWAP and price-movement events do not give a usable confirmation. 32,776 screen cells (23,241 event specs x market/limit mechanics, 10 books) and 27,808 full-grid cells (632 carried specs x 11 mechanics x 70/30 and pure-wait x N and M) were scored on PRE+X'; best pooled PRE+X' gain over the plain 3-pt-dip floor in the screen is +0.28 pts per planned lot (that is what the best of 32,776 cells looks like by chance); 70% of screen cells are below the floor. The White reality check on PRE+X' weeks over each book's 5,269 S2 cells has p between 0.09 and 0.99 (none <= 0.05), Romano-Wolf stepdown survivors: 0 in all 10 books, PBO 0.09-0.73. Of the 67 cells looked at once in the recent windows, 15 are >= 0 in L6M; 0 reach CANDIDATE-RECENT by the prereg gates (an earlier draft of this look listed 3; they were an artefact of a placebo defect for the mechanic-d state semantics, fixed and re-run) and 0 reach PASS (cumulative-adjusted p across 287,592 cells is 1.0 for every cell). Every one of the 67 is a mechanic-d filter or a limit/market cell whose gain is matched by the shuffled-day (+7 d) or random-timing placebo, i.e. it is STRUCTURE (the plain-dip split, skipped signals) rather than information in the event; the top L6M cells (+1.0..+1.3 pts per planned lot) have MDE 3-8 pts. See section 3.

## 2. The named case: waiting for the 15-s EMA-8/21 cross after the signal

Waiting for the 15-s EMA-8/21 cross after the KB signal and entering at market there adds +0.14 pts per planned lot on 75% of signals with a median wait of 570 s in L6M (MDE 1.72; HOLD +0.16, PRE -0.31, X' -0.21, L3M view +0.60); on the 25% of signals with no cross before the hold dies the 70% slice stays at the signal (floor P&L on them -7.3 pts). It is inside the MDE, negative in PRE and X'. Descriptive look, not selected.

Delta vs the 70/30 plain 3-pt dip floor, pts per planned lot, N basis, mechanic a, hold 0, all ten books (recent first):

| book   |   L3M |   Y26 |   L6M |   HOLD |   PRE |     X |
|:-------|------:|------:|------:|-------:|------:|------:|
| DN     | -0.78 | -2.72 | -0.39 |  -0.22 |  0.25 |  0.35 |
| HM     | -0.03 |  0.84 | -0.15 |   0.03 | -0.86 | -0.72 |
| KB     |  0.6  |  0.82 |  0.14 |   0.16 | -0.31 | -0.21 |
| MA     | -1.81 | -1.69 | -0.64 |  -0.71 |  0.49 | -0.02 |
| MV     | -0.4  | -0.48 | -0.36 |  -0.22 | -0.12 |  0.17 |
| PB     | -2.03 | -0.93 | -1.85 |  -1.48 |  0.52 | -0.54 |
| PE     |  0.38 |  1.1  |  0.04 |   0.08 | -0.26 | -0.15 |
| SM     | -2.55 | -4.62 | -2.16 |  -2.27 | -0.14 |  0.02 |
| ST     | -0.86 | -1.6  | -1.09 |  -1.21 | -0.15 |  0.16 |
| WT     | -0.36 | -0.26 | -0.26 |  -0.22 | -0.21 |  0.52 |

KB, L6M, by hold-N and mechanic (a market at the cross, b limit at the slow EMA):

|   hold | mech   |   d_planned |    lo |   hi |   mde |   fill |   med_wait_s |   skipped_floor |
|-------:|:-------|------------:|------:|-----:|------:|-------:|-------------:|----------------:|
|      0 | a      |        0.14 | -1.06 | 1.35 |  1.72 |   0.75 |        570   |           -7.28 |
|      0 | b      |       -0.01 | -0.72 | 0.69 |  1.01 |   0.63 |        650   |           10.91 |
|      1 | a      |        0.16 | -1.08 | 1.4  |  1.77 |   0.74 |        588   |           -7.95 |
|      1 | b      |       -0.09 | -0.9  | 0.72 |  1.16 |   0.62 |        675   |           11.4  |
|      2 | a      |        0.23 | -0.95 | 1.4  |  1.67 |   0.75 |        605   |           -8.13 |
|      2 | b      |        0.23 | -0.6  | 1.06 |  1.18 |   0.61 |        692.5 |           10.1  |
|      3 | a      |        0.14 | -1.01 | 1.3  |  1.65 |   0.74 |        630   |           -8.73 |
|      3 | b      |        0.41 | -0.15 | 0.96 |  0.79 |   0.6  |        699   |            9.29 |

## 3. Cells looked at once (67 = per book top-3 + per book-session top-1 on PRE+X'), with the quant-layer header

Units: delta vs the 70/30 plain 3-pt-dip floor, pts per PLANNED lot (cf_engine primary; skipped signals count as 0 P&L in the filter mechanic) and per CONTRACT of final position (sum net / sum lots, cell minus floor). Bases: N (headline), M beside; pure-wait W0 beside. The fill basis is the measured limit-at-touch basis (the +1-tick-through variant was not run for the looked cells). Latency 1 s / 3 s = the event delayed by 1 / 3 s (headline L6M). breakeven = extra cost per fill that zeroes the L6M gain. Placebo rank = share of 200 (book rank-1 cells) / 40 / 20 state-preserving random-timing draws that beat the real cell (0.00 = real beats all). DSR with N = cumulative cells. Capacity (contracts at book depth) NOT computed (needs book-depth join at fills; not built); stack $/wk is for the six engine books only.

| book   | session   | event                                            | cell            | tier                                                               |   L3M |   L6M |   HOLD |   PRE |     X |   dpc_L6M |   fill_L6M |   L6M_mde |   trades_per_week |
|:-------|:----------|:-------------------------------------------------|:----------------|:-------------------------------------------------------------------|------:|------:|-------:|------:|------:|----------:|-----------:|----------:|------------------:|
| PE     | ALL       | 2m move resumes beyond 0.5 ATR from the WMA-20   | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            |  1.33 | -0    |   0.02 |  0.66 |  1.08 |      0.21 |       0.74 |      2.39 |             42.64 |
| DN     | ALL       | 15s ALMA-8 slope (3-bar) turns in favour         | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            |  0.49 | -0.01 |   0.3  |  1.16 |  0.7  |      0.93 |       0.79 |      1.83 |             25.04 |
| KB     | ALL       | 1s HMA 89/200 cross held 0 bars                  | a|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            |  0.27 | -0.07 |  -0.22 |  0.76 |  0.08 |     -0.09 |       0.98 |      1.18 |             44.89 |
| KB     | ALL       | 1s HMA 100/200 cross held 0 bars                 | a|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            |  0.08 | -0.1  |  -0.33 |  0.83 | -0.07 |     -0.11 |       0.98 |      1.13 |             44.89 |
| DN     | ALL       | 15s ALMA-8 slope exceeds 0.02 ATR per bar        | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            |  0.22 | -0.16 |   0.1  |  1.24 |  0.17 |      0.78 |       0.79 |      1.76 |             25.04 |
| WT     | asia      | 30s VIDYA ribbon 8/13/21/34/55 exit              | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -0.2  | -0.2  |  -0.12 |  0.67 |  0.48 |      0.38 |       0.79 |      1.41 |             16.89 |
| ST     | nyam      | 1m close reclaims the EMA-13 (close #1)          | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            |  0.66 | -0.28 |  -0.38 |  1.61 |  1.98 |      0.26 |       0.84 |      3    |             15.11 |
| WT     | london    | 3m pullback to within 1.0 ATR of the VWMA-20     | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -0.75 | -0.3  |  -0.25 |  1.02 | -0.37 |     -0.41 |       0.69 |      2.6  |             14.36 |
| WT     | ALL       | 15s pullback to within 0.5 ATR of the HMA-5      | b|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -0.3  | -0.31 |  -0.14 |  0.09 |  0.92 |     -0.19 |       0.55 |      0.78 |             60.93 |
| HM     | ALL       | 2m pullback to within 1.0 ATR of the VIDYA-9     | b|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -0.76 | -0.33 |  -0.24 |  0.34 |  0.54 |     -0.25 |       0.59 |      1.93 |             32.46 |
| MV     | london    | 15s insidebreak                                  | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -1.61 | -0.45 |  -0.66 |  4.55 |  1.96 |      1.75 |       0.61 |      5.62 |              8.18 |
| DN     | ALL       | 3m pullback to within 1.0 ATR of the EMA-8       | a|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -0.64 | -0.46 |  -0.31 |  0.84 |  0.95 |     -0.08 |       0.71 |      1.85 |             25.04 |
| WT     | ALL       | 3m pullback to within 0.5 ATR of the ALMA-9      | b|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -0.07 | -0.5  |  -0.31 |  0.18 |  0.6  |     -0.22 |       0.38 |      0.76 |             60.93 |
| KB     | nyam      | 1s T3 34/50 cross held 0 bars                    | b|far|X3|A70|N  | BEST-AVAILABLE-NEGATIVE                                            | -0.26 | -0.52 |  -0.62 |  0.6  |  1.22 |     -0.55 |       0.82 |      1.77 |             13.96 |
| ST     | asia      | 1s pullback to within 1.0 ATR of the ALMA-9      | b|far|X3|A70|N  | BEST-AVAILABLE-NEGATIVE                                            | -0.53 | -0.59 |  -1.04 |  1.11 |  1.68 |     -0.59 |       0.86 |      2.06 |             11.11 |
| WT     | ALL       | 1m pullback to within 2.0 ATR of the KAMA-89     | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -0.47 | -0.62 |  -0.58 |  0.26 |  0.64 |     -0.18 |       0.67 |      1.13 |             60.93 |
| MA     | ALL       | 3m pullback to within 1.0 ATR of the SMA-21      | b|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -1.04 | -0.64 |  -0.54 |  0.79 |  1.25 |     -0.53 |       0.62 |      2.25 |             14.54 |
| SM     | nyam      | 30s close reclaims the TEMA-9 (close #2)         | b|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -1.58 | -0.7  |  -0.87 |  1.85 |  5.11 |     -0.65 |       0.76 |      3.49 |              3.4  |
| MV     | nyam      | 3m nclose N=2                                    | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            |  0.93 | -0.71 |  -0.77 |  0.69 |  5.07 |      0.63 |       0.66 |      5.61 |             11.79 |
| MV     | nypm      | 1s accel W=10                                    | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            |  2.2  | -0.98 |  -1.68 |  1.76 |  5.21 |     -3.33 |       0.34 |      7.83 |              7.21 |
| MA     | ALL       | 15s ALMA 34/100 cross held 1 bars                | a|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -2.59 | -1.01 |  -1    |  1.11 |  0.71 |     -0.85 |       0.86 |      2.32 |             14.54 |
| KB     | nypm      | 15s pullback to within 1.0 ATR of the DEMA-9     | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -1.04 | -1.11 |  -0.77 |  0.28 |  4.12 |     -0.41 |       0.66 |      4.55 |              8.39 |
| ST     | ALL       | 2m move resumes beyond 0.5 ATR from the WMA-20   | b|far|X3|A70|N  | BEST-AVAILABLE-NEGATIVE                                            | -1.04 | -1.23 |  -1.09 |  0.43 |  0.89 |     -0.81 |       0.49 |      1.24 |             44.86 |
| SM     | ALL       | 3m pullback to within 1.0 ATR of the T3-55       | c2|mid|X8|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -0.24 | -1.24 |  -0.82 |  1.47 |  0.83 |     -1.1  |       0.4  |      2.89 |             11.63 |
| MV     | asia      | 15s move resumes beyond 2.0 ATR from the SMA-200 | b|far|X3|A70|N  | BEST-AVAILABLE-NEGATIVE                                            | -1.61 | -1.24 |  -1.2  |  1.98 |  1.03 |     -1.24 |       0.8  |      1.84 |             10.89 |
| SM     | ALL       | 3m pullback to within 1.0 ATR of the T3-55       | b|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -0.72 | -1.27 |  -0.76 |  1.59 |  1.24 |     -1.15 |       0.41 |      2.56 |             11.63 |
| ST     | ALL       | 1m move resumes beyond 0.5 ATR from the VWMA-33  | b|far|X3|A70|N  | BEST-AVAILABLE-NEGATIVE                                            | -1.05 | -1.29 |  -1.08 |  0.44 |  1.08 |     -1.02 |       0.58 |      1.6  |             44.86 |
| MA     | ALL       | 45s SMA 5/13 cross held 0 bars                   | a|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -2.39 | -1.3  |  -1.26 |  1.3  |  0.13 |     -1.15 |       0.87 |      1.82 |             14.54 |
| ST     | nypm      | 5s pullback to within 0.5 ATR of the TEMA-13     | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            |  0.27 | -1.39 |  -1.11 |  1.94 |  3.61 |     -0.26 |       0.48 |      5.54 |              7.86 |
| SM     | ALL       | 3m pullback to within 1.0 ATR of the T3-55       | b|mid|X3|A70|N  | BEST-AVAILABLE-NEGATIVE                                            | -0.06 | -1.52 |  -1.03 |  1.51 |  0.98 |     -1.42 |       0.45 |      3.16 |             11.63 |
| PB     | ALL       | 30s pullback to within 2.0 ATR of the SMA-100    | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -1.14 | -1.58 |  -1.34 |  1.92 |  0.09 |     -0.23 |       0.77 |      2.39 |             30.93 |
| DN     | asia      | 45s VWMA 5/8 cross held 1 bars                   | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            |  1.94 | -1.79 |  -2.47 |  2.1  |  1.48 |      0.35 |       0.73 |      4.24 |              6.43 |
| PE     | london    | 1m nr n=4                                        | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -2.19 | -1.85 |  -2.43 |  4.25 | -0.08 |     -0.49 |       0.59 |      7.2  |              7.89 |
| PB     | ALL       | 2m move resumes beyond 1.0 ATR from the KAMA-21  | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -1.07 | -1.95 |  -1.3  |  1.3  |  1.54 |      0.02 |       0.7  |      2.68 |             30.93 |
| HM     | london    | 3m pullback to within 0.5 ATR of the EMA-34      | b|mid|X3|A70|N  | BEST-AVAILABLE-NEGATIVE                                            | -0.23 | -2.03 |  -1.71 |  0.96 |  1.14 |     -2.12 |       0.55 |      3.59 |              7.46 |
| WT     | nyam      | 3m pullback to within 0.5 ATR of the HMA-200     | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -0.6  | -2.18 |  -2.26 |  1.14 |  1.35 |     -1.07 |       0.41 |      4.15 |             15.79 |
| HM     | ALL       | 3m pullback to within 1.0 ATR of the ALMA-50     | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -1.95 | -2.25 |  -2.12 |  0.62 | -0.03 |     -1.02 |       0.59 |      4.09 |             32.46 |
| PB     | asia      | 2m pullback to within 1.0 ATR of the KAMA-21     | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -1.97 | -2.43 |  -2.14 |  3.17 |  1.64 |      1.29 |       0.64 |      4.95 |              8.82 |
| PB     | nypm      | 1m hi-anchored VWAP band2                        | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -1.87 | -2.59 |  -3.55 |  3.59 |  5.77 |    -11.62 |       0.09 |      8.78 |              5.82 |
| HM     | ALL       | 3m pullback to within 1.0 ATR of the VWMA-20     | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -2.85 | -2.62 |  -2.94 |  0.67 |  0.24 |     -1.61 |       0.59 |      3.69 |             32.46 |
| KB     | asia      | 1s T3-34 slope exceeds 0.05 ATR per bar          | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -3.88 | -2.7  |  -1.94 |  0.25 |  5.07 |     -3.25 |       0.72 |      3.6  |             11.96 |
| HM     | nyam      | 2m pullback to within 0.5 ATR of the KAMA-50     | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -1.72 | -2.96 |  -1.41 |  0.41 |  3.93 |      1.27 |       0.48 |      7.13 |              7.96 |
| SM     | london    | 45s pullback to within 1.0 ATR of the T3-200     | b|mid|X3|A70|N  | BEST-AVAILABLE-NEGATIVE                                            | -2.74 | -3.44 |  -2.54 |  4.42 |  1.49 |     -3.36 |       0.5  |      5.07 |              3.11 |
| HM     | asia      | 15s bos fractal=3                                | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -2.87 | -3.6  |  -3.43 |  2.03 |  0.02 |     -3.1  |       0.75 |      4.34 |              9.25 |
| SM     | asia      | 3m close reclaims the TEMA-5 (close #2)          | a|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -7.83 | -3.94 |  -4.51 |  1.59 |  2    |     -3.88 |       0.93 |      6.18 |              3.56 |
| KB     | london    | 3m pullback to within 0.5 ATR of the KAMA-20     | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -4.24 | -4.07 |  -3.97 |  2.65 |  5.05 |      0.27 |       0.5  |      6.22 |              8.36 |
| PB     | nyam      | 1m hl fractal=3                                  | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -5.04 | -4.82 |  -4.55 |  3.6  |  0.29 |     -3.25 |       0.44 |      8.13 |              7.89 |
| PB     | london    | 30s ALMA 33/34 cross held 2 bars                 | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -5.15 | -4.85 |  -4.31 |  3.3  |  0.72 |     -0.1  |       0.46 |      6.69 |              6.82 |
| ST     | london    | 3m pullback to within 1.0 ATR of the KAMA-34     | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -5.58 | -4.91 |  -5.1  |  3.42 |  3    |     -3.45 |       0.69 |      5.43 |              8.36 |
| PB     | ALL       | 2m choch fractal=3                               | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -4.8  | -5.02 |  -4.46 |  2.12 |  0.12 |     -1.79 |       0.42 |      3.96 |             30.93 |
| DN     | london    | 2m HMA 8/13 cross held 2 bars                    | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -7.24 | -6.82 |  -5.05 |  2.65 |  4.19 |     -7.57 |       0.51 |      7.35 |              5.36 |
| DN     | nypm      | 15s hv-anchored VWAP band1                       | d|near|X3|A70|N | BEST-AVAILABLE-NEGATIVE                                            | -0    | -8.86 |  -8.66 |  0.87 |  7.66 |    -12.02 |       0.23 |     12.46 |              3.71 |
| PE     | nyam      | 2m move resumes beyond 0.5 ATR from the WMA-20   | d|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 |  2.46 |  1.3  |   1.01 |  2.32 |  0.42 |      1.18 |       0.76 |      3.87 |             12.57 |
| WT     | nypm      | 3m TEMA-20 slope (3-bar) turns in favour         | d|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 |  2.78 |  1.26 |   1.75 |  2.34 |  0.93 |      1.98 |       0.36 |      3.75 |             10.64 |
| HM     | nypm      | 1s pullback to within 0.5 ATR of the HMA-5       | d|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 |  4.79 |  1.25 |   1.28 |  1.8  |  5.18 |      3.47 |       0.49 |      7.02 |              6.36 |
| PE     | asia      | 5s VWMA-55 slope (3-bar) turns in favour         | d|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 |  2.91 |  1.21 |   1.44 |  2.17 |  1.3  |      3.6  |       0.63 |      5.17 |             11.68 |
| PE     | ALL       | 2m pullback to within 1.0 ATR of the WMA-33      | d|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 |  1.84 |  1.18 |   1.07 |  0.72 |  0.81 |      2.48 |       0.56 |      2.91 |             42.64 |
| MA     | asia      | 15s pullback to within 2.0 ATR of the SMA-200    | d|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 |  4.84 |  1.05 |   3.04 |  1.26 |  2.61 |      1.85 |       0.65 |      8.08 |              5.18 |
| DN     | nyam      | 15s DEMA-8 slope (3-bar) turns in favour         | d|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 | -0.16 |  0.81 |   0.74 |  2.8  |  1.82 |      0.73 |       0.82 |      3.6  |              8.18 |
| PE     | ALL       | 2m pullback to within 1.0 ATR of the VIDYA-9     | d|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 |  1.24 |  0.73 |   0.6  |  0.93 |  0.79 |      1.32 |       0.68 |      2.57 |             42.64 |
| PE     | nypm      | 3m WMA-200 slope exceeds 0.1 ATR per bar         | d|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 |  4.12 |  0.62 |   1.54 |  2.22 |  2.49 |     -8.03 |       0.13 |      7.53 |              8.21 |
| MV     | ALL       | 1m pullback to within 2.0 ATR of the KAMA-89     | d|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 |  0.72 |  0.5  |   0.44 |  0.17 |  2.83 |      1.71 |       0.67 |      3.09 |             40.39 |
| ST     | ALL       | 2m pullback to within 2.0 ATR of the KAMA-34     | d|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 |  2.59 |  0.5  |   0.58 |  0.98 |  0.68 |      2.18 |       0.7  |      2.32 |             44.86 |
| KB     | ALL       | 1s T3 33/50 cross held 0 bars                    | a|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 |  0.51 |  0.4  |   0.21 |  0.81 |  0.1  |      0.38 |       0.97 |      1.01 |             44.89 |
| MV     | ALL       | 15s pullback to within 2.0 ATR of the SMA-200    | b|near|X3|A70|N | DEAD(failed: placebo/shuffled-day)                                 |  0.65 |  0.28 |   0.1  |  0.87 |  0.45 |      0.21 |       0.66 |      1.27 |             40.39 |
| MA     | nyam      | 1m ALMA-5 slope (5-bar) turns in favour          | a|near|X3|A70|N | DEAD(failed: recent>=0 & PRE+X>0 & fill>=10%,placebo/shuffled-day) |  0.41 |  0.18 |  -0.82 |  3.58 |  2.01 |      0.66 |       0.78 |      2.62 |              3.38 |
| MV     | ALL       | 30s pullback to within 2.0 ATR of the SMA-100    | b|near|X3|A70|N | DEAD(failed: recent>=0 & PRE+X>0 & fill>=10%,placebo/shuffled-day) |  0.27 |  0.04 |  -0.16 |  0.9  |  0.32 |     -0.01 |       0.63 |      1.31 |             40.39 |

Quant-layer columns for the CANDIDATE-RECENT and the five best-L6M cells:

| book   | session   | event                                          | cell            |   L6M |   boot_week_lo |   boot_week_hi |   L6M_M |   L6M_W0N |   lat1_L6M |   lat3_L6M |   breakeven_ce |   top5_share |   dsr_L6M |   dsr_PX |   plac_rank_L6M |   plac_rank_PX |   shift7_L6M |   nbr_mean_PX |   pbo |   rc_p_PX |   rc_p_cum |   rw_survivors_book |   drift_pos |   drift_n |   fold_pos_L6M |   half1 |   half2 |   nw_t_L6M |   stack_L6M |   stack_corr | regime                                                                                                                                                                                                                              |
|:-------|:----------|:-----------------------------------------------|:----------------|------:|---------------:|---------------:|--------:|----------:|-----------:|-----------:|---------------:|-------------:|----------:|---------:|----------------:|---------------:|-------------:|--------------:|------:|----------:|-----------:|--------------------:|------------:|----------:|---------------:|--------:|--------:|-----------:|------------:|-------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| PE     | nyam      | 2m move resumes beyond 0.5 ATR from the WMA-20 | d|near|X3|A70|N |  1.3  |          -1.62 |           3.85 |    1.64 |      1.54 |       1.3  |       2.36 |           5.31 |         2.27 |      0.01 |     0.03 |            0.55 |           0    |         2.08 |         -0.54 |  0.55 |      0.71 |          1 |                   0 |           8 |        12 |              6 |   -1.1  |    2.66 |      -0.55 |       nan   |       nan    | {"vol_lo": [21, -2.84], "vol_mid": [100, 0.14], "vol_hi": [231, 2.19], "sess_asia": [0, NaN], "sess_close": [0, NaN], "sess_london": [0, NaN], "sess_nyam": [352, 1.3], "sess_nypm": [0, NaN], "sess_pre": [0, NaN]}                |
| WT     | nypm      | 3m TEMA-20 slope (3-bar) turns in favour       | d|near|X3|A70|N |  1.26 |          -1.56 |           3.86 |    2.66 |      0.45 |       1.26 |       1.45 |          10.7  |         1.73 |      0.29 |     0.42 |            0.25 |           0    |         0.75 |         -0.01 |  0.73 |      0.42 |          1 |                   0 |          10 |        12 |              4 |   -0.8  |    2.91 |       1.02 |       nan   |       nan    | {"vol_lo": [95, -3.07], "vol_mid": [107, 1.62], "vol_hi": [96, 5.13], "sess_asia": [0, NaN], "sess_close": [0, NaN], "sess_london": [0, NaN], "sess_nyam": [0, NaN], "sess_nypm": [298, 1.26], "sess_pre": [0, NaN]}                |
| HM     | nypm      | 1s pullback to within 0.5 ATR of the HMA-5     | d|near|X3|A70|N |  1.25 |          -3.86 |           6.09 |    1.95 |     -0.93 |       1.22 |      -0.3  |           7.95 |         2.2  |      0.18 |     0.02 |            0.1  |           0.05 |         1.27 |         -0.33 |  0.65 |      0.99 |          1 |                   0 |           8 |        12 |              4 |   -1.86 |    3.91 |       0.86 |       nan   |       nan    | {"vol_lo": [59, 2.73], "vol_mid": [54, -0.18], "vol_hi": [65, 1.11], "sess_asia": [0, NaN], "sess_close": [0, NaN], "sess_london": [0, NaN], "sess_nyam": [0, NaN], "sess_nypm": [178, 1.25], "sess_pre": [0, NaN]}                 |
| PE     | asia      | 5s VWMA-55 slope (3-bar) turns in favour       | d|near|X3|A70|N |  1.21 |          -2.38 |           4.78 |    1.89 |      0.54 |       2.14 |       0.72 |           6.01 |         2.48 |      0.11 |     0.01 |            0    |           0    |         1.9  |         -0.28 |  0.55 |      0.71 |          1 |                   0 |          10 |        12 |              4 |   -0.31 |    2.13 |       0.72 |       nan   |       nan    | {"vol_lo": [107, -1.49], "vol_mid": [109, 3.21], "vol_hi": [111, 1.85], "sess_asia": [327, 1.21], "sess_close": [0, NaN], "sess_london": [0, NaN], "sess_nyam": [0, NaN], "sess_nypm": [0, NaN], "sess_pre": [0, NaN]}              |
| PE     | ALL       | 2m pullback to within 1.0 ATR of the WMA-33    | d|near|X3|A70|N |  1.18 |          -0.91 |           3.19 |    1.95 |      0.98 |       1.38 |       1.33 |           6.51 |         2.57 |      0.08 |     0    |            0.22 |           0.42 |        -1.17 |         -0.36 |  0.55 |      0.71 |          1 |                   0 |           9 |        12 |              4 |    0.05 |    1.86 |       0.55 |       475.4 |        -0.42 | {"vol_lo": [229, -0.58], "vol_mid": [401, 0.83], "vol_hi": [564, 2.15], "sess_asia": [327, -1.25], "sess_close": [1, NaN], "sess_london": [221, -2.53], "sess_nyam": [352, 3.73], "sess_nypm": [230, 3.61], "sess_pre": [63, 3.76]} |

Plain sentences:

* taking the plain-dip split only if the event is already present after the PE nyam signal, waiting for 2m move resumes beyond 0.5 ATR from the WMA-20, adds +1.30 pts per contract on 76% of signals with a median wait of 7 s in L6M (MDE 3.87; PRE+X' +1.79) [tier DEAD(failed: placebo/shuffled-day); 1 of 60,584 cells in this program; 70/30 split + filter = STRUCTURE unless the placebo says otherwise]
* taking the plain-dip split only if the event is already present after the WT nypm signal, waiting for 3m TEMA-20 slope (3-bar) turns in favour, adds +1.26 pts per contract on 36% of signals with a median wait of 19 s in L6M (MDE 3.75; PRE+X' +1.92) [tier DEAD(failed: placebo/shuffled-day); 1 of 60,584 cells in this program; 70/30 split + filter = STRUCTURE unless the placebo says otherwise]
* taking the plain-dip split only if the event is already present after the HM nypm signal, waiting for 1s pullback to within 0.5 ATR of the HMA-5, adds +1.25 pts per contract on 49% of signals with a median wait of 26 s in L6M (MDE 7.02; PRE+X' +2.78) [tier DEAD(failed: placebo/shuffled-day); 1 of 60,584 cells in this program; 70/30 split + filter = STRUCTURE unless the placebo says otherwise]
* taking the plain-dip split only if the event is already present after the PE asia signal, waiting for 5s VWMA-55 slope (3-bar) turns in favour, adds +1.21 pts per contract on 63% of signals with a median wait of 78 s in L6M (MDE 5.17; PRE+X' +1.95) [tier DEAD(failed: placebo/shuffled-day); 1 of 60,584 cells in this program; 70/30 split + filter = STRUCTURE unless the placebo says otherwise]
* taking the plain-dip split only if the event is already present after the PE signal, waiting for 2m pullback to within 1.0 ATR of the WMA-33, adds +1.18 pts per contract on 56% of signals with a median wait of 22 s in L6M (MDE 2.91; PRE+X' +0.74) [tier DEAD(failed: placebo/shuffled-day); 1 of 60,584 cells in this program; 70/30 split + filter = STRUCTURE unless the placebo says otherwise]

## 4. Program-level validity (PRE+X' weeks, every S2 A70|N cell of the book)

| book   |   rc_t |   rc_p |   rc_p_cum |   rw_survivors |   pbo |   sr_var |   n_cells |
|:-------|-------:|-------:|-----------:|---------------:|------:|---------:|----------:|
| KB     |  2.945 |  0.431 |          1 |              0 | 0.627 |    0.006 |      5269 |
| PE     |  2.529 |  0.707 |          1 |              0 | 0.548 |    0.006 |      5269 |
| SM     |  2.954 |  0.573 |          1 |              0 | 0.087 |    0.008 |      5269 |
| HM     |  1.671 |  0.99  |          1 |              0 | 0.654 |    0.005 |      5269 |
| MV     |  2.564 |  0.663 |          1 |              0 | 0.655 |    0.005 |      5269 |
| PB     |  3.554 |  0.158 |          1 |              0 | 0.486 |    0.006 |      5269 |
| DN     |  3.847 |  0.086 |          1 |              0 | 0.667 |    0.006 |      5269 |
| ST     |  3.072 |  0.395 |          1 |              0 | 0.685 |    0.006 |      5269 |
| WT     |  2.784 |  0.421 |          1 |              0 | 0.731 |    0.003 |      5269 |
| MA     |  2.345 |  0.729 |          1 |              0 | 0.318 |    0.009 |      5269 |

## 5. Family view (screen, PRE+X' only; mean over specs of the n-weighted delta vs floor, pts per planned lot; mechanic a market at the event)

| fam   | ev          |     1s |     5s |    15s |    30s |    45s |     1m |     2m |     3m |
|:------|:------------|-------:|-------:|-------:|-------:|-------:|-------:|-------:|-------:|
| MA    | cross       |  -0.15 |  -0.1  |  -0.12 |  -0.15 |  -0.17 |  -0.19 |  -0.24 |  -0.26 |
| MA    | distpull    |  -0.11 |  -0.05 |  -0.1  |  -0.12 |  -0.12 |  -0.19 |  -0.22 |  -0.23 |
| MA    | distres     |  -0.18 |  -0.13 |  -0.13 |  -0.15 |  -0.16 |  -0.17 |  -0.2  |  -0.23 |
| MA    | reclaim     |  -0.17 |  -0.11 |  -0.1  |  -0.09 |  -0.1  |  -0.12 |  -0.16 |  -0.18 |
| MA    | ribbon      |  -0.14 |  -0.07 |  -0.07 |  -0.12 |  -0.12 |  -0.14 |  -0.15 |  -0.19 |
| MA    | slopeatr    |  -0.17 |  -0.11 |  -0.1  |  -0.11 |  -0.13 |  -0.14 |  -0.17 |  -0.19 |
| MA    | slopesign   |  -0.16 |  -0.1  |  -0.09 |  -0.11 |  -0.1  |  -0.12 |  -0.18 |  -0.21 |
| MV    | accel       |  -0.14 | nan    | nan    | nan    | nan    | nan    | nan    | nan    |
| MV    | bos         | nan    | nan    |  -0.1  |  -0.2  |  -0.21 |  -0.14 |  -0.3  |  -0.18 |
| MV    | brkprev     | nan    | nan    |  -0.15 |  -0.14 |  -0.1  |  -0.08 |  -0.03 |  -0.18 |
| MV    | burst       | nan    |  -0.12 | nan    | nan    | nan    | nan    | nan    | nan    |
| MV    | choch       | nan    | nan    |  -0.15 |  -0.11 |  -0.17 |  -0.2  |  -0.18 |  -0.28 |
| MV    | hl          | nan    | nan    |  -0.09 |  -0.05 |  -0.07 |  -0.05 |  -0.1  |  -0.16 |
| MV    | insidebreak | nan    | nan    |  -0.05 |  -0.2  |  -0.26 |  -0.22 |  -0.32 |  -0.29 |
| MV    | nclose      | nan    | nan    |  -0.08 |  -0.13 |  -0.11 |  -0.12 |  -0.2  |  -0.23 |
| MV    | nr          | nan    | nan    |  -0.05 |  -0.08 |  -0.19 |  -0.16 |  -0.06 |  -0.22 |
| MV    | osc         | nan    |  -0.13 |  -0.08 |  -0.09 |  -0.1  |  -0.07 |  -0.16 |  -0.14 |
| MV    | stall       |  -0.15 | nan    | nan    | nan    | nan    | nan    | nan    | nan    |
| MV    | tickspeed_z | nan    |  -0.07 |  -0.1  |  -0.11 | nan    | nan    | nan    | nan    |
| MV    | velocity    |  -0.19 | nan    | nan    | nan    | nan    | nan    | nan    | nan    |
| VW    | band1       | nan    |  -0.18 |  -0.21 |  -0.29 |  -0.27 |  -0.27 |  -0.32 |  -0.34 |
| VW    | band2       | nan    |  -0.29 |  -0.3  |  -0.3  |  -0.32 |  -0.34 |  -0.38 |  -0.38 |
| VW    | band3       | nan    |  -0.31 |  -0.32 |  -0.32 |  -0.33 |  -0.32 |  -0.32 |  -0.32 |
| VW    | cross       | nan    |  -0.17 |  -0.23 |  -0.26 |  -0.25 |  -0.23 |  -0.29 |  -0.3  |
| VW    | reclaim2    | nan    |  -0.17 |  -0.22 |  -0.23 |  -0.23 |  -0.26 |  -0.3  |  -0.31 |

Mechanic b (limit at the event reference level), level events only:

| fam   | ev          |     1s |     5s |   15s |   30s |   45s |    1m |    2m |    3m |
|:------|:------------|-------:|-------:|------:|------:|------:|------:|------:|------:|
| MA    | distpull    |  -0.14 |  -0.12 | -0.15 | -0.14 | -0.14 | -0.14 | -0.15 | -0.16 |
| MA    | distres     |  -0.11 |  -0.09 | -0.08 | -0.08 | -0.11 | -0.12 | -0.16 | -0.19 |
| MA    | reclaim     |  -0.1  |  -0.09 | -0.07 | -0.07 | -0.09 | -0.09 | -0.13 | -0.17 |
| MA    | ribbon      |  -0.17 |  -0.14 | -0.12 | -0.15 | -0.16 | -0.17 | -0.16 | -0.18 |
| MV    | bos         | nan    | nan    |  0.04 | -0.13 | -0.05 | -0.03 | -0.21 | -0.12 |
| MV    | brkprev     | nan    | nan    | -0.05 | -0.03 |  0.01 | -0.09 | -0.07 |  0.02 |
| MV    | choch       | nan    | nan    | -0.12 |  0.02 | -0.15 |  0    | -0.01 | -0.23 |
| MV    | hl          | nan    | nan    | -0.18 | -0.2  | -0.22 | -0.15 | -0    |  0.02 |
| MV    | insidebreak | nan    | nan    |  0.03 | -0.08 | -0.11 | -0.11 | -0.13 | -0.15 |
| MV    | nr          | nan    | nan    | -0    | -0.03 | -0.02 |  0.02 |  0.03 | -0.07 |
| VW    | band1       | nan    |  -0.2  | -0.23 | -0.3  | -0.25 | -0.26 | -0.33 | -0.35 |
| VW    | band2       | nan    |  -0.26 | -0.31 | -0.29 | -0.33 | -0.36 | -0.38 | -0.39 |
| VW    | band3       | nan    |  -0.32 | -0.3  | -0.31 | -0.33 | -0.31 | -0.32 | -0.33 |
| VW    | reclaim2    | nan    |  -0.17 | -0.2  | -0.21 | -0.22 | -0.23 | -0.32 | -0.33 |

MA types (all tf/periods/events, mechanic a):

| typ   |   specs |   mean_delta |   pct_pos |   best |
|:------|--------:|-------------:|----------:|-------:|
| ALMA  |    2104 |       -0.131 |     3.85  |  0.075 |
| DEMA  |    2104 |       -0.158 |     1.283 |  0.042 |
| EMA   |    2104 |       -0.148 |     1.901 |  0.069 |
| HMA   |    2102 |       -0.157 |     1.189 |  0.057 |
| KAMA  |    2104 |       -0.14  |     2.852 |  0.067 |
| SMA   |    2104 |       -0.145 |     2.424 |  0.08  |
| T3    |    2104 |       -0.176 |     0.998 |  0.13  |
| TEMA  |    2096 |       -0.156 |     1.002 |  0.05  |
| VIDYA |    2104 |       -0.171 |     1.806 |  0.141 |
| VWMA  |    1841 |       -0.141 |     2.879 |  0.057 |
| WMA   |    2104 |       -0.142 |     1.806 |  0.078 |

## 6. What was not run / limits

* JMA not built (proprietary, no public definition; same as T-ZEN). VWMA and VWAP not on 1 s (no volume series). Distance in ticks not run (monotone relabel of the ATR threshold). Event-count lot sizer (e) and structure-stop / risk-matched stop variants (f) not run: the cf_engine kernel has no such path (CF-ENG owns it). Capacity and live-calibrated basis not computed. Other bar types (BARS addendum S3: HA/range/renko/tick/volume bars) not run because nothing on time bars survived PRE+X' + recent gates; the generators accept any bar-store series (sm_series.load_store_series) if the lead wants it.
* Mechanic d (event already present as a filter) is the source of every top cell: it takes the plain-dip split only when the event state is on and books P&L 0 on skipped signals; its gain is the skipped signals' floor P&L (negative for the books where a coarse gate drops a loser-heavy subset) - a trade-selection effect measured in a few hundred trades per book, not a confirmation timing effect. Random-timing placebo for d keeps the state semantics (same events relocated within the day).
* Screen ranking used mechanics a and b only; mechanics c1/c2/d were scored only on carried specs, so a spec whose value lives in c/d could be missed.
