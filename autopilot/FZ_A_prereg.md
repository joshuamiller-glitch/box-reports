# FZ-1 PREREG - T-FAVORABLE-ZONES section A (location-quality map), 2026-10-30
Written and hashed BEFORE any outcome statistic of any location cell was computed. Only feature coverage/distributions were looked at (no outcomes).
Code (hashed with this file in DECISIONS.md): l2vast/ds3/code/fz/{fz_feat.py,fz_lib.py,fz_cells.py}. Cell specs: out/fz/A_cell_specs.txt (sha256 of the spec list 6ffa0206fb1387f0784cc1c6f1480c04c9e21dea9e49dbbdf9ebee2719ca7642).
dead_lookup (5 representative family specs: poi_behind / location / htf / take / fz) : 0 EXACT/NEAR hits - no earlier program scored a location-conditioned take-only (CF-A/B scored levels as limit-confirmation mechanics, a different object).

## Universe and outcomes
Signals: the 44,370 capped held-signal trades of cf_engine.load() (10 books ST HM WT KB SM PE PB DN MV MA; lock-engine books = ST HM WT KB SM PE; PB DN MV MA labelled non-lock), label day <= 20260206, UNTOUCHED never read.
Windows (own masks): X'=20230401..20240131, PRE=20240201..20250630, HOLD=20250701..20260206, L6M=20250801..20260206, Y26=20260101..20260206, L3M=20251106..20260206 (VIEW ONLY, never selects).
Outcome of a signal for the MAP = the held-signal market trade at the signal second (1 lot, per contract = per lot): x_N (N basis, no target-fill correction) primary, x_M (measured), P(target)=exit_type==1, MAE (max adverse excursion, pts), MFE. Pooled lift = precision-weighted (n_kept*n_rest/(n_kept+n_rest)) within-book (kept - rest) difference, i.e. "the same book's signals without the location"; week-clustered SE (stratified influence function). Per-book lifts likewise.
Bases for the RULES (section B, separate prereg later): M0 market at signal, S73 = 70/30 plain 3-pt dip (the floor), W0 = pure wait; bases M, N, LIVE-CAL.

## Location features (all causal; read at the last bar CLOSED strictly before the signal second)
* POI behind (store = NTZ-1 poi_store via poi_api, 685 streams, importing only): POI between entry and stop, distance from entry back to its near edge <= D, D in {0 (in-zone, zones only),2,5,10,15,20}; variant fresh (never touched since formation) / mit (touched before = the retest, second touch) / any. Stream-level (10,509 cells), class aggregate (285), timeframe aggregate (224), confluence (number of distinct POI classes / timeframes with a POI within D >= k; 30), defended = class POI behind AND book flag {absorption/iceberg, refill, imbalance support, liquidity-sweep reversal} (216).
* Premium/discount: side-aligned position of the entry in the dealing range: last confirmed fractal-5 swing high/low on 5m/15m/1h/4h/1d, prior-day range, prior-week range, current day / week / session so far; favourable = discount (long) / premium (short) <= 0.2 / 1/3 / 0.5 of the range; complement >= 2/3 as control (40). OTE (62-79% retracement of the last leg in the signal direction) per TF + any (6).
* HTF agreement: Supertrend(10,3), EMA20/50/100 stack, price vs EMA50, Ichimoku (cloud+tenkan/kijun, cloud only), BOS state, on 5m..1d, agree and against; counts of agreeing tools per TF and across 1h/4h/1d (78).
* Book defended at the signal second (l2set bit-plane BL/BS, 10-s windows; side aligned): absorption ratio >=2/3/5/10 with no clear, iceberg, refill/pull-own (3 levels), sweep reversal, imbalance support, big prints, opposing-heavy (control); l2 continuous thresholds (34).
Total 11,422 pooled cells (x 10 books for the per-book rankings).

## Mechanisms and predicted effects (written before seeing numbers)
1. POI behind, fresh, close (D<=5) on PDX/SES/DEV/KZ/ARR-FVG_CE/OB: resting stops/limits cluster at the level so a signal fired at it has a nearer, defended invalidation; predicted +0.3..+1.0 pt/contract and +1..+3 pp P(target) for fresh prior-day/session levels within 5 pts; mit (retest) predicted weaker than fresh (liquidity consumed at the first touch); noise (|lift| < MDE) for most of the 10k cells.
2. Premium/discount: effect is protocol-dependent: reversal books (PE, KB, SM) predicted positive in discount-long/premium-short; momentum books (ST, HM, WT) predicted ~0 or negative (they fire with the move). Pooled can hide it, so per book is reported first.
3. HTF agreement: predicted positive for trend-following books, ~0 for reversal books.
4. Book defended: predicted small positive when POI behind AND flag; flags are rare (<= 25% fire, absorption/iceberg < 1%) so power is the issue.
Honest expectation: the map will mostly show lifts inside MDE (earlier programs found no per-contract edge beyond structure on the same signals); the point of the map is to SEE it.

## Selection (PRE + X' ONLY) and the single recent look
Eligible: n_keep >= 300 in PRE and >= 100 in X', keep_rate_PRE <= 0.85, lift_N > 0 and lift_M > 0 in BOTH PRE and X'. Rank by the inverse-variance combination of the PRE and X' lifts, z = lift/se. Pooled top 300 + per book (eligible n_keep_b >= 80 PRE and >= 30 X') top 30 per book. This selected set (union) and nothing else is looked at in HOLD / L6M / Y26 (+L3M view-only) ONCE, with quarter series, session columns, MAE profile, P(target). The PRE/X' tables of every cell are saved as the map's "unselected" half (sealed recent columns of non-selected cells are never decoded).
Multiplicity: n_cells = 11,422 pooled + per-book ranking (10 x eligible) counted in UF_TRIALS.json side="fz"; White RC + Romano-Wolf + DSR + PBO (qv.program_validity) on the selected cells; cumulative-adjusted p reported beside.
Controls: complement/rest of the same book; random fire-rate placebo (mask permuted within book x session x week, >= 200 draws for selected); random-level placebo for POI cells (each POI displaced by a random offset, touch recomputed, same stream); shuffled-day placebo; time-shifted placebo not applicable to static location (stated).
Tiering: LEAD / CONFIRMED / best-of-F per the memory policy; nothing is killed on the pooled number.
