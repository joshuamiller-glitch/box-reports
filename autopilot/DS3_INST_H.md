# DS3_INST_H - minute-of-day alpha (T-INSTITUTIONAL section H), INST-1

**DATA line.** On disk: NQ 1-min and 1-s tables (trade first/last/hi/lo, volume, bid/ask, depth) 2023-02..2026-10, ES/RTY same, tape. Derived: label-day x ET-minute grid (780 label days to 2026-02-06; the tables label a bucket by its END, verified against the tape, grid rebuilt on bucket starts), 30-min forward range, per-signal entry minute. **To buy: nothing for section H.** Prereg `prereg/INST_H_prereg.md` sha256 `8b02e656...` (DECISIONS.md); selections logged before looks: h1_selection.json, h2_selection.json, h3_selection.json.

## Page 1

**Plain sentence.** Minute-of-day alpha (H): the 2023-26 sheet has real structure (h=1: 18 minute cells with |t|>=3 vs 3.3 under shuffled minute labels, max |t| 6.5 vs 95th 4.2; the strongest are a pre-open sell drift 09:24 and a 10:43-10:52 negative drift of 4-5 pts per 5-15 min), but walk-forward (fit trailing 6 months, trade next month) the drift-minute book fails: of 6 cells only h=15 weekday-specific passed PRE and X' (PRE +3.5, X' +0.8 pts/trade) and it is -3.5 L3M / -1.8 L6M / -2.0 HOLD per trade (MDE 8.2), shuffled-minute placebo rank 0.39, DEAD; rescaling the live brackets by minute-of-day vol lost in PRE in all 6 cells (-0.07 to -0.85 pts/signal) and the walk-forward minute-bucket skip filter lost in PRE and X' in all 4 cells, so neither got a recent look; 0 PASS, 0 CANDIDATE, nothing promoted.

### H0 sheet vs shuffled minute labels (200 draws; cells with n>=300 days)

| h (min) | real cells |t|>=3 | placebo mean (95th) | real max |t| | placebo max |t| 95th |
|---|---|---|---|---|
| 1 | 18 | 3.3 (6) | 6.54 | 4.18 |
| 5 | 25 | 3.4 (9) | 5.20 | 4.03 |
| 15 | 9 | 3.5 (11) | 4.09 | 3.82 |
| 30 | 1 | 3.9 (16) | 3.01 | 3.76 |

Strongest pooled cells (h = hold in minutes; start = bucket start; mean pts over the hold):

| h | start | mean pts | t |
|---|---|---|---|
| 1 | 09:24 ET (start) | -1.06 | -6.5 |
| 1 | 10:50 ET (start) | -1.95 | -4.5 |
| 1 | 13:12 ET (start) | +1.25 | +4.4 |
| 1 | 19:01 ET (start) | -0.60 | -4.2 |
| 1 | 15:39 ET (start) | -0.99 | -4.0 |
| 1 | 15:19 ET (start) | +0.90 | +3.9 |
| 5 | 10:48 ET (start) | -4.52 | -5.2 |
| 5 | 10:49 ET (start) | -4.02 | -4.7 |
| 5 | 09:23 ET (start) | -2.12 | -4.7 |
| 5 | 02:55 ET (start) | -1.04 | -4.2 |
| 5 | 10:50 ET (start) | -3.51 | -4.0 |
| 5 | 15:35 ET (start) | -2.44 | -3.8 |
| 15 | 10:45 ET (start) | -5.53 | -4.1 |
| 15 | 10:43 ET (start) | -5.47 | -4.0 |
| 15 | 10:44 ET (start) | -5.30 | -3.9 |
| 15 | 18:18 ET (start) | +1.73 | +3.7 |
| 15 | 10:42 ET (start) | -5.21 | -3.7 |
| 15 | 15:25 ET (start) | -3.84 | -3.5 |

Full minute x weekday return/vol tables and the signal-pay-by-hour tables: out/inst/H/sheet.pkl (keys pooled, dow, range30, range30_dow, pay_hour, pay_hour_book, pay_hour_dow).

### H1 walk-forward drift-minute book (NQ 1 contract, per trade net pts, 3-s delay unless stated; MDE = 2.8 x day-clustered SE)

| cell | carried (PRE, X' >0 in N) | L3M | L6M | HOLD | PRE | X' | MDE L6M | 1-s L6M | M L6M | tier |
|---|---|---|---|---|---|---|---|---|---|---|
| drift_wf|h=5|var=A | no | not looked | | | -0.43 | +0.25 | | | | DEAD (failed PRE+X') |
| drift_wf|h=15|var=A | no | not looked | | | -1.61 | +0.65 | | | | DEAD (failed PRE+X') |
| drift_wf|h=30|var=A | no | not looked | | | -1.81 | +2.13 | | | | DEAD (failed PRE+X') |
| drift_wf|h=5|var=B | no | not looked | | | -0.60 | -0.92 | | | | DEAD (failed PRE+X') |
| drift_wf|h=15|var=B | yes | -3.54 | -1.76 | -1.99 | +3.48 | +0.78 | 8.2 | -2.33 | -2.27 | DEAD |
| drift_wf|h=30|var=B | no | not looked | | | -0.10 | -0.17 | | | | DEAD (failed PRE+X') |

Carried cell: gates STRICT False, TOLERANT (literal) False, TOL-B and TOL-nc (post-hoc) False / False, NOW-ONLY False; stack (+5 contracts, $k/wk) L3M -1.44, L6M -0.66 (MDE 3.10), PRE +1.08, X' +0.23; persistence 0.33, shrunk size 0.00; capacity 5.0 contracts; shuffled-minute rank L6M 0.39 (all months 0.95); fit-lag 1/2/3 months L6M [-1.44, 1.02, 1.09]; trades per week 4.1; L6M by entry session {london: n16 +4.4, close: n8 -1.5, nyam: n16 -4.7, asia: n32 +0.4, pre: n4 -17.1, nypm: n38 -2.8}.

Reading: over all months the walk-forward beats 95% of shuffled-minute walk-forwards (rank 0.95 on 1-min pnl), i.e. the minute structure is not pure noise, but it has not been paying in 2025-26 and the stable cells fall under the 0.742 pt cost.

### H2 bracket re-scale by minute-of-day vol (6 cells) and H3 minute-bucket skip filter (4 cells)

H2 per-contract N delta (scaled minus original re-simulated bracket, 9,792 PRE / 2,387 X' live signals; tie-out of the engine at s=1: daily series identical to the baseline): stop g0.5 PRE -0.49 / X' +0.41; stop g1 -0.85 / +0.75; target g0.5 -0.14 / -0.62; target g1 -0.07 / -0.39; both g0.5 -0.56 / -0.26; both g1 -0.41 / +0.98. None positive in both: DEAD, no recent look, no stack line.
H3 (n skipped / PRE delta / X' delta): 15-min book 619 / -0.14 / -0.48; 15-min pooled 1,895 / -0.58 / -0.97; 30-min book 1,480 / -0.26 / -0.76; 30-min pooled 2,652 / -0.32 / -1.94. DEAD, no recent look.

### Notes
* Counts: STRICT/TOLERANT/NOW-ONLY over 16 cells: 0/0/0 (the one looked-at cell is negative in L3M, L6M, HOLD). Headline TOLERANT is the literal gate; TOL-B / TOL-nc are post-hoc labels.
* Disclosure: while testing the walk-forward code I printed one pooled all-month 1-min result (no fills, not windowed) before the selection/look split.
* dead_lookup run before scoring: 0 hits; nearby families NTE1/NTE1C tm.* time-of-day state filters, EINT2 f.excl*. DEAD_CELLS appended for the 16 cells.
* H2 limits: the lock R stays 60 pts x lots; brackets re-simulated on the 1-s path with the engine's own cost conventions (N stop 1.28, target 0; M target year cost; LIVE_CAL stop 2.45).
* The pre-open (09:24) and 10:43-10:52 drifts are in-sample sheet facts; no mechanism was tested.