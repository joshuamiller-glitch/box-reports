# DS3_SIZER_VOLTARGET - T-SIZER-EXHAUST Addendum 2 (SZ-VT), refreshed 2026-11-09 17:03Z
**Post-hoc, Shadow only, no PASS claims. PRE-PROOF (entry match < .85). Numbers below are FIRST-ORDER SCREEN unless a row says [EXACT]. Prereg: autopilot/SZ_VT_PREREG.md (sha in DECISIONS.md). ALL EXACT ROWS ARE PENDING/VOID until re-run with the fixed sz_exact driver (key bug found 17:00Z).**

**VERDICT (plain, provisional: first-order screen, exact rows in section 7 pending): no vol-target cell is yet confirmed at equal mean out of sample; the skip rules that win in-sample (quantile/multiple skip of 55-60 % of signals) FAIL the equal-mean walk-forward (-17 % / -11 %) and lose $40-80k of the +$104.8k high-vol live week, while the rules that scale instead of skip (half, graded 3-step, continuous (ref/now)^p, per-book P7+K7, stack-P&L target-vol, all-measure consensus) hold in the first-order walk-forward at +15 to +39 % maxDD cut at the realised equal mean and cost $34-78/wk of mean per $1k of maxDD cut against $118 for simply sizing down; the exact engine historically shrinks first-order cuts 2-5x, so the claim stands or falls on section 7.**

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
| special (first/dur q_gk5_w12_all20 [] | 0.82 | 56.0 / 46.0 | 79.9 | 203 / 165 | 15.0 / - | 26.5 | 7.8 / 7.8 / 6.4 | 20 / 16 | 5.7 |
| session-slot ref r_gk15_w6_slot10 [1.1, 0] | 0.97 | 32.3 / 31.4 | 79.9 | 181 / 165 | 10.7 / - | 38.7 | 7.8 / 7.8 / 7.6 | 20 / 18 | 6.8 |
| continuous (ref/no r_park1_w10_all40 [2, 0] | 0.91 | 53.9 / 49.0 | 79.9 | 203 / 165 | 15.3 / - | 23.7 | 7.8 / 7.8 / 7.1 | 20 / 17 | 6.4 |
| z-score z_ewma5_l97_slot10 [1.0, 0] | 0.95 | 45.8 / 43.6 | 79.9 | 232 / 165 | 10.4 / - | 26.7 | 7.8 / 7.8 / 7.5 | 20 / 19 | 6.7 |
| half (lo=.5) steps r_gk1_w10_all60 [1.1, 0.5] | 0.89 | 54.5 / 48.8 | 79.9 | 208 / 165 | 17.9 / - | 23.8 | 7.8 / 7.8 / 7.0 | 20 / 17 | 6.3 |

Doubling everything (s = 2 on Q1-A) doubles maxDD and the largest single-trade risk ($7.8k -> $15.7k) with the same Calmar; it does not cut drawdown at equal mean. A vol-target cell with s < 1 earns the Q1-A mean with s x lots, so its single-trade risk is lower than Q1-A's by the factor s, not higher.

## 5. Which books suffer in high vol? (all-measure consensus vol rank q = mean quantile rank of 53 measures vs the prior 20 days; Q1-A lots; mean net $ per trade / win rate / n)
| book | q < .5 | .5-.7 | .7-.85 | > .85 | share of the book's Q1-A P&L earned in q > .7 |
|---|---|---|---|---|---|
| K7 | +66 / 47% / 1986 | +109 / 49% / 1649 | +38 / 46% / 1681 | +27 / 45% / 1856 | 27% |
| P7 | +397 / 50% / 1826 | +334 / 49% / 1311 | +147 / 48% / 1129 | -40 / 47% / 994 | 10% |
| M7 | +57 / 43% / 1579 | -80 / 38% / 892 | -11 / 41% / 918 | +4 / 41% / 1127 | -48% |
| U7 | +219 / 51% / 829 | +264 / 52% / 322 | +355 / 53% / 161 | +547 / 56% / 59 | 25% |
| A7 | +142 / 53% / 610 | +40 / 48% / 268 | +185 / 54% / 182 | -48 / 42% / 99 | 23% |
| H7 | +185 / 49% / 478 | +353 / 51% / 173 | +0 / 43% / 211 | +111 / 49% / 250 | 16% |
| O7 | -67 / 25% / 12 | +318 / 43% / 138 | +159 / 36% / 247 | +32 / 33% / 107 | 49% |
| ALL | +178 / 48% / 7320 | +157 / 47% / 4753 | +78 / 45% / 4529 | +17 / 44% / 4492 | 17% |

Reading: if the >.85 column is lower than the < .5 column the book loses its edge in hot tape; a book whose high-vol bucket earns as much as the quiet bucket should not be scoped into a vol rule (the per-book scope rows in section 1 choose P7+K7 for this reason when they win).

## 6. Old-vs-new base (Addendum 1): the same rule on the OLD base (DS3_SIZER S4A engine: 51 % ThL2Cut exits), S1b-COMB (state cuts) and the NOCUT / UNIF controls
Base-change proof (Q1-A zero-rule row, first-order series on each trade list): 
| base | trades | mean $/trade | Q1-A maxDD L6M / PRE / X' ($k) | exit mix (top 4) |
|---|---|---|---|---|
| S1B-COMB | 21135 | 117 | 80 / 140 / 117 | Target 45%, StateCut 32%, StopJoin 9%, StopJoinFallback 5% |
| OLD-BASE | 23776 | 76 | 142 / 165 / 76 | ThL2Cut 51%, Target 38%, PolicyCut 5%, StopJoin 1% |

| cell (b5 pick) | NEW cut L6M/PRE/X' (EQ) | OLD-BASE cut L6M/PRE/X' (EQ) | delta EQ L6M | rank new -> old (of ~30k down-only) | NOCUT EQ L6M/PRE/X' | UNIF EQ L6M/PRE/X' | same-to-the-dollar? |
|---|---|---|---|---|---|---|---|
| interactions (ca q_park15_w12_all10 [0.6, 0] | +81/+53/+74 (+83/+57/+76) | +63/+61/+29 (+54/+51/+12) | -29 | 1 -> 858 | +85/+31/+77 | +80/+62/+68 | differs |
| quantile-adaptiv q_atr1_n5_all5 [0.6, 0] | +72/+17/+66 (+74/+24/+69) | +56/+37/+31 (+55/+36/+30) | -19 | 89 -> 5169 | +79/+49/+49 | +63/+58/+42 | differs |
| per-book/session r_ewma5_l90_all40 [1.1, 0] | +60/+52/+62 (+64/+56/+65) | +71/+63/+28 (+75/+69/+39) | +12 | 294 -> 13 | +74/+58/+71 | +75/+66/+79 | differs |
| ratio step/cont  r_atr1_n14_all10 [1.1, 0] | +64/+59/+46 (+68/+63/+52) | +79/+53/+19 (+76/+46/+7) | +9 | 326 -> 1507 | +80/+52/+58 | +71/+42/+50 | differs |
| graded 3-step q_park1_w10_all10 [0.6, 0.8] | +54/+57/+63 (+61/+63/+69) | +67/+51/+44 (+73/+60/+55) | +13 | 328 -> 259 | +78/+51/+58 | +70/+61/+54 | differs |
| special (first/d q_gk5_w12_all20 [] | +30/+53/+53 (+42/+61/+61) | +39/+62/-9 (+51/+69/+12) | +9 | 381 -> 899 | +67/+70/+43 | +61/+75/+33 | differs |
| session-slot ref r_gk15_w6_slot10 [1.1, 0] | +60/+61/+5 (+61/+62/+8) | +57/+53/-58 (+63/+59/-39) | +2 | 394 -> 296 | +84/+71/+23 | +65/+71/+25 | differs |
| continuous (ref/ r_park1_w10_all40 [2, 0] | +33/+54/+57 (+39/+58/+61) | +49/+55/+27 (+56/+60/+37) | +17 | 502 -> 478 | +54/+50/+57 | +49/+62/+54 | differs |
| z-score z_ewma5_l97_slot10 [1.0, 0] | +43/+50/+50 (+45/+52/+52) | +54/+56/-8 (+44/+46/-32) | -1 | 1061 -> 1960 | +44/+28/+51 | +52/+43/+52 | differs |
| half (lo=.5) ste r_gk1_w10_all60 [1.1, 0.5] | +32/+46/+52 (+39/+51/+57) | +46/+47/+30 (+55/+56/+42) | +16 | 1130 -> 504 | +47/+46/+55 | +45/+55/+60 | differs |

Across 36973 cells present on both bases: correlation of L6M cut new vs old 0.69; of the tolerant equal-mean score 0.72; top-50 overlap (new top-50 that are also in the old top-50) 0. Every row differs from the old base number (no identical-to-the-dollar rows): the vol rules are not exit-independent, and the old-base top cells are not the new-base top cells.

**EXACT STATUS (17:05Z): all earlier VT exact runs (VT_E1, VT_E7) were VOID (sz_exact table-mode key bug: multipliers keyed on arm time, not the signal second; fixed by SZ-CORE, runs quarantined). All exact rows below are PENDING until re-run with the fixed driver; every number in sections 1-6, 8-10 is first-order screen only. Table mode (static M) is used for these cells; rule mode (sz_rules) would need the quantile features inside the engine, listed as v1.6 work.**
## 7. EXACT engine rows (sz_exact static M tables on the S1b tick engine; windows shown only when every month is present)
| set | cell | window | exact cut | exact EQ cut | exact d mean $/wk | first-order cut | first-order EQ cut | first-order d mean |
|---|---|---|---|---|---|---|---|---|
| (no complete window yet) |

## 8. Rate: weekly mean given up per $1k of maxDD cut (WF OOS, equal lots) vs the size-down-everything benchmark
Benchmark (scale Q1-A down by x%: mean and maxDD both fall x%): $118/wk of mean per $1k of maxDD. | family | OOS cut % | OOS $ maxDD cut | d mean $/wk | $ mean per $1k of maxDD | vs benchmark |
|---|---|---|---|---|---|
| interactions (cap/cooldown) | 48.5 | 67996 | -4776 | 70 | cheaper |
| per-book/session scope | 47.0 | 65982 | -2274 | 34 | cheaper |
| stack/book P&L target-vol | 45.2 | 63457 | -3300 | 52 | cheaper |
| vol-skip multiples only (old AB style r_*, lo=0) | 43.8 | 61443 | -7085 | 115 | cheaper |
| composite consensus (all stages comp) | 42.3 | 59369 | -4283 | 72 | cheaper |
| composite pooled scope | 38.6 | 54131 | -4214 | 78 | cheaper |
| ratio step/cont (r_*) | 36.8 | 51680 | -7174 | 139 | dearer |
| event-excluded ref | 35.8 | 50166 | -4971 | 99 | cheaper |
| z-score | 34.1 | 47869 | -3550 | 74 | cheaper |
| graded 3-step | 34.0 | 47747 | -2651 | 56 | cheaper |
| composite graded/half (no zero) | 32.4 | 45492 | -2063 | 45 | cheaper |
| continuous (ref/now)^p | 30.4 | 42684 | -3082 | 72 | cheaper |
| half (lo=.5) steps | 25.0 | 35051 | -1471 | 42 | cheaper |
| ALL B (onQ1A) | 19.3 | 27032 | -7229 | 267 | dearer |
| quantile-adaptive (q_*) | 19.3 | 27032 | -5170 | 191 | dearer |
| session-slot ref | 19.3 | 27032 | -7126 | 264 | dearer |
| special (first/dur/dir/vov/evt) | 17.7 | 24891 | -2208 | 89 | cheaper |

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
- **continuous (ref/now)^p**: measure/feature `r_park1_w10_all40`, shape `cont`, params [2, 0], scope ["pool"], with the ER sizer underneath (onQ1A), down-only. First-order: cut +33/+54/+57 (L6M/PRE/X'), EQ +39/+58/+61, s 0.91, skip 0 %, live week d$ -41810. WF family OOS at the realised equal mean 14.8 %.
- **half (lo=.5) steps**: measure/feature `r_gk1_w10_all60`, shape `step`, params [1.1, 0.5], scope ["pool"], with the ER sizer underneath (onQ1A), down-only. First-order: cut +32/+46/+52 (L6M/PRE/X'), EQ +39/+51/+57, s 0.89, skip 0 %, live week d$ -33836. WF family OOS at the realised equal mean 17.7 %.
- **graded 3-step**: measure/feature `q_park1_w10_all10`, shape `g3`, params [0.6, 0.8], scope ["pool"], with the ER sizer underneath (onQ1A), down-only. First-order: cut +54/+57/+63 (L6M/PRE/X'), EQ +61/+63/+69, s 0.85, skip 37 %, live week d$ -51248. WF family OOS at the realised equal mean 22.4 %.
- **per-book/session scope**: measure/feature `r_ewma5_l90_all40`, shape `step`, params [1.1, 0], scope ["book", "P7", "K7"], with the ER sizer underneath (onQ1A), down-only. First-order: cut +60/+52/+62 (L6M/PRE/X'), EQ +64/+56/+65, s 0.91, skip 39 %, live week d$ -82105. WF family OOS at the realised equal mean 38.6 %.
- composite pooled scope: no cell in the b5 selection (selected by tolerant score; see ledger for TVOL cells).
- stack/book P&L target-vol: no cell in the b5 selection (selected by tolerant score; see ledger for TVOL cells).

Feature key: `r_<measure>_<all|slot><N>` = ratio of the measure to its median over the previous N trading days (`all` = all minutes, `slot` = same half-hour +-15 min); `q_...` = fraction of those reference values below the current value; measures: park1_w10 = Parkinson vol over the last 10 one-minute bars, gk1_wW = Garman-Klass, rv1_wW = realized vol of 1-min returns, atr1_nN = ATR of N one-minute bars, ewma5_l90 = EWMA (lambda .90) of squared 5-min returns, `COMP` = consensus over all 53 measures.

## 11. v1.6 fields needed (none of this exists in D7 v1.5; the v1.5 panel has TrendEr* ER sizer, session lot tables, A06 slots, B02 range filter, StackCutPct/StackAsiaOnly, lock caps and L2 gate stages only)
- VolMeasure (enum: Parkinson, GK, RV1m, RV5m, ATR, EWMA), VolBars (window), VolBarMin (1/5/15), VolRefDays (5-60), VolRefType (all minutes / same half-hour slot), VolRefStat (median ratio / quantile rank), VolMode (continuous / step / graded), VolP, VolFloor, VolBreak1, VolBreak2, VolLoMult1, VolLoMult2, VolBookMask (per-book on/off, e.g. P7+K7), VolWithEr (stack on top of TrendEr or replace), VolEventExclude (FOMC/CPI/NFP days dropped from the norm), VolMaxCap (down-only: never above table lots).
- Rolling per-minute store of the measure for the last 60 trading days (all minutes, plus slot index) so the quantile/median is computed causally at the signal second; engine rounding as above; skip means no entry (the signal is consumed).
- Stack target-vol: StackVolDays (10/15/20), StackVolTargetMult (x expanding median of its own trailing vol), StackVolP, StackVolFloor, from the realised daily P&L of the previous days (per book optional).
- NOT first-order testable here and therefore needing engine work before any claim: delay-and-recheck, equal-$-risk stop widening, sigma-scaled lock caps, vol-governed state-cut arm/persistence.