# DS3_SIZER_EXHAUST - T-SIZER-EXHAUST ranked tables (SZ-CORE, 2026-11-09 16:50Z)

**Label: base S1b-COMB (live D7 v1.5 with the seven state-cut lines), controls NOCUT / UNIF where the owner ran them; first-order unless stage says S2 (exact); entries not live-matched (entry match < .85); in-sample; PRE-PROOF. Post-hoc, Shadow only, no PASS claims.**

Windows as of 2026-11-09 (L6M 20260512-, HOLD 20251111-, PRE 20240201-20250630, X' 20230401-20240131). Cut = maxDD cut vs Q1-A in % (+ = shallower); equal-mean = every cell scaled by one global factor so its L6M mean equals Q1-A's; worst-20 cut = change of the sum of the 20 worst weeks. Placebo = same-count down-sizing within book x session; family p = max-stat over the owner family set (own-draw p in the placebo column). Ranking key: equal-mean L6M maxDD cut (drawdown first), mean is the tie-break. Down-only = live candidates; UP rows are reported only.

**Audit note (SZ-CORE 2026-11-09):** several owner ledgers dropped the carrying weeks (202629-39) from the weekly vector BEFORE computing maxDD (directive: all weeks for maxDD, carrying week dropped from means only). Their L6M/HOLD cuts are overstated (e.g. J pair 18fe3fdc2530: owner 100% L6M cut = 0 maxDD in 14 retained weeks; sz_core all-weeks rescoring gives +37%). The sz_core rescoring of finalists is in the finalist table; ledger numbers are owner numbers until rescored.

## Scoreboard

| family | cells | down-only | LEAD | LEAD+ (placebo ok) | CANDIDATE (first-order screen incl.) | CANDIDATE exact-confirmed |
|--|--|--|--|--|--|--|
| A ER family | 16290 | 12240 | 7194 | 923 | 0 | 0 |
| B Volatility target | 3994 | 3626 | 403 | 536 | 0 | 0 |
| C Equal-risk / parity | 28 | 16 | 14 | 0 | 2 | 0 |
| D Equity-curve / state | 160 | 146 | 72 | 0 | 7 | 0 |
| E Exposure / concentration | 74 | 74 | 37 | 0 | 4 | 0 |
| F Time / session | 118 | 118 | 28 | 5 | 0 | 0 |
| G Signal quality | 1214 | 890 | 379 | 34 | 0 | 0 |
| H Regime | 224 | 149 | 60 | 11 | 0 | 0 |
| I Book-level recent performance | 188 | 186 | 78 | 0 | 3 | 0 |
| J Combinations | 798 | 798 | 313 | 0 | 478 | 0 |
| K P7 | 391 | 391 | 149 | 0 | 134 | 0 |

> **TESTING-DEFECT BOX.** Cells whose new-base d mean equals the old-base page to the dollar: 0.

**USER ADDENDUM 1 (16:30Z) status:** first-order is a SCREEN ONLY; the sizing verdict needs EXACT engine runs for every family top-5 and every reference row on L6M, PRE, X', HOLD. Exact-confirmed cells on this page: 5 of 23479 with any exact window, 0 with all of L6M/PRE/X' (the label carries [EXACT] / [EXACT partial] / [FIRST-ORDER SCREEN ONLY]). Exact queue: autopilot SZ-CORE queue, reference rows first, then family top-5; windows L6M, PRE, X', HOLD.

**Rule (SZ-BASE, 2026-11-09):** first-order pnl-per-lot scaling is a SCREEN ONLY. It cannot see exits: exact shows ladder L cut -76 against -43 first-order and B -143 against -73, and first-order overstates the up-size net by $290k-$820k over 26 months. Exact engine runs are required for every family top-5 and every reference row. Exact rows are labelled by mode: table (static multiplier keyed by book and signal second; signals created by changed exits get m = 1, 4-8% of trades), rule (multiplier computed from causal features at the signal second of any signal), or engine-sizer.

J pairs: identical cells (min and product of 0/1 multipliers) are deduplicated before ranking and before the family null.

### Base-change proof (SZ-BASE, autopilot/SZ_BASE_PROOF.md, first lines)

**PLAIN VERDICT (3 sentences, for the user).** No: sizing is not independent of the exit rule - in the exact engine a lot change moves 82-86% of the affected trades' $ per lot and 6-7% of their exit types (cut counts 5,384 vs 4,731-5,566), so the old-looking signs on S3 (Q1-A shallowest, ladder L -46%, vol-target +29%) are mostly lot arithmetic, and the base itself did change (cuts 56% -> 38% of exits, stops 3% -> 14%, Q1-A L6M maxDD 105k -> 82k), with every family top cell losing most of its edge on the old base (rule-based recompute: A/B leaders keep their cut on volatility but ER cells flip to a mean cost, rank correlation new vs old 0.11-0.44). Defects found: first-order pnl-per-lot scaling cannot see exits (overstates up-size mean by $290k-$820k per 26 months; screen only, exact runs needed), the S3 page dropped carrying weeks before maxDD (L1M = L2M = L3M identical; corrected table in section 7), exact-driver multiplier table unmatched for 4-8% of re-entry signals, and J min/product duplicate cells; nothing is identical to the old page to the dollar and the fixes (all-weeks rescoring done here, exact re-runs ordered) are listed in section 4.

# SZ_BASE_PROOF - is sizing independent of the exit rule, or was something wrong? (SZ-BASE, 2026-11-09 ~16:50Z)
**Post-hoc, Shadow only, no PASS claims. PRE-PROOF (entries not live-matched). Trade-level numpy work only; no exact engine run by SZ-BASE.**

**VERDICT (plain).** The base DID change, a lot (table below): old DS3 S4A engine (V13T ts2, 21,397 trades, 54-57% of exits are per-print TH-L2 cuts) vs S1b-COMB (21,135 trades, 38% state cuts, stop exits 3% -> 14%, X' cuts 51% -> 18%); maxDD of Q1-A L6M 105k -> 82k, PRE 88k -> 140k, X' 81k -> 122k; never-cut NOCUT maxDD L6M 222k -> 191k. So S3 did not run on the old base. Sizing is NOT independent of the exit rule: (a) in the EXACT engine lots change which exit fires (matched trades with changed lots: 82-86% change $ per lot, 6-7% change exit type, state-cut count 5384 -> 4731 sizer-off / 5432 ladder L / 5566 vol-target over 26 months), and first-order overstates the up-size mean by $290k-$820k per 26 months and understates the ladder drawdown (L6M cut: L -43 first-order vs -76 exact, B -73 vs -143); (b) the SIGNS of the reference rows (L and B deeper than Q1-A, vol-target shallower) repeat on every base because they are mostly lot arithmetic (L adds 33% lots, B 64%, vol-target removes 14%) - they are not evidence of exit independence; magnitudes move 20-30 points across bases and "sizer off" even changes sign (L6M cut +2 V0, -34 COMB, +9 NOCUT, +17 UNIF).
**What was wrong (DEFECTS, details section 4):** D1 first-order pnl-per-lot scaling cannot see exits (sz_core.daily, s3_sizer.scale_pnl): screen only, fails on every up-size row - exact engine needed (already ordered by the lead). D2 DS3_TH_S3_SIZER_S1B.md (S3 page): windows L1M = L2M = L3M identical to the dollar for every cell, because instr2_eval drops weeks 202629-39 from the weekly vector BEFORE maxDD (all-weeks rule broken; maxDD there is a 5-week path). Not a cached old trade list; but S3 maxDD/cuts must be re-read from the all-weeks rescore (here). D3 exact driver keys the multiplier table by (book, signal second) of the Q1-A base trades: signals created by changed exits (re-entries, blackout) are not matched (4-8% of exact trades) and get m = 1, and the table is applied after the Q1-A ladder (rounding differs from first-order). D4 J family: min/product pairs of 0/1 multipliers give identical cells (1,318 of 1,573 J rows share their result with another row), inflating the J count and J family p. No cell is identical to the old page to the dollar (0 of 4,110 down-only rescored cells; 133 zero-change cells are 0 on both).
**Old-vs-new for cells (task 2):** the new first-order top-5 of every family do NOT carry to the old base: median cut collapses (example A: +36% mean new cut L6M vs -2% on old V0, +20% on replica HOLD); cut correlation new vs old V0 0.41 (HOLD 0.76), equal-mean-cut rank correlation 0.27 (HOLD 0.55); the top-ranked cells fall to ranks 60-900 of their family. Reading: the first-order "top" is largely in-sample selection plus base-specific exits; no family result is base-independent. Transfer caveat: old trades carry the new M only where the signal matches (V0 59%, HOLD 78%; unmatched M = 1), so old numbers are biased toward smaller changes. Files: /mnt/l2/l2vast/_th_sz/sz_base_old.parquet (old = V0; hold_* = replica HOLD).

## 1. Base-change proof (stack ex O7 for like-for-like; windows as of 2026-11-09, data to 20261030; trades by label day of exit)
Old bases: V0 = research ts2 reference behind DS3_SIZER S4A (run_v13t_ts2; ledger /mnt/l2/l2vast/ds3_base4/defects/kfix/V0_off.pkl = 21,397 trades, $2,520,149.07, ties to the S4A Q1-A row 104,809 / 26,999 L6M exactly; V0_off_nocut.pkl = cut off); replica HOLD = /mnt/l2/l2vast/_th_state/base_b/HOLD (old live per-print cut on the S1b engine). New: S1b-COMB / NOCUT / UNIF.

**Window L6M**

| base | trades | cuts (n / %) | target % | stop % | lock/stack % | other % | mean trade $ | mean lots | $/wk | maxDD $ |
|--|--|--|--|--|--|--|--|--|--|--|
| OLD V0 (DS3 S4A engine) Q1-A | 4919 | 2788 / 56.7 | 39.0 | 3.4 | 0.8 | 0.1 | 147 | 2.13 | 27858 | 104809 |
| OLD V0 NOCUT | 4347 | 0 / 0.0 | 51.6 | 46.3 | 1.6 | 0.5 | 82 | 2.14 | 13738 | 222071 |
| OLD replica HOLD | 5028 | 2723 / 54.2 | 40.8 | 3.5 | 1.4 | 0.2 | 108 | 2.15 | 20789 | 121515 |
| NEW S1b-COMB | 4595 | 1756 / 38.2 | 45.3 | 13.5 | 2.6 | 0.3 | 137 | 2.14 | 24164 | 81955 |
| NEW S1b-NOCUT | 4035 | 0 / 0.0 | 51.4 | 42.1 | 6.1 | 0.4 | 106 | 2.20 | 16467 | 190667 |
| NEW S1b-UNIF | 4400 | 1230 / 28.0 | 47.2 | 20.9 | 3.5 | 0.4 | 86 | 2.16 | 14504 | 181551 |

**Window HOLD**

| base | trades | cuts (n / %) | target % | stop % | lock/stack % | other % | mean trade $ | mean lots | $/wk | maxDD $ |
|--|--|--|--|--|--|--|--|--|--|--|
| OLD V0 (DS3 S4A engine) Q1-A | 8811 | 5002 / 56.8 | 38.5 | 3.3 | 0.8 | 0.7 | 123 | 2.14 | 20870 | 122025 |
| OLD V0 NOCUT | 7885 | 0 / 0.0 | 51.6 | 46.1 | 1.5 | 0.8 | 88 | 2.16 | 13415 | 222071 |
| OLD replica HOLD | 9084 | 5029 / 55.4 | 39.7 | 3.2 | 1.4 | 0.3 | 82 | 2.15 | 14356 | 121515 |
| NEW S1b-COMB | 8258 | 3082 / 37.3 | 44.6 | 14.7 | 2.9 | 0.5 | 99 | 2.15 | 15746 | 105692 |
| NEW S1b-NOCUT | 7190 | 0 / 0.0 | 50.7 | 42.6 | 6.1 | 0.7 | 81 | 2.21 | 11220 | 190667 |
| NEW S1b-UNIF | 7758 | 1926 / 24.8 | 47.1 | 23.5 | 4.0 | 0.6 | 76 | 2.17 | 11400 | 181551 |

**Window PRE**

| base | trades | cuts (n / %) | target % | stop % | lock/stack % | other % | mean trade $ | mean lots | $/wk | maxDD $ |
|--|--|--|--|--|--|--|--|--|--|--|
| OLD V0 (DS3 S4A engine) Q1-A | 7814 | 4202 / 53.8 | 39.7 | 3.3 | 0.5 | 2.7 | 127 | 2.16 | 13202 | 88180 |
| OLD V0 NOCUT | 7367 | 0 / 0.0 | 52.8 | 43.9 | 0.8 | 2.5 | 134 | 2.16 | 13170 | 174642 |

## Reference rows (EXACT engine; every row needed on L6M, HOLD, PRE, X')

| reference cell (EXACT, S1b-COMB, vs exact Q1-A = base) | L6M cut / d mean | HOLD | PRE | X' | complete months |
|--|--|--|--|--|--|
| Q1-A (live reference) | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | all 43 |
| sizer off (x1) | -28.2 / -2367 | -38.6 / -1233 | pending | pending | 26 |
| old ladder L (x0.5/x1.5) | -76.1 / -494 | -41.5 / -98 | pending | pending | 27 |
| B (x1/x1.5, up only) | -142.6 / +2876 | -94.8 / +2598 | pending | pending | 27 |
| ZL-1 vol-target | +28.3 / +10 | +21.1 / -688 | pending | pending | 27 |
| MV-london override | -1.2 / -107 | +6.8 / +28 | pending | pending | 26 |

## Vol-target family (SZ-VT, autopilot/DS3_SIZER_VOLTARGET.md, user top priority; exact engine from the start; first 70 lines, incl. executability rows: scale factor s, max single-trade $ risk, max lots on at once)

# DS3_SIZER_VOLTARGET - T-SIZER-EXHAUST Addendum 2 (SZ-VT), refreshed 2026-11-09 16:49Z
**Post-hoc, Shadow only, no PASS claims. PRE-PROOF (entry match < .85). Numbers below are FIRST-ORDER SCREEN unless a row says [EXACT]. Prereg: autopilot/SZ_VT_PREREG.md (sha in DECISIONS.md).**

@@VERDICT@@

## 0. What was built (B1-B5)
- Features at the signal second (causal, NQ 1-min state bars closed before the signal; code/th_sz_vt/vt_feat.py, 1,859 columns): 53 vol measures (rv1 w10/30/60/120/240, rv5, GK / Parkinson on 1/5/15-min, ATR b1/5/15 n5/14/30/50, EWMA lam .90/.94/.97/.99 on 1/5-min) x sigma_ref windows 5/10/20/40/60 trading days x reference type {all minutes, same half-hour slot, and for 8 core measures all/slot with FOMC/CPI/NFP days excluded from the norm} x {ratio now/median, quantile of the trailing distribution, log z-score}; core dynamics (minutes above 1.25x = spiked vs sustained, ratio now / 30 min ago = vol-of-vol, std of the ratio), direction-aware move of the last 5/15/30/60 min in 1-min sigma, event-day flag; range ratios (overnight/pre/first-30/so-far) and VIX from the AB store.
- Cells scored: **51,408 pooled grid cells** (shapes: continuous (ref/now)^p p .5-2 floor 0/.25/.5, quantile step q .6-.95 to x0.5 or 0, graded 3-step {1,.5,0} at quantile pairs, multiple step 1.1-2.0, z step; with and without the ER sizer) + 1,824 B2 special rules (first signal of the episode per book / stack, spiked vs sustained, direction-aware, rising vs falling vol, event-day) + 850 per-book/session scope cells + 744 B4 interaction cells (stack exposure cap 8-20 lots, post-loss cooldown in high vol) + 864 stack and per-book P&L target-vol cells (trailing 10/15/20 d P&L vol, target = q x expanding median, p .5-2, floor 0-.5). Down-only family on top of Q1-A (onQ1A): 30,031 cells; "alone" (ER sizer removed, M can exceed 1 where ER<.3) are reported in the ledger as UP-labelled, never promoted.
- NOT table-expressible, therefore NOT scored (stated, not hidden): delay-and-recheck entries (changes entry price, needs an engine subclass), the equal-$-risk stop form (wider stop, fewer lots: stop is an engine input), vol-scaled +-R day caps, and vol-governed state-cut arm/persistence (engine rules). They need `state_sizer_b` subclasses (cde_exact.py pattern); listed in section 8 as v1.6 work. Tick count / contracts per second / spread / depth proxies and VXN: the per-second feature store is path-aligned to trades, not to arbitrary signal seconds, VXN is not owned, and VIX stops 2026-10-16; the liquidity proxies are NOT in this page (stated gap). NQ 1-min data runs to 2026-11-05 so all NQ measures cover the whole live week; ES/RTY cross-instrument vol uses 1-s closes that end 2026-10-16 (unavailable after: multiplier 1) and is not part of the screened grid in this version.
- Validation: purged monthly walk-forward of the PICKING procedure per family (26-week training, 7-day embargo, 34 test months 2024-01..2026-10): pick = highest training equal-mean maxDD cut; reported at equal lots, with s fixed from the training window, and at the realised equal OOS mean; time split (pick on weeks <= 2025-06-30, test 2025-07..2026-11); placebo (same lot ratios permuted within book x session, B=200) and a family null over all 30,031 down-only cells (max-stat over the same permutations); held-out live week (frozen file, first-order); EXACT engine for the top cells (section 6).

## 1. Best cell per family (down-only on Q1-A, first-order). Cut = stack maxDD cut vs Q1-A; EQ = at equal L6M mean (lots x s)
| family | cell (feature shape params scope) | cut L6M/PRE/X' (equal lots) | EQ cut L6M/PRE/X' | s | d mean $/wk L6M | worst-20 L6M cell/ref ($k) | Ulcer L6M cell/ref ($k) | skip share | p own / p fam(VT set, all stages) | WF family OOS cut: equal lots / realised equal mean | live wk d$ | stage |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| interactions (cap/cooldown) | q_park15_w12_all10 step [0.6, 0] ["pool"] | +81/+53/+74 | +83/+57/+76 | 0.92 | +1872 | +279/+165 | 4.3 | 0.53 | 0.005 / 0.005 | 48.5 / 27.6 | - | S1 first-order |
| quantile-adaptive (q_*) | q_atr1_n5_all5 step [0.6, 0] ["pool"] | +72/+17/+66 | +74/+24/+69 | 0.91 | +2192 | +193/+165 | 8.7 | 0.58 | 0.005 / 0.020 | 19.3 / -17.3 | -41380 | S1 first-order |
| per-book/session scope | r_ewma5_l90_all40 step [1.1, 0] ["book", "P7", "K7"] | +60/+52/+62 | +64/+56/+65 | 0.91 | +2213 | +220/+165 | 11.8 | 0.39 | 0.005 / 0.090 | 47.0 / 38.6 | -82105 | S1 first-order |
| ratio step/cont (r_*) | r_atr1_n14_all10 step [1.1, 0] ["pool"] | +64/+59/+46 | +68/+63/+52 | 0.89 | +2805 | +267/+165 | 9.0 | 0.61 | 0.005 / 0.109 | 36.8 / -11.4 | -55860 | S1 first-order |
| graded 3-step | q_park1_w10_all10 g3 [0.6, 0.8] ["pool"] | +54/+57/+63 | +61/+63/+69 | 0.85 | +3995 | +245/+165 | 11.7 | 0.37 | 0.005 / 0.109 | 34.0 / 22.4 | -51248 | S1 first-order |
| special (first/dur/dir/vov/evt) | q_gk5_w12_all20 special [] ["pool"] | +30/+53/+53 | +42/+61/+61 | 0.82 | +5122 | +248/+165 | 18.3 | 0.33 | 0.005 / 0.174 | 17.7 / 5.1 | -74770 | S1 first-order |
| session-slot ref | r_gk15_w6_slot10 step [1.1, 0] ["pool"] | +60/+61/+5 | +61/+62/+8 | 0.97 | +663 | +186/+165 | 11.0 | 0.50 | 0.010 / 0.179 | 19.3 / -41.6 | -81535 | S1 first-order |
| continuous (ref/now)^p | r_park1_w10_all40 cont [2, 0] ["pool"] | +33/+54/+57 | +39/+58/+61 | 0.91 | +2239 | +223/+165 | 16.8 | 0.00 | 0.005 / 0.224 | 30.4 / 14.8 | -41810 | S1 first-order |
| z-score | z_ewma5_l97_slot10 step [1.0, 0] ["pool"] | +43/+50/+50 | +45/+52/+52 | 0.95 | +1125 | +243/+165 | 10.9 | 0.29 | 0.005 / 0.572 | 34.1 / 16.2 | -43965 | S1 first-order |
| half (lo=.5) steps | r_gk1_w10_all60 step [1.1, 0.5] ["pool"] | +32/+46/+52 | +39/+51/+57 | 0.89 | +2626 | +232/+165 | 20.0 | 0.00 | 0.005 / 0.597 | 25.0 / 17.7 | -33836 | S1 first-order |

Reading the columns: "skip share" is the share of signals taken to zero lots; a cell that skips 50-60 % of signals and still shows a higher mean at equal lots is selecting the quiet-tape trades, which is the part that fails out of sample (section 2). Worst-20 = sum of the 20 worst weeks (higher = better). The placebo draws permute the same lot ratios within book x session, so p own tests timing, not size.

## 2. Does the picking procedure hold out of sample? (purged monthly WF per family, 34 months; Q1-A OOS mean $16574/wk, OOS maxDD $140k)
| family | cells | OOS maxDD cut, equal lots | d mean $/wk (equal lots) | OOS cut at REALISED equal mean (s_oos) | s_oos | OOS cut with s fixed from training | d mean $/wk (s train) | worst-20 cut (s train) | months on Q1-A | holds? |
|---|---|---|---|---|---|---|---|---|---|---|
| per-book/session scope | 850 | 47.0 | -2274 | 38.6 | 1.16 | 40.9 | -3124 | 25.3 | 0/34 | YES (first-order) |
| stack/book P&L target-vol | 864 | 45.2 | -3300 | 31.6 | 1.25 | 28.4 | -1354 | 15.6 | 0/34 | YES (first-order) |
| interactions (cap/cooldown) | 744 | 48.5 | -4776 | 27.6 | 1.40 | 36.2 | -3981 | 36.8 | 0/34 | YES (first-order) |
| composite graded/half (no zero) | 5220 | 32.4 | -2063 | 22.8 | 1.14 | 24.6 | -2879 | 20.9 | 0/34 | YES (first-order) |
| composite consensus (all stages comp) | 7018 | 42.3 | -4283 | 22.2 | 1.35 | 24.5 | -3758 | 22.3 | 0/34 | YES (first-order) |
| graded 3-step | 4978 | 34.0 | -2651 | 21.5 | 1.19 | 33.8 | -3988 | 30.3 | 0/34 | YES (first-order) |
| half (lo=.5) steps | 9204 | 25.0 | -1471 | 17.7 | 1.10 | 28.8 | -2412 | 21.4 | 0/34 | YES (first-order) |
| composite pooled scope | 388 | 38.6 | -4214 | 17.6 | 1.34 | 28.1 | -3818 | 22.1 | 0/34 | YES (first-order) |
| z-score | 3660 | 34.1 | -3550 | 16.2 | 1.27 | 10.8 | -6238 | 26.9 | 0/34 | YES (first-order) |
| continuous (ref/now)^p | 9480 | 30.4 | -3082 | 14.5 | 1.23 | 27.6 | -3264 | 15.7 | 0/34 | YES (first-order) |
| event-excluded ref | 3353 | 35.8 | -4971 | 8.2 | 1.43 | -12.8 | -4543 | 14.5 | 0/34 | weak |
| special (first/dur/dir/vov/evt) | 1823 | 17.7 | -2208 | 5.1 | 1.15 | 12.8 | -4041 | 24.1 | 0/34 | YES (first-order) |
| vol-skip multiples only (old AB style r_*, lo=0) | 2417 | 43.8 | -7085 | 1.8 | 1.75 | 23.0 | -7033 | 24.5 | 0/34 | weak |
| ratio step/cont (r_*) | 12177 | 36.8 | -7174 | -11.4 | 1.76 | 11.6 | -7115 | 19.2 | 0/34 | NO |
| quantile-adaptive (q_*) | 9749 | 19.3 | -5170 | -17.3 | 1.45 | 8.6 | -5280 | 28.6 | 0/34 | NO |
| session-slot ref | 12776 | 19.3 | -7126 | -41.6 | 1.75 | 8.6 | -7321 | 16.6 | 0/34 | NO |
| ALL B (onQ1A) | 37049 | 19.3 | -7229 | -43.2 | 1.77 | 8.6 | -7240 | 25.5 | 0/34 | NO |

Reading: s fixed from training leaves the OOS mean 7-20 % below Q1-A in most families (the training-window s is not the OOS s), so "cut at the realised equal mean" is the honest equal-mean column; the trained-s column shows the cut that would actually be live with the mean given up in the next column. Simple size-down-everything benchmark: cutting maxDD by x % costs x % of the mean = about $118/wk of mean per $1k of maxDD (Q1-A mean / maxDD); a family only buys something if its rate is below that.

## 3. Time split: pick on weeks up to 2025-06-30 (118 weeks), test 2025-07..2026-11 (70 weeks)
| top-k by training equal-mean cut | test EQ cut (s from training), median | share of picks with test EQ cut > 0 | test mean / Q1-A mean (s from training) | test EQ cut with test-fitted s, median |
|---|---|---|---|---|
| 1 | 9.0 | 1.00 | 0.73 | -23.8 |
| 5 | -17.2 | 0.40 | 0.73 | -58.9 |
| 20 | 13.1 | 0.70 | 0.80 | -10.8 |
| 50 | 17.1 | 0.70 | 0.86 | -8.0 |
| 300 | -0.8 | 0.48 | 0.86 | -21.4 |

All 36844 down-only cells: rank correlation of training score vs test EQ cut 0.27; share of cells with positive test EQ cut (s from training) 0.59, median 3.0 %. 

## 4. B5 - scaled-to-Q1-A-mean rows and executability ("if we double the size isn't it better?")
Scale factor s = Q1-A L6M mean / cell L6M mean (s < 1: the cell earns more than Q1-A at equal lots and is scaled DOWN to match; s > 1: scaled UP). Largest single-trade risk = lots x stop (59.9 pts median, 56 P7, 40 O7) x $20. Max lots on at once = peak sum of open lots in the base trade list at the cell's lots (x s). The P7 7-lot table becomes 7 x s lots; slices, participation cap and margin were NOT re-simulated here: the table shows how many lots the P7 table and the stack would hold at scale s (margin scales with max lots at once), and the exact engine runs in section 6 apply the real slicing at unscaled lots.
| cell | s | maxDD L6M cell / scaled ($k) | Q1-A maxDD L6M ($k) | worst-20 scaled / ref ($k) | Ulcer scaled / ref ($k) | Calmar L6M cell (ann mean / maxDD) | largest trade risk: Q1-A / cell / scaled ($k) | max lots at once: Q1-A / scaled | P7 table x s |
|---|---|---|---|---|---|---|---|---|---|
| interactions (cap/ q_park15_w12_all10 [0.6, 0] | 0.92 | 14.9 / 13.8 | 79.9 | 258 / 165 | 3.9 / - | 84.8 | 7.8 / 7.8 / 7.2 | 20 / 14 | 6.5 |
| quantile-adaptive  q_atr1_n5_all5 [0.6, 0] | 0.91 | 22.8 / 20.7 | 79.9 | 176 / 165 | 7.9 / - | 56.1 | 7.8 / 7.8 / 7.1 | 20 / 17 | 6.4 |
| per-book/session s r_ewma5_l90_all40 [1.1, 0] | 0.91 | 31.7 / 28.9 | 79.9 | 201 / 165 | 10.8 / - | 42.0 | 7.8 / 7.8 / 7.2 | 20 / 17 | 6.4 |
| ratio step/cont (r r_atr1_n14_all10 [1.1, 0] | 0.89 | 29.1 / 25.9 | 79.9 | 237 / 165 | 8.0 / - | 45.0 | 7.8 / 7.8 / 7.0 | 20 / 17 | 6.2 |
| graded 3-step q_park1_w10_all10 [0.6, 0.8] | 0.85 | 37.1 / 31.5 | 79.9 | 208 / 165 | 9.9 / - | 36.9 | 7.8 / 7.8 / 6.7 | 20 / 16 | 5.9 |

## Family A - ER family

ER family: 16290 cells (12240 down-only); best by equal-mean L6M maxDD cut: ER-NQ er_nq_b3_n14 t2 [0.6, 0.0, 1.0] cuts L6M maxDD +83% at equal lots (d mean -10512 $/wk) and +67% at equal mean (PRE +14%, X' +19%); placebo p 0.05, family p 1.00, WF n/a -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ er_nq_b3_n14 t2 | [0.6, 0.0, 1.0] | +83 / +21 / +55 / +58 | -30 | +85 | -10512 | +67 / -53 / +14 / +19 | 42.4 | 91% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.05 | 1.00 |  | -103485 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b5_n45 t2 | [0.25, 0.0, 1.0] | +64 / +1 / +44 / -8 | -52 | +63 | -4365 | +55 / -22 / +31 / -34 | 32.2 | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 |  | -38280 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b3_n14 t2 | [0.55, 0.0, 1.0] | +66 / +26 / +47 / +37 | -3 | +75 | -6998 | +49 / -11 / +20 / +6 | 27.4 | 88% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.09 | 1.00 |  | -91335 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b30_n10 t2 | [0.5, 0.0, 1.0] | +52 / -12 / +17 / +35 | -53 | +61 | -1968 | +47 / -23 / +9 / +29 | 26.2 | 78% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 |  | -72540 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b5_n60 t3 | [0.2, 0.4, 0.25, 0.5, 1.0] | +58 / +1 / +46 / +30 | +1 | +60 | -4590 | +47 / -25 / +31 / +11 | 26.1 | 35% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | -35797 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b30_n10 t2 | [0.5, 0.0, 1.0] | +63 / +25 / +44 / +45 | -55 | +61 | -6723 | +46 / -10 / +18 / +20 | 25.5 | 70% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 |  | -75660 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b5_n45 t2 | [0.25, 0.0, 1.0] | +65 / +27 / +51 / -1 | -82 | +63 | -8154 | +45 / -15 / +23 / -59 | 26.5 | 73% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.08 | 1.00 |  | -49405 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b5_n5 t2 | [0.1, 0.0, 1.0] | +17 / -30 / -3 / -31 | +157 | +29 | +11724 | +45 / +14 / +31 / +13 | 27.6 | 44% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | -25004 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b5_n5 t2 | [0.1, 0.0, 1.0] | +36 / -9 / +8 / +9 | +62 | +42 | +3125 | +44 / +5 / +20 / +21 | 24.8 | 10% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.06 | 1.00 |  | -32210 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| ER-xinst er_max2_b15_n20 t3 | [0.35, 0.45, 0.25, 0.5, 1.0] | +44 / -24 / +35 / +11 | +22 | +57 | -300 | +44 / -26 / +34 / +10 | 27.4 | 33% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | -32510 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ er_nq_b15_n14 t2 | [0.55, 0.5, 1.5] | +21 / +2 / -18 / -57 | +51 | +38 | +9453 | +44 / +30 / +17 / -12 | 26.7 | 32% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.05 | 1.00 |  | +46687 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b15_n14 t2 | [0.5, 0.5, 1.5] | +10 / -9 / +10 / -59 | +53 | +28 | +11306 | +39 / +26 / +39 / -8 | 25.2 | 36% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | +64797 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b3_n14 t2 | [0.55, 0.5, 1.5] | +21 / -21 / +30 / -25 | +110 | +30 | +7608 | +38 / +6 / +46 / +3 | 28.4 | 34% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | -11846 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family B - Volatility target

Volatility target: 3994 cells (3626 down-only); best by equal-mean L6M maxDD cut: VOL-pool vr_park_w10_g20 stepv [1.25, 0.0] cuts L6M maxDD +53% at equal lots (d mean +3560 $/wk) and +59% at equal mean (PRE +56%, X' +71%); placebo p 0.02, family p 0.28, WF n/a -> LEAD+ (placebo ok; WF n/a or fail) [EXACT partial].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-pool vr_park_w10_g20 stepv | [1.25, 0.0] | +53 / +58 / +49 / +67 | +35 | +64 | +3560 | +59 / +63 / +56 / +71 | 35.8 | 56% | +4 /  /  /  (+1416; table mode) | +54 / -1.5 / +98 | 0.02 | 0.28 |  | -48050 | S1 | LEAD+ (placebo ok; WF n/a or fail) [EXACT partial] |
| VOL-pool vr_gk_w10_g20 stepv | [1.25, 0.0] | +54 / +59 / +58 / +55 | +7 | +66 | +2243 | +58 / +63 / +62 / +59 | 34.8 | 56% | +19 /  /  /  (+1498; table mode) | +63 / -9.3 / +9 | 0.02 | 0.28 |  | -63235 | S1 | LEAD+ (placebo ok; WF n/a or fail) [EXACT partial] |
| VOL-pool vr_ewma5_l90_g20 stepv | [1.25, 0.0] | +51 / +48 / +47 / +47 | +56 | +66 | +3658 | +57 / +55 / +54 / +54 | 35.7 | 54% | FIRST-ORDER SCREEN ONLY | +53 / -2.5 / +14 | 0.02 | 0.57 |  | -86585 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_atr_b1_n5_g20 stepv | [1.25, 0.0] | +32 / +30 / +21 / +56 | +96 | +66 | +13166 | +57 / +56 / +50 / +72 | 34.0 | 78% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.32 |  | -13954 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_rv1_w10_g20 stepv | [1.25, 0.0] | +47 / +14 / -38 / +52 | +141 | +59 | +5702 | +56 / +29 / -14 / +60 | 39.2 | 78% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 0.40 |  | -53054 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_gk_w10_g20 stepv | [1.25, 0.0] | +33 / +46 / +48 / +47 | +47 | +54 | +11037 | +54 / +63 / +65 / +64 | 33.4 | 77% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.12 |  | -36404 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_rv5_w48_bk stepv | [1.25, 0.0] | +22 / +7 / +20 / +9 | +130 | +50 | +15192 | +54 / +44 / +52 / +46 | 31.6 | 63% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.71 |  | -87274 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_atr_b15_n5_g20 stepv | [1.25, 0.0] | +28 / +38 / +36 / +51 | +94 | +43 | +12779 | +54 / +60 / +58 / +68 | 32.9 | 75% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.28 |  | -70190 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_atr_b1_n5_g20 stepv | [1.25, 0.0] | +48 / +47 / +47 / +67 | +24 | +66 | +2579 | +53 / +52 / +52 / +71 | 31.0 | 58% | FIRST-ORDER SCREEN ONLY | +49 / -1.6 / +164 | 0.03 | 0.68 |  | -42935 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_atr_b15_n5_g20 stepv | [1.25, 0.0] | +47 / +49 / +55 / +62 | +22 | +55 | +1720 | +51 / +53 / +58 / +65 | 31.1 | 51% | FIRST-ORDER SCREEN ONLY | +60 / -12.4 / +0 | 0.02 | 0.28 |  | -80055 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-pool vr_gk_w10_g20 pow | [1.0, 0.5, 1.5] | +30 / +26 / +34 / +32 | +77 | +36 | +5653 | +45 / +42 / +48 / +46 | 25.3 | 36% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.97 |  | -20343 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_atr_b15_n5_g20 pow | [1.0, 0.5, 1.5] | +26 / +21 / +16 / +31 | +50 | +29 | +7156 | +43 / +40 / +36 / +47 | 26.7 | 38% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | -23055 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_park_w10_g20 pow | [1.0, 0.5, 1.5] | +31 / +25 / +30 / +32 | +61 | +34 | +4187 | +42 / +37 / +41 / +43 | 24.0 | 36% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | -18559 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family C - Equal-risk / parity

Equal-risk / parity: 28 cells (16 down-only); best by equal-mean L6M maxDD cut: riskcap_per_trade R$3600 cuts L6M maxDD +31% at equal lots (d mean -8513 $/wk) and +2% at equal mean (PRE +18%, X' +31%); placebo p 0.02, family p 1.00, WF +32 -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| riskcap_per_trade | R$3600 | +31 / +34 / +42 / +51 | -8 | +12 | -8513 | +2 / +7 / +18 / +31 | 19.4 | 22% | FIRST-ORDER SCREEN ONLY | +1 / +30.0 / +2 | 0.02 | 1.00 | +32 | -38377 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| volparity_down | win120_refmed | +56 / +31 / +46 / +37 | +33 | +4 | -16574 | -2 / -61 / -24 / -46 | 18.5 | 30% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.04 | 1.00 | +32 |  | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| riskcap_per_trade | R$4800 | +20 / +14 / +21 / +19 | -16 | +2 | -6658 | -4 / -11 / -2 / -6 | 18.3 | 8% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.31 | 1.00 | +32 | -27016 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| volparity_down | win60_refmed | +56 / +28 / +49 / +32 | +39 | -4 | -16945 | -6 / -73 / -21 / -62 | 17.9 | 30% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.09 | 1.00 | +32 |  | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| riskcap_per_trade | R$6000 | +14 / +9 / +17 / +18 | -17 | -3 | -5889 | -7 / -14 / -3 / -3 | 17.7 | 7% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.43 | 1.00 | +32 | -17840 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| riskcap_per_trade | R$2400 | +33 / +38 / +55 / +64 | +21 | -6 | -13123 | -22 / -12 / +17 / +34 | 15.5 | 24% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.34 | 1.00 | +32 | -51309 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| volparity_down | win20_refmin | +57 / +50 / +70 / +74 | +46 | -8 | -18825 | -22 / -40 / +15 / +28 | 15.5 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.26 | 1.00 | +32 |  | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| esparity_down | last100tr_refmin | +57 / +50 / +70 / +68 | +47 | -7 | -18926 | -22 / -42 / +14 / +10 | 15.5 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.20 | 1.00 | +32 |  | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| esparity_down | last50tr_refmin | +57 / +50 / +70 / +72 | +47 | -7 | -18847 | -22 / -41 / +15 / +22 | 15.5 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.22 | 1.00 | +32 |  | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| volparity_down | win60_refmin | +57 / +50 / +70 / +37 | +46 | -7 | -18851 | -22 / -43 / +15 / -77 | 15.5 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.17 | 1.00 | +32 |  | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| volparity_up | win60_refmed_clip.5-1.5 | +35 / +16 / +45 / +20 | -2 | +11 | -10504 | -2 / -31 / +14 / -26 | 18.7 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.18 | 1.00 | +32 |  | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| volparity_up | win20_refmin_clip.5-1.5 | +47 / +39 / +43 / +54 | +26 | +1 | -14104 | -2 / -18 / -10 / +11 | 18.6 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.18 | 1.00 | +32 |  | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| volparity_up | win120_refmin_clip.5-1.5 | +47 / +39 / +43 / +29 | +26 | +1 | -14106 | -2 / -18 / -10 / -38 | 18.6 | 38% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.20 | 1.00 | +32 |  | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family D - Equity-curve / state

Equity-curve / state: 160 cells (146 down-only); best by equal-mean L6M maxDD cut: week_loss_stack X20000_f0.00 cuts L6M maxDD +44% at equal lots (d mean -2097 $/wk) and +40% at equal mean (PRE +4%, X' -54%); placebo p 0.01, family p 1.00, WF +39 -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| week_loss_stack | X20000_f0.00 | +44 / +14 / +11 / -42 | +3 | +44 | -2097 | +40 / +7 / +4 / -54 | 31.6 | 24% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 1.00 | +39 | +0 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| consec_loss | stack_k5_f0.00 | +34 / +15 / +47 / -47 | -46 | +38 | +413 | +34 / +16 / +48 / -45 | 28.9 | 22% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +39 | -5710 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| consec_loss | stack_k4_f0.00 | +39 / -44 / +27 / -48 | -38 | +53 | -2521 | +33 / -57 / +20 / -62 | 28.4 | 32% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.08 | 1.00 | +39 | -84210 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| dayloss_stack$ | X16000_f0.00 | +30 / -49 / +18 / +5 | -33 | +35 | +498 | +31 / -47 / +19 / +7 | 27.5 | 9% | FIRST-ORDER SCREEN ONLY | +17 / +13.1 / +5 | 0.02 | 1.00 | +39 | +0 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| consec_loss | book_k3_f0.00 | +35 / +5 / +44 / -8 | +1 | +24 | -3122 | +27 / -6 / +38 / -21 | 26.1 | 14% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.06 | 1.00 | +39 | -72285 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| eqdd_book_20d_R | Y1R_f0.50_sticky | +47 / +41 / +45 / +48 | +26 | +25 | -8535 | +24 / +16 / +22 / +27 | 25.1 | 33% | +24 /  /  /  (-5611; engine-sizer mode) | -6 / +52.1 / +115 | 0.04 | 0.85 | +39 | +0 | S1 | CANDIDATE (own-p only; family p 0.85) [EXACT partial] |
| eqdd_stack_20d | Y10000_f0.50_live | +41 / +37 / +43 / +13 | +29 | +17 | -6609 | +24 / +18 / +26 / -12 | 24.8 | 26% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 | +39 | +0 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| eqdd_book_20d_R | Y4R_f0.25_sticky | +44 / +25 / +51 / +36 | +40 | +33 | -8025 | +23 / -3 / +33 / +12 | 24.7 | 29% | FIRST-ORDER SCREEN ONLY | -27 / +71.2 / +118 | 0.05 | 1.00 | +39 | +0 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| eqdd_stack_20d | Y20000_f0.50_live | +36 / +26 / +42 / +14 | +23 | +11 | -5357 | +22 / +9 / +29 / -5 | 24.3 | 21% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +39 | +0 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| week_loss_stack | X10000_f0.50 | +24 / +7 / +36 / -49 | +7 | +24 | -1497 | +20 / +2 / +32 / -57 | 23.6 | 10% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +39 | +0 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| eqdd_stack_UP_at_high | Y20000_f0.50_up1.25 | +36 / +28 / +40 / -14 | +32 | +13 | -4836 | +23 / +14 / +29 / -37 | 24.6 | 29% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.04 | 1.00 | +39 | +25118 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| antimartingale_UP | book_n4_x1.25 | +0 / -1 / -1 / -1 | -2 | -2 | -54 | -0 / -1 / -1 / -1 | 18.9 | 1% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.17 | 1.00 | +39 | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| antimartingale_UP | book_n3_x1.50 | +5 / -2 / -6 / -6 | -8 | -16 | -5268 | -16 / -25 / -29 / -29 | 16.3 | 4% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.28 | 1.00 | +39 | -3448 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family E - Exposure / concentration

Exposure / concentration: 74 cells (74 down-only); best by equal-mean L6M maxDD cut: corr_same_side N30min_f0.5_ge1_others cuts L6M maxDD +37% at equal lots (d mean -6495 $/wk) and +19% at equal mean (PRE +10%, X' -13%); placebo p 0.06, family p 1.00, WF +11 -> CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| corr_same_side | N30min_f0.5_ge1_others | +37 / +16 / +30 / +13 | +23 | +21 | -6495 | +19 / -8 / +10 / -13 | 23.5 | 19% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.06 | 1.00 | +11 | -35277 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| newentry_haircut_day_dd | Y15000_f0.0 | +31 / -42 / +39 / -34 | +11 | +17 | -5255 | +16 / -73 / +25 / -64 | 22.5 | 19% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.14 | 1.00 | +11 | +0 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| total_lots_cap | cap4_skip | +58 / +11 / +71 / +39 | +40 | +34 | -14993 | +13 / -84 / +40 / -26 | 21.8 | 32% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 | +11 | -73240 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| same_side_lots_cap | cap6_skip | +41 / +40 / +45 / +55 | -1 | +44 | -9614 | +12 / +10 / +18 / +33 | 21.6 | 15% | FIRST-ORDER SCREEN ONLY | +7 / +34.1 / +48 | 0.05 | 1.00 | +11 | -53550 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| total_lots_cap | cap6_skip | +41 / +46 / +45 / +40 | +8 | +40 | -10409 | +8 / +16 / +15 / +7 | 20.7 | 18% | FIRST-ORDER SCREEN ONLY | +21 / +19.9 / +45 | 0.06 | 1.00 | +11 | -52835 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| same_side_lots_cap | cap4_trunc | +52 / +27 / +40 / +47 | +35 | +25 | -14135 | +7 / -41 / -17 / -3 | 20.4 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.08 | 1.00 | +11 | -35944 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| newentry_haircut_day_dd | Y15000_f0.5 | +12 / -24 / +29 / -0 | +0 | +11 | -1616 | +7 / -31 / +25 / -6 | 20.4 | 4% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.13 | 1.00 | +11 | +0 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| same_side_lots_cap | cap12_skip | +6 / -1 / +2 / -21 | +4 | +4 | +105 | +7 / -1 / +3 / -20 | 20.3 | 1% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 | +11 | -18780 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| newentry_haircut_day_dd | Y24000_f0.0 | +1 / -19 / +29 / -3 | -25 | +21 | +1689 | +7 / -13 / +32 / +2 | 20.3 | 5% | FIRST-ORDER SCREEN ONLY | +7 / -5.3 / +1 | 0.12 | 1.00 | +11 | +0 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| total_lots_cap | cap12_skip | +6 / -1 / +2 / -21 | +2 | +4 | -128 | +6 / -1 / +2 / -21 | 20.2 | 2% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.12 | 1.00 | +11 | -27180 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

## Family F - Time / session

Time / session: 118 cells (118 down-only); best by equal-mean L6M maxDD cut: dow {"dow": 2, "m": 0} cuts L6M maxDD +51% at equal lots (d mean +1171 $/wk) and +54% at equal mean (PRE +8%, X' +39%); placebo p 0.01, family p 1.00, WF n/a -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| dow | {"dow": 2, "m": 0} | +51 / +27 / +4 / +35 | -12 |  | +1171 | +54 / +31 / +8 / +39 |  | 20% | FIRST-ORDER SCREEN ONLY | +23 / +28.2 / +1 | 0.01 | 1.00 |  | -28160 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| slot48 | {"m": 0, "slot": 8} | +12 / -3 / -1 / -12 | +28 |  | +2552 | +21 / +7 / +9 / -1 |  | 3% | FIRST-ORDER SCREEN ONLY | +7 / +5.4 / +19 | 0.29 | 1.00 |  | +3890 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| dow | {"dow": 0, "m": 0} | +24 / -119 / +22 / +52 | -42 |  | -1865 | +18 / -138 / +15 / +48 |  | 19% | FIRST-ORDER SCREEN ONLY | +11 / +12.9 / +141 | 0.08 | 1.00 |  | -28440 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| dow | {"dow": 2, "m": 0.5} | +15 / +11 / +6 / +23 | -1 |  | -50 | +15 / +10 / +6 / +23 |  | 7% | FIRST-ORDER SCREEN ONLY | +7 / +7.7 / +21 | 0.05 | 1.00 |  | -6193 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| slot48 | {"m": 0, "slot": 40} | +12 / -6 / -8 / +16 | +7 |  | +139 | +12 / -5 / -8 / +16 |  | 3% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.05 | 1.00 |  | +3120 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| slot48 | {"m": 0, "slot": 10} | +9 / +3 / +5 / +4 | +16 |  | +652 | +12 / +6 / +7 / +6 |  | 2% | FIRST-ORDER SCREEN ONLY | +13 / -3.8 / +4 | 0.29 | 1.00 |  | -8855 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| slot48 | {"m": 0, "slot": 22} | +8 / +4 / +5 / +9 | +17 |  | +883 | +11 / +7 / +8 / +12 |  | 5% | FIRST-ORDER SCREEN ONLY | -1 / +8.7 / +160 | 0.30 | 1.00 |  | -10145 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| slot48 | {"m": 0, "slot": 15} | +2 / -21 / +9 / +2 | +11 |  | +2463 | +11 / -11 / +17 / +11 |  | 2% | FIRST-ORDER SCREEN ONLY | -18 / +19.9 / +191 | 0.07 | 1.00 |  | +5425 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| slot48 | {"m": 0.5, "slot": 15} | +6 / -4 / +3 / +0 | +7 |  | +1116 | +10 / +0 / +7 / +4 |  | 1% | FIRST-ORDER SCREEN ONLY | -6 / +12.0 / +178 | 0.02 | 1.00 |  | +2672 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| slot48 | {"m": 0.5, "slot": 8} | +6 / -3 / +2 / -2 | +12 |  | +902 | +9 / +1 / +5 / +2 |  | 1% | FIRST-ORDER SCREEN ONLY | +1 / +5.2 / +86 | 0.17 | 1.00 |  | +1382 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

## Family G - Signal quality

Signal quality: 1214 cells (890 down-only); best by equal-mean L6M maxDD cut: qgate {"feat": "nA40", "m": 0, "q": 0.5, "tail": "low"} cuts L6M maxDD +90% at equal lots (d mean -11981 $/wk) and +78% at equal mean (PRE -7%, X' -128%); placebo p 0.20, family p 1.00, WF n/a -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate | {"feat": "nA40", "m": 0, "q": 0.5, "tail": "low"} | +90 / +18 / +53 / +0 | -40 |  | -11981 | +78 / -88 / -7 / -128 |  | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.20 | 1.00 |  | -74295 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate | {"feat": "nA40", "m": 0, "q": 0.3, "tail": "low"} | +90 / +18 / +53 / +0 | -40 |  | -11981 | +78 / -88 / -7 / -128 |  | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.22 | 1.00 |  | -74295 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate | {"feat": "nA40", "m": 0, "q": 0.2, "tail": "low"} | +90 / +18 / +53 / +0 | -40 |  | -11981 | +78 / -88 / -7 / -128 |  | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.27 | 1.00 |  | -74295 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate | {"feat": "nA40", "m": 0, "q": 0.1, "tail": "low"} | +90 / +18 / +53 / +0 | -40 |  | -11981 | +78 / -88 / -7 / -128 |  | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.30 | 1.00 |  | -74295 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate | {"feat": "nA20", "m": 0, "q": 0.2, "tail": "low"} | +87 / +57 / +58 / +0 | -76 |  | -16790 | +39 / -101 / -95 / -369 |  | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.49 | 1.00 |  | -96325 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate | {"feat": "nA20", "m": 0, "q": 0.1, "tail": "low"} | +87 / +57 / +58 / +0 | -76 |  | -16790 | +39 / -101 / -95 / -369 |  | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.66 | 1.00 |  | -96325 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate | {"feat": "nA20", "m": 0, "q": 0.5, "tail": "low"} | +87 / +57 / +58 / +0 | -76 |  | -16790 | +39 / -101 / -95 / -369 |  | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.66 | 1.00 |  | -96325 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate | {"feat": "nA20", "m": 0, "q": 0.3, "tail": "low"} | +87 / +57 / +58 / +0 | -76 |  | -16790 | +39 / -101 / -95 / -369 |  | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.61 | 1.00 |  | -96325 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate | {"feat": "twap_slope_sg", "m": 0, "q": 0.5, "tail": "low"} | +43 / -61 / +32 / +0 | -27 |  | -2792 | +35 / -84 / +22 / -14 |  | 45% | FIRST-ORDER SCREEN ONLY | -18 / +61.3 / +966 | 0.30 | 1.00 |  | -28565 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate_x_er | {"er": "erhigh", "feat": "f_r_ab8", "m": 0, "q": 0.5, "tail": "low"} | +46 / +4 / +17 / +0 | -17 |  | -4651 | +32 / -21 / -4 / -25 |  | 17% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.24 | 1.00 |  | +0 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate_x_er | {"er": "erlow", "feat": "f_ema20_rel", "m": 1.5, "q": 0.5, "tail": "lo | +14 / -8 / +4 / +0 | +60 |  | +4952 | +28 / +10 / +20 / +17 |  | 14% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 1.00 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| qgate_UP | {"feat": "nA40", "m": 1.5, "q": 0.2, "tail": "high"} | +6 / -26 / -3 / +0 | +68 |  | +4992 | +23 / -3 / +16 / +19 |  | 24% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 1.00 |  | +19148 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| qgate_x_er | {"er": "erlow", "feat": "f_tot_rel_base", "m": 1.5, "q": 0.5, "tail":  | +8 / -22 / -2 / +0 | +56 |  | +4543 | +23 / -3 / +14 / +16 |  | 20% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family H - Regime

Regime: 224 cells (149 down-only); best by equal-mean L6M maxDD cut: regime {"cond": "adx5_ge20", "m": 0.5} cuts L6M maxDD +41% at equal lots (d mean -2574 $/wk) and +33% at equal mean (PRE +29%, X' +35%); placebo p 0.01, family p 1.00, WF n/a -> LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "adx5_ge20", "m": 0.5} | +41 / +20 / +38 / +43 | +9 |  | -2574 | +33 / +9 / +29 / +35 |  | 30% | FIRST-ORDER SCREEN ONLY | +29 / +12.3 / +18 | 0.01 | 1.00 |  | -33303 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| regime | {"cond": "on_ratio_ge0.8", "m": 0} | +41 / -19 / +44 / -74 | +2 |  | -5549 | +26 / -48 / +30 / -118 |  | 35% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.74 | 1.00 |  | -62715 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime | {"cond": "prior_range_day", "m": 0} | +39 / +1 / +9 / -107 | -5 |  | -5768 | +23 / -25 / -16 / -162 |  | 29% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.60 | 1.00 |  | -59710 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime | {"cond": "gap_with_ge0.25", "m": 0.5} | +35 / +16 / +16 / +8 | -26 |  | -3890 | +22 / -2 / -1 / -11 |  | 16% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.53 | 1.00 |  | -6578 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime | {"cond": "on_ratio_ge0.8", "m": 0.5} | +23 / +8 / +31 / +1 | +19 |  | -715 | +21 / +5 / +29 / -2 |  | 11% | FIRST-ORDER SCREEN ONLY | +16 / +7.8 / +18 | 0.07 | 1.00 |  | -17583 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| regime | {"cond": "od_with_ge0.05", "m": 0} | +21 / +17 / -0 / +29 | +19 |  | -17 | +21 / +17 / -0 / +29 |  | 17% | FIRST-ORDER SCREEN ONLY | -9 / +30.0 / +265 | 0.65 | 1.00 |  | -515 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| regime | {"cond": "on_ratio_ge1.0", "m": 0.5} | +21 / +4 / +15 / +4 | +15 |  | -652 | +19 / +1 / +13 / +2 |  | 7% | FIRST-ORDER SCREEN ONLY | +16 / +5.4 / +14 | 0.12 | 1.00 |  | -18285 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime | {"cond": "od_against_ge0.05", "m": 0} | +9 / +3 / +13 / -30 | +28 |  | +2989 | +19 / +14 / +22 / -16 |  | 9% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.35 | 1.00 |  | -2340 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime | {"cond": "ib_ext_with_ge0.25", "m": 0} | +15 / -4 / +4 / -1 | +24 |  | +910 | +18 / -0 / +8 / +3 |  | 6% | FIRST-ORDER SCREEN ONLY | +6 / +8.8 / +80 | 0.26 | 1.00 |  | -11905 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime | {"cond": "od_with_ge0.10", "m": 0} | +21 / +17 / +5 / +13 | +3 |  | -1073 | +17 / +13 / -0 / +8 |  | 15% | FIRST-ORDER SCREEN ONLY | -10 / +30.4 / +259 | 0.87 | 1.00 |  | -515 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime_UP | {"cond": "twap_slope_with_ge0.25", "m": 1.5} | -2 / -45 / -13 / -39 | +73 |  | +8824 | +26 / -5 / +18 / -1 |  | 23% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.25 | 1.00 |  | +34999 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| regime_UP | {"cond": "both_agree_15", "m": 1.5} | -26 / -48 / -50 / -48 | +120 |  | +15295 | +25 / +12 / +11 / +12 |  | 74% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| regime_UP | {"cond": "both_agree_60", "m": 1.5} | -25 / -39 / -39 / -3 | +107 |  | +13360 | +23 / +15 / +14 / +37 |  | 76% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 0.99 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family I - Book-level recent performance

Book-level recent performance: 188 cells (186 down-only); best by equal-mean L6M maxDD cut: I5 stack rolling Calmar {"D": 20, "mult": 0.0, "x": 3.0} cuts L6M maxDD +68% at equal lots (d mean -8191 $/wk) and +49% at equal mean (PRE +27%, X' +48%); placebo p 0.05, family p 1.00, WF +41 -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| I5 stack rolling Calmar | {"D": 20, "mult": 0.0, "x": 3.0} | +68 / +24 / +55 / +68 | -102 | +52 | -8191 | +49 / -23 / +27 / +48 | 27.1 | 72% | FIRST-ORDER SCREEN ONLY | -14 / +82.6 / +169 | 0.05 | 1.00 | +41 | -104810 | S1-first-order | LEAD [FIRST-ORDER SCREEN ONLY] |
| I5 stack rolling Calmar | {"D": 20, "mult": 0.5, "x": 3.0} | +37 / +33 / +36 / +57 | +2 | +41 | -2103 | +30 / +26 / +29 / +52 | 19.7 | 28% | FIRST-ORDER SCREEN ONLY | -13 / +49.8 / +135 | 0.07 | 0.85 | +41 | -37680 | S1-first-order | CANDIDATE (own-p only; family p 0.85) [FIRST-ORDER SCREEN ONLY] |
| I5 stack rolling Calmar | {"D": 10, "mult": 0.5, "x": 2.0} | +30 / +33 / +43 / +42 | -14 | +25 | -1340 | +26 / +29 / +40 / +38 | 18.7 | 25% | FIRST-ORDER SCREEN ONLY | -15 / +45.0 / +120 | 0.08 | 0.96 | +41 | -37680 | S1-first-order | LEAD [FIRST-ORDER SCREEN ONLY] |
| I5 stack rolling Calmar | {"D": 10, "mult": 0.0, "x": 3.0} | +57 / +65 / +55 / +81 | -127 | +59 | -8954 | +25 / +40 / +23 / +67 | 18.6 | 73% | FIRST-ORDER SCREEN ONLY | +4 / +52.4 / +143 | 0.05 | 1.00 | +41 | -104810 | S1-first-order | LEAD [FIRST-ORDER SCREEN ONLY] |
| I3 book rolling Calmar | {"D": 10, "mult": 0.0, "x": 1.0} | +33 / +10 / +64 / +64 | -21 | +32 | -2670 | +23 / -2 / +59 / +59 | 18.1 | 61% | FIRST-ORDER SCREEN ONLY | +24 / +9.2 / -1 | 0.08 | 1.00 | +41 | -105580 | S1-first-order | LEAD [FIRST-ORDER SCREEN ONLY] |
| I3 book rolling Calmar | {"D": 10, "mult": 0.5, "x": 2.0} | +34 / +31 / +46 / +43 | -7 | +31 | -4023 | +23 / +20 / +37 / +34 | 23.4 | 28% | FIRST-ORDER SCREEN ONLY | -0 / +34.5 / +100 | 0.13 | 0.96 | +41 | -38365 | S1-first-order | LEAD [FIRST-ORDER SCREEN ONLY] |
| I3 book rolling Calmar | {"D": 10, "mult": 0.5, "x": 1.0} | +21 / +29 / +47 / +45 | +13 | +24 | +349 | +22 / +30 / +48 / +45 | 17.9 | 23% | FIRST-ORDER SCREEN ONLY | +8 / +13.1 / +5 | 0.10 | 0.98 | +41 | -38365 | S1-first-order | CANDIDATE (own-p only; family p 0.98) [FIRST-ORDER SCREEN ONLY] |
| I5 stack rolling Calmar | {"D": 10, "mult": 0.5, "x": 3.0} | +30 / +33 / +43 / +48 | -25 | +38 | -2228 | +22 / +25 / +37 / +42 | 17.9 | 29% | FIRST-ORDER SCREEN ONLY | -4 / +34.6 / +108 | 0.14 | 0.99 | +41 | -37680 | S1-first-order | LEAD [FIRST-ORDER SCREEN ONLY] |
| I3 book rolling Calmar | {"D": 10, "mult": 0.5, "x": 0.5} | +17 / +22 / +38 / +42 | -7 | +17 | -43 | +16 / +22 / +38 / +41 | 18.1 | 19% | FIRST-ORDER SCREEN ONLY | +3 / +13.7 / +60 | 0.19 | 0.99 | +41 | -37165 | S1-first-order | LEAD [FIRST-ORDER SCREEN ONLY] |
| I1 last-N-trades R | {"N": 12, "mult": 0.5, "thr_R": 0.5} | +27 / +17 / +27 / +5 | -8 | +31 | -3574 | +16 / +5 / +16 / -9 | 20.7 | 14% | FIRST-ORDER SCREEN ONLY | -21 / +47.5 / +140 | 0.11 | 0.96 | +41 | -11928 | S1-first-order | LEAD [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| I6 up-allowed hot x1.5 / cold x0.5 | {"N": 8, "thr_R": 2} | -9 / -9 / -10 / -24 | -16 | -11 | +983 | -4 / -4 / -5 / -19 | 13.3 | 34% | FIRST-ORDER SCREEN ONLY | -16 / +7.0 / +6 | 0.41 | 1.00 | +41 | +2320 | S1-first-order | UP (report) [FIRST-ORDER SCREEN ONLY] |
| I6 up-allowed hot x1.5 / cold x0.5 | {"N": 8, "thr_R": 4} | -18 / +4 / -4 / -32 | -34 | -16 | -2792 | -34 / -9 / -18 / -50 | 11.1 | 11% | FIRST-ORDER SCREEN ONLY | -5 / -12.4 / -65 | 0.95 | 1.00 | +41 | -280 | S1-first-order | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family J - Combinations

Combinations: 798 cells (798 down-only); best by equal-mean L6M maxDD cut: J pair min {"a": "ext-B:9806533560c9", "b": "ext-G:cebf694ec6e2"} cuts L6M maxDD +85% at equal lots (d mean +2314 $/wk) and +86% at equal mean (PRE +62%, X' +72%); placebo p 0.02, family p 0.97, WF +26 -> CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-G:cebf694ec6e2"} | +85 / +10 / +58 / +69 | +56 | +86 | +2314 | +86 / +19 / +62 / +72 | 105.6 | 72% | FIRST-ORDER SCREEN ONLY | +22 / +62.4 / +686 | 0.02 | 0.97 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-E:E|total_lots_cap|cap4_trunc|se | +79 / +16 / +58 / +73 | +64 | +85 | +3902 | +82 / +29 / +64 / +77 | 81.4 | 69% | FIRST-ORDER SCREEN ONLY | +54 / +24.9 / +60 | 0.02 | 0.97 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-F:e42de98e2549"} | +84 / +30 / +41 / +59 | +45 | +88 | -2876 | +82 / +21 / +34 / +54 | 93.7 | 63% | FIRST-ORDER SCREEN ONLY | +45 / +38.4 / +190 | 0.02 | 1.00 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:1b5942ac8cd6", "b": "ext-E:E|total_lots_cap|cap4_trunc|se | +78 / +31 / +37 / +66 | +42 | +81 | +3078 | +81 / +39 / +44 / +70 | 76.4 | 70% | FIRST-ORDER SCREEN ONLY | +39 / +38.9 / +381 | 0.02 | 0.72 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.72) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "I:83d7d23f2f5d", "b": "ext-B:9806533560c9"} | +86 / +9 / +63 / +57 | +5 | +87 | -5163 | +81 / -20 / +52 / +44 | 72.8 | 82% | FIRST-ORDER SCREEN ONLY | +29 / +56.9 / +881 | 0.03 | 1.00 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:d852c862a088", "b": "ext-E:E|total_lots_cap|cap4_skip|ses | +79 / +16 / +54 / +66 | +31 | +81 | +936 | +80 / +20 / +56 / +67 | 72.3 | 67% | FIRST-ORDER SCREEN ONLY | +53 / +26.0 / +117 | 0.02 | 0.67 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.67) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-E:E|total_lots_cap|cap4_skip|sess_london", "b": "ext-SZQ:AB | +82 / +8 / +58 / +53 | +71 | +84 | -2710 | +80 / -2 / +53 / +47 | 85.4 | 66% | FIRST-ORDER SCREEN ONLY | +66 / +15.7 / +4 | 0.02 | 0.38 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.38) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-D:D|eqdd_stack_20d|Y20000_f0.25_ | +76 / +14 / +51 / +38 | +71 | +86 | +4223 | +80 / +27 / +58 / +48 | 71.5 | 61% | FIRST-ORDER SCREEN ONLY | +45 / +30.6 / +181 | 0.02 | 1.00 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-F:87dbd27287dc"} | +81 / +46 / +46 / +52 | +50 | +86 | -2673 | +79 / +40 / +40 / +47 | 80.1 | 56% | FIRST-ORDER SCREEN ONLY | +45 / +35.5 / +203 | 0.02 | 1.00 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:1b5942ac8cd6", "b": "ext-D:D|eqdd_stack_20d|Y20000_f0.25_ | +75 / +39 / +65 / +55 | +36 | +78 | +3660 | +78 / +48 / +70 / +61 | 67.7 | 62% | FIRST-ORDER SCREEN ONLY | +22 / +53.3 / +758 | 0.02 | 0.90 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.90) [FIRST-ORDER SCREEN ONLY] |

## Family K - P7

P7: 391 cells (391 down-only); best by equal-mean L6M maxDD cut: K6 ext-B on P7 only {"cell": "9806533560c9", "orig": "ext ext-B {\"cell\": \"980 cuts L6M maxDD +44% at equal lots (d mean +5351 $/wk) and +54% at equal mean (PRE +50%, X' +67%); placebo p 0.02, family p 0.80, WF +34 -> CANDIDATE (own-p only; family p 0.80) [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K6 ext-B on P7 only | {"cell": "9806533560c9", "orig": "ext ext-B {\"cell\": \"9806533560c9\ | +44 / +45 / +39 / +60 | +79 | +52 | +5351 | +54 / +55 / +50 / +67 | 33.1 | 13% | FIRST-ORDER SCREEN ONLY | +32 / +11.9 / +5 | 0.02 | 0.80 | +34 |  | S1-first-order | CANDIDATE (own-p only; family p 0.80) [FIRST-ORDER SCREEN ONLY] |
| K6 ext-B on P7 only | {"cell": "faebfc320da8", "orig": "ext ext-B {\"cell\": \"faebfc320da8\ | +42 / +32 / +42 / +60 | +64 | +55 | +3507 | +50 / +41 / +50 / +65 | 30.3 | 15% | FIRST-ORDER SCREEN ONLY | +41 / +1.0 / +2 | 0.02 | 0.95 | +34 |  | S1-first-order | CANDIDATE (own-p only; family p 0.95) [FIRST-ORDER SCREEN ONLY] |
| K6 ext-B on P7 only | {"cell": "c1d4e97d2d2c", "orig": "ext ext-B {\"cell\": \"c1d4e97d2d2c\ | +29 / +37 / +37 / +24 | +93 | +53 | +5877 | +43 / +50 / +50 / +40 | 25.8 | 11% | FIRST-ORDER SCREEN ONLY | +35 / -5.9 / +0 | 0.02 | 0.80 | +34 |  | S1-first-order | CANDIDATE (own-p only; family p 0.80) [FIRST-ORDER SCREEN ONLY] |
| K6 ext-B on P7 only | {"cell": "b03055b79198", "orig": "ext ext-B {\"cell\": \"b03055b79198\ | +30 / +13 / +35 / +34 | +67 | +44 | +4598 | +42 / +28 / +46 / +45 | 25.2 | 11% | FIRST-ORDER SCREEN ONLY | +39 / -8.4 / -2 | 0.05 | 0.95 | +34 |  | S1-first-order | CANDIDATE (own-p only; family p 0.95) [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only | {"cell": "4631cbe633a4", "orig": "ext ext-A {\"cell\": \"4631cbe633a4\ | +36 / +20 / +45 / +27 | +19 | +48 | +2030 | +41 / +27 / +50 / +33 | 24.8 | 15% | FIRST-ORDER SCREEN ONLY | -13 / +49.0 / +365 | 0.02 | 0.71 | +34 |  | S1-first-order | CANDIDATE (own-p only; family p 0.71) [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only | {"cell": "07a9eb57e868", "orig": "ext ext-A {\"cell\": \"07a9eb57e868\ | +36 / +20 / +45 / +27 | +19 | +48 | +2030 | +41 / +27 / +50 / +33 | 24.8 | 15% | FIRST-ORDER SCREEN ONLY | -13 / +49.0 / +365 | 0.02 | 0.71 | +34 |  | S1-first-order | CANDIDATE (own-p only; family p 0.71) [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only | {"cell": "e8116ed4fa4e", "orig": "ext ext-A {\"cell\": \"e8116ed4fa4e\ | +42 / -10 / +31 / +18 | +22 | +46 | -722 | +40 / -14 / +29 / +16 | 25.9 | 16% | FIRST-ORDER SCREEN ONLY | -16 / +57.9 / +378 | 0.02 | 0.07 | +34 |  | S1-first-order | CANDIDATE [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only | {"cell": "7850ad5e165a", "orig": "ext ext-A {\"cell\": \"7850ad5e165a\ | +42 / -10 / +31 / +18 | +22 | +46 | -722 | +40 / -14 / +29 / +16 | 25.9 | 16% | FIRST-ORDER SCREEN ONLY | -16 / +57.9 / +378 | 0.02 | 0.07 | +34 |  | S1-first-order | CANDIDATE [FIRST-ORDER SCREEN ONLY] |
| K6 ext-G on P7 only | {"cell": "f98bd2daa16b", "orig": "ext ext-G {\"cell\": \"f98bd2daa16b\ | +39 / +13 / +16 / +0 | +29 | +44 | -90 | +39 / +12 / +16 / -0 | 24.6 | 4% | FIRST-ORDER SCREEN ONLY | +24 / +15.3 / +31 | 0.02 | 0.46 | +34 |  | S1-first-order | CANDIDATE (own-p only; family p 0.46) [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only | {"cell": "a64be38872f3", "orig": "ext ext-A {\"cell\": \"a64be38872f3\ | +36 / +4 / +28 / +15 | +35 | +42 | +1115 | +39 / +9 / +31 / +19 | 24.5 | 12% | FIRST-ORDER SCREEN ONLY | +12 / +24.1 / +119 | 0.02 | 0.05 | +34 |  | S1-first-order | CANDIDATE [FIRST-ORDER SCREEN ONLY] |

## Cross-family finalists (CANDIDATE / LEAD+ labels, top 25 by equal-mean L6M cut)

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-G:cebf694ec6e2"} | +85 / +10 / +58 / +69 | +56 | +86 | +2314 | +86 / +19 / +62 / +72 | 105.6 | 72% | FIRST-ORDER SCREEN ONLY | +22 / +62.4 / +686 | 0.02 | 0.97 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-E:E|total_lots_cap|cap4_trunc|se | +79 / +16 / +58 / +73 | +64 | +85 | +3902 | +82 / +29 / +64 / +77 | 81.4 | 69% | FIRST-ORDER SCREEN ONLY | +54 / +24.9 / +60 | 0.02 | 0.97 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-F:e42de98e2549"} | +84 / +30 / +41 / +59 | +45 | +88 | -2876 | +82 / +21 / +34 / +54 | 93.7 | 63% | FIRST-ORDER SCREEN ONLY | +45 / +38.4 / +190 | 0.02 | 1.00 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:1b5942ac8cd6", "b": "ext-E:E|total_lots_cap|cap4_trunc|se | +78 / +31 / +37 / +66 | +42 | +81 | +3078 | +81 / +39 / +44 / +70 | 76.4 | 70% | FIRST-ORDER SCREEN ONLY | +39 / +38.9 / +381 | 0.02 | 0.72 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.72) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "I:83d7d23f2f5d", "b": "ext-B:9806533560c9"} | +86 / +9 / +63 / +57 | +5 | +87 | -5163 | +81 / -20 / +52 / +44 | 72.8 | 82% | FIRST-ORDER SCREEN ONLY | +29 / +56.9 / +881 | 0.03 | 1.00 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:d852c862a088", "b": "ext-E:E|total_lots_cap|cap4_skip|ses | +79 / +16 / +54 / +66 | +31 | +81 | +936 | +80 / +20 / +56 / +67 | 72.3 | 67% | FIRST-ORDER SCREEN ONLY | +53 / +26.0 / +117 | 0.02 | 0.67 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.67) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-E:E|total_lots_cap|cap4_skip|sess_london", "b": "ext-SZQ:AB | +82 / +8 / +58 / +53 | +71 | +84 | -2710 | +80 / -2 / +53 / +47 | 85.4 | 66% | FIRST-ORDER SCREEN ONLY | +66 / +15.7 / +4 | 0.02 | 0.38 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.38) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-D:D|eqdd_stack_20d|Y20000_f0.25_ | +76 / +14 / +51 / +38 | +71 | +86 | +4223 | +80 / +27 / +58 / +48 | 71.5 | 61% | FIRST-ORDER SCREEN ONLY | +45 / +30.6 / +181 | 0.02 | 1.00 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-F:87dbd27287dc"} | +81 / +46 / +46 / +52 | +50 | +86 | -2673 | +79 / +40 / +40 / +47 | 80.1 | 56% | FIRST-ORDER SCREEN ONLY | +45 / +35.5 / +203 | 0.02 | 1.00 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:1b5942ac8cd6", "b": "ext-D:D|eqdd_stack_20d|Y20000_f0.25_ | +75 / +39 / +65 / +55 | +36 | +78 | +3660 | +78 / +48 / +70 / +61 | 67.7 | 62% | FIRST-ORDER SCREEN ONLY | +22 / +53.3 / +758 | 0.02 | 0.90 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.90) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "K:ac4e6310f17b", "b": "ext-B:1b5942ac8cd6"} | +75 / +61 / +61 / +68 | +65 | +81 | +3311 | +78 / +66 / +66 / +72 | 67.2 | 63% | FIRST-ORDER SCREEN ONLY | +28 / +47.1 / +753 | 0.02 | 0.64 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.64) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "Jtree:9be3e678872f", "b": "ext-B:1b5942ac8cd6"} | +77 / +50 / +33 / +77 | +18 | +79 | +737 | +78 / +52 / +35 / +78 | 66.6 | 66% | FIRST-ORDER SCREEN ONLY | +25 / +52.7 / +723 | 0.02 | 0.97 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "K:b8c7a11b7c62", "b": "ext-B:1b5942ac8cd6"} | +73 / +63 / +60 / +69 | +70 | +78 | +4279 | +78 / +69 / +66 / +74 | 65.4 | 63% | FIRST-ORDER SCREEN ONLY | +33 / +40.3 / +555 | 0.02 | 0.64 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.64) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:d852c862a088", "b": "ext-K:4717a767cf4d"} | +74 / +42 / +67 / +59 | +45 | +79 | +3093 | +77 / +49 / +71 / +64 | 64.1 | 60% | FIRST-ORDER SCREEN ONLY | +50 / +23.9 / +157 | 0.02 | 0.64 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.64) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "K:5ac97ef10c49", "b": "ext-B:1b5942ac8cd6"} | +78 / +59 / +65 / +68 | +34 | +86 | -963 | +77 / +57 / +63 / +66 | 62.8 | 66% | FIRST-ORDER SCREEN ONLY | +16 / +61.6 / +1106 | 0.02 | 0.67 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.67) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-E:E|total_lots_cap|cap4_skip|ses | +79 / -18 / +65 / +56 | +65 | +89 | -3672 | +76 / -37 / +59 / +49 | 72.1 | 66% | FIRST-ORDER SCREEN ONLY | +61 / +18.1 / +26 | 0.02 | 0.90 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.90) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-A:27003ddb767c", "b": "ext-B:9806533560c9"} | +73 / -15 / +65 / +39 | +54 | +78 | +2191 | +76 / -5 / +68 / +44 | 59.9 | 72% | FIRST-ORDER SCREEN ONLY | +64 / +9.5 / +18 | 0.02 | 1.00 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "Jtree:9be3e678872f", "b": "ext-B:9806533560c9"} | +74 / +41 / +51 / +75 | +40 | +81 | +1110 | +75 / +44 / +54 / +76 | 59.2 | 64% | FIRST-ORDER SCREEN ONLY | +39 / +35.1 / +352 | 0.02 | 1.00 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-SZQ:AB_1b5942_0"} | +71 / +56 / +42 / +68 | +62 | +82 | +4291 | +75 / +63 / +52 / +73 | 59.1 | 62% | FIRST-ORDER SCREEN ONLY | +30 / +40.4 / +582 | 0.02 | 0.74 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.74) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:1b5942ac8cd6", "b": "ext-K:6fa18a1ca7ac"} | +70 / +55 / +63 / +68 | +63 | +76 | +4288 | +75 / +62 / +69 / +73 | 58.2 | 61% | FIRST-ORDER SCREEN ONLY | +32 / +38.2 / +557 | 0.02 | 0.67 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.67) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:1b5942ac8cd6", "b": "ext-K:4717a767cf4d"} | +70 / +46 / +66 / +64 | +69 | +79 | +4108 | +75 / +55 / +71 / +69 | 58.0 | 61% | FIRST-ORDER SCREEN ONLY | +42 / +28.7 / +383 | 0.02 | 0.67 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.67) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:1b5942ac8cd6", "b": "ext-K:d16e6b6b3c26"} | +70 / +55 / +64 / +68 | +61 | +76 | +4111 | +75 / +62 / +69 / +73 | 57.8 | 61% | FIRST-ORDER SCREEN ONLY | +32 / +38.2 / +555 | 0.02 | 0.67 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.67) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-F:e42de98e2549", "b": "ext-G:d83c9df25d9f"} | +74 / +25 / +9 / +35 | +10 | +81 | +493 | +75 / +26 / +11 / +37 | 56.4 | 26% | FIRST-ORDER SCREEN ONLY | +29 / +44.8 / +475 | 0.02 | 0.54 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.54) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-A:1fb40ebdb01a", "b": "ext-D:D|dayloss_stack$|X16000_f0.00| | +76 / -25 / +57 / +54 | +24 | +81 | -812 | +75 / -30 / +56 / +53 | 59.1 | 25% | FIRST-ORDER SCREEN ONLY | -29 / +104.1 / +1338 | 0.02 | 0.87 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 0.87) [FIRST-ORDER SCREEN ONLY] |
| J pair min | {"a": "ext-B:9806533560c9", "b": "ext-H:61f3cbb073a5"} | +77 / +65 / +49 / +61 | +35 | +81 | -2469 | +75 / +60 / +43 / +56 | 57.4 | 70% | FIRST-ORDER SCREEN ONLY | +40 / +37.1 / +649 | 0.02 | 1.00 | +26 |  | S1-first-order | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
