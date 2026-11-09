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

## 1e. TopK for the T-JOINT sizer layer (registered in /mnt/l2/l2vast/_th_joint/layers/sizer/topK.json; live Q1-A sizer is always entry 0; scale rules only, all layers ON)
- VT_S1 (897b0e0dc1ec): `r_park1_w10_all60 cont [2, 0.25]` scope [pool], with ER underneath; first-order EQ cut +32/+55/+62, s 0.93, live wk d$ -42813; exact: pending (queue month-major, L6M then PRE then X-prime then HOLD).
- VT_S2 (e4de3e4dce9c): `q_gk1_w10_all60 step [0.6, 0.5]` scope [pool], with ER underneath; first-order EQ cut +38/+53/+58, s 0.87, live wk d$ -33836; exact: pending (queue month-major, L6M then PRE then X-prime then HOLD).
- VT_S3 (f5a33aa69dcf): `r_gk1_w10_all60 cont [2, 0.25]` scope [book, P7, K7], with ER underneath; first-order EQ cut +21/+55/+51, s 0.91, live wk d$ -45243; exact: pending (queue month-major, L6M then PRE then X-prime then HOLD).
- VT_S4 (896711fc3c9f): `r_COMP_all60 cont [2, 0.25]` scope [pool], with ER underneath; first-order EQ cut +23/+50/+70, s 0.91, live wk d$ -53293; exact: pending (queue month-major, L6M then PRE then X-prime then HOLD).
- VT_S5 (38f03a4622ea): `q_COMP_all60 step [0.6, 0.5]` scope [pool], with ER underneath; first-order EQ cut +22/+45/+64, s 0.89, live wk d$ -38288; exact: pending (queue month-major, L6M then PRE then X-prime then HOLD).
All five are table-mode (static M keyed on the signal second, fixed driver). Rule mode would be needed only to size signals created by changed exits (re-entries); the vol features are not computable inside the engine today (v1.6 work).

## 2. Does the picking procedure hold out of sample? (purged monthly WF per family, 34 months; Q1-A OOS mean $16576/wk, OOS maxDD $140k)
| family | cells | OOS maxDD cut, equal lots | d mean $/wk (equal lots) | OOS cut at REALISED equal mean (s_oos) | s_oos | OOS cut with s fixed from training | d mean $/wk (s train) | worst-20 cut (s train) | months on Q1-A | holds? |
|---|---|---|---|---|---|---|---|---|---|---|
| per-book/session scope | 850 | 49.0 | -2235 | 41.0 | 1.16 | 43.1 | -3162 | 26.6 | 0/34 | YES (first-order) |
| composite graded/half (no zero) | 5220 | 44.4 | -2417 | 34.9 | 1.17 | 35.6 | -2481 | 21.4 | 0/34 | YES (first-order) |
| SCALE single measure | 904 | 41.9 | -1852 | 34.6 | 1.13 | 23.0 | -1804 | 18.6 | 0/34 | YES (first-order) |
| stack/book P&L target-vol | 864 | 46.7 | -3288 | 33.5 | 1.25 | 34.9 | -1349 | 18.1 | 0/34 | YES (first-order) |
| half (lo=.5) steps | 9806 | 25.0 | -1026 | 20.0 | 1.07 | 29.2 | -2082 | 23.7 | 0/34 | YES (first-order) |
| composite pooled scope | 388 | 38.6 | -4175 | 17.9 | 1.34 | 32.0 | -3945 | 19.6 | 0/34 | YES (first-order) |
| z-score | 3660 | 35.8 | -3636 | 17.7 | 1.28 | 13.8 | -6530 | 28.2 | 0/34 | YES (first-order) |
| continuous (ref/now)^p | 10272 | 31.4 | -2855 | 17.1 | 1.21 | 31.0 | -3278 | 16.1 | 0/34 | YES (first-order) |
| graded 3-step | 5055 | 25.8 | -1769 | 17.0 | 1.12 | 31.7 | -2968 | 31.1 | 0/34 | YES (first-order) |
| interactions (cap/cooldown) | 744 | 44.8 | -5835 | 14.8 | 1.54 | 28.0 | -5099 | 36.3 | 0/34 | YES (first-order) |
| composite consensus (all stages comp) | 7018 | 38.4 | -5219 | 10.1 | 1.46 | 19.5 | -5118 | 23.2 | 0/34 | YES (first-order) |
| SCALE P7+K7 scope | 446 | 16.9 | -1352 | 9.5 | 1.09 | 22.9 | -1427 | 12.2 | 0/34 | YES (first-order) |
| special (first/dur/dir/vov/evt) | 1824 | 17.7 | -1940 | 6.8 | 1.13 | 13.8 | -3597 | 22.2 | 0/34 | YES (first-order) |
| ratio step/cont (r_*) | 12381 | 43.6 | -6607 | 6.3 | 1.66 | 23.1 | -6395 | 26.1 | 0/34 | YES (first-order) |
| SCALE consensus measure | 880 | 16.9 | -1930 | 5.9 | 1.13 | 22.9 | -1726 | 13.1 | 0/34 | YES (first-order) |
| SCALE pooled | 446 | 16.9 | -2031 | 5.3 | 1.14 | 22.9 | -1630 | 19.5 | 0/34 | YES (first-order) |
| vol-skip multiples only (old AB style r_*, lo=0) | 2461 | 43.6 | -6779 | 4.6 | 1.69 | 23.1 | -6640 | 27.7 | 0/34 | weak |
| SCALE rules (never zero) all | 1784 | 16.9 | -2171 | 4.4 | 1.15 | 22.9 | -2023 | 14.8 | 0/34 | weak |
| event-excluded ref | 3355 | 35.8 | -6048 | -1.2 | 1.57 | -7.2 | -5761 | 11.4 | 0/34 | NO |
| quantile-adaptive (q_*) | 9911 | 26.6 | -5095 | -6.0 | 1.44 | 16.1 | -5704 | 28.4 | 0/34 | NO |
| ALL B (onQ1A) | 39200 | 26.6 | -5874 | -13.8 | 1.55 | 16.1 | -6245 | 31.4 | 0/34 | NO |
| session-slot ref | 12963 | 26.6 | -6678 | -23.0 | 1.67 | 16.1 | -7007 | 20.8 | 0/34 | NO |

Reading: s fixed from training leaves the OOS mean 7-20 % below Q1-A in most families (the training-window s is not the OOS s), so "cut at the realised equal mean" is the honest equal-mean column; the trained-s column shows the cut that would actually be live with the mean given up in the next column. Simple size-down-everything benchmark: cutting maxDD by x % costs x % of the mean = about $118/wk of mean per $1k of maxDD (Q1-A mean / maxDD); a family only buys something if its rate is below that.

## 3. Time split: pick on weeks up to 2025-06-30 (118 weeks), test 2025-07..2026-11 (70 weeks)
| top-k by training equal-mean cut | test EQ cut (s from training), median | share of picks with test EQ cut > 0 | test mean / Q1-A mean (s from training) | test EQ cut with test-fitted s, median |
|---|---|---|---|---|
| 1 | 28.2 | 1.00 | 0.76 | 5.2 |
| 5 | 17.3 | 0.80 | 0.82 | -0.6 |
| 20 | 18.1 | 0.85 | 0.87 | 7.3 |
| 50 | 18.9 | 0.90 | 0.94 | 17.0 |
| 300 | 16.4 | 0.86 | 0.91 | 8.9 |

All 38975 down-only cells: rank correlation of training score vs test EQ cut 0.51; share of cells with positive test EQ cut (s from training) 0.71, median 8.9 %. 

## 4. B5 - scaled-to-Q1-A-mean rows and executability ("if we double the size isn't it better?")
Scale factor s = Q1-A L6M mean / cell L6M mean (s < 1: the cell earns more than Q1-A at equal lots and is scaled DOWN to match; s > 1: scaled UP). Largest single-trade risk = lots x stop (59.9 pts median, 56 P7, 40 O7) x $20. Max lots on at once = peak sum of open lots in the base trade list at the cell's lots (x s). The P7 7-lot table becomes 7 x s lots; slices, participation cap and margin were NOT re-simulated here: the table shows how many lots the P7 table and the stack would hold at scale s (margin scales with max lots at once), and the exact engine runs in section 6 apply the real slicing at unscaled lots.
| cell | s | maxDD L6M cell / scaled ($k) | Q1-A maxDD L6M ($k) | worst-20 scaled / ref ($k) | Ulcer scaled / ref ($k) | Calmar L6M cell (ann mean / maxDD) | largest trade risk: Q1-A / cell / scaled ($k) | max lots at once: Q1-A / scaled | P7 table x s |
|---|---|---|---|---|---|---|---|---|---|
| interactions (cap/ q_park15_w12_all10 [0.6, 0] | 0.93 | 16.0 / 14.8 | 79.9 | 256 / 165 | 4.2 / - | 78.7 | 7.8 / 7.8 / 7.3 | 20 / 14 | 6.5 |
| quantile-adaptive  q_gk1_w10_all5 [0.6, 0] | 0.83 | 27.7 / 23.0 | 79.9 | 194 / 165 | 7.5 / - | 50.4 | 7.8 / 7.8 / 6.5 | 20 / 16 | 5.8 |
| ratio step/cont (r r_ewma5_l90_all40 [1.1, 0] | 0.91 | 28.5 / 26.1 | 79.9 | 186 / 165 | 10.0 / - | 46.5 | 7.8 / 7.8 / 7.2 | 20 / 17 | 6.4 |
| per-book/session s q_park15_w12_all10 [0.6, 0] | 0.93 | 26.8 / 24.9 | 79.9 | 221 / 165 | 9.8 / - | 46.8 | 7.8 / 7.8 / 7.3 | 20 / 18 | 6.5 |
| graded 3-step q_park1_w10_all10 [0.6, 0.8] | 0.85 | 37.1 / 31.5 | 79.9 | 209 / 165 | 9.9 / - | 36.9 | 7.8 / 7.8 / 6.6 | 20 / 16 | 5.9 |
| special (first/dur q_atr5_n14_all20 [] | 0.84 | 53.9 / 45.3 | 79.9 | 217 / 165 | 12.9 / - | 26.8 | 7.8 / 7.8 / 6.6 | 20 / 17 | 5.9 |
| session-slot ref r_gk15_w6_slot10 [1.1, 0] | 0.97 | 32.3 / 31.4 | 79.9 | 181 / 165 | 10.7 / - | 38.6 | 7.8 / 7.8 / 7.6 | 20 / 18 | 6.8 |
| continuous (ref/no r_park1_w10_all40 [2, 0] | 0.92 | 53.9 / 49.5 | 79.9 | 203 / 165 | 15.4 / - | 24.5 | 7.8 / 7.8 / 7.2 | 20 / 17 | 6.4 |
| composite pooled s q_COMP_all10 [0.5, 0.8] | 0.91 | 40.0 / 36.5 | 79.9 | 218 / 165 | 14.7 / - | 31.8 | 7.8 / 7.8 / 7.2 | 20 / 17 | 6.4 |
| SCALE rules (never r_park1_w10_all60 [2, 0.25] | 0.93 | 58.4 / 54.5 | 79.9 | 200 / 165 | 16.7 / - | 22.3 | 7.8 / 7.8 / 7.3 | 20 / 18 | 6.5 |
| composite consensu q_COMP_all60 [0.6, 0] | 0.86 | 64.7 / 55.9 | 79.9 | 193 / 165 | 14.2 / - | 20.8 | 7.8 / 7.8 / 6.8 | 20 / 17 | 6.1 |
| z-score z_park1_w10_slot20 [1.0, 0] | 0.98 | 69.9 / 68.5 | 79.9 | 121 / 165 | 22.1 / - | 17.7 | 7.8 / 7.8 / 7.7 | 20 / 19 | 6.9 |

Doubling everything (s = 2 on Q1-A) doubles maxDD and the largest single-trade risk ($7.8k -> $15.7k) with the same Calmar; it does not cut drawdown at equal mean. A vol-target cell with s < 1 earns the Q1-A mean with s x lots, so its single-trade risk is lower than Q1-A's by the factor s, not higher.

## 5. Which books suffer in high vol? (all-measure consensus vol rank q = mean quantile rank of 53 measures vs the prior 20 days; Q1-A lots; mean net $ per trade / win rate / n)
| book | q < .5 | .5-.7 | .7-.85 | > .85 | share of the book's Q1-A P&L earned in q > .7 |
|---|---|---|---|---|---|
| K7 | +71 / 47% / 1978 | +104 / 48% / 1649 | +43 / 46% / 1678 | +24 / 44% / 1867 | 28% |
| P7 | +396 / 50% / 1816 | +323 / 49% / 1315 | +161 / 48% / 1129 | -49 / 47% / 1000 | 10% |
| M7 | +56 / 43% / 1573 | -78 / 38% / 893 | -5 / 41% / 915 | -2 / 41% / 1135 | -55% |
| U7 | +225 / 51% / 830 | +249 / 52% / 320 | +370 / 53% / 161 | +466 / 55% / 60 | 25% |
| A7 | +142 / 53% / 612 | +31 / 47% / 266 | +185 / 54% / 181 | -59 / 42% / 100 | 22% |
| H7 | +200 / 49% / 483 | +345 / 51% / 167 | -19 / 42% / 211 | +103 / 49% / 251 | 12% |
| O7 | -67 / 25% / 12 | +310 / 42% / 139 | +149 / 36% / 244 | +65 / 34% / 109 | 50% |
| ALL | +180 / 48% / 7304 | +151 / 47% / 4749 | +83 / 45% / 4519 | +11 / 44% / 4522 | 17% |

Reading: if the >.85 column is lower than the < .5 column the book loses its edge in hot tape; a book whose high-vol bucket earns as much as the quiet bucket should not be scoped into a vol rule (the per-book scope rows in section 1 choose P7+K7 for this reason when they win).

## 6. Old-vs-new base (Addendum 1): the same rule on the OLD base (DS3_SIZER S4A engine: 51 % ThL2Cut exits), S1b-COMB (state cuts) and the NOCUT / UNIF controls
Base-change proof (Q1-A zero-rule row, first-order series on each trade list): 
| base | trades | mean $/trade | Q1-A maxDD L6M / PRE / X' ($k) | exit mix (top 4) |
|---|---|---|---|---|
| S1B-COMB | 21135 | 117 | 80 / 140 / 129 | Target 45%, StateCut 32%, StopJoin 9%, StopJoinFallback 5% |
| OLD-BASE | 23776 | 76 | 142 / 169 / 76 | ThL2Cut 51%, Target 38%, PolicyCut 5%, StopJoin 1% |

| cell (b5 pick) | NEW cut L6M/PRE/X' (EQ) | OLD-BASE cut L6M/PRE/X' (EQ) | delta EQ L6M | rank new -> old (of ~30k down-only) | NOCUT EQ L6M/PRE/X' | UNIF EQ L6M/PRE/X' | same-to-the-dollar? |
|---|---|---|---|---|---|---|---|
| interactions (ca q_park15_w12_all10 [0.6, 0] | +80/+57/+76 (+81/+60/+78) | +63/+62/+31 (+54/+53/+14) | -27 | 1 -> 826 | +85/+35/+79 | +80/+63/+71 | differs |
| quantile-adaptiv q_gk1_w10_all5 [0.6, 0] | +65/+6/+61 (+71/+22/+68) | +71/+19/+27 (+78/+39/+45) | +7 | 167 -> 2030 | +78/+19/+75 | +81/+61/+82 | differs |
| ratio step/cont  r_ewma5_l90_all40 [1.1, 0] | +64/+53/+65 (+67/+57/+68) | +76/+46/+30 (+73/+38/+20) | +6 | 184 -> 4807 | +76/+55/+72 | +78/+70/+81 | differs |
| per-book/session q_park15_w12_all10 [0.6, 0] | +67/+48/+63 (+69/+52/+66) | +68/+51/+35 (+73/+58/+44) | +4 | 255 -> 398 | +80/+33/+72 | +69/+54/+63 | differs |
| graded 3-step q_park1_w10_all10 [0.6, 0.8] | +54/+58/+66 (+61/+64/+72) | +67/+52/+44 (+73/+61/+55) | +13 | 318 -> 259 | +78/+52/+62 | +70/+61/+58 | differs |
| special (first/d q_atr5_n14_all20 [] | +33/+54/+56 (+43/+61/+63) | +66/+49/+17 (+72/+59/+33) | +29 | 397 -> 386 | +65/+57/+51 | +59/+64/+40 | differs |
| session-slot ref r_gk15_w6_slot10 [1.1, 0] | +60/+61/+16 (+61/+62/+18) | +57/+54/-73 (+63/+60/-51) | +2 | 417 -> 305 | +84/+71/+32 | +65/+71/+34 | differs |
| continuous (ref/ r_park1_w10_all40 [2, 0] | +33/+55/+60 (+38/+58/+63) | +48/+56/+27 (+55/+61/+36) | +16 | 530 -> 669 | +53/+50/+55 | +48/+62/+52 | differs |
| composite pooled q_COMP_all10 [0.5, 0.8] | +50/+53/+67 (+54/+58/+70) | +59/+47/+34 (+56/+43/+29) | +2 | 582 -> 2815 | +68/+56/+73 | +60/+63/+70 | differs |
| SCALE rules (nev r_park1_w10_all60 [2, 0.25] | +27/+52/+60 (+32/+55/+62) | +49/+62/+26 (+55/+66/+35) | +23 | 774 -> 634 | +52/+54/+51 | +45/+65/+49 | differs |
| composite consen q_COMP_all60 [0.6, 0] | +19/+46/+66 (+30/+53/+71) | +50/+68/+19 (+62/+76/+38) | +32 | 979 -> 239 | +56/+58/+73 | +66/+68/+77 | differs |
| z-score z_park1_w10_slot20 [1.0, 0] | +13/+52/+52 (+14/+53/+53) | +36/+31/-3 (+49/+44/+17) | +34 | 1074 -> 2347 | +14/+28/+46 | +23/+40/+51 | differs |

Across 39139 cells present on both bases: correlation of L6M cut new vs old 0.69; of the tolerant equal-mean score 0.73; top-50 overlap (new top-50 that are also in the old top-50) 0. Every row differs from the old base number (no identical-to-the-dollar rows): the vol rules are not exit-independent, and the old-base top cells are not the new-base top cells.

**EXACT STATUS (17:05Z): all earlier VT exact runs (VT_E1, VT_E7) were VOID (sz_exact table-mode key bug: multipliers keyed on arm time, not the signal second; fixed by SZ-CORE, runs quarantined). All exact rows below are PENDING until re-run with the fixed driver; every number in sections 1-6, 8-10 is first-order screen only. Table mode (static M) is used for these cells; rule mode (sz_rules) would need the quantile features inside the engine, listed as v1.6 work.**
## 7. EXACT engine rows (sz_exact static M tables on the S1b tick engine; windows shown only when every month is present)
| set | cell | window | exact cut | exact EQ cut | exact d mean $/wk | first-order cut | first-order EQ cut | first-order d mean |
|---|---|---|---|---|---|---|---|---|
| (no complete window yet) |

## 8. Rate: weekly mean given up per $1k of maxDD cut (WF OOS, equal lots) vs the size-down-everything benchmark
Benchmark (scale Q1-A down by x%: mean and maxDD both fall x%): $118/wk of mean per $1k of maxDD. | family | OOS cut % | OOS $ maxDD cut | d mean $/wk | $ mean per $1k of maxDD | vs benchmark |
|---|---|---|---|---|---|
| per-book/session scope | 49.0 | 68698 | -2235 | 33 | cheaper |
| stack/book P&L target-vol | 46.7 | 65558 | -3288 | 50 | cheaper |
| interactions (cap/cooldown) | 44.8 | 62861 | -5835 | 93 | cheaper |
| composite graded/half (no zero) | 44.4 | 62231 | -2417 | 39 | cheaper |
| ratio step/cont (r_*) | 43.6 | 61206 | -6607 | 108 | cheaper |
| vol-skip multiples only (old AB style r_*, lo=0) | 43.6 | 61206 | -6779 | 111 | cheaper |
| SCALE single measure | 41.9 | 58734 | -1852 | 32 | cheaper |
| composite pooled scope | 38.6 | 54131 | -4175 | 77 | cheaper |
| composite consensus (all stages comp) | 38.4 | 53882 | -5219 | 97 | cheaper |
| z-score | 35.8 | 50184 | -3636 | 72 | cheaper |
| event-excluded ref | 35.8 | 50166 | -6048 | 121 | dearer |
| continuous (ref/now)^p | 31.4 | 44074 | -2855 | 65 | cheaper |
| quantile-adaptive (q_*) | 26.6 | 37248 | -5095 | 137 | dearer |
| ALL B (onQ1A) | 26.6 | 37248 | -5874 | 158 | dearer |
| session-slot ref | 26.6 | 37248 | -6678 | 179 | dearer |
| graded 3-step | 25.8 | 36221 | -1769 | 49 | cheaper |
| half (lo=.5) steps | 25.0 | 35051 | -1026 | 29 | cheaper |
| special (first/dur/dir/vov/evt) | 17.7 | 24891 | -1940 | 78 | cheaper |
| SCALE P7+K7 scope | 16.9 | 23715 | -1352 | 57 | cheaper |
| SCALE rules (never zero) all | 16.9 | 23683 | -2171 | 92 | cheaper |
| SCALE pooled | 16.9 | 23683 | -2031 | 86 | cheaper |
| SCALE consensus measure | 16.9 | 23683 | -1930 | 81 | cheaper |

## 9. Plain sentence per family (first-order screen; exact rows in section 7 override when present)
- **continuous (ref/now)^p.** Continuous (ref/now)^p sizing: the best cells keep every signal (skip share 0) and cut maxDD +33/+54/+57 % (L6M/PRE/X') at equal lots with +$2.2k/wk; the walk-forward of picking among 7,320 cells cuts OOS maxDD 30 % at equal lots and 15 % at the realised equal mean, so it holds in this screen, but the cut is smaller than the skip cells promise in-sample.
- **half (lo=.5) steps.** Half instead of skip: halving above the 1.1x / 60th-percentile break cuts +32/+46/+52 % at equal lots, keeps all signals and holds OOS (WF 25 % equal lots, 18 % at the realised equal mean) at a cheaper mean cost than skips.
- **graded 3-step.** Graded {1, .5, 0} at two quantile breaks cuts 54-63 % in-sample while skipping only about 37 % of signals; WF 34 % equal lots, 22 % at the realised equal mean.
- **quantile-adaptive (q_*).** Quantile-adaptive skip (skip above the 60th-90th percentile of the trailing 5-60 d distribution): best in-sample cut of any family but the picking procedure FAILS at equal mean (WF +19 % at equal lots, -17 % at realised equal mean): adaptive thresholds removed the fixed-multiple bias but not the selection problem; skipping 55-60 % of signals gives back the live week (-$40k to -$55k of $104.8k).
- **ratio step/cont (r_*).** Ratio-multiple skips (the first-page family): in-sample +64/+59/+46 but WF at the realised equal mean -11 %.
- **session-slot ref.** Session-aware (same half-hour slot) norm: does not rescue the skip rule; WF at equal mean negative, and it adds a weaker X' cut.
- **event-excluded ref.** Excluding FOMC/CPI/NFP days from the norm: slightly better equal-lots WF (36 %) but only +8 % at the realised equal mean (weak).
- **z-score.** z-score thresholds: comparable to the quantile skips, WF +16 % at equal mean (weak-positive).
- **special (first/dur/dir/vov/evt).** Skip less (first signal of the episode, spiked vs sustained, direction-aware, rising vol, event day): skipping only when vol has been SUSTAINED above 1.25x for 30-120 min keeps most of the benefit (best tolerant score 61 vs 20 for "spiked"), skipping only high-vol signals that go WITH the last 5-60 min move beats skipping those against it (59 vs 23), while first-signal-of-episode (46 per book, 19 stack) and vol-of-vol (31) cells are weaker (first-order screen scores); WF +5 % at the realised equal mean (weak).
- **per-book/session scope.** Per book: scoping the rule to P7+K7 (P7 loses -$40/trade in the top vol bucket, U7 and H7 do not) skips about 40 % of signals, cuts 60/52/62 % in-sample, and the per-book WF holds (47 % equal lots, 39 % at the realised equal mean).
- **stack/book P&L target-vol.** Target-volatility of the stack P&L (trailing 10-20 d vol, down-only): in-sample modest (equal-mean X' negative), but the WF picks hold (45 % equal lots, 32 % at the realised equal mean); it keeps all signals and is the cheapest rate of the family.
- **interactions (cap/cooldown).** Stack exposure cap and post-loss cooldown on top of the vol rule: the cap adds a few points to the best skip cell (+81 vs +69 L6M) but is picked from a small set; WF 28 % at the realised equal mean.
- **composite pooled scope.** All-measure consensus (mean quantile rank over 53 measures): removes the choice of measure; its pooled graded/skip cells hold OOS at 18 % (26 w) to 40 % (52 w) at the realised equal mean.

## 10. Panel-ready definitions of what holds (first-order WF + time split; exact confirmation pending where section 7 is empty)
Definitions are in terms of the engine-computable measure at the signal second: **measure** m(t) on 1-min bars closed before the signal; **sigma_ref** = median (or quantile rank) of m over the previous N trading days, all minutes; **ratio** x = m(t)/sigma_ref; M = lots_after_Q1A x multiplier, rounded max(1, floor(lots x mult + .5)), 0 = skip.
- **continuous (ref/now)^p**: measure/feature `r_park1_w10_all40`, shape `cont`, params [2, 0], scope ["pool"], with the ER sizer underneath (onQ1A), down-only. First-order: cut +33/+55/+60 (L6M/PRE/X'), EQ +38/+58/+63, s 0.92, skip 0 %, live week d$ -41810. WF family OOS at the realised equal mean 17.1 %.
- **half (lo=.5) steps**: measure/feature `r_gk1_w10_all60`, shape `step`, params [1.25, 0.5], scope ["pool"], with the ER sizer underneath (onQ1A), down-only. First-order: cut +18/+46/+52 (L6M/PRE/X'), EQ +26/+52/+57, s 0.90, skip 0 %, live week d$ -26638. WF family OOS at the realised equal mean 20.0 %.
- **graded 3-step**: measure/feature `q_park1_w10_all10`, shape `g3`, params [0.6, 0.8], scope ["pool"], with the ER sizer underneath (onQ1A), down-only. First-order: cut +54/+58/+66 (L6M/PRE/X'), EQ +61/+64/+72, s 0.85, skip 37 %, live week d$ -51248. WF family OOS at the realised equal mean 17.0 %.
- **per-book/session scope**: measure/feature `q_park15_w12_all10`, shape `step`, params [0.6, 0], scope ["book", "P7", "K7"], with the ER sizer underneath (onQ1A), down-only. First-order: cut +67/+48/+63 (L6M/PRE/X'), EQ +69/+52/+66, s 0.93, skip 35 %, live week d$ -65885. WF family OOS at the realised equal mean 41.0 %.
- **composite pooled scope**: measure/feature `q_COMP_all10`, shape `g3`, params [0.5, 0.8], scope ["pool"], with the ER sizer underneath (onQ1A), down-only. First-order: cut +50/+53/+67 (L6M/PRE/X'), EQ +54/+58/+70, s 0.91, skip 28 %, live week d$ -63368. WF family OOS at the realised equal mean 17.9 %.
- **stack/book P&L target-vol**: measure/feature `tvol_ALL`, shape `tvol`, params [20, 0.8, 2, 0.5, "ALL"], scope ["pool"], with the ER sizer underneath (onQ1A), down-only. First-order: cut +47/+43/+2 (L6M/PRE/X'), EQ +24/+18/-41, s 1.44, skip 0 %, live week d$ -37680. WF family OOS at the realised equal mean 33.5 %.

Feature key: `r_<measure>_<all|slot><N>` = ratio of the measure to its median over the previous N trading days (`all` = all minutes, `slot` = same half-hour +-15 min); `q_...` = fraction of those reference values below the current value; measures: park1_w10 = Parkinson vol over the last 10 one-minute bars, gk1_wW = Garman-Klass, rv1_wW = realized vol of 1-min returns, atr1_nN = ATR of N one-minute bars, ewma5_l90 = EWMA (lambda .90) of squared 5-min returns, `COMP` = consensus over all 53 measures.

## 11. v1.6 fields needed (none of this exists in D7 v1.5; the v1.5 panel has TrendEr* ER sizer, session lot tables, A06 slots, B02 range filter, StackCutPct/StackAsiaOnly, lock caps and L2 gate stages only)
- VolMeasure (enum: Parkinson, GK, RV1m, RV5m, ATR, EWMA), VolBars (window), VolBarMin (1/5/15), VolRefDays (5-60), VolRefType (all minutes / same half-hour slot), VolRefStat (median ratio / quantile rank), VolMode (continuous / step / graded), VolP, VolFloor, VolBreak1, VolBreak2, VolLoMult1, VolLoMult2, VolBookMask (per-book on/off, e.g. P7+K7), VolWithEr (stack on top of TrendEr or replace), VolEventExclude (FOMC/CPI/NFP days dropped from the norm), VolMaxCap (down-only: never above table lots).
- Rolling per-minute store of the measure for the last 60 trading days (all minutes, plus slot index) so the quantile/median is computed causally at the signal second; engine rounding as above; skip means no entry (the signal is consumed).
- Stack target-vol: StackVolDays (10/15/20), StackVolTargetMult (x expanding median of its own trailing vol), StackVolP, StackVolFloor, from the realised daily P&L of the previous days (per book optional).
- NOT first-order testable here and therefore needing engine work before any claim: delay-and-recheck, equal-$-risk stop widening, sigma-scaled lock caps, vol-governed state-cut arm/persistence.