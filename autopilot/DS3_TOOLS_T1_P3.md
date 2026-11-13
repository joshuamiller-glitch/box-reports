# DS3_TOOLS_T1_P3 — T1 MBO standing program (W-TL1b). Page 3, rebuilt 2026-11-13T05:11Z by code/th_tools/t1_p3_driver.sh every 4 h. Research only, Shadow, no PASS claim.

## 0. Status plain sentence
H5 (iceberg pattern), H6 (queue / passive fill with the real touch and print-through), H7 (learned 5-60 s signed move, distilled to plain conditions, timing only) and H8 (two-event combos) are tested on L3M (78 days, JN05W2 trade list, NOCUT base repeated). See the tables: a flag/condition is called only if it clears placebo + day-block t + repeat across bases; otherwise NULL. Nothing is recommended for live. Data fact the reader needs: NQ.v.0 books in 2026 are THIN: median spread at the signal second 4 ticks (1 point), median queue at the touch 1 lot (orders at touch 1) — verified by an independent dict replay of the raw records (kernel = replay at 9/9 checked seconds). So 'queue position' is mostly a spread question, not a queue question.

## Quotes (quote only, nothing bought; cost per get_cost, billable GB)
- NQ L3M_PRE incremental 2026-05-01..08-01: $153.25 (91.4 GB). Justified only if a feature in H5-H8 shows a sign-consistent L3M effect; none does yet, so NOT requested.
- ES.v.0 MBO 2026-08-01..11-01: $51.19 (44.0 GB); 2026-10-01..11-01: $8.37 (18.4 GB). RTY.v.0 MBO 2026-08-01..11-01: $18.17 (14.7 GB); October only $3.22 (5.8 GB). Cheap enough to run the same H1-H8 on ES/RTY as 'other markets as clues' (widening order); recommend RTY L3M ($18) and ES October ($8) only after the lead agrees.

# Base JN05W2

## H6 queue / passive fill model (resting limit at the own touch at the signal second; JN05W2, L3M, n=1494 fills of the trade list)

Fill within 15 / 30 / 60 / 300 s (volume at/through our touch >= queue ahead + our lots): 77% / 83% / 87% / 94%; median fill time 3 s; median queue at touch 1 lots, median orders at touch 1.

OOS R2 of log(fill time) (train days<55, test days>=56; trades only, small n): MBP-visible only (queue size at touch, spread, 10 s adverse volume, range): +0.095 ; + MBO-only (orders at touch, young-cancel share, 10 s adds, big cancels): +0.042. MBO adds if the second exceeds the first by a margin larger than the noise of ~0.05.

| wait T (s) | passive fill rate | mean value of the rule (ticks per trade; + = better than crossing at the signal) | of which filled | of which chased | missed-winner cost (y30 of chased trades) |
|---|---|---|---|---|---|
| 15 | 77% | -0.05 | +3.65 | -12.28 | +14.18 |
| 30 | 83% | +0.26 | +3.69 | -16.87 | +20.74 |
| 60 | 87% | +0.18 | +3.72 | -23.42 | +23.56 |
Fill model (mbo_feat2 cols 34-36): a resting limit at our own touch price at the signal second is filled when a print trades THROUGH it (lowest sell print < our bid / highest buy print > our ask), or when volume at the touch while the print low/high equals our price covers the queue ahead plus our lots; cancels ahead of us are ignored (conservative); one-second granularity. Engine entry price vs mid at the signal second: median +1.00 ticks (+ = paid above/below mid in the trade direction), mean spread 3.8 ticks (median 4), median queue at touch (lots) by session: all 1
(value for the filled trades = spread saved; for chased trades = cost of the touch moving away during the wait. The crossing alternative is 0 by construction. Ticks x lots x $5 = $ per trade; adverse selection of passive fills = the y30 of filled vs chased: filled -4.01 ticks, chased +20.74 ticks.)

## H5 / H8 / H7-at-entry: flags at the signal second (n=1494 trades; outcomes net of the mean in the trailing-60 s range quintile; day-block t)

| flag | n | fwd30 d (t) | fwd60 d (t) | net $/lot d (t) | placebo p (fwd30, random flags same n, 2000 draws) |
|---|---|---|---|---|---|
| ice_own | 129 | +0.22 (+0.1) | -3.13 (-0.5) | +34.84 (+0.2) | 0.913 |
| ice_opp | 129 | +0.24 (+0.0) | +1.56 (-0.2) | +26.83 (-0.5) | 0.908 |
| pull&sweep | 54 | -1.89 (+0.0) | -4.10 (-0.2) | +213.17 (+1.7) | 0.588 |
| pull&oppadd | 138 | -0.73 (-0.0) | -2.69 (-0.5) | +71.57 (+0.2) | 0.736 |
| oppadd&sweep | 50 | +0.05 (+0.3) | -3.19 (-0.3) | +252.84 (+1.4) | 0.991 |
| bigq(q0>=p80) | 545 | +0.37 (+0.8) | +0.97 (-0.1) | +45.37 (+0.9) | 0.791 |
| smallq(q0<=p20) | 949 | -0.37 (-0.8) | -0.97 (+0.1) | -45.37 (-0.9) | 0.778 |
| learned pred top 20% (favourable) | 299 | -1.63 (-0.5) | -0.88 (-0.3) | -40.54 (-0.8) | 0.314 |
| learned pred bottom 20% (adverse) | 299 | -0.16 (-0.1) | -1.86 (-1.0) | -118.50 (-1.8) | 0.915 |
Family: 27 cells, |t|>=2: 0 (chance ~1.2).

## H7 learned 5-60 s signed mid move (timing only)

Panel: 1389318 rows (every 5th second, 78 days), 31 features (trailing-10 s book-side sums, touch size/count, imbalance, 10/60 s move, range, hour). LightGBM small (num_leaves 8, 200 trees, lr 0.03, min_leaf 2000, monotone off), train on the first 55 days with a 1-day purge, test on the last 22 days; 3 seeds.

| target | OOS corr | OOS R2 | top-decile pred mean (ticks) | bottom-decile | spread | days-in-test sign agreement |
|---|---|---|---|---|---|---|
| y5 | +0.0083 | -0.00012 | +0.130 | -0.227 | +0.357 | 16/22 |
| y30 | +0.0002 | -0.00064 | +0.014 | -0.196 | +0.211 | 14/22 |
| y60 | -0.0034 | -0.00063 | -0.496 | +0.076 | -0.572 | 11/22 |

Top features by gain (y30): mv10 19%, mv60 9%, rv60 9%, modup_a 8%, hour 7%, modaway_a 5%
Distilled plain rule test (3 conditions at most, thresholds from the TRAIN span quintiles, scored on the TEST span, ticks of fwd30 mid move; + = up): 
- mv10>=Q80 & mv60>=Q80: n=47134 mean fwd30 -0.216 (rest -0.172)
- mv10<=Q20 & mv60<=Q20: n=49674 mean fwd30 -0.111 (rest -0.187)
- mv10>=Q80 & mv60<=Q20: n=18894 mean fwd30 -0.354 (rest -0.168)
- mv10<=Q20 & mv60>=Q80: n=18009 mean fwd30 +0.115 (rest -0.191)

# Base JN05W2J_NOCUT

## H6 queue / passive fill model (resting limit at the own touch at the signal second; JN05W2J_NOCUT, L3M, n=1429 fills of the trade list)

Fill within 15 / 30 / 60 / 300 s (volume at/through our touch >= queue ahead + our lots): 78% / 84% / 87% / 94%; median fill time 2 s; median queue at touch 1 lots, median orders at touch 1.

OOS R2 of log(fill time) (train days<55, test days>=56; trades only, small n): MBP-visible only (queue size at touch, spread, 10 s adverse volume, range): +0.095 ; + MBO-only (orders at touch, young-cancel share, 10 s adds, big cancels): +0.061. MBO adds if the second exceeds the first by a margin larger than the noise of ~0.05.

| wait T (s) | passive fill rate | mean value of the rule (ticks per trade; + = better than crossing at the signal) | of which filled | of which chased | missed-winner cost (y30 of chased trades) |
|---|---|---|---|---|---|
| 15 | 78% | -0.02 | +3.60 | -12.64 | +15.58 |
| 30 | 84% | +0.17 | +3.64 | -17.66 | +22.45 |
| 60 | 87% | +0.12 | +3.67 | -24.52 | +26.01 |
Fill model (mbo_feat2 cols 34-36): a resting limit at our own touch price at the signal second is filled when a print trades THROUGH it (lowest sell print < our bid / highest buy print > our ask), or when volume at the touch while the print low/high equals our price covers the queue ahead plus our lots; cancels ahead of us are ignored (conservative); one-second granularity. Engine entry price vs mid at the signal second: median +1.50 ticks (+ = paid above/below mid in the trade direction), mean spread 3.7 ticks (median 4), median queue at touch (lots) by session: all 1
(value for the filled trades = spread saved; for chased trades = cost of the touch moving away during the wait. The crossing alternative is 0 by construction. Ticks x lots x $5 = $ per trade; adverse selection of passive fills = the y30 of filled vs chased: filled -4.02 ticks, chased +22.45 ticks.)

## H5 / H8 / H7-at-entry: flags at the signal second (n=1429 trades; outcomes net of the mean in the trailing-60 s range quintile; day-block t)

| flag | n | fwd30 d (t) | fwd60 d (t) | net $/lot d (t) | placebo p (fwd30, random flags same n, 2000 draws) |
|---|---|---|---|---|---|
| ice_own | 123 | -0.52 (+0.4) | -1.49 (+0.6) | -37.49 (+0.3) | 0.817 |
| ice_opp | 125 | +1.38 (+1.1) | +0.45 (+0.8) | +0.83 (+0.2) | 0.573 |
| pull&sweep | 50 | -4.02 (-0.3) | +3.42 (+0.7) | +190.98 (+1.2) | 0.262 |
| pull&oppadd | 129 | +0.76 (+0.6) | -1.88 (+0.1) | -46.23 (+0.0) | 0.741 |
| oppadd&sweep | 45 | +0.29 (+0.3) | +11.26 (+1.1) | +258.90 (+1.5) | 0.937 |
| bigq(q0>=p80) | 538 | -1.11 (+0.4) | -0.46 (-0.1) | +3.20 (+0.9) | 0.447 |
| smallq(q0<=p20) | 891 | +1.11 (-0.4) | +0.46 (+0.1) | -3.20 (-0.9) | 0.443 |
| learned pred top 20% (favourable) | 286 | -0.87 (+0.5) | -0.10 (+0.5) | +33.17 (+0.2) | 0.604 |
| learned pred bottom 20% (adverse) | 286 | -0.08 (-0.5) | -2.24 (-1.0) | -83.47 (-1.0) | 0.960 |
Family: 27 cells, |t|>=2: 0 (chance ~1.2).

## H7 learned 5-60 s signed mid move (timing only)

Panel: 1389318 rows (every 5th second, 78 days), 31 features (trailing-10 s book-side sums, touch size/count, imbalance, 10/60 s move, range, hour). LightGBM small (num_leaves 8, 200 trees, lr 0.03, min_leaf 2000, monotone off), train on the first 55 days with a 1-day purge, test on the last 22 days; 3 seeds.

| target | OOS corr | OOS R2 | top-decile pred mean (ticks) | bottom-decile | spread | days-in-test sign agreement |
|---|---|---|---|---|---|---|
| y5 | +0.0083 | -0.00012 | +0.130 | -0.227 | +0.357 | 16/22 |
| y30 | +0.0002 | -0.00064 | +0.014 | -0.196 | +0.211 | 14/22 |
| y60 | -0.0034 | -0.00063 | -0.496 | +0.076 | -0.572 | 11/22 |

Top features by gain (y30): mv10 19%, mv60 9%, rv60 9%, modup_a 8%, hour 7%, modaway_a 5%
Distilled plain rule test (3 conditions at most, thresholds from the TRAIN span quintiles, scored on the TEST span, ticks of fwd30 mid move; + = up): 
- mv10>=Q80 & mv60>=Q80: n=47134 mean fwd30 -0.216 (rest -0.172)
- mv10<=Q20 & mv60<=Q20: n=49674 mean fwd30 -0.111 (rest -0.187)
- mv10>=Q80 & mv60<=Q20: n=18894 mean fwd30 -0.354 (rest -0.168)
- mv10<=Q20 & mv60>=Q80: n=18009 mean fwd30 +0.115 (rest -0.191)


# H10 robustness of the aged-opposing-large-order lead (JN05W2, L3M, n=1755 trades, 78 days)

Flag = nearest >=8-lot resting order on the opposing book within DIST ticks of the touch with age > AGE s, at the signal second. d = flagged minus unflagged of range-quintile-residualised outcome; t = day-block; h1/h2 = same-sign in the two halves of the span; perm p on net (2000 random flags of the same n).

| dist | age s | n | days | target d (t) | net $/lot d (t) | net h1 / h2 | perm p |
|---|---|---|---|---|---|---|---|
| 5 | 10 | 24 | 21 | +0.15 (+1.3) | +214.83 (+1.0) | +234 / +197 | 0.308 |
| 5 | 30 | 19 | | too few | | | |
| 5 | 60 | 14 | | too few | | | |
| 5 | 120 | 12 | | too few | | | |
| 5 | 300 | 7 | | too few | | | |
| 8 | 10 | 47 | 34 | +0.25 (+2.9) | +427.52 (+2.6) | +395 / +455 | 0.004 |
| 8 | 30 | 39 | 28 | +0.23 (+2.1) | +371.55 (+1.7) | +267 / +470 | 0.023 |
| 8 | 60 | 29 | 23 | +0.29 (+2.7) | +455.42 (+2.1) | +326 / +558 | 0.015 |
| 8 | 120 | 27 | 22 | +0.31 (+3.0) | +545.80 (+2.6) | +457 / +615 | 0.007 |
| 8 | 300 | 19 | | too few | | | |
| 12 | 10 | 76 | 46 | +0.22 (+3.5) | +406.60 (+3.5) | +414 / +398 | 0.001 |
| 12 | 30 | 64 | 41 | +0.19 (+2.7) | +348.22 (+2.7) | +267 / +405 | 0.009 |
| 12 | 60 | 53 | 35 | +0.23 (+3.7) | +420.91 (+3.7) | +302 / +495 | 0.003 |
| 12 | 120 | 49 | 33 | +0.25 (+3.8) | +478.63 (+4.0) | +437 / +501 | 0.001 |
| 12 | 300 | 33 | 27 | +0.30 (+4.2) | +607.64 (+4.2) | +383 / +750 | 0.000 |
| 20 | 10 | 155 | 55 | +0.10 (+1.0) | +160.41 (+0.8) | +100 / +221 | 0.064 |
| 20 | 30 | 128 | 53 | +0.08 (+0.7) | +132.83 (+0.5) | +77 / +192 | 0.155 |
| 20 | 60 | 107 | 49 | +0.09 (+1.2) | +141.26 (+0.9) | +18 / +273 | 0.169 |
| 20 | 120 | 99 | 45 | +0.10 (+1.4) | +158.39 (+1.1) | +70 / +249 | 0.131 |
| 20 | 300 | 74 | 36 | +0.11 (+2.3) | +191.39 (+2.0) | +56 / +327 | 0.102 |
Family: 30 cells (20 variants x 2 outcomes), |t|>=2: 18 (chance ~1.4; variants overlap, so they are NOT independent evidence).

Lead variant dist<=12, age>60 s: per book (n, mean net $/lot flagged vs rest): A7 4 +729 vs -15; H7 3 +76 vs +133; K7 20 +411 vs +41; M7 9 +711 vs +16; O7 0 +nan vs +299; P7 14 +456 vs +71; U7 3 +405 vs +60
By side: long 29 +300, short 24 +694.
Concentration: flagged trades fall on 35 days; best 3 days carry 28% of the flagged net $ (sum +25353 per lot); median per-flagged-trade +1199 vs mean +478.
Bootstrap 5/50/95% of flagged mean net: [276.0, 484.0, 696.0] ($/lot); unflagged mean +47.

## H10 summary: the one sign-consistent lead (see autopilot/T1_AGED_WALL_PREREG.md, frozen rule + holdout test)
Aged (>60 s) >=8-lot order on the opposing book within 12 ticks at the signal second: n=53 (35 days), net +$421/lot vs +$47, target rate +23 pts (t +3.7 / +3.7), both halves positive, hour-of-day-matched placebo p 0.003, permutation p 0.003, 6/7 books positive, both sides; repeats on JN05W2J_NOCUT (+325, t 2.5). Excess at the user's lots about +$4.4k/week in-sample (selected from a 20-variant grid). Needs the L3M_PRE holdout ($153.25, quoted) to separate from selection.

# H11 trend-week and mechanism checks of the aged-wall lead (JN05W2, L3M, n=1755; flagged 53)

Excess = flagged minus unflagged range-residualised net $/lot within the stratum (placebo/permutation for the whole lead already p 0.003).

## Trend-week / regime strata

| stratum | result |
|---|---|
| trade WITH the 30-min trend (mv30>0) | n=51 vs 1357, excess +418 |
| trade AGAINST the 30-min trend | n=2 (too few) |
| trend day (|day move|/range > median) | n=24 vs 833, excess +438 |
| chop day | n=29 vs 869, excess +417 |
| long | n=29 vs 839, excess +227 |
| short | n=24 vs 863, excess +653 |
| session asia | n=24 vs 727, excess +368 |
| session london | n=11 vs 531, excess +250 |
| session pre | n=2 (too few) |
| session nyam | n=8 vs 174, excess +997 |
| session nypm | n=3 (too few) |
| session close | n=5 vs 130, excess +258 |

## By month and leave-one-month-out

| month | result |
|---|---|
| 2026-08 | n=16 vs 579, excess +156 |
| 2026-09 | n=19 vs 590, excess +424 |
| 2026-10 | n=18 vs 533, excess +660 |
| all but 2026-08 | n=37 vs 1123, excess +538 |
| all but 2026-09 | n=34 vs 1112, excess +419 |
| all but 2026-10 | n=35 vs 1169, excess +300 |

Flagged trades fall in 13 of 14 calendar weeks; the best single week carries 21% of the flagged residual net.

## Presence vs age (is it the wall or its age)

| opposing >=8-lot order within 12 ticks | n | mean net $/lot (residualised) | target rate |
|---|---|---|---|
| none within 12 ticks | 1398 | -23 | 0.42 |
| young (<10 s) | 281 | +9 | 0.42 |
| 10-60 s | 23 | +345 | 0.61 |
| aged (>60 s) | 53 | +408 | 0.66 |

## Mechanism clues

Wall survival (same order still resting within 14 ticks 60 s later): 2% of flagged signals. Net $/lot flagged, wall survived +1199 (n=1) vs consumed/pulled +464 (n=52).
Wall distance (ticks from our touch) among flagged: median 8; target distance of the Target exits among flagged: median 240 ticks; share of flagged Target exits with target farther than the wall (price traded THROUGH the wall): 100%. Wall size median 10 lots (min 8, max 67).
Trade with/against 30-min trend among flagged: with 51, against 2 (all trades: with 80%).
Books among flagged: K7 20, P7 14, M7 9, A7 4, H7 3, U7 3

# H9 (JN05W2, L3M v2): exit timing at zone / order-flow regime at loss / liquidity map at entry

### A. Target-zone approach (first second favourable excursion >= 16 ticks; one sample per trade, n=1358); hold = exit price minus mid now, ticks (+ = holding beats taking now, - = a take now would have been better)

Flagged vs unflagged; MBO state at the approach second vs the real outcome of the live exit.

| flag | n | hold d (t) | fwd120 d (t) | mae30 d (t) | placebo p (hold) |
|---|---|---|---|---|---|
| opp large order within 5 ticks ahead | 66 | +10.69 (+1.1) | +2.15 (+1.0) | +2.04 (+0.6) | 0.673 |
| opp large within 12 ticks (nearest) | 164 | -4.29 (+0.8) | +4.10 (+0.4) | +0.53 (+0.5) | 0.803 |
| adv_flow (absorbed) | 0 | too few | | |
| adv_flow_mv (sweep through) | 0 | too few | | |
| own_pull | 136 | +11.87 (+0.2) | +7.20 (+0.4) | -6.92 (-1.1) | 0.534 |
| opp_add | 136 | -4.87 (-0.7) | +5.96 (+0.1) | -8.60 (-1.9) | 0.778 |
| qdep | 329 | +4.15 (-0.2) | -4.78 (-1.7) | +0.07 (-0.0) | 0.744 |
| flick | 137 | -12.62 (+0.2) | -11.31 (-2.2) | -8.16 (-2.3) | 0.497 |
Family: 18 cells, |t|>=2: 2 (chance ~0.8).

### B. Per-minute order-flow regime at the loss state (first second unrealised <= -16 ticks, n=1385); hold = exit minus mid now (- = cut now would have been better)

cancel-to-trade (c2t), mean order lifetime (life), young-cancel share, big-cancel share, touch depth, efficiency |move|/range over the last 60 s (trend = high eff).

| flag | n | hold d (t) | fwd120 d (t) | mae30 d (t) | placebo p (hold) |
|---|---|---|---|---|---|
| c2t top decile | 139 | +3.64 (-0.5) | -4.20 (-1.2) | -0.08 (-0.7) | 0.827 |
| c2t bottom decile | 139 | +16.33 (+0.2) | +7.71 (+1.5) | +1.86 (-0.2) | 0.363 |
| life top decile | 139 | +8.52 (+0.6) | -4.07 (-1.0) | +1.31 (+0.8) | 0.638 |
| life bottom decile | 139 | -8.29 (-0.7) | +5.75 (+0.5) | -1.81 (-0.8) | 0.643 |
| young top decile | 139 | +8.95 (+1.4) | +6.28 (+0.5) | -6.30 (-2.1) | 0.639 |
| young bottom decile | 139 | -21.56 (-1.2) | +1.82 (+0.2) | +0.65 (+0.1) | 0.214 |
| bigshare top decile | 1385 | too few | | |
| bigshare bottom decile | 1264 | +14.97 (+0.5) | +13.64 (+2.0) | +0.62 (-0.8) | 0.437 |
| depth top decile | 202 | +5.25 (-0.6) | +2.99 (+0.1) | +0.76 (+0.4) | 0.736 |
| depth bottom decile | 504 | +13.88 (+0.9) | -1.29 (-0.1) | -0.21 (+0.0) | 0.206 |
| eff top decile | 140 | +26.21 (+1.8) | +0.33 (+0.3) | +2.04 (+1.1) | 0.125 |
| eff bottom decile | 139 | -4.85 (+0.0) | +5.79 (+1.5) | -2.10 (-0.8) | 0.778 |
Family: 33 cells, |t|>=2: 1 (chance ~1.5).

### C. Liquidity map at the entry second (n=1754): nearest >=8-lot resting order ahead (resistance for a long) / behind (support); outcomes net of range quintile: mfe, mae over the trade (ticks), target reached, net $/lot

Use: target in front of a wall / stop behind support. A wall ahead should lower mfe and target-reach; support behind should lower |mae|.

| flag | n | mfe d (t) | mae d (t) | target d (t) | net d (t) | placebo p (mfe) |
|---|---|---|---|---|---|---|
| opp large (>=8) within 12 ticks ahead | 357 | -22.82 (+2.2) | +28.42 (+0.9) | +0.06 (+1.4) | +113.15 (+1.5) | 0.000 |
| opp large within 5 ticks | 44 | +19.31 (+1.4) | -1.50 (+0.4) | +0.10 (+0.9) | +174.98 (+0.7) | 0.146 |
| own large (support) within 12 ticks behind | 306 | -34.60 (+0.2) | +30.16 (+0.1) | +0.03 (+0.7) | +65.81 (+0.7) | 0.000 |
| opp large aged >60 s (survivor) ahead | 53 | +44.72 (+3.5) | +2.76 (+0.5) | +0.23 (+3.7) | +420.29 (+3.7) | 0.000 |
Family: 16 cells, |t|>=2: 4 (chance ~0.7).

### D. Queue ahead at our touch at the signal (the cancel-ahead question)

queue at own touch (lots) percentiles 10/50/90/99: [0.0, 1.0, 2.0, 5.0] ; orders at touch: [0.0, 1.0, 2.0, 4.0] ; share of signals with queue ahead <= 2 lots: 90%. With one order typically ahead, queue position is binary (that order cancels or trades), so a per-order cancel-ahead model is first-order only for the 2% of signals with >=5 lots ahead.


# H9 (JN05W2J_NOCUT, L3M v2): exit timing at zone / order-flow regime at loss / liquidity map at entry

### A. Target-zone approach (first second favourable excursion >= 16 ticks; one sample per trade, n=1328); hold = exit price minus mid now, ticks (+ = holding beats taking now, - = a take now would have been better)

Flagged vs unflagged; MBO state at the approach second vs the real outcome of the live exit.

| flag | n | hold d (t) | fwd120 d (t) | mae30 d (t) | placebo p (hold) |
|---|---|---|---|---|---|
| opp large order within 5 ticks ahead | 69 | -8.93 (+0.6) | +0.06 (+0.5) | +2.34 (+1.0) | 0.739 |
| opp large within 12 ticks (nearest) | 167 | -25.31 (-0.3) | +2.57 (+0.8) | +1.46 (+1.4) | 0.171 |
| adv_flow (absorbed) | 0 | too few | | |
| adv_flow_mv (sweep through) | 0 | too few | | |
| own_pull | 133 | +0.56 (+0.1) | -0.44 (-0.0) | -9.17 (-1.4) | 0.973 |
| opp_add | 133 | -8.09 (-0.2) | +0.40 (+0.1) | -9.77 (-1.9) | 0.713 |
| qdep | 320 | +4.22 (-0.4) | -4.29 (-1.1) | +0.36 (+0.3) | 0.763 |
| flick | 133 | +14.83 (+1.8) | -7.67 (-1.0) | -7.13 (-1.9) | 0.462 |
Family: 18 cells, |t|>=2: 0 (chance ~0.8).

### B. Per-minute order-flow regime at the loss state (first second unrealised <= -16 ticks, n=1330); hold = exit minus mid now (- = cut now would have been better)

cancel-to-trade (c2t), mean order lifetime (life), young-cancel share, big-cancel share, touch depth, efficiency |move|/range over the last 60 s (trend = high eff).

| flag | n | hold d (t) | fwd120 d (t) | mae30 d (t) | placebo p (hold) |
|---|---|---|---|---|---|
| c2t top decile | 133 | +24.49 (+0.6) | +1.71 (+0.2) | -0.23 (-0.5) | 0.225 |
| c2t bottom decile | 133 | +13.54 (-0.8) | +9.01 (+1.7) | +1.68 (-0.2) | 0.507 |
| life top decile | 133 | +30.26 (+1.1) | -4.16 (-1.5) | +1.50 (+1.2) | 0.124 |
| life bottom decile | 133 | +13.35 (-0.3) | +8.21 (+0.7) | -1.28 (-0.7) | 0.522 |
| young top decile | 133 | -4.90 (+0.4) | +8.09 (+1.4) | -7.15 (-2.3) | 0.808 |
| young bottom decile | 133 | -23.07 (-1.3) | +1.87 (-0.4) | +0.99 (+0.5) | 0.268 |
| bigshare top decile | 1330 | too few | | |
| bigshare bottom decile | 1204 | +20.55 (+0.6) | +12.66 (+1.4) | -1.14 (-1.2) | 0.343 |
| depth top decile | 197 | -23.04 (-2.0) | -0.24 (-0.5) | +0.42 (+0.2) | 0.186 |
| depth bottom decile | 481 | +25.05 (+1.3) | +2.14 (+0.2) | +0.52 (+0.4) | 0.048 |
| eff top decile | 134 | +38.37 (+2.6) | +0.94 (+0.2) | +2.13 (+0.6) | 0.054 |
| eff bottom decile | 133 | +12.77 (+1.2) | +5.40 (+1.6) | -2.19 (-0.7) | 0.548 |
Family: 33 cells, |t|>=2: 2 (chance ~1.5).

### C. Liquidity map at the entry second (n=1642): nearest >=8-lot resting order ahead (resistance for a long) / behind (support); outcomes net of range quintile: mfe, mae over the trade (ticks), target reached, net $/lot

Use: target in front of a wall / stop behind support. A wall ahead should lower mfe and target-reach; support behind should lower |mae|.

| flag | n | mfe d (t) | mae d (t) | target d (t) | net d (t) | placebo p (mfe) |
|---|---|---|---|---|---|---|
| opp large (>=8) within 12 ticks ahead | 295 | -37.96 (+0.4) | +40.18 (+0.2) | +0.03 (+0.3) | +33.18 (-0.1) | 0.000 |
| opp large within 5 ticks | 34 | +3.57 (+0.3) | -5.22 (-0.0) | -0.04 (+0.1) | -62.10 (-0.1) | 0.823 |
| own large (support) within 12 ticks behind | 261 | -45.75 (-0.3) | +44.88 (+0.5) | +0.03 (+0.1) | +46.11 (+0.1) | 0.000 |
| opp large aged >60 s (survivor) ahead | 47 | +36.76 (+2.6) | +14.79 (+1.3) | +0.16 (+2.7) | +324.81 (+2.5) | 0.004 |
Family: 16 cells, |t|>=2: 3 (chance ~0.7).

### D. Queue ahead at our touch at the signal (the cancel-ahead question)

queue at own touch (lots) percentiles 10/50/90/99: [0.0, 1.0, 2.0, 5.0] ; orders at touch: [0.0, 1.0, 2.0, 4.0] ; share of signals with queue ahead <= 2 lots: 90%. With one order typically ahead, queue position is binary (that order cancels or trades), so a per-order cancel-ahead model is first-order only for the 2% of signals with >=5 lots ahead.


# FROZEN HOLDOUT: aged-wall rule on L3M_PRE (/mnt/l2/l2vast/_tools/t1/l3m_pre_v2 .. ; n=2120 trades, 79 days, flagged 45 on 28 days)

- net_r: flagged minus unflagged +276.209, day-block t +2.04, halves ['+287.996', '+264.811'], permutation p 0.072
- tgt_r: flagged minus unflagged +0.130, day-block t +1.99, halves ['+0.126', '+0.140'], permutation p 0.096
- raw net $/lot flagged +368 vs rest +82; target rate flagged 0.58 vs rest 0.44; flagged trades/week 2.8

PRE-REGISTERED CRITERION (d_net>0 AND t>=2 AND d_target>0 AND both halves positive, n>=15): MET.
VERDICT IN PLAIN WORDS: the lead replicated out of sample.

## Live path and cost quote for the aged-wall lead (quote only; nothing subscribed; prices from databento.com/pricing and its blog, fetched 2026-11-13, need confirmation with Databento sales)
The feature needs, per second at the signal, the age and distance of the largest resting order per side = order-ID (MBO / L3) state, kept by a Python sidecar and written to a file/socket D7 reads (feature names: opp_wall_dist, opp_wall_age_s, opp_wall_size; update 1 Hz, state maintained event by event). NT8 OnMarketDepth is price-level, so it cannot supply order age.
Why our plan cannot do it: our Databento entitlement is the historical/usage side; live CME MBO is not entitled. What an entitlement would need (as published): CME live data is subscription-only since 2025-04 (usage-based live CME discontinued). Standard plan $199/month ($179 if grandfathered), but L2/L3 appear to have been removed from Standard (user report on Databento's roadmap site; the pricing page layout does not show it) — treat as NOT included. Plus: $1,750/month plan fee plus $1,750/month licence fee (annual contract, contact sales; dedicated connectivity); Unlimited $4,500 + $4,500/month (annual). Live MBO inclusion for Plus/Unlimited must be confirmed in writing; CME professional-vs-non-professional licence class also changes the fee (not shown on the page). Rough cost if Plus: about $3,500/month = about $810/week plus engineering for the sidecar.
Break-even: the lead's in-sample excess is about $4.4k/week at the user's lots (selected from a 20-variant grid; will be shrunk by the holdout). It would pay Plus ($810/week) if at least ~20% of it survives; it does not pay for the Standard-plan class of price if MBO is not in it. Alternatives to quote if the holdout holds: another CME data vendor with MBO live (not checked), or CME direct. Decision waits for the frozen holdout (L3M_PRE).
Sources: https://databento.com/pricing ; https://databento.com/blog/introducing-new-cme-pricing-plans ; https://databento.com/blog/updates-to-subscription-pricing ; https://roadmap.databento.com/b/n0o5prm6/feature-ideas/service-distrubtion


## Next (never empty)
H9 ES/RTY MBO (after approval), per-order cancel-ahead queue model (needs per-price order-level state: kernel extension), exit timing at target zone (item 4), liquidity map levels (item 5), order-flow regime per minute (item 6). Hypothesis log autopilot/T1_HYPOTHESIS_LOG.md.
