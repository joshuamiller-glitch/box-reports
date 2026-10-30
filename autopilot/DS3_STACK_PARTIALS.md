# DS3_STACK_PARTIALS - T-STACK-PARTIALS: managing the stack as ONE position (SP-1, 2026-10-30)

Research only. No live, execution-server or chart change. UNTOUCHED never read. Masks own, capped 20260206 (2026=0101..0206 ~5 weeks, L6M=20250801.., **L3M=20251106..20260206 view only**, HOLD=20250701.., PRE=20240201..20250630, X'=20230401..20240131). Prereg `l2vast/ds3/prereg/SP1_prereg.md` sha256 7b82dcb0a80ab50f3859d728c7cd6767358e1f61989be7718e1cb7c80356b359; selection (PRE+X' only, basis N) sha256 9d00afcbee9a55423d062d4fab5c89f6e1ce4c8020d890424af4ed827e2b6244 logged before the single recent look; multiplicity side=stack_partials 396 cell-scopes (198 specs x 2 entry bases). Code `l2vast/ds3/code/stackpart/`, outputs `l2vast/ds3/out/stackpart/`.

## 1. One-paragraph answer

Managing the stack as one position does **not** pay on the measured fills, on the no-target-correction basis N or on the live-calibrated basis, with one narrow exception and one recency-only family. (1) Every pre-specified stack partial, stack-breakeven / MAE+k stop, staged partial, same-side cap (lots or R), correlated-entry sizing, stack cut and stack trail **lowers the stack weekly mean in PRE** (on N: 0 of 98 partial cells, 0 of 20 all-session caps, 0 of 24 stack cuts, 0 of 3 trails and 1 of 14 sizing cells (S73 only) are >= 0 in PRE; ranges PRE -44k..-2k $/wk, MDE 14-34k); the partials do not even shorten the PRE tail (worst-20 change -22%..+10%), the caps and halved sizing do (+2..+42%) but only by removing lots (mean -5k..-29k), i.e. at about the rate scaling the base down would. (2) The recency-only family is **first book stopped -> cut the rest** (cut 33/50/100% of the other same-side books when one book stops out): positive on N in L6M, HOLD and L3M on both entry bases and on LIVE-CAL, rank 0.91-1.00 (L6M/HOLD/L3M) vs 200 random cuts at the same fire rate and time-since-first-entry, but negative in PRE (-6k..-12k/wk; PRE rank 0.41-0.56 for the MKT 33/50% cells, i.e. no better than random cuts there) and ~0 in X': CANDIDATE-RECENT, not PASS. (3) The only cell >= 0 on N in PRE, X', HOLD, L6M and L3M (negative in the 5-week 2026 window: MKT -2.4k, S73 -6.5k, sign only; every effect is under 1/3 of its L6M MDE of 12-13k) is the **pre-NY-session same-side cap** (skip an entry in the 08:30-09:30 'pre' session when >= 19 research lots (~8 lots at the 12-lot live scale) are already on that side): +1.3k..+4.5k $/wk, placebo rank 0.88-1.00 vs random same-rate pre-session skips (200 draws), 6 of 6 (MKT) / 5 of 6 (S73) purged folds positive - a LEAD that fails the reality check (program RC p 0.90 / 0.50, Romano-Wolf 0 survivors, DSR 0.02); it skips 429 (MKT) / 358 (S73) of ~1,070 pre-session entries over 35 months (54 / 48 in L6M). Nothing is PASS.

Why partials do not pay: the books are 60-pt stop / 60-pt target brackets; a stack that reaches +2R keeps going to its targets about as often as it gives back. In the stack-state panel (section 3) the episodes that touched +2R ended below zero 47% of the time but ended on average +2.6 pts/lot above entry - giving up the winners' target (and paying a 0.995-pt market exit + fee on the closed lots) costs more than the give-back avoided. In the last 3-6 months the picture flips (the base stack lost in L3M, -26k/wk on M), which is why several rules look good in L6M/HOLD/L3M and not in PRE: that is a regime read, not an edge.

## 2. Program header (QUANT-LAYER section 5; program level, PRE+X' weeks, basis N)

* White RC p over the 198 specs: MKT 0.895, S73 0.498. Romano-Wolf stepdown survivors (p<=0.05): MKT 0, S73 0. PBO (CSCV, 16 blocks of weeks): MKT 0.35, S73 0.32. Best cell t: MKT 1.00, S73 1.94. N_cum for the recent-window p: 147,646 + 396.
* Minimum backtest length implied by 396 trials at weekly SR ~0.03-0.2: > 119 weeks of PRE+X' is NOT enough to separate any cell from the best of 396 noise draws (best t < 2.0).

### Header for CANDIDATE-RECENT / LEAD rows (every column; N basis unless noted; per-contract = lot-weighted pts per base trade after 0.242 fee + the exit costs of the engine)

| cell | base | pts/contract L3M [block-bootstrap CI] | L6M | HOLD | PRE | X' | trades/wk (base) | fires/wk | 1 of N | RC p (program) | Romano-Wolf survives | DSR | PBO | placebo rank L6M / PRE | neighbour mean Δ PRE+X' ($/wk) | breakeven extra cost (pts) | capacity | top-5% share of gain | corr(Δ, stack) L6M | regime it works in | drift sign (quarters +) | folds + | plain sentence |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| partial|trig=R1.5|P=33|tgt=prorata | MKT | +0.65 [-0.99,+2.46] | +0.20 | +0.25 | -0.73 | +0.14 | 128.6 | 14.7 | 1 of 396 | 0.90 | N (p 1.00) | 0.000 | 0.35 | 0.77 (200) / 0.07 (200) | -10751 | 1.1 | 8.8 lots per event = 18 s on the 2-s 1-lot slice schedule; depth NOT measured (needs top-5 depth at the fire seconds) | 0.51 | -0.58 | 0 +0.24, 1 -0.55, 2 +0.34 (vol tercile: pts per base trade L6M) | 4/12 | 2/6 | see section 6 |
| cap|lots=19|mode=skip|session=pre | MKT | +0.34 [-0.09,+0.89] | +0.17 | +0.20 | +0.08 | +0.19 | 128.6 | 2.9 | 1 of 396 | 0.90 | N (p 0.90) | 0.023 | 0.35 | 1.00 (200) / 0.99 (200) | +1306 | nan | entry skip: no extra fills; depth n/a | 1.00 | -0.11 | 0 +0.07, 1 +0.38, 2 +0.04 (vol tercile: pts per base trade L6M) | 7/12 | 6/6 | see section 6 |
| cut|trig=stackR-3|act=weakest | MKT | -0.05 [-1.19,+1.20] | +0.31 | +0.13 | -0.80 | +0.29 | 128.6 | 4.4 | 1 of 396 | 0.90 | N (p 1.00) | 0.000 | 0.35 | 0.90 (200) / 0.00 (200) | -11921 | 3.8 | 34.1 lots per event = 68 s on the 2-s 1-lot slice schedule; depth NOT measured (needs top-5 depth at the fire seconds) | 0.56 | -0.31 | 0 -1.02, 1 -1.63, 2 +1.33 (vol tercile: pts per base trade L6M) | 6/12 | 3/6 | see section 6 |
| cut|trig=firstBookStopped|act=cutRest33 | MKT | +0.95 [-0.24,+2.09] | +0.72 | +0.56 | -0.38 | -0.04 | 128.6 | 14.5 | 1 of 396 | 0.90 | N (p 1.00) | 0.000 | 0.35 | 0.98 (200) / 0.41 (200) | -4020 | 5.1 | 5.8 lots per event = 12 s on the 2-s 1-lot slice schedule; depth NOT measured (needs top-5 depth at the fire seconds) | 0.61 | -0.16 | 0 +0.42, 1 +0.84, 2 +0.31 (vol tercile: pts per base trade L6M) | 6/12 | 2/6 | see section 6 |
| cut|trig=firstBookStopped|act=cutRest50 | MKT | +2.07 [+0.57,+3.50] | +1.21 | +1.00 | -0.42 | -0.00 | 128.6 | 14.7 | 1 of 396 | 0.90 | N (p 1.00) | 0.000 | 0.35 | 1.00 (200) / 0.56 (200) | -4477 | 3.7 | 8.8 lots per event = 18 s on the 2-s 1-lot slice schedule; depth NOT measured (needs top-5 depth at the fire seconds) | 0.53 | -0.23 | 0 +0.33, 1 +1.17, 2 +1.16 (vol tercile: pts per base trade L6M) | 5/12 | 2/6 | see section 6 |
| cut|trig=firstBookStopped|act=cutRest100 | MKT | +1.49 [-0.72,+3.76] | +0.49 | +0.38 | -0.57 | +0.05 | 128.6 | 13.5 | 1 of 396 | 0.90 | N (p 1.00) | 0.000 | 0.35 | 0.97 (200) / 0.83 (200) | -4020 | 3.2 | 17.2 lots per event = 34 s on the 2-s 1-lot slice schedule; depth NOT measured (needs top-5 depth at the fire seconds) | 0.44 | -0.52 | 0 -0.22, 1 -0.43, 2 +0.72 (vol tercile: pts per base trade L6M) | 6/12 | 2/6 | see section 6 |
| confluence|cfUp1.5_3m|alone | MKT | +1.51 [+0.65,+2.46] | +0.73 | +0.62 | -0.00 | -0.01 | 128.6 | 0.0 | 1 of 396 | 0.90 | N (p 1.00) | 0.002 | 0.35 | 0.93 (200) / 0.95 (200) | +nan | nan | entry skip: no extra fills; depth n/a | 0.38 | -0.33 | 0 +0.25, 1 -0.01, 2 +0.92 (vol tercile: pts per base trade L6M) | 8/12 | 4/6 | see section 6 |
| confluence|cfUp2_3m|partial|trig=R2|P=33 | MKT | +1.54 [-0.18,+3.35] | +0.98 | +0.70 | -0.85 | -0.15 | 128.6 | 11.0 | 1 of 396 | 0.90 | N (p 1.00) | 0.000 | 0.35 | 0.63 (200) / 0.00 (200) | -14335 | 5.4 | 10.5 lots per event = 21 s on the 2-s 1-lot slice schedule; depth NOT measured (needs top-5 depth at the fire seconds) | 0.30 | -0.39 | 0 +1.14, 1 -0.44, 2 +0.91 (vol tercile: pts per base trade L6M) | 5/12 | 3/6 | see section 6 |
| cap|lots=19|mode=skip|session=pre | S73 | +0.07 [-0.42,+0.67] | +0.14 | +0.14 | +0.15 | +0.10 | 128.7 | 2.4 | 1 of 396 | 0.50 | N (p 0.81) | 0.007 | 0.32 | 1.00 (200) / 1.00 (200) | +1631 | nan | entry skip: no extra fills; depth n/a | 1.00 | -0.25 | 0 -0.18, 1 +0.66, 2 -0.01 (vol tercile: pts per base trade L6M) | 8/12 | 5/6 | see section 6 |
| cut|trig=stackR-3|act=weakest | S73 | +0.20 [-1.30,+1.86] | +0.37 | +0.35 | -0.68 | +0.13 | 128.7 | 4.1 | 1 of 396 | 0.50 | N (p 1.00) | 0.000 | 0.32 | 0.97 (200) / 0.03 (200) | -14157 | 1.7 | 34.5 lots per event = 69 s on the 2-s 1-lot slice schedule; depth NOT measured (needs top-5 depth at the fire seconds) | 0.56 | -0.32 | 0 -1.54, 1 -1.03, 2 +1.55 (vol tercile: pts per base trade L6M) | 6/12 | 2/6 | see section 6 |
| cut|trig=firstBookStopped|act=cutRest50 | S73 | +0.95 [-0.34,+2.23] | +0.32 | +0.22 | -0.32 | -0.07 | 128.7 | 14.6 | 1 of 396 | 0.50 | N (p 1.00) | 0.000 | 0.32 | 1.00 (200) / 0.80 (200) | -4478 | 1.3 | 8.7 lots per event = 17 s on the 2-s 1-lot slice schedule; depth NOT measured (needs top-5 depth at the fire seconds) | 0.55 | -0.27 | 0 -0.36, 1 +0.32, 2 +0.46 (vol tercile: pts per base trade L6M) | 6/12 | 2/6 | see section 6 |
| cut|trig=firstBookStopped|act=cutRest100 | S73 | +1.53 [-0.34,+3.31] | +0.19 | +0.12 | -0.46 | -0.04 | 128.7 | 13.5 | 1 of 396 | 0.50 | N (p 1.00) | 0.000 | 0.32 | 1.00 (200) / 0.97 (200) | -3714 | 0.5 | 17.2 lots per event = 34 s on the 2-s 1-lot slice schedule; depth NOT measured (needs top-5 depth at the fire seconds) | 0.45 | -0.55 | 0 -1.19, 1 -0.06, 2 +0.49 (vol tercile: pts per base trade L6M) | 5/12 | 2/6 | see section 6 |
| confluence|cfUp1.5_3m|partial|trig=R2|P=33 | S73 | +0.36 [-0.93,+1.79] | +0.14 | +0.08 | -0.65 | -0.22 | 128.7 | 11.2 | 1 of 396 | 0.50 | N (p 1.00) | 0.000 | 0.32 | 0.60 (200) / 0.00 (200) | -15218 | 1.4 | 10.0 lots per event = 20 s on the 2-s 1-lot slice schedule; depth NOT measured (needs top-5 depth at the fire seconds) | 0.37 | -0.40 | 0 -0.42, 1 -0.92, 2 +0.85 (vol tercile: pts per base trade L6M) | 3/12 | 3/6 | see section 6 |
| confluence|cfUp2_3m|alone | S73 | +0.41 [-0.30,+1.16] | +0.39 | +0.26 | +0.07 | -0.13 | 128.7 | 0.0 | 1 of 396 | 0.50 | N (p 1.00) | 0.000 | 0.32 | n/a / n/a | +nan | nan | entry skip: no extra fills; depth n/a | 0.30 | -0.01 | 0 +0.79, 1 -0.95, 2 +0.48 (vol tercile: pts per base trade L6M) | 5/12 | 4/6 | see section 6 |

A cell missing a column (placebo rank n/a, capacity n/a) is **not promoted**; none is promoted. Per-contract numbers are `ppc_*` in `out/stackpart/qv_cells.csv`.

## 3. Step 1 - the stack-state panel (every in-trade second)

`out/stackpart/panel/panel_YYYYMM.parquet`: 37,500,155 rows = every second in which >= 1 of the six books is open on a side (lock-admitted base set, market entries, basis M), with net same-side lots, books on the side (bitmask, count), books on the other side, combined unrealised in pts per lot and in R (R0 = $8,690, the mean book full stop at research lots), the stack's MFE / MAE since its first entry, seconds since the first entry, weakest / strongest book's own unrealised (and which book), whether all books entered within 60 / 180 / 300 s of the first (same impulse), and the first book's entry session. Episode table: `panel_episodes.parquet`.

```
37500155 20230403 20260206
episodes 5342
seconds with nb>=2 share 0.6977845558238359  nb>=3 0.4807904127329607  nb>=4 0.2976111698738312
             n  dur_min  nbmax        mfe        mae  endppl  maxR  minR
win                                                                     
L3M        335    63.75   3.24  42.599998  45.419998  -12.59  1.79 -1.81
L6M_pre3   307   119.07   3.64  42.990002  44.439999   -7.12  2.07 -2.01
PRE       1706   100.47   3.47  42.310001  45.610001  -11.90  1.94 -1.95
other      912   217.78   3.69  40.709999  45.720001  -13.59  2.08 -2.09
same impulse (all books within 3 min) vs separate
        n        mfe        mae  endppl  maxR  minR  nbmax
cl3                                                       
0    2935  42.570000  46.349998  -12.47  2.07 -2.06   3.66
1     325  36.349998  37.970001   -7.68  1.15 -1.23   2.30
           n        mfe        mae     endppl  minR  nbmax
asia    1471  40.750000  48.680000 -19.549999 -2.40   4.11
london   575  43.020000  45.349998  -9.970000 -1.83   3.29
pre      185  39.930000  45.540001 -14.530000 -1.84   3.31
nyam     724  44.169998  42.259998  -1.630000 -1.56   2.97
nypm     305  41.720001  38.250000  -2.430000 -1.29   2.59
R>= 1 2456 of 3260 end ppl mean -1.28 frac ending below 0 0.504
R>= 1.5 1968 of 3260 end ppl mean 1.52 frac ending below 0 0.477
R>= 2 1491 of 3260 end ppl mean 2.65 frac ending below 0 0.469
R>= 3 707 of 3260 end ppl mean 3.57 frac ending below 0 0.463
R<= -1 2559 end ppl mean -25.65
R<= -2 1541 end ppl mean -32.1
R<= -3 661 end ppl mean -35.82

```

Reading: 70% of in-trade seconds have >= 2 books on the same side, 48% >= 3, 30% >= 4 - the stack is the normal state, not the exception. Episodes with all books inside 3 minutes of each other ('same impulse') are rarer (10%) and smaller (2.3 books); the typical stack builds up over hours. Separate-entry stacks reach a larger MFE and larger MAE (they last longer). The 2026-10-30 11:40 case (short 12 lots: P6 5, K6 3, M6 3, H6 1) is post-cutoff and NOT read; the class of situations (>= 3 books same side within minutes, all with 60-pt stops) is rows with nb>=3 and cl3=1 in the panel.

## 4. Engine, validation and approximations

* The six-book per-book lock engine (day -2R/+5R entry test, give-back arm, week floor, 1-s MTM) is called exactly (`sl_lib.run_book`); the MKT base reproduces `ls_engine.base_daily` to 0.0 $ per book (stack L6M +18.8k/wk, HOLD +8.6k on M; the table below is on N where the target correction is removed, L6M +61k). Each modified trade is split into child rows (partials + remainder) so the lock engine sees the real partial exits.
* Stack state is computed on the set the lock engine admitted in the previous pass (3 passes; row toggles per pass ~2,000 / 150 / <10) - the feedback of rules on blocked / admitted entries is real; the residual toggles are noise-level.
* Partials are market exits at the close of the next second, cost 0.995 pt (TIMEC) + 0.242 fee per lot (the lock engine's own flatten convention uses 0.5 pt: sensitivity below, breakeven extra cost per rule).
* Libraries contain taken signals only: signals that arrived while a book was inside its original trade are absent, so the lots freed by a partial **cannot re-enter on an in-trade signal**; what is counted is the lock-engine effect (entries admitted / blocked because P&L, give-back arm and week floor states changed) and the next library signal. The re-entry columns ('Δ from the same trades' vs 're-entry in / out') report it separately: the partial is not credited with it.
* 70/30 base = L2SE pooled PRE-selected cell (dip 3, 1 of 8, no chase, risk-capped, re-based target); the second leg's add fill is simulated as in jtrade; a stack stop move is not applied to a row whose add is still pending (documented). Caps check the initial 70% lots at entry.
* Live-lot scale: research lots ST10 HM10 WT7 KB5.2 SM7.4 PE5.6 (the stack today was 12 live lots); caps 6/8/10/12 live lots are mapped x2.35 to 14/19/24/28 research lots.
* Equal-risk frame (STRUCTURE): scale the rule's weekly series by c so its worst-20-weeks equals the base's in the same window, report c * rule mean - base mean; in short windows (L3M 14 weeks, L6M 28 weeks) the worst-20 is most of the window, so the frame is unstable there and is shown for HOLD / PRE / X' too. A lot factor > 1 means the rule allows more lots at equal tail risk.

## 5. Results by rule (recent first; N basis; M and LIVE-CAL beside; 70/30 base (S73) and market base (MKT))

Stack numbers are daily-$ sums of the six books (report scale), weekly mean / SD, maxDD of the cumulative window, worst-20-weeks (sum of the 20 worst weeks), Δ = rule - base paired by week with MDE = 2.8 SE of the paired weekly difference. 'G5s' are the cap-per-session cells. Each group's single recent look covers its flagship cell (prereg), S_mean and S_risk (PRE+X' selection).

### G1 Stack partial on profit, pro-rata (X R / X pts per lot; P 25/33/50%)

| role | rule | base | Δ mean L3M | Δ mean L6M (MDE) | Δ mean HOLD | Δ mean PRE | Δ mean X' | Δ L6M on M / LIVE-CAL | Δ worst-20 L6M / PRE | equal-risk (STRUCTURE): lot factor→Δ mean, L6M ; HOLD | placebo rank L6M / PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| flagship | partial|trig=R2|P=33|tgt=prorata | MKT | +6.1k | -0.0k (+27.2k) | -0.8k | -16.5k | -3.9k | +5.5k / +4.4k | +114.1k / +72.0k | 3.94→+180.8k ; 1.16→+6.9k | 0.33 (200) / 0.00 (200) | BEST-AVAILABLE-NEGATIVE |
| S_mean | partial|trig=R1.5|P=33|tgt=prorata | MKT | +14.1k | +4.6k (+31.8k) | +4.7k | -13.2k | +1.4k | +3.5k / +0.7k | +281.4k / +99.6k | nan→n/a ; 1.49→+30.7k | 0.77 (200) / 0.07 (200) | CANDIDATE-RECENT |
| S_risk | partial|trig=R1.5|P=50|tgt=prorata | MKT | +12.1k | -6.0k (+41.5k) | -5.0k | -21.0k | +4.8k | +1.0k / -2.9k | +170.6k / +67.4k | nan→n/a ; 1.49→+16.3k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| flagship | partial|trig=R2|P=33|tgt=prorata | S73 | -9.7k | -5.6k (+23.7k) | -6.4k | -10.9k | -1.4k | -0.1k / -5.7k | -198.3k / +96.5k | nan→n/a ; 0.81→-18.1k | 0.33 (200) / 0.03 (200) | BEST-AVAILABLE-NEGATIVE |
| S_risk | partial|trig=R2|P=50|tgt=prorata | S73 | -7.2k | -7.5k (+29.7k) | -9.8k | -17.6k | -2.3k | -0.9k / -6.3k | -126.3k / +139.9k | nan→n/a ; 0.94→-13.2k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |

* **Verdict (flagship, MKT)**: partial|trig=R2|P=33|tgt=prorata (MKT, N): keeps 100% of the stack mean and cuts worst-20-weeks by +75% in the last 6 months (HOLD 98% / +14%, L3M +6.1k/wk, PRE 71% / +3%, X' 76% / +4%)
* **Verdict (flagship, S73)**: partial|trig=R2|P=33|tgt=prorata (S73, N): keeps 93% of the stack mean and cuts worst-20-weeks by -60% in the last 6 months (HOLD 90% / -24%, L3M -9.7k/wk, PRE 82% / +4%, X' 92% / +15%)

### G2 Stack partial: whole weakest book / latest entrant

| role | rule | base | Δ mean L3M | Δ mean L6M (MDE) | Δ mean HOLD | Δ mean PRE | Δ mean X' | Δ L6M on M / LIVE-CAL | Δ worst-20 L6M / PRE | equal-risk (STRUCTURE): lot factor→Δ mean, L6M ; HOLD | placebo rank L6M / PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| flagship | partial|trig=R2|P=100|tgt=weakest | MKT | +14.9k | -1.2k (+22.5k) | +1.1k | -10.9k | -6.5k | -1.2k / -6.4k | +32.4k / +112.3k | 1.27→+15.1k ; 1.13→+7.5k | 0.60 (30) / 0.03 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | partial|trig=R3|P=100|tgt=latest | MKT | -3.1k | -5.9k (+16.6k) | -4.4k | -6.4k | -0.7k | -1.4k / -6.1k | -8.1k / -23.1k | 0.95→-8.7k ; 1.07→-1.3k | 0.10 (30) / 0.00 (30) | BEST-AVAILABLE-NEGATIVE |
| flagship | partial|trig=R2|P=100|tgt=weakest | S73 | -1.6k | -8.3k (+23.5k) | -7.4k | -6.6k | -4.0k | -1.2k / -4.1k | -119.5k / +183.1k | nan→n/a ; 0.91→-13.0k | 0.17 (30) / 0.17 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | partial|trig=R2|P=100|tgt=latest | S73 | -1.2k | -4.6k (+22.4k) | -5.9k | -4.8k | +0.4k | -0.7k / -0.0k | -97.1k / +53.0k | nan→n/a ; 0.90→-11.9k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |

* **Verdict (flagship, MKT)**: partial|trig=R2|P=100|tgt=weakest (MKT, N): keeps 98% of the stack mean and cuts worst-20-weeks by +21% in the last 6 months (HOLD 102% / +11%, L3M +14.9k/wk, PRE 81% / +5%, X' 60% / +9%)
* **Verdict (flagship, S73)**: partial|trig=R2|P=100|tgt=weakest (S73, N): keeps 89% of the stack mean and cuts worst-20-weeks by -36% in the last 6 months (HOLD 89% / -10%, L3M -1.6k/wk, PRE 89% / +8%, X' 78% / +10%)

### G3 Stack partial + remaining stops to stack breakeven / MAE+k

| role | rule | base | Δ mean L3M | Δ mean L6M (MDE) | Δ mean HOLD | Δ mean PRE | Δ mean X' | Δ L6M on M / LIVE-CAL | Δ worst-20 L6M / PRE | equal-risk (STRUCTURE): lot factor→Δ mean, L6M ; HOLD | placebo rank L6M / PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| flagship | partial|trig=R2|P=33|tgt=prorata|stop=stackBE | MKT | +9.1k | +2.7k (+44.5k) | -0.0k | -29.2k | -6.8k | +3.0k / -1.8k | +146.6k / -171.4k | 23.87→+1470.1k ; 1.23→+10.9k | 0.80 (30) / 0.00 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | partial|trig=R1.5|P=33|tgt=prorata|stop=MAE+10 | MKT | +16.8k | -1.2k (+51.0k) | +2.5k | -22.3k | +7.3k | +2.4k / -7.4k | +269.2k / -72.0k | nan→n/a ; 1.76→+41.0k | 0.47 (30) / 0.00 (30) | BEST-AVAILABLE-NEGATIVE |
| S_risk | partial|trig=R1.5|P=50|tgt=prorata|stop=MAE+10 | MKT | +17.6k | -5.0k (+54.3k) | -1.9k | -29.0k | +6.9k | +1.1k / -7.9k | +147.6k / -156.9k | 28.54→+1551.4k ; 1.54→+23.3k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| flagship | partial|trig=R2|P=33|tgt=prorata|stop=stackBE | S73 | -13.9k | -9.1k (+41.6k) | -10.3k | -21.0k | -6.0k | +4.7k / -6.2k | -155.7k / -115.0k | nan→n/a ; 0.89→-16.5k | 0.13 (30) / 0.00 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | partial|trig=pts40|P=33|tgt=prorata|stop=stackBE | S73 | +5.0k | -9.2k (+35.1k) | -7.3k | -10.4k | -7.3k | +4.6k / -7.6k | -19.0k / +13.6k | nan→n/a ; 1.24→+6.8k | 0.13 (30) / 0.20 (30) | BEST-AVAILABLE-NEGATIVE |
| S_risk | partial|trig=R2|P=50|tgt=prorata|stop=MAE+10 | S73 | -5.2k | -6.8k (+34.0k) | -8.0k | -24.2k | -1.7k | +7.3k / -1.0k | -48.6k / +169.5k | nan→n/a ; 1.10→-2.0k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |

* **Verdict (flagship, MKT)**: partial|trig=R2|P=33|tgt=prorata|stop=stackBE (MKT, N): keeps 104% of the stack mean and cuts worst-20-weeks by +96% in the last 6 months (HOLD 100% / +18%, L3M +9.1k/wk, PRE 50% / -7%, X' 58% / -3%)
* **Verdict (flagship, S73)**: partial|trig=R2|P=33|tgt=prorata|stop=stackBE (S73, N): keeps 88% of the stack mean and cuts worst-20-weeks by -47% in the last 6 months (HOLD 84% / -12%, L3M -13.9k/wk, PRE 66% / -5%, X' 67% / +7%)

### G4 Staged stack partial (P at X and again at 2X)

| role | rule | base | Δ mean L3M | Δ mean L6M (MDE) | Δ mean HOLD | Δ mean PRE | Δ mean X' | Δ L6M on M / LIVE-CAL | Δ worst-20 L6M / PRE | equal-risk (STRUCTURE): lot factor→Δ mean, L6M ; HOLD | placebo rank L6M / PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| flagship | partial|trig=R2|P=33|tgt=prorata|staged=2X | MKT | +6.0k | +0.5k (+27.0k) | -0.4k | -17.0k | -4.0k | +6.1k / +4.9k | +132.5k / +31.5k | 7.47→+401.4k ; 1.19→+8.5k | 0.43 (30) / 0.00 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | partial|trig=R1.5|P=33|tgt=prorata|staged=2X | MKT | +8.2k | -0.9k (+32.4k) | -0.0k | -14.0k | +1.9k | +1.0k / -5.1k | +185.8k / +31.8k | nan→n/a ; 1.32→+15.5k | 0.50 (30) / 0.10 (30) | BEST-AVAILABLE-NEGATIVE |
| S_risk | partial|trig=R1.5|P=50|tgt=prorata|staged=2X | MKT | +4.9k | -12.0k (+43.8k) | -9.8k | -21.3k | +7.6k | -3.6k / -10.5k | +84.4k / +31.0k | 2.23→+49.0k ; 1.41→+6.1k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| flagship | partial|trig=R2|P=33|tgt=prorata|staged=2X | S73 | -9.7k | -4.9k (+23.6k) | -5.9k | -11.0k | -1.7k | +0.5k / -5.1k | -181.3k / +90.8k | nan→n/a ; 0.81→-17.7k | 0.33 (30) / 0.00 (30) | BEST-AVAILABLE-NEGATIVE |
| S_risk | partial|trig=R1|P=50|tgt=prorata|staged=2X | S73 | -16.2k | -22.2k (+42.4k) | -18.1k | -30.3k | -4.1k | -4.0k / -24.5k | -204.9k / +152.7k | nan→n/a ; 1.39→+0.9k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |

* **Verdict (flagship, MKT)**: partial|trig=R2|P=33|tgt=prorata|staged=2X (MKT, N): keeps 101% of the stack mean and cuts worst-20-weeks by +87% in the last 6 months (HOLD 99% / +16%, L3M +6.0k/wk, PRE 71% / +1%, X' 75% / +4%)
* **Verdict (flagship, S73)**: partial|trig=R2|P=33|tgt=prorata|staged=2X (S73, N): keeps 94% of the stack mean and cuts worst-20-weeks by -55% in the last 6 months (HOLD 91% / -24%, L3M -9.7k/wk, PRE 82% / +4%, X' 90% / +16%)

### G5 Same-side exposure cap in lots (per session variants G5s)

| role | rule | base | Δ mean L3M | Δ mean L6M (MDE) | Δ mean HOLD | Δ mean PRE | Δ mean X' | Δ L6M on M / LIVE-CAL | Δ worst-20 L6M / PRE | equal-risk (STRUCTURE): lot factor→Δ mean, L6M ; HOLD | placebo rank L6M / PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| flagship | cap|lots=19|mode=room | MKT | -22.3k | -21.9k (+47.5k) | -19.8k | -22.8k | -6.2k | -25.3k / -21.9k | +8.2k / +427.4k | 1.06→-19.6k ; 1.23→-13.2k | 0.00 (30) / 0.00 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | cap|lots=28|mode=room | MKT | -11.9k | -7.9k (+30.7k) | -8.4k | -15.1k | -5.2k | -12.9k / -9.0k | +111.9k / +183.4k | 3.73→+138.2k ; 1.13→-3.1k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| S_risk | cap|lots=14|mode=room | MKT | -6.3k | -25.7k (+59.3k) | -20.4k | -21.3k | -4.7k | -14.2k / -21.5k | -7.6k / +924.4k | 0.95→-27.4k ; 1.56→-4.6k | 0.00 (30) / 0.00 (30) | BEST-AVAILABLE-NEGATIVE |
| flagship | cap|lots=19|mode=room | S73 | -28.1k | -19.5k (+38.8k) | -18.1k | -14.6k | -6.4k | -25.1k / -21.8k | -192.9k / +356.1k | nan→n/a ; 0.96→-20.0k | 0.00 (30) / 0.00 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | cap|lots=24|mode=skip | S73 | -24.3k | -15.9k (+34.1k) | -18.6k | -10.7k | -2.9k | -17.6k / -15.1k | -144.2k / +358.4k | nan→n/a ; 0.88→-24.3k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| S_risk | cap|lots=14|mode=skip | S73 | -29.0k | -42.6k (+61.3k) | -36.0k | -29.4k | -6.9k | -29.7k / -38.1k | -502.7k / +683.3k | -1.95→-150.2k ; 1.02→-35.4k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |

* **Verdict (flagship, MKT)**: cap|lots=19|mode=room (MKT, N): keeps 64% of the stack mean and cuts worst-20-weeks by +5% in the last 6 months (HOLD 59% / +19%, L3M -22.3k/wk, PRE 61% / +18%, X' 61% / +29%)
* **Verdict (flagship, S73)**: cap|lots=19|mode=room (S73, N): keeps 75% of the stack mean and cuts worst-20-weeks by -58% in the last 6 months (HOLD 73% / -4%, L3M -28.1k/wk, PRE 76% / +15%, X' 65% / +27%)

### G5s Same-side lot cap applied in one entry session only

| role | rule | base | Δ mean L3M | Δ mean L6M (MDE) | Δ mean HOLD | Δ mean PRE | Δ mean X' | Δ L6M on M / LIVE-CAL | Δ worst-20 L6M / PRE | equal-risk (STRUCTURE): lot factor→Δ mean, L6M ; HOLD | placebo rank L6M / PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S_mean | cap|lots=19|mode=skip|session=pre | MKT | +4.5k | +2.6k (+13.3k) | +3.9k | +1.6k | +3.1k | +1.0k / +2.7k | +53.5k / +194.3k | 1.54→+37.0k ; 1.06→+7.2k | 1.00 (200) / 0.99 (200) | LEAD |
| S_risk | cap|lots=24|mode=skip|session=asia | MKT | -26.6k | -19.1k (+37.6k) | -16.4k | -10.7k | -0.9k | -17.8k / -17.7k | -213.4k / +171.9k | 0.42→-43.8k ; 0.91→-19.2k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| S_mean | cap|lots=19|mode=skip|session=pre | S73 | +1.3k | +2.5k (+12.3k) | +2.7k | +3.1k | +1.3k | +0.9k / +2.7k | +85.6k / +193.5k | nan→n/a ; 1.18→+15.2k | 1.00 (200) / 1.00 (200) | LEAD |
| S_risk | cap|lots=19|mode=skip|session=asia | S73 | -44.5k | -30.2k (+39.3k) | -26.3k | -15.2k | -3.6k | -28.2k / -28.0k | -592.0k / +171.4k | -1.28→-141.6k ; 0.61→-42.1k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |

* **Verdict (S_mean, MKT)**: cap|lots=19|mode=skip|session=pre (MKT, N): keeps 104% of the stack mean and cuts worst-20-weeks by +35% in the last 6 months (HOLD 108% / +6%, L3M +4.5k/wk, PRE 103% / +8%, X' 119% / +15%)
* **Verdict (S_mean, S73)**: cap|lots=19|mode=skip|session=pre (S73, N): keeps 103% of the stack mean and cuts worst-20-weeks by +26% in the last 6 months (HOLD 104% / +15%, L3M +1.3k/wk, PRE 105% / +8%, X' 107% / +12%)

### G6 Same-side exposure cap in R (lot-points)

| role | rule | base | Δ mean L3M | Δ mean L6M (MDE) | Δ mean HOLD | Δ mean PRE | Δ mean X' | Δ L6M on M / LIVE-CAL | Δ worst-20 L6M / PRE | equal-risk (STRUCTURE): lot factor→Δ mean, L6M ; HOLD | placebo rank L6M / PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| flagship | cap|lotpts=1140|mode=room | MKT | -23.6k | -20.3k (+48.8k) | -19.1k | -22.6k | -4.6k | -22.7k / -20.7k | +52.2k / +401.0k | 1.52→+1.0k ; 1.24→-12.1k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| S_mean | cap|lotpts=1680|mode=skip | MKT | -0.4k | -7.0k (+32.7k) | -6.6k | -13.6k | -2.5k | -10.4k / -7.6k | +109.8k / +368.5k | 3.54→+131.6k ; 1.23→+3.0k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| S_risk | cap|lotpts=840|mode=room | MKT | -15.3k | -29.8k (+58.1k) | -23.0k | -27.8k | -4.4k | -22.0k / -26.2k | -179.6k / +731.9k | 0.46→-46.9k ; 1.30→-15.4k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| flagship | cap|lotpts=1140|mode=room | S73 | -25.3k | -21.7k (+37.4k) | -21.6k | -14.3k | -5.8k | -24.8k / -21.6k | -151.5k / +364.3k | nan→n/a ; 0.94→-24.3k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| S_mean | cap|lotpts=1680|mode=room | S73 | -6.4k | -6.5k (+22.3k) | -7.0k | -4.6k | -5.9k | -12.5k / -10.0k | -72.3k / +86.3k | nan→n/a ; 0.90→-12.9k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| S_risk | cap|lotpts=1140|mode=skip | S73 | -27.6k | -27.3k (+45.1k) | -25.6k | -21.4k | -8.9k | -26.0k / -24.4k | -205.4k / +361.8k | nan→n/a ; 0.96→-27.4k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |

* **Verdict (flagship, MKT)**: cap|lotpts=1140|mode=room (MKT, N): keeps 67% of the stack mean and cuts worst-20-weeks by +34% in the last 6 months (HOLD 60% / +19%, L3M -23.6k/wk, PRE 61% / +17%, X' 71% / +28%)
* **Verdict (flagship, S73)**: cap|lotpts=1140|mode=room (S73, N): keeps 73% of the stack mean and cuts worst-20-weeks by -46% in the last 6 months (HOLD 68% / -6%, L3M -25.3k/wk, PRE 77% / +16%, X' 68% / +26%)

### G7 Correlated-entry sizing

| role | rule | base | Δ mean L3M | Δ mean L6M (MDE) | Δ mean HOLD | Δ mean PRE | Δ mean X' | Δ L6M on M / LIVE-CAL | Δ worst-20 L6M / PRE | equal-risk (STRUCTURE): lot factor→Δ mean, L6M ; HOLD | placebo rank L6M / PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| flagship | size|nsame>=1|same=0.5|opp=1 | MKT | +13.9k | -10.6k (+42.1k) | -6.4k | -25.6k | -4.4k | -8.5k / -9.5k | +308.7k / +666.5k | nan→n/a ; 2.06→+37.8k | 0.67 (30) / 0.13 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | size|nsame>=1|same=1|opp=1.5 | MKT | +3.3k | -5.5k (+24.0k) | -1.9k | -8.8k | +4.7k | -5.9k / -6.6k | -28.2k / -133.2k | 0.84→-14.2k ; 0.93→-5.1k | 0.00 (30) / 0.00 (30) | BEST-AVAILABLE-NEGATIVE |
| flagship | size|nsame>=1|same=0.5|opp=1 | S73 | -5.8k | -28.2k (+38.6k) | -23.9k | -26.1k | -8.3k | -19.2k / -31.8k | -178.1k / +605.2k | nan→n/a ; 1.20→-15.1k | 0.40 (30) / 0.23 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | size|nsame>=1|same=1|opp=1.5 | S73 | -11.3k | -15.9k (+16.7k) | -11.1k | -3.1k | +6.6k | -5.2k / -15.8k | -309.3k / -59.3k | nan→n/a ; 0.69→-28.4k | 0.00 (30) / 0.00 (30) | BEST-AVAILABLE-NEGATIVE |

* **Verdict (flagship, MKT)**: size|nsame>=1|same=0.5|opp=1 (MKT, N): keeps 83% of the stack mean and cuts worst-20-weeks by +202% in the last 6 months (HOLD 87% / +51%, L3M +13.9k/wk, PRE 56% / +28%, X' 73% / +42%)
* **Verdict (flagship, S73)**: size|nsame>=1|same=0.5|opp=1 (S73, N): keeps 64% of the stack mean and cuts worst-20-weeks by -54% in the last 6 months (HOLD 64% / +17%, L3M -5.8k/wk, PRE 58% / +26%, X' 54% / +41%)

### G8 Stack stop / stack cut

| role | rule | base | Δ mean L3M | Δ mean L6M (MDE) | Δ mean HOLD | Δ mean PRE | Δ mean X' | Δ L6M on M / LIVE-CAL | Δ worst-20 L6M / PRE | equal-risk (STRUCTURE): lot factor→Δ mean, L6M ; HOLD | placebo rank L6M / PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| flagship | cut|trig=stackR-2|act=prorata50 | MKT | -2.5k | -11.2k (+34.5k) | -11.9k | -11.9k | -0.8k | -15.7k / -9.1k | -102.4k / +106.9k | 0.60→-31.4k ; 0.87→-16.7k | 0.17 (30) / 0.20 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | cut|trig=stackR-3|act=latest | MKT | +0.6k | -1.7k (+11.5k) | -3.8k | -3.7k | -0.9k | -4.2k / -1.2k | -52.9k / +12.2k | 0.74→-17.1k ; 0.92→-7.3k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| S_risk | cut|trig=stackR-3|act=weakest | MKT | -1.2k | +5.9k (+40.1k) | +2.5k | -14.9k | +4.5k | -2.0k / +11.5k | +186.9k / +168.9k | nan→n/a ; 1.02→+3.7k | 0.90 (200) / 0.00 (200) | CANDIDATE-RECENT |
| flagship | cut|trig=stackR-2|act=prorata50 | S73 | -13.5k | -20.7k (+29.2k) | -19.4k | -16.7k | +0.2k | -17.4k / -17.9k | -431.7k / +48.1k | -3.34→-274.2k ; 0.61→-37.6k | 0.00 (30) / 0.00 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | cut|trig=stackR-3|act=latest | S73 | -4.6k | -2.5k (+10.5k) | -3.2k | -2.3k | -1.2k | -7.6k / -3.6k | -61.6k / +102.4k | nan→n/a ; 0.88→-10.5k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| S_risk | cut|trig=stackR-3|act=weakest | S73 | +4.9k | +7.2k (+43.4k) | +6.7k | -13.7k | +2.1k | -8.9k / +7.1k | +152.2k / +243.5k | nan→n/a ; 1.27→+26.2k | 0.97 (200) / 0.03 (200) | CANDIDATE-RECENT |

* **Verdict (flagship, MKT)**: cut|trig=stackR-2|act=prorata50 (MKT, N): keeps 82% of the stack mean and cuts worst-20-weeks by -67% in the last 6 months (HOLD 75% / -15%, L3M -2.5k/wk, PRE 79% / +4%, X' 95% / +18%)
* **Verdict (flagship, S73)**: cut|trig=stackR-2|act=prorata50 (S73, N): keeps 74% of the stack mean and cuts worst-20-weeks by -130% in the last 6 months (HOLD 71% / -63%, L3M -13.5k/wk, PRE 73% / +2%, X' 101% / +17%)

### G9 First book stopped: cut the rest

| role | rule | base | Δ mean L3M | Δ mean L6M (MDE) | Δ mean HOLD | Δ mean PRE | Δ mean X' | Δ L6M on M / LIVE-CAL | Δ worst-20 L6M / PRE | equal-risk (STRUCTURE): lot factor→Δ mean, L6M ; HOLD | placebo rank L6M / PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| flagship | cut|trig=firstBookStopped|act=cutRest50 | MKT | +35.7k | +23.0k (+28.5k) | +19.3k | -8.2k | +0.7k | +6.8k / +20.6k | +464.9k / +114.5k | nan→n/a ; 1.33→+41.5k | 1.00 (200) / 0.56 (200) | CANDIDATE-RECENT |
| S_mean | cut|trig=firstBookStopped|act=cutRest33 | MKT | +15.4k | +13.5k (+20.4k) | +11.0k | -7.3k | +0.1k | +6.5k / +16.2k | +292.8k / +170.2k | nan→n/a ; 1.19→+22.2k | 0.98 (200) / 0.41 (200) | CANDIDATE-RECENT |
| S_risk | cut|trig=firstBookStopped|act=cutRest100 | MKT | +26.5k | +10.4k (+44.2k) | +7.9k | -11.6k | +1.8k | -3.9k / +13.5k | +345.4k / +293.0k | nan→n/a ; 1.23→+20.7k | 0.97 (200) / 0.83 (200) | CANDIDATE-RECENT |
| flagship | cut|trig=firstBookStopped|act=cutRest50 | S73 | +16.0k | +6.6k (+26.8k) | +4.6k | -6.5k | -0.4k | +4.3k / +6.7k | +130.1k / +168.6k | nan→n/a ; 1.00→+4.7k | 1.00 (200) / 0.80 (200) | CANDIDATE-RECENT |
| S_risk | cut|trig=firstBookStopped|act=cutRest100 | S73 | +27.8k | +4.6k (+42.2k) | +3.1k | -9.4k | +0.3k | -5.9k / +8.3k | +209.1k / +356.9k | nan→n/a ; 1.24→+19.6k | 1.00 (200) / 0.97 (200) | CANDIDATE-RECENT |

* **Verdict (flagship, MKT)**: cut|trig=firstBookStopped|act=cutRest50 (MKT, N): keeps 137% of the stack mean and cuts worst-20-weeks by +304% in the last 6 months (HOLD 140% / +25%, L3M +35.7k/wk, PRE 86% / +5%, X' 104% / -2%)
* **Verdict (flagship, S73)**: cut|trig=firstBookStopped|act=cutRest50 (S73, N): keeps 108% of the stack mean and cuts worst-20-weeks by +39% in the last 6 months (HOLD 107% / +0%, L3M +16.0k/wk, PRE 90% / +7%, X' 98% / -2%)

### G10 Stack trail on the combined position

| role | rule | base | Δ mean L3M | Δ mean L6M (MDE) | Δ mean HOLD | Δ mean PRE | Δ mean X' | Δ L6M on M / LIVE-CAL | Δ worst-20 L6M / PRE | equal-risk (STRUCTURE): lot factor→Δ mean, L6M ; HOLD | placebo rank L6M / PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| flagship | trail|T=30|stack | MKT | -0.2k | -18.5k (+72.5k) | -15.2k | -25.2k | -10.3k | -11.6k / -16.1k | -141.1k / +62.4k | 0.52→-39.1k ; 0.94→-17.2k | 0.40 (30) / 0.07 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | trail|T=40|stack | MKT | +31.8k | -8.3k (+52.1k) | -3.2k | -12.3k | +2.3k | -8.8k / -6.8k | -43.8k / +135.8k | 0.78→-20.2k ; 1.02→-2.3k | 0.43 (30) / 0.23 (30) | BEST-AVAILABLE-NEGATIVE |
| flagship | trail|T=30|stack | S73 | +1.3k | -19.3k (+64.3k) | -21.1k | -19.1k | -17.8k | -16.5k / -18.3k | -235.5k / +212.0k | nan→n/a ; 0.92→-24.8k | 0.43 (30) / 0.43 (30) | BEST-AVAILABLE-NEGATIVE |
| S_mean | trail|T=40|stack | S73 | +6.7k | -16.5k (+43.6k) | -15.7k | -3.2k | -1.7k | -11.4k / -14.9k | -153.7k / +309.6k | nan→n/a ; 1.00→-15.5k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |

* **Verdict (flagship, MKT)**: trail|T=30|stack (MKT, N): keeps 70% of the stack mean and cuts worst-20-weeks by -92% in the last 6 months (HOLD 69% / -6%, L3M -0.2k/wk, PRE 57% / +3%, X' 36% / -19%)
* **Verdict (flagship, S73)**: trail|T=30|stack (S73, N): keeps 76% of the stack mean and cuts worst-20-weeks by -71% in the last 6 months (HOLD 68% / -9%, L3M +1.3k/wk, PRE 69% / +9%, X' 2% / -21%)

### G11 Confluence (EINT1) with / without the stack partial

| role | rule | base | Δ mean L3M | Δ mean L6M (MDE) | Δ mean HOLD | Δ mean PRE | Δ mean X' | Δ L6M on M / LIVE-CAL | Δ worst-20 L6M / PRE | equal-risk (STRUCTURE): lot factor→Δ mean, L6M ; HOLD | placebo rank L6M / PRE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| flagship | confluence|cfUp2_3m|partial|trig=R2|P=33 | MKT | +32.7k | +17.8k (+39.3k) | +14.2k | -14.8k | -3.0k | +16.8k / +15.2k | +506.2k / -94.2k | nan→n/a ; 1.58→+50.4k | 0.63 (200) / 0.00 (200) | CANDIDATE-RECENT |
| S_mean | confluence|cfUp1.5_3m|alone | MKT | +29.4k | +13.4k (+26.2k) | +11.3k | +0.5k | -0.1k | +15.5k / +13.2k | +413.7k / +185.4k | nan→n/a ; 1.46→+38.7k | 0.93 (200) / 0.95 (200) | CANDIDATE-RECENT |
| flagship | confluence|cfUp2_3m|partial|trig=R2|P=33 | S73 | +7.2k | -1.9k (+37.6k) | -5.6k | -11.7k | -7.5k | +9.9k / -4.6k | -12.8k / -62.6k | nan→n/a ; 0.92→-10.6k | n/a / n/a | BEST-AVAILABLE-NEGATIVE |
| S_mean | confluence|cfUp2_3m|alone | S73 | +8.2k | +6.6k (+26.0k) | +5.2k | +1.9k | -2.1k | +3.2k / +6.4k | +25.7k / -148.1k | nan→n/a ; 0.89→-2.5k | n/a / n/a | CANDIDATE-RECENT |
| S_risk | confluence|cfUp1.5_3m|partial|trig=R2|P=33 | S73 | +6.7k | +4.1k (+28.6k) | +2.0k | -11.1k | -4.3k | +7.7k / +7.8k | +95.4k / -49.5k | nan→n/a ; 1.30→+22.6k | 0.60 (200) / 0.00 (200) | CANDIDATE-RECENT |

* **Verdict (flagship, MKT)**: confluence|cfUp2_3m|partial|trig=R2|P=33 (MKT, N): keeps 129% of the stack mean and cuts worst-20-weeks by +331% in the last 6 months (HOLD 129% / +37%, L3M +32.7k/wk, PRE 74% / -4%, X' 81% / +8%)
* **Verdict (flagship, S73)**: confluence|cfUp2_3m|partial|trig=R2|P=33 (S73, N): keeps 98% of the stack mean and cuts worst-20-weeks by -4% in the last 6 months (HOLD 92% / -9%, L3M +7.2k/wk, PRE 81% / -3%, X' 59% / +1%)

### Detail tables (flagship cells and every CANDIDATE-RECENT / LEAD row): stack weekly mean, SD, maxDD, worst-20-weeks, recent first

#### partial|trig=R2|P=33|tgt=prorata - MKT - tier BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +11.0k → +17.2k | +6.1k (+32.7k) | 140k → 137k | 372k → 444k | 155k → 241k | +85.9k | nan / n/a | +0.8k / +8.0k / -2.7k |
| 2026 | +18.9k → +47.0k | +28.1k (+52.5k) | 186k → 155k | 346k → 279k | 114k → 282k | +168.3k | nan / n/a | +9.2k / +18.1k / +0.8k |
| L6M | +61.5k → +61.5k | -0.0k (+27.2k) | 146k → 132k | 372k → 444k | -153k → -39k | +114.1k | 3.94 / +180.8k | -8.2k / +10.4k / -2.2k |
| HOLD | +48.3k → +47.5k | -0.8k (+23.8k) | 173k → 160k | 651k → 659k | -1095k → -941k | +153.3k | 1.16 / +6.9k | -8.4k / +10.0k / -2.5k |
| PRE | +58.0k → +41.5k | -16.5k (+15.9k) | 139k → 125k | 704k → 517k | -2418k → -2346k | +72.0k | 1.03 / -15.3k | -7.2k / -7.9k / -1.5k |
| X' | +16.0k → +12.2k | -3.9k (+14.9k) | 104k → 86k | 490k → 379k | -1457k → -1396k | +61.4k | 1.04 / -3.3k | +0.3k / -3.0k / -1.2k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -26.5k → -25.5k | +0.9k (+27.3k) | 135k → 119k | 608k → 628k | -371k → -357k | +13.3k | 1.04 / -0.0k | +5.9k / -6.8k / +1.9k |
| 2026 | -18.7k → -3.2k | +15.5k (+52.2k) | 185k → 146k | 457k → 363k | -112k → -19k | +93.1k | 5.79 / -0.0k | +9.2k / +5.0k / +1.4k |
| L6M | +18.8k → +24.3k | +5.5k (+19.1k) | 135k → 125k | 608k → 628k | -882k → -703k | +178.3k | 1.25 / +11.7k | +3.7k / +0.7k / +1.2k |
| HOLD | +8.6k → +12.2k | +3.6k (+17.6k) | 163k → 150k | 696k → 687k | -1777k → -1551k | +226.1k | 1.15 / +5.4k | +2.9k / -0.6k / +1.2k |
| PRE | +27.7k → +22.2k | -5.5k (+12.9k) | 130k → 125k | 746k → 579k | -2817k → -2729k | +88.5k | 1.03 / -4.8k | -3.0k / -3.4k / +0.9k |
| X' | +5.2k → +2.5k | -2.7k (+15.5k) | 102k → 84k | 567k → 489k | -1653k → -1561k | +92.4k | 1.06 / -2.5k | +0.9k / -3.1k / -0.5k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -1.0k → +11.4k | +12.4k (+26.9k) | 141k → 137k | 417k → 483k | -14k → 159k | +173.9k | nan / n/a | +2.5k / +7.5k / +2.4k |
| 2026 | +11.5k → +39.8k | +28.3k (+50.0k) | 187k → 160k | 371k → 295k | 69k → 239k | +170.0k | nan / n/a | +10.1k / +19.5k / -1.3k |
| L6M | +50.0k → +54.4k | +4.4k (+22.1k) | 145k → 136k | 417k → 483k | -372k → -215k | +156.5k | 1.73 / +43.9k | -6.3k / +9.7k / +1.0k |
| HOLD | +37.2k → +40.0k | +2.8k (+19.7k) | 173k → 163k | 684k → 687k | -1321k → -1135k | +185.5k | 1.16 / +9.3k | -6.7k / +9.1k / +0.4k |
| PRE | +46.1k → +31.8k | -14.4k (+15.3k) | 137k → 125k | 778k → 602k | -2620k → -2503k | +116.4k | 1.05 / -12.9k | -8.1k / -6.0k / -0.2k |
| X' | +7.0k → +2.4k | -4.7k (+15.2k) | 104k → 87k | 560k → 537k | -1661k → -1618k | +42.6k | 1.03 / -4.6k | +0.3k / -3.9k / -1.0k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 648 | +4.65 | +0.32 (MDE 3.30) | +1.5k |
| HM | 538 | +3.27 | +0.97 (MDE 2.46) | +3.7k |
| WT | 874 | +1.80 | -0.43 (MDE 1.05) | -1.9k |
| KB | 649 | +3.73 | -1.75 (MDE 2.99) | -4.2k |
| SM | 279 | +2.00 | +0.89 (MDE 3.00) | +1.3k |
| PE | 612 | +3.11 | -0.18 (MDE 2.20) | -0.4k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1618 | +4.25 | -1.95 (MDE 1.61) | -8.4k |
| HM | 1532 | +2.45 | -0.58 (MDE 1.83) | -2.4k |
| WT | 2386 | +0.73 | -0.06 (MDE 0.63) | -0.3k |
| KB | 1678 | +4.96 | -0.95 (MDE 1.88) | -2.2k |
| SM | 822 | +4.43 | -0.73 (MDE 1.13) | -1.2k |
| PE | 1621 | +3.17 | -0.87 (MDE 1.62) | -2.1k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1579 | -0.61 |
| london | 804 | -1.13 |
| pre | 165 | +0.49 |
| nyam | 744 | +2.02 |
| nypm | 305 | -1.16 |
| close | 3 | -1.99 |

#### partial|trig=R1.5|P=33|tgt=prorata - MKT - tier CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +11.0k → +25.1k | +14.1k (+49.2k) | 140k → 124k | 372k → 501k | 155k → 352k | +197.2k | nan / n/a | -1.9k / +13.1k / +2.9k |
| 2026 | +18.9k → +70.2k | +51.3k (+98.6k) | 186k → 129k | 346k → 210k | 114k → 421k | +307.6k | nan / n/a | +9.4k / +39.0k / +2.8k |
| L6M | +61.5k → +66.0k | +4.6k (+31.8k) | 146k → 124k | 372k → 501k | -153k → 128k | +281.4k | nan / n/a | -8.7k / +12.1k / +1.1k |
| HOLD | +48.3k → +53.0k | +4.7k (+28.9k) | 173k → 148k | 651k → 559k | -1095k → -734k | +360.4k | 1.49 / +30.7k | -6.9k / +11.2k / +0.3k |
| PRE | +58.0k → +44.8k | -13.2k (+15.5k) | 139k → 129k | 704k → 492k | -2418k → -2318k | +99.6k | 1.04 / -11.3k | -9.8k / -3.1k / -0.3k |
| X' | +16.0k → +17.4k | +1.4k (+17.3k) | 104k → 92k | 490k → 413k | -1457k → -1352k | +105.2k | 1.08 / +2.7k | +2.2k / -0.7k / -0.1k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -26.5k → -20.1k | +6.3k (+42.0k) | 135k → 112k | 608k → 592k | -371k → -282k | +88.8k | 1.32 / -0.0k | +2.4k / +1.2k / +2.8k |
| 2026 | -18.7k → +7.1k | +25.8k (+82.3k) | 185k → 126k | 457k → 330k | -112k → 42k | +154.8k | nan / n/a | +7.9k / +19.3k / -1.4k |
| L6M | +18.8k → +22.3k | +3.5k (+26.0k) | 135k → 113k | 608k → 592k | -882k → -649k | +233.2k | 1.36 / +11.5k | -2.2k / +4.7k / +0.9k |
| HOLD | +8.6k → +11.4k | +2.8k (+24.7k) | 163k → 137k | 696k → 614k | -1777k → -1415k | +362.1k | 1.26 / +5.7k | +0.1k / +1.7k / +1.0k |
| PRE | +27.7k → +18.7k | -9.0k (+13.8k) | 130k → 129k | 746k → 575k | -2817k → -2924k | -106.8k | 0.96 / -9.7k | -4.5k / -4.4k / -0.1k |
| X' | +5.2k → +8.1k | +3.0k (+17.3k) | 102k → 90k | 567k → 435k | -1653k → -1504k | +149.3k | 1.10 / +3.8k | +3.4k / -0.6k / +0.1k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -1.0k → +8.6k | +9.7k (+46.1k) | 141k → 121k | 417k → 545k | -14k → 121k | +135.4k | nan / n/a | -0.5k / +8.6k / +1.6k |
| 2026 | +11.5k → +49.4k | +37.9k (+96.2k) | 187k → 127k | 371k → 237k | 69k → 296k | +227.6k | nan / n/a | +8.8k / +32.4k / -3.3k |
| L6M | +50.0k → +50.7k | +0.7k (+29.1k) | 145k → 124k | 417k → 545k | -372k → -142k | +229.3k | 2.61 / +82.5k | -7.2k / +7.6k / +0.3k |
| HOLD | +37.2k → +37.7k | +0.5k (+26.7k) | 173k → 149k | 684k → 607k | -1321k → -1015k | +305.5k | 1.30 / +11.9k | -5.5k / +6.4k / -0.4k |
| PRE | +46.1k → +30.3k | -15.8k (+14.7k) | 137k → 129k | 778k → 643k | -2620k → -2669k | -49.7k | 0.98 / -16.4k | -10.5k / -5.4k / +0.0k |
| X' | +7.0k → +8.5k | +1.5k (+17.5k) | 104k → 94k | 560k → 447k | -1661k → -1547k | +113.7k | 1.07 / +2.1k | +2.4k / -1.0k / +0.1k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 648 | +4.65 | +1.06 (MDE 3.41) | +4.9k |
| HM | 538 | +3.27 | +0.38 (MDE 2.98) | +1.4k |
| WT | 874 | +1.80 | -0.27 (MDE 1.21) | -1.2k |
| KB | 649 | +3.73 | -1.33 (MDE 2.98) | -3.2k |
| SM | 279 | +2.00 | +0.42 (MDE 3.59) | +0.6k |
| PE | 612 | +3.11 | +0.81 (MDE 2.41) | +2.0k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1618 | +4.25 | -1.21 (MDE 1.89) | -5.2k |
| HM | 1532 | +2.45 | -0.53 (MDE 1.92) | -2.2k |
| WT | 2386 | +0.73 | -0.19 (MDE 0.73) | -0.8k |
| KB | 1678 | +4.96 | -0.60 (MDE 1.90) | -1.4k |
| SM | 822 | +4.43 | -1.02 (MDE 1.27) | -1.7k |
| PE | 1621 | +3.17 | -0.79 (MDE 1.93) | -1.9k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1579 | -0.50 |
| london | 804 | -0.75 |
| pre | 165 | +0.81 |
| nyam | 744 | +1.79 |
| nypm | 305 | +1.13 |
| close | 3 | -1.99 |

#### partial|trig=R2|P=33|tgt=prorata - S73 - tier BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +31.3k → +21.5k | -9.7k (+32.7k) | 130k → 128k | 319k → 420k | 438k → 301k | -136.2k | nan / n/a | -2.1k / +1.8k / -9.4k |
| 2026 | +37.0k → +40.0k | +3.0k (+42.2k) | 185k → 154k | 306k → 281k | 222k → 240k | +17.9k | nan / n/a | +0.1k / +5.7k / -2.8k |
| L6M | +79.1k → +73.5k | -5.6k (+23.7k) | 137k → 138k | 319k → 420k | 332k → 134k | -198.3k | nan / n/a | -7.9k / +7.0k / -4.7k |
| HOLD | +66.7k → +60.3k | -6.4k (+21.4k) | 169k → 165k | 625k → 592k | -630k → -781k | -151.3k | 0.81 / -18.1k | -8.4k / +6.5k / -4.5k |
| PRE | +61.8k → +50.9k | -10.9k (+13.9k) | 139k → 128k | 615k → 486k | -2305k → -2208k | +96.5k | 1.04 / -8.7k | -7.8k / -1.9k / -1.3k |
| X' | +18.2k → +16.8k | -1.4k (+15.9k) | 102k → 82k | 469k → 357k | -1392k → -1186k | +205.9k | 1.17 / +1.5k | -1.1k / -0.4k / +0.1k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -17.2k → -19.0k | -1.8k (+22.3k) | 136k → 121k | 537k → 549k | -241k → -266k | -25.1k | 0.91 / +0.0k | +6.4k / -6.8k / -1.4k |
| 2026 | +0.8k → -6.9k | -7.7k (+46.5k) | 183k → 148k | 348k → 323k | 5k → -42k | -46.4k | -0.11 / -0.0k | +6.1k / -9.0k / -4.8k |
| L6M | +32.1k → +32.0k | -0.1k (+17.8k) | 139k → 128k | 537k → 549k | -639k → -534k | +104.4k | 1.20 / +6.2k | -0.5k / +0.7k / -0.3k |
| HOLD | +20.2k → +19.0k | -1.1k (+16.3k) | 165k → 153k | 698k → 651k | -1559k → -1409k | +149.9k | 1.11 / +0.9k | -1.1k / +0.5k / -0.6k |
| PRE | +35.4k → +26.5k | -8.8k (+14.7k) | 137k → 127k | 756k → 595k | -2788k → -2785k | +3.7k | 1.00 / -8.8k | -3.3k / -4.7k / -0.8k |
| X' | +8.0k → +7.1k | -0.9k (+15.6k) | 99k → 80k | 520k → 381k | -1559k → -1332k | +227.3k | 1.17 / +0.3k | +0.6k / -1.4k / -0.0k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +15.1k → +1.8k | -13.2k (+25.4k) | 135k → 126k | 363k → 462k | 211k → 25k | -185.3k | nan / n/a | -0.7k / -7.4k / -5.1k |
| 2026 | +26.0k → +18.1k | -8.0k (+43.7k) | 192k → 156k | 322k → 292k | 156k → 109k | -47.7k | nan / n/a | +0.8k / -5.8k / -2.9k |
| L6M | +65.1k → +59.5k | -5.7k (+20.5k) | 139k → 137k | 363k → 462k | 51k → -91k | -142.1k | -0.56 / -98.4k | -7.1k / +2.3k / -0.9k |
| HOLD | +53.2k → +44.6k | -8.6k (+19.1k) | 171k → 164k | 658k → 657k | -927k → -1056k | -128.1k | 0.88 / -14.0k | -7.9k / +0.7k / -1.4k |
| PRE | +50.0k → +38.7k | -11.2k (+14.5k) | 139k → 128k | 705k → 585k | -2540k → -2492k | +48.1k | 1.02 / -10.5k | -7.1k / -2.8k / -1.3k |
| X' | +9.5k → +6.7k | -2.7k (+16.1k) | 103k → 82k | 525k → 410k | -1599k → -1375k | +223.1k | 1.16 / -1.6k | -1.6k / -0.7k / -0.4k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 660 | +6.25 | +0.13 (MDE 3.34) | +0.6k |
| HM | 541 | +3.73 | +1.16 (MDE 2.66) | +4.5k |
| WT | 897 | +2.64 | -0.33 (MDE 0.65) | -1.5k |
| KB | 637 | +4.03 | -3.22 (MDE 2.34) | -7.6k |
| SM | 282 | +3.96 | -0.22 (MDE 2.58) | -0.3k |
| PE | 587 | +3.36 | -0.51 (MDE 2.90) | -1.2k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1649 | +4.42 | -0.95 (MDE 1.59) | -4.2k |
| HM | 1550 | +2.76 | -0.35 (MDE 1.95) | -1.5k |
| WT | 2373 | +1.06 | -0.05 (MDE 0.71) | -0.2k |
| KB | 1707 | +4.09 | -0.53 (MDE 1.35) | -1.3k |
| SM | 821 | +4.56 | -0.93 (MDE 1.16) | -1.5k |
| PE | 1610 | +3.86 | -0.95 (MDE 1.63) | -2.3k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1585 | -0.73 |
| london | 822 | -1.28 |
| pre | 167 | +1.41 |
| nyam | 732 | -0.13 |
| nypm | 294 | +0.24 |
| close | 4 | +0.00 |

#### cut|trig=firstBookStopped|act=cutRest50 - MKT - tier CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +11.0k → +46.8k | +35.7k (+44.3k) | 140k → 153k | 372k → 472k | 155k → 655k | +500.4k | nan / n/a | +10.2k / +19.8k / +5.7k |
| 2026 | +18.9k → +88.0k | +69.1k (+54.0k) | 186k → 170k | 346k → 245k | 114k → 528k | +414.4k | nan / n/a | +16.5k / +44.3k / +8.3k |
| L6M | +61.5k → +84.5k | +23.0k (+28.5k) | 146k → 144k | 372k → 472k | -153k → 312k | +464.9k | nan / n/a | +3.4k / +17.4k / +2.2k |
| HOLD | +48.3k → +67.7k | +19.3k (+26.1k) | 173k → 179k | 651k → 708k | -1095k → -824k | +270.7k | 1.33 / +41.5k | +4.1k / +13.1k / +2.1k |
| PRE | +58.0k → +49.8k | -8.2k (+15.4k) | 139k → 133k | 704k → 668k | -2418k → -2303k | +114.5k | 1.05 / -5.7k | -4.4k / -2.8k / -1.0k |
| X' | +16.0k → +16.7k | +0.7k (+17.9k) | 104k → 105k | 490k → 426k | -1457k → -1483k | -25.5k | 0.98 / +0.4k | -1.6k / +3.4k / -1.2k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -26.5k → -17.9k | +8.6k (+38.3k) | 135k → 142k | 608k → 662k | -371k → -251k | +120.2k | 1.48 / +0.0k | +11.4k / -3.7k / +0.9k |
| 2026 | -18.7k → +29.2k | +47.9k (+52.9k) | 185k → 181k | 457k → 320k | -112k → 175k | +287.5k | nan / n/a | +20.2k / +25.6k / +2.1k |
| L6M | +18.8k → +25.6k | +6.8k (+24.0k) | 135k → 131k | 608k → 662k | -882k → -691k | +190.6k | 1.28 / +13.8k | +2.8k / +3.5k / +0.5k |
| HOLD | +8.6k → +10.7k | +2.1k (+22.6k) | 163k → 163k | 696k → 765k | -1777k → -1700k | +76.9k | 1.05 / +2.6k | +3.4k / +0.0k / -1.3k |
| PRE | +27.7k → +21.2k | -6.6k (+14.4k) | 130k → 133k | 746k → 745k | -2817k → -2833k | -16.1k | 0.99 / -6.7k | -2.8k / -3.8k / +0.1k |
| X' | +5.2k → +6.4k | +1.2k (+17.9k) | 102k → 104k | 567k → 511k | -1653k → -1648k | +5.0k | 1.00 / +1.2k | -0.6k / +2.9k / -1.1k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -1.0k → +28.6k | +29.6k (+41.5k) | 141k → 151k | 417k → 515k | -14k → 400k | +414.8k | nan / n/a | +13.3k / +10.1k / +6.2k |
| 2026 | +11.5k → +77.2k | +65.7k (+49.2k) | 187k → 178k | 371k → 272k | 69k → 463k | +394.4k | nan / n/a | +17.4k / +39.0k / +9.3k |
| L6M | +50.0k → +70.6k | +20.6k (+25.7k) | 145k → 143k | 417k → 515k | -372k → 67k | +438.2k | nan / n/a | +6.5k / +11.6k / +2.5k |
| HOLD | +37.2k → +54.9k | +17.7k (+23.4k) | 173k → 178k | 684k → 731k | -1321k → -1019k | +302.1k | 1.30 / +34.0k | +7.3k / +8.0k / +2.4k |
| PRE | +46.1k → +39.8k | -6.4k (+14.0k) | 137k → 132k | 778k → 667k | -2620k → -2412k | +207.9k | 1.09 / -2.9k | -2.0k / -3.8k / -0.6k |
| X' | +7.0k → +8.4k | +1.4k (+17.4k) | 104k → 103k | 560k → 497k | -1661k → -1625k | +36.1k | 1.02 / +1.5k | +0.8k / +1.4k / -0.8k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 648 | +4.65 | +2.05 (MDE 3.51) | +9.5k |
| HM | 538 | +3.27 | +2.81 (MDE 3.48) | +10.8k |
| WT | 874 | +1.80 | -0.22 (MDE 0.29) | -1.0k |
| KB | 649 | +3.73 | -0.38 (MDE 3.47) | -0.9k |
| SM | 279 | +2.00 | +1.02 (MDE 3.71) | +1.5k |
| PE | 612 | +3.11 | +1.25 (MDE 3.18) | +3.1k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1618 | +4.25 | -1.18 (MDE 1.69) | -5.1k |
| HM | 1532 | +2.45 | +0.56 (MDE 1.89) | +2.3k |
| WT | 2386 | +0.73 | +0.06 (MDE 0.29) | +0.3k |
| KB | 1678 | +4.96 | -1.15 (MDE 2.12) | -2.7k |
| SM | 822 | +4.43 | -0.39 (MDE 1.46) | -0.6k |
| PE | 1621 | +3.17 | -0.97 (MDE 1.91) | -2.4k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1579 | +0.36 |
| london | 804 | +0.65 |
| pre | 165 | -1.24 |
| nyam | 744 | +2.35 |
| nypm | 305 | +2.67 |
| close | 3 | +3.50 |

#### cut|trig=firstBookStopped|act=cutRest33 - MKT - tier CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +11.0k → +26.4k | +15.4k (+35.1k) | 140k → 149k | 372k → 479k | 155k → 370k | +215.2k | nan / n/a | +6.1k / +8.3k / +1.0k |
| 2026 | +18.9k → +66.2k | +47.3k (+46.5k) | 186k → 182k | 346k → 308k | 114k → 397k | +283.6k | nan / n/a | +10.4k / +37.9k / -1.1k |
| L6M | +61.5k → +75.0k | +13.5k (+20.4k) | 146k → 145k | 372k → 479k | -153k → 140k | +292.8k | nan / n/a | +2.8k / +11.1k / -0.4k |
| HOLD | +48.3k → +59.3k | +11.0k (+18.8k) | 173k → 178k | 651k → 702k | -1095k → -921k | +173.4k | 1.19 / +22.2k | +3.5k / +7.6k / -0.1k |
| PRE | +58.0k → +50.7k | -7.3k (+13.4k) | 139k → 135k | 704k → 620k | -2418k → -2247k | +170.2k | 1.08 / -3.5k | -2.4k / -4.2k / -0.7k |
| X' | +16.0k → +16.2k | +0.1k (+14.7k) | 104k → 103k | 490k → 465k | -1457k → -1468k | -11.1k | 0.99 / -0.0k | -1.1k / +2.4k / -1.2k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -26.5k → -21.1k | +5.4k (+34.0k) | 135k → 148k | 608k → 680k | -371k → -296k | +75.1k | 1.25 / -0.0k | +7.8k / -2.9k / +0.4k |
| 2026 | -18.7k → +19.0k | +37.7k (+50.4k) | 185k → 192k | 457k → 352k | -112k → 114k | +226.2k | nan / n/a | +13.7k / +24.0k / -0.0k |
| L6M | +18.8k → +25.3k | +6.5k (+20.7k) | 135k → 140k | 608k → 680k | -882k → -766k | +115.9k | 1.15 / +10.3k | +1.8k / +4.2k / +0.5k |
| HOLD | +8.6k → +11.8k | +3.2k (+19.3k) | 163k → 170k | 696k → 760k | -1777k → -1751k | +26.4k | 1.02 / +3.4k | +2.3k / +0.7k / +0.2k |
| PRE | +27.7k → +19.8k | -7.9k (+11.2k) | 130k → 132k | 746k → 774k | -2817k → -2890k | -72.6k | 0.97 / -8.4k | -1.5k / -6.4k / +0.0k |
| X' | +5.2k → +5.8k | +0.6k (+15.1k) | 102k → 103k | 567k → 521k | -1653k → -1678k | -25.3k | 0.98 / +0.5k | -0.6k / +2.6k / -1.4k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -1.0k → +16.4k | +17.4k (+32.8k) | 141k → 155k | 417k → 552k | -14k → 230k | +243.9k | nan / n/a | +9.8k / +8.5k / -0.9k |
| 2026 | +11.5k → +61.4k | +49.9k (+35.9k) | 187k → 185k | 371k → 291k | 69k → 368k | +299.4k | nan / n/a | +12.7k / +38.7k / -1.5k |
| L6M | +50.0k → +66.2k | +16.2k (+20.2k) | 145k → 148k | 417k → 552k | -372k → -51k | +320.9k | 7.34 / +435.6k | +5.7k / +11.2k / -0.7k |
| HOLD | +37.2k → +51.8k | +14.6k (+18.2k) | 173k → 179k | 684k → 698k | -1321k → -1078k | +243.3k | 1.23 / +26.3k | +6.4k / +8.6k / -0.4k |
| PRE | +46.1k → +41.2k | -4.9k (+12.6k) | 137k → 132k | 778k → 659k | -2620k → -2381k | +238.8k | 1.10 / -0.8k | -1.1k / -3.5k / -0.3k |
| X' | +7.0k → +5.6k | -1.4k (+14.1k) | 104k → 102k | 560k → 572k | -1661k → -1678k | -16.6k | 0.99 / -1.4k | +0.3k / -0.6k / -1.1k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 648 | +4.65 | +1.70 (MDE 3.00) | +7.8k |
| HM | 538 | +3.27 | +1.88 (MDE 2.89) | +7.2k |
| WT | 874 | +1.80 | -0.11 (MDE 0.22) | -0.5k |
| KB | 649 | +3.73 | -0.89 (MDE 2.42) | -2.1k |
| SM | 279 | +2.00 | +0.76 (MDE 3.27) | +1.1k |
| PE | 612 | +3.11 | -0.02 (MDE 2.54) | -0.0k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1618 | +4.25 | -0.73 (MDE 1.62) | -3.2k |
| HM | 1532 | +2.45 | -0.22 (MDE 1.54) | -0.9k |
| WT | 2386 | +0.73 | +0.13 (MDE 0.18) | +0.6k |
| KB | 1678 | +4.96 | -0.76 (MDE 1.78) | -1.8k |
| SM | 822 | +4.43 | -0.21 (MDE 1.14) | -0.3k |
| PE | 1621 | +3.17 | -0.73 (MDE 1.84) | -1.8k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1579 | +0.12 |
| london | 804 | +0.20 |
| pre | 165 | -1.21 |
| nyam | 744 | +1.24 |
| nypm | 305 | +1.81 |
| close | 3 | +3.50 |

#### cut|trig=firstBookStopped|act=cutRest100 - MKT - tier CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +11.0k → +37.6k | +26.5k (+69.2k) | 140k → 144k | 372k → 515k | 155k → 526k | +371.6k | nan / n/a | +17.0k / +12.6k / -3.1k |
| 2026 | +18.9k → +89.0k | +70.1k (+104.2k) | 186k → 143k | 346k → 243k | 114k → 534k | +420.4k | nan / n/a | +29.3k / +43.6k / -2.9k |
| L6M | +61.5k → +71.9k | +10.4k (+44.2k) | 146k → 127k | 372k → 515k | -153k → 192k | +345.4k | nan / n/a | +2.9k / +11.8k / -4.3k |
| HOLD | +48.3k → +56.2k | +7.9k (+39.5k) | 173k → 163k | 651k → 713k | -1095k → -892k | +203.0k | 1.23 / +20.7k | +4.4k / +7.8k / -4.2k |
| PRE | +58.0k → +46.4k | -11.6k (+22.0k) | 139k → 126k | 704k → 522k | -2418k → -2125k | +293.0k | 1.14 / -5.2k | -7.4k / -0.8k / -3.5k |
| X' | +16.0k → +17.9k | +1.8k (+27.4k) | 104k → 114k | 490k → 489k | -1457k → -1465k | -7.7k | 0.99 / +1.7k | -0.1k / +3.2k / -1.2k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -26.5k → -22.7k | +3.8k (+63.7k) | 135k → 130k | 608k → 721k | -371k → -318k | +52.5k | 1.17 / -0.0k | +12.5k / -4.7k / -4.0k |
| 2026 | -18.7k → +32.7k | +51.4k (+98.1k) | 185k → 134k | 457k → 324k | -112k → 196k | +308.6k | nan / n/a | +33.2k / +18.1k / +0.1k |
| L6M | +18.8k → +14.9k | -3.9k (+42.6k) | 135k → 114k | 608k → 721k | -882k → -788k | +93.5k | 1.12 / -2.1k | -0.2k / +4.5k / -8.3k |
| HOLD | +8.6k → +2.7k | -5.9k (+38.0k) | 163k → 147k | 696k → 753k | -1777k → -1744k | +33.7k | 1.02 / -5.9k | +1.7k / +1.2k / -8.8k |
| PRE | +27.7k → +16.7k | -11.0k (+20.6k) | 130k → 128k | 746k → 713k | -2817k → -2792k | +25.3k | 1.01 / -10.9k | -4.0k / -4.9k / -2.1k |
| X' | +5.2k → +8.1k | +2.9k (+27.6k) | 102k → 113k | 567k → 578k | -1653k → -1659k | -6.4k | 1.00 / +2.9k | +1.0k / +3.3k / -1.3k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -1.0k → +29.1k | +30.1k (+66.5k) | 141k → 145k | 417k → 546k | -14k → 407k | +421.7k | nan / n/a | +23.7k / +6.9k / -0.5k |
| 2026 | +11.5k → +78.6k | +67.2k (+101.4k) | 187k → 144k | 371k → 250k | 69k → 472k | +402.9k | nan / n/a | +33.0k / +37.6k / -3.5k |
| L6M | +50.0k → +63.5k | +13.5k (+44.1k) | 145k → 129k | 417k → 546k | -372k → 8k | +379.2k | nan / n/a | +10.1k / +8.2k / -4.8k |
| HOLD | +37.2k → +48.5k | +11.3k (+39.2k) | 173k → 164k | 684k → 721k | -1321k → -1074k | +247.2k | 1.23 / +22.5k | +11.2k / +4.6k / -4.5k |
| PRE | +46.1k → +38.2k | -7.9k (+22.4k) | 137k → 126k | 778k → 629k | -2620k → -2287k | +333.2k | 1.15 / -2.4k | -2.7k / -2.8k / -2.5k |
| X' | +7.0k → +13.7k | +6.7k (+27.9k) | 104k → 115k | 560k → 517k | -1661k → -1577k | +83.9k | 1.05 / +7.4k | +4.7k / +2.4k / -0.4k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 648 | +4.65 | +0.91 (MDE 4.63) | +4.2k |
| HM | 538 | +3.27 | +2.70 (MDE 4.36) | +10.4k |
| WT | 874 | +1.80 | -0.24 (MDE 0.39) | -1.1k |
| KB | 649 | +3.73 | -2.80 (MDE 3.93) | -6.8k |
| SM | 279 | +2.00 | +1.04 (MDE 5.24) | +1.5k |
| PE | 612 | +3.11 | +0.84 (MDE 3.75) | +2.1k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1618 | +4.25 | -1.63 (MDE 2.50) | -7.0k |
| HM | 1532 | +2.45 | +0.35 (MDE 2.50) | +1.4k |
| WT | 2386 | +0.73 | +0.22 (MDE 0.40) | +1.0k |
| KB | 1678 | +4.96 | -1.21 (MDE 2.64) | -2.8k |
| SM | 822 | +4.43 | -1.33 (MDE 2.60) | -2.2k |
| PE | 1621 | +3.17 | -0.84 (MDE 2.67) | -2.0k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1579 | +0.28 |
| london | 804 | -0.32 |
| pre | 165 | -3.59 |
| nyam | 744 | +1.06 |
| nypm | 305 | +1.41 |
| close | 3 | +3.50 |

#### cut|trig=firstBookStopped|act=cutRest50 - S73 - tier CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +31.3k → +47.3k | +16.0k (+35.1k) | 130k → 142k | 319k → 367k | 438k → 662k | +224.0k | nan / n/a | +10.5k / +1.7k / +3.7k |
| 2026 | +37.0k → +86.2k | +49.2k (+34.7k) | 185k → 191k | 306k → 274k | 222k → 517k | +294.9k | nan / n/a | +18.5k / +19.8k / +10.8k |
| L6M | +79.1k → +85.7k | +6.6k (+26.8k) | 137k → 133k | 319k → 367k | 332k → 462k | +130.1k | nan / n/a | +0.2k / +4.4k / +2.0k |
| HOLD | +66.7k → +71.3k | +4.6k (+24.0k) | 169k → 170k | 625k → 667k | -630k → -629k | +1.1k | 1.00 / +4.7k | +0.1k / +2.8k / +1.7k |
| PRE | +61.8k → +55.4k | -6.5k (+16.0k) | 139k → 135k | 615k → 586k | -2305k → -2136k | +168.6k | 1.08 / -2.1k | -5.7k / +0.6k / -1.4k |
| X' | +18.2k → +17.8k | -0.4k (+17.6k) | 102k → 103k | 469k → 421k | -1392k → -1423k | -31.4k | 0.98 / -0.8k | -2.7k / +3.8k / -1.5k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -17.2k → -15.3k | +1.9k (+24.2k) | 136k → 135k | 537k → 622k | -241k → -214k | +26.6k | 1.12 / +0.0k | +12.1k / -11.8k / +1.6k |
| 2026 | +0.8k → +22.5k | +21.7k (+37.7k) | 183k → 176k | 348k → 328k | 5k → 135k | +130.5k | nan / n/a | +18.1k / -0.7k / +4.3k |
| L6M | +32.1k → +36.4k | +4.3k (+22.7k) | 139k → 134k | 537k → 622k | -639k → -510k | +128.3k | 1.25 / +13.5k | +5.2k / -0.7k / -0.1k |
| HOLD | +20.2k → +21.7k | +1.5k (+19.9k) | 165k → 164k | 698k → 730k | -1559k → -1526k | +32.9k | 1.02 / +2.0k | +4.9k / -2.1k / -1.3k |
| PRE | +35.4k → +27.2k | -8.1k (+15.4k) | 137k → 135k | 756k → 766k | -2788k → -2799k | -10.3k | 1.00 / -8.2k | -3.2k / -4.2k / -0.7k |
| X' | +8.0k → +6.7k | -1.3k (+16.7k) | 99k → 100k | 520k → 511k | -1559k → -1605k | -46.3k | 0.97 / -1.4k | -2.4k / +2.6k / -1.4k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +15.1k → +28.8k | +13.7k (+33.1k) | 135k → 146k | 363k → 442k | 211k → 403k | +192.0k | nan / n/a | +13.6k / -5.3k / +5.4k |
| 2026 | +26.0k → +65.5k | +39.5k (+34.8k) | 192k → 193k | 322k → 308k | 156k → 393k | +236.8k | nan / n/a | +22.5k / +5.8k / +11.1k |
| L6M | +65.1k → +71.8k | +6.7k (+23.7k) | 139k → 134k | 363k → 442k | 51k → 195k | +143.6k | nan / n/a | +3.2k / +0.4k / +3.0k |
| HOLD | +53.2k → +58.6k | +5.4k (+21.2k) | 171k → 171k | 658k → 688k | -927k → -855k | +72.5k | 1.08 / +10.4k | +3.1k / -0.3k / +2.6k |
| PRE | +50.0k → +43.2k | -6.8k (+14.4k) | 139k → 132k | 705k → 680k | -2540k → -2309k | +231.3k | 1.10 / -2.5k | -3.7k / -2.6k / -0.6k |
| X' | +9.5k → +9.3k | -0.2k (+17.4k) | 103k → 103k | 525k → 498k | -1599k → -1587k | +12.0k | 1.01 / -0.1k | -0.8k / +1.9k / -1.3k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 660 | +6.25 | +1.24 (MDE 3.01) | +5.8k |
| HM | 541 | +3.73 | +0.52 (MDE 2.44) | +2.0k |
| WT | 897 | +2.64 | -0.35 (MDE 0.45) | -1.6k |
| KB | 637 | +4.03 | -0.82 (MDE 2.81) | -1.9k |
| SM | 282 | +3.96 | +0.10 (MDE 3.10) | +0.1k |
| PE | 587 | +3.36 | +0.91 (MDE 3.52) | +2.1k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1649 | +4.42 | -0.53 (MDE 1.86) | -2.3k |
| HM | 1550 | +2.76 | -0.08 (MDE 1.94) | -0.3k |
| WT | 2373 | +1.06 | +0.01 (MDE 0.36) | +0.0k |
| KB | 1707 | +4.09 | -0.12 (MDE 1.99) | -0.3k |
| SM | 821 | +4.56 | -0.56 (MDE 1.66) | -0.9k |
| PE | 1610 | +3.86 | -1.09 (MDE 1.77) | -2.6k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1585 | +0.25 |
| london | 822 | +0.15 |
| pre | 167 | -0.62 |
| nyam | 732 | +0.30 |
| nypm | 294 | +0.65 |
| close | 4 | +0.00 |

#### cut|trig=firstBookStopped|act=cutRest100 - S73 - tier CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +31.3k → +59.0k | +27.8k (+59.8k) | 130k → 137k | 319k → 393k | 438k → 827k | +388.9k | nan / n/a | +17.0k / +11.0k / -0.3k |
| 2026 | +37.0k → +102.1k | +65.1k (+64.2k) | 185k → 154k | 306k → 272k | 222k → 613k | +390.4k | nan / n/a | +27.3k / +32.5k / +5.3k |
| L6M | +79.1k → +83.6k | +4.6k (+42.2k) | 137k → 116k | 319k → 393k | 332k → 541k | +209.1k | nan / n/a | -1.7k / +10.5k / -4.2k |
| HOLD | +66.7k → +69.8k | +3.1k (+37.7k) | 169k → 156k | 625k → 655k | -630k → -510k | +120.0k | 1.24 / +19.6k | -0.6k / +7.7k / -4.0k |
| PRE | +61.8k → +52.5k | -9.4k (+22.4k) | 139k → 125k | 615k → 584k | -2305k → -1948k | +356.9k | 1.18 / +0.2k | -10.9k / +3.1k / -1.6k |
| X' | +18.2k → +18.5k | +0.3k (+26.6k) | 102k → 110k | 469k → 468k | -1392k → -1392k | -0.2k | 1.00 / +0.3k | -1.4k / +3.7k / -1.9k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -17.2k → -18.5k | -1.4k (+49.0k) | 136k → 116k | 537k → 646k | -241k → -260k | -19.0k | 0.93 / +0.0k | +12.1k / -13.4k / -0.0k |
| 2026 | +0.8k → +32.3k | +31.5k (+80.5k) | 183k → 129k | 348k → 303k | 5k → 194k | +189.2k | nan / n/a | +27.4k / -1.4k / +5.5k |
| L6M | +32.1k → +26.2k | -5.9k (+35.7k) | 139k → 114k | 537k → 646k | -639k → -556k | +82.6k | 1.15 / -2.1k | +2.1k / -2.5k / -5.6k |
| HOLD | +20.2k → +14.1k | -6.1k (+32.0k) | 165k → 148k | 698k → 717k | -1559k → -1497k | +62.0k | 1.04 / -5.5k | +3.6k / -3.5k / -6.2k |
| PRE | +35.4k → +26.0k | -9.4k (+22.5k) | 137k → 126k | 756k → 697k | -2788k → -2492k | +296.5k | 1.12 / -6.3k | -5.0k / -1.6k / -2.8k |
| X' | +8.0k → +9.3k | +1.3k (+26.0k) | 99k → 107k | 520k → 499k | -1559k → -1557k | +1.7k | 1.00 / +1.4k | -0.3k / +2.4k / -0.7k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +15.1k → +45.2k | +30.1k (+59.4k) | 135k → 139k | 363k → 471k | 211k → 632k | +421.5k | nan / n/a | +22.8k / +5.8k / +1.4k |
| 2026 | +26.0k → +96.5k | +70.5k (+66.2k) | 192k → 155k | 322k → 283k | 156k → 579k | +422.8k | nan / n/a | +35.1k / +31.0k / +4.3k |
| L6M | +65.1k → +73.5k | +8.3k (+41.1k) | 139k → 119k | 363k → 471k | 51k → 327k | +276.3k | nan / n/a | +3.3k / +7.9k / -2.9k |
| HOLD | +53.2k → +60.9k | +7.7k (+37.0k) | 171k → 157k | 658k → 662k | -927k → -718k | +209.2k | 1.29 / +25.4k | +4.6k / +5.9k / -2.8k |
| PRE | +50.0k → +43.8k | -6.2k (+22.7k) | 139k → 121k | 705k → 672k | -2540k → -2079k | +461.4k | 1.22 / +3.5k | -6.4k / +1.7k / -1.5k |
| X' | +9.5k → +15.3k | +5.8k (+26.9k) | 103k → 112k | 525k → 493k | -1599k → -1486k | +112.9k | 1.08 / +7.0k | +4.1k / +3.2k / -1.4k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 660 | +6.25 | +0.85 (MDE 4.62) | +4.0k |
| HM | 541 | +3.73 | +2.18 (MDE 3.57) | +8.4k |
| WT | 897 | +2.64 | -0.46 (MDE 0.67) | -2.1k |
| KB | 637 | +4.03 | -2.62 (MDE 3.61) | -6.2k |
| SM | 282 | +3.96 | -0.83 (MDE 4.31) | -1.2k |
| PE | 587 | +3.36 | +0.71 (MDE 4.83) | +1.7k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1649 | +4.42 | -1.39 (MDE 2.72) | -6.1k |
| HM | 1550 | +2.76 | +0.44 (MDE 2.52) | +1.8k |
| WT | 2373 | +1.06 | +0.14 (MDE 0.48) | +0.6k |
| KB | 1707 | +4.09 | -0.29 (MDE 2.50) | -0.7k |
| SM | 821 | +4.56 | -1.60 (MDE 2.72) | -2.6k |
| PE | 1610 | +3.86 | -1.01 (MDE 2.68) | -2.4k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1585 | -0.06 |
| london | 822 | -1.10 |
| pre | 167 | -1.41 |
| nyam | 732 | +0.72 |
| nypm | 294 | +2.08 |
| close | 4 | -15.32 |

#### cap|lots=19|mode=skip|session=pre - MKT - tier LEAD (>=0 on N in L6M, HOLD, PRE and X'; placebo/RC gates not passed)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +11.0k → +15.6k | +4.5k (+18.2k) | 140k → 143k | 372k → 379k | 155k → 218k | +63.3k | nan / n/a | -0.9k / +0.5k / +4.9k |
| 2026 | +18.9k → +16.5k | -2.4k (+8.3k) | 186k → 180k | 346k → 344k | 114k → 99k | -14.6k | nan / n/a | -1.9k / -3.8k / +3.2k |
| L6M | +61.5k → +64.0k | +2.6k (+13.3k) | 146k → 144k | 372k → 379k | -153k → -99k | +53.5k | 1.54 / +37.0k | -0.7k / -1.5k / +4.8k |
| HOLD | +48.3k → +52.2k | +3.9k (+11.9k) | 173k → 171k | 651k → 620k | -1095k → -1028k | +66.1k | 1.06 / +7.2k | -0.6k / -1.5k / +6.0k |
| PRE | +58.0k → +59.6k | +1.6k (+7.3k) | 139k → 135k | 704k → 514k | -2418k → -2223k | +194.3k | 1.09 / +6.8k | +0.4k / +0.6k / +0.6k |
| X' | +16.0k → +19.2k | +3.1k (+10.5k) | 104k → 97k | 490k → 473k | -1457k → -1245k | +211.9k | 1.17 / +6.4k | -0.4k / -0.1k / +3.6k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -26.5k → -24.2k | +2.3k (+13.5k) | 135k → 133k | 608k → 572k | -371k → -338k | +32.3k | 1.10 / +0.0k | -0.6k / -2.5k / +5.4k |
| 2026 | -18.7k → -22.8k | -4.1k (+10.6k) | 185k → 177k | 457k → 464k | -112k → -137k | -24.6k | 0.82 / +0.0k | -0.8k / -5.3k / +1.9k |
| L6M | +18.8k → +19.8k | +1.0k (+10.0k) | 135k → 132k | 608k → 572k | -882k → -823k | +58.9k | 1.07 / +2.4k | -0.4k / -2.9k / +4.2k |
| HOLD | +8.6k → +10.8k | +2.2k (+8.9k) | 163k → 160k | 696k → 664k | -1777k → -1694k | +83.5k | 1.05 / +2.7k | -0.3k / -3.2k / +5.7k |
| PRE | +27.7k → +30.6k | +2.9k (+6.7k) | 130k → 127k | 746k → 555k | -2817k → -2600k | +217.1k | 1.08 / +5.4k | +0.9k / +0.9k / +1.0k |
| X' | +5.2k → +7.0k | +1.8k (+10.6k) | 102k → 94k | 567k → 566k | -1653k → -1467k | +185.7k | 1.13 / +2.7k | -0.7k / -0.7k / +3.3k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -1.0k → +3.7k | +4.7k (+18.5k) | 141k → 142k | 417k → 424k | -14k → 51k | +65.8k | nan / n/a | -1.4k / +0.5k / +5.6k |
| 2026 | +11.5k → +9.2k | -2.3k (+9.6k) | 187k → 179k | 371k → 368k | 69k → 55k | -13.6k | nan / n/a | -3.1k / -3.7k / +4.5k |
| L6M | +50.0k → +52.7k | +2.7k (+13.6k) | 145k → 141k | 417k → 424k | -372k → -296k | +76.0k | 1.26 / +16.2k | -1.0k / -1.6k / +5.3k |
| HOLD | +37.2k → +40.9k | +3.7k (+12.1k) | 173k → 169k | 684k → 652k | -1321k → -1235k | +85.8k | 1.07 / +6.6k | -0.8k / -1.9k / +6.5k |
| PRE | +46.1k → +48.6k | +2.4k (+6.8k) | 137k → 134k | 778k → 588k | -2620k → -2422k | +197.7k | 1.08 / +6.4k | +0.3k / +0.6k / +1.5k |
| X' | +7.0k → +10.3k | +3.2k (+10.6k) | 104k → 97k | 560k → 541k | -1661k → -1429k | +232.1k | 1.16 / +4.9k | -0.8k / +0.1k / +3.9k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 648 | +4.65 | +0.41 (MDE 1.89) | +1.9k |
| HM | 538 | +3.27 | -0.11 (MDE 1.22) | -0.4k |
| WT | 874 | +1.80 | +0.02 (MDE 0.79) | +0.1k |
| KB | 649 | +3.73 | +0.26 (MDE 1.29) | +0.6k |
| SM | 279 | +2.00 | +0.43 (MDE 1.21) | +0.6k |
| PE | 612 | +3.11 | -0.12 (MDE 0.95) | -0.3k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1618 | +4.25 | +0.14 (MDE 0.85) | +0.6k |
| HM | 1532 | +2.45 | +0.34 (MDE 0.84) | +1.4k |
| WT | 2386 | +0.73 | -0.10 (MDE 0.50) | -0.5k |
| KB | 1678 | +4.96 | +0.13 (MDE 1.01) | +0.3k |
| SM | 822 | +4.43 | -0.24 (MDE 0.73) | -0.4k |
| PE | 1621 | +3.17 | +0.05 (MDE 0.66) | +0.1k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1579 | +0.00 |
| london | 804 | +0.00 |
| pre | 165 | +5.43 |
| nyam | 744 | -0.96 |
| nypm | 305 | +0.87 |
| close | 3 | +0.00 |

#### cap|lots=19|mode=skip|session=pre - S73 - tier LEAD (>=0 on N in L6M, HOLD, PRE and X'; placebo/RC gates not passed)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +31.3k → +32.6k | +1.3k (+19.9k) | 130k → 129k | 319k → 307k | 438k → 456k | +18.4k | nan / n/a | -1.3k / -0.2k / +2.7k |
| 2026 | +37.0k → +30.6k | -6.5k (+19.3k) | 185k → 171k | 306k → 307k | 222k → 183k | -38.8k | nan / n/a | -3.3k / -3.3k / +0.1k |
| L6M | +79.1k → +81.5k | +2.5k (+12.3k) | 137k → 132k | 319k → 307k | 332k → 418k | +85.6k | nan / n/a | -0.1k / -0.3k / +2.9k |
| HOLD | +66.7k → +69.4k | +2.7k (+11.1k) | 169k → 164k | 625k → 593k | -630k → -534k | +95.8k | 1.18 / +15.2k | -0.1k / -0.9k / +3.7k |
| PRE | +61.8k → +64.9k | +3.1k (+6.4k) | 139k → 136k | 615k → 472k | -2305k → -2111k | +193.5k | 1.09 / +9.0k | -0.0k / +2.5k / +0.6k |
| X' | +18.2k → +19.5k | +1.3k (+8.8k) | 102k → 96k | 469k → 429k | -1392k → -1226k | +166.3k | 1.14 / +3.9k | -0.5k / -0.1k / +1.8k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -17.2k → -13.7k | +3.5k (+16.7k) | 136k → 134k | 537k → 498k | -241k → -192k | +48.5k | 1.25 / +0.0k | -0.2k / +0.6k / +3.1k |
| 2026 | +0.8k → -3.9k | -4.7k (+11.4k) | 183k → 174k | 348k → 357k | 5k → -23k | -28.0k | -0.20 / +0.0k | -0.6k / -3.2k / -0.9k |
| L6M | +32.1k → +33.0k | +0.9k (+11.2k) | 139k → 132k | 537k → 498k | -639k → -514k | +125.1k | 1.24 / +8.9k | -0.3k / -0.5k / +1.6k |
| HOLD | +20.2k → +21.6k | +1.4k (+10.2k) | 165k → 158k | 698k → 666k | -1559k → -1401k | +158.0k | 1.11 / +3.9k | -0.2k / -1.4k / +3.0k |
| PRE | +35.4k → +39.3k | +4.0k (+6.8k) | 137k → 133k | 756k → 557k | -2788k → -2585k | +202.7k | 1.08 / +7.1k | -0.1k / +2.6k / +1.4k |
| X' | +8.0k → +9.5k | +1.5k (+8.5k) | 99k → 94k | 520k → 480k | -1559k → -1391k | +167.7k | 1.12 / +2.6k | -0.6k / -0.1k / +2.2k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +15.1k → +17.9k | +2.9k (+19.7k) | 135k → 134k | 363k → 370k | 211k → 251k | +40.3k | nan / n/a | -1.2k / +0.4k / +3.6k |
| 2026 | +26.0k → +19.7k | -6.3k (+18.8k) | 192k → 178k | 322k → 323k | 156k → 118k | -37.9k | nan / n/a | -3.2k / -3.4k / +0.3k |
| L6M | +65.1k → +67.8k | +2.7k (+12.4k) | 139k → 133k | 363k → 370k | 51k → 153k | +102.1k | nan / n/a | -0.3k / -0.4k / +3.4k |
| HOLD | +53.2k → +56.2k | +3.0k (+11.2k) | 171k → 165k | 658k → 625k | -927k → -810k | +117.6k | 1.15 / +11.1k | -0.2k / -1.0k / +4.2k |
| PRE | +50.0k → +53.1k | +3.1k (+6.5k) | 139k → 136k | 705k → 535k | -2540k → -2334k | +206.2k | 1.09 / +7.8k | -0.2k / +2.5k / +0.8k |
| X' | +9.5k → +10.6k | +1.1k (+8.9k) | 103k → 98k | 525k → 484k | -1599k → -1424k | +174.4k | 1.12 / +2.4k | -0.6k / -0.2k / +1.9k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 660 | +6.25 | +0.31 (MDE 0.95) | +1.5k |
| HM | 541 | +3.73 | +0.04 (MDE 1.08) | +0.2k |
| WT | 897 | +2.64 | +0.08 (MDE 0.93) | +0.4k |
| KB | 637 | +4.03 | -0.03 (MDE 1.18) | -0.1k |
| SM | 282 | +3.96 | +0.65 (MDE 1.34) | +1.0k |
| PE | 587 | +3.36 | -0.19 (MDE 1.72) | -0.4k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1649 | +4.42 | +0.44 (MDE 0.77) | +1.9k |
| HM | 1550 | +2.76 | +0.12 (MDE 0.80) | +0.5k |
| WT | 2373 | +1.06 | -0.12 (MDE 0.50) | -0.5k |
| KB | 1707 | +4.09 | +0.47 (MDE 0.80) | +1.1k |
| SM | 821 | +4.56 | -0.27 (MDE 0.74) | -0.4k |
| PE | 1610 | +3.86 | +0.21 (MDE 0.49) | +0.5k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1585 | +0.00 |
| london | 822 | +0.00 |
| pre | 167 | +2.61 |
| nyam | 732 | -0.73 |
| nypm | 294 | +1.54 |
| close | 4 | +0.00 |

#### confluence|cfUp2_3m|partial|trig=R2|P=33 - MKT - tier CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +11.0k → +43.7k | +32.7k (+57.5k) | 140k → 127k | 372k → 461k | 155k → 612k | +457.7k | nan / n/a | -1.5k / +29.6k / +4.7k |
| 2026 | +18.9k → +65.9k | +47.0k (+105.9k) | 186k → 126k | 346k → 189k | 114k → 396k | +281.9k | nan / n/a | -2.4k / +54.1k / -4.6k |
| L6M | +61.5k → +79.3k | +17.8k (+39.3k) | 146k → 134k | 372k → 461k | -153k → 353k | +506.2k | nan / n/a | -2.7k / +19.9k / +0.6k |
| HOLD | +48.3k → +62.5k | +14.2k (+35.2k) | 173k → 165k | 651k → 656k | -1095k → -694k | +401.0k | 1.58 / +50.4k | -4.0k / +17.9k / +0.4k |
| PRE | +58.0k → +43.2k | -14.8k (+18.9k) | 139k → 137k | 704k → 466k | -2418k → -2512k | -94.2k | 0.96 / -16.4k | -4.2k / -4.1k / -6.5k |
| X' | +16.0k → +13.1k | -3.0k (+24.3k) | 104k → 88k | 490k → 388k | -1457k → -1339k | +117.9k | 1.09 / -1.8k | -4.9k / +1.0k / +0.8k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -26.5k → -7.9k | +18.6k (+70.1k) | 135k → 111k | 608k → 570k | -371k → -110k | +260.8k | 3.37 / -0.0k | +7.1k / +8.3k / +3.3k |
| 2026 | -18.7k → +11.4k | +30.2k (+138.9k) | 185k → 103k | 457k → 224k | -112k → 68k | +181.0k | nan / n/a | +0.9k / +36.4k / -7.1k |
| L6M | +18.8k → +35.6k | +16.8k (+42.0k) | 135k → 122k | 608k → 570k | -882k → -362k | +519.9k | 2.44 / +67.9k | +7.2k / +8.4k / +1.2k |
| HOLD | +8.6k → +20.9k | +12.4k (+37.5k) | 163k → 153k | 696k → 701k | -1777k → -1358k | +418.8k | 1.31 / +18.8k | +5.6k / +5.8k / +1.0k |
| PRE | +27.7k → +21.4k | -6.3k (+18.3k) | 130k → 134k | 746k → 552k | -2817k → -2868k | -51.0k | 0.98 / -6.7k | +0.7k / -5.8k / -1.2k |
| X' | +5.2k → +4.7k | -0.5k (+24.2k) | 102k → 85k | 567k → 459k | -1653k → -1466k | +187.4k | 1.13 / +0.1k | -3.8k / +1.2k / +2.2k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -1.0k → +29.1k | +30.2k (+54.0k) | 141k → 125k | 417k → 474k | -14k → 408k | +422.3k | nan / n/a | -0.9k / +23.6k / +7.4k |
| 2026 | +11.5k → +41.9k | +30.4k (+103.8k) | 187k → 127k | 371k → 221k | 69k → 251k | +182.4k | nan / n/a | -2.4k / +38.5k / -5.6k |
| L6M | +50.0k → +65.2k | +15.2k (+36.5k) | 145k → 133k | 417k → 474k | -372k → 96k | +467.4k | nan / n/a | -0.4k / +14.3k / +1.3k |
| HOLD | +37.2k → +48.9k | +11.7k (+33.0k) | 173k → 163k | 684k → 670k | -1321k → -919k | +402.2k | 1.44 / +33.2k | -2.3k / +13.4k / +0.6k |
| PRE | +46.1k → +30.0k | -16.2k (+17.7k) | 137k → 135k | 778k → 604k | -2620k → -2770k | -150.4k | 0.95 / -17.8k | -4.3k / -7.1k / -4.8k |
| X' | +7.0k → +4.5k | -2.5k (+24.1k) | 104k → 89k | 560k → 418k | -1661k → -1536k | +125.0k | 1.08 / -2.1k | -4.9k / +0.8k / +1.6k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 648 | +4.65 | +0.40 (MDE 3.32) | +1.8k |
| HM | 538 | +3.27 | +3.04 (MDE 5.32) | +11.7k |
| WT | 874 | +1.80 | +1.41 (MDE 2.13) | +6.2k |
| KB | 649 | +3.73 | -0.70 (MDE 3.68) | -1.7k |
| SM | 279 | +2.00 | +2.79 (MDE 6.03) | +4.1k |
| PE | 612 | +3.11 | -1.75 (MDE 5.27) | -4.3k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1618 | +4.25 | -2.35 (MDE 2.46) | -10.1k |
| HM | 1532 | +2.45 | +0.08 (MDE 2.35) | +0.3k |
| WT | 2386 | +0.73 | -0.40 (MDE 1.38) | -1.8k |
| KB | 1678 | +4.96 | -1.09 (MDE 2.44) | -2.5k |
| SM | 822 | +4.43 | -0.37 (MDE 2.85) | -0.6k |
| PE | 1621 | +3.17 | -0.04 (MDE 2.63) | -0.1k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1579 | -0.00 |
| london | 804 | -0.69 |
| pre | 165 | -0.83 |
| nyam | 744 | +3.41 |
| nypm | 305 | +1.70 |
| close | 3 | +6.03 |

#### confluence|cfUp1.5_3m|alone - MKT - tier CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +11.0k → +40.5k | +29.4k (+32.6k) | 140k → 136k | 372k → 353k | 155k → 566k | +411.7k | nan / n/a | +8.4k / +20.2k / +0.7k |
| 2026 | +18.9k → +40.1k | +21.2k (+43.9k) | 186k → 176k | 346k → 276k | 114k → 241k | +127.0k | nan / n/a | +2.9k / +20.3k / -2.0k |
| L6M | +61.5k → +74.9k | +13.4k (+26.2k) | 146k → 137k | 372k → 353k | -153k → 261k | +413.7k | nan / n/a | +8.1k / +10.3k / -4.9k |
| HOLD | +48.3k → +59.6k | +11.3k (+23.2k) | 173k → 169k | 651k → 669k | -1095k → -750k | +344.7k | 1.46 / +38.7k | +6.1k / +9.4k / -4.2k |
| PRE | +58.0k → +58.5k | +0.5k (+14.2k) | 139k → 138k | 704k → 594k | -2418k → -2232k | +185.4k | 1.08 / +5.3k | +4.9k / +0.2k / -4.6k |
| X' | +16.0k → +16.0k | -0.1k (+14.0k) | 104k → 110k | 490k → 545k | -1457k → -1636k | -179.2k | 0.89 / -1.8k | -0.3k / +0.6k / -0.4k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -26.5k → -5.7k | +20.8k (+35.4k) | 135k → 133k | 608k → 457k | -371k → -80k | +291.0k | 4.65 / -0.0k | +2.7k / +11.5k / +6.6k |
| 2026 | -18.7k → -1.8k | +17.0k (+55.8k) | 185k → 171k | 457k → 405k | -112k → -11k | +101.7k | 10.47 / +0.0k | -0.3k / +13.5k / +3.7k |
| L6M | +18.8k → +34.3k | +15.5k (+22.7k) | 135k → 136k | 608k → 457k | -882k → -562k | +319.8k | 1.57 / +35.0k | +7.3k / +5.8k / +2.3k |
| HOLD | +8.6k → +20.7k | +12.1k (+20.5k) | 163k → 167k | 696k → 745k | -1777k → -1565k | +212.0k | 1.14 / +14.9k | +4.8k / +5.3k / +2.0k |
| PRE | +27.7k → +31.2k | +3.5k (+13.0k) | 130k → 138k | 746k → 701k | -2817k → -2821k | -4.2k | 1.00 / +3.5k | +4.5k / +0.7k / -1.7k |
| X' | +5.2k → +3.8k | -1.4k (+15.2k) | 102k → 109k | 567k → 716k | -1653k → -1825k | -171.5k | 0.91 / -1.7k | -2.5k / -1.2k / +2.3k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -1.0k → +28.5k | +29.5k (+34.0k) | 141k → 137k | 417k → 384k | -14k → 399k | +413.4k | nan / n/a | +8.8k / +17.4k / +3.3k |
| 2026 | +11.5k → +30.4k | +19.0k (+45.8k) | 187k → 177k | 371k → 289k | 69k → 183k | +113.8k | nan / n/a | +1.7k / +20.1k / -2.8k |
| L6M | +50.0k → +63.2k | +13.2k (+25.8k) | 145k → 135k | 417k → 384k | -372k → 59k | +430.8k | nan / n/a | +8.7k / +8.3k / -3.8k |
| HOLD | +37.2k → +49.1k | +11.9k (+23.2k) | 173k → 171k | 684k → 703k | -1321k → -963k | +357.8k | 1.37 / +30.1k | +6.4k / +8.8k / -3.4k |
| PRE | +46.1k → +47.1k | +1.0k (+13.5k) | 137k → 139k | 778k → 700k | -2620k → -2508k | +111.5k | 1.04 / +3.1k | +5.4k / -1.3k / -3.1k |
| X' | +7.0k → +5.3k | -1.7k (+14.9k) | 104k → 110k | 560k → 696k | -1661k → -1842k | -180.9k | 0.90 / -2.3k | -1.4k / -0.1k / -0.3k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 648 | +4.65 | -0.17 (MDE 2.42) | -0.8k |
| HM | 538 | +3.27 | +2.33 (MDE 4.39) | +8.9k |
| WT | 874 | +1.80 | +1.03 (MDE 2.10) | +4.5k |
| KB | 649 | +3.73 | -0.92 (MDE 3.19) | -2.2k |
| SM | 279 | +2.00 | +2.77 (MDE 4.48) | +4.1k |
| PE | 612 | +3.11 | -0.43 (MDE 3.31) | -1.1k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1618 | +4.25 | -0.52 (MDE 1.69) | -2.2k |
| HM | 1532 | +2.45 | +0.52 (MDE 1.86) | +2.1k |
| WT | 2386 | +0.73 | +0.14 (MDE 1.05) | +0.6k |
| KB | 1678 | +4.96 | -0.24 (MDE 1.81) | -0.6k |
| SM | 822 | +4.43 | +0.50 (MDE 1.99) | +0.8k |
| PE | 1621 | +3.17 | -0.12 (MDE 2.28) | -0.3k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1579 | +0.76 |
| london | 804 | +1.34 |
| pre | 165 | -3.28 |
| nyam | 744 | +1.13 |
| nypm | 305 | -2.10 |
| close | 3 | +5.00 |

#### confluence|cfUp2_3m|partial|trig=R2|P=33 - S73 - tier BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +31.3k → +38.4k | +7.2k (+44.6k) | 130k → 127k | 319k → 463k | 438k → 538k | +100.6k | nan / n/a | +3.4k / +13.8k / -10.0k |
| 2026 | +37.0k → +62.3k | +25.3k (+63.4k) | 185k → 145k | 306k → 199k | 222k → 374k | +151.8k | nan / n/a | -0.5k / +36.0k / -10.2k |
| L6M | +79.1k → +77.1k | -1.9k (+37.6k) | 137k → 130k | 319k → 463k | 332k → 320k | -12.8k | nan / n/a | -7.2k / +13.1k / -7.8k |
| HOLD | +66.7k → +61.1k | -5.6k (+33.9k) | 169k → 160k | 625k → 639k | -630k → -687k | -56.5k | 0.92 / -10.6k | -9.8k / +11.2k / -7.0k |
| PRE | +61.8k → +50.1k | -11.7k (+21.5k) | 139k → 136k | 615k → 490k | -2305k → -2367k | -62.6k | 0.97 / -13.1k | -3.5k / +3.1k / -11.3k |
| X' | +18.2k → +10.7k | -7.5k (+21.3k) | 102k → 90k | 469k → 496k | -1392k → -1372k | +19.7k | 1.01 / -7.4k | -9.8k / +0.6k / +1.6k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -17.2k → -4.6k | +12.6k (+52.2k) | 136k → 113k | 537k → 516k | -241k → -64k | +176.5k | 3.75 / -0.0k | +11.2k / +2.1k / -0.7k |
| 2026 | +0.8k → +18.3k | +17.5k (+92.5k) | 183k → 135k | 348k → 263k | 5k → 110k | +105.1k | nan / n/a | -2.3k / +30.7k / -10.8k |
| L6M | +32.1k → +42.0k | +9.9k (+33.8k) | 139k → 130k | 537k → 516k | -639k → -347k | +291.4k | 1.84 / +45.1k | +7.8k / +3.7k / -1.7k |
| HOLD | +20.2k → +27.6k | +7.4k (+30.3k) | 165k → 155k | 698k → 663k | -1559k → -1284k | +274.6k | 1.21 / +13.3k | +6.0k / +2.7k / -1.2k |
| PRE | +35.4k → +27.5k | -7.8k (+21.2k) | 137k → 133k | 756k → 565k | -2788k → -2798k | -9.7k | 1.00 / -7.9k | -0.2k / -4.1k / -3.5k |
| X' | +8.0k → +1.7k | -6.3k (+20.3k) | 99k → 90k | 520k → 538k | -1559k → -1565k | -6.1k | 1.00 / -6.3k | -7.1k / -0.5k / +1.4k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +15.1k → +20.8k | +5.8k (+46.0k) | 135k → 121k | 363k → 482k | 211k → 292k | +81.1k | nan / n/a | +4.5k / +6.4k / -5.1k |
| 2026 | +26.0k → +42.5k | +16.5k (+74.5k) | 192k → 143k | 322k → 228k | 156k → 255k | +98.9k | nan / n/a | -0.1k / +23.8k / -7.2k |
| L6M | +65.1k → +60.5k | -4.6k (+34.8k) | 139k → 127k | 363k → 482k | 51k → 42k | -8.9k | nan / n/a | -5.6k / +5.7k / -4.7k |
| HOLD | +53.2k → +45.9k | -7.2k (+31.6k) | 171k → 156k | 658k → 644k | -927k → -909k | +18.4k | 1.02 / -6.3k | -8.3k / +5.5k / -4.5k |
| PRE | +50.0k → +36.9k | -13.0k (+20.9k) | 139k → 135k | 705k → 616k | -2540k → -2650k | -110.4k | 0.96 / -14.6k | -2.9k / -0.9k / -9.2k |
| X' | +9.5k → +1.1k | -8.4k (+20.7k) | 103k → 91k | 525k → 542k | -1599k → -1602k | -2.9k | 1.00 / -8.4k | -10.1k / -0.3k / +2.0k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 660 | +6.25 | -2.24 (MDE 4.16) | -10.6k |
| HM | 541 | +3.73 | +2.43 (MDE 4.76) | +9.4k |
| WT | 897 | +2.64 | +1.01 (MDE 1.96) | +4.5k |
| KB | 637 | +4.03 | -2.23 (MDE 3.65) | -5.3k |
| SM | 282 | +3.96 | +2.60 (MDE 4.48) | +3.9k |
| PE | 587 | +3.36 | -1.65 (MDE 5.70) | -3.9k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1649 | +4.42 | -1.86 (MDE 2.68) | -8.2k |
| HM | 1550 | +2.76 | -0.32 (MDE 2.51) | -1.3k |
| WT | 2373 | +1.06 | -0.17 (MDE 1.37) | -0.8k |
| KB | 1707 | +4.09 | -0.25 (MDE 2.46) | -0.6k |
| SM | 821 | +4.56 | -0.64 (MDE 2.88) | -1.0k |
| PE | 1610 | +3.86 | +0.05 (MDE 2.40) | +0.1k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1585 | -0.26 |
| london | 822 | -1.50 |
| pre | 167 | -1.03 |
| nyam | 732 | +0.21 |
| nypm | 294 | +2.52 |
| close | 4 | +1.83 |

#### confluence|cfUp2_3m|alone - S73 - tier CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +31.3k → +39.5k | +8.2k (+33.1k) | 130k → 141k | 319k → 386k | 438k → 553k | +115.3k | nan / n/a | +5.7k / +18.7k / -16.1k |
| 2026 | +37.0k → +42.8k | +5.8k (+40.7k) | 185k → 189k | 306k → 275k | 222k → 257k | +34.7k | nan / n/a | -7.4k / +23.4k / -10.2k |
| L6M | +79.1k → +85.7k | +6.6k (+26.0k) | 137k → 143k | 319k → 386k | 332k → 358k | +25.7k | nan / n/a | +7.2k / +15.8k / -16.3k |
| HOLD | +66.7k → +71.9k | +5.2k (+23.4k) | 169k → 175k | 625k → 644k | -630k → -706k | -75.8k | 0.89 / -2.5k | +3.1k / +15.5k / -13.4k |
| PRE | +61.8k → +63.7k | +1.9k (+21.6k) | 139k → 155k | 615k → 632k | -2305k → -2453k | -148.1k | 0.94 / -2.0k | +5.7k / +4.2k / -8.1k |
| X' | +18.2k → +16.1k | -2.1k (+19.7k) | 102k → 102k | 469k → 559k | -1392k → -1454k | -61.5k | 0.96 / -2.8k | -2.8k / -0.1k / +0.8k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -17.2k → -10.2k | +7.0k (+44.9k) | 136k → 127k | 537k → 538k | -241k → -143k | +97.7k | 1.68 / -0.0k | +1.2k / +10.6k / -4.9k |
| 2026 | +0.8k → +18.9k | +18.1k (+42.0k) | 183k → 177k | 348k → 284k | 5k → 114k | +108.8k | nan / n/a | -2.6k / +24.8k / -4.1k |
| L6M | +32.1k → +35.3k | +3.2k (+28.6k) | 139k → 134k | 537k → 538k | -639k → -602k | +36.2k | 1.06 / +5.3k | +4.1k / +6.8k / -7.7k |
| HOLD | +20.2k → +22.0k | +1.9k (+25.5k) | 165k → 163k | 698k → 730k | -1559k → -1587k | -28.6k | 0.98 / +1.5k | +1.4k / +6.4k / -5.9k |
| PRE | +35.4k → +38.1k | +2.8k (+22.1k) | 137k → 150k | 756k → 720k | -2788k → -2841k | -53.3k | 0.98 / +2.1k | +6.9k / +0.8k / -4.9k |
| X' | +8.0k → +4.1k | -3.9k (+19.4k) | 99k → 98k | 520k → 587k | -1559k → -1613k | -54.1k | 0.97 / -4.0k | -5.0k / -0.0k / +1.1k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +15.1k → +26.7k | +11.7k (+39.7k) | 135k → 138k | 363k → 432k | 211k → 374k | +163.1k | nan / n/a | +7.5k / +13.5k / -9.4k |
| 2026 | +26.0k → +29.1k | +3.1k (+31.6k) | 192k → 185k | 322k → 289k | 156k → 175k | +18.5k | nan / n/a | -4.4k / +12.6k / -5.1k |
| L6M | +65.1k → +71.6k | +6.4k (+25.2k) | 139k → 138k | 363k → 432k | 51k → 117k | +66.0k | nan / n/a | +6.8k / +10.0k / -10.3k |
| HOLD | +53.2k → +58.7k | +5.6k (+22.7k) | 171k → 172k | 658k → 666k | -927k → -898k | +29.6k | 1.03 / +7.5k | +2.9k / +10.8k / -8.1k |
| PRE | +50.0k → +51.9k | +1.9k (+22.0k) | 139k → 155k | 705k → 708k | -2540k → -2729k | -189.0k | 0.93 / -1.7k | +6.3k / +2.9k / -7.3k |
| X' | +9.5k → +5.2k | -4.3k (+18.2k) | 103k → 105k | 525k → 654k | -1599k → -1713k | -114.0k | 0.93 / -4.6k | -4.4k / -1.4k / +1.5k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 660 | +6.25 | -1.60 (MDE 3.71) | -7.6k |
| HM | 541 | +3.73 | +2.23 (MDE 4.66) | +8.6k |
| WT | 897 | +2.64 | +1.58 (MDE 2.47) | +7.1k |
| KB | 637 | +4.03 | -1.44 (MDE 3.89) | -3.4k |
| SM | 282 | +3.96 | +3.04 (MDE 4.90) | +4.5k |
| PE | 587 | +3.36 | -1.12 (MDE 5.42) | -2.6k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1649 | +4.42 | -0.86 (MDE 2.54) | -3.8k |
| HM | 1550 | +2.76 | +0.89 (MDE 2.31) | +3.7k |
| WT | 2373 | +1.06 | +0.02 (MDE 1.29) | +0.1k |
| KB | 1707 | +4.09 | +0.15 (MDE 2.49) | +0.3k |
| SM | 821 | +4.56 | -0.58 (MDE 2.89) | -0.9k |
| PE | 1610 | +3.86 | +1.03 (MDE 2.37) | +2.5k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1585 | +0.83 |
| london | 822 | -0.27 |
| pre | 167 | -1.06 |
| nyam | 732 | -0.69 |
| nypm | 294 | +1.46 |
| close | 4 | +1.83 |

#### confluence|cfUp1.5_3m|partial|trig=R2|P=33 - S73 - tier CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative)

basis N
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +31.3k → +38.0k | +6.7k (+43.2k) | 130k → 118k | 319k → 425k | 438k → 532k | +94.3k | nan / n/a | +6.2k / +5.3k / -4.7k |
| 2026 | +37.0k → +73.5k | +36.5k (+85.7k) | 185k → 143k | 306k → 222k | 222k → 441k | +218.8k | nan / n/a | +4.1k / +30.3k / +2.1k |
| L6M | +79.1k → +83.2k | +4.1k (+28.6k) | 137k → 127k | 319k → 425k | 332k → 428k | +95.4k | nan / n/a | -2.6k / +11.5k / -4.8k |
| HOLD | +66.7k → +68.7k | +2.0k (+26.2k) | 169k → 156k | 625k → 578k | -630k → -485k | +145.4k | 1.30 / +22.6k | -4.5k / +10.9k / -4.4k |
| PRE | +61.8k → +50.7k | -11.1k (+16.2k) | 139k → 132k | 615k → 490k | -2305k → -2354k | -49.5k | 0.98 / -12.2k | -3.7k / -2.1k / -5.3k |
| X' | +18.2k → +13.9k | -4.3k (+19.9k) | 102k → 87k | 469k → 407k | -1392k → -1359k | +33.3k | 1.02 / -4.0k | -4.6k / -0.8k / +1.0k |

basis M
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | -17.2k → -9.9k | +7.3k (+25.3k) | 136k → 117k | 537k → 465k | -241k → -138k | +102.6k | 1.74 / +0.0k | +10.3k / -5.5k / +2.5k |
| 2026 | +0.8k → +9.0k | +8.2k (+36.9k) | 183k → 157k | 348k → 339k | 5k → 54k | +49.4k | nan / n/a | +1.0k / +4.8k / +2.4k |
| L6M | +32.1k → +39.8k | +7.7k (+19.9k) | 139k → 126k | 537k → 465k | -639k → -394k | +244.1k | 1.62 / +32.3k | +5.6k / +1.5k / +0.5k |
| HOLD | +20.2k → +27.7k | +7.6k (+18.5k) | 165k → 151k | 698k → 612k | -1559k → -1262k | +297.3k | 1.24 / +14.1k | +4.3k / +2.3k / +1.0k |
| PRE | +35.4k → +28.3k | -7.0k (+17.0k) | 137k → 131k | 756k → 564k | -2788k → -2811k | -22.9k | 0.99 / -7.2k | -1.7k / -3.4k / -1.9k |
| X' | +8.0k → +5.7k | -2.3k (+19.0k) | 99k → 86k | 520k → 454k | -1559k → -1497k | +61.7k | 1.04 / -2.1k | -2.3k / -1.0k / +0.9k |

basis LIVE
| window | stack weekly mean base → rule | Δ mean (MDE) | SD base → rule | maxDD base → rule | worst-20-wk base → rule | Δ worst-20 | equal-risk lot factor / Δ mean at equal risk (STRUCTURE) | Δ from the same trades / re-entry in / re-entry out ($/wk) |
|---|---|---|---|---|---|---|---|---|
| L3M (view) | +15.1k → +29.8k | +14.8k (+43.5k) | 135k → 129k | 363k → 449k | 211k → 418k | +207.0k | nan / n/a | +8.1k / +3.9k / +2.8k |
| 2026 | +26.0k → +65.3k | +39.3k (+76.9k) | 192k → 165k | 322k → 263k | 156k → 392k | +235.6k | nan / n/a | +4.6k / +22.6k / +12.1k |
| L6M | +65.1k → +72.9k | +7.8k (+29.9k) | 139k → 133k | 363k → 449k | 51k → 191k | +140.1k | nan / n/a | -2.4k / +10.8k / -0.6k |
| HOLD | +53.2k → +58.5k | +5.3k (+27.5k) | 171k → 160k | 658k → 603k | -927k → -718k | +209.2k | 1.29 / +22.4k | -4.4k / +10.5k / -0.8k |
| PRE | +50.0k → +38.2k | -11.8k (+16.8k) | 139k → 133k | 705k → 574k | -2540k → -2667k | -127.2k | 0.95 / -13.6k | -2.9k / -4.0k / -4.9k |
| X' | +9.5k → +3.9k | -5.5k (+20.5k) | 103k → 87k | 525k → 475k | -1599k → -1582k | +16.1k | 1.01 / -5.5k | -4.0k / -1.8k / +0.2k |

Per book per contract (N, L6M) - what each book loses / gains by being cut as part of the stack:

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 660 | +6.25 | -0.82 (MDE 2.65) | -3.9k |
| HM | 541 | +3.73 | +1.00 (MDE 3.79) | +3.9k |
| WT | 897 | +2.64 | +1.17 (MDE 1.68) | +5.3k |
| KB | 637 | +4.03 | -1.69 (MDE 3.37) | -4.0k |
| SM | 282 | +3.96 | +2.06 (MDE 3.62) | +3.1k |
| PE | 587 | +3.36 | -0.09 (MDE 4.29) | -0.2k |

Per book per contract (N, PRE):

| book | base trades in window | base pts / contract / trade (N) | rule Δ pts / contract / trade | Δ $/wk |
|---|---|---|---|---|
| ST | 1649 | +4.42 | -2.29 (MDE 1.86) | -10.1k |
| HM | 1550 | +2.76 | +0.13 (MDE 2.09) | +0.5k |
| WT | 2373 | +1.06 | +0.21 (MDE 1.08) | +0.9k |
| KB | 1707 | +4.09 | +0.14 (MDE 1.75) | +0.3k |
| SM | 821 | +4.56 | -0.47 (MDE 2.02) | -0.8k |
| PE | 1610 | +3.86 | -0.85 (MDE 2.15) | -2.0k |

Session column (N, L6M; entry session of the trade):

| session | base trades | Δ pts / contract / trade |
|---|---|---|
| asia | 1585 | -0.15 |
| london | 822 | +0.05 |
| pre | 167 | +0.52 |
| nyam | 732 | +0.17 |
| nypm | 294 | +1.65 |
| close | 4 | +1.09 |

### 5b. Execution, cost and sensitivity of the candidate rows (N; Δ stack mean $/wk; L6M unless stated)

| rule | base | Δ L6M (0 s) | 1 s latency | 3 s latency | +1 pt extra exit cost: Δ L6M | breakeven extra cost (pts) | +-25/50% variants: share >=0 L6M / mean L6M | variants mean Δ PRE+X' | 8-neighbour mean Δ PRE+X' (grid) | rolling quarters + | purged folds + (6) | first-half / second-half of L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| partial|trig=R1.5|P=33|tgt=prorata | MKT | +3.9k | +3.6k | +3.5k | +0.3k | 1.1 | 0.75 / +1.5k | -8.7k | -10.8k | 4/12 | 2 | -4.5k / +12.3k |
| cap|lots=19|mode=skip|session=pre | MKT | +3.2k | n/a | n/a | n/a | nan | 1.00 / +3.7k | +0.2k | +1.3k | 7/12 | 6 | +0.1k / +6.4k |
| cut|trig=stackR-3|act=weakest | MKT | +5.9k | +6.8k | +7.6k | +4.3k | 3.8 | 0.50 / -4.6k | -3.9k | -11.9k | 6/12 | 3 | +12.7k / -0.9k |
| cut|trig=firstBookStopped|act=cutRest33 | MKT | +13.8k | +17.0k | +14.9k | +11.1k | 5.1 | 1.00 / +16.9k | -3.9k | -4.0k | 6/12 | 2 | +9.7k / +17.9k |
| cut|trig=firstBookStopped|act=cutRest50 | MKT | +23.2k | +23.5k | +22.4k | +16.9k | 3.7 | 1.00 / +15.9k | -4.4k | -4.5k | 5/12 | 2 | +7.5k / +38.9k |
| cut|trig=firstBookStopped|act=cutRest100 | MKT | +9.5k | +10.4k | +10.0k | +6.5k | 3.2 | 1.00 / +13.9k | -4.9k | -4.0k | 6/12 | 2 | -9.1k / +28.0k |
| confluence|cfUp1.5_3m|alone | MKT | +14.0k | n/a | n/a | n/a | nan | nan / n/a | n/a | n/a | 8/12 | 4 | -0.5k / +28.4k |
| confluence|cfUp2_3m|partial|trig=R2|P=33 | MKT | +18.7k | +18.9k | +18.2k | +15.3k | 5.4 | 1.00 / +16.5k | -9.7k | -14.3k | 5/12 | 3 | +8.5k / +28.9k |
| cap|lots=19|mode=skip|session=pre | S73 | +2.7k | n/a | n/a | n/a | nan | 1.00 / +2.0k | +1.4k | +1.6k | 8/12 | 5 | +4.3k / +1.2k |
| cut|trig=stackR-3|act=weakest | S73 | +7.2k | +5.1k | +5.1k | +3.0k | 1.7 | 0.25 / -9.6k | -6.8k | -14.2k | 6/12 | 2 | +10.6k / +3.8k |
| cut|trig=firstBookStopped|act=cutRest50 | S73 | +6.1k | +8.2k | +3.8k | +1.3k | 1.3 | 1.00 / +6.8k | -3.8k | -4.5k | 6/12 | 2 | -5.8k / +18.0k |
| cut|trig=firstBookStopped|act=cutRest100 | S73 | +3.7k | -0.6k | +3.2k | -3.3k | 0.5 | 1.00 / +5.8k | -4.4k | -3.7k | 5/12 | 2 | -21.7k / +29.1k |
| confluence|cfUp1.5_3m|partial|trig=R2|P=33 | S73 | +2.8k | +3.5k | +3.6k | +0.8k | 1.4 | 0.88 / +4.6k | -8.5k | -15.2k | 3/12 | 3 | -1.4k / +6.9k |
| confluence|cfUp2_3m|alone | S73 | +7.6k | n/a | n/a | n/a | nan | nan / n/a | n/a | n/a | 5/12 | 4 | +7.3k / +7.8k |

Latency: the partial / cut fills at the close of second k+1+delay (delay 1 or 3 s after the trigger second); caps and sizing decide at the signal second and have no trigger-to-order delay in this engine. Breakeven = extra exit cost per lot-exit (pts) at which the L6M Δ mean is zero (linear from the +1 pt run); n/a for entry-skip rules (no extra fills). Drift series by quarter: `out/stackpart/drift_quarterly.csv`.

## 6. Verdicts, one per rule (directive sentence form; L6M = last 6 months; N basis, M and LIVE-CAL in section 5)

* **G1 / MKT** Stack partial on profit, pro-rata (X R / X pts per lot; P 25/33/50%) - partial|trig=R2|P=33|tgt=prorata (MKT, N): keeps 100% of the stack mean and cuts worst-20-weeks by +75% in the last 6 months (HOLD 98% / +14%, L3M +6.1k/wk, PRE 71% / +3%, X' 76% / +4%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G1 / S73** Stack partial on profit, pro-rata (X R / X pts per lot; P 25/33/50%) - partial|trig=R2|P=33|tgt=prorata (S73, N): keeps 93% of the stack mean and cuts worst-20-weeks by -60% in the last 6 months (HOLD 90% / -24%, L3M -9.7k/wk, PRE 82% / +4%, X' 92% / +15%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G2 / MKT** Stack partial: whole weakest book / latest entrant - partial|trig=R2|P=100|tgt=weakest (MKT, N): keeps 98% of the stack mean and cuts worst-20-weeks by +21% in the last 6 months (HOLD 102% / +11%, L3M +14.9k/wk, PRE 81% / +5%, X' 60% / +9%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G2 / S73** Stack partial: whole weakest book / latest entrant - partial|trig=R2|P=100|tgt=weakest (S73, N): keeps 89% of the stack mean and cuts worst-20-weeks by -36% in the last 6 months (HOLD 89% / -10%, L3M -1.6k/wk, PRE 89% / +8%, X' 78% / +10%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G3 / MKT** Stack partial + remaining stops to stack breakeven / MAE+k - partial|trig=R2|P=33|tgt=prorata|stop=stackBE (MKT, N): keeps 104% of the stack mean and cuts worst-20-weeks by +96% in the last 6 months (HOLD 100% / +18%, L3M +9.1k/wk, PRE 50% / -7%, X' 58% / -3%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G3 / S73** Stack partial + remaining stops to stack breakeven / MAE+k - partial|trig=R2|P=33|tgt=prorata|stop=stackBE (S73, N): keeps 88% of the stack mean and cuts worst-20-weeks by -47% in the last 6 months (HOLD 84% / -12%, L3M -13.9k/wk, PRE 66% / -5%, X' 67% / +7%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G4 / MKT** Staged stack partial (P at X and again at 2X) - partial|trig=R2|P=33|tgt=prorata|staged=2X (MKT, N): keeps 101% of the stack mean and cuts worst-20-weeks by +87% in the last 6 months (HOLD 99% / +16%, L3M +6.0k/wk, PRE 71% / +1%, X' 75% / +4%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G4 / S73** Staged stack partial (P at X and again at 2X) - partial|trig=R2|P=33|tgt=prorata|staged=2X (S73, N): keeps 94% of the stack mean and cuts worst-20-weeks by -55% in the last 6 months (HOLD 91% / -24%, L3M -9.7k/wk, PRE 82% / +4%, X' 90% / +16%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G5 / MKT** Same-side exposure cap in lots (per session variants G5s) - cap|lots=19|mode=room (MKT, N): keeps 64% of the stack mean and cuts worst-20-weeks by +5% in the last 6 months (HOLD 59% / +19%, L3M -22.3k/wk, PRE 61% / +18%, X' 61% / +29%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G5 / S73** Same-side exposure cap in lots (per session variants G5s) - cap|lots=19|mode=room (S73, N): keeps 75% of the stack mean and cuts worst-20-weeks by -58% in the last 6 months (HOLD 73% / -4%, L3M -28.1k/wk, PRE 76% / +15%, X' 65% / +27%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G6 / MKT** Same-side exposure cap in R (lot-points) - cap|lotpts=1140|mode=room (MKT, N): keeps 67% of the stack mean and cuts worst-20-weeks by +34% in the last 6 months (HOLD 60% / +19%, L3M -23.6k/wk, PRE 61% / +17%, X' 71% / +28%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G6 / S73** Same-side exposure cap in R (lot-points) - cap|lotpts=1140|mode=room (S73, N): keeps 73% of the stack mean and cuts worst-20-weeks by -46% in the last 6 months (HOLD 68% / -6%, L3M -25.3k/wk, PRE 77% / +16%, X' 68% / +26%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G7 / MKT** Correlated-entry sizing - size|nsame>=1|same=0.5|opp=1 (MKT, N): keeps 83% of the stack mean and cuts worst-20-weeks by +202% in the last 6 months (HOLD 87% / +51%, L3M +13.9k/wk, PRE 56% / +28%, X' 73% / +42%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G7 / S73** Correlated-entry sizing - size|nsame>=1|same=0.5|opp=1 (S73, N): keeps 64% of the stack mean and cuts worst-20-weeks by -54% in the last 6 months (HOLD 64% / +17%, L3M -5.8k/wk, PRE 58% / +26%, X' 54% / +41%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G8 / MKT** Stack stop / stack cut - cut|trig=stackR-2|act=prorata50 (MKT, N): keeps 82% of the stack mean and cuts worst-20-weeks by -67% in the last 6 months (HOLD 75% / -15%, L3M -2.5k/wk, PRE 79% / +4%, X' 95% / +18%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G8 / S73** Stack stop / stack cut - cut|trig=stackR-2|act=prorata50 (S73, N): keeps 74% of the stack mean and cuts worst-20-weeks by -130% in the last 6 months (HOLD 71% / -63%, L3M -13.5k/wk, PRE 73% / +2%, X' 101% / +17%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G9 / MKT** First book stopped: cut the rest - cut|trig=firstBookStopped|act=cutRest50 (MKT, N): keeps 137% of the stack mean and cuts worst-20-weeks by +304% in the last 6 months (HOLD 140% / +25%, L3M +35.7k/wk, PRE 86% / +5%, X' 104% / -2%). Tier: CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative).
* **G9 / S73** First book stopped: cut the rest - cut|trig=firstBookStopped|act=cutRest50 (S73, N): keeps 108% of the stack mean and cuts worst-20-weeks by +39% in the last 6 months (HOLD 107% / +0%, L3M +16.0k/wk, PRE 90% / +7%, X' 98% / -2%). Tier: CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative).
* **G10 / MKT** Stack trail on the combined position - trail|T=30|stack (MKT, N): keeps 70% of the stack mean and cuts worst-20-weeks by -92% in the last 6 months (HOLD 69% / -6%, L3M -0.2k/wk, PRE 57% / +3%, X' 36% / -19%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G10 / S73** Stack trail on the combined position - trail|T=30|stack (S73, N): keeps 76% of the stack mean and cuts worst-20-weeks by -71% in the last 6 months (HOLD 68% / -9%, L3M +1.3k/wk, PRE 69% / +9%, X' 2% / -21%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).
* **G11 / MKT** Confluence (EINT1) with / without the stack partial - confluence|cfUp2_3m|partial|trig=R2|P=33 (MKT, N): keeps 129% of the stack mean and cuts worst-20-weeks by +331% in the last 6 months (HOLD 129% / +37%, L3M +32.7k/wk, PRE 74% / -4%, X' 81% / +8%). Tier: CANDIDATE-RECENT (N and LIVE-CAL >=0 in L6M and HOLD; PRE and/or X' negative).
* **G11 / S73** Confluence (EINT1) with / without the stack partial - confluence|cfUp2_3m|partial|trig=R2|P=33 (S73, N): keeps 98% of the stack mean and cuts worst-20-weeks by -4% in the last 6 months (HOLD 92% / -9%, L3M +7.2k/wk, PRE 81% / -3%, X' 59% / +1%). Tier: BEST-AVAILABLE-NEGATIVE (stack mean < 0 on N in L6M and/or HOLD).

Reading of the sentence: 'keeps X% of the stack mean' = rule mean / base mean in the window on N (base L6M +61k/wk on N, PRE +58k, X' +16k, HOLD +48k); 'cuts worst-20-weeks by Y%' = (rule - base) / |base| of the sum of the 20 worst weekly totals, positive = shallower, negative = deeper. In L6M (28 weeks) and L3M (14 weeks) the worst-20 sum covers most of the window, so a +300% move there means the tail weeks turned positive, not a 3x risk cut; read the HOLD / PRE / X' columns for the tail effect.

## 7. The run-this table

| rule | run it? | evidence | live state D6 must compute |
|---|---|---|---|
| Stack partial on profit (R or pts/lot triggers, pro-rata / weakest / latest, +BE/MAE stop, staged) | NO | 0 of 98 cells >= 0 in PRE on N (PRE -38k..-4k/wk, PRE worst-20 -22%..+10%); recent windows mixed (e.g. 1.5R/33% L6M +4.6k, HOLD +4.7k, PRE -13k); equal-risk frame no gain; placebo rank of the 1.5R/33% cell vs random partials 0.79-0.92 recent, 0.10 PRE | other books' positions, combined unrealised pts/lot and R |
| Same-side lot cap / R cap (all sessions) | NO | 0 of 20 cells >= 0 in PRE (PRE -29k..-5k/wk); cuts PRE worst-20 by 2-42% by removing lots; equal-risk neutral or worse | net same-side lots |
| Pre-session (08:30-09:30 ET) same-side cap: skip an entry when >= 19 research lots (~8 lots at the 12-lot live scale) are already on the side | PAPER-TRADE (LEAD, not PASS) | N >= 0 in PRE, X', HOLD, L6M, L3M on both entry bases (+1.3k..+4.5k/wk, MDE 12-13k; 2026 5 weeks -2.4k / -6.5k); all 4 variants (19/24 lots x room/skip) >= 0 in PRE and X' on both bases (neighbours agree), placebo rank 0.88-1.00 / 200, 6/6 and 5/6 folds +; fails RC / RW / DSR; ~430 skips in 35 months | net same-side lots at the signal, session id (pre) |
| Correlated-entry sizing (50% / 67% when books are on; 150% / skip when a book is opposite) | NO | 1 of 14 cells >= 0 in PRE (S73 opposite-side 150%: +0.8k PRE, -11k..-16k L6M/HOLD); same-side halving cuts PRE worst-20 by up to 29% (X' 42%) but loses -26k/wk of mean | books on same / other side at the signal |
| Stack stop / cut (stack at -1..-3R, all books under water, close weakest / latest / pro-rata) | NO | 0 of 24 cells >= 0 in PRE (-35k..-2k); only '-3R close weakest' is positive in L6M/HOLD (MKT +5.9k/+2.5k; LIVE-CAL +11.5k/+7.9k), negative PRE -15k | combined unrealised in R, per-book unrealised |
| First book stopped -> cut the rest (50% / 33% / 100% of the other same-side books) | FORWARD-TEST ONLY (CANDIDATE-RECENT) | N and LIVE-CAL >= 0 in L6M, HOLD, L3M on both bases; PRE -6k..-12k, X' ~0; rank vs random cuts 0.91-1.00 recent, 0.41-0.97 PRE (0.41/0.56 MKT 33/50%); regime-dependent (base stack was losing in L3M) | stop-out event of a book, books still open on the same side |
| Stack trail (20/30/40 pts behind the stack MFE) | NO | 0 of 3 cells >= 0 in PRE (-44k..-3k); L3M positive only for some T=30/40 cells | stack MFE in pts/lot |
| Confluence (EINT1) + stack partial | NO for the pair; confluence alone is EINT1's lead | cfUp1.5 alone L6M +13.5k/wk (MKT; shuffled-within-day placebo rank 0.93 L6M, 0.95 PRE), cfUp2 alone +6.6k (S73); with the R2/33% partial L6M +17.8k (MKT) / +4.1k (S73) but PRE -11k..-15k vs +0.5k..+1.9k alone | other books' same-direction entries within 3 min |

## 8. What each cell is (STRUCTURE vs INFO)

* Partials, caps, sizing multipliers, stack cuts and trails are STRUCTURE: they change the lots and the exit timing; their stack-mean effect is the lots removed times the books' edge, and the equal-risk frame (section 5) shows whether any of them beats scaling the base down. None does. The first-book-stopped cut and the pre-session cap are the only rules whose placebo (random cut at the same rate / random skip at the same rate) they beat, i.e. the only ones with an INFO component (the timing of the cut / the state at the pre-session signal carries information); both are tiny samples (first-stop cut fires ~1,500 times; pre cap ~430 skips).
* The 70/30 base results differ from the market base by the lock-engine feedback (the 70/30 stack is larger in lots and its give-back arm / week floor fire differently); the sign pattern is the same.

## 9. Disclosures and limits

* The smoke test printed L6M/HOLD/PRE/X' stack means of the G1 flagship once (DECISIONS.md); everything else in the recent windows was read once in stage B. Neighbour means use PRE+X' only (no extra look). Sensitivity variants (+-25/50% of X, P, C, T) read the recent windows for the 16 candidate cells only (same group look).
* Placebos: 200 draws for the candidate cells and 30 draws for the other selected cells (rank resolution 0.03). Latency (1 s / 3 s) and the +1 pt exit-cost breakeven are in `qv_cells.csv` (columns lat1_*, lat3_*, breakeven_extra_cost_pts_L6M).
* Depth capacity at the fire seconds is NOT measured (needs the top-5 book at the partial seconds; the mbp-10 store is not joined to the stack seconds): events are 1-lot slices on the live 2-s schedule only. Regime split by vol tag uses the library's vol_tag_entry_day.
* The 11:40 ET 2026-10-30 12-lot short is post-cutoff and was not read.
* QL-1 qv.py not present: tests implemented locally in `sp_qv.py` (stationary-bootstrap RC and Romano-Wolf stepdown on weekly deltas, 4-week blocks, 2,000 draws; DSR with trials = 396; PBO by CSCV with 16 blocks of weeks; Newey-West lag 4; purged 6-fold with one-week embargo on the weekly delta series).
