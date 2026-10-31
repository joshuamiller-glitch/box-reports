# DS3_NO_TRADE_C_D - T-NO-TRADE-EXPANDED sections C and D at LIVE lots on the D6-faithful engine, the learned no-trade model per D6 book, the states NTE-1 could not build, the calendar gaps (agent NT-3, 2026-10-31)

Research only; no live / execution / chart change, no credentials, no purchases. Prereg `autopilot/NT3_prereg.md` sha256 79b6908d9afbccf068c424aa5ed0710b7cf0506e16a59992d013169fb6e84120 (DECISIONS.md, before any engine-scored result). Masks capped 20260206 (windows L3M 20251106.., L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131); UNTOUCHED never read. Code `l2vast/ds3/code/ntexp3/`, outputs `l2vast/ds3/out/ntexp2/` (states_all.parquet 717 states, specs_CD.parquet, results_{C,D,L,T}.parquet, res_*.npz = daily stack $ of every run, valid_*.csv, map_new.parquet, learned_*).

**Base (every number below is a paired weekly delta vs this stack).** D6 composite on `sundaydecision/sdlib` (= `sundaystack2/ss2_lib` with A6 = PB7), integer half-up min-1 lots, causal running-max locks, live lots/sessions (K6 2 AS/LO/NA/NP; P6 7 AS/LO/NA; U6 4 AS/LO; H6 4 AS / 2 NA; M6 2 LO/NA; A6 1 AS; O6 has no series), Native 1.28, 70/30 split on all books, PE confirmation, stop cut, 8-line zone skip (20 pts), ER sizer on all six, A6 at market. Stack level $k/wk: L3M 37.7 | L6M 43.5 | HOLD 40.5 | PRE 24.7 | X' 8.4 (ties to DS3_SUNDAY_DECISION 43.5 L6M). Live signals (rows with lots) L3M/L6M/HOLD/PRE/X': 2432/4368/4821/9792/3616. A rule = skip (added to the zone skip: the signal is never taken, the one-position rule and the governors see the book without it), x0.5 / x1.5 (multiplier on the ER multiplier: lots = Max(1, Floor(lots x ER x m + 0.5)), enters the running max), take-only (skip the complement). Per-signal $ at live lots = pnl x kept x 20 x lots (reproduces the engine daily exactly). Cell = stack delta $k/wk (MDE = 2.8 x SE of the paired weekly delta); `~` = inside MDE. Delay and re-target actions are NOT run (the lock engine has no hold-then-take path); size 25% equals size 50% at 1-2 lot books because of the min-1 rule.

## 0. Page 1 - what the stack says (a null is a result)

1. **Section C (where NOT to take a valid signal): no rule survives. Across the 926 engine-run C cells (6 combination families x 7 scopes x skip / x0.5), the 282 skip cells that were positive in BOTH PRE and X' (selection windows) average +0.8k/wk there and -0.9k/wk in L6M / -0.8k in HOLD; only 30% are positive in L6M and 0% clear the L6M MDE.** (x0.5: +0.4k selection -> -0.6k L6M.) The correlation across all C cells between the selection-window gain and the L6M gain is -0.23: a skip rule's out-of-sample sign is the opposite of its in-sample sign (NTE-1's finding, reproduced at live lots on the D6 engine). Screened 65,715 combinations (8,628 valid: >= 25 live signals in each of PRE and X', fire share <= 60%), engine-run the top 15 of each type per scope.
2. **Section D (where to take MORE): size-up x1.5 is positive in every recent window for most cells, and that is structure.** The 495 x1.5 cells selected positive in both PRE and X' average +1.0k selection and +0.8k L6M (67% positive, 4% beyond MDE) - but the base stack earns +43.5k/wk, so ANY extra lot on a random subset adds money: uniform x1.5 on EVERY live signal is +18.6k L6M (MDE 11.1) and **only 3.5k of that survives if the day / week locks are NOT widened by the larger multiplier (the running-max SizeMult rule): the size-up gain is the governors, not the lots**, and the weekly mean/SD ratio does not improve (3e). Take-only (skip the complement) cells average -2.5k L6M. One cell (size x1.5 when 5-min ER >= 0.386 AND >= 1.5 ATR beyond the 5-min EMA20, all books) meets the prereg CONFIRMED-RECENT gates (positive PRE / X' / L6M / HOLD, L6M +13.8k beyond MDE 11.7, beats the random same-rate and time-shifted placebos at 24 of 24) and is NOT promoted: it is the ER sizer taken one step further (ER >= 0.30 alone gives +17.5k), 64% of its gain is lock widening, no Romano-Wolf survivor in its family, equal-risk ratio flat (3e).
3. **Learned no-trade model (walk-forward LightGBM P(target), monthly and 3-month refits, per D6 book + pooled): it discriminates P(target) (out-of-sample AUC 0.55-0.79, A6 and M6 weakest) but the policies do not make money on the stack.** Real model, bottom-20% skip, L6M stack delta by scope: A6 -0.0 | H6 -0.2 | K6 +0.8 | M6 -1.1 | P6 -3.5 | POOL6 -1.4 | U6 +0.3 ($k/wk, monthly refit). The model's low bucket is dominated by 'a set-line from the 11-line set lies within 20 pts ahead' (the ZONES family the base already skips for 8 lines) - section 2.
4. **States NTE-1 could not build, now built from the engines' own recursions** (KB band-break closure, PE pullback depth, A6/PB7 pullback depth, MV vote count, signal-bar volume) **and 60-s / 120-s sweeps from l2feat** (section 4, both edges, per book, last 6 months first). **Calendar gaps:** dated sources on disk and used - Treasury auction closes (13:00 ET notes/bonds, 11:30 ET bills; `data/gap/ds50/treasury_auctions.csv`, 588 auctions 2012-2026) and mega-cap earnings nights (EDGAR 8-K item 2.02 acceptance times for 10 of the top-15 NQ names, `data/gap/edgar`, 694 filings); STILL NAMED GAPS (nothing on disk, nothing fabricated): PPI, retail sales, GDP release dates, Fed speakers, the other 5 top-15 reporters (PEP, CSCO, AMD, TMUS, ADBE), the 10:00 releases other than the ISM rule dates (section 5).
5. **Nothing here is promoted.** CONFIRMED-RECENT (prereg) needs: positive in PRE and X' and L6M and HOLD, L6M delta above its MDE, and BOTH placebos (random same-rate, time-shifted) beaten at the 95th percentile; promotion (qv) additionally needs a Romano-Wolf survivor, the neighbourhood / breakeven / capacity columns and, for a size-up, an improved equal-risk ratio. Every row is selected on PRE u X' only, with one recent look per group (post-hoc flag: none of these rows was chosen using L3M / L6M / HOLD, so they are honest out-of-sample looks, but the group of 65,715 screened combinations is the multiplicity). One learned/extracted skip is worth naming as a LEAD: the K6 AND-set (2d) is positive in all five windows with both placebos beaten, but +0.6k/wk L6M against an MDE of 1.8k.

### Plain sentences
- The best single-state skip over all six D6 books (ranked on PRE u X' only: `xm.es_minus_nq60s>=1.5`) removes 3.9 live signals a week (2.5% of them) and moves the stack by +2.5 (4.1)~ PRE / +3.0 (4.1)~ X' (selection) and -2.6 (6.1)~ L3M / -0.5 (4.0)~ L6M / -0.8 (3.7)~ HOLD $k/wk; the signals it removes earned +0.1k/wk in the base in L6M (that is the cost of skipping them).
- The learned no-trade model (pooled over the six D6 books, monthly refit, skip the bottom 20% of predicted P(target)) acts on 20.0 of ~156 live signals a week in L6M (keeps 87% of the live signals) and adds -1.4 (5.3)~ L6M / -1.2 (4.7)~ HOLD / +1.8 (5.0)~ PRE / -2.4 (5.2)~ X' $k/wk at the D6 live lots; the signals it skips earned +1.1k/wk in the base. Per book (monthly, bottom 20%): A6 -0.0 (0.1)~ L6M; H6 -0.2 (1.6)~ L6M; K6 +0.8 (1.3)~ L6M; M6 -1.1 (1.3)~ L6M; P6 -3.5 (4.1)~ L6M; POOL6 -1.4 (5.3)~ L6M; U6 +0.3 (0.7)~ L6M. At equal risk (the random same-rate skip is the lot-matched null, 2c) it adds nothing distinguishable from zero.
- 'The states that most reliably precede a failed signal in this market' (PRE u X' conjunction rank over all six books, ALL scope): `xm.es_minus_nq60s>=1.5` (L6M stack -0.5k/wk); `st.1h.rng_exp1<=0.6003` (L6M stack -1.8k/wk); `st.prev_ret_rth>=0.7105` (L6M stack -0.9k/wk). They are not stable: the lowering of P(target) in PRE u X' and in the last six months correlate at Spearman +0.08 (NTE-1), and the stack deltas of the same cells flip sign (1a).

## 1. Section C - pairs / triples / k-of-n / four-legged / nested, PRE u X' ranked, D6 stack at live lots

Selection (PRE u X' only; nothing else was computed before the lists were fixed): 717 states -> 1,131 masks; per scope (ALL, K6, P6, U6, H6, M6, A6) and direction the per-signal live-lot kept $ of signals inside vs outside the state, Welch t in PRE and in X' separately, conjunction score min(t_PRE, t_X') of the lowering; one threshold per state; top 30 distinct states per scope. Combinations built from those 30 (pairs 435, triples 4,060, k-of-n 2/3 of the top 10 and 3/4/5 of the top 30, OR of the top 2/3, four-legged = one state from each of location / time-calendar / volatility-book-tape / after-event, top 3 per family AND, plus any-3-of-4, nested = `nest.setline_20_30` (an 8-line-set line 20-30 pts ahead, beyond the base zone skip) AND each top state) and screened per signal; the top 15 per type per scope were engine-run as skip and x0.5. Screened 65,715; valid 8,628; engine-run 926 C cells. Per-scope screen counts: `combo_screen_counts.csv`.

### 1a. The flip, by family (all engine-run cells with a positive PRE and X' stack delta; $k/wk, mean over cells)

| family | action | cells run | selected (PRE>0 and X'>0) | mean PRE | mean X' | mean L6M | mean HOLD | share L6M>0 | share L6M>MDE |
|---|---|---|---|---|---|---|---|---|---|
| single | skip | 210 | 97 | +0.4 | +0.7 | -1.3 | -1.2 | 29% | 0% |
| single | x0.5 | 210 | 92 | +0.3 | +0.3 | -0.8 | -0.6 | 23% | 0% |
| pair | skip | 105 | 86 | +0.6 | +0.9 | -0.7 | -0.6 | 27% | 0% |
| pair | x0.5 | 105 | 76 | +0.3 | +0.4 | -0.5 | -0.4 | 26% | 0% |
| triple | skip | 93 | 75 | +0.7 | +0.8 | -0.3 | -0.3 | 40% | 0% |
| triple | x0.5 | 93 | 66 | +0.3 | +0.3 | -0.3 | -0.3 | 29% | 0% |
| k-of-n | skip | 29 | 21 | +1.5 | +2.7 | -2.4 | -2.1 | 14% | 0% |
| k-of-n | x0.5 | 29 | 21 | +0.9 | +1.1 | -1.5 | -1.3 | 5% | 0% |
| four-legged | skip | 3 | 0 | - | - | - | - | 0% | 0% |
| four-legged | x0.5 | 3 | 0 | - | - | - | - | 0% | 0% |
| nested | skip | 23 | 3 | +0.2 | +0.4 | -0.2 | -0.3 | 33% | 0% |
| nested | x0.5 | 23 | 3 | +0.1 | +0.1 | +0.1 | +0.1 | 33% | 0% |

### 1b. The reported top rule per family and action (chosen on min(PRE, X') STACK delta - selection windows only; one recent look)

| family | action | scope | rule | n PRE/X' sig | PRE | X' | L3M | L6M | HOLD | fired/wk (L6M) | base $ of the affected signals $k/wk | placebo rank rand / shift | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| four | skip | K6 | st.5m.ribbon_w<=0.8036 AND st.ret_RTY_15m>=14.65 AND aft.book_loser_within10 | 96/34 | -0.0 (0.8)~ | +0.1 (0.4)~ | -0.2 (1.6)~ | +0.0 (0.9)~ | +0.1 (0.8)~ | 1.5 | -0.2 | 0.67 / 0.62 | NO |
| four | x0.5 | U6 | st.15m.bbw_pct100<=0.2 AND st.sig_rv_5m<=5.882 AND stk.same_lots_res>=20 | 27/29 | +0.0 (0.4)~ | -0.0 (0.8)~ | +0.0 (0.0)~ | +0.1 (0.8)~ | +0.3 (0.8)~ | 0.1 | -0.3 | 0.79 / 0.79 | NO |
| kofn | skip | P6 | xm.es_minus_nq60s>=1.5 OR st.1h.rng_exp1<=0.6003 OR st.1d.chop14<=35.66 | 567/170 | +5.6 (6.9)~ | +5.3 (5.8)~ | -6.0 (9.5)~ | -2.9 (6.9)~ | -1.1 (7.3)~ | 4.4 | +1.5 | 1.00 / 0.96 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| kofn | x0.5 | P6 | xm.es_minus_nq60s>=1.5 OR st.1h.rng_exp1<=0.6003 OR st.1d.chop14<=35.66 | 567/170 | +3.7 (3.9)~ | +2.5 (3.2)~ | -7.9 (12.3)~ | -3.7 (7.0)~ | -2.6 (6.6)~ | 4.4 | +1.5 | 0.96 / 0.88 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| nested | skip | ALL | nest.setline_20_30 AND tm.lunch.1130_1330 | 30/25 | +0.1 (1.2)~ | +0.7 (1.1)~ | +0.2 (0.8)~ | -0.2 (0.6)~ | -0.1 (0.6)~ | 0.8 | +0.3 | 0.21 / 0.46 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| nested | x0.5 | P6 | nest.setline_20_30 AND void.lvn_ahead_50pctTD | 77/34 | +0.1 (2.6)~ | +0.1 (1.8)~ | +2.0 (4.5)~ | +0.5 (3.0)~ | +0.4 (2.6)~ | 1.0 | -1.0 | 0.92 / 0.83 | LEAD (placebo not beaten) |
| pair | skip | P6 | px.struct.1h.mixed AND st.5m.bbw_pct100<=0.44 | 241/85 | +2.1 (6.3)~ | +2.8 (3.6)~ | -2.2 (9.3)~ | -2.1 (5.0)~ | -1.8 (4.4)~ | 3.3 | +1.5 | 0.79 / 0.88 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| pair | x0.5 | P6 | px.struct.1h.mixed AND st.5m.bbw_pct100<=0.44 | 241/85 | +1.0 (4.6)~ | +1.1 (1.9)~ | -2.5 (9.8)~ | -2.1 (5.2)~ | -1.7 (4.6)~ | 3.3 | +1.5 | 0.71 / 0.92 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| single | skip | ALL | xm.es_minus_nq60s>=1.5 | 556/169 | +2.5 (4.1)~ | +3.0 (4.1)~ | -2.6 (6.1)~ | -0.5 (4.0)~ | -0.8 (3.7)~ | 3.9 | +0.1 | 0.92 / 0.92 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| single | x0.5 | ALL | xm.es_minus_nq60s>=1.5 | 556/169 | +1.1 (1.7)~ | +1.4 (1.9)~ | -2.5 (4.3)~ | -1.2 (2.4)~ | -1.4 (2.4)~ | 3.9 | +0.1 | 0.62 / 0.62 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| triple | skip | P6 | void.lvn_ahead_50pctTD AND st.vix9d_over_vix<=0.8937 AND px.struct.1h.mixed | 105/49 | +2.5 (2.7)~ | +2.4 (3.3)~ | -4.7 (5.8)~ | -1.2 (5.0)~ | -1.5 (5.2)~ | 2.7 | +0.4 | 0.79 / 0.75 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| triple | x0.5 | P6 | void.lvn_ahead_50pctTD AND st.sig_es_nq_div5>=0.273 AND px.struct.1h.mixed | 95/51 | +0.8 (2.4)~ | +1.3 (1.7)~ | -3.8 (8.0)~ | -2.0 (4.3)~ | -0.9 (4.2)~ | 0.9 | +1.1 | 0.17 / 0.21 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |

### 1c. Per D6 book: the best skip per scope and family on min(PRE, X') (the book-level answer; x0.5 in the CSV `results_C.parquet`)

| scope | best family | rule | n PRE/X' | PRE | X' | L3M | L6M | HOLD | fired/wk | base $ affected $k/wk | tier (no placebo) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | any2 | xm.es_minus_nq60s>=1.5 OR st.1h.rng_exp1<=0.6003 | 1376/507 | +4.4 (7.0)~ | +4.4 (6.9)~ | -6.4 (15.4)~ | -2.7 (10.0)~ | -2.2 (9.0)~ | 14.0 | +1.7 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| K6 | any3 | st.prev_rng_atrd>=1.301 OR day.afterbigday1p5pct OR px.ext.5m.ema50<=-2 | 1143/226 | +1.0 (2.2)~ | +1.5 (1.5) | -4.3 (6.9)~ | -2.4 (4.1)~ | -2.5 (3.9)~ | 17.7 | +2.2 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| P6 | any3 | xm.es_minus_nq60s>=1.5 OR st.1h.rng_exp1<=0.6003 OR st.1d.chop14<=35.66 | 567/170 | +5.6 (6.9)~ | +5.3 (5.8)~ | -6.0 (9.5)~ | -2.9 (6.9)~ | -1.1 (7.3)~ | 4.4 | +1.5 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| U6 | triple | st.1h.rsi14>=60.22 AND stk.same_lots_res>=20 AND px.ext.15m.ema200<=-2 | 35/27 | +0.7 (1.3)~ | +0.8 (1.7)~ | -0.3 (3.1)~ | -0.6 (1.9)~ | -0.6 (1.6)~ | 0.5 | +0.6 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| H6 | kof3of10 | >= 3.0 of [st.prev_rng_atrd>=1.301; st.1h.rng_exp1<=0.6003; st.1m.bbw_pct100>=0.79; aft.pooled_winner_within10; aft.pooled_winner_within20; st.15m.... | 457/148 | +1.4 (2.5)~ | +2.4 (2.2) | -5.8 (4.4) | -5.7 (4.0) | -4.7 (3.7) | 6.8 | +5.8 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| M6 | any2 | px.ext.1m.ema20>=3 OR st.ret_YM_15m>=19.18 | 316/70 | +0.6 (1.3)~ | +0.7 (1.0)~ | -0.6 (2.8)~ | -0.2 (1.5)~ | -0.1 (1.4)~ | 3.5 | -0.0 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| A6 | single | bk.sweep_against30>=4 | 150/32 | +0.8 (2.0)~ | +0.6 (1.6)~ | -1.7 (2.6)~ | -1.0 (1.5)~ | -0.8 (1.3)~ | 3.8 | +0.8 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |

## 2. The learned no-trade model - walk-forward LightGBM P(target), per D6 book and pooled

Model: LightGBM binary (120 rounds, 15 leaves, feature fraction 0.3) on all 717 states + signal quality (td, sd, td/sd, side, minute-of-day, weekday, session); target = the trade's exit type is the target; one model per D6 book trained on ALL sessions of the book (the base's zone-skip survivors), pooled model on the six books; refit MONTHLY and every 3 MONTHS (Q), training = trailing 365 days of trades CLOSED before the refit date (>= 300 rows), first refit 2023-06-01 (so X' is predicted from 2023-06). Policy: act on live signals whose predicted P(target) is below the q-quantile (q = 10/20/30%) of the book's PRE u X' predictions (the cut is set on selection windows only): skip, or x0.5. Placebos: LABEL-shuffled (6 monthly draws per book; 3 for the pooled 3-month model) and FEATURE-shuffled (columns permuted independently, 3 draws; 2 for pooled), refit and engine-run exactly like the real model. Note that td/sd are in the feature set: the model partly learns the target distance, which the engine already knows - the stack numbers below are the arbiter, not the AUC.

### 2a. Discrimination (AUC of predicted P(target) on live signals) and Brier skill vs the unconditional rate, real model; label-shuffled / feature-shuffled AUC in L6M

| scope | refit | AUC PRE | AUC X' | AUC HOLD | AUC L6M | Brier skill L6M | label-shuffled AUC L6M (mean of draws) | feature-shuffled AUC L6M |
|---|---|---|---|---|---|---|---|---|
| K6 | monthly | 0.673 | 0.678 | 0.677 | 0.666 | +0.106 | 0.500 | 0.513 |
| K6 | 3-month | 0.669 | 0.677 | 0.678 | 0.668 | +0.110 | - | - |
| P6 | monthly | 0.666 | 0.632 | 0.687 | 0.688 | +0.101 | 0.497 | 0.509 |
| P6 | 3-month | 0.653 | 0.667 | 0.685 | 0.687 | +0.100 | - | - |
| U6 | monthly | 0.678 | 0.615 | 0.786 | 0.783 | +0.228 | 0.512 | 0.498 |
| U6 | 3-month | 0.677 | - | 0.775 | 0.778 | +0.217 | - | - |
| H6 | monthly | 0.685 | 0.647 | 0.677 | 0.662 | +0.091 | 0.519 | 0.491 |
| H6 | 3-month | 0.687 | 0.669 | 0.678 | 0.661 | +0.087 | - | - |
| M6 | monthly | 0.596 | 0.602 | 0.578 | 0.568 | +0.013 | 0.476 | 0.475 |
| M6 | 3-month | 0.605 | 0.625 | 0.579 | 0.575 | +0.025 | - | - |
| A6 | monthly | 0.591 | 0.554 | 0.559 | 0.558 | -0.008 | 0.496 | 0.512 |
| A6 | 3-month | 0.592 | 0.539 | 0.571 | 0.566 | +0.000 | - | - |
| POOL6 | monthly | 0.652 | 0.655 | 0.655 | 0.649 | +0.087 | - | - |
| POOL6 | 3-month | 0.651 | 0.644 | 0.654 | 0.646 | +0.083 | 0.497 | 0.489 |

### 2b. Calibration (quintiles of predicted P(target); predicted -> observed; monthly refit; live signals)

| scope | window | Q1 (lowest) | Q2 | Q3 | Q4 | Q5 (highest) |
|---|---|---|---|---|---|---|
| K6 | PRE+X | 0.11 -> 0.09 (n 708) | 0.30 -> 0.40 (n 708) | 0.44 -> 0.54 (n 708) | 0.53 -> 0.51 (n 708) | 0.64 -> 0.56 (n 708) |
| K6 | HOLD | 0.13 -> 0.07 (n 262) | 0.36 -> 0.45 (n 261) | 0.48 -> 0.49 (n 261) | 0.55 -> 0.55 (n 261) | 0.65 -> 0.56 (n 262) |
| K6 | L3M | 0.16 -> 0.12 (n 138) | 0.40 -> 0.51 (n 138) | 0.49 -> 0.45 (n 137) | 0.57 -> 0.54 (n 138) | 0.66 -> 0.56 (n 138) |
| P6 | PRE+X | 0.14 -> 0.13 (n 531) | 0.27 -> 0.35 (n 531) | 0.37 -> 0.45 (n 530) | 0.46 -> 0.46 (n 531) | 0.59 -> 0.52 (n 531) |
| P6 | HOLD | 0.15 -> 0.12 (n 198) | 0.26 -> 0.30 (n 198) | 0.39 -> 0.45 (n 197) | 0.49 -> 0.54 (n 198) | 0.60 -> 0.54 (n 198) |
| P6 | L3M | 0.16 -> 0.13 (n 110) | 0.27 -> 0.27 (n 109) | 0.40 -> 0.37 (n 109) | 0.50 -> 0.54 (n 109) | 0.61 -> 0.58 (n 109) |
| U6 | PRE+X | 0.12 -> 0.09 (n 116) | 0.22 -> 0.21 (n 115) | 0.38 -> 0.61 (n 115) | 0.50 -> 0.62 (n 115) | 0.63 -> 0.41 (n 116) |
| U6 | HOLD | 0.14 -> 0.05 (n 42) | 0.24 -> 0.14 (n 42) | 0.43 -> 0.44 (n 41) | 0.54 -> 0.60 (n 42) | 0.64 -> 0.62 (n 42) |
| H6 | PRE+X | 0.11 -> 0.08 (n 296) | 0.30 -> 0.46 (n 295) | 0.42 -> 0.50 (n 296) | 0.50 -> 0.51 (n 295) | 0.63 -> 0.57 (n 296) |
| H6 | HOLD | 0.13 -> 0.12 (n 108) | 0.35 -> 0.47 (n 108) | 0.49 -> 0.61 (n 107) | 0.57 -> 0.60 (n 108) | 0.68 -> 0.60 (n 108) |
| H6 | L3M | 0.15 -> 0.22 (n 55) | 0.40 -> 0.54 (n 54) | 0.52 -> 0.56 (n 55) | 0.60 -> 0.63 (n 54) | 0.70 -> 0.58 (n 55) |
| M6 | PRE+X | 0.20 -> 0.23 (n 328) | 0.38 -> 0.54 (n 327) | 0.46 -> 0.53 (n 328) | 0.53 -> 0.53 (n 327) | 0.63 -> 0.52 (n 328) |
| M6 | HOLD | 0.24 -> 0.31 (n 124) | 0.43 -> 0.52 (n 123) | 0.50 -> 0.52 (n 123) | 0.56 -> 0.50 (n 123) | 0.64 -> 0.55 (n 124) |
| M6 | L3M | 0.26 -> 0.36 (n 67) | 0.43 -> 0.49 (n 67) | 0.50 -> 0.52 (n 66) | 0.55 -> 0.58 (n 67) | 0.63 -> 0.51 (n 67) |
| A6 | PRE+X | 0.22 -> 0.36 (n 466) | 0.32 -> 0.35 (n 465) | 0.38 -> 0.40 (n 465) | 0.45 -> 0.49 (n 465) | 0.59 -> 0.51 (n 466) |
| A6 | HOLD | 0.31 -> 0.36 (n 232) | 0.38 -> 0.50 (n 232) | 0.43 -> 0.46 (n 232) | 0.50 -> 0.50 (n 232) | 0.61 -> 0.54 (n 232) |
| A6 | L3M | 0.31 -> 0.38 (n 99) | 0.39 -> 0.52 (n 99) | 0.45 -> 0.51 (n 99) | 0.51 -> 0.46 (n 99) | 0.61 -> 0.51 (n 99) |
| POOL6 | PRE+X | 0.13 -> 0.13 (n 2572) | 0.32 -> 0.42 (n 2571) | 0.41 -> 0.49 (n 2572) | 0.49 -> 0.50 (n 2571) | 0.59 -> 0.53 (n 2572) |
| POOL6 | HOLD | 0.19 -> 0.16 (n 965) | 0.40 -> 0.42 (n 964) | 0.46 -> 0.52 (n 964) | 0.52 -> 0.54 (n 964) | 0.60 -> 0.56 (n 964) |
| POOL6 | L3M | 0.22 -> 0.19 (n 487) | 0.41 -> 0.42 (n 486) | 0.47 -> 0.51 (n 486) | 0.53 -> 0.51 (n 486) | 0.60 -> 0.57 (n 487) |

### 2c. The policies on the STACK (D6 engine at live lots; $k/wk (MDE); skipped-signal base P&L beside) - real model, then the placebo draws

| scope | refit | q | action | PRE | X' | L3M | L6M | HOLD | acted-on signals/wk (L6M) | base $ of acted-on signals $k/wk | label-shuffled L6M: mean [min, max] (n) | feature-shuffled L6M: mean [min, max] (n) | real L6M rank among the 9 shuffles |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K6 | M | 10% | skip | +0.2 (0.7)~ | +0.2 (0.3)~ | -0.0 (0.4)~ | +0.3 (0.9)~ | +0.2 (0.8)~ | 2.4 | -0.1 | -0.2 [-0.4, +0.2] (6) | -0.1 [-0.3, +0.1] (3) | 1.00 of 9 |
| K6 | M | 10% | x0.5 | -0.2 (0.5)~ | +0.0 (0.1)~ | +0.0 (0.0)~ | +0.2 (0.6)~ | +0.2 (0.5)~ | 2.4 | -0.1 | -0.1 [-0.4, +0.0] (6) | +0.1 [-0.0, +0.2] (3) | 1.00 of 9 |
| K6 | M | 20% | skip | +0.3 (1.2)~ | +0.0 (0.6)~ | +1.3 (1.8)~ | +0.8 (1.3)~ | +0.7 (1.2)~ | 6.9 | -0.5 | +0.2 [-0.4, +0.9] (6) | -0.4 [-0.6, -0.1] (3) | 0.89 of 9 |
| K6 | M | 20% | x0.5 | +0.1 (0.7)~ | +0.0 (0.1)~ | +0.0 (0.7)~ | +0.4 (0.9)~ | +0.6 (1.1)~ | 6.9 | -0.5 | -0.0 [-0.3, +0.6] (6) | -0.2 [-0.6, -0.0] (3) | 0.89 of 9 |
| K6 | M | 30% | skip | +0.3 (1.6)~ | -0.4 (1.4)~ | +1.7 (2.4)~ | +0.7 (2.6)~ | +0.6 (2.3)~ | 9.8 | -0.4 | -0.6 [-1.4, -0.1] (6) | -1.1 [-1.9, -0.7] (3) | 1.00 of 9 |
| K6 | M | 30% | x0.5 | -0.1 (1.0)~ | -0.1 (0.7)~ | +0.9 (2.4)~ | -0.6 (2.5)~ | -0.3 (2.3)~ | 9.8 | -0.4 | -0.2 [-0.7, +0.5] (6) | -1.0 [-1.7, -0.3] (3) | 0.33 of 9 |
| K6 | Q | 20% | skip | +0.4 (1.2)~ | +0.0 (0.4)~ | +1.3 (1.8)~ | +0.5 (1.7)~ | +0.5 (1.4)~ | 7.2 | -0.5 | - | - | - |
| K6 | Q | 20% | x0.5 | +0.1 (0.7)~ | -0.0 (0.1)~ | +0.0 (0.7)~ | +0.4 (0.9)~ | +0.6 (1.1)~ | 7.2 | -0.5 | - | - | - |
| P6 | M | 10% | skip | +0.2 (2.5)~ | -0.7 (1.2)~ | -0.5 (3.3)~ | -0.8 (2.0)~ | -0.3 (1.9)~ | 2.3 | +0.5 | -1.6 [-4.0, +1.8] (6) | -0.5 [-3.5, +2.6] (3) | 0.56 of 9 |
| P6 | M | 10% | x0.5 | +0.2 (1.3)~ | -0.4 (0.6)~ | -0.5 (2.4)~ | -0.5 (1.3)~ | -0.3 (1.2)~ | 2.3 | +0.5 | -1.1 [-4.2, +1.0] (6) | -0.7 [-2.2, +0.4] (3) | 0.56 of 9 |
| P6 | M | 20% | skip | +0.5 (3.9)~ | -1.6 (3.7)~ | -4.8 (5.5)~ | -3.5 (4.1)~ | -2.8 (3.7)~ | 7.4 | +2.1 | -3.0 [-6.6, +3.0] (6) | -5.8 [-7.6, -2.3] (3) | 0.56 of 9 |
| P6 | M | 20% | x0.5 | -0.4 (2.9)~ | -1.0 (2.0)~ | -2.6 (3.5)~ | -2.0 (2.5)~ | -1.7 (2.2)~ | 7.4 | +2.1 | -2.7 [-4.8, +1.5] (6) | -3.9 [-6.9, -0.2] (3) | 0.67 of 9 |
| P6 | M | 30% | skip | -1.8 (4.7)~ | -3.4 (5.7)~ | -4.9 (8.7)~ | -4.6 (5.7)~ | -4.6 (5.4)~ | 10.1 | +3.2 | -7.9 [-11.9, +0.9] (6) | -7.6 [-10.3, -2.3] (3) | 0.78 of 9 |
| P6 | M | 30% | x0.5 | -1.3 (3.2)~ | -2.0 (3.1)~ | -2.2 (4.9)~ | -2.7 (3.2)~ | -2.4 (3.0)~ | 10.1 | +3.2 | -5.2 [-7.6, -1.2] (6) | -4.9 [-7.8, -0.5] (3) | 0.78 of 9 |
| P6 | Q | 20% | skip | -0.4 (3.9)~ | +0.3 (2.5)~ | -2.5 (5.0)~ | -3.1 (3.9)~ | -2.8 (3.4)~ | 7.4 | +2.0 | - | - | - |
| P6 | Q | 20% | x0.5 | -0.9 (2.8)~ | +0.2 (1.3)~ | -0.4 (2.2)~ | -1.4 (2.0)~ | -1.3 (1.8)~ | 7.4 | +2.0 | - | - | - |
| U6 | M | 10% | skip | +0.1 (0.7)~ | -0.2 (0.5)~ | +0.5 (1.3)~ | +0.2 (0.7)~ | +0.2 (0.6)~ | 0.5 | -0.2 | -0.3 [-0.9, +0.3] (6) | +0.2 [+0.0, +0.4] (3) | 0.78 of 9 |
| U6 | M | 10% | x0.5 | +0.1 (0.4)~ | -0.1 (0.2)~ | +0.2 (0.7)~ | +0.1 (0.3)~ | +0.1 (0.3)~ | 0.5 | -0.2 | -0.1 [-0.5, +0.1] (6) | +0.1 [+0.0, +0.3] (3) | 0.78 of 9 |
| U6 | M | 20% | skip | +0.3 (1.1)~ | -0.3 (0.6)~ | +0.6 (1.3)~ | +0.3 (0.7)~ | +0.3 (0.6)~ | 0.9 | -0.3 | -0.3 [-1.0, +0.4] (6) | +0.2 [+0.0, +0.4] (3) | 0.67 of 9 |
| U6 | M | 20% | x0.5 | +0.1 (0.6)~ | -0.2 (0.3)~ | +0.3 (0.7)~ | +0.2 (0.3)~ | +0.2 (0.3)~ | 0.9 | -0.3 | -0.1 [-0.6, +0.2] (6) | +0.1 [+0.0, +0.3] (3) | 0.78 of 9 |
| U6 | M | 30% | skip | -0.0 (1.3)~ | -0.7 (0.9)~ | +0.6 (1.3)~ | +0.7 (1.0)~ | +0.7 (0.9)~ | 1.6 | -0.7 | -0.3 [-1.1, +0.2] (6) | +0.2 [+0.1, +0.3] (3) | 1.00 of 9 |
| U6 | M | 30% | x0.5 | -0.0 (0.7)~ | -0.3 (0.5)~ | +0.3 (0.7)~ | +0.3 (0.5)~ | +0.4 (0.5)~ | 1.6 | -0.7 | -0.1 [-0.6, +0.1] (6) | +0.2 [+0.1, +0.3] (3) | 1.00 of 9 |
| U6 | Q | 20% | skip | -0.0 (1.2)~ | -0.2 (0.5)~ | +0.5 (1.3)~ | +0.2 (0.7)~ | +0.2 (0.6)~ | 1.1 | -0.2 | - | - | - |
| U6 | Q | 20% | x0.5 | -0.0 (0.6)~ | -0.1 (0.2)~ | +0.2 (0.7)~ | +0.1 (0.3)~ | +0.1 (0.3)~ | 1.1 | -0.2 | - | - | - |
| H6 | M | 10% | skip | +0.0 (0.4)~ | +0.2 (0.2)~ | -0.4 (1.0)~ | -0.3 (0.8)~ | -0.3 (0.7)~ | 1.0 | +0.3 | +0.0 [-0.2, +0.3] (6) | -0.1 [-0.2, -0.1] (3) | 0.00 of 9 |
| H6 | M | 10% | x0.5 | +0.1 (0.2)~ | +0.1 (0.2)~ | -0.2 (0.5)~ | -0.1 (0.4)~ | -0.1 (0.3)~ | 1.0 | +0.3 | -0.0 [-0.3, +0.1] (6) | -0.1 [-0.1, -0.0] (3) | 0.22 of 9 |
| H6 | M | 20% | skip | +0.0 (0.6)~ | -0.1 (0.5)~ | +0.6 (2.5)~ | -0.2 (1.6)~ | -0.1 (1.4)~ | 2.8 | +0.2 | -0.5 [-2.3, +0.0] (6) | -0.8 [-0.9, -0.7] (3) | 0.78 of 9 |
| H6 | M | 20% | x0.5 | +0.1 (0.3)~ | +0.0 (0.3)~ | +0.3 (1.2)~ | -0.1 (0.8)~ | -0.1 (0.7)~ | 2.8 | +0.2 | -0.3 [-1.4, +0.1] (6) | -0.4 [-0.5, -0.3] (3) | 0.67 of 9 |
| H6 | M | 30% | skip | -0.1 (1.2)~ | -0.9 (1.4)~ | -0.0 (4.7)~ | -0.5 (2.6)~ | -0.0 (2.4)~ | 4.1 | +0.5 | -0.9 [-2.3, +0.1] (6) | -1.7 [-2.4, -1.0] (3) | 0.67 of 9 |
| H6 | M | 30% | x0.5 | -0.1 (0.6)~ | -0.3 (0.7)~ | +0.0 (2.3)~ | -0.3 (1.2)~ | -0.1 (1.1)~ | 4.1 | +0.5 | -0.3 [-1.2, +0.2] (6) | -0.7 [-1.0, -0.3] (3) | 0.67 of 9 |
| H6 | Q | 20% | skip | +0.1 (0.7)~ | -0.2 (0.5)~ | +0.6 (2.4)~ | -0.1 (1.5)~ | -0.0 (1.3)~ | 2.8 | +0.1 | - | - | - |
| H6 | Q | 20% | x0.5 | +0.1 (0.3)~ | -0.1 (0.2)~ | +0.3 (1.2)~ | -0.0 (0.8)~ | -0.0 (0.7)~ | 2.8 | +0.1 | - | - | - |
| M6 | M | 10% | skip | -0.2 (0.3)~ | +0.1 (0.6)~ | -0.3 (0.6)~ | -0.6 (1.1)~ | -0.5 (0.9)~ | 1.5 | +0.4 | -0.1 [-0.7, +0.7] (6) | -0.2 [-0.5, +0.1] (3) | 0.11 of 9 |
| M6 | M | 10% | x0.5 | +0.1 (0.5)~ | +0.1 (0.3)~ | -0.0 (0.1)~ | -0.3 (0.6)~ | -0.3 (0.6)~ | 1.5 | +0.4 | -0.1 [-0.7, +0.0] (6) | -0.1 [-0.1, +0.0] (3) | 0.11 of 9 |
| M6 | M | 20% | skip | -0.2 (0.8)~ | +0.0 (0.9)~ | -1.1 (1.1)~ | -1.1 (1.3)~ | -0.9 (1.1)~ | 2.6 | +0.7 | -0.3 [-0.9, +0.5] (6) | -0.4 [-0.5, -0.4] (3) | 0.00 of 9 |
| M6 | M | 20% | x0.5 | +0.1 (0.6)~ | -0.0 (0.4)~ | -0.1 (0.4)~ | -0.3 (0.7)~ | -0.3 (0.6)~ | 2.6 | +0.7 | -0.3 [-0.6, -0.0] (6) | -0.1 [-0.1, -0.0] (3) | 0.33 of 9 |
| M6 | M | 30% | skip | -0.8 (1.3)~ | +0.1 (1.2)~ | -0.5 (1.9)~ | -0.8 (1.6)~ | -0.8 (1.5)~ | 4.1 | +0.4 | -0.7 [-1.6, +0.1] (6) | -1.0 [-1.7, -0.4] (3) | 0.56 of 9 |
| M6 | M | 30% | x0.5 | -0.1 (0.9)~ | +0.0 (0.5)~ | +0.2 (0.8)~ | -0.2 (0.8)~ | -0.2 (0.7)~ | 4.1 | +0.4 | -0.4 [-1.0, +0.0] (6) | -0.3 [-0.4, -0.2] (3) | 0.78 of 9 |
| M6 | Q | 20% | skip | +0.4 (0.8)~ | +0.5 (0.7)~ | -0.3 (0.9)~ | -0.7 (1.2)~ | -0.8 (1.1)~ | 2.6 | +0.5 | - | - | - |
| M6 | Q | 20% | x0.5 | +0.3 (0.6)~ | +0.1 (0.3)~ | -0.0 (0.1)~ | -0.3 (0.7)~ | -0.3 (0.6)~ | 2.6 | +0.5 | - | - | - |
| A6 | M | 10% | skip | +0.1 (0.9)~ | +0.1 (0.3)~ | +0.0 (0.0)~ | -0.0 (0.0)~ | +0.0 (0.0)~ | 0.2 | +0.0 | -0.1 [-0.2, +0.0] (6) | -0.0 [-0.0, -0.0] (3) | 0.56 of 9 |
| A6 | M | 10% | x0.5 | -0.1 (0.2)~ | +0.0 (0.2)~ | +0.0 (0.0)~ | -0.0 (0.0)~ | +0.0 (0.0)~ | 0.2 | +0.0 | -0.1 [-0.2, +0.0] (6) | -0.0 [-0.1, -0.0] (3) | 0.67 of 9 |
| A6 | M | 20% | skip | +0.2 (1.0)~ | -0.2 (0.6)~ | -0.1 (0.2)~ | -0.0 (0.1)~ | -0.0 (0.1)~ | 1.6 | +0.1 | -0.1 [-0.5, +0.1] (6) | +0.0 [-0.0, +0.1] (3) | 0.44 of 9 |
| A6 | M | 20% | x0.5 | -0.2 (0.3)~ | -0.1 (0.3)~ | -0.1 (0.2)~ | -0.1 (0.2)~ | -0.1 (0.1)~ | 1.6 | +0.1 | -0.1 [-0.3, +0.1] (6) | +0.0 [-0.1, +0.1] (3) | 0.44 of 9 |
| A6 | M | 30% | skip | +0.1 (1.0)~ | -0.0 (1.0)~ | +0.3 (0.8)~ | +0.5 (0.9)~ | +0.4 (0.8)~ | 4.1 | -0.2 | -0.2 [-0.6, +0.1] (6) | +0.1 [-0.0, +0.2] (3) | 1.00 of 9 |
| A6 | M | 30% | x0.5 | -0.2 (0.4)~ | -0.1 (0.4)~ | +0.2 (0.6)~ | +0.1 (0.3)~ | +0.1 (0.3)~ | 4.1 | -0.2 | -0.2 [-0.5, +0.1] (6) | -0.0 [-0.2, +0.1] (3) | 0.78 of 9 |
| A6 | Q | 20% | skip | +0.2 (0.9)~ | +0.1 (0.7)~ | -0.1 (0.2)~ | -0.1 (0.2)~ | -0.1 (0.1)~ | 1.0 | +0.3 | - | - | - |
| A6 | Q | 20% | x0.5 | -0.1 (0.3)~ | +0.0 (0.2)~ | -0.1 (0.2)~ | -0.1 (0.2)~ | -0.1 (0.2)~ | 1.0 | +0.3 | - | - | - |
| POOL6 | M | 10% | skip | +0.1 (2.3)~ | +0.3 (3.5)~ | -0.3 (1.7)~ | -0.8 (2.5)~ | -0.5 (2.3)~ | 7.9 | +1.0 | - | - | - |
| POOL6 | M | 10% | x0.5 | -0.0 (1.3)~ | +0.1 (1.9)~ | -0.3 (0.8)~ | -0.3 (1.3)~ | -0.2 (1.2)~ | 7.9 | +1.0 | - | - | - |
| POOL6 | M | 20% | skip | +1.8 (5.0)~ | -2.4 (5.2)~ | +3.1 (4.8)~ | -1.4 (5.3)~ | -1.2 (4.7)~ | 20.0 | +1.1 | - | - | - |
| POOL6 | M | 20% | x0.5 | +0.1 (3.2)~ | -1.2 (2.6)~ | +1.1 (2.1)~ | -0.6 (2.7)~ | -0.3 (2.4)~ | 20.0 | +1.1 | - | - | - |
| POOL6 | M | 30% | skip | -1.5 (6.5)~ | -4.3 (8.4)~ | -0.4 (9.3)~ | -3.4 (7.0)~ | -2.2 (6.4)~ | 26.9 | +3.2 | - | - | - |
| POOL6 | M | 30% | x0.5 | -0.5 (3.7)~ | -1.9 (4.3)~ | -0.0 (5.3)~ | -1.8 (3.9)~ | -1.1 (3.5)~ | 26.9 | +3.2 | - | - | - |
| POOL6 | Q | 20% | skip | +1.1 (5.0)~ | -1.9 (6.6)~ | +1.5 (6.7)~ | -2.2 (5.6)~ | -1.8 (5.0)~ | 19.6 | +1.4 | -0.6 [-1.2, +0.4] (3) | -0.4 [-0.7, -0.2] (2) | 0.00 of 5 |
| POOL6 | Q | 20% | x0.5 | -0.2 (3.2)~ | -1.1 (3.2)~ | +0.9 (2.2)~ | -0.7 (2.7)~ | -0.4 (2.4)~ | 19.6 | +1.4 | -0.2 [-0.6, +0.3] (3) | -0.2 [-0.3, -0.0] (2) | 0.00 of 5 |

Of 84 real-model policy cells (7 scopes x 2 refits x 3 cut-offs x 2 actions), 18 are positive in both PRE and X'; of those 6 are also positive in L6M and HOLD, and 0 beat the L6M MDE.

### 2d. Extracted AND-sets (depth-3 tree, <= 6 leaves, fitted on PRE u X' to the model's bottom-20% membership; leaves with precision >= 30% and >= 15 low-P signals kept; applied to all windows) and the retained gain

**K6** - 4 rules, fires on 1200 signals in all history:
  - set.ahead20_set11_fresh > 0.5 AND set.ahead20_set8 <= 0.5 AND st.vwap_dist_pts_eth <= 40.87   [leaf: 44 low of 64]
  - set.ahead20_set11_fresh > 0.5 AND set.ahead20_set8 <= 0.5 AND st.vwap_dist_pts_eth > 40.87   [leaf: 18 low of 60]
  - set.ahead20_set11_fresh > 0.5 AND set.ahead20_set8 > 0.5 AND st.rv30m_vs_med20d <= 3.556   [leaf: 599 low of 639]
  - set.ahead20_set11_fresh > 0.5 AND set.ahead20_set8 > 0.5 AND st.rv30m_vs_med20d > 3.556   [leaf: 33 low of 59]
  - tree skip: PRE +0.8 (1.4)~ | X' +0.2 (0.6)~ | L3M +1.5 (1.8)~ | L6M +0.6 (1.8)~ | HOLD +0.5 (1.6)~; acted-on 7.9/wk, their base $ -0.5k/wk; the model's own bottom-20% skip: +0.8 (1.3)~ L6M / +0.7 (1.2)~ HOLD
  - tree x0.5: PRE +0.1 (0.7)~ | X' +0.0 (0.2)~ | L3M +0.1 (0.7)~ | L6M +0.4 (0.9)~ | HOLD +0.6 (1.1)~; acted-on 7.9/wk, their base $ -0.5k/wk; the model's own bottom-20% x0.5: +0.4 (0.9)~ L6M / +0.6 (1.1)~ HOLD
**P6** - 3 rules, fires on 709 signals in all history:
  - set.ahead20_set11_fresh <= 0.5 AND st.sig_rv_5m > 54.38 AND st.1h.rng_exp1 <= 1.687   [leaf: 28 low of 50]
  - set.ahead20_set11_fresh > 0.5 AND st.5m.ribbon_w <= 2.692   [leaf: 359 low of 371]
  - set.ahead20_set11_fresh > 0.5 AND st.5m.ribbon_w > 2.692   [leaf: 49 low of 68]
  - tree skip: PRE -0.2 (4.5)~ | X' -0.4 (2.9)~ | L3M -0.9 (3.8)~ | L6M -1.9 (3.6)~ | HOLD -1.7 (3.1)~; acted-on 4.5/wk, their base $ +1.2k/wk; the model's own bottom-20% skip: -3.5 (4.1)~ L6M / -2.8 (3.7)~ HOLD
  - tree x0.5: PRE -1.2 (3.6)~ | X' -0.3 (1.6)~ | L3M +0.0 (0.6)~ | L6M -0.8 (1.8)~ | HOLD -0.7 (1.6)~; acted-on 4.5/wk, their base $ +1.2k/wk; the model's own bottom-20% x0.5: -2.0 (2.5)~ L6M / -1.7 (2.2)~ HOLD
**U6** - 3 rules, fires on 238 signals in all history:
  - set.ahead20_set11_fresh > 0.5 AND st.15m.don20_w <= 4.209 AND st.1m.range_pos60 > 0.4522   [leaf: 26 low of 41]
  - set.ahead20_set11_fresh > 0.5 AND st.15m.don20_w > 4.209 AND st.5m.rsi14 <= 59.36   [leaf: 26 low of 49]
  - set.ahead20_set11_fresh > 0.5 AND st.15m.don20_w > 4.209 AND st.5m.rsi14 > 59.36   [leaf: 42 low of 50]
  - tree skip: PRE +0.3 (1.4)~ | X' -0.1 (1.0)~ | L3M +1.7 (2.2)~ | L6M +1.2 (1.4)~ | HOLD +1.1 (1.2)~; acted-on 1.5/wk, their base $ -1.2k/wk; the model's own bottom-20% skip: +0.3 (0.7)~ L6M / +0.3 (0.6)~ HOLD
  - tree x0.5: PRE +0.1 (0.7)~ | X' -0.1 (0.5)~ | L3M +0.8 (1.1)~ | L6M +0.6 (0.7)~ | HOLD +0.6 (0.6)~; acted-on 1.5/wk, their base $ -1.2k/wk; the model's own bottom-20% x0.5: +0.2 (0.3)~ L6M / +0.2 (0.3)~ HOLD
**H6** - 3 rules, fires on 575 signals in all history:
  - set.ahead20_set11_fresh > 0.5 AND st.15m.range_pos60 <= 0.3037 AND st.5m.macd_hist <= -0.012   [leaf: 52 low of 72]
  - set.ahead20_set11_fresh > 0.5 AND st.15m.range_pos60 <= 0.3037 AND st.5m.macd_hist > -0.012   [leaf: 211 low of 221]
  - set.ahead20_set11_fresh > 0.5 AND st.15m.range_pos60 > 0.3037   [leaf: 29 low of 72]
  - tree skip: PRE +0.3 (0.9)~ | X' -0.4 (1.1)~ | L3M +0.4 (3.9)~ | L6M -0.4 (2.2)~ | HOLD -0.3 (2.0)~; acted-on 3.9/wk, their base $ +0.4k/wk; the model's own bottom-20% skip: -0.2 (1.6)~ L6M / -0.1 (1.4)~ HOLD
  - tree x0.5: PRE +0.2 (0.4)~ | X' -0.2 (0.6)~ | L3M +0.2 (1.9)~ | L6M -0.2 (1.1)~ | HOLD -0.2 (0.9)~; acted-on 3.9/wk, their base $ +0.4k/wk; the model's own bottom-20% x0.5: -0.1 (0.8)~ L6M / -0.1 (0.7)~ HOLD
**M6** - 3 rules, fires on 388 signals in all history:
  - set.ahead20_set11_fresh <= 0.5 AND bk.spread_t>=3 <= 0.5 AND set.ahead20_set8 > 0.5   [leaf: 19 low of 40]
  - set.ahead20_set11_fresh > 0.5 AND st.1m.range_pos60 <= 0.3114   [leaf: 38 low of 40]
  - set.ahead20_set11_fresh > 0.5 AND st.1m.range_pos60 > 0.3114   [leaf: 182 low of 182]
  - tree skip: PRE -0.4 (0.7)~ | X' +0.4 (1.1)~ | L3M -0.5 (1.1)~ | L6M -1.6 (1.7)~ | HOLD -1.2 (1.6)~; acted-on 2.9/wk, their base $ +1.2k/wk; the model's own bottom-20% skip: -1.1 (1.3)~ L6M / -0.9 (1.1)~ HOLD
  - tree x0.5: PRE +0.1 (0.5)~ | X' +0.2 (0.5)~ | L3M -0.6 (1.6)~ | L6M -0.8 (1.0)~ | HOLD -0.7 (0.9)~; acted-on 2.9/wk, their base $ +1.2k/wk; the model's own bottom-20% x0.5: -0.3 (0.7)~ L6M / -0.3 (0.6)~ HOLD
**A6** - 4 rules, fires on 865 signals in all history:
  - eng.pb.run_bars <= 129.5 AND x_wd <= 5 AND bk.sw_ag120>=2 <= 0.5   [leaf: 123 low of 312]
  - eng.pb.run_bars <= 129.5 AND x_wd > 5 AND bk.sweep_with30>=4 <= 0.5   [leaf: 120 low of 191]
  - eng.pb.run_bars <= 129.5 AND x_wd > 5 AND bk.sweep_with30>=4 > 0.5   [leaf: 26 low of 76]
  - eng.pb.run_bars > 129.5 AND eng.pb.run_atr <= 1.63   [leaf: 16 low of 40]
  - tree skip: PRE +0.6 (1.0)~ | X' -0.3 (1.0)~ | L3M -1.1 (1.8)~ | L6M -1.1 (1.1) | HOLD -1.0 (1.0)~; acted-on 6.9/wk, their base $ +0.8k/wk; the model's own bottom-20% skip: -0.0 (0.1)~ L6M / -0.0 (0.1)~ HOLD
  - tree x0.5: PRE -0.3 (0.6)~ | X' -0.0 (0.5)~ | L3M -0.4 (0.8)~ | L6M -0.5 (0.7)~ | HOLD -0.4 (0.7)~; acted-on 6.9/wk, their base $ +0.8k/wk; the model's own bottom-20% x0.5: -0.1 (0.2)~ L6M / -0.1 (0.1)~ HOLD
**POOL6** - 3 rules, fires on 3137 signals in all history:
  - set.ahead20_set11_fresh > 0.5 AND set.ahead20_set8 <= 0.5 AND st.5m.macd_hist <= -0.1755   [leaf: 22 low of 59]
  - set.ahead20_set11_fresh > 0.5 AND set.ahead20_set8 <= 0.5 AND st.5m.macd_hist > -0.1755   [leaf: 244 low of 287]
  - set.ahead20_set11_fresh > 0.5 AND set.ahead20_set8 > 0.5   [leaf: 1933 low of 1952]
  - tree skip: PRE +1.5 (4.9)~ | X' -1.4 (4.7)~ | L3M +2.3 (7.5)~ | L6M -1.9 (5.9)~ | HOLD -1.6 (5.2)~; acted-on 20.4/wk, their base $ +1.1k/wk; the model's own bottom-20% skip: -2.2 (5.6)~ L6M / -1.8 (5.0)~ HOLD
  - tree x0.5: PRE -0.2 (3.2)~ | X' -0.8 (2.5)~ | L3M +1.3 (2.6)~ | L6M -0.6 (2.8)~ | HOLD -0.3 (2.5)~; acted-on 20.4/wk, their base $ +1.1k/wk; the model's own bottom-20% x0.5: -0.7 (2.7)~ L6M / -0.4 (2.4)~ HOLD

Reading: the tree is the 'simpler rule' the QUANT-LAYER asks for. For K6, P6, U6, H6, M6 and the pooled model the first split is a set-line flag (`set.ahead20_set11_fresh`, the 11-line set from the POI store; the live 8-line set is already skipped inside 20 pts by the base, but the NTE-1 flag and the SS-2 zone feature are not identical definitions, so some flagged signals remain in the base) - the learned model largely re-derives the ZONES skip family and then adds a second condition (HTF range position, MACD, Donchian width, VWAP distance). For A6 the splits are PB7's own state (regime-run age and size) and sweeps. Its retained stack gain is the row above; where the model's own gain is not above its shuffled twins the AND-set has nothing to retain.

## 3. Section D - the opposite side: size up x1.5 / take-only where P(target) is HIGHER (multiplier route only)

Same screen with the sign flipped (conjunction score min(t_PRE, t_X') of the RAISING of per-signal live-lot $); top 30 states per scope, same combination types, the top 15 per type per scope engine-run as x1.5 (lots = Max(1, Floor(lots x ER mult x 1.5 + 0.5)); the running-max governors see the larger multiplier, so day / week locks widen with it) and as take-only (skip the complement inside the scope). **A size-up changes the lots: the equal-risk frame is the LOT-MATCHED UNIFORM SCALING null - the same x1.5 on a random subset of the same size per book x session, or on ALL signals of the scope (rows U below) - and a size-up that does not beat it is STRUCTURE, not an edge.**

### 3a. The structure benchmark: x on EVERY live signal of the scope (no state), stack delta $k/wk (MDE)

| scope | action | PRE | X' | L3M | L6M | HOLD | contracts added (share of the scope's lots) |
|---|---|---|---|---|---|---|---|
| A6 | x0.5 | -0.6 (0.7)~ | -0.2 (0.8)~ | -0.6 (2.2)~ | -0.7 (1.4)~ | -0.7 (1.3)~ | -50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| A6 | x1.5 | +0.1 (0.4)~ | +0.1 (0.2)~ | +0.5 (1.9)~ | +0.2 (1.0)~ | +0.1 (0.9)~ | +50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| A6 | x2 | +0.9 (1.0)~ | +0.3 (0.8)~ | +2.3 (2.1) | +1.6 (1.4) | +1.3 (1.3) | +100% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| ALL | x0.5 | -10.9 (9.2) | -5.5 (6.9)~ | -21.8 (18.2) | -22.8 (13.1) | -21.0 (14.2) | -50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| ALL | x1.5 | +10.3 (10.5)~ | +3.2 (6.9)~ | +15.0 (17.1)~ | +18.6 (11.1) | +17.8 (12.2) | +50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| ALL | x2 | +20.9 (18.6) | +6.2 (13.3)~ | +28.7 (33.1)~ | +36.1 (20.7) | +34.5 (22.9) | +100% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| H6 | x0.5 | -0.8 (1.7)~ | +0.1 (1.6)~ | -5.2 (5.5)~ | -4.1 (3.0) | -3.7 (2.7) | -50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| H6 | x1.5 | +1.5 (1.9)~ | -0.4 (1.8)~ | +6.3 (6.7)~ | +5.5 (3.7) | +4.7 (3.4) | +50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| H6 | x2 | +2.5 (3.5)~ | -0.5 (3.3)~ | +11.5 (12.0)~ | +9.5 (6.6) | +8.3 (6.0) | +100% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| K6 | x0.5 | -1.2 (2.2)~ | -0.6 (1.9)~ | -2.6 (7.2)~ | -2.7 (4.3)~ | -2.1 (4.0)~ | -50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| K6 | x1.5 | +3.5 (3.2) | +1.1 (2.5)~ | +1.8 (6.7)~ | +2.3 (4.9)~ | +2.1 (4.8)~ | +50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| K6 | x2 | +3.9 (4.0)~ | +0.7 (3.3)~ | +3.8 (9.8)~ | +5.6 (6.4)~ | +4.5 (6.5)~ | +100% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| M6 | x0.5 | -0.4 (1.7)~ | +0.1 (1.6)~ | +0.2 (4.2)~ | -0.0 (2.3)~ | -0.0 (2.2)~ | -50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| M6 | x1.5 | +1.2 (2.0)~ | -0.6 (2.4)~ | +1.6 (6.3)~ | +1.4 (3.7)~ | +1.1 (3.6)~ | +50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| M6 | x2 | +1.9 (3.3)~ | -0.5 (3.3)~ | -0.1 (6.4)~ | +1.0 (4.2)~ | +1.0 (4.3)~ | +100% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| P6 | x0.5 | -6.6 (6.9)~ | -3.7 (5.1)~ | -14.7 (13.7) | -15.3 (9.8) | -14.4 (10.2) | -50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| P6 | x1.5 | +3.4 (7.0)~ | +2.1 (4.4)~ | +6.2 (15.3)~ | +9.3 (9.0) | +9.7 (8.6) | +50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| P6 | x2 | +9.3 (13.1)~ | +4.1 (9.2)~ | +13.6 (24.7)~ | +18.5 (15.8) | +19.1 (15.7) | +100% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| U6 | x0.5 | -1.2 (2.3)~ | -1.1 (2.0)~ | +1.1 (3.8)~ | +0.0 (2.5)~ | -0.2 (2.4)~ | -50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| U6 | x1.5 | +1.2 (2.3)~ | +1.1 (2.0)~ | -1.1 (3.8)~ | -0.0 (2.5)~ | +0.2 (2.4)~ | +50% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |
| U6 | x2 | +2.4 (4.5)~ | +2.1 (4.0)~ | -2.3 (7.7)~ | -0.0 (5.0)~ | +0.3 (4.9)~ | +100% (min-1 and half-up rounding make the realised change smaller at 1-2 lot books) |

### 3b. The flip, by family

| family | action | cells run | selected (PRE>0 and X'>0) | mean PRE | mean X' | mean L6M | mean HOLD | share L6M>0 | share L6M>MDE | mean L6M EXCESS over the lot-matched uniform null | share with EXCESS>0 in L6M and HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|
| single | x1.5 | 210 | 202 | +1.2 | +0.9 | +1.2 | +1.2 | 72% | 6%  | +0.2 | 46% |
| single | take | 210 | 4 | +0.3 | +0.9 | -7.2 | -6.1 | 0% | 0%  | +nan | nan% |
| pair | x1.5 | 105 | 104 | +1.1 | +0.9 | +0.5 | +0.6 | 66% | 2%  | +0.2 | 46% |
| pair | take | 105 | 0 | - | - | - | - | 0% | 0%  | +nan | nan% |
| triple | x1.5 | 105 | 105 | +0.9 | +0.8 | +0.3 | +0.3 | 61% | 2%  | +0.1 | 47% |
| triple | take | 105 | 0 | - | - | - | - | 0% | 0%  | +nan | nan% |
| k-of-n | x1.5 | 30 | 30 | +3.1 | +2.2 | +2.7 | +2.6 | 100% | 10%  | +0.6 | 67% |
| k-of-n | take | 30 | 10 | +0.3 | +0.8 | -0.6 | -0.1 | 30% | 0%  | +nan | nan% |
| four-legged | x1.5 | 36 | 33 | +0.5 | +0.8 | +0.0 | +0.1 | 55% | 0%  | -0.2 | 45% |
| four-legged | take | 36 | 0 | - | - | - | - | 0% | 0%  | +nan | nan% |
| nested | x1.5 | 26 | 21 | +0.4 | +0.6 | -0.2 | +0.0 | 29% | 0%  | -0.3 | 29% |
| nested | take | 26 | 0 | - | - | - | - | 0% | 0%  | +nan | nan% |

### 3c. The reported top rule per family and action (chosen on min(PRE, X') stack delta; one recent look) with the PLACEBO RANKS (fraction of 24 draws the real L6M delta beats; random same-rate per book x session = the lot-matched null / pattern shifted in time)

| family | action | scope | rule | n PRE/X' sig | PRE | X' | L3M | L6M | HOLD | fired/wk (L6M) | base $ of the affected signals $k/wk | placebo rank rand / shift | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| four | take | K6 | st.15m.bbw_pct100>=0.97 AND evt.rthgap_abs>=40 AND st.gap_atrd>=0.2374 | 71/29 | -1.4 (2.3)~ | +0.2 (3.0)~ | +2.0 (4.5)~ | -0.6 (4.0)~ | -0.7 (3.6)~ | 21.1 | +0.8 | 0.25 / 0.12 | NO |
| four | x1.5 | ALL | st.1h.swing_run>=2 AND evt.rthgap_abs>=20 AND st.open_drive30>=0.1828 | 339/115 | +1.3 (3.5)~ | +1.5 (3.3)~ | -0.2 (5.4)~ | +1.5 (4.2)~ | +1.4 (3.8)~ | 6.6 | +6.9 | 0.96 / 0.88 | LEAD (placebo not beaten) |
| kofn | take | H6 | st.f60_vs_med>=1.398 OR st.1h.range_pos60>=0.462 OR st.5m.adx14>=34.82 | 444/184 | +0.6 (2.5)~ | +0.7 (2.3)~ | -1.0 (6.7)~ | -1.7 (3.6)~ | -1.4 (3.4)~ | 5.4 | +1.7 | 1.00 / 1.00 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| kofn | x1.5 | ALL | >= 3.0 of [st.f60_vs_med>=1.398; st.sig_delta10_s>=66; st.sig_delta60_s>=286; st.1h.swing_run>=2; st.15m.st10_3_age<=6; st.5m.range_pos60>=0.451; s... | 1600/652 | +8.4 (6.3) | +6.2 (5.8) | +2.6 (7.4)~ | +5.0 (7.2)~ | +5.6 (6.7)~ | 23.1 | +12.1 | 0.88 / 0.96 | LEAD (placebo not beaten) |
| nested | take | A6 | nest.setline_20_30 AND eng.pb.run_atr<=2 | 41/41 | -1.0 (1.9)~ | +0.0 (2.2)~ | -1.4 (4.4)~ | -1.3 (2.7)~ | -1.3 (2.4)~ | 36.8 | +1.6 | 0.17 / 0.12 | NO |
| nested | x1.5 | ALL | nest.setline_20_30 AND px.ext.5m.ema20>=1.5 | 238/137 | +1.3 (2.5)~ | +1.9 (2.8)~ | -0.0 (8.4)~ | +1.3 (5.1)~ | +1.5 (4.5)~ | 3.7 | +2.4 | 0.71 / 0.96 | LEAD (placebo not beaten) |
| pair | take | A6 | eng.pb.run_bars<=30 AND eng.pb.run_atr<=2 | 400/186 | -0.2 (1.7)~ | -0.2 (1.4)~ | -1.2 (3.7)~ | -0.7 (2.9)~ | -0.5 (2.6)~ | 31.8 | +0.9 | 0.21 / 0.46 | NO |
| pair | x1.5 | ALL | st.5m.er20>=0.3857 AND px.ext.5m.ema20>=1.5 | 1858/702 | +5.5 (10.5)~ | +3.7 (6.6)~ | +10.4 (21.6)~ | +13.8 (11.7) | +14.1 (12.3) | 27.4 | +36.1 | 1.00 / 1.00 | CONFIRMED-RECENT by the prereg gates - NOT promoted: size-up = governor-coupled structure, no RW survivor, mean/SD not above base (3e) |
| single | take | H6 | st.15m.hma_slope>=0.4067 | 241/111 | +0.4 (2.9)~ | +0.8 (2.8)~ | -6.6 (8.5)~ | -6.1 (5.5) | -5.1 (5.1)~ | 13.7 | +5.8 | 0.96 / 0.96 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) |
| single | x1.5 | ALL | st.1h.swing_run>=2 | 2339/849 | +5.3 (7.4)~ | +3.6 (6.5)~ | -7.4 (19.3)~ | +0.4 (13.4)~ | +1.6 (12.0)~ | 32.6 | +14.1 | 0.12 / 0.17 | LEAD (placebo not beaten) |
| triple | take | A6 | eng.pb.run_bars<=30 AND eng.pb.run_atr<=2 AND eng.all.sigbar_vol_rel>=2 | 121/63 | -0.4 (1.9)~ | -0.5 (1.5)~ | -1.0 (3.8)~ | -0.9 (3.1)~ | -0.6 (2.8)~ | 36.3 | +1.4 | 0.25 / 0.42 | NO |
| triple | x1.5 | ALL | st.15m.st10_3_age<=6 AND px.struct.1h.with AND px.ext.5m.ema20>=1.5 | 348/135 | +3.3 (3.0) | +2.9 (3.3)~ | +0.4 (4.5)~ | +3.0 (5.5)~ | +2.4 (5.6)~ | 4.5 | +6.6 | 0.96 / 1.00 | LEAD |

### 3d. Per D6 book: the best x1.5 per scope on min(PRE, X')

| scope | family | rule | n PRE/X' | PRE | X' | L3M | L6M | HOLD | fired/wk | base $ affected $k/wk | tier (no placebo) | uniform x1.5 on the whole scope L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | kof3of10 | >= 3.0 of [st.f60_vs_med>=1.398; st.sig_delta10_s>=66; st.sig_delta60_s>=286; st.1h.swing_run>=2; st.15m.st10_3_age<=6; st.5m.range_pos60>=0.451; s... | 1600/652 | +8.4 (6.3) | +6.2 (5.8) | +2.6 (7.4)~ | +5.0 (7.2)~ | +5.6 (6.7)~ | 23.1 | +12.1 | LEAD (no placebo run) | +18.6 (11.1) |
| K6 | kof2of10 | >= 2.0 of [st.15m.bbw_pct100>=0.97; st.15m.rsi14>=69.25; px.late.atDayExtreme5_run100; st.rs_nq_rty_15m>=17.93; st.sig_er30<=0.04075; px.loc.OR30.m... | 1379/467 | +2.4 (2.9)~ | +2.0 (2.4)~ | +1.4 (5.1)~ | +2.4 (3.6)~ | +1.8 (4.1)~ | 18.2 | +4.1 | LEAD (no placebo run) | +2.3 (4.9)~ |
| P6 | kof3of10 | >= 3.0 of [st.sig_delta60_s>=286; st.sig_delta10_s>=66; st.5m.range_pos60>=0.451; px.struct.1h.with; st.sig_absorb10_s>=140.3; st.sig_rv_5m>=24.04;... | 557/175 | +5.6 (4.5) | +4.4 (4.5)~ | -0.5 (8.9)~ | +0.3 (5.9)~ | +0.2 (5.3)~ | 8.2 | +5.2 | LEAD (no placebo run) | +9.3 (9.0) |
| U6 | kof3of10 | >= 3.0 of [st.days_since_trend>=5; st.1m.adx14>=32.39; st.1h.er20<=0.04579; st.1m.rsi14>=68.17; st.sig_er120<=0.03867; st.4h.adx14>=34.44; st.1m.er... | 254/108 | +1.5 (1.6)~ | +1.4 (1.4) | -0.3 (3.4)~ | +0.7 (2.1)~ | +0.9 (2.2)~ | 3.3 | +1.8 | LEAD (no placebo run) | -0.0 (2.5)~ |
| H6 | kof2of10 | >= 2.0 of [st.f60_vs_med>=1.398; st.1h.range_pos60>=0.462; st.5m.adx14>=34.82; st.open_drive30>=0.1828; st.prev_er_rth<=0.04948; px.ext.1m.ema200>=... | 543/235 | +2.1 (1.8) | +1.0 (1.5)~ | +5.4 (5.9)~ | +3.9 (3.6) | +3.6 (3.2) | 9.4 | +7.2 | LEAD (no placebo run) | +5.5 (3.7) |
| M6 | kof3of10 | >= 3.0 of [st.f60_vs_med>=1.398; st.1d.atr_ratio<=0.9356; eng.mv.vote>=5; px.struct.1h.with; st.1h.rsi14>=60.22; stk.nbooks_same>=4; st.rv30_ann<=1... | 534/231 | +1.5 (2.0)~ | +1.5 (2.0)~ | -0.5 (4.0)~ | +0.2 (2.7)~ | +0.1 (2.8)~ | 8.5 | -0.1 | LEAD (no placebo run) | +1.4 (3.7)~ |
| A6 | single | cal.earn.amc_post960 | 187/66 | +0.1 (0.2)~ | +0.1 (0.2)~ | +0.0 (0.0)~ | -0.0 (0.1)~ | -0.1 (0.2)~ | 3.1 | -0.4 | FLIPPED (gain in PRE+X', loss in L6M/HOLD) | +0.2 (1.0)~ |

### 3e. The one D cell that beats BOTH placebos - anatomy (the equal-risk frame, the governor coupling, the neighbourhood)

`D|91|x1.5` = size up x1.5 (on top of the ER multiplier) when the 5-min ER20 >= 0.386 (the 75th percentile of ER on PRE u X') AND the signal is >= 1.5 ATR14(5m) beyond the 5-min EMA20 in the trade direction (`px.ext.5m.ema20>=1.5`), all six books: stack +5.5 (10.5)~ PRE | +3.7 (6.6)~ X' | +10.4 (21.6)~ L3M | +13.8 (11.7) L6M | +14.1 (12.3) HOLD, 27 signals/wk (18% of live signals). It beats the random same-rate size-up (rank 1.00 of 24; 95th percentile of the draws +5.2k) and the time-shifted pattern (1.00; +6.5k), and 10 of 12 quarters are positive. **But:** (1) it is the existing ER sizer taken one step further (ER >= 0.30 is already x1.5 in D6; this is x2.25 at the high-ER end), and the ER-only version (`ER>=0.30`, x1.5 on top) gives +17.5k L6M / +7.5k PRE / +2.2k X' - larger than the pair; the extension leg adds nothing the ER leg does not already carry; (2) **64% of the L6M gain is the governors**: with the lots multiplied but the day / week locks left at the planned-lot multiple the same rule earns +4.9 (14.7)~ L6M (uniform x1.5 on every signal, lots only: +3.5 (17.4)~ vs +18.6 (11.1) coupled), the same lock-widening mechanism SS-2 found for the ER sizer; (3) **the equal-risk frame**: weekly SD rises with the mean (table below), the L6M mean / SD ratio is unchanged or lower than the base's, i.e. more lots, not more edge; (4) the selection-window deltas are inside their MDE (PRE +5.5 (10.5)~, X' +3.7 (6.6)~) and the family's Romano-Wolf stepdown has 0 survivors among 105 pairs; the White RC p of 0.002 in 6a is against a zero null, which a size-up fails by construction (the uniform x1.5 earns +18.6k) - the placebo rank is the right test and it is the only one passed. Verdict: **LEAD for the ER-sizer family (a larger top multiplier), STRUCTURE for D6's purposes; not a no-trade / take-more state.** Post-hoc: the family 'ER sizer' was chosen by SS-2 after looking at L6M / HOLD, so this is a refinement of a post-hoc rule.

Neighbourhood (stack delta L6M / HOLD $k/wk, x1.5 coupled; rows = ER threshold, columns = extension leg; 2nd number lots-only/decoupled L6M):

| ER >= | ext none | ext >= 1.5 ATR | ext >= 2 ATR | ext >= 3 ATR |
|---|---|---|---|---|
| 0.300 | +17.5 / +17.7 (+0.8 lots-only) | +19.2 / +18.5 (+3.5 lots-only) | +12.3 / +11.7 (+7.2 lots-only) | +3.5 / +2.9 (+5.0 lots-only) |
| 0.350 | +13.0 / +12.8 (+4.9 lots-only) | +16.1 / +15.7 (+5.6 lots-only) | +9.8 / +9.6 (+4.3 lots-only) | +3.0 / +2.5 (+4.6 lots-only) |
| 0.386 | +11.9 / +11.5 (+4.2 lots-only) | +13.8 / +14.1 (+4.9 lots-only) | +7.9 / +8.1 (+2.8 lots-only) | +2.6 / +2.1 (+4.6 lots-only) |
| 0.450 | +8.7 / +9.2 (+5.3 lots-only) | +9.3 / +10.3 (+5.0 lots-only) | +5.3 / +5.8 (+2.7 lots-only) | +1.1 / +1.0 (+2.8 lots-only) |
| 0.550 | +4.2 / +4.9 (+4.1 lots-only) | +3.9 / +4.9 (+4.2 lots-only) | +3.6 / +4.3 (+4.4 lots-only) | -0.6 / -0.3 (+1.2 lots-only) |

Mean of the 8 neighbours of the chosen cell, L6M coupled: +10.3k (all 8 of 8 positive); by book (center rule, coupled L6M): K6 +3.4, P6 +6.7, U6 -0.2, H6 +2.5, M6 +1.4, A6 -0.0; x2.0 on the pair: +25.0 (21.7) L6M (lots only +7.7 (22.8)~).

Risk beside the size-ups (weekly P&L of the stack, $k): mean / SD / mean-over-SD / max drawdown of the weekly cumulative / sum of the 20 worst weeks

| variant | L6M | HOLD | PRE |
|---|---|---|---|
| BASE (D6 composite) | 43.5 / 42.9 / 1.01 / 21 / 417 | 40.5 / 52.3 / 0.78 / 101 / 178 | 24.7 / 55.7 / 0.44 / 223 / -836 |
| uniform x1.5 all signals, coupled | 62.1 / 60.4 / 1.03 / 37 / 592 | 58.3 / 74.3 / 0.78 / 146 / 244 | 35.0 / 85.2 / 0.41 / 331 / -1307 |
| uniform x1.5 all signals, lots only (governors unchanged) | 47.0 / 59.0 / 0.80 / 38 / 325 | 46.0 / 69.1 / 0.67 / 94 / 21 | 24.4 / 67.9 / 0.36 / 249 / -1126 |
| ER>=0.30 x1.5 (ER sizer high multiplier 1.5 -> 2.25), coupled | 61.0 / 58.9 / 1.04 / 22 / 596 | 58.3 / 72.5 / 0.80 / 110 / 271 | 32.2 / 84.3 / 0.38 / 309 / -1391 |
| ER>=0.30 x1.5, lots only | 44.3 / 53.6 / 0.83 / 56 / 345 | 43.4 / 66.1 / 0.66 / 110 / 40 | 26.1 / 73.5 / 0.36 / 337 / -1254 |
| ER>=0.386 AND ext>=1.5 ATR x1.5, coupled (the D-pair rule) | 57.3 / 60.3 / 0.95 / 28 / 501 | 54.6 / 72.1 / 0.76 / 100 / 207 | 30.2 / 80.2 / 0.38 / 248 / -1326 |
| ER>=0.386 AND ext>=1.5 ATR x1.5, lots only | 48.4 / 60.0 / 0.81 / 59 / 354 | 45.9 / 70.3 / 0.65 / 118 / 50 | 25.5 / 69.5 / 0.37 / 298 / -1148 |

## 4. The states NTE-1 could not build - built from the engines' own recursions and the 1-s l2feat flow columns, with their maps (both edges)

Definitions (exact, computable live): `eng.kb.*` use the 3-min Keltner recursion of KB (EMA14 mid, Wilder ATR10, k = 1.0) on the signal's 3-min break bar (100% of KB signals reproduce an outside-band close); `eng.pe.*` use the PE arming event (EMA20(1m) touch against the 5-min ST(10,3) regime; trigger = break of the arming bar's extreme) and the last 5-min fractal swing leg (5,361 of 5,361 PE signals matched to an event); `eng.pb.*` (A6 = PB7) use the 1-min ST10 regime run (direction of the 10-min Supertrend), its extreme and start, ATR14(5m); `eng.mv.vote` = the signed count of the 5 vol-normalised lookbacks (15/30/60/120/240 min, |z| >= 0.5; the engine fires at 4 of 5; 5,141 of 5,167 MV signals reproduced as a fresh >=4 vote); `bk.sw_*` = NQ sweep counters over the trailing 60 / 120 / 15 / 5 s from the 1-s l2feat table at the decision second (sided: against = the sweep side opposes the signal). Cells: P(target) with the state vs without, live-lot signals, 'in% / out% (n in)', `*` = |z| >= 2 (binomial z of the difference), `**` = |z| >= 3.

### 4a. KB (K6) band-break closure

| state | scope | L3M | L6M | HOLD | PRE | X' | pts/ctr in vs out L6M |
|---|---|---|---|---|---|---|---|
| `eng.kb.break_rng<=0.25` | K6 | 43 / 43 (399) | 44 / 45 (685) | 42 / 43 (746) | 44 / 43 (1643) | 33 / 35 (507) | +2.1 / +3.0 |
| `eng.kb.break_rng<=0.5` | K6 | 43 / 44 (628) | 44 / 48 (1083) | 42 / 45 (1184) | 44 / 41 (2655) | 33 / 44 (845)* | +2.2 / +5.1 |
| `eng.kb.break_rng>=0.75` | K6 | - | 70 / 44 (10) | 64 / 42 (11) | 45 / 43 (20) | 42 / 34 (12) | +19.2 / +2.4 |
| `eng.kb.break_atr<=0.1` | K6 | 44 / 43 (169) | 46 / 43 (280) | 45 / 42 (306) | 46 / 43 (674) | 29 / 35 (192) | +2.8 / +2.4 |
| `eng.kb.break_atr<=0.25` | K6 | 43 / 44 (341) | 44 / 44 (586) | 43 / 42 (641) | 44 / 43 (1424) | 33 / 35 (419) | +2.0 / +2.9 |
| `eng.kb.break_atr<=0.5` | K6 | 43 / 46 (531) | 44 / 45 (908) | 42 / 43 (980) | 43 / 44 (2155) | 34 / 35 (667) | +2.4 / +2.8 |
| `eng.kb.break_atr>=1` | K6 | 50 / 43 (44) | 52 / 43 (88) | 49 / 42 (99) | 43 / 44 (214) | 34 / 34 (94) | +9.6 / +1.9 |
| `eng.kb.close_pos<=0.5` | K6 | 54 / 43 (26) | 50 / 44 (52) | 50 / 42 (58) | 43 / 44 (145) | 33 / 34 (42) | +1.7 / +2.5 |
| `eng.kb.close_pos<=0.75` | K6 | 50 / 41 (159) | 50 / 42 (287)* | 47 / 41 (325) | 44 / 43 (826) | 33 / 35 (244) | +8.3 / +0.7 |
| `eng.kb.close_pos>=0.9` | K6 | 40 / 45 (271) | 41 / 46 (447) | 40 / 44 (485) | 41 / 45 (1019) | 37 / 32 (366) | -0.7 / +4.4 |
| `eng.kb.band_wid_rel<=4` | K6 | - | - | - | 18 / 44 (28)** | 15 / 35 (33)** | - |
| `eng.kb.band_wid_rel>=12` | K6 | 44 / 42 (512) | 45 / 41 (805) | 45 / 39 (862)* | 46 / 36 (2147)** | 36 / 31 (564) | +1.0 / +5.5 |
| `eng.kb.mid_dist_atr<=1.1` | K6 | 44 / 43 (169) | 46 / 43 (280) | 45 / 42 (306) | 46 / 43 (674) | 29 / 35 (192) | +2.8 / +2.4 |
| `eng.kb.mid_dist_atr>=1.5` | K6 | 46 / 43 (158) | 45 / 44 (287) | 43 / 42 (327) | 44 / 43 (757) | 35 / 34 (304) | +2.8 / +2.4 |
| `eng.kb.mid_dist_atr>=2` | K6 | 50 / 43 (44) | 52 / 43 (88) | 49 / 42 (99) | 43 / 44 (214) | 34 / 34 (94) | +9.6 / +1.9 |

### 4b. PE (P6) pullback depth and arm-to-trigger

| state | scope | L3M | L6M | HOLD | PRE | X' | pts/ctr in vs out L6M |
|---|---|---|---|---|---|---|---|
| `eng.pe.depth_leg<=0.23` | P6 | 39 / 36 (209) | 42 / 37 (357) | 41 / 37 (394) | 40 / 38 (852) | 41 / 33 (291)* | +5.2 / +2.3 |
| `eng.pe.depth_leg>=0.62` | P6 | 30 / 40 (166)* | 32 / 42 (274)* | 33 / 41 (291)* | 36 / 39 (686) | 31 / 39 (223)* | -2.9 / +6.3 |
| `eng.pe.depth_leg>=0.8` | P6 | 30 / 39 (114) | 31 / 41 (179)* | 32 / 40 (191)* | 37 / 39 (453) | 29 / 39 (154)* | -2.5 / +5.0 |
| `eng.pe.ext_beyond_ema_atr<=0.25` | P6 | 38 / 37 (136) | 41 / 39 (232) | 39 / 39 (264) | 37 / 39 (591) | 34 / 37 (181) | +1.1 / +4.7 |
| `eng.pe.ext_beyond_ema_atr>=1` | P6 | 38 / 38 (194) | 40 / 39 (314) | 41 / 38 (334) | 38 / 39 (740) | 34 / 37 (250) | +7.3 / +1.9 |
| `eng.pe.ext_beyond_ema_atr>=2` | P6 | 31 / 39 (80) | 30 / 41 (123)* | 33 / 40 (131) | 36 / 39 (335) | 34 / 36 (102) | -5.2 / +5.2 |
| `eng.pe.arm_to_trig_min<=2` | P6 | 34 / 41 (289) | 36 / 43 (488) | 36 / 42 (543)* | 36 / 41 (1103)* | 37 / 35 (368) | -0.3 / +8.6 |
| `eng.pe.arm_to_trig_min>=10` | P6 | 43 / 37 (94) | 42 / 39 (151) | 44 / 38 (160) | 39 / 38 (417) | 37 / 36 (115) | +8.9 / +2.7 |
| `eng.pe.arm_to_trig_min>=20` | P6 | 46 / 37 (28) | 41 / 39 (49) | 42 / 39 (52) | 40 / 38 (141) | 31 / 36 (42) | +7.4 / +3.6 |
| `eng.pe.ema_dist_atr<=0` | P6 | 33 / 38 (39) | 36 / 40 (53) | 35 / 39 (55) | 32 / 39 (140) | 43 / 36 (54) | -2.5 / +4.2 |
| `eng.pe.ema_dist_atr>=0.5` | P6 | 38 / 36 (413) | 40 / 38 (684) | 40 / 37 (751) | 38 / 39 (1665) | 35 / 40 (525) | +3.7 / +3.8 |
| `eng.pe.ema_dist_atr>=1` | P6 | 38 / 37 (224) | 41 / 38 (375) | 42 / 37 (407) | 37 / 40 (958) | 32 / 39 (289)* | +6.5 / +1.8 |

### 4c. A6 = PB7 pullback depth and regime run

| state | scope | L3M | L6M | HOLD | PRE | X' | pts/ctr in vs out L6M |
|---|---|---|---|---|---|---|---|
| `eng.pb.pull_frac<=0.23` | A6 | 49 / 41 (401) | 49 / 43 (876) | 48 / 40 (957)* | 45 / 44 (1269) | 38 / 34 (551) | +10.1 / +2.2 |
| `eng.pb.pull_frac>=0.62` | A6 | 41 / 48 (32) | 46 / 48 (56) | 41 / 47 (68) | 45 / 44 (136) | 29 / 38 (89) | +4.2 / +9.0 |
| `eng.pb.run_atr<=2` | A6 | 44 / 49 (143) | 46 / 49 (272) | 44 / 48 (318) | 43 / 45 (588) | 31 / 41 (296)* | +4.5 / +10.3 |
| `eng.pb.run_atr>=10` | A6 | 50 / 47 (122) | 56 / 44 (328)** | 55 / 43 (354)** | 50 / 43 (395)* | 44 / 35 (174)* | +22.4 / +2.6 |
| `eng.pb.run_atr>=5` | A6 | 51 / 45 (211) | 52 / 45 (496)* | 52 / 43 (536)* | 45 / 44 (653) | 47 / 32 (279)** | +14.3 / +3.9 |
| `eng.pb.run_bars<=30` | A6 | 51 / 47 (99) | 48 / 48 (177) | 45 / 48 (211) | 42 / 45 (430) | 31 / 40 (206)* | +11.5 / +8.2 |
| `eng.pb.run_bars>=120` | A6 | 46 / 50 (279) | 48 / 49 (662) | 48 / 45 (715) | 46 / 43 (879) | 40 / 35 (364) | +6.3 / +13.0 |
| `eng.pb.run_bars>=360` | A6 | 59 / 44 (111)* | 57 / 44 (317)** | 56 / 43 (347)** | 46 / 44 (358) | 51 / 33 (171)** | +21.1 / +3.5 |

### 4d. MV (M6) vote count and strength

| state | scope | L3M | L6M | HOLD | PRE | X' | pts/ctr in vs out L6M |
|---|---|---|---|---|---|---|---|
| `eng.mv.vote<=4` | M6 | 49 / 48 (284) | 49 / 51 (481) | 48 / 48 (529) | 47 / 52 (1150) | 41 / 49 (409) | +4.5 / +6.0 |
| `eng.mv.vote>=5` | M6 | 48 / 49 (50) | 51 / 49 (78) | 48 / 48 (88) | 52 / 47 (193) | 49 / 41 (51) | +6.0 / +4.5 |
| `eng.mv.vote_min` | M6 | 49 / 48 (284) | 49 / 51 (481) | 48 / 48 (529) | 47 / 52 (1150) | 41 / 49 (409) | +4.5 / +6.0 |
| `eng.mv.zsum<=0.8` | M6 | 54 / 47 (111) | 51 / 48 (187) | 49 / 47 (203) | 46 / 49 (403) | 37 / 44 (106) | +8.0 / +3.0 |
| `eng.mv.zsum>=1.2` | M6 | 51 / 49 (63) | 56 / 48 (111) | 55 / 46 (128) | 48 / 48 (284) | 43 / 42 (128) | +11.3 / +3.0 |
| `eng.mv.zsum>=1.6` | M6 | 46 / 49 (13) | 41 / 50 (22) | 40 / 48 (25) | 48 / 48 (46) | 35 / 43 (26) | -6.2 / +5.1 |

### 4e. Weak signal bar (volume < 0.5 x the 60-bar median), all books

| state | scope | L3M | L6M | HOLD | PRE | X' | pts/ctr in vs out L6M |
|---|---|---|---|---|---|---|---|
| `eng.all.sigbar_vol_rel<=0.5` | ALL | 50 / 44 (115) | 49 / 45 (245) | 48 / 44 (269) | 40 / 43 (453) | 32 / 36 (192) | +9.7 / +4.9 |
| `eng.all.sigbar_vol_rel>=2` | ALL | 41 / 45 (679) | 42 / 46 (1230)* | 41 / 45 (1383)* | 42 / 43 (2960) | 35 / 37 (1102) | +3.5 / +5.8 |
| `eng.all.sigbar_vol_rel<=0.5` | K6 | 38 / 44 (21) | 43 / 44 (44) | 43 / 43 (47) | 40 / 44 (88) | 29 / 34 (28) | +0.6 / +2.6 |
| `eng.all.sigbar_vol_rel<=0.5` | P6 | 48 / 37 (23) | 48 / 39 (48) | 41 / 39 (56) | 42 / 38 (122) | 23 / 37 (48)* | +18.6 / +2.9 |
| `eng.all.sigbar_vol_rel<=0.5` | U6 | - | - | 18 / 38 (11) | 25 / 40 (24) | 10 / 34 (10)* | - |
| `eng.all.sigbar_vol_rel<=0.5` | H6 | 69 / 49 (16) | 61 / 49 (36) | 62 / 47 (39) | 34 / 45 (67) | 23 / 34 (31) | +22.9 / +5.7 |
| `eng.all.sigbar_vol_rel<=0.5` | M6 | 31 / 50 (13) | 32 / 50 (19) | 32 / 48 (19) | 36 / 48 (39) | 58 / 42 (12) | -23.8 / +5.7 |
| `eng.all.sigbar_vol_rel<=0.5` | A6 | 55 / 47 (40) | 56 / 47 (90) | 55 / 46 (97) | 44 / 45 (113) | 43 / 37 (63) | +13.3 / +8.3 |
| `eng.all.sigbar_vol_rel>=2` | K6 | 42 / 44 (177) | 42 / 45 (317) | 41 / 43 (356) | 44 / 43 (846) | 34 / 34 (286) | +1.0 / +3.0 |
| `eng.all.sigbar_vol_rel>=2` | P6 | 32 / 39 (120) | 32 / 42 (207)* | 32 / 41 (230)* | 35 / 40 (538)* | 39 / 35 (166) | +3.2 / +3.9 |
| `eng.all.sigbar_vol_rel>=2` | U6 | 29 / 43 (41) | 34 / 41 (74) | 33 / 39 (84) | 36 / 42 (182) | 30 / 35 (92) | -1.2 / +10.1 |
| `eng.all.sigbar_vol_rel>=2` | H6 | 49 / 51 (91) | 49 / 50 (153) | 49 / 48 (167) | 45 / 44 (387) | 32 / 34 (149) | +5.3 / +7.8 |
| `eng.all.sigbar_vol_rel>=2` | M6 | 43 / 52 (110) | 43 / 52 (174) | 43 / 51 (202) | 46 / 48 (412) | 33 / 46 (128)* | -0.3 / +6.9 |
| `eng.all.sigbar_vol_rel>=2` | A6 | 44 / 49 (140) | 46 / 49 (305) | 45 / 48 (344) | 45 / 44 (595) | 37 / 37 (281) | +8.6 / +8.8 |

### 4f. 60-s / 120-s / 15-s / 5-s sweeps (against = opposing the signal), ALL scope and the books

| state | scope | L3M | L6M | HOLD | PRE | X' | pts/ctr in vs out L6M |
|---|---|---|---|---|---|---|---|
| `bk.sw_ag120>=16` | ALL | 43 / 45 (1060) | 44 / 46 (1775) | 43 / 45 (1927) | 45 / 42 (4291)* | 39 / 34 (1434)** | +2.6 / +6.9 |
| `bk.sw_ag120>=2` | ALL | 44 / 51 (2255) | 45 / 47 (3919) | 44 / 44 (4309) | 44 / 37 (8720)** | 37 / 33 (2900) | +4.8 / +8.5 |
| `bk.sw_ag120>=6` | ALL | 44 / 45 (1689) | 45 / 45 (2800) | 44 / 43 (3034) | 44 / 40 (6491)** | 37 / 34 (1984) | +4.1 / +7.1 |
| `bk.sw_ag15>=1` | ALL | 43 / 46 (1614) | 45 / 46 (2765) | 44 / 44 (3003) | 44 / 42 (6259) | 38 / 34 (2030)* | +3.8 / +7.6 |
| `bk.sw_ag15>=3` | ALL | 44 / 45 (910) | 45 / 45 (1505) | 44 / 44 (1639) | 44 / 42 (3755) | 39 / 34 (1172)* | +3.5 / +6.1 |
| `bk.sw_ag15>=6` | ALL | 44 / 44 (553) | 44 / 45 (903) | 43 / 44 (970) | 45 / 42 (2329)* | 38 / 36 (645) | +3.6 / +5.6 |
| `bk.sw_ag5>=1` | ALL | 44 / 44 (1020) | 46 / 45 (1762) | 45 / 43 (1914) | 44 / 42 (4247) | 39 / 34 (1326)** | +5.5 / +5.0 |
| `bk.sw_ag5>=2` | ALL | 44 / 44 (611) | 43 / 46 (1006) | 43 / 44 (1084) | 44 / 43 (2620) | 41 / 35 (755)* | +3.3 / +5.7 |
| `bk.sw_ag60>=1` | ALL | 44 / 49 (2200) | 45 / 47 (3824) | 44 / 45 (4195) | 44 / 38 (8664)** | 37 / 33 (2886) | +4.9 / +7.1 |
| `bk.sw_ag60>=20` | ALL | 43 / 45 (664) | 44 / 46 (1075) | 43 / 44 (1167) | 45 / 42 (2831)* | 39 / 35 (792) | +2.4 / +6.1 |
| `bk.sw_ag60>=3` | ALL | 44 / 46 (1706) | 45 / 46 (2849) | 44 / 44 (3097) | 44 / 41 (6574)* | 38 / 34 (2059)* | +4.0 / +7.3 |
| `bk.sw_ag60>=8` | ALL | 43 / 45 (1088) | 44 / 46 (1813) | 43 / 45 (1969) | 44 / 42 (4442)* | 39 / 34 (1431)* | +2.8 / +6.8 |
| `bk.sw_net_ag60>=2` | ALL | 46 / 44 (394) | 46 / 45 (684) | 45 / 44 (740) | 46 / 42 (1530)* | 34 / 36 (525) | +5.8 / +5.0 |
| `bk.sw_net_ag60>=6` | ALL | 45 / 44 (182) | 47 / 45 (276) | 46 / 44 (294) | 47 / 43 (611)* | 39 / 36 (220) | +6.0 / +5.1 |
| `bk.sw_wi60>=20` | ALL | 43 / 45 (820) | 44 / 46 (1331) | 44 / 44 (1446) | 45 / 42 (3357)* | 39 / 35 (1025)* | +2.9 / +6.1 |
| `bk.sw_wi60>=3` | ALL | 44 / 47 (1965) | 45 / 46 (3344) | 44 / 45 (3664) | 44 / 41 (7668)* | 38 / 33 (2449)* | +4.1 / +8.6 |
| `bk.sw_wi60>=8` | ALL | 43 / 45 (1374) | 44 / 46 (2269) | 43 / 45 (2468) | 45 / 41 (5411)** | 38 / 34 (1696)* | +3.2 / +7.3 |
| `bk.sweep_against10>=1` | ALL | 44 / 44 (1383) | 45 / 45 (2382) | 44 / 43 (2584) | 44 / 42 (5492) | 38 / 34 (1781)* | +4.2 / +6.4 |
| `bk.sweep_against10>=3` | ALL | 44 / 44 (705) | 44 / 45 (1165) | 44 / 44 (1254) | 44 / 42 (2954) | 39 / 35 (882) | +3.7 / +5.7 |
| `bk.sweep_against10>=8` | ALL | 41 / 45 (250) | 42 / 45 (391) | 41 / 44 (415) | 43 / 43 (1036) | 39 / 36 (242) | +0.6 / +5.6 |
| `bk.sweep_against30>=1` | ALL | 44 / 46 (1961) | 45 / 46 (3363) | 44 / 44 (3677) | 44 / 40 (7503)* | 38 / 32 (2447)** | +4.1 / +8.6 |
| `bk.sweep_against30>=12` | ALL | 43 / 45 (540) | 43 / 46 (882) | 43 / 44 (956) | 44 / 43 (2351) | 38 / 36 (616) | +1.9 / +6.0 |
| `bk.sweep_against30>=4` | ALL | 43 / 45 (1097) | 45 / 45 (1837) | 44 / 44 (1994) | 45 / 42 (4445)* | 39 / 34 (1414)** | +3.6 / +6.3 |
| `bk.sweep_with30>=12` | ALL | 41 / 46 (664)* | 43 / 46 (1076) | 43 / 44 (1163) | 44 / 42 (2769) | 39 / 35 (806)* | +1.8 / +6.3 |
| `bk.sweep_with30>=4` | ALL | 43 / 46 (1323) | 44 / 46 (2224) | 43 / 44 (2430) | 44 / 42 (5295) | 38 / 34 (1692)* | +3.4 / +7.0 |
| `bk.sweepvol_against30>=150` | ALL | 41 / 45 (216) | 42 / 45 (325) | 42 / 44 (343) | 44 / 43 (686) | 35 / 36 (241) | +0.7 / +5.5 |
| `bk.sweepvol_against30>=50` | ALL | 41 / 45 (642) | 43 / 46 (1083) | 42 / 45 (1180) | 45 / 42 (2651)* | 39 / 35 (912)* | +2.2 / +6.1 |
| `bk.swv_ag60>=100` | ALL | 42 / 45 (677) | 43 / 46 (1130) | 42 / 44 (1232) | 44 / 42 (2835) | 39 / 35 (977)* | +2.3 / +6.2 |
| `bk.swv_ag60>=300` | ALL | 42 / 44 (220) | 43 / 45 (336) | 43 / 44 (357) | 43 / 43 (682) | 36 / 36 (222) | +1.0 / +5.5 |
| `bk.sw_ag60>=3` | K6 | 43 / 48 (567) | 44 / 44 (958) | 43 / 41 (1037) | 45 / 39 (2338)* | 37 / 27 (717)* | +1.1 / +8.3 |
| `bk.sw_ag60>=3` | P6 | 34 / 47 (396)* | 37 / 45 (622)* | 36 / 44 (672)* | 36 / 44 (1506)** | 38 / 33 (423) | +3.8 / +3.8 |
| `bk.sw_ag60>=3` | U6 | 42 / 29 (57) | 43 / 33 (88) | 41 / 33 (99) | 38 / 41 (233) | 37 / 31 (70) | +9.2 / +1.9 |
| `bk.sw_ag60>=3` | H6 | 52 / 46 (214) | 52 / 45 (357) | 50 / 43 (391) | 48 / 35 (829)** | 36 / 30 (312) | +7.1 / +6.8 |
| `bk.sw_ag60>=3` | M6 | 50 / 44 (284) | 50 / 46 (467) | 49 / 44 (515) | 48 / 45 (1118) | 40 / 51 (377) | +5.3 / +1.5 |
| `bk.sw_ag60>=3` | A6 | 48 / 47 (188) | 48 / 48 (357) | 48 / 47 (383) | 51 / 41 (550)** | 40 / 36 (160) | +6.5 / +10.0 |
| `bk.sw_ag60>=8` | K6 | 43 / 45 (404) | 43 / 46 (681) | 42 / 43 (734) | 45 / 41 (1761)* | 39 / 29 (524)** | -0.3 / +6.2 |
| `bk.sw_ag60>=8` | P6 | 28 / 46 (255)** | 30 / 47 (406)** | 31 / 46 (442)** | 33 / 43 (974)** | 37 / 35 (318) | +1.9 / +5.3 |
| `bk.sw_ag60>=8` | U6 | 41 / 36 (22) | 45 / 36 (33) | 46 / 35 (35) | 50 / 38 (70) | - | +4.9 / +5.6 |
| `bk.sw_ag60>=8` | H6 | 56 / 43 (153)* | 55 / 44 (259)* | 54 / 42 (285)* | 49 / 38 (639)** | 37 / 30 (259) | +8.4 / +5.4 |
| `bk.sw_ag60>=8` | M6 | 49 / 50 (212) | 49 / 49 (361) | 48 / 47 (399) | 50 / 43 (879)* | 40 / 46 (298) | +4.5 / +5.0 |
| `bk.sw_ag60>=8` | A6 | 62 / 46 (42)* | 56 / 47 (73) | 55 / 47 (74) | 58 / 43 (119)** | 54 / 37 (24) | +9.0 / +8.8 |

### 4g. Both edges of every new state, ranked on PRE u X' only (z of the difference in P(target)); L6M beside - the lowering list and the raising list

**LOWERS P(target) most (skip side)**

| state | scope | PRE u X': in% / out% (n) | z | L6M | HOLD |
|---|---|---|---|---|---|
| `bk.sw_ag60>=20` | P6 | 30 / 41 (789) | -5.9 | 26 / 45 (256)** | 26 / 44 (276)** |
| `bk.sweep_with30>=12` | P6 | 30 / 41 (805) | -5.5 | 25 / 45 (264)** | 26 / 44 (282)** |
| `bk.sw_wi60>=20` | P6 | 31 / 41 (1010) | -5.3 | 28 / 46 (323)** | 28 / 45 (350)** |
| `eng.kb.band_wid_rel<=4` | K6 | 16 / 42 (61) | -5.2 | - | - |
| `eng.kb.band_wid_rel<=4` | ALL | 16 / 42 (61) | -5.2 | - | - |
| `bk.sweep_against10>=8` | P6 | 26 / 39 (322) | -5.2 | 19 / 42 (93)** | 20 / 41 (97)** |
| `bk.sweep_against30>=12` | P6 | 30 / 40 (681) | -5.2 | 25 / 44 (225)** | 25 / 43 (240)** |
| `bk.swv_ag60>=100` | P6 | 31 / 41 (832) | -5.0 | 26 / 45 (265)** | 26 / 44 (285)** |
| `bk.swv_ag60>=300` | P6 | 23 / 39 (189) | -4.9 | 17 / 41 (75)** | 17 / 41 (78)** |
| `bk.sw_ag15>=6` | P6 | 31 / 40 (676) | -4.6 | 27 / 43 (221)** | 27 / 43 (232)** |

**RAISES P(target) most (take / size-up side)**

| state | scope | PRE u X': in% / out% (n) | z | L6M | HOLD |
|---|---|---|---|---|---|
| `nest.setline_20_30` | ALL | 53 / 40 (968) | +8.0 | 50 / 45 (306) | 50 / 43 (342)* |
| `cal.earn.amc_post960` | A6 | 63 / 40 (253) | +7.3 | 16 / 51 (87)** | 24 / 50 (116)** |
| `cal.earn.amc_day_evening` | A6 | 63 / 40 (265) | +7.3 | 23 / 51 (94)** | 31 / 49 (112)** |
| `cal.earn.amc_day_evening` | ALL | 55 / 40 (623) | +6.9 | 31 / 46 (227)** | 36 / 44 (258)* |
| `cal.earn.amc_post960` | ALL | 49 / 40 (1247) | +6.0 | 38 / 46 (449)** | 39 / 45 (505)* |
| `eng.kb.band_wid_rel>=12` | K6 | 44 / 34 (2711) | +6.0 | 45 / 41 (805) | 45 / 39 (862)* |
| `eng.kb.band_wid_rel>=12` | ALL | 44 / 34 (2711) | +6.0 | 45 / 41 (805) | 45 / 39 (862)* |
| `cal.earn.amc_post360` | A6 | 60 / 41 (207) | +5.4 | 14 / 50 (64)** | 26 / 49 (89)** |
| `cal.earn.amc_post360` | ALL | 53 / 41 (442) | +5.3 | 24 / 46 (166)** | 29 / 45 (201)** |
| `bk.sw_wi60>=20` | K6 | 46 / 38 (1622) | +5.2 | 46 / 42 (485) | 46 / 40 (522)* |

Plain lines (last six months, live-lot signals; z in brackets):
- KB signals whose 3-m break bar closed less than 25% of its range beyond the Keltner band reach the target 44% vs 45% otherwise (L6M, n = 685, z -0.3).
- PE signals after a pullback deeper than 62% of the last 5-m swing leg reach the target 32% vs 42% otherwise (L6M, n = 274, z -2.8).
- PE signals after a pullback shallower than 23% of the leg reach the target 42% vs 37% otherwise (L6M, n = 357, z +1.4).
- A6 (PB7) signals whose pullback is 62%+ of the regime run reach the target 46% vs 48% otherwise (L6M, n = 56, z -0.3).
- Signals within 60 s of 3+ sweeps against them reach the target 45% vs 46% otherwise (L6M, n = 2849, z -0.5).
- Signals fired in the 120 min after a mega-cap earnings print reach the target 31% vs 45% otherwise (L6M, n = 54, z -2.2).

## 5. Calendar gaps - what is on disk, what is used, what stays named

| source | where | coverage | used as | status |
|---|---|---|---|---|
| CPI (46), NFP (43), FOMC statement (32) release dates and clocks | `l2vast/standS/event_calendar_core.csv` (bls.gov / federalreserve.gov, saved 2026-09-18) | 2023-02..2026-12 | `tm.rel.CORE830/FOMC.*`, `tm.day.*` (NTE-1) | VERIFIED |
| jobless claims, PCE, ISM mfg/svc, JOLTS, consumer confidence, FOMC minutes | rules on the verified core (Thursday 08:30; last Friday; 1st / 3rd business day 10:00; first / last Tuesday; +21 d) | same | `tm.rel.R830/R1000/FOMCMIN.*` | RULE-BASED, unverified dates |
| **Treasury auction closes** (notes and bonds 13:00 ET: 491; bills 11:30 ET: 97; 3/5/7/10/20/30-year, 17/26/52-week) | `data/gap/ds50/treasury_auctions.csv` | 588 auctions, close dates 2012-08-09..2026-10-21 (covers the whole 2023-02..2026-02 sample) | `cal.auct.1300.pre5/10/15/30`, `.post2/5/10`, `cal.auct.1300long.*` (10/20/30-year), `cal.auct.1130bill.*`, `cal.auct.day1300`, `cal.auct.day1300_afternoon` | VERIFIED dates (the file's close times; result time taken = close) |
| **Mega-cap earnings nights** (EDGAR 8-K item 2.02 acceptance time stamps) | `data/gap/edgar/CIK*.json` (AAPL, MSFT, COST, AMZN, NVDA, NFLX, TSLA, META, GOOGL, AVGO; one event per quarter) | 694 filings; filings reach 2026-09-25..2026-10-15 | `cal.earn.amc_post30/120/360/960` (after-close >= 16:00 ET), `cal.earn.bmo_post*`, `cal.earn.rth_day_after`, `cal.earn.night_all`, `cal.earn.amc_day_evening` | VERIFIED time stamps; 10 of the top-15 names (PEP, CSCO, AMD, TMUS, ADBE absent) |
| **NAMED GAPS (nothing on disk; nothing fabricated)** | PPI, retail sales, GDP (advance / second / third), durable goods, housing starts, UMich, Fed-speaker calendar, the 5 missing top-15 earnings, holiday-shifted claims other than Thanksgiving, bill auctions other than the 11:30 close | - | not scored | needs a BLS / Census / BEA release calendar file (free, no download scripted here); recorded in `DS3_THL2_NEEDS.md` terms as a data request |

### 5a. Treasury auction windows (ALL scope; P(target) in / out, live-lot signals)

| state | scope | L3M | L6M | HOLD | PRE | X' | pts/ctr in vs out L6M |
|---|---|---|---|---|---|---|---|
| `cal.auct.1300.post10` | ALL | - | - | - | 33 / 43 (18) | - | - |
| `cal.auct.1300.post5` | ALL | - | - | - | 40 / 43 (10) | - | - |
| `cal.auct.1300.pre10` | ALL | - | - | - | 38 / 43 (16) | - | - |
| `cal.auct.1300.pre15` | ALL | - | - | - | 36 / 43 (25) | - | - |
| `cal.auct.1300.pre30` | ALL | - | 31 / 45 (13) | 31 / 44 (13) | 38 / 43 (40) | - | -9.5 / +5.2 |
| `cal.auct.1300long.post10` | ALL | - | - | - | 30 / 43 (10) | - | - |
| `cal.auct.1300long.pre30` | ALL | - | - | - | 30 / 43 (20) | - | - |
| `cal.auct.day1300` | ALL | 45 / 44 (673) | 41 / 47 (1193)** | 40 / 45 (1301)** | 43 / 43 (2978) | 40 / 35 (844)* | +0.4 / +7.0 |
| `cal.auct.day1300_afternoon` | ALL | 50 / 44 (22) | 50 / 45 (42) | 50 / 44 (44) | 36 / 43 (130) | 36 / 36 (47) | +17.3 / +5.0 |

### 5b. Earnings nights (ALL scope)

| state | scope | L3M | L6M | HOLD | PRE | X' | pts/ctr in vs out L6M |
|---|---|---|---|---|---|---|---|
| `cal.earn.amc_day_evening` | ALL | 41 / 44 (125) | 31 / 46 (227)** | 36 / 44 (258)* | 58 / 42 (454)** | 44 / 36 (169)* | -8.7 / +5.9 |
| `cal.earn.amc_post120` | ALL | 26 / 44 (34)* | 31 / 45 (54)* | 43 / 44 (68) | 45 / 43 (103) | 43 / 36 (42) | -0.9 / +5.2 |
| `cal.earn.amc_post30` | ALL | 20 / 44 (10) | 39 / 45 (18) | 45 / 44 (20) | 46 / 43 (26) | - | +5.5 / +5.2 |
| `cal.earn.amc_post360` | ALL | 25 / 45 (97)** | 24 / 46 (166)** | 29 / 45 (201)** | 54 / 43 (344)** | 51 / 36 (98)** | -14.0 / +5.9 |
| `cal.earn.amc_post960` | ALL | 40 / 45 (265) | 38 / 46 (449)** | 39 / 45 (505)* | 49 / 42 (925)** | 51 / 35 (322)** | -4.0 / +6.2 |
| `cal.earn.night_all` | ALL | 39 / 44 (99) | 44 / 45 (160) | 43 / 44 (178) | 42 / 43 (305) | 50 / 36 (115)** | -3.1 / +5.5 |
| `cal.earn.rth_day_after` | ALL | 50 / 44 (121) | 48 / 45 (214) | 48 / 44 (233) | 49 / 43 (502)* | 41 / 36 (214) | +6.7 / +5.1 |

Reading: the 13:00 auction windows hold few live signals (about 5-11 a week in the pre-30 window, 1-2 a week within +-5 min) and the difference in P(target) is inside the binomial noise in every window; the earnings-night states are the Asia / London / pre-open hours of the day after a mega-cap print (about 2,700 + 3,800 signals of 44,370 in all history) - see the table for the direction by window, none is beyond z = 3 in L6M together with PRE u X'. These are descriptive maps; the states are also in the section C / D screens (`cal.*` families) and none reached a reported top rule except where listed in 1b / 3c.

## 6. QUANT-LAYER validity and the qv header

### 6a. Program-level multiple-testing control (all engine-run cells of a family x action; daily stack deltas, circular block bootstrap block 5 days, 500 draws)

| family | action | cells | White RC p (L6M) | RC p (HOLD) | Romano-Wolf survivors L6M / HOLD | PBO (CSCV, all dates) | min backtest length (years) for this many trials at SR 1 |
|---|---|---|---|---|---|---|---|
| C-four | skip | 3 | 0.54 | 0.24 | 0 / 0 | 0.86 | 0.73 |
| C-four | x0.5 | 3 | 0.45 | 0.23 | 0 / 0 | 0.94 | 0.73 |
| C-kofn | skip | 29 | 0.96 | 0.95 | 0 / 0 | 0.27 | 4.24 |
| C-kofn | x0.5 | 29 | 0.95 | 0.95 | 0 / 0 | 0.57 | 4.24 |
| C-nested | skip | 23 | 0.50 | 0.58 | 0 / 0 | 0.47 | 3.85 |
| C-nested | x0.5 | 23 | 0.61 | 0.70 | 0 / 0 | 0.52 | 3.85 |
| C-pair | skip | 105 | 0.82 | 0.84 | 0 / 0 | 0.79 | 6.49 |
| C-pair | x0.5 | 105 | 0.95 | 0.96 | 0 / 0 | 0.85 | 6.49 |
| C-single | skip | 210 | 1.00 | 1.00 | 0 / 0 | 0.46 | 7.74 |
| C-single | x0.5 | 210 | 1.00 | 1.00 | 0 / 0 | 0.38 | 7.74 |
| C-triple | skip | 93 | 0.77 | 0.80 | 0 / 0 | 0.77 | 6.27 |
| C-triple | x0.5 | 93 | 0.89 | 0.87 | 0 / 0 | 0.84 | 6.27 |
| D-four | take | 36 | 0.90 | 0.82 | 0 / 0 | 0.19 | 4.61 |
| D-four | x1.5 | 36 | 0.51 | 0.51 | 0 / 0 | 0.59 | 4.61 |
| D-kofn | take | 30 | 0.99 | 0.87 | 0 / 0 | 0.43 | 4.30 |
| D-kofn | x1.5 | 30 | 0.01 | 0.00 | 1 / 1 | 0.52 | 4.30 |
| D-nested | take | 26 | 0.95 | 0.95 | 0 / 0 | 0.02 | 4.06 |
| D-nested | x1.5 | 26 | 0.67 | 0.44 | 0 / 0 | 0.38 | 4.06 |
| D-pair | take | 105 | 0.98 | 0.94 | 0 / 0 | 0.53 | 6.49 |
| D-pair | x1.5 | 105 | 0.00 | 0.00 | 0 / 0 | 0.72 | 6.49 |
| D-single | take | 210 | 1.00 | 0.93 | 0 / 0 | 0.62 | 7.74 |
| D-single | x1.5 | 210 | 0.00 | 0.00 | 3 / 3 | 0.56 | 7.74 |
| D-triple | take | 105 | 0.90 | 0.87 | 0 / 0 | 0.42 | 6.49 |
| D-triple | x1.5 | 105 | 0.19 | 0.24 | 0 / 0 | 0.79 | 6.49 |
| L-M | skip | 21 | 0.81 | 0.81 | 0 / 0 | 0.57 | 3.69 |
| L-M | x0.5 | 21 | 0.88 | 0.62 | 0 / 0 | 0.67 | 3.69 |
| L-Q | skip | 21 | 0.73 | 0.64 | 0 / 0 | 0.46 | 3.69 |
| L-Q | x0.5 | 21 | 0.76 | 0.53 | 0 / 0 | 0.28 | 3.69 |
| T | skip | 7 | 0.39 | 0.33 | 1 / 1 | 0.27 | 1.92 |
| T | x0.5 | 7 | 0.36 | 0.30 | 1 / 1 | 0.53 | 1.92 |

### 6b. qv header of the reported top rule per family and action (columns that need new infrastructure are listed as missing; a cell missing any column is not promoted)

| group | action | key | L3M / L6M / HOLD / PRE / X' ($k/wk) | L6M MDE | L6M block-bootstrap CI (weeks, block 4) | fire rate L6M | fired / wk | cells in the family | RC p (L6M, family) | RW survives | DSR (daily, trials = cells) | PBO | placebo rank rand / shift (24 each; 95th pct of the draws rand / shift) | stack corr (weekly) | top-5%-weeks share | positive quarters | promote_ok | missing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C-four | skip | `C|211|skip` | -0.2 / +0.0 / +0.1 / -0.0 / +0.1 | 0.9 | [-0.5, +0.5] | 1.0% | 1.5 | 3 | 0.54 | N | 0.27 | 0.86 | 0.67 / 0.62 (+0.5 / +0.4) | -0.30 | 4.74 | 5/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| C-four | x0.5 | `C|497|x0.5` | +0.0 / +0.1 / +0.3 / +0.0 / -0.0 | 0.8 | [-0.3, +0.7] | 0.1% | 0.1 | 3 | 0.45 | N | 0.34 | 0.94 | 0.79 / 0.79 (+0.3 / +0.5) | -0.16 | 1.96 | 8/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| C-kofn | skip | `C|367|skip` | -6.0 / -2.9 / -1.1 / +5.6 / +5.3 | 6.9 | [-7.5, +1.5] | 2.8% | 4.4 | 29 | 0.96 | N | 0.77 | 0.27 | 1.00 / 0.96 (-5.7 / -3.3) | +0.02 | -0.43 | 11/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| C-kofn | x0.5 | `C|367|x0.5` | -7.9 / -3.7 / -2.6 / +3.7 / +2.5 | 7.0 | [-9.3, +0.5] | 2.8% | 4.4 | 29 | 0.95 | N | 0.53 | 0.57 | 0.96 / 0.88 (-4.4 / -2.4) | -0.00 | -0.36 | 9/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| C-nested | skip | `C|38|skip` | +0.2 / -0.2 / -0.1 / +0.1 / +0.7 | 0.6 | [-0.6, +0.3] | 0.5% | 0.8 | 23 | 0.50 | N | 0.14 | 0.47 | 0.21 / 0.46 (+0.5 / +0.3) | -0.25 | -0.78 | 6/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| C-nested | x0.5 | `C|368|x0.5` | +2.0 / +0.5 / +0.4 / +0.1 / +0.1 | 3.0 | [-1.0, +2.4] | 0.7% | 1.0 | 23 | 0.61 | N | 0.04 | 0.52 | 0.92 / 0.83 (+1.1 / +1.6) | -0.21 | 1.94 | 5/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| C-pair | skip | `C|343|skip` | -2.2 / -2.1 / -1.8 / +2.1 / +2.8 | 5.0 | [-6.5, +1.7] | 2.1% | 3.3 | 105 | 0.82 | N | 0.09 | 0.79 | 0.79 / 0.88 (+0.2 / -1.4) | +0.10 | -0.40 | 8/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| C-pair | x0.5 | `C|343|x0.5` | -2.5 / -2.1 / -1.7 / +1.0 / +1.1 | 5.2 | [-5.8, +1.0] | 2.1% | 3.3 | 105 | 0.95 | N | 0.02 | 0.85 | 0.71 / 0.92 (+0.2 / -2.1) | -0.14 | -0.38 | 7/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| C-single | skip | `C|48|skip` | -2.6 / -0.5 / -0.8 / +2.5 / +3.0 | 4.0 | [-3.2, +1.6] | 2.5% | 3.9 | 210 | 1.00 | N | 0.31 | 0.46 | 0.92 / 0.92 (+0.4 / -0.2) | -0.23 | -1.80 | 8/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| C-single | x0.5 | `C|48|x0.5` | -2.5 / -1.2 / -1.4 / +1.1 / +1.4 | 2.4 | [-2.3, -0.2] | 2.5% | 3.9 | 210 | 1.00 | N | 0.10 | 0.38 | 0.62 / 0.62 (-0.2 / -0.2) | -0.31 | -0.33 | 7/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| C-triple | skip | `C|350|skip` | -4.7 / -1.2 / -1.5 / +2.5 / +2.4 | 5.0 | [-5.1, +2.6] | 1.7% | 2.7 | 93 | 0.77 | N | 0.36 | 0.77 | 0.79 / 0.75 (+0.2 / +0.2) | -0.30 | -1.17 | 9/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| C-triple | x0.5 | `C|356|x0.5` | -3.8 / -2.0 / -0.9 / +0.8 / +1.3 | 4.3 | [-5.4, +0.2] | 0.5% | 0.9 | 93 | 0.89 | N | 0.07 | 0.84 | 0.17 / 0.21 (+0.5 / +0.8) | -0.10 | -0.20 | 8/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| D-four | take | `D|288|take` | +2.0 / -0.6 / -0.7 / -1.4 / +0.2 | 4.0 | [-3.5, +2.2] | 13.5% | 21.1 | 36 | 0.90 | N | 0.00 | 0.19 | 0.25 / 0.12 (+0.4 / +0.4) | -0.33 | -1.26 | 4/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| D-four | x1.5 | `D|118|x1.5` | -0.2 / +1.5 / +1.4 / +1.3 / +1.5 | 4.2 | [-1.8, +4.5] | 4.2% | 6.6 | 36 | 0.51 | N | 0.37 | 0.59 | 0.96 / 0.88 (+1.1 / +1.7) | -0.04 | 0.94 | 6/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| D-kofn | take | `D|688|take` | -1.0 / -1.7 / -1.4 / +0.6 / +0.7 | 3.6 | [-3.3, +0.1] | 3.4% | 5.4 | 30 | 0.99 | N | 0.05 | 0.43 | 1.00 / 1.00 (-2.2 / -1.9) | -0.16 | -0.64 | 5/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| D-kofn | x1.5 | `D|109|x1.5` | +2.6 / +5.0 / +5.6 / +8.4 / +6.2 | 7.2 | [+1.4, +8.7] | 14.8% | 23.1 | 30 | 0.01 | Y | 1.00 | 0.52 | 0.88 / 0.96 (+5.3 / +4.4) | +0.00 | 0.42 | 12/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| D-nested | take | `D|941|take` | -1.4 / -1.3 / -1.3 / -1.0 / +0.0 | 2.7 | [-3.4, +0.8] | 23.6% | 36.8 | 26 | 0.95 | N | 0.00 | 0.02 | 0.17 / 0.12 (-0.2 / -0.8) | -0.12 | -0.35 | 2/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| D-nested | x1.5 | `D|131|x1.5` | -0.0 / +1.3 / +1.5 / +1.3 / +1.9 | 5.1 | [-1.8, +4.3] | 2.4% | 3.7 | 26 | 0.67 | N | 0.71 | 0.38 | 0.71 / 0.96 (+2.2 / +1.2) | +0.30 | 1.13 | 9/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| D-pair | take | `D|907|take` | -1.2 / -0.7 / -0.5 / -0.2 / -0.2 | 2.9 | [-2.8, +1.4] | 20.4% | 31.8 | 105 | 0.98 | N | 0.00 | 0.53 | 0.21 / 0.46 (+0.5 / +0.1) | -0.39 | -1.02 | 4/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| D-pair | x1.5 | `D|91|x1.5` | +10.4 / +13.8 / +14.1 / +5.5 / +3.7 | 11.7 | [+7.2, +19.8] | 17.5% | 27.4 | 105 | 0.00 | N | 0.69 | 0.72 | 1.00 / 1.00 (+5.2 / +6.5) | +0.69 | 0.32 | 10/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| D-single | take | `D|708|take` | -6.6 / -6.1 / -5.1 / +0.4 / +0.8 | 5.5 | [-8.9, -3.1] | 8.8% | 13.7 | 210 | 1.00 | N | 0.00 | 0.62 | 0.96 / 0.96 (-6.3 / -6.6) | -0.32 | -0.16 | 6/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| D-single | x1.5 | `D|149|x1.5` | -7.4 / +0.4 / +1.6 / +5.3 / +3.6 | 13.4 | [-10.1, +9.3] | 20.9% | 32.6 | 210 | 0.00 | Y | 0.29 | 0.56 | 0.12 / 0.17 (+6.6 / +6.8) | +0.28 | 7.89 | 9/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| D-triple | take | `D|920|take` | -1.0 / -0.9 / -0.6 / -0.4 / -0.5 | 3.1 | [-3.1, +1.4] | 23.3% | 36.3 | 105 | 0.90 | N | 0.00 | 0.42 | 0.25 / 0.42 (+0.0 / -0.1) | -0.35 | -0.88 | 5/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| D-triple | x1.5 | `D|95|x1.5` | +0.4 / +3.0 / +2.4 / +3.3 / +2.9 | 5.5 | [-0.3, +6.5] | 2.9% | 4.5 | 105 | 0.19 | N | 0.95 | 0.79 | 0.96 / 1.00 (+1.8 / +2.3) | -0.34 | 0.70 | 11/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| L-M | skip | `L|K6|M|real|0|q10|skip` | -0.0 / +0.3 / +0.2 / +0.2 / +0.2 | 0.9 | [-0.1, +0.9] | 1.5% | 2.4 | 21 | 0.81 | N | 0.28 | 0.57 | 0.88 / 0.88 (+0.5 / +0.7) | -0.11 | 1.35 | 7/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| L-M | x0.5 | `L|M6|M|real|0|q10|x0.5` | -0.0 / -0.3 / -0.3 / +0.1 / +0.1 | 0.6 | [-0.8, -0.0] | 1.0% | 1.5 | 21 | 0.88 | N | 0.05 | 0.67 | 0.21 / 0.21 (+0.1 / +0.3) | -0.25 | -0.00 | 4/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| L-Q | skip | `L|M6|Q|real|0|q20|skip` | -0.3 / -0.7 / -0.8 / +0.4 / +0.5 | 1.2 | [-1.6, +0.0] | 1.7% | 2.6 | 21 | 0.73 | N | 0.15 | 0.46 | 0.33 / 0.12 (+1.4 / +1.4) | -0.34 | -0.12 | 8/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| L-Q | x0.5 | `L|M6|Q|real|0|q20|x0.5` | -0.0 / -0.3 / -0.3 / +0.3 / +0.1 | 0.7 | [-0.8, +0.0] | 1.7% | 2.6 | 21 | 0.76 | N | 0.22 | 0.28 | 0.42 / 0.29 (+0.5 / +0.5) | -0.31 | -0.00 | 6/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| T | skip | `T|K6|q20|skip` | +1.5 / +0.6 / +0.5 / +0.8 / +0.2 | 1.8 | [-0.9, +2.0] | 5.1% | 7.9 | 7 | 0.39 | Y | 0.84 | 0.27 | 1.00 / 0.96 (-0.2 / +0.3) | -0.38 | 0.85 | 10/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |
| T | x0.5 | `T|M6|q20|x0.5` | -0.6 / -0.8 / -0.7 / +0.1 / +0.2 | 1.0 | [-1.5, -0.2] | 1.8% | 2.9 | 7 | 0.36 | Y | 0.05 | 0.53 | 0.04 / 0.12 (+0.3 / +0.5) | -0.02 | -0.00 | 3/12 | no | neighbourhood_mean, breakeven_slip, capacity_contracts, regime split |

Not run (stated): thresholds +-25/50% neighbourhood surface, breakeven slippage, depth capacity, purged k-fold / CPCV for the learned layer (the walk-forward IS time-respecting; the cross-fitted CPCV is not run), latency 1 s / 3 s, IC decay by horizon. They are the columns marked missing; no row reached the point where they would change a decision.

## 7. Verdicts per family, post-hoc flags, D6 mapping

- **C pairs / triples / k-of-n / four-legged / nested (skip, x0.5):** pair: skip: 86/105 selected, mean L6M -0.7k, 0 beyond MDE; x0.5: 76/105 selected, mean L6M -0.5k, 0 beyond MDE | triple: skip: 75/93 selected, mean L6M -0.3k, 0 beyond MDE; x0.5: 66/93 selected, mean L6M -0.3k, 0 beyond MDE | k-of-n: skip: 21/29 selected, mean L6M -2.4k, 0 beyond MDE; x0.5: 21/29 selected, mean L6M -1.5k, 0 beyond MDE | four-legged: skip: 0/3 selected, mean L6M n/ak, 0 beyond MDE; x0.5: 0/3 selected, mean L6M n/ak, 0 beyond MDE | nested: skip: 3/23 selected, mean L6M -0.2k, 0 beyond MDE; x0.5: 3/23 selected, mean L6M +0.1k, 0 beyond MDE. Verdict: structure / noise, no rule is positive in PRE, X', L6M and HOLD and beyond MDE.
- **C singles (the top-30 states):** skip: 97/210 selected, mean L6M -1.3k, 0 beyond MDE; x0.5: 92/210 selected, mean L6M -0.8k, 0 beyond MDE. Same.
- **D size-up x1.5 and take-only:** single: x1.5: 202/210 selected, mean L6M +1.2k, 12 beyond MDE; take: 4/210 selected, mean L6M -7.2k, 0 beyond MDE | pair: x1.5: 104/105 selected, mean L6M +0.5k, 2 beyond MDE; take: 0/105 selected, mean L6M n/ak, 0 beyond MDE | triple: x1.5: 105/105 selected, mean L6M +0.3k, 2 beyond MDE; take: 0/105 selected, mean L6M n/ak, 0 beyond MDE | k-of-n: x1.5: 30/30 selected, mean L6M +2.7k, 3 beyond MDE; take: 10/30 selected, mean L6M -0.6k, 0 beyond MDE | four-legged: x1.5: 33/36 selected, mean L6M +0.0k, 0 beyond MDE; take: 0/36 selected, mean L6M n/ak, 0 beyond MDE | nested: x1.5: 21/26 selected, mean L6M -0.2k, 0 beyond MDE; take: 0/26 selected, mean L6M n/ak, 0 beyond MDE. A positive x1.5 is the stack's own positive edge times more lots: the uniform x1.5 on all signals earns the figure in 3a, and a state rule is worth only what it adds over the same-rate random size-up (placebo rank in 3c). Take-only throws away winners in every family.
- **Learned model:** AUC 0.55-0.79 out of sample (U6 0.78, P6 0.69, K6 0.67, H6 0.66, POOL6 0.65, M6 0.57, A6 0.56) and reasonably calibrated in the middle quintiles (K6 / P6 / H6 over-predict the top quintile by 5-10 pp), but the policies on the stack are inside MDE (K6 monthly skip +0.3 / +0.8 / +0.7k L6M at q = 10 / 20 / 30% and U6 +0.2 / +0.3 / +0.7k are the only consistently positive books, 0.5-1.7% of the stack) and P6 / M6 are negative; the shuffled twins span the same range (2c); the extracted AND-sets re-derive the set-line (ZONES) family. Verdict: no learned no-trade layer; the discrimination is real (P(target) is partly predictable from td/sd and the set line) and is not money.
- **New states (KB closure, PE depth, PB7 depth, MV vote, 60-s sweeps, auctions, earnings):** described in section 4 / 5 with both edges. The one recurring structure is on A6: long / old regime runs (eng.pb.run_atr >= 10 or run_bars >= 360) carry higher P(target) in every window (section 4c), and the PE deep pullback (>= 62% of the leg) lowers P(target) in L3M / L6M / HOLD / X' (4b): they are LEADS for the next prereg (single states, selected here by the map, not by a stack run) - not rules.

**Post-hoc flags.** Selection of every engine-run cell used PRE u X' only; the reported top rule per family was chosen on min(PRE, X') STACK delta (selection windows); the L3M / L6M / HOLD numbers are ONE look per family. The section-4 maps are descriptive and show all windows (including the recent ones) beside; the sentences "A6 long runs raise P(target)" and "PE deep pullbacks lower it" are read off those maps after looking at L6M / HOLD, so they are post-hoc LEADS (PRE and X' evidence is in the same row). The learned-model cut-off q was chosen on PRE u X' predictions; the three q values are all shown.

**D6 mapping.** Nothing in this report is a THP_POLICY entry: no rule passes the gates (positive in PRE and X' and L6M and HOLD, L6M beyond MDE, both placebos beaten, Romano-Wolf survivor). If the D6 owner wants a shadow-log, the computable-live definitions are exact in section 4 (`eng.kb.break_rng`, `eng.pe.depth_leg`, `eng.pb.run_atr`, `eng.mv.vote`, 60-s sweep counters) and in the release calendar files (`out/ntexp/release_calendar.csv` plus the new Treasury / earnings states, a daily file from the two source files named above); the live set-line flags are the existing zone feed. Files: `results_{C,D,L,T,U}.parquet`, `valid_programs.csv`, `valid_top_rules.csv`, `map_new.parquet`, `learned_*`, RECENT_WINS rows `out/recent_wins/nt3.csv`.

**Questions for the D6 owner (also in MORNING.md).** None blocking. (1) If a dated PPI / retail-sales / GDP calendar (BLS / Census / BEA release schedules) can be dropped into `data/gap/`, the 08:30 family can be completed; today only CPI / NFP / FOMC are verified. (2) The 10:00 releases other than ISM remain rule-dated.
