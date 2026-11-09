# DS3_SIZER_EXHAUST - T-SIZER-EXHAUST ranked tables (SZ-CORE, 2026-11-09 19:19Z)

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
| F Time / session | 118 | 118 | 31 | 4 | 0 | 0 |
| G Signal quality | 1214 | 890 | 374 | 32 | 0 | 0 |
| H Regime | 224 | 149 | 65 | 6 | 0 | 0 |
| I Book-level recent performance | 188 | 186 | 71 | 0 | 8 | 0 |
| J Combinations | 1179 | 1179 | 412 | 0 | 757 | 0 |
| K P7 | 408 | 408 | 180 | 0 | 122 | 0 |

> **TESTING-DEFECT BOX.** Cells whose new-base d mean equals the old-base page to the dollar: 0.

**USER ADDENDUM 1 (16:30Z) status:** first-order is a SCREEN ONLY; the sizing verdict needs EXACT engine runs for every family top-5 and every reference row on L6M, PRE, X', HOLD. Exact-confirmed cells on this page: 9 of 23877 with any exact window, 0 with all of L6M/PRE/X' (the label carries [EXACT] / [EXACT partial] / [FIRST-ORDER SCREEN ONLY]). Exact queue: autopilot SZ-CORE queue, reference rows first, then family top-5; windows L6M, PRE, X', HOLD.

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
| sizer off (x1) | -28.2 / -2511 | -6.4 / -970 | +28.3 / +3359 | +0.5 / +2617 | 43 |
| old ladder L (x0.5/x1.5) | -76.1 / -504 | -41.5 / -103 | -17.0 / +3887 | pending | 42 |
| B (x1/x1.5, up only) | -142.6 / +2723 | -94.8 / +2856 | -15.2 / +7200 | +3.9 / +4649 | 43 |
| ZL-1 vol-target (factor built on unadjusted bars; 97 trades differ after adjustment; X_VTA pending) | +28.3 / +10 | +29.1 / -684 | -6.3 / -1877 | pending | 41 |
| MV-london override | -1.2 / -107 | +6.8 / +28 | pending | pending | 26 |

## Vol-target family (SZ-VT, autopilot/DS3_SIZER_VOLTARGET.md, user top priority; exact engine from the start; first 70 lines, incl. executability rows: scale factor s, max single-trade $ risk, max lots on at once)

# DS3_SIZER_VOLTARGET - T-SIZER-EXHAUST Addendum 2 (SZ-VT), refreshed 2026-11-09 17:52Z
**Post-hoc, Shadow only, no PASS claims. PRE-PROOF (entry match < .85). Numbers below are FIRST-ORDER SCREEN unless a row says [EXACT]. Prereg: autopilot/SZ_VT_PREREG.md (sha in DECISIONS.md). ROLL-EXCL (the 33 base trades alive across a contract roll carry weight 0 in every first-order number; key book7 x signal second). ALL EXACT ROWS ARE PENDING/VOID until re-run with the fixed sz_exact driver (key bug found 17:00Z).**

**VERDICT (plain, provisional, first-order; ALL exact rows pending): every D7 layer stays ON, so the candidates are scale rules (never to zero) on top of the live ER sizer, and the skip-to-zero vol rules are reference/UP rows only. Skip rules that win in-sample (+80/+57/+76 for the best cell) fail the equal-mean walk-forward and lose $40-80k of the $104.8k high-vol live week, and the in-sample winner on the S1b base ranks #826 (of ~30k) on the old base, so in-sample picks do not carry. Pre-registered 5-test stability (WF 26/52 wk, split-half A/B, time split; cut at the realised equal mean): SCALE single measure (worst test +29.4 %), per-book/session scope (worst test +22.0 %), SCALE P7+K7 scope (worst test +7.4 %), composite pooled (worst test +6.7 %), composite graded/half/cont (worst test +6.7 %), half (lo=.5) steps (worst test +6.6 %), SCALE consensus measure (worst test +5.9 %), SCALE pooled (worst test +5.3 %), SCALE rules (never zero) all (worst test +4.4 %) are positive in all 5, while the skip, graded-to-zero, z-score, special and interactions families flip sign; the single-measure scale rows are optimistic (measure list ranked on the whole sample) and the consensus-measure rows (no measure picked) are the clean test; nothing is confirmed on the exact engine, so if the exact rows (section 7) do not hold, keep the live Q1-A sizer. Scale rules cost about -$34k to -$48k of the live week at p=2 floor .25 (that week was 69 % above 1.25x vol).**

## 0. What was built (B1-B5)
- Features at the signal second (causal, NQ 1-min state bars closed before the signal; code/th_sz_vt/vt_feat.py, 1,859 columns): 53 vol measures (rv1 w10/30/60/120/240, rv5, GK / Parkinson on 1/5/15-min, ATR b1/5/15 n5/14/30/50, EWMA lam .90/.94/.97/.99 on 1/5-min) x sigma_ref windows 5/10/20/40/60 trading days x reference type {all minutes, same half-hour slot, and for 8 core measures all/slot with FOMC/CPI/NFP days excluded from the norm} x {ratio now/median, quantile of the trailing distribution, log z-score}; core dynamics (minutes above 1.25x = spiked vs sustained, ratio now / 30 min ago = vol-of-vol, std of the ratio), direction-aware move of the last 5/15/30/60 min in 1-min sigma, event-day flag; range ratios (overnight/pre/first-30/so-far) and VIX from the AB store.
- Cells scored: **51,408 pooled grid cells** (shapes: continuous (ref/now)^p p .5-2 floor 0/.25/.5, quantile step q .6-.95 to x0.5 or 0, graded 3-step {1,.5,0} at quantile pairs, multiple step 1.1-2.0, z step; with and without the ER sizer) + 1,824 B2 special rules (first signal of the episode per book / stack, spiked vs sustained, direction-aware, rising vs falling vol, event-day) + 850 per-book/session scope cells + 744 B4 interaction cells (stack exposure cap 8-20 lots, post-loss cooldown in high vol) + 864 stack and per-book P&L target-vol cells (trailing 10/15/20 d P&L vol, target = q x expanding median, p .5-2, floor 0-.5). Down-only family on top of Q1-A (onQ1A): 30,031 cells; "alone" (ER sizer removed, M can exceed 1 where ER<.3) are reported in the ledger as UP-labelled, never promoted.
- NOT table-expressible, therefore NOT scored (stated, not hidden): delay-and-recheck entries (changes entry price, needs an engine subclass), the equal-$-risk stop form (wider stop, fewer lots: stop is an engine input), vol-scaled +-R day caps, and vol-governed state-cut arm/persistence (engine rules). They need `state_sizer_b` subclasses (cde_exact.py pattern); listed in section 8 as v1.6 work. Tick count / contracts per second / spread / depth proxies and VXN: the per-second feature store is path-aligned to trades, not to arbitrary signal seconds, VXN is not owned, and VIX stops 2026-10-16; the liquidity proxies are NOT in this page (stated gap). NQ 1-min data runs to 2026-11-05 so all NQ measures cover the whole live week; ES/RTY cross-instrument vol uses 1-s closes that end 2026-10-16 (unavailable after: multiplier 1) and is not part of the screened grid in this version.
- Validation: purged monthly walk-forward of the PICKING procedure per family (26-week training, 7-day embargo, 34 test months 2024-01..2026-10): pick = highest training equal-mean maxDD cut; reported at equal lots, with s fixed from the training window, and at the realised equal OOS mean; time split (pick on weeks <= 2025-06-30, test 2025-07..2026-11); placebo (same lot ratios permuted within book x session, B=200) and a family null over all 30,031 down-only cells (max-stat over the same permutations); held-out live week (frozen file, first-order); EXACT engine for the top cells (section 6).

## 1. Best cell per family (down-only on Q1-A, first-order). Cut = stack maxDD cut vs Q1-A; EQ = at equal L6M mean (lots x s)
| family | cell (feature shape params scope) | cut L6M/PRE/X' (equal lots) | EQ cut L6M/PRE/X' | s | d mean $/wk L6M | worst-20 L6M cell/ref ($k) | Ulcer L6M cell/ref ($k) | skip share | p own / p fam(VT set, all stages) | WF family OOS cut: equal lots / realised equal mean | live wk d$ | stage |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| interactions (cap/cooldown) | q_park15_w12_all10 step [0.6, 0] ["pool"] | +80/+57/+76 | +81/+60/+78 | 0.93 | +1758 | +277/+165 | 4.5 | 0.53 | 0.005 / 0.005 | 44.8 / 14.8 | - | S1 first-order |
| quantile-adaptive (q_*) | q_gk1_w10_all5 step [0.6, 0] ["pool"] | +65/+6/+61 | +71/+22/+68 | 0.83 | +4569 | +233/+165 | 9.1 | 0.57 | 0.005 / 0.045 | 26.6 / -6.0 | -53950 | S1 first-order |
| ratio step/cont (r_*) | r_ewma5_l90_all40 step [1.1, 0] ["pool"] | +64/+53/+65 | +67/+57/+68 | 0.91 | +2182 | +203/+165 | 10.9 | 0.62 | 0.005 / 0.055 | 43.6 / 6.3 | -91430 | S1 first-order |
| per-book/session scope | q_park15_w12_all10 step [0.6, 0] ["book", "P7", "K7"] | +67/+48/+63 | +69/+52/+66 | 0.93 | +1688 | +238/+165 | 10.5 | 0.35 | 0.005 / 0.085 | 49.0 / 41.0 | -65885 | S1 first-order |
| graded 3-step | q_park1_w10_all10 g3 [0.6, 0.8] ["pool"] | +54/+58/+66 | +61/+64/+72 | 0.85 | +4002 | +247/+165 | 11.6 | 0.37 | 0.005 / 0.119 | 25.8 / 17.0 | -51248 | S1 first-order |
| special (first/dur/dir/vov/evt) | q_atr5_n14_all20 special [] ["pool"] | +33/+54/+56 | +43/+61/+63 | 0.84 | +4422 | +258/+165 | 15.3 | 0.43 | 0.005 / 0.184 | 17.7 / 6.8 | -70800 | S1 first-order |
| session-slot ref | r_gk15_w6_slot10 step [1.1, 0] ["pool"] | +60/+61/+16 | +61/+62/+18 | 0.97 | +675 | +186/+165 | 11.0 | 0.50 | 0.005 / 0.219 | 26.6 / -23.0 | -81535 | S1 first-order |
| continuous (ref/now)^p | r_park1_w10_all40 cont [2, 0] ["pool"] | +33/+55/+60 | +38/+58/+63 | 0.92 | +2109 | +221/+165 | 16.8 | 0.00 | 0.005 / 0.313 | 31.4 / 17.1 | -41810 | S1 first-order |
| composite pooled scope | q_COMP_all10 g3 [0.5, 0.8] ["pool"] | +50/+53/+67 | +54/+58/+70 | 0.91 | +2146 | +239/+165 | 16.1 | 0.28 | 0.005 / 0.338 | 38.6 / 17.9 | -63368 | S1 first-order |
| SCALE rules (never zero) all | r_park1_w10_all60 cont [2, 0.25] ["pool"] | +27/+52/+60 | +32/+55/+62 | 0.93 | +1642 | +214/+165 | 17.9 | 0.00 | 0.005 / 0.458 | 16.9 / 4.4 | -42813 | S1 first-order |
| composite consensus (all stages comp) | q_COMP_all60 step [0.6, 0] ["book", "P7", "K7"] | +19/+46/+66 | +30/+53/+71 | 0.86 | +3510 | +223/+165 | 16.5 | 0.35 | 0.010 / 0.547 | 38.4 / 10.1 | -92905 | S1 first-order |
| z-score | z_park1_w10_slot20 step [1.0, 0] ["pool"] | +13/+52/+52 | +14/+53/+53 | 0.98 | +482 | +123/+165 | 22.6 | 0.31 | 0.010 / 0.567 | 35.8 / 17.7 | -75135 | S1 first-order |
| half (lo=.5) steps | r_gk1_w10_all60 step [1.25, 0.5] ["pool"] | +18/+46/+52 | +26/+52/+57 | 0.90 | +2420 | +231/+165 | 21.4 | 0.00 | 0.005 / 0.612 | 25.0 / 20.0 | -26638 | S1 first-order |
| stack/book P&L target-vol | tvol_ALL tvol [20, 0.8, 2, 0.5, "ALL"] ["pool"] | +47/+43/+2 | +24/+18/-41 | 1.44 | -6672 | +129/+165 | 17.7 | 0.00 | 0.015 / 1.000 | 46.7 / 33.5 | -37680 | S1 first-order |

Reading the columns: "skip share" is the share of signals taken to zero lots; a cell that skips 50-60 % of signals and still shows a higher mean at equal lots is selecting the quiet-tape trades, which is the part that fails out of sample (section 2). Worst-20 = sum of the 20 worst weeks (higher = better). The placebo draws permute the same lot ratios within book x session, so p own tests timing, not size.

## 1b. Stability of the verdict per family (pre-registered 5 tests: WF 26 wk, WF 52 wk, split-half A (train first half), split-half B (train second half), time split (train <= 2025-06-30); metric = OOS maxDD cut % at the REALISED test equal mean; NaN = family not in that WF table)
| family | cells | WF26 | WF52 | split A | split B | time split | positive of 5 | worst | stable? |
|---|---|---|---|---|---|---|---|---|---|
| SCALE single measure | 904 | 34.6 | 34.4 | 37.9 | 31.3 | 29.4 | 5 | 29.4 | STABLE (5/5 > 0) |
| per-book/session scope | 850 | 41.0 | 34.5 | 43.1 | 34.4 | 22.0 | 5 | 22.0 | STABLE (5/5 > 0) |
| SCALE P7+K7 scope | 446 | 9.5 | 14.3 | 7.4 | 37.9 | 26.9 | 5 | 7.4 | STABLE (5/5 > 0) |
| composite pooled | 388 | 17.9 | 34.8 | 36.1 | 34.5 | 6.7 | 5 | 6.7 | STABLE (5/5 > 0) |
| composite graded/half/cont | 5220 | 34.9 | 26.3 | 36.1 | 34.5 | 6.7 | 5 | 6.7 | STABLE (5/5 > 0) |
| half (lo=.5) steps | 9806 | 20.0 | 15.8 | 8.4 | 28.4 | 6.6 | 5 | 6.6 | STABLE (5/5 > 0) |
| SCALE consensus measure | 880 | 5.9 | 10.9 | 14.9 | 25.9 | 23.2 | 5 | 5.9 | STABLE (5/5 > 0) |
| SCALE pooled | 446 | 5.3 | 11.7 | 14.9 | 31.3 | 30.6 | 5 | 5.3 | STABLE (5/5 > 0) |
| SCALE rules (never zero) all | 1784 | 4.4 | 13.0 | 14.9 | 31.3 | 29.4 | 5 | 4.4 | STABLE (5/5 > 0) |
| continuous (ref/now)^p | 10272 | 17.1 | 22.2 | 4.1 | 40.1 | -2.4 | 4 | -2.4 | mostly |
| stack/book P&L target-vol | 864 | 33.5 | 32.4 | 5.6 | -25.7 | 5.8 | 4 | -25.7 | mostly |
| interactions | 744 | 14.8 | 5.5 | 43.8 | -289.9 | 15.3 | 4 | -289.9 | mostly |
| skip steps (lo=0), pooled grid | 7462 | 4.6 | -0.6 | -2.9 | 5.7 | 5.2 | 3 | -2.9 | unstable |
| special rules | 1824 | 6.8 | 7.9 | 24.8 | -59.3 | -40.9 | 3 | -59.3 | unstable |
| z-score steps | 3660 | - | - | -2.9 | 20.3 | 0.9 | 2 | -2.9 | unstable |
| graded 3-step | 5055 | 17.0 | -2.4 | -0.3 | -13.4 | -77.0 | 1 | -77.0 | unstable |

Plainly: SCALE single measure (worst test +29.4 %), per-book/session scope (worst test +22.0 %), SCALE P7+K7 scope (worst test +7.4 %), composite pooled (worst test +6.7 %), composite graded/half/cont (worst test +6.7 %), half (lo=.5) steps (worst test +6.6 %), SCALE consensus measure (worst test +5.9 %), SCALE pooled (worst test +5.3 %), SCALE rules (never zero) all (worst test +4.4 %) are the families with a stable (5/5) verdict; the skip, graded-to-zero and z-score families flip sign between halves. Caveat: the 20 single measures in "SCALE single measure" were ranked on the whole sample, so that row is optimistic; the consensus row (no measure picked) is the clean test.

## 1c. SCALE rules (never zero, on top of the ER sizer) - best 10 by tolerant equal-mean score; p own / p fam (VT set); live-week d$ (first-order)
| cell | scope | cut L6M/PRE/X' | EQ cut L6M/PRE/X' | s | d mean L6M $/wk | p own / p fam | live wk d$ | max lots at once (Q1-A 20) |
|---|---|---|---|---|---|---|---|---|
| r_park1_w10_all60 cont [2, 0.25] | [pool] | +27/+52/+60 | +32/+55/+62 | 0.93 | +1642 | 0.005 / 0.458 | -42813 | 17.8 |
| r_gk1_w10_all40 cont [2, 0.25] | [pool] | +29/+51/+53 | +35/+54/+57 | 0.92 | +1902 | 0.005 / 0.493 | -40756 | 17.6 |
| q_gk1_w10_all60 step [0.6, 0.5] | [pool] | +29/+46/+52 | +38/+53/+58 | 0.87 | +3271 | 0.005 / 0.537 | -33836 | 16.6 |
| r_gk1_w10_all60 cont [2, 0.25] | [book, K7, P7, M7, A7, O7] | +14/+50/+47 | +23/+56/+53 | 0.90 | +2697 | 0.005 / 0.552 | -47559 | 17.0 |
| r_atr1_n14_all60 cont [2, 0.25] | [pool] | +20/+48/+55 | +26/+52/+59 | 0.92 | +1907 | 0.005 / 0.607 | -39468 | 17.6 |
| r_park1_w10_all40 cont [2, 0.25] | [pool] | +32/+48/+58 | +37/+52/+62 | 0.92 | +1943 | 0.005 / 0.607 | -40304 | 17.5 |
| r_park15_w6_all60 cont [2, 0.25] | [pool] | +24/+46/+58 | +32/+52/+62 | 0.90 | +2488 | 0.005 / 0.617 | -49711 | 17.2 |
| r_gk1_w10_all60 step [1.1, 0.5] | [pool] | +32/+46/+52 | +39/+51/+57 | 0.90 | +2533 | 0.005 / 0.632 | -33836 | 17.1 |
| r_gk1_w10_all60 cont [2, 0.5] | [pool] | +24/+48/+51 | +30/+51/+55 | 0.93 | +1678 | 0.005 / 0.632 | -33838 | 17.7 |
| r_gk1_w10_all60 cont [2, 0.25] | [book, P7, K7] | +14/+50/+46 | +21/+55/+51 | 0.91 | +2350 | 0.005 / 0.652 | -45243 | 18.2 |

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
| slot48 [ROLL-EXCL] | {"m": 0, "slot": 8} | +12 / -3 / -1 / -11 | -28 |  | +2552 | +21 / +7 / +9 / -0 |  | 3% | FIRST-ORDER SCREEN ONLY | +7 / +5.4 / +19 | 0.28 | 1.00 |  | +3890 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| dow [ROLL-EXCL] | {"dow": 0, "m": 0} | +24 / -98 / +22 / +47 | +42 |  | -1865 | +18 / -115 / +15 / +43 |  | 19% | FIRST-ORDER SCREEN ONLY | +11 / +12.9 / +141 | 0.09 | 1.00 |  | -28440 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| dow [ROLL-EXCL] | {"dow": 2, "m": 0.5} | +15 / +11 / +6 / +25 | +1 |  | +46 | +15 / +11 / +6 / +25 |  | 7% | FIRST-ORDER SCREEN ONLY | +7 / +7.7 / +21 | 0.03 | 1.00 |  | -6193 | S1 | LEAD+ (placebo ok; WF n/a or fail) [FIRST-ORDER SCREEN ONLY] |
| slot48 [owner, not roll-excl] | {"m": 0, "slot": 40} | +12 / -6 / -8 / +14 | +7 |  | +139 | +12 / -5 / -8 / +15 |  | 3% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.06 | 1.00 |  | +3120 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| slot48 [ROLL-EXCL] | {"m": 0, "slot": 10} | +9 / +3 / +5 / +3 | -16 |  | +652 | +12 / +6 / +7 / +6 |  | 2% | FIRST-ORDER SCREEN ONLY | +13 / -3.8 / +4 | 0.29 | 1.00 |  | -8855 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| slot48 [ROLL-EXCL] | {"m": 0, "slot": 22} | +8 / +4 / +5 / +8 | -17 |  | +883 | +11 / +7 / +8 / +11 |  | 5% | FIRST-ORDER SCREEN ONLY | -1 / +8.7 / +160 | 0.30 | 1.00 |  | -10145 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| slot48 [ROLL-EXCL] | {"m": 0, "slot": 15} | +2 / -2 / +9 / +2 | -11 |  | +2463 | +11 / +7 / +17 / +11 |  | 2% | FIRST-ORDER SCREEN ONLY | -18 / +19.9 / +191 | 0.07 | 1.00 |  | +5425 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| slot48 [ROLL-EXCL] | {"m": 0.5, "slot": 15} | +6 / -0 / +3 / +0 | -7 |  | +1116 | +10 / +4 / +7 / +4 |  | 1% | FIRST-ORDER SCREEN ONLY | -6 / +12.0 / +178 | 0.01 | 1.00 |  | +2672 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| slot48 [ROLL-EXCL] | {"m": 0.5, "slot": 8} | +6 / -3 / +2 / -2 | -12 |  | +902 | +9 / +1 / +5 / +2 |  | 1% | FIRST-ORDER SCREEN ONLY | +1 / +5.2 / +86 | 0.17 | 1.00 |  | +1382 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

## Family G - Signal quality

Signal quality: 1214 cells (890 down-only); best by equal-mean L6M maxDD cut: qgate {"feat": "nA40", "m": 0, "q": 0.2, "tail": "low"} cuts L6M maxDD +90% at equal lots (d mean -11882 $/wk) and +78% at equal mean (PRE -14%, X' -127%); placebo p 0.29, family p 1.00, WF n/a -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate [owner, not roll-excl] | {"feat": "nA40", "m": 0, "q": 0.2, "tail": "low"} | +90 / +18 / +50 / +0 | -39 |  | -11882 | +78 / -87 / -14 / -127 |  | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.29 | 1.00 |  | -74295 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA40", "m": 0, "q": 0.1, "tail": "low"} | +90 / +18 / +50 / +0 | -39 |  | -11882 | +78 / -87 / -14 / -127 |  | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.31 | 1.00 |  | -74295 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA40", "m": 0, "q": 0.5, "tail": "low"} | +90 / +18 / +50 / +0 | -39 |  | -11882 | +78 / -87 / -14 / -127 |  | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.20 | 1.00 |  | -74295 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA40", "m": 0, "q": 0.3, "tail": "low"} | +90 / +18 / +50 / +0 | -39 |  | -11882 | +78 / -87 / -14 / -127 |  | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.25 | 1.00 |  | -74295 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA20", "m": 0, "q": 0.3, "tail": "low"} | +90 / +57 / +56 / +0 | -73 |  | -16691 | +56 / -100 / -106 / -366 |  | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.58 | 1.00 |  | -96325 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA20", "m": 0, "q": 0.1, "tail": "low"} | +90 / +57 / +56 / +0 | -73 |  | -16691 | +56 / -100 / -106 / -366 |  | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.63 | 1.00 |  | -96325 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA20", "m": 0, "q": 0.5, "tail": "low"} | +90 / +57 / +56 / +0 | -73 |  | -16691 | +56 / -100 / -106 / -366 |  | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.66 | 1.00 |  | -96325 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [owner, not roll-excl] | {"feat": "nA20", "m": 0, "q": 0.2, "tail": "low"} | +90 / +57 / +56 / +0 | -73 |  | -16691 | +56 / -100 / -106 / -366 |  | 79% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.47 | 1.00 |  | -96325 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate_x_er [owner, not roll-excl] | {"er": "erhigh", "feat": "ema_x_sg", "m": 0, "q": 0.5, "tail": "high"} | +50 / +21 / +18 / +0 | -37 |  | -4452 | +36 / +0 / -3 / -27 |  | 25% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.42 | 1.00 |  | -42685 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| qgate [ROLL-EXCL] | {"feat": "twap_slope_sg", "m": 0, "q": 0.5, "tail": "low"} | +43 / -61 / +32 / +0 | +27 |  | -2502 | +36 / -81 / +23 / -13 |  | 45% | FIRST-ORDER SCREEN ONLY | -18 / +61.3 / +965 | 0.30 | 1.00 |  | -28565 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate_x_er [owner, not roll-excl] | {"er": "erlow", "feat": "f_ema20_rel", "m": 1.5, "q": 0.5, "tail": "lo | +11 / -8 / +4 / +0 | +69 |  | +5694 | +28 / +13 / +22 / +19 |  | 15% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 1.00 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| qgate_x_er [owner, not roll-excl] | {"er": "erlow", "feat": "f_tot_rel_base", "m": 1.5, "q": 0.5, "tail":  | +7 / -6 / -1 / +0 | +52 |  | +6320 | +25 / +15 / +19 / +20 |  | 21% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| qgate_x_er [owner, not roll-excl] | {"er": "erlow", "feat": "f_ahead_rel_base", "m": 1.5, "q": 0.5, "tail" | +8 / -13 / +10 / +0 | +57 |  | +5214 | +24 / +7 / +26 / +18 |  | 23% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 1.00 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family H - Regime

Regime: 224 cells (149 down-only); best by equal-mean L6M maxDD cut: regime {"cond": "adx5_ge20", "m": 0.5} cuts L6M maxDD +41% at equal lots (d mean -2574 $/wk) and +33% at equal mean (PRE +29%, X' +35%); placebo p 0.01, family p 1.00, WF n/a -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime [ROLL-EXCL] | {"cond": "adx5_ge20", "m": 0.5} | +41 / +20 / +38 / +43 | -9 |  | -2574 | +33 / +9 / +29 / +35 |  | 30% | FIRST-ORDER SCREEN ONLY | +29 / +12.3 / +18 | 0.01 | 1.00 |  | -33303 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [owner, not roll-excl] | {"cond": "on_ratio_ge0.8", "m": 0} | +41 / +16 / +39 / -74 | +2 |  | -4609 | +29 / -1 / +27 / -108 |  | 35% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.69 | 1.00 |  | -62715 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [owner, not roll-excl] | {"cond": "gap_with_ge0.25", "m": 0.5} | +35 / +16 / +16 / +6 | -26 |  | -3353 | +24 / +1 / +2 / -10 |  | 16% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.50 | 1.00 |  | -6578 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [owner, not roll-excl] | {"cond": "prior_range_day", "m": 0} | +39 / +1 / +9 / -89 | -5 |  | -5768 | +23 / -25 / -16 / -138 |  | 29% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.50 | 1.00 |  | -59710 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [ROLL-EXCL] | {"cond": "on_ratio_ge0.8", "m": 0.5} | +23 / +14 / +31 / +1 | -19 |  | -715 | +21 / +12 / +29 / -2 |  | 11% | FIRST-ORDER SCREEN ONLY | +16 / +7.8 / +18 | 0.05 | 1.00 |  | -17583 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [ROLL-EXCL] | {"cond": "od_with_ge0.05", "m": 0} | +21 / +17 / -4 / +36 | -19 |  | -17 | +21 / +17 / -4 / +36 |  | 17% | FIRST-ORDER SCREEN ONLY | -9 / +30.0 / +265 | 0.58 | 1.00 |  | -515 | S1 | no [FIRST-ORDER SCREEN ONLY] |
| regime [ROLL-EXCL] | {"cond": "on_ratio_ge1.0", "m": 0.5} | +21 / +4 / +15 / +4 | -15 |  | -652 | +19 / +1 / +13 / +1 |  | 7% | FIRST-ORDER SCREEN ONLY | +16 / +5.4 / +13 | 0.12 | 1.00 |  | -18285 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [owner, not roll-excl] | {"cond": "od_against_ge0.05", "m": 0} | +9 / +6 / +13 / -27 | +28 |  | +2989 | +19 / +16 / +22 / -13 |  | 9% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.31 | 1.00 |  | -2340 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [ROLL-EXCL] | {"cond": "ib_ext_with_ge0.25", "m": 0} | +15 / -2 / +4 / -1 | -24 |  | +910 | +18 / +2 / +8 / +3 |  | 6% | FIRST-ORDER SCREEN ONLY | +6 / +8.8 / +79 | 0.25 | 1.00 |  | -11905 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |
| regime [ROLL-EXCL] | {"cond": "od_with_ge0.10", "m": 0} | +21 / +17 / +3 / +21 | -3 |  | -1073 | +17 / +13 / -2 / +17 |  | 15% | FIRST-ORDER SCREEN ONLY | -10 / +30.4 / +258 | 0.81 | 1.00 |  | -515 | S1 | LEAD [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime_UP [owner, not roll-excl] | {"cond": "twap_slope_with_ge0.25", "m": 1.5} | -2 / -31 / -13 / -41 | +73 |  | +8681 | +26 / +5 / +18 / -2 |  | 23% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.26 | 1.00 |  | +34999 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| regime_UP [owner, not roll-excl] | {"cond": "both_agree_15", "m": 1.5} | -26 / -43 / -50 / -44 | +120 |  | +15441 | +25 / +15 / +11 / +15 |  | 74% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |
| regime_UP [owner, not roll-excl] | {"cond": "both_agree_60", "m": 1.5} | -25 / -39 / -39 / -7 | +107 |  | +13360 | +24 / +15 / +14 / +34 |  | 76% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 1.00 |  | +0 | S1 | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family I - Book-level recent performance

Book-level recent performance: 188 cells (186 down-only); best by equal-mean L6M maxDD cut: I5 stack rolling Calmar {"D": 20, "mult": 0.0, "x": 3.0} cuts L6M maxDD +68% at equal lots (d mean -8191 $/wk) and +49% at equal mean (PRE +26%, X' +53%); placebo p 0.05, family p 1.00, WF +41 -> CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| I5 stack rolling Calmar [ROLL-EXCL] | {"D": 20, "mult": 0.0, "x": 3.0} | +68 / +24 / +55 / +71 | +102 | +52 | -8191 | +49 / -23 / +26 / +53 | 26.9 | 72% | FIRST-ORDER SCREEN ONLY | -14 / +82.6 / +169 | 0.05 | 1.00 | +41 | -104810 | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| I3 book rolling Calmar [ROLL-EXCL] | {"D": 10, "mult": 0.0, "x": 1.0} | +39 / +6 / +44 / +63 | +19 | +32 | -2479 | +31 / -7 / +36 / +58 | 18.0 | 61% | FIRST-ORDER SCREEN ONLY | +24 / +15.0 / +2 | 0.08 | 1.00 | +41 | -105580 | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| I5 stack rolling Calmar [ROLL-EXCL] | {"D": 10, "mult": 0.0, "x": 3.0} | +57 / +65 / +55 / +83 | +127 | +59 | -8954 | +25 / +40 / +23 / +70 | 18.4 | 73% | FIRST-ORDER SCREEN ONLY | +4 / +52.4 / +144 | 0.05 | 1.00 | +41 | -104810 | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| I5 stack rolling Calmar [ROLL-EXCL] | {"D": 20, "mult": 0.5, "x": 3.0} | +34 / +47 / +41 / +49 | +25 | +41 | -4095 | +19 / +35 / +27 / +37 | 19.6 | 28% | +8 /  /  /  (-1488; table (IJK driver) mode) | -13 / +47.6 / +133 | 0.07 | 0.86 | +41 | -37680 | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.86) [EXACT partial] |
| I3 book rolling Calmar [ROLL-EXCL] | {"D": 10, "mult": 0.5, "x": 1.0} | +22 / +32 / +47 / +47 | -1 | +24 | -1239 | +17 / +27 / +43 / +43 | 17.8 | 23% | +23 /  /  /  (-1466; table (IJK driver) mode) | +8 / +14.1 / +7 | 0.10 | 0.98 | +41 | -38365 | FIRST-ORDER SCREEN ONLY | LEAD [EXACT partial] |
| I3 book rolling Calmar [ROLL-EXCL] | {"D": 10, "mult": 0.5, "x": 2.0} | +34 / +47 / +47 / +51 | +34 | +31 | -4857 | +15 / +32 / +32 / +36 | 23.4 | 28% | +11 /  /  /  (-4702; table (IJK driver) mode) | -0 / +34.5 / +100 | 0.13 | 0.96 | +41 | -38365 | FIRST-ORDER SCREEN ONLY | LEAD [EXACT partial] |
| I3 book rolling Calmar [ROLL-EXCL] | {"D": 10, "mult": 0.0, "x": 0.5} | +24 / -18 / +36 / +9 | +43 | +22 | -2731 | +14 / -34 / +27 / -3 | 17.4 | 51% | FIRST-ORDER SCREEN ONLY | +11 / +12.5 / +3 | 0.14 | 1.00 | +41 | -102520 | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| I5 stack rolling Calmar [ROLL-EXCL] | {"D": 10, "mult": 0.5, "x": 2.0} | +28 / +42 / +42 / +40 | +49 | +25 | -3644 | +14 / +31 / +30 / +27 | 18.6 | 25% | FIRST-ORDER SCREEN ONLY | -15 / +43.0 / +115 | 0.08 | 0.96 | +41 | -37680 | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.96) [FIRST-ORDER SCREEN ONLY] |
| I4 stack trailing-D-days $ [ROLL-EXCL] | {"D": 10, "mult": 0.5, "thr_usd": 10000} | +18 / +30 / +26 / -40 | +8 | +10 | -1564 | +13 / +26 / +21 / -48 | 20.9 | 9% | FIRST-ORDER SCREEN ONLY | +5 / +12.5 / +7 | 0.10 | 0.92 | +41 | -25260 | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| I4 stack trailing-D-days $ [ROLL-EXCL] | {"D": 10, "mult": 0.0, "thr_usd": 20000} | +21 / +7 / +5 / -65 | +22 | +8 | -2813 | +12 / -4 / -6 / -85 | 19.8 | 18% | FIRST-ORDER SCREEN ONLY | +17 / +4.6 / -7 | 0.15 | 0.99 | +41 | -62800 | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| I6 up-allowed hot x1.5 / cold x0.5 [owner, not roll-excl] | {"N": 8, "thr_R": 2} | -9 / +3 / -10 / -27 | -16 | -11 | +3100 | +3 / +14 / +2 / -12 | 16.3 | 34% | FIRST-ORDER SCREEN ONLY | -16 / +7.0 / +81 | 0.23 | 1.00 | +41 | +2320 | FIRST-ORDER SCREEN ONLY | UP (report) [FIRST-ORDER SCREEN ONLY] |
| I6 up-allowed hot x1.5 / cold x0.5 [owner, not roll-excl] | {"N": 8, "thr_R": 4} | -18 / +5 / -4 / -29 | -34 | -16 | -2888 | -35 / -8 / -19 / -48 | 11.0 | 11% | FIRST-ORDER SCREEN ONLY | -5 / -12.4 / -65 | 0.96 | 1.00 | +41 | -280 | FIRST-ORDER SCREEN ONLY | UP (report) [FIRST-ORDER SCREEN ONLY] |

## Family J - Combinations

Combinations: 1179 cells (1179 down-only); best by equal-mean L6M maxDD cut: J pair min {"a": "I:83d7d23f2f5d", "b": "ext-VT:c5f9e199982a"} cuts L6M maxDD +99% at equal lots (d mean -7903 $/wk) and +99% at equal mean (PRE +52%, X' +57%); placebo p 0.03, family p 1.00, WF +11 -> CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| J pair min [ROLL-EXCL] | {"a": "I:83d7d23f2f5d", "b": "ext-VT:c5f9e199982a"} | +99 / +14 / +70 / +73 | +26 | +100 | -7903 | +99 / -37 / +52 / +57 | 1383.9 | 89% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "ext-L:53569966ba30", "b": "ext-VT:e3f124a36d05"} | +96 / +22 / +64 / +74 | -43 | +98 | -1366 | +96 / +16 / +61 / +73 | 330.7 | 82% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +11 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair product [ROLL-EXCL] | {"a": "ext-H:d1b5ea189963", "b": "ext-VT:c5f9e199982a"} | +94 / +69 / +63 / +74 | -15 | +96 | -4132 | +93 / +62 / +55 / +68 | 216.8 | 75% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +11 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "ext-K:d16e6b6b3c26", "b": "ext-VT:e3f124a36d05"} | +93 / +38 / +63 / +73 | -74 | +94 | +1359 | +93 / +41 / +65 / +75 | 211.4 | 65% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.10 | +11 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "ext-K:6fa18a1ca7ac", "b": "ext-VT:e3f124a36d05"} | +93 / +38 / +64 / +73 | -75 | +94 | +1338 | +93 / +41 / +66 / +75 | 211.2 | 65% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.10 | +11 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "K:5ac97ef10c49", "b": "ext-VT:c5f9e199982a"} | +94 / +71 / +68 / +73 | -16 | +97 | -3572 | +93 / +66 / +61 / +67 | 209.1 | 76% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +11 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair product [ROLL-EXCL] | {"a": "K:5ac97ef10c49", "b": "ext-VT:c5f9e199982a"} | +94 / +70 / +71 / +75 | -14 | +96 | -4284 | +93 / +63 / +64 / +69 | 161.0 | 76% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.97 | +11 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair product [ROLL-EXCL] | {"a": "ext-K:d16e6b6b3c26", "b": "ext-VT:e3f124a36d05"} | +92 / +33 / +66 / +77 | -77 | +94 | +1613 | +93 / +37 / +69 / +78 | 198.1 | 65% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.10 | +11 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair product [ROLL-EXCL] | {"a": "ext-K:6fa18a1ca7ac", "b": "ext-VT:e3f124a36d05"} | +92 / +33 / +67 / +77 | -78 | +94 | +1592 | +93 / +37 / +69 / +78 | 197.9 | 65% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.10 | +11 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "K:b8c7a11b7c62", "b": "ext-VT:c5f9e199982a"} | +92 / +68 / +63 / +70 | -34 | +95 | -490 | +92 / +67 / +62 / +69 | 188.1 | 73% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.72 | +11 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |

## Family K - P7

P7: 408 cells (408 down-only); best by equal-mean L6M maxDD cut: K6 ext-VT on P7 only {"cell": "c3eb2c6eff46", "orig": "ext ext-VT {\"cell\": \"c3 cuts L6M maxDD +49% at equal lots (d mean +2255 $/wk) and +53% at equal mean (PRE +47%, X' +34%); placebo p 0.01, family p 0.64, WF +39 -> LEAD [FIRST-ORDER SCREEN ONLY].

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K6 ext-VT on P7 only [ROLL-EXCL] | {"cell": "c3eb2c6eff46", "orig": "ext ext-VT {\"cell\": \"c3eb2c6eff46 | +49 / +20 / +42 / +28 | -26 | +62 | +2255 | +53 / +27 / +47 / +34 | 40.6 | 14% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 0.64 | +39 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-VT on P7 only [ROLL-EXCL] | {"cell": "4f42f1248635", "orig": "ext ext-VT {\"cell\": \"4f42f1248635 | +49 / +16 / +33 / +28 | -24 | +62 | +2125 | +53 / +23 / +38 / +34 | 40.4 | 14% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 0.61 | +39 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-VT on P7 only [ROLL-EXCL] | {"cell": "b12bf5626d65", "orig": "ext ext-VT {\"cell\": \"b12bf5626d65 | +49 / +16 / +34 / +28 | -20 | +61 | +1766 | +52 / +22 / +39 / +33 | 39.0 | 14% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 0.55 | +39 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-VT on P7 only [ROLL-EXCL] | {"cell": "83d8bb73d0ee", "orig": "ext ext-VT {\"cell\": \"83d8bb73d0ee | +45 / +3 / +19 / +10 | -34 | +59 | +3020 | +52 / +14 / +29 / +21 | 38.6 | 13% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 0.65 | +39 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-VT on P7 only [ROLL-EXCL] | {"cell": "b04aa4944756", "orig": "ext ext-VT {\"cell\": \"b04aa4944756 | +45 / +3 / +20 / +2 | -36 | +59 | +2919 | +51 / +14 / +29 / +13 | 38.4 | 14% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.01 | 0.69 | +39 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-B on P7 only [ROLL-EXCL] | {"cell": "9806533560c9", "orig": "ext ext-B {\"cell\": \"9806533560c9\ | +36 / +37 / +29 / +57 | -57 | +52 | +4129 | +46 / +47 / +40 / +64 | 33.6 | 13% | -28 /  /  /  (+185; table (IJK driver) mode) | +32 / +4.5 / +0 | 0.02 | 0.87 | +39 |  | FIRST-ORDER SCREEN ONLY | LEAD [EXACT partial] |
| K6 ext-B on P7 only [ROLL-EXCL] | {"cell": "faebfc320da8", "orig": "ext ext-B {\"cell\": \"faebfc320da8\ | +35 / +30 / +34 / +61 | -47 | +55 | +2285 | +41 / +36 / +40 / +65 | 31.0 | 15% | FIRST-ORDER SCREEN ONLY | +41 / -6.4 / -3 | 0.04 | 0.94 | +39 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only [ROLL-EXCL] | {"cell": "7850ad5e165a", "orig": "ext ext-A {\"cell\": \"7850ad5e165a\ | +42 / +2 / +27 / +9 | -8 | +46 | -1527 | +38 / -4 / +22 / +2 | 25.9 | 16% | FIRST-ORDER SCREEN ONLY | -16 / +57.7 / +377 | 0.01 | 0.07 | +39 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only [ROLL-EXCL] | {"cell": "e8116ed4fa4e", "orig": "ext ext-A {\"cell\": \"e8116ed4fa4e\ | +42 / +2 / +27 / +9 | -8 | +46 | -1527 | +38 / -4 / +22 / +2 | 25.9 | 16% | FIRST-ORDER SCREEN ONLY | -16 / +57.7 / +377 | 0.01 | 0.07 | +39 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |
| K6 ext-A on P7 only [ROLL-EXCL] | {"cell": "a64be38872f3", "orig": "ext ext-A {\"cell\": \"a64be38872f3\ | +35 / +16 / +27 / +10 | -31 | +42 | +778 | +38 / +19 / +29 / +13 | 24.4 | 12% | FIRST-ORDER SCREEN ONLY | +12 / +23.4 / +119 | 0.01 | 0.01 | +39 |  | FIRST-ORDER SCREEN ONLY | LEAD [FIRST-ORDER SCREEN ONLY] |

## Cross-family finalists (CANDIDATE / LEAD+ labels, top 25 by equal-mean L6M cut)

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | EXACT cut L6M/HOLD/PRE/Xp (d mean) | old base cut L6M / delta / rank chg | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| J pair min [ROLL-EXCL] | {"a": "I:83d7d23f2f5d", "b": "ext-VT:c5f9e199982a"} | +99 / +14 / +70 / +73 | +26 | +100 | -7903 | +99 / -37 / +52 / +57 | 1383.9 | 89% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.03 | 1.00 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair product [ROLL-EXCL] | {"a": "ext-H:61f3cbb073a5", "b": "ext-VT:c5f9e199982a"} | +94 / +74 / +70 / +73 | +6 | +95 | -6273 | +92 / +63 / +58 / +62 | 182.6 | 78% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [ROLL-EXCL] | {"a": "ext-H:61f3cbb073a5", "b": "ext-VT:c5f9e199982a"} | +92 / +74 / +63 / +71 | +6 | +93 | -5644 | +90 / +65 / +51 / +61 | 141.8 | 78% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-E:E|same_side_lots_cap|cap4_trunc|sess_london", "b": "ext-V | +90 / +70 / +68 / +75 | +9 | +94 | -2206 | +89 / +67 / +65 / +72 | 133.8 | 76% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.97 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.97) [FIRST-ORDER SCREEN ONLY] |
| J pair product [owner, not roll-excl] | {"a": "I:da1529221cbe", "b": "ext-VT:e3f124a36d05"} | +90 / +64 / +67 / +78 | +12 | +92 | -2612 | +89 / +59 / +62 / +75 | 133.6 | 71% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.62 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.62) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "Jtree:0d8433a1c4cd", "b": "ext-VT:e3f124a36d05"} | +90 / +24 / +54 / +76 | +39 | +91 | -1723 | +89 / +17 / +50 / +74 | 132.7 | 70% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-F:87dbd27287dc", "b": "ext-VT:c5f9e199982a"} | +92 / +52 / +61 / +67 | +13 | +95 | -7530 | +89 / +34 / +47 / +54 | 163.5 | 72% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-D:D|eqdd_stack_20d|Y20000_f0.25_sticky|sess_london", "b": " | +87 / +30 / +64 / +73 | +70 | +92 | +1496 | +88 / +34 / +66 / +74 | 123.7 | 66% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.46 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.46) [FIRST-ORDER SCREEN ONLY] |
| J pair product [owner, not roll-excl] | {"a": "Jtree:0d8433a1c4cd", "b": "ext-VT:9504ab9e63ac"} | +89 / +48 / +44 / +78 | +7 | +93 | -3143 | +88 / +40 / +35 / +74 | 118.4 | 75% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.72 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.72) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-K:6fa18a1ca7ac", "b": "ext-VT:c5f9e199982a"} | +88 / +70 / +62 / +74 | +32 | +93 | -469 | +88 / +69 / +61 / +73 | 118.1 | 73% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.92 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.92) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-K:d16e6b6b3c26", "b": "ext-VT:c5f9e199982a"} | +88 / +70 / +62 / +74 | +31 | +93 | -534 | +88 / +69 / +61 / +73 | 117.8 | 73% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.92 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.92) [FIRST-ORDER SCREEN ONLY] |
| J pair product [owner, not roll-excl] | {"a": "ext-D:D|eqdd_stack_20d|Y20000_f0.25_sticky|sess_london", "b": " | +87 / +26 / +63 / +72 | +72 | +92 | +1558 | +87 / +31 / +66 / +74 | 116.1 | 66% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.46 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.46) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-L:6fa81ee4110a", "b": "ext-VT:c5f9e199982a"} | +89 / +36 / +65 / +53 | +38 | +95 | -2928 | +87 / +26 / +60 / +46 | 114.4 | 81% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair product [owner, not roll-excl] | {"a": "K:b8c7a11b7c62", "b": "ext-VT:e3f124a36d05"} | +86 / +32 / +69 / +77 | +81 | +94 | +1353 | +87 / +36 / +71 / +78 | 111.9 | 65% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.38 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.38) [FIRST-ORDER SCREEN ONLY] |
| J pair product [owner, not roll-excl] | {"a": "ext-C:C|riskcap_per_trade|R$3600|ALL", "b": "ext-VT:c5f9e199982 | +90 / +72 / +70 / +74 | +9 | +95 | -4435 | +87 / +65 / +62 / +68 | 111.0 | 77% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 1.00 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-B:e2058312a643", "b": "ext-VT:e3f124a36d05"} | +86 / +33 / +57 / +76 | +60 | +89 | +1755 | +87 / +38 / +60 / +78 | 110.8 | 62% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.21 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.21) [FIRST-ORDER SCREEN ONLY] |
| J pair product [owner, not roll-excl] | {"a": "ext-H:61f3cbb073a5", "b": "ext-VT:e3f124a36d05"} | +89 / +53 / +69 / +80 | +24 | +90 | -4374 | +87 / +42 / +61 / +75 | 110.1 | 71% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.90 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.90) [FIRST-ORDER SCREEN ONLY] |
| J pair product [owner, not roll-excl] | {"a": "K:ac4e6310f17b", "b": "ext-VT:e3f124a36d05"} | +86 / +35 / +69 / +78 | +78 | +94 | +824 | +87 / +38 / +71 / +78 | 109.4 | 65% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.38 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.38) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "Jtree:9be3e678872f", "b": "ext-VT:e3f124a36d05"} | +87 / +38 / +49 / +76 | +34 | +88 | -1625 | +86 / +33 / +45 / +74 | 105.3 | 70% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.95 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.95) [FIRST-ORDER SCREEN ONLY] |
| J pair product [owner, not roll-excl] | {"a": "ext-E:E|total_lots_cap|cap4_trunc|sess_london", "b": "ext-VT:95 | +86 / +47 / +63 / +68 | +30 | +91 | -635 | +86 / +46 / +61 / +67 | 102.4 | 76% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.10 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.10) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-E:E|total_lots_cap|cap4_trunc|sess_london", "b": "ext-VT:95 | +86 / +46 / +63 / +69 | +28 | +91 | -701 | +86 / +44 / +62 / +68 | 102.1 | 76% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.10 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.10) [FIRST-ORDER SCREEN ONLY] |
| J pair product [owner, not roll-excl] | {"a": "K:5ac97ef10c49", "b": "ext-VT:e3f124a36d05"} | +87 / +46 / +69 / +76 | +52 | +93 | -2337 | +86 / +39 / +65 / +73 | 102.0 | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.82 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.82) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "K:5ac97ef10c49", "b": "ext-VT:e3f124a36d05"} | +87 / +52 / +69 / +75 | +52 | +92 | -1924 | +86 / +47 / +66 / +72 | 101.9 | 68% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.72 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.72) [FIRST-ORDER SCREEN ONLY] |
| J pair product [owner, not roll-excl] | {"a": "ext-E:E|same_side_lots_cap|cap4_trunc|sess_london", "b": "ext-V | +85 / +31 / +66 / +83 | +65 | +91 | +588 | +86 / +32 / +67 / +83 | 100.5 | 70% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.44 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.44) [FIRST-ORDER SCREEN ONLY] |
| J pair min [owner, not roll-excl] | {"a": "ext-D:D|consec_loss|stack_k2_f0.00|sess_london", "b": "ext-VT:e | +87 / +20 / +70 / +76 | +75 | +90 | -3234 | +85 / +9 / +66 / +73 | 122.1 | 70% | FIRST-ORDER SCREEN ONLY | n/a (SZ-BASE pending) | 0.02 | 0.69 | +11 |  | FIRST-ORDER SCREEN ONLY | CANDIDATE (own-p only; family p 0.69) [FIRST-ORDER SCREEN ONLY] |
