# DS3_SIZER_EXHAUST - T-SIZER-EXHAUST ranked tables (SZ-CORE, 2026-11-09 17:38Z)

**Label: base S1b-COMB (live D7 v1.5 with the seven state-cut lines), controls NOCUT / UNIF where the owner ran them; first-order unless stage says S2 (exact); entries not live-matched (entry match < .85); in-sample; PRE-PROOF. Post-hoc, Shadow only, no PASS claims.**

Windows as of 2026-11-09 (L6M 20260512-, HOLD 20251111-, PRE 20240201-20250630, X' 20230401-20240131). Cut = maxDD cut vs Q1-A in % (+ = shallower); equal-mean = every cell scaled by one global factor so its L6M mean equals Q1-A's; worst-20 cut = change of the sum of the 20 worst weeks. Placebo = same-count down-sizing within book x session; family p = max-stat over the owner family set (own-draw p in the placebo column). Ranking key: equal-mean L6M maxDD cut (drawdown first), mean is the tie-break. Down-only = live candidates; UP rows are reported only.

**Audit note (SZ-CORE 2026-11-09):** several owner ledgers dropped the carrying weeks (202629-39) from the weekly vector BEFORE computing maxDD (directive: all weeks for maxDD, carrying week dropped from means only). Their L6M/HOLD cuts are overstated (e.g. J pair 18fe3fdc2530: owner 100% L6M cut = 0 maxDD in 14 retained weeks; sz_core all-weeks rescoring gives +37%). The sz_core rescoring of finalists is in the finalist table; ledger numbers are owner numbers until rescored.

**ROLL-EXCL (SZ-BASE section 9, 2026-11-09):** the replica engine runs on stitched raw prints (14 contract rolls, +185-316 pts); 33 trades alive across a roll (31 exit by Target/Stop within 2 s, net +$20.2k in COMB) are EXCLUDED from every window metric: first-order scoring (sz_core Base weight 0, M length unchanged), exact scoring (sz_exact.py score/report) and the reference rows. X' maxDD of the base changes +10% (116.9k to 128.9k), HOLD cuts move up to 21 pts, L6M is unchanged. Rows marked "ROLL-EXCL (core rescore)" are re-scored by sz_core; ledger numbers marked "owner number, NOT roll-excluded" are the owners' own scorers and are flagged OLD COLUMNS until the owners re-score. FIRST-ORDER numbers are ROLL-EXCL only: they remove the 33 trades but cannot see the follow-on effects of those trades on locks, day states, stack caps and re-entries (exact rows can, but the exact base itself still contains the 33 until the engine patch is run; exact scoring excludes the same 33 keys). The engine fix (flatten-at-roll patch prepared in code/th_sz/sz_exact_roll.py; runbook in SZ_API.md section 10) and the base rebuild are deferred until after the FINAL pages.

**STANDING RULE (user, 2026-11-09 17:20Z, autopilot/STANDING_RULE_LAYERS_ON_20261109.md):** every D7 layer stays ON. "Off", "no rule", "empty side" and "plain 60/60" are REFERENCE rows only. Each program delivers the best SETTING of its layer (the live setting is retained if nothing beats it) and the best profit rule per book even if inside MDE. In this study: sizer-off is a reference row; the deliverable is the best sizing setting per book and for the stack, with "live setting retained" stated where nothing beats it.

## Scoreboard

| family | cells | down-only | LEAD | LEAD+ (placebo ok) | CANDIDATE (first-order screen incl.) | CANDIDATE exact-confirmed |
|--|--|--|--|--|--|--|
| A ER family | 16290 | 12240 | 7191 | 926 | 0 | 0 |
| B Volatility target | 3994 | 3626 | 421 | 518 | 0 | 0 |
| C Equal-risk / parity | 28 | 16 | 14 | 0 | 2 | 0 |
| D Equity-curve / state | 160 | 146 | 71 | 0 | 7 | 0 |
| E Exposure / concentration | 74 | 74 | 37 | 0 | 4 | 0 |
| F Time / session | 118 | 118 | 30 | 4 | 0 | 0 |
| G Signal quality | 1214 | 890 | 386 | 28 | 0 | 0 |
| H Regime | 224 | 149 | 64 | 6 | 0 | 0 |
| I Book-level recent performance | 188 | 186 | 73 | 0 | 8 | 0 |
| J Combinations | 1081 | 1081 | 415 | 0 | 657 | 0 |
| K P7 | 391 | 391 | 169 | 0 | 114 | 0 |

> **TESTING-DEFECT BOX.** Cells whose new-base d mean equals the old-base page to the dollar: 0.

**USER ADDENDUM 1 (16:30Z) status:** first-order is a SCREEN ONLY; the sizing verdict needs EXACT engine runs for every family top-5 and every reference row on L6M, PRE, X', HOLD. Exact-confirmed cells on this page: 8 of 23762 with any exact window, 0 with all of L6M/PRE/X' (the label carries [EXACT] / [EXACT partial] / [FIRST-ORDER SCREEN ONLY]). Exact queue: autopilot SZ-CORE queue, reference rows first, then family top-5; windows L6M, PRE, X', HOLD.

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
| sizer off (x1) | -28.2 / -2511 | -6.4 / -970 | pending | pending | 30 |
| old ladder L (x0.5/x1.5) | -76.1 / -504 | -41.5 / -103 | pending | pending | 30 |
| B (x1/x1.5, up only) | -142.6 / +2723 | -94.8 / +2856 | pending | pending | 31 |
| ZL-1 vol-target (factor built on unadjusted bars; 97 trades differ after adjustment; X_VTA pending) | +28.3 / +10 | +29.1 / -684 | pending | pending | 30 |
| MV-london override | -1.2 / -107 | +6.8 / +28 | pending | pending | 26 |

## Vol-target family (SZ-VT, autopilot/DS3_SIZER_VOLTARGET.md, user top priority; exact engine from the start; first 70 lines, incl. executability rows: scale factor s, max single-trade $ risk, max lots on at once)

# DS3_SIZER_VOLTARGET - T-SIZER-EXHAUST Addendum 2 (SZ-VT), refreshed 2026-11-09 17:32Z
**Post-hoc, Shadow only, no PASS claims. PRE-PROOF (entry match < .85). Numbers below are FIRST-ORDER SCREEN unless a row says [EXACT]. Prereg: autopilot/SZ_VT_PREREG.md (sha in DECISIONS.md). ALL EXACT ROWS ARE PENDING/VOID until re-run with the fixed sz_exact driver (key bug found 17:00Z).**

**VERDICT (plain, provisional, first-order; ALL exact rows pending): every D7 layer stays ON, so the candidates are scale rules (never to zero) on top of the live ER sizer, and the skip-to-zero vol rules are reference/UP rows only. Skip rules that win in-sample (+79/+60/+78 for the best cell) fail the equal-mean walk-forward and lose $40-80k of the $104.8k high-vol live week, and the in-sample winner on the S1b base ranks #1254 (of ~30k) on the old base, so in-sample picks do not carry. Of the scale families only "SCALE single measure" (never-zero rules on the 20 best single measures) is stable in all 5 pre-registered out-of-sample tests (WF 26/52 wk, split-half A and B, time split: +25 to +35 % maxDD cut at the realised equal mean, but its measure list was chosen with full-sample information, so treat it as an upper bound), the consensus-measure scale family is positive in all 5 but small (+5 to +23 %), and nothing is confirmed on the exact engine; if the exact rows (section 7) do not hold, keep the live Q1-A sizer. Scale rules cost about -$34k to -$48k of the live week at p=2 floor .25 (that week was 69 % above 1.25x vol).**

## 0. What was built (B1-B5)
- Features at the signal second (causal, NQ 1-min state bars closed before the signal; code/th_sz_vt/vt_feat.py, 1,859 columns): 53 vol measures (rv1 w10/30/60/120/240, rv5, GK / Parkinson on 1/5/15-min, ATR b1/5/15 n5/14/30/50, EWMA lam .90/.94/.97/.99 on 1/5-min) x sigma_ref windows 5/10/20/40/60 trading days x reference type {all minutes, same half-hour slot, and for 8 core measures all/slot with FOMC/CPI/NFP days excluded from the norm} x {ratio now/median, quantile of the trailing distribution, log z-score}; core dynamics (minutes above 1.25x = spiked vs sustained, ratio now / 30 min ago = vol-of-vol, std of the ratio), direction-aware move of the last 5/15/30/60 min in 1-min sigma, event-day flag; range ratios (overnight/pre/first-30/so-far) and VIX from the AB store.
- Cells scored: **51,408 pooled grid cells** (shapes: continuous (ref/now)^p p .5-2 floor 0/.25/.5, quantile step q .6-.95 to x0.5 or 0, graded 3-step {1,.5,0} at quantile pairs, multiple step 1.1-2.0, z step; with and without the ER sizer) + 1,824 B2 special rules (first signal of the episode per book / stack, spiked vs sustained, direction-aware, rising vs falling vol, event-day) + 850 per-book/session scope cells + 744 B4 interaction cells (stack exposure cap 8-20 lots, post-loss cooldown in high vol) + 864 stack and per-book P&L target-vol cells (trailing 10/15/20 d P&L vol, target = q x expanding median, p .5-2, floor 0-.5). Down-only family on top of Q1-A (onQ1A): 30,031 cells; "alone" (ER sizer removed, M can exceed 1 where ER<.3) are reported in the ledger as UP-labelled, never promoted.
- NOT table-expressible, therefore NOT scored (stated, not hidden): delay-and-recheck entries (changes entry price, needs an engine subclass), the equal-$-risk stop form (wider stop, fewer lots: stop is an engine input), vol-scaled +-R day caps, and vol-governed state-cut arm/persistence (engine rules). They need `state_sizer_b` subclasses (cde_exact.py pattern); listed in section 8 as v1.6 work. Tick count / contracts per second / spread / depth proxies and VXN: the per-second feature store is path-aligned to trades, not to arbitrary signal seconds, VXN is not owned, and VIX stops 2026-10-16; the liquidity proxies are NOT in this page (stated gap). NQ 1-min data runs to 2026-11-05 so all NQ measures cover the whole live week; ES/RTY cross-instrument vol uses 1-s closes that end 2026-10-16 (unavailable after: multiplier 1) and is not part of the screened grid in this version.
- Validation: purged monthly walk-forward of the PICKING procedure per family (26-week training, 7-day embargo, 34 test months 2024-01..2026-10): pick = highest training equal-mean maxDD cut; reported at equal lots, with s fixed from the training window, and at the realised equal OOS mean; time split (pick on weeks <= 2025-06-30, test 2025-07..2026-11); placebo (same lot ratios permuted within book x session, B=200) and a family null over all 30,031 down-only cells (max-stat over the same permutations); held-out live week (frozen file, first-order); EXACT engine for the top cells (section 6).

## 1. Best cell per family (down-only on Q1-A, first-order). Cut = stack maxDD cut vs Q1-A; EQ = at equal L6M mean (lots x s)
| family | cell (feature shape params scope) | cut L6M/PRE/X' (equal lots) | EQ cut L6M/PRE/X' | s | d mean $/wk L6M | worst-20 L6M cell/ref ($k) | Ulcer L6M cell/ref ($k) | skip share | p own / p fam(VT set, all stages) | WF family OOS cut: equal lots / realised equal mean | live wk d$ | stage |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| interactions (cap/cooldown) | q_gk1_w120_all10 step [0.6, 0] ["pool"] | +79/+60/+78 | +77/+57/+76 | 1.07 | -1442 | +211/+165 | 5.5 | 0.55 | 0.005 / 0.005 | 43.2 / 15.3 | - | S1 first-order |
| per-book/session scope | r_ewma5_l90_all40 step [1.1, 0] ["book", "P7"] | +60/+45/+60 | +66/+54/+66 | 0.85 | +4094 | +250/+165 | 12.8 | 0.15 | 0.005 / 0.075 | 43.7 / 29.2 | -64405 | S1 first-order |
| quantile-adaptive (q_*) | q_park15_w12_all10 step [0.6, 0] ["pool"] | +68/+58/+60 | +72/+63/+65 | 0.88 | +3157 | +274/+165 | 7.2 | 0.53 | 0.005 / 0.085 | 24.3 / -12.5 | -79635 | S1 first-order |
| ratio step/cont (r_*) | r_COMP_all10 step [1.25, 0] ["pool"] | +36/+61/+62 | +42/+65/+66 | 0.90 | +2384 | +228/+165 | 16.9 | 0.50 | 0.005 / 0.095 | 34.7 / -9.0 | -77455 | S1 first-order |
| graded 3-step | q_park15_w12_all10 g3 [0.6, 0.9] ["pool"] | +59/+39/+58 | +63/+45/+62 | 0.90 | +2540 | +238/+165 | 14.7 | 0.16 | 0.005 / 0.134 | 23.3 / 13.1 | -56415 | S1 first-order |
| session-slot ref | r_gk15_w6_slot10 step [1.1, 0] ["pool"] | +60/+61/+8 | +61/+62/+11 | 0.97 | +675 | +186/+165 | 11.0 | 0.50 | 0.005 / 0.189 | 23.5 / -11.7 | -81535 | S1 first-order |
| special (first/dur/dir/vov/evt) | q_atr5_n14_all20 special [] ["pool"] | +33/+54/+52 | +43/+61/+59 | 0.84 | +4422 | +258/+165 | 15.3 | 0.43 | 0.005 / 0.229 | 17.7 / 6.0 | -70800 | S1 first-order |
| continuous (ref/now)^p | r_park1_w10_all40 cont [2, 0] ["pool"] | +33/+55/+56 | +38/+58/+59 | 0.92 | +2109 | +221/+165 | 16.8 | 0.00 | 0.005 / 0.264 | 31.4 / 15.5 | -41810 | S1 first-order |
| composite pooled scope | r_COMP_all20 step [1.25, 0] ["pool"] | +8/+58/+54 | +16/+61/+58 | 0.91 | +2193 | +186/+165 | 19.6 | 0.51 | 0.005 / 0.289 | 38.6 / 16.1 | -72970 | S1 first-order |
| SCALE rules (never zero) all | r_gk1_w10_all60 cont [2, 0.25] ["book", "K7", "P7", "M7", "A7", "O7"] | +14/+50/+52 | +23/+56/+57 | 0.90 | +2697 | +240/+165 | 20.4 | 0.00 | 0.005 / 0.383 | 16.9 / 5.6 | -47559 | S1 first-order |
| composite consensus (all stages comp) | q_COMP_all60 step [0.6, 0] ["book", "P7", "K7"] | +19/+46/+63 | +30/+53/+68 | 0.86 | +3510 | +223/+165 | 16.5 | 0.35 | 0.005 / 0.522 | 35.9 / 6.4 | -92905 | S1 first-order |
| z-score | z_park15_w24_all10 step [1.0, 0] ["pool"] | +37/+24/+46 | +52/+41/+58 | 0.77 | +6750 | +258/+165 | 20.6 | 0.22 | 0.005 / 0.617 | 33.3 / 14.0 | -61335 | S1 first-order |
| half (lo=.5) steps | r_park5_w12_allx60 step [1.25, 0.5] ["pool"] | +0/+45/+45 | +11/+51/+51 | 0.89 | +2838 | +233/+165 | 25.5 | 0.00 | 0.005 / 0.652 | 25.0 / 20.6 | -32283 | S1 first-order |
| stack/book P&L target-vol | tvol_ALL tvol [20, 0.8, 2, 0.5, "ALL"] ["pool"] | +47/+43/+3 | +24/+18/-41 | 1.45 | -6768 | +129/+165 | 17.7 | 0.00 | 0.015 / 1.000 | 45.2 / 31.6 | -37680 | S1 first-order |

Reading the columns: "skip share" is the share of signals taken to zero lots; a cell that skips 50-60 % of signals and still shows a higher mean at equal lots is selecting the quiet-tape trades, which is the part that fails out of sample (section 2). Worst-20 = sum of the 20 worst weeks (higher = better). The placebo draws permute the same lot ratios within book x session, so p own tests timing, not size.

## 1b. Stability of the verdict per family (pre-registered 5 tests: WF 26 wk, WF 52 wk, split-half A (train first half), split-half B (train second half), time split (train <= 2025-06-30); metric = OOS maxDD cut % at the REALISED test equal mean; NaN = family not in that WF table)
| family | cells | WF26 | WF52 | split A | split B | time split | positive of 5 | worst | stable? |
|---|---|---|---|---|---|---|---|---|---|
| SCALE single measure | 904 | 35.2 | 34.7 | 34.6 | 24.7 | 29.5 | 5 | 24.7 | STABLE (5/5 > 0) |
| SCALE rules (never zero) all | 1784 | 5.6 | 13.2 | 14.7 | 24.7 | 29.5 | 5 | 5.6 | STABLE (5/5 > 0) |
| SCALE consensus measure | 880 | 5.3 | 11.6 | 14.7 | 18.7 | 23.1 | 5 | 5.3 | STABLE (5/5 > 0) |
| SCALE pooled | 446 | 5.0 | 11.1 | 14.7 | 24.7 | 30.7 | 5 | 5.0 | STABLE (5/5 > 0) |
| per-book/session scope | 850 | 29.2 | 34.2 | 43.2 | 1.7 | 18.5 | 5 | 1.7 | STABLE (5/5 > 0) |
| interactions | 744 | 15.3 | -2.8 | 40.8 | 17.0 | 31.4 | 4 | -2.8 | mostly |
| SCALE P7+K7 scope | 446 | 8.9 | 13.2 | -4.5 | 31.7 | 27.0 | 4 | -4.5 | mostly |
| half (lo=.5) steps | 9806 | 20.6 | 15.4 | 8.2 | 21.7 | -11.8 | 4 | -11.8 | mostly |
| composite pooled | 388 | 16.1 | 33.4 | 36.0 | 28.0 | -19.2 | 4 | -19.2 | mostly |
| composite graded/half/cont | 5220 | 33.7 | 27.4 | 36.0 | 5.6 | -19.2 | 4 | -19.2 | mostly |
| stack/book P&L target-vol | 864 | 31.6 | 32.6 | 5.6 | -27.4 | 1.5 | 4 | -27.4 | mostly |
| continuous (ref/now)^p | 10272 | 15.5 | 21.1 | 3.7 | 34.2 | -29.8 | 4 | -29.8 | mostly |
| special rules | 1824 | 6.0 | 8.8 | 12.6 | -31.6 | 8.9 | 4 | -31.6 | mostly |
| skip steps (lo=0), pooled grid | 7463 | 1.8 | 5.6 | -27.4 | 0.6 | -11.0 | 3 | -27.4 | unstable |
| graded 3-step | 5021 | 13.1 | -10.3 | -22.8 | -23.9 | 31.4 | 2 | -23.9 | unstable |
| z-score steps | 3660 | - | - | -27.4 | -71.3 | -0.5 | 0 | -71.3 | unstable |

Plainly: the stable verdict belongs to the scale families (SCALE single measure 5/5, min +25 %; per-book/session scope 5/5 but its split B is only +1.7 %; consensus SCALE 5/5, min +5 %). The skip, graded-to-zero and z-score families flip sign between halves. Caveat: the 20 single measures in "SCALE single measure" were ranked on the whole sample, so that row is optimistic; the consensus row (no measure picked) is the clean test.

## 1c. SCALE rules (never zero, on top of the ER sizer) - best 10 by tolerant equal-mean score; p own / p fam (VT set); live-week d$ (first-order)
| cell | scope | cut L6M/PRE/X' | EQ cut L6M/PRE/X' | s | d mean L6M $/wk | p own / p fam | live wk d$ | max lots at once (Q1-A 20) |
|---|---|---|---|---|---|---|---|---|
| r_gk1_w10_all60 cont [2, 0.25] | [book, K7, P7, M7, A7, O7] | +14/+50/+52 | +23/+56/+57 | 0.90 | +2697 | 0.005 / 0.383 | -47559 | 17.0 |
| r_gk1_w10_all60 cont [2, 0.25] | [book, P7, K7] | +14/+50/+49 | +21/+55/+54 | 0.91 | +2350 | 0.005 / 0.478 | -45243 | 18.2 |
| q_gk1_w10_all60 step [0.6, 0.5] | [pool] | +29/+46/+47 | +38/+53/+54 | 0.87 | +3271 | 0.005 / 0.502 | -33836 | 16.6 |
| r_atr1_n14_all60 cont [2, 0.25] | [book, K7, P7, M7, A7, O7] | +16/+49/+48 | +24/+54/+53 | 0.90 | +2595 | 0.005 / 0.542 | -40993 | 18.0 |
| r_atr1_n14_all60 cont [2, 0.25] | [book, P7, K7] | +14/+48/+48 | +21/+52/+53 | 0.91 | +2211 | 0.005 / 0.602 | -38676 | 18.3 |
| r_gk1_w10_all60 step [1.25, 0.5] | [pool] | +18/+46/+47 | +26/+52/+52 | 0.90 | +2420 | 0.005 / 0.617 | -26638 | 17.1 |
| r_gk1_w10_all60 step [1.1, 0.5] | [pool] | +32/+46/+53 | +39/+51/+58 | 0.90 | +2533 | 0.005 / 0.622 | -33836 | 17.1 |
| r_gk1_w10_all60 cont [2, 0.5] | [pool] | +24/+48/+48 | +29/+51/+51 | 0.93 | +1678 | 0.005 / 0.622 | -33838 | 17.7 |
| r_park15_w6_all60 cont [2, 0.25] | [book, K7, P7, M7, A7, O7] | +25/+45/+53 | +32/+51/+57 | 0.90 | +2465 | 0.005 / 0.652 | -48642 | 17.2 |
| r_ewma1_l90_all60 cont [2, 0.25] | [book, K7, P7, M7, A7, O7] | +16/+46/+49 | +22/+50/+53 | 0.93 | +1741 | 0.005 / 0.667 | -41991 | 18.6 |

## 1d. Price-source / roll check (ZN-CORE and SZ-FGH finding)
bars1m_NQ (as read by C.nq1m) has 12 roll gaps of 184-318 pts at 00:00 UTC on the roll Wednesdays (2023-06-14 ... 2026-09-16) and none visible for the 2024-12 and 2025-06 rolls (weekend gaps there are market gaps, no +200 pt jump). They are additively back-adjusted in code/th_sz_vt/vt_roll.py and every vt feature, cell, WF, null and the ledger were rebuilt (pre-fix files in vt/preroll). Which of the 53 measures cross a roll: Parkinson and Garman-Klass use bar-internal high/low/open/close, so they are NOT affected (0 % of signals change > 5 %); ATR, rv1/rv5 and EWMA use the previous close or returns and WERE affected (0.2 % of signals for ATR, 0.4-0.6 % rv, 0.8 % EWMA(1-min), 2.5 % EWMA(5-min), up to 7.7 % for lambda .99); 24.5 % of the 21,135 trades have at least one of the 610 ratio features changed > 5 % (long-memory EWMA and the 60-day norms crossing a roll), but each single cell is affected on 0-0.4 % of trades (e.g. park1_w10_all40 0 %, ewma5_l90_all40 0.35 %). The range-ratio and VIX columns (rr_*, vix_*, from SZ-AB feat files, overnight range crossing a roll) were NOT rebuilt and are excluded from every claim. Ranks moved slightly after the rebuild; top cells are Parkinson/GK cells, so the labels did not change.


## Family A - ER family

ER family: 16290 cells (12240 down-only); best by equal-mean L6M maxDD cut: ER-NQ er_nq_b3_n14 t2 [0.6, 0.0, 1.0] cuts L6M maxDD +83% at equal lots (d mean -10512 $/wk) and +67% at equal mean (PRE +14%, X' +19%); placebo p 0.05, family p 1.00, WF n/a -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ er_nq_b3_n14 t2 [owner, not roll-excl] | [0.6, 0.0, 1.0] | +83 / +21 / +55 / +58 | -30 | +85 | -10512 | +67 / -53 / +14 / +19 | 42.4 | 91% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.05 | 1.00 |  | -103485 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b5_n45 t2 [owner, not roll-excl] | [0.25, 0.0, 1.0] | +64 / +1 / +44 / -8 | -52 | +63 | -4365 | +55 / -22 / +31 / -34 | 32.2 | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 |  | -38280 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b3_n14 t2 [owner, not roll-excl] | [0.55, 0.0, 1.0] | +66 / +26 / +47 / +37 | -3 | +75 | -6998 | +49 / -11 / +20 / +6 | 27.4 | 88% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.09 | 1.00 |  | -91335 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b30_n10 t2 [owner, not roll-excl] | [0.5, 0.0, 1.0] | +52 / -12 / +17 / +35 | -53 | +61 | -1968 | +47 / -23 / +9 / +29 | 26.2 | 78% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 |  | -72540 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b5_n60 t3 [owner, not roll-excl] | [0.2, 0.4, 0.25, 0.5, 1.0] | +58 / +1 / +46 / +30 | +1 | +60 | -4590 | +47 / -25 / +31 / +11 | 26.1 | 35% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | -35797 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b30_n10 t2 [owner, not roll-excl] | [0.5, 0.0, 1.0] | +63 / +25 / +44 / +45 | -55 | +61 | -6723 | +46 / -10 / +18 / +20 | 25.5 | 70% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 |  | -75660 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b5_n45 t2 [owner, not roll-excl] | [0.25, 0.0, 1.0] | +65 / +27 / +51 / -1 | -82 | +63 | -8154 | +45 / -15 / +23 / -59 | 26.5 | 73% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.08 | 1.00 |  | -49405 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b5_n5 t2 [owner, not roll-excl] | [0.1, 0.0, 1.0] | +17 / -30 / -3 / -31 | +157 | +29 | +11724 | +45 / +14 / +31 / +13 | 27.6 | 44% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | -25004 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b5_n5 t2 [owner, not roll-excl] | [0.1, 0.0, 1.0] | +36 / -9 / +8 / +9 | +62 | +42 | +3125 | +44 / +5 / +20 / +21 | 24.8 | 10% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.06 | 1.00 |  | -32210 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| ER-xinst er_max2_b15_n20 t3 [owner, not roll-excl] | [0.35, 0.45, 0.25, 0.5, 1.0] | +44 / -24 / +35 / +11 | +22 | +57 | -300 | +44 / -26 / +34 / +10 | 27.4 | 33% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | -32510 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ er_nq_b15_n14 t2 [owner, not roll-excl] | [0.55, 0.5, 1.5] | +21 / +2 / -18 / -57 | +51 | +38 | +9453 | +44 / +30 / +17 / -12 | 26.7 | 32% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.05 | 1.00 |  | +46687 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b15_n14 t2 [owner, not roll-excl] | [0.5, 0.5, 1.5] | +10 / -9 / +10 / -59 | +53 | +28 | +11306 | +39 / +26 / +39 / -8 | 25.2 | 36% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | +64797 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| ER-NQ er_nq_b3_n14 t2 [owner, not roll-excl] | [0.55, 0.5, 1.5] | +21 / -21 / +30 / -25 | +110 | +30 | +7608 | +38 / +6 / +46 / +3 | 28.4 | 34% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | -11846 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family B - Volatility target

Volatility target: 3994 cells (3626 down-only); best by equal-mean L6M maxDD cut: VOL-pool vr_park_w10_g20 stepv [1.25, 0.0] cuts L6M maxDD +53% at equal lots (d mean +3219 $/wk) and +59% at equal mean (PRE +52%, X' +74%); placebo p 0.02, family p 0.28, WF n/a -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-pool vr_park_w10_g20 stepv [ROLL-EXCL] | [1.25, 0.0] | +53 / +58 / +45 / +70 | -29 | +64 | +3219 | +59 / +63 / +52 / +74 | 35.8 | 56% | FIRST-ORDER SCREEN ONLY | +54 / -1.5 / +98 | 0.02 | 0.28 |  | -48050 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_gk_w10_g20 stepv [ROLL-EXCL] | [1.25, 0.0] | +54 / +59 / +57 / +55 | -7 | +66 | +2507 | +59 / +63 / +61 / +59 | 34.8 | 56% | FIRST-ORDER SCREEN ONLY | +63 / -9.3 / +9 | 0.02 | 0.28 |  | -63235 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_atr_b1_n5_g20 stepv [owner, not roll-excl] | [1.25, 0.0] | +32 / +30 / +21 / +56 | +96 | +66 | +13166 | +57 / +56 / +50 / +72 | 34.0 | 78% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.32 |  | -13954 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_rv1_w10_g20 stepv [owner, not roll-excl] | [1.25, 0.0] | +47 / +14 / -38 / +52 | +141 | +59 | +5702 | +56 / +29 / -14 / +60 | 39.2 | 78% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 0.40 |  | -53054 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_gk_w10_g20 stepv [owner, not roll-excl] | [1.25, 0.0] | +33 / +46 / +48 / +47 | +47 | +54 | +11037 | +54 / +63 / +65 / +64 | 33.4 | 77% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.12 |  | -36404 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_rv5_w48_bk stepv [owner, not roll-excl] | [1.25, 0.0] | +22 / +7 / +20 / +9 | +130 | +50 | +15192 | +54 / +44 / +52 / +46 | 31.6 | 63% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.71 |  | -86674 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_atr_b15_n5_g20 stepv [owner, not roll-excl] | [1.25, 0.0] | +28 / +38 / +36 / +51 | +94 | +43 | +12779 | +54 / +60 / +58 / +68 | 32.9 | 75% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.28 |  | -70190 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_atr_b1_n5_g20 stepv [ROLL-EXCL] | [1.25, 0.0] | +48 / +47 / +47 / +65 | -24 | +66 | +2722 | +53 / +52 / +53 / +69 | 31.0 | 58% | FIRST-ORDER SCREEN ONLY | +49 / -1.6 / +165 | 0.03 | 0.68 |  | -42935 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_atr_b15_n5_g20 stepv [ROLL-EXCL] | [1.25, 0.0] | +49 / +49 / +55 / +66 | -22 | +55 | +1864 | +53 / +53 / +58 / +68 | 31.1 | 51% | FIRST-ORDER SCREEN ONLY | +60 / -10.8 / +1 | 0.02 | 0.28 |  | -80055 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_ewma5_l94_g20 stepv [ROLL-EXCL] | [1.25, 0.0] | +44 / +53 / +26 / +57 | -36 | +65 | +3564 | +52 / +59 / +36 / +63 | 29.5 | 52% | FIRST-ORDER SCREEN ONLY | +44 / -0.2 / +23 | 0.05 | 1.00 |  | -81595 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-pool vr_gk_w10_g20 pow [owner, not roll-excl] | [1.0, 0.5, 1.5] | +30 / +26 / +34 / +32 | +77 | +36 | +5653 | +45 / +42 / +48 / +46 | 25.3 | 36% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.97 |  | -20343 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_atr_b15_n5_g20 pow [owner, not roll-excl] | [1.0, 0.5, 1.5] | +26 / +21 / +16 / +31 | +50 | +29 | +7156 | +43 / +40 / +36 / +47 | 26.7 | 38% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | -23055 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| VOL-pool vr_park_w10_g20 pow [owner, not roll-excl] | [1.0, 0.5, 1.5] | +31 / +25 / +30 / +32 | +61 | +34 | +4187 | +42 / +37 / +41 / +43 | 24.0 | 36% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 |  | -18559 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family C - Equal-risk / parity

Equal-risk / parity: 28 cells (16 down-only); best by equal-mean L6M maxDD cut: riskcap_per_trade R$3600 cuts L6M maxDD +31% at equal lots (d mean -1544 $/wk) and +26% at equal mean (PRE +38%, X' +46%); placebo p 0.03, family p 1.00, WF +32 -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| riskcap_per_trade [ROLL-EXCL] | R$3600 | +31 / +34 / +42 / +50 | -21 | +12 | -1544 | +26 / +29 / +38 / +46 | 19.4 | 22% | FIRST-ORDER SCREEN ONLY | +1 / +30.0 / +2 | 0.03 | 1.00 | +32 | -38377 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| volparity_down [owner, not roll-excl] | win120_refmed | +56 / +39 / +46 / +40 | +33 | +4 | -16626 | -3 / -41 / -25 / -38 | 18.5 | 30% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.05 | 1.00 | +32 |  | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| riskcap_per_trade [owner, not roll-excl] | R$4800 | +20 / +14 / +21 / +20 | -16 | +2 | -6711 | -4 / -12 / -2 / -4 | 18.3 | 8% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.33 | 1.00 | +32 | -27016 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| volparity_down [owner, not roll-excl] | win60_refmed | +56 / +36 / +49 / +34 | +39 | -4 | -16998 | -6 / -53 / -22 / -57 | 17.9 | 30% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.10 | 1.00 | +32 |  | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| riskcap_per_trade [owner, not roll-excl] | R$6000 | +14 / +9 / +17 / +18 | -17 | -3 | -5942 | -8 / -14 / -4 / -3 | 17.7 | 7% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.50 | 1.00 | +32 | -17840 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| riskcap_per_trade [owner, not roll-excl] | R$2400 | +33 / +46 / +55 / +67 | +21 | -6 | -13175 | -22 / +2 / +17 / +40 | 15.5 | 24% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.43 | 1.00 | +32 | -51309 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| volparity_down [owner, not roll-excl] | win20_refmin | +57 / +59 / +70 / +77 | +46 | -8 | -18877 | -22 / -16 / +15 / +34 | 15.5 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.29 | 1.00 | +32 |  | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| esparity_down [owner, not roll-excl] | last100tr_refmin | +57 / +59 / +70 / +71 | +47 | -7 | -18979 | -22 / -17 / +14 / +18 | 15.5 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.21 | 1.00 | +32 |  | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| esparity_down [owner, not roll-excl] | last50tr_refmin | +57 / +59 / +70 / +75 | +47 | -7 | -18899 | -23 / -16 / +14 / +29 | 15.5 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.23 | 1.00 | +32 |  | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| volparity_down [owner, not roll-excl] | win60_refmin | +57 / +58 / +70 / +43 | +46 | -7 | -18904 | -23 / -19 / +14 / -61 | 15.5 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.18 | 1.00 | +32 |  | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| volparity_up [owner, not roll-excl] | win60_refmed_clip.5-1.5 | +35 / +29 / +45 / +21 | -2 | +27 | -6463 | +17 / +9 / +30 / -1 | 22.8 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.06 | 1.00 | +32 |  | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| volparity_up [owner, not roll-excl] | win20_refmin_clip.5-1.5 | +47 / +44 / +43 / +53 | +26 | +1 | -14157 | -2 / -9 / -10 / +8 | 18.6 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.24 | 1.00 | +32 |  | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| volparity_up [owner, not roll-excl] | win120_refmin_clip.5-1.5 | +47 / +44 / +43 / +26 | +26 | +1 | -14158 | -2 / -9 / -10 / -44 | 18.6 | 38% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.28 | 1.00 | +32 |  | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family D - Equity-curve / state

Equity-curve / state: 160 cells (146 down-only); best by equal-mean L6M maxDD cut: week_loss_stack X20000_f0.00 cuts L6M maxDD +44% at equal lots (d mean -2097 $/wk) and +40% at equal mean (PRE +7%, X' -50%); placebo p 0.03, family p 1.00, WF +36 -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| week_loss_stack [owner, not roll-excl] | X20000_f0.00 | +44 / +14 / +14 / -39 | +3 | +44 | -2097 | +40 / +7 / +7 / -50 | 31.6 | 24% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 | +36 | +0 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| consec_loss [owner, not roll-excl] | stack_k5_f0.00 | +34 / +33 / +47 / -43 | -46 | +38 | +413 | +34 / +34 / +48 / -41 | 29.0 | 22% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 | +36 | -5710 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| consec_loss [owner, not roll-excl] | stack_k4_f0.00 | +39 / -23 / +27 / -43 | -38 | +53 | -2521 | +33 / -34 / +20 / -57 | 28.5 | 32% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +36 | -84210 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| dayloss_stack$ [ROLL-EXCL] | X16000_f0.00 | +30 / -28 / +18 / +4 | -46 | +35 | +478 | +31 / -26 / +19 / +6 | 27.6 | 9% | FIRST-ORDER SCREEN ONLY | +17 / +13.1 / +5 | 0.01 | 1.00 | +36 | +0 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| eqdd_book_20d_R [ROLL-EXCL] | Y1R_f0.50_sticky | +47 / +41 / +45 / +47 | +24 | +26 | -5195 | +30 / +23 / +28 / +31 | 25.4 | 33% | +24 /  /  /  (-5611; engine-sizer mode) | -6 / +52.1 / +116 | 0.01 | 0.70 | +36 | +0 | S1 | CANDIDATE (own-p only; family p 0.70) [EXACT partial] |
| eqdd_book_20d_R [ROLL-EXCL] | Y4R_f0.25_sticky | +44 / +34 / +51 / +37 | +38 | +34 | -4745 | +28 / +15 / +37 / +18 | 25.0 | 29% | FIRST-ORDER SCREEN ONLY | -27 / +71.2 / +120 | 0.03 | 0.97 | +36 | +0 | S1 | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| consec_loss [owner, not roll-excl] | book_k3_f0.00 | +35 / +26 / +44 / -7 | +1 | +24 | -3122 | +27 / +17 / +38 / -20 | 26.2 | 14% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.05 | 1.00 | +36 | -72285 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| eqdd_stack_20d [ROLL-EXCL] | Y10000_f0.50_sticky | +44 / +44 / +43 / +46 | +24 | +25 | -6783 | +26 / +26 / +25 / +28 | 25.4 | 30% | FIRST-ORDER SCREEN ONLY | -24 / +68.6 / +115 | 0.01 | 0.53 | +36 | +0 | S1 | CANDIDATE (own-p only; family p 0.53) [FIRST-ORDER SCREEN ONLY] |
| eqdd_stack_20d [owner, not roll-excl] | Y10000_f0.50_live | +41 / +43 / +43 / +18 | +29 | +17 | -6609 | +24 / +26 / +26 / -6 | 24.9 | 26% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.05 | 1.00 | +36 | +0 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| eqdd_book_20d_R [ROLL-EXCL] | Y2R_f0.25_sticky | +45 / +52 / +63 / +58 | +47 | +22 | -6957 | +22 / +31 / +47 / +40 | 20.7 | 33% | FIRST-ORDER SCREEN ONLY | -28 / +73.4 / +116 | 0.05 | 1.00 | +36 | +0 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| eqdd_stack_UP_at_high [owner, not roll-excl] | Y20000_f0.50_up1.25 | +36 / +39 / +40 / -3 | +32 | +13 | -4856 | +23 / +27 / +29 / -23 | 24.7 | 29% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.04 | 1.00 | +36 | +25118 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| antimartingale_UP [owner, not roll-excl] | book_n4_x1.50 | +4 / -1 / -0 / -2 | +1 | -0 | -300 | +3 / -2 / -1 / -3 | 19.6 | 2% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.05 | 1.00 | +36 | -655 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| antimartingale_UP [owner, not roll-excl] | book_n4_x1.25 | +0 / -1 / -1 / -1 | -2 | -2 | -54 | -0 / -1 / -1 / -1 | 19.0 | 1% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.17 | 1.00 | +36 | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family E - Exposure / concentration

Exposure / concentration: 74 cells (74 down-only); best by equal-mean L6M maxDD cut: same_side_lots_cap cap6_skip cuts L6M maxDD +41% at equal lots (d mean -2601 $/wk) and +33% at equal mean (PRE +37%, X' +53%); placebo p 0.05, family p 1.00, WF +31 -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| same_side_lots_cap [ROLL-EXCL] | cap6_skip | +41 / +49 / +45 / +59 | -18 | +44 | -2601 | +33 / +42 / +37 / +53 | 21.6 | 15% | FIRST-ORDER SCREEN ONLY | +7 / +34.1 / +51 | 0.05 | 1.00 | +31 | -53550 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| total_lots_cap [ROLL-EXCL] | cap6_skip | +41 / +52 / +45 / +46 | -6 | +40 | -3364 | +30 / +43 / +35 / +35 | 20.7 | 18% | FIRST-ORDER SCREEN ONLY | +21 / +19.9 / +48 | 0.05 | 1.00 | +31 | -52835 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| corr_same_side [owner, not roll-excl] | N30min_f0.5_ge1_others | +37 / +36 / +30 / +15 | +23 | +21 | -6495 | +20 / +18 / +10 / -9 | 23.6 | 19% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.06 | 1.00 | +31 | -35277 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| newentry_haircut_day_dd [owner, not roll-excl] | Y15000_f0.0 | +31 / -1 / +39 / -32 | +11 | +17 | -5255 | +16 / -24 / +25 / -61 | 22.6 | 19% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.15 | 1.00 | +31 | +0 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| total_lots_cap [owner, not roll-excl] | cap4_skip | +58 / +28 / +71 / +44 | +37 | +34 | -15045 | +13 / -49 / +40 / -16 | 21.8 | 32% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 | +31 | -73240 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| newentry_haircut_day_dd [owner, not roll-excl] | Y15000_f0.5 | +12 / +8 / +29 / -0 | +0 | +11 | -1616 | +7 / +3 / +25 / -6 | 20.4 | 4% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.08 | 1.00 | +31 | +0 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| same_side_lots_cap [owner, not roll-excl] | cap12_skip | +6 / +20 / +2 / -19 | +4 | +4 | +105 | +7 / +21 / +3 / -18 | 20.4 | 1% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 | +31 | -18780 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| same_side_lots_cap [owner, not roll-excl] | cap4_trunc | +52 / +44 / +40 / +48 | +35 | +25 | -14187 | +7 / -9 / -17 / -1 | 20.4 | 39% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.08 | 1.00 | +31 | -35944 | S1 | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| newentry_haircut_day_dd [ROLL-EXCL] | Y24000_f0.0 | +1 / +2 / +29 / -4 | -35 | +21 | +1621 | +7 / +8 / +32 / +2 | 20.4 | 5% | FIRST-ORDER SCREEN ONLY | +7 / -5.3 / +1 | 0.08 | 1.00 | +31 | +0 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| same_side_lots_cap [owner, not roll-excl] | cap8_trunc | +18 / +24 / +10 / +0 | +7 | +8 | -3545 | +7 / +13 / -2 / -14 | 20.4 | 12% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.11 | 1.00 | +31 | -11180 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

## Family F - Time / session

Time / session: 118 cells (118 down-only); best by equal-mean L6M maxDD cut: dow {"dow": 2, "m": 0} cuts L6M maxDD +51% at equal lots (d mean +1120 $/wk) and +54% at equal mean (PRE +5%, X' +44%); placebo p 0.01, family p 1.00, WF n/a -> LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| dow [ROLL-EXCL] | {"dow": 2, "m": 0} | +51 / +27 / +0 / +41 | +12 |  | +1120 | +54 / +31 / +5 / +44 |  | 20% | FIRST-ORDER SCREEN ONLY | +23 / +28.2 / +1 | 0.01 | 1.00 |  | -28160 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| slot48 [ROLL-EXCL] | {"m": 0, "slot": 8} | +12 / -3 / -1 / -11 | -28 |  | +2552 | +21 / +7 / +9 / -0 |  | 3% | FIRST-ORDER SCREEN ONLY | +7 / +5.4 / +19 | 0.29 | 1.00 |  | +3890 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| dow [ROLL-EXCL] | {"dow": 0, "m": 0} | +24 / -98 / +22 / +47 | +42 |  | -1865 | +18 / -115 / +15 / +43 |  | 19% | FIRST-ORDER SCREEN ONLY | +11 / +12.9 / +141 | 0.08 | 1.00 |  | -28440 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| dow [ROLL-EXCL] | {"dow": 2, "m": 0.5} | +15 / +11 / +6 / +25 | +1 |  | +46 | +15 / +11 / +6 / +25 |  | 7% | FIRST-ORDER SCREEN ONLY | +7 / +7.7 / +21 | 0.05 | 1.00 |  | -6193 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| slot48 [owner, not roll-excl] | {"m": 0, "slot": 40} | +12 / -6 / -8 / +16 | +7 |  | +139 | +12 / -5 / -8 / +16 |  | 3% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.05 | 1.00 |  | +3120 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| slot48 [ROLL-EXCL] | {"m": 0, "slot": 10} | +9 / +3 / +5 / +3 | -16 |  | +652 | +12 / +6 / +7 / +6 |  | 2% | FIRST-ORDER SCREEN ONLY | +13 / -3.8 / +4 | 0.29 | 1.00 |  | -8855 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| slot48 [ROLL-EXCL] | {"m": 0, "slot": 22} | +8 / +4 / +5 / +8 | -17 |  | +883 | +11 / +7 / +8 / +11 |  | 5% | FIRST-ORDER SCREEN ONLY | -1 / +8.7 / +160 | 0.30 | 1.00 |  | -10145 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| slot48 [ROLL-EXCL] | {"m": 0, "slot": 15} | +2 / -2 / +9 / +2 | -11 |  | +2463 | +11 / +7 / +17 / +11 |  | 2% | FIRST-ORDER SCREEN ONLY | -18 / +19.9 / +191 | 0.07 | 1.00 |  | +5425 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| slot48 [ROLL-EXCL] | {"m": 0.5, "slot": 15} | +6 / -0 / +3 / +0 | -7 |  | +1116 | +10 / +4 / +7 / +4 |  | 1% | FIRST-ORDER SCREEN ONLY | -6 / +12.0 / +178 | 0.02 | 1.00 |  | +2672 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| slot48 [ROLL-EXCL] | {"m": 0.5, "slot": 8} | +6 / -3 / +2 / -2 | -12 |  | +902 | +9 / +1 / +5 / +2 |  | 1% | FIRST-ORDER SCREEN ONLY | +1 / +5.2 / +86 | 0.17 | 1.00 |  | +1382 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

## Family G - Signal quality

Signal quality: 1214 cells (890 down-only); best by equal-mean L6M maxDD cut: qgate {"feat": "nA40", "m": 0, "q": 0.1, "tail": "low"} cuts L6M maxDD +90% at equal lots (d mean -11981 $/wk) and +78% at equal mean (PRE -7%, X' -128%); placebo p 0.30, family p 1.00, WF n/a -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate [owner, not roll-excl] | {"feat": "nA40", "m": 0, "q": 0.1, "tail": "low"} | +90 / +18 / +53 / +0 | -40 |  | -11981 | +78 / -88 / -7 / -128 |  | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.30 | 1.00 |  | -74295 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA40", "m": 0, "q": 0.5, "tail": "low"} | +90 / +18 / +53 / +0 | -40 |  | -11981 | +78 / -88 / -7 / -128 |  | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.20 | 1.00 |  | -74295 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA40", "m": 0, "q": 0.3, "tail": "low"} | +90 / +18 / +53 / +0 | -40 |  | -11981 | +78 / -88 / -7 / -128 |  | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.22 | 1.00 |  | -74295 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA40", "m": 0, "q": 0.2, "tail": "low"} | +90 / +18 / +53 / +0 | -40 |  | -11981 | +78 / -88 / -7 / -128 |  | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.27 | 1.00 |  | -74295 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA20", "m": 0, "q": 0.2, "tail": "low"} | +87 / +57 / +58 / +0 | -76 |  | -16790 | +39 / -101 / -95 / -369 |  | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.49 | 1.00 |  | -96325 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA20", "m": 0, "q": 0.3, "tail": "low"} | +87 / +57 / +58 / +0 | -76 |  | -16790 | +39 / -101 / -95 / -369 |  | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.61 | 1.00 |  | -96325 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA20", "m": 0, "q": 0.1, "tail": "low"} | +87 / +57 / +58 / +0 | -76 |  | -16790 | +39 / -101 / -95 / -369 |  | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.66 | 1.00 |  | -96325 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA20", "m": 0, "q": 0.5, "tail": "low"} | +87 / +57 / +58 / +0 | -76 |  | -16790 | +39 / -101 / -95 / -369 |  | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.66 | 1.00 |  | -96325 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [ROLL-EXCL] | {"feat": "twap_slope_sg", "m": 0, "q": 0.5, "tail": "low"} | +43 / -61 / +32 / +0 | +27 |  | -2502 | +36 / -81 / +23 / -13 |  | 45% | FIRST-ORDER SCREEN ONLY | -18 / +61.3 / +966 | 0.30 | 1.00 |  | -28565 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate_x_er [owner, not roll-excl] | {"er": "erhigh", "feat": "ema_x_sg", "m": 0, "q": 0.5, "tail": "high"} | +47 / +17 / -5 / +0 | -42 |  | -4654 | +34 / -4 / -32 / -25 |  | 25% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.51 | 1.00 |  | -47490 | S1 | no [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate_x_er [owner, not roll-excl] | {"er": "erlow", "feat": "f_ema20_rel", "m": 1.5, "q": 0.5, "tail": "lo | +14 / -8 / +4 / +0 | +60 |  | +4952 | +28 / +10 / +20 / +17 |  | 14% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 1.00 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| qgate_UP [owner, not roll-excl] | {"feat": "nA40", "m": 1.5, "q": 0.2, "tail": "high"} | +6 / -26 / -3 / +0 | +68 |  | +4992 | +23 / -3 / +16 / +19 |  | 24% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 1.00 |  | +19148 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| qgate_x_er [owner, not roll-excl] | {"er": "erlow", "feat": "f_tot_rel_base", "m": 1.5, "q": 0.5, "tail":  | +8 / -22 / -2 / +0 | +56 |  | +4543 | +23 / -3 / +14 / +16 |  | 20% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family H - Regime

Regime: 224 cells (149 down-only); best by equal-mean L6M maxDD cut: regime {"cond": "adx5_ge20", "m": 0.5} cuts L6M maxDD +41% at equal lots (d mean -2574 $/wk) and +33% at equal mean (PRE +29%, X' +35%); placebo p 0.01, family p 1.00, WF n/a -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime [ROLL-EXCL] | {"cond": "adx5_ge20", "m": 0.5} | +41 / +20 / +38 / +43 | -9 |  | -2574 | +33 / +9 / +29 / +35 |  | 30% | FIRST-ORDER SCREEN ONLY | +29 / +12.3 / +18 | 0.01 | 1.00 |  | -33303 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [owner, not roll-excl] | {"cond": "on_ratio_ge0.8", "m": 0} | +41 / -5 / +37 / -81 | +2 |  | -4609 | +29 / -26 / +24 / -117 |  | 35% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.76 | 1.00 |  | -62715 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [owner, not roll-excl] | {"cond": "gap_with_ge0.25", "m": 0.5} | +35 / +16 / +16 / +7 | -26 |  | -3353 | +24 / +1 / +2 / -9 |  | 16% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.49 | 1.00 |  | -6578 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [owner, not roll-excl] | {"cond": "prior_range_day", "m": 0} | +39 / +1 / +9 / -107 | -5 |  | -5768 | +23 / -25 / -16 / -162 |  | 29% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.60 | 1.00 |  | -59710 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [ROLL-EXCL] | {"cond": "on_ratio_ge0.8", "m": 0.5} | +23 / +14 / +31 / +1 | -19 |  | -715 | +21 / +12 / +29 / -2 |  | 11% | FIRST-ORDER SCREEN ONLY | +16 / +7.8 / +18 | 0.06 | 1.00 |  | -17583 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [ROLL-EXCL] | {"cond": "od_with_ge0.05", "m": 0} | +21 / +17 / -4 / +36 | -19 |  | -17 | +21 / +17 / -4 / +36 |  | 17% | FIRST-ORDER SCREEN ONLY | -9 / +30.0 / +265 | 0.65 | 1.00 |  | -515 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| regime [ROLL-EXCL] | {"cond": "on_ratio_ge1.0", "m": 0.5} | +21 / +4 / +15 / +4 | -15 |  | -652 | +19 / +1 / +13 / +1 |  | 7% | FIRST-ORDER SCREEN ONLY | +16 / +5.4 / +13 | 0.12 | 1.00 |  | -18285 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [owner, not roll-excl] | {"cond": "od_against_ge0.05", "m": 0} | +9 / +3 / +13 / -30 | +28 |  | +2989 | +19 / +14 / +22 / -16 |  | 9% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.35 | 1.00 |  | -2340 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [ROLL-EXCL] | {"cond": "ib_ext_with_ge0.25", "m": 0} | +15 / -2 / +4 / -1 | -24 |  | +910 | +18 / +2 / +8 / +3 |  | 6% | FIRST-ORDER SCREEN ONLY | +6 / +8.8 / +79 | 0.26 | 1.00 |  | -11905 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [ROLL-EXCL] | {"cond": "od_with_ge0.10", "m": 0} | +21 / +17 / +3 / +21 | -3 |  | -1073 | +17 / +13 / -2 / +17 |  | 15% | FIRST-ORDER SCREEN ONLY | -10 / +30.4 / +258 | 0.87 | 1.00 |  | -515 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime_UP [owner, not roll-excl] | {"cond": "twap_slope_with_ge0.25", "m": 1.5} | -2 / -48 / -13 / -40 | +73 |  | +8439 | +25 / -8 / +17 / -2 |  | 23% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.30 | 1.00 |  | +34999 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| regime_UP [owner, not roll-excl] | {"cond": "both_agree_15", "m": 1.5} | -26 / -48 / -50 / -48 | +120 |  | +15295 | +25 / +12 / +11 / +12 |  | 74% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| regime_UP [owner, not roll-excl] | {"cond": "both_agree_60", "m": 1.5} | -25 / -39 / -39 / -3 | +107 |  | +13360 | +23 / +15 / +14 / +37 |  | 76% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 1.00 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family I - Book-level recent performance

Book-level recent performance: 188 cells (186 down-only); best by equal-mean L6M maxDD cut: I5 stack rolling Calmar {"D": 20, "mult": 0.0, "x": 3.0} cuts L6M maxDD +68% at equal lots (d mean -8191 $/wk) and +49% at equal mean (PRE +26%, X' +53%); placebo p 0.05, family p 1.00, WF +41 -> CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| I5 stack rolling Calmar [ROLL-EXCL] | {"D": 20, "mult": 0.0, "x": 3.0} | +68 / +24 / +55 / +71 | +102 | +52 | -8191 | +49 / -23 / +26 / +53 | 27.1 | 72% | FIRST-ORDER SCREEN ONLY | -14 / +82.6 / +169 | 0.05 | 1.00 | +41 | -104810 | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| I3 book rolling Calmar [ROLL-EXCL] | {"D": 10, "mult": 0.0, "x": 1.0} | +39 / +6 / +44 / +63 | +19 | +32 | -2479 | +31 / -7 / +36 / +58 | 18.1 | 61% | FIRST-ORDER SCREEN ONLY | +24 / +15.0 / +2 | 0.08 | 1.00 | +41 | -105580 | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| I5 stack rolling Calmar [ROLL-EXCL] | {"D": 10, "mult": 0.0, "x": 3.0} | +57 / +65 / +55 / +83 | +127 | +59 | -8954 | +25 / +40 / +23 / +70 | 18.6 | 73% | FIRST-ORDER SCREEN ONLY | +4 / +52.4 / +144 | 0.05 | 1.00 | +41 | -104810 | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| I5 stack rolling Calmar [ROLL-EXCL] | {"D": 20, "mult": 0.5, "x": 3.0} | +34 / +47 / +41 / +49 | +25 | +41 | -4095 | +19 / +35 / +27 / +37 | 19.7 | 28% | +8 /  /  /  (-1584; table (IJK driver) mode) | -13 / +47.6 / +133 | 0.07 | 0.85 | +41 | -37680 | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.85) [EXACT partial] |
| I3 book rolling Calmar [ROLL-EXCL] | {"D": 10, "mult": 0.5, "x": 1.0} | +22 / +32 / +47 / +47 | -1 | +24 | -1239 | +17 / +27 / +43 / +43 | 17.9 | 23% | +23 /  /  /  (-1466; table (IJK driver) mode) | +8 / +14.1 / +7 | 0.10 | 0.98 | +41 | -38365 | FIRST-ORDER SCREEN ONLY | LEAD [EXACT partial] |
| I3 book rolling Calmar [ROLL-EXCL] | {"D": 10, "mult": 0.5, "x": 2.0} | +34 / +47 / +47 / +51 | +34 | +31 | -4857 | +15 / +32 / +32 / +36 | 23.4 | 28% | +11 /  /  /  (-4799; table (IJK driver) mode) | -0 / +34.5 / +100 | 0.13 | 0.96 | +41 | -38365 | FIRST-ORDER SCREEN ONLY | LEAD [EXACT partial] |
| I3 book rolling Calmar [ROLL-EXCL] | {"D": 10, "mult": 0.0, "x": 0.5} | +24 / -18 / +36 / +9 | +43 | +22 | -2731 | +14 / -34 / +27 / -3 | 17.6 | 51% | FIRST-ORDER SCREEN ONLY | +11 / +12.5 / +3 | 0.14 | 0.99 | +41 | -102520 | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| I5 stack rolling Calmar [ROLL-EXCL] | {"D": 10, "mult": 0.5, "x": 2.0} | +28 / +42 / +42 / +40 | +49 | +25 | -3644 | +14 / +31 / +30 / +27 | 18.7 | 25% | FIRST-ORDER SCREEN ONLY | -15 / +43.0 / +115 | 0.08 | 0.96 | +41 | -37680 | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.96) [FIRST-ORDER SCREEN ONLY] |
| I4 stack trailing-D-days $ [ROLL-EXCL] | {"D": 10, "mult": 0.5, "thr_usd": 10000} | +18 / +30 / +26 / -40 | +8 | +10 | -1564 | +13 / +26 / +21 / -48 | 20.9 | 9% | FIRST-ORDER SCREEN ONLY | +5 / +12.5 / +7 | 0.10 | 0.92 | +41 | -25260 | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| I4 stack trailing-D-days $ [ROLL-EXCL] | {"D": 10, "mult": 0.0, "thr_usd": 20000} | +21 / +7 / +5 / -65 | +22 | +8 | -2813 | +12 / -4 / -6 / -85 | 19.8 | 18% | FIRST-ORDER SCREEN ONLY | +17 / +4.6 / -7 | 0.13 | 0.99 | +41 | -62800 | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| I6 up-allowed hot x1.5 / cold x0.5 [owner, not roll-excl] | {"N": 8, "thr_R": 2} | -9 / -9 / -10 / -24 | -16 | -11 | +983 | -4 / -4 / -5 / -19 | 13.3 | 34% | FIRST-ORDER SCREEN ONLY | -16 / +7.0 / +9 | 0.41 | 1.00 | +41 | +2320 | FIRST-ORDER SCREEN ONLY | UP (report) [FIRST-ORDER SCREEN ONLY] |
| I6 up-allowed hot x1.5 / cold x0.5 [owner, not roll-excl] | {"N": 8, "thr_R": 4} | -18 / +4 / -4 / -32 | -34 | -16 | -2792 | -34 / -9 / -18 / -50 | 11.1 | 11% | FIRST-ORDER SCREEN ONLY | -5 / -12.4 / -65 | 0.95 | 1.00 | +41 | -280 | FIRST-ORDER SCREEN ONLY | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family J - Combinations

Combinations: 1081 cells (1081 down-only); best by equal-mean L6M maxDD cut: J pair min {"a": "I:83d7d23f2f5d", "b": "ext-VT:b47d9923a960"} cuts L6M maxDD +89% at equal lots (d mean -4351 $/wk) and +86% at equal mean (PRE +48%, X' +72%); placebo p 0.02, family p 1.00, WF +35 -> CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| J pair min [ROLL-EXCL] | {"a": "I:83d7d23f2f5d", "b": "ext-VT:b47d9923a960"} | +89 / -7 / +58 / +78 | +14 | +92 | -4351 | +86 / -33 / +48 / +72 | 109.6 | 84% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "ext-B:9806533560c9", "b": "ext-G:cebf694ec6e2"} | +85 / +10 / +56 / +72 | -56 | +86 | +2604 | +86 / +20 / +60 / +75 | 105.6 | 72% | FIRST-ORDER SCREEN ONLY | +22 / +62.4 / +685 | 0.02 | 0.97 | +35 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "ext-L:53569966ba30", "b": "ext-VT:7edf0660d35c"} | +85 / +42 / +58 / +27 | -24 | +90 | +483 | +86 / +43 / +59 / +29 | 98.8 | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +35 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "ext-B:1b5942ac8cd6", "b": "ext-L:6fa81ee4110a"} | +85 / +36 / +61 / +51 | -46 | +90 | -662 | +85 / +34 / +60 / +49 | 94.3 | 71% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.97 | +35 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "ext-H:61f3cbb073a5", "b": "ext-VT:b47d9923a960"} | +86 / +61 / +78 / +81 | -18 | +88 | -3279 | +83 / +54 / +74 / +77 | 87.4 | 74% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.92 | +35 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "ext-B:9806533560c9", "b": "ext-E:E|total_lots_cap|cap4_trunc|se | +79 / +38 / +58 / +75 | -64 | +85 | +3902 | +82 / +47 / +64 / +79 | 81.4 | 69% | FIRST-ORDER SCREEN ONLY | +54 / +24.9 / +56 | 0.02 | 0.97 | +35 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "I:83d7d23f2f5d", "b": "ext-VT:a5a7135ca8ed"} | +85 / -1 / +62 / +34 | -19 | +91 | -3407 | +82 / -21 / +55 / +21 | 83.6 | 78% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 | +35 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "ext-B:9806533560c9", "b": "ext-F:e42de98e2549"} | +84 / +30 / +41 / +63 | -45 | +88 | -2828 | +82 / +21 / +34 / +58 | 93.7 | 63% | FIRST-ORDER SCREEN ONLY | +45 / +38.4 / +185 | 0.02 | 1.00 | +35 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "ext-B:9806533560c9", "b": "ext-E:E|same_side_lots_cap|cap4_trun | +78 / +52 / +57 / +66 | -59 | +84 | +3449 | +81 / +59 / +63 / +71 | 77.4 | 65% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +35 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "ext-B:1b5942ac8cd6", "b": "ext-E:E|total_lots_cap|cap4_trunc|se | +78 / +52 / +33 / +69 | -42 | +81 | +3078 | +81 / +58 / +41 / +73 | 76.4 | 70% | FIRST-ORDER SCREEN ONLY | +39 / +38.9 / +375 | 0.02 | 0.69 | +35 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |

## Family K - P7

P7: 391 cells (391 down-only); best by equal-mean L6M maxDD cut: K6 ext-B on P7 only {"cell": "9806533560c9", "orig": "ext ext-B {\"cell\": \"980 cuts L6M maxDD +36% at equal lots (d mean +4129 $/wk) and +46% at equal mean (PRE +40%, X' +64%); placebo p 0.02, family p 0.80, WF +34 -> LEAD [EXACT partial].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K6 ext-B on P7 only [ROLL-EXCL] | {"cell": "9806533560c9", "orig": "ext ext-B {\"cell\": \"9806533560c9\ | +36 / +37 / +29 / +57 | -57 | +52 | +4129 | +46 / +47 / +40 / +64 | 33.1 | 13% | -28 /  /  /  (+185; table (IJK driver) mode) | +32 / +4.5 / +5 | 0.02 | 0.80 | +34 |  | FIRST-ORDER SCREEN ONLY | LEAD [EXACT partial] |
| K6 ext-B on P7 only [ROLL-EXCL] | {"cell": "faebfc320da8", "orig": "ext ext-B {\"cell\": \"faebfc320da8\ | +35 / +30 / +34 / +61 | -47 | +55 | +2285 | +41 / +36 / +40 / +65 | 30.3 | 15% | FIRST-ORDER SCREEN ONLY | +41 / -6.4 / +2 | 0.02 | 0.95 | +34 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only [ROLL-EXCL] | {"cell": "e8116ed4fa4e", "orig": "ext ext-A {\"cell\": \"e8116ed4fa4e\ | +42 / +2 / +27 / +9 | -8 | +46 | -1527 | +38 / -4 / +22 / +2 | 25.9 | 16% | FIRST-ORDER SCREEN ONLY | -16 / +57.7 / +382 | 0.02 | 0.07 | +34 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only [ROLL-EXCL] | {"cell": "7850ad5e165a", "orig": "ext ext-A {\"cell\": \"7850ad5e165a\ | +42 / +2 / +27 / +9 | -8 | +46 | -1527 | +38 / -4 / +22 / +2 | 25.9 | 16% | FIRST-ORDER SCREEN ONLY | -16 / +57.7 / +382 | 0.02 | 0.07 | +34 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only [ROLL-EXCL] | {"cell": "a64be38872f3", "orig": "ext ext-A {\"cell\": \"a64be38872f3\ | +35 / +16 / +27 / +10 | -31 | +42 | +778 | +38 / +19 / +29 / +13 | 24.5 | 12% | FIRST-ORDER SCREEN ONLY | +12 / +23.4 / +124 | 0.02 | 0.05 | +34 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only [ROLL-EXCL] | {"cell": "07a9eb57e868", "orig": "ext ext-A {\"cell\": \"07a9eb57e868\ | +33 / +20 / +43 / +20 | -2 | +48 | +848 | +35 / +23 / +45 / +23 | 24.8 | 15% | FIRST-ORDER SCREEN ONLY | -13 / +46.1 / +364 | 0.02 | 0.71 | +34 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only [ROLL-EXCL] | {"cell": "4631cbe633a4", "orig": "ext ext-A {\"cell\": \"4631cbe633a4\ | +33 / +20 / +43 / +20 | -2 | +48 | +848 | +35 / +23 / +45 / +23 | 24.8 | 15% | FIRST-ORDER SCREEN ONLY | -13 / +46.1 / +364 | 0.02 | 0.71 | +34 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-B on P7 only [ROLL-EXCL] | {"cell": "c1d4e97d2d2c", "orig": "ext ext-B {\"cell\": \"c1d4e97d2d2c\ | +21 / +37 / +29 / -7 | -76 | +53 | +4370 | +34 / +47 / +41 / +11 | 25.8 | 11% | FIRST-ORDER SCREEN ONLY | +35 / -13.3 / -5 | 0.02 | 0.80 | +34 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-G on P7 only [ROLL-EXCL] | {"cell": "f98bd2daa16b", "orig": "ext ext-G {\"cell\": \"f98bd2daa16b\ | +36 / +8 / +14 / +0 | -17 | +44 | -1115 | +33 / +3 / +10 / -5 | 24.6 | 4% | FIRST-ORDER SCREEN ONLY | +24 / +11.8 / +31 | 0.02 | 0.46 | +34 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K1 P7 lot cap by session [ROLL-EXCL] | {"asia": 5, "london": 3, "nyam": 3} | +27 / +12 / +34 / +18 | -39 | +36 | +1266 | +31 / +17 / +38 / +23 | 21.5 | 14% | -3 /  /  /  (+2766; table (IJK driver) mode) | +15 / +11.9 / +38 | 0.01 | 0.02 | +39 | -21736 | FIRST-ORDER SCREEN ONLY | LEAD [EXACT partial] |

## Cross-family finalists (CANDIDATE / LEAD+ labels, top 25 by equal-mean L6M cut)

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| J pair min [ROLL-EXCL] | {"a": "I:83d7d23f2f5d", "b": "ext-VT:b47d9923a960"} | +89 / -7 / +58 / +78 | +14 | +92 | -4351 | +86 / -33 / +48 / +72 | 109.6 | 84% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "K:5ac97ef10c49", "b": "ext-VT:b47d9923a960"} | +80 / +41 / +70 / +76 | +27 | +85 | -1781 | +78 / +36 / +68 / +74 | 65.5 | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.82 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.82) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "K:b8c7a11b7c62", "b": "ext-B:1b5942ac8cd6"} | +73 / +63 / +60 / +69 | +70 | +78 | +4279 | +78 / +69 / +66 / +74 | 65.4 | 63% | FIRST-ORDER SCREEN ONLY | +33 / +40.3 / +542 | 0.02 | 0.67 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.67) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-L:6fa81ee4110a", "b": "ext-SZQ:AB_751631_0"} | +80 / +53 / +61 / +27 | +93 | +88 | -3429 | +78 / +46 / +56 / +16 | 78.0 | 70% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-L:6fa81ee4110a", "b": "ext-VT:a5a7135ca8ed"} | +77 / +11 / +55 / +10 | +55 | +88 | +125 | +77 / +12 / +55 / +10 | 64.8 | 63% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-B:d852c862a088", "b": "ext-K:4717a767cf4d"} | +74 / +42 / +67 / +59 | +45 | +79 | +3093 | +77 / +49 / +71 / +64 | 64.1 | 60% | FIRST-ORDER SCREEN ONLY | +50 / +23.9 / +142 | 0.02 | 0.64 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.64) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "K:5ac97ef10c49", "b": "ext-B:1b5942ac8cd6"} | +78 / +59 / +65 / +68 | +34 | +86 | -963 | +77 / +57 / +63 / +66 | 62.8 | 66% | FIRST-ORDER SCREEN ONLY | +16 / +61.6 / +1091 | 0.02 | 0.67 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.67) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-B:1b5942ac8cd6", "b": "ext-D:D|consec_loss|stack_k2_f0.00|s | +75 / +9 / +38 / +61 | +15 | +75 | +1942 | +77 / +16 / +43 / +64 | 62.6 | 65% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.82 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.82) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-E:E|total_lots_cap|cap4_trunc|sess_london", "b": "ext-VT:a5 | +73 / -8 / +69 / +62 | +60 | +77 | +3856 | +77 / +8 / +74 / +67 | 62.4 | 60% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.97 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "Jtree:0d8433a1c4cd", "b": "ext-VT:b47d9923a960"} | +77 / +49 / +64 / +79 | +41 | +85 | -48 | +77 / +48 / +64 / +79 | 62.1 | 69% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.05 | 0.97 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-F:e42de98e2549", "b": "ext-VT:a5a7135ca8ed"} | +80 / +34 / +48 / +60 | +40 | +81 | -3604 | +77 / +24 / +41 / +54 | 77.5 | 55% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-D:D|consec_loss|stack_k2_f0.00|sess_london", "b": "ext-VT:b | +75 / +2 / +50 / +63 | +29 | +76 | +1481 | +76 / +8 / +53 / +65 | 61.4 | 66% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.18 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.18) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-K:4717a767cf4d", "b": "ext-VT:b47d9923a960"} | +73 / +42 / +66 / +66 | +68 | +78 | +2960 | +76 / +49 / +70 / +70 | 61.3 | 63% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.51 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.51) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-K:6fa18a1ca7ac", "b": "ext-VT:b47d9923a960"} | +73 / +42 / +69 / +68 | +60 | +76 | +3040 | +76 / +49 / +73 / +72 | 61.3 | 63% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.44 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.44) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "I:286a27d471d4", "b": "ext-VT:b47d9923a960"} | +78 / +54 / +71 / +73 | +9 | +83 | -1348 | +76 / +51 / +70 / +72 | 61.3 | 72% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair product [owner, not roll-excl] | {"a": "Jtree:9be3e678872f", "b": "ext-VT:a5a7135ca8ed"} | +76 / +19 / +51 / +51 | +31 | +79 | +622 | +76 / +21 / +52 / +52 | 61.2 | 55% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.97 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-E:E|same_side_lots_cap|cap4_trunc|sess_london", "b": "ext-S | +71 / +53 / +63 / +67 | +72 | +77 | +4649 | +76 / +60 / +69 / +72 | 64.0 | 64% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.59 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.59) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-K:d16e6b6b3c26", "b": "ext-VT:b47d9923a960"} | +73 / +42 / +70 / +68 | +58 | +76 | +2912 | +76 / +49 / +73 / +71 | 61.0 | 63% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.41 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.41) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-B:9806533560c9", "b": "ext-L:6fa81ee4110a"} | +76 / +25 / +46 / +46 | +45 | +89 | +262 | +76 / +26 / +46 / +47 | 61.1 | 71% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-A:27003ddb767c", "b": "ext-B:9806533560c9"} | +73 / -15 / +65 / +39 | +54 | +78 | +2191 | +76 / -5 / +68 / +44 | 59.9 | 72% | FIRST-ORDER SCREEN ONLY | +64 / +9.5 / -10 | 0.02 | 0.97 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "Jtree:9be3e678872f", "b": "ext-VT:a5a7135ca8ed"} | +73 / +7 / +46 / +47 | +47 | +77 | +2046 | +75 / +14 / +50 / +51 | 59.3 | 55% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.97 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "Jtree:9be3e678872f", "b": "ext-B:9806533560c9"} | +74 / +41 / +51 / +75 | +40 | +81 | +1110 | +75 / +44 / +54 / +76 | 59.2 | 64% | FIRST-ORDER SCREEN ONLY | +39 / +35.1 / +323 | 0.02 | 1.00 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-B:9806533560c9", "b": "ext-SZQ:AB_1b5942_0"} | +71 / +56 / +42 / +68 | +62 | +82 | +4291 | +75 / +63 / +52 / +73 | 59.1 | 62% | FIRST-ORDER SCREEN ONLY | +30 / +40.4 / +552 | 0.02 | 0.72 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.72) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-B:9806533560c9", "b": "ext-D:D|consec_loss|stack_k2_f0.00|s | +76 / -22 / +55 / +44 | +93 | +85 | -628 | +75 / -25 / +54 / +42 | 73.5 | 64% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.97 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-B:1b5942ac8cd6", "b": "ext-K:6fa18a1ca7ac"} | +70 / +55 / +63 / +68 | +63 | +76 | +4288 | +75 / +62 / +69 / +73 | 58.2 | 61% | FIRST-ORDER SCREEN ONLY | +32 / +38.2 / +526 | 0.02 | 0.67 | +35 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.67) [FIRST-ORDER SCREEN ONLY] |
