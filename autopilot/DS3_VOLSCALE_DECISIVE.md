# DS3_VOLSCALE_DECISIVE - decisive test of A3's stack-level vol-scaler (L8, 0.5-2.0, feed ON and OFF) and its 12-cell neighbourhood (A8, 2026-11-01). Frozen definitions, post-hoc consistency test, SHADOW ONLY, no PASS

Prereg `l2vast/ds3/prereg/VOLSCALE_DECISIVE_prereg.md` sha256 `ab651eaa164b0702e7c7135a2c3272d94184f30e899904bec6a2600adf590308` (in DECISIONS.md before any statistic; dead_lookup first: VS01, L4, L13 and the per-book cell are EXACT in A3SZ = a frozen-definition re-test of an already-scored post-hoc lead; clips 0.5-1.5 / 0.25-2.0 and the daily update were NOT FOUND; append_cells after). Code `l2vast/ds3/code/volscale_decisive/`, results `l2vast/ds3/out/volscale_decisive/`. Engine = DS3_ONE_CONVENTION through dd_lib/a3_lib unchanged (live lots, parity stop, K6 70/30, running max, integer half-up min-1 lots, multiplier only through mer_fn; VS01 ties to A3 to 0.0). Masks capped 20260206, no post-cap file opened. Windows L3M 14 / L6M 28 / HOLD 32 / PRE 75 / X' 44 / ALL 149 weeks; units $k per week unless stated. **Integrity:** A3 saw L6M/HOLD and selected the variant for Shadow after PRE; PRE and ALL are one 241k episode (2024-08-19..09-30); the HOLD/L6M look is A3's, so this is a consistency test, not a holdout. Nothing here is a PASS.

## Page 1 - the table (all 12 prereg cells; every maxDD change is vs the cell's own baseline: COMP for feed ON, COMPnf for feed OFF)

| cell | maxDD $k before→after: L6M · HOLD · PRE · X' · ALL [95% stationary-bootstrap CI of the % change: PRE; ALL] | worst-20 ALL $k before→after [PRE] | mean change L6M (MDE) · ALL (MDE) | equal-risk mean change (c) L6M · ALL | placebo rank ALL / L6M (n draws) | LOEO (5 singles; all five removed) | lag in weeks | RISK-KEEP (user def.: cut>=20% with mean inside MDE) | D6 mapping |
|---|---|---|---|---|---|---|---|---|---|
| VS01 L8 c0.5-2.0 stack weekly, feed ON | 22.9→24.7 · 97.0→73.1 · 241.2→133.8 · 120.5→120.5 · 241.2→133.8 [PRE -49%..-12%; ALL -47%..+1%] | -1098.1→-889.1 [-875.2→-637.7] | -3.9 (6.3) · -2.6 (3.3) | 1.7 · 0.9 (c 1.18) | 100% / 50% (1000) | 5/5; all five: +2% | 4/5 pre-positioned (m<=0.9 at the first losing week); in-episode reaction: 1/5 (lag 3 wk) | **PRE/ALL cut only (L6M: NO)**; strict gates fail: G3, G4, G6, G7, G8 | weekly stack m, section 7 |
| VS02 L8 c0.5-2.0 stack weekly, feed OFF | 38.5→38.5 · 80.0→75.9 · 225.4→140.1 · 89.1→89.1 · 225.4→140.1 [PRE -52%..+13%; ALL -46%..+12%] | -985.3→-870.3 [-801.3→-674.2] | -1.5 (6.7) · 0.3 (3.7) | 5.6 · 2.3 (c 1.10) | 98% / 19% (1000) | 5/5; all five: +10% | 4/5 pre-positioned (m<=0.9 at the first losing week); in-episode reaction: 1/5 (lag 3 wk) | **PRE/ALL cut only (L6M: NO)**; strict gates fail: G4, G7, G8 | weekly stack m, section 7 |
| VS03 L4 (stack, ON) | 22.9→26.1 · 97.0→88.0 · 241.2→150.6 · 120.5→120.5 · 241.2→150.6 [PRE -41%..-2%; ALL -38%..+7%] | -1098.1→-942.5 [-875.2→-672.8] | -7.1 (6.7) · -3.4 (3.4) | 2.2 · 0.4 (c 1.20) | 94% / 27% (300) | 5/5; all five: -6% | 4/5 pre-positioned (m<=0.9 at the first losing week); in-episode reaction: 0/5 (lag n/a wk) | **PRE/ALL cut only (L6M: NO)**; strict gates fail: G2, G3, G4, G5, G8 | - |
| VS04 L13 (stack, ON) | 22.9→26.1 · 97.0→95.5 · 241.2→157.7 · 120.5→120.5 · 241.2→157.7 [PRE -38%..-3%; ALL -36%..+3%] | -1098.1→-958.9 [-875.2→-694.7] | -3.7 (5.9) · -2.7 (2.7) | 1.5 · 0.2 (c 1.18) | 95% / 26% (300) | 5/5; all five: +1% | 3/5 pre-positioned (m<=0.9 at the first losing week); in-episode reaction: 1/5 (lag 3 wk) | **PRE/ALL cut only (L6M: NO)**; strict gates fail: G3, G4, G5, G7, G8 | - |
| VS05 clip 0.5-1.5 (ON) | 22.9→24.7 · 97.0→73.1 · 241.2→133.8 · 120.5→120.5 · 241.2→133.8 [PRE -49%..-12%; ALL -47%..+1%] | -1098.1→-889.1 [-875.2→-637.7] | -3.9 (6.3) · -2.6 (3.3) | 1.7 · 0.9 (c 1.18) | 100% / 46% (300) | 5/5; all five: +2% | 4/5 pre-positioned (m<=0.9 at the first losing week); in-episode reaction: 1/5 (lag 3 wk) | **PRE/ALL cut only (L6M: NO)**; strict gates fail: G3, G4, G7, G8 | - |
| VS06 clip 0.25-2.0 (ON) | 22.9→24.7 · 97.0→73.1 · 241.2→133.8 · 120.5→120.5 · 241.2→133.8 [PRE -49%..-12%; ALL -47%..+1%] | -1098.1→-889.1 [-875.2→-637.7] | -3.9 (6.3) · -2.6 (3.3) | 1.7 · 0.9 (c 1.18) | 100% / 50% (1000) | 5/5; all five: +2% | 4/5 pre-positioned (m<=0.9 at the first losing week); in-episode reaction: 1/5 (lag 3 wk) | **PRE/ALL cut only (L6M: NO)**; strict gates fail: G3, G4, G7, G8 | - |
| VS07 per-book L8 (ON) | 22.9→24.0 · 97.0→80.7 · 241.2→162.3 · 120.5→120.5 · 241.2→162.3 [PRE -41%..-7%; ALL -37%..+0%] | -1098.1→-946.2 [-875.2→-724.4] | -7.3 (6.4) · -3.4 (3.0) | 0.1 · 0.2 (c 1.17) | 93% / 55% (300) | 5/5; all five: -9% | 0/5 pre-positioned (m<=0.9 at the first losing week); in-episode reaction: 0/5 (lag n/a wk) | **NO** (fails G2, G4, G5, G8) | - |
| VS08 daily update, 40 days (ON) | 22.9→24.7 · 97.0→87.2 · 241.2→130.8 · 120.5→120.5 · 241.2→130.8 [PRE -48%..-10%; ALL -46%..+3%] | -1098.1→-921.7 [-875.2→-648.2] | -4.2 (5.7) · -3.2 (3.0) | 1.2 · 0.3 (c 1.17) | 100% / 41% (300) | 5/5; all five: -1% | 4/5 pre-positioned (m<=0.9 at the first losing week); in-episode reaction: 1/5 (lag 2 wk) | **NO** (fails G2, G3, G4, G8) | - |
| VS09 L4 (OFF) | 38.5→19.6 · 80.0→79.2 · 225.4→197.7 · 89.1→89.1 · 225.4→197.7 [PRE -38%..+27%; ALL -35%..+22%] | -985.3→-903.1 [-801.3→-718.6] | -1.7 (9.2) · -0.1 (4.2) | 5.9 · 1.9 (c 1.10) | 46% / 73% (300) | 4/5; all five: +12% | 4/5 pre-positioned (m<=0.9 at the first losing week); in-episode reaction: 0/5 (lag n/a wk) | **NO** (fails G1, G4, G5, G7, G8) | - |
| VS10 L13 (OFF) | 38.5→38.5 · 80.0→82.3 · 225.4→193.6 · 89.1→89.1 · 225.4→193.6 [PRE -40%..+19%; ALL -35%..+16%] | -985.3→-926.8 [-801.3→-736.1] | -1.3 (6.5) · 0.3 (3.3) | 2.3 · 1.5 (c 1.08) | 87% / 20% (300) | 4/5; all five: +8% | 3/5 pre-positioned (m<=0.9 at the first losing week); in-episode reaction: 1/5 (lag 3 wk) | **NO** (fails G1, G4, G5, G7, G8) | - |
| VS11 clip 0.5-1.5 (OFF) | 38.5→38.5 · 80.0→75.9 · 225.4→140.1 · 89.1→89.1 · 225.4→140.1 [PRE -52%..+13%; ALL -46%..+12%] | -985.3→-870.3 [-801.3→-674.2] | -1.5 (6.7) · 0.3 (3.7) | 5.6 · 2.3 (c 1.10) | 99% / 19% (300) | 5/5; all five: +10% | 4/5 pre-positioned (m<=0.9 at the first losing week); in-episode reaction: 1/5 (lag 3 wk) | **PRE/ALL cut only (L6M: NO)**; strict gates fail: G4, G7, G8 | - |
| VS12 clip 0.25-2.0 (OFF) | 38.5→38.5 · 80.0→75.9 · 225.4→140.1 · 89.1→89.1 · 225.4→140.1 [PRE -52%..+13%; ALL -46%..+12%] | -985.3→-870.3 [-801.3→-674.2] | -1.5 (6.7) · 0.3 (3.7) | 5.6 · 2.3 (c 1.10) | 99% / 19% (300) | 5/5; all five: +10% | 4/5 pre-positioned (m<=0.9 at the first losing week); in-episode reaction: 1/5 (lag 3 wk) | **PRE/ALL cut only (L6M: NO)**; strict gates fail: G4, G7, G8 | - |

**Plain sentence.** The stack-level vol-scaler is a real but single-episode drawdown cut, not a hedge, and its mean cost is a de-leverage cost. VS01 (L8, 0.5-2.0, stack, weekly, feed ON) takes maxDD 241.2→133.8k (-45%) in PRE and ALL (the same 7-week 2024-08/09 path), worst-20 ALL -1,098→-889k, SD -7.6k/wk, Calmar 0.09→0.15, at a mean of -2.6k/wk (MDE 3.3, CI [-4.9, -0.4]); L6M maxDD 22.9→24.7k (+8%) with mean -3.9k (MDE 6.3); X' unchanged by construction (the 16-week warm-up covers the 2023 drawdown). **Beats placebo:** 0 of 1,000 AR(1)-matched random multiplier paths (same mean, dispersion, autocorrelation) cut as much (median placebo cut -15%, p 0.001, Holm over the 12 cells 0.012; over A3's 52 cells 0.052) and a uniform 13.6% lot trim cuts 14%. **Does not survive:** with the 241k episode removed the cut is -18% of the 156k remainder, with the top five removed the maxDD is +2% (79.6→81.3k); the ALL bootstrap CI of the change is [-47%, +1%] (PRE [-49%, -12%]). **Why:** it is not de-levering after the first bad weeks; the multiplier is a state (0.66 at the first losing week of the 241k episode, pushed down by two big winning weeks), it does not fall after a bad week (9 weeks below -1 SD: 1.00 at +1, 1.02 at +2, 1.07-1.08 at +5/+6 weeks), shifting the path by 1-2 weeks in either direction leaves -40..-45% while 8 weeks leaves the uniform-trim -14%, and the trailing SD barely predicts the next week (corr of m with |P&L| -0.03; worst-20 weeks have m 0.83 vs 0.89 mean). The HOLD failure of B2 is NOT repaired, it is avoided by luck of sample and by not lot-matching: lot-matched, VS01 is -17% in HOLD but +46% in L6M, and calm-then-shock simulations deepen maxDD in 79-90% of paths (m 1.57 at the shock start). **Feed OFF twin VS02:** ALL -38% (225.4→140.1k), L6M 0%, mean -1.5 / +0.3k, placebo rank 98% (p 0.021, Holm 0.126 fails), CI PRE [-52%, +13%]. **Neighbourhood:** L4 / L13 / per-book / daily / clip variants cut ALL 33-46% but L4 and per-book breach the L6M mean MDE; the clip never binds (m 0.60-1.55), so VS05/VS06 are VS01. **Equal-risk** (lots x1.18 to restore the ALL worst-20): mean +0.9k ALL, +1.7k L6M (inside MDE), so nothing is gained or lost in edge. **RISK-KEEP (user definition: cut >= 20% with the mean inside its MDE): YES for VS01 and VS02 on PRE/ALL only, NO on the L6M reading; strict gates failed by VS01: G3 (L6M +8%), G4 (PRE and X' agree: X' 0%), G6 (timing), G7 (LOEO, all five removed), G8 (ALL bootstrap CI reaches +1%). Shadow only, no stack change.**


## 1. Per-episode table: the composite's top-10 drawdown episodes (ALL weekly path, peak to new high) and the multiplier path

Episode = weekly cumulative P&L from a peak to the next new high; `depth` = baseline peak-to-trough; `after span` = the cell's P&L over the SAME weeks (peak to the baseline trough; negative = loss); `m path` = multiplier in force for weeks (peak-2 .. trough), the first two entries are before the first losing week; `lag95` = weeks from the first losing week until m first falls to 0.95 x its first-week value (blank = never inside the episode); `pre-pos` = share of the cut explained by the multiplier already in force at the first losing week, (1-m_first) x depth / (depth - |after span|).

**VS01 (L8 c0.5-2.0 stack weekly, feed ON)**

| ep | start..trough (ISO wk) | wks | depth $k | after span $k | cell dd in window $k | after/before | m prior wk | m first loss wk | m min | m path | lag95 | pre-pos share |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 202434..202440 | 7 | 241.2 | -133.1 | 133.8 | 0.55 | 0.70 | 0.66 | 0.60 | 0.70 0.70 0.66 0.65 0.63 0.60 0.61 0.64 0.71 | 3 | 0.76 |
| 2 | 202411..202415 | 5 | 156.4 | -128.0 | 128.0 | 0.82 | 0.84 | 0.81 | 0.81 | 0.83 0.84 0.81 0.85 0.84 0.84 0.83 |  | 1.04 |
| 3 | 202314..202320 | 7 | 120.5 | -120.5 | 120.5 | 1.00 | nan | 1.00 | 1.00 | 1.00 1.00 1.00 1.00 1.00 1.00 1.00 |  |  |
| 4 | 202528..202530 | 3 | 97.0 | -73.1 | 73.1 | 0.75 | 0.76 | 0.80 | 0.80 | 0.75 0.76 0.80 0.88 0.90 |  | 0.80 |
| 5 | 202506..202509 | 4 | 95.7 | -61.3 | 61.3 | 0.64 | 0.76 | 0.65 | 0.63 | 0.86 0.76 0.65 0.63 0.63 0.65 |  | 0.98 |
| 6 | 202405..202407 | 3 | 79.6 | -68.3 | 68.3 | 0.86 | 0.95 | 0.93 | 0.93 | 1.07 0.95 0.93 1.04 0.95 |  | 0.51 |
| 7 | 202351..202351 | 1 | 65.7 | -81.3 | 81.3 | 1.24 | 1.23 | 1.25 | 1.25 | 1.43 1.23 1.25 |  |  |
| 8 | 202524..202524 | 1 | 57.9 | -41.3 | 41.3 | 0.71 | 0.85 | 0.82 | 0.82 | 0.81 0.85 0.82 |  | 0.62 |
| 9 | 202346..202347 | 2 | 56.5 | -65.6 | 65.6 | 1.16 | 1.12 | 1.23 | 1.23 | 1.12 1.12 1.23 1.33 |  |  |
| 10 | 202516..202516 | 1 | 50.2 | -37.8 | 37.8 | 0.75 | 0.79 | 0.82 | 0.82 | 0.86 0.79 0.82 |  | 0.74 |

**VS02 (L8 c0.5-2.0 stack weekly, feed OFF)**

| ep | start..trough (ISO wk) | wks | depth $k | after span $k | cell dd in window $k | after/before | m prior wk | m first loss wk | m min | m path | lag95 | pre-pos share |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 202434..202440 | 7 | 225.4 | -140.1 | 140.1 | 0.62 | 0.70 | 0.66 | 0.60 | 0.70 0.70 0.66 0.65 0.63 0.60 0.61 0.64 0.71 | 3 | 0.90 |
| 2 | 202411..202415 | 5 | 142.5 | -128.1 | 128.1 | 0.90 | 0.84 | 0.81 | 0.81 | 0.83 0.84 0.81 0.85 0.84 0.84 0.83 |  |  |
| 3 | 202314..202320 | 7 | 89.1 | -89.1 | 89.1 | 1.00 | nan | 1.00 | 1.00 | 1.00 1.00 1.00 1.00 1.00 1.00 1.00 |  |  |
| 4 | 202528..202530 | 3 | 80.0 | -75.9 | 75.9 | 0.95 | 0.76 | 0.80 | 0.80 | 0.75 0.76 0.80 0.88 0.90 |  |  |
| 5 | 202523..202524 | 2 | 79.1 | -38.0 | 41.1 | 0.48 | 0.81 | 0.85 | 0.82 | 0.76 0.81 0.85 0.82 |  | 0.29 |
| 6 | 202506..202508 | 3 | 72.1 | -42.9 | 70.3 | 0.60 | 0.76 | 0.65 | 0.63 | 0.86 0.76 0.65 0.63 0.63 |  | 0.87 |
| 7 | 202351..202351 | 1 | 65.7 | -79.6 | 79.6 | 1.21 | 1.23 | 1.25 | 1.25 | 1.43 1.23 1.25 |  |  |
| 8 | 202346..202347 | 2 | 58.2 | -48.1 | 48.1 | 0.83 | 1.12 | 1.23 | 1.23 | 1.12 1.12 1.23 1.33 |  |  |
| 9 | 202424..202426 | 3 | 45.4 | -38.7 | 38.7 | 0.85 | 0.77 | 0.77 | 0.77 | 0.74 0.77 0.77 1.00 1.11 |  |  |
| 10 | 202409..202409 | 1 | 42.8 | -28.4 | 28.4 | 0.66 | 0.92 | 0.83 | 0.83 | 0.95 0.92 0.83 |  | 0.52 |

Reading: the multiplier is a state, not a reaction. In the top-10 episodes the first-losing-week multiplier is 0.65-1.25; the 7 episodes entered with m<0.95 (high trailing vol before the peak) lose 0.73 x the baseline loss on average (the 241k episode: m 0.66, after/before 0.55), the 2 entered with m>=1.1 (calm before the peak: episodes 7, 9) lose 1.20 x (deeper than the baseline). Inside an episode m moves at most 9% after the first losing week, so the answer to 'is it simply de-levering after the first bad weeks?' is NO. In the 241k episode the multiplier fell 0.88 -> 0.70 in 2024-W32, the week after two large WINS (+133k and +102k in W31/W32) inflated the trailing SD (the SD is symmetric), i.e. BEFORE the first losing week (W34 -10k, W35 -19k, W36 -76k); 43% of the baseline depth was incurred by the third losing week and 72% by the fourth while m moved 0.66 -> 0.63-0.65 (-4%); the first 5% fall below its first-week value came in the fourth losing week (lag95 = 3 weeks; m 0.60, its minimum), when 72% of the depth was already incurred. Over the 9 weeks worse than -1 SD (after the warm-up) the multiplier is unchanged at +1 week (1.00), 1.02 at +2 and 1.07-1.08 at +5/+6 weeks, so the typical reaction lag is longer than the episodes. Episode 3 (2023) lies in the 16-week warm-up (m=1.0) and gets no help. The cut is therefore a bet that a stretch of large weeks (of either sign) is followed by losses; section 6 measures how weak that persistence is (corr of m with the next week's |P&L| = -0.03).

## 2. Leave-one-episode-out (top-5 episodes of the baseline ALL path removed singly and all five; the same weeks removed from both series; survive = dMaxDD<0, worst-20 better, cut>=10%)

**VS01** ALL window (PRE-window version in parentheses)

| removed | maxDD before | after | change | worst-20 change | survives | (PRE window: change · survives) |
|---|---|---|---|---|---|---|
| none | 241.2 | 133.8 | -45% | 209.0 | yes | -45% · yes |
| ep1 | 156.4 | 128.0 | -18% | 114.3 | yes | -18% · yes |
| ep2 | 241.2 | 133.8 | -45% | 186.9 | yes | -45% · yes |
| ep3 | 241.2 | 133.8 | -45% | 229.4 | yes | -45% · yes |
| ep4 | 241.2 | 133.8 | -45% | 180.7 | yes | -45% · yes |
| ep5 | 241.2 | 133.8 | -45% | 193.2 | yes | -45% · yes |
| all top-5 | 79.6 | 81.3 | +2% | 35.1 | no | -18% · yes |

**VS02** ALL window (PRE-window version in parentheses)

| removed | maxDD before | after | change | worst-20 change | survives | (PRE window: change · survives) |
|---|---|---|---|---|---|---|
| none | 225.4 | 140.1 | -38% | 114.9 | yes | -38% · yes |
| ep1 | 142.5 | 128.1 | -10% | 64.3 | yes | -10% · yes |
| ep2 | 225.4 | 140.1 | -38% | 94.9 | yes | -38% · yes |
| ep3 | 225.4 | 140.1 | -38% | 120.1 | yes | -38% · yes |
| ep4 | 225.4 | 140.1 | -38% | 107.2 | yes | -38% · yes |
| ep5 | 225.4 | 140.1 | -38% | 90.9 | yes | -38% · yes |
| all top-5 | 72.1 | 79.6 | +10% | -15.8 | no | +85% · no |

## 3. Placebo family (1,000 draws for VS01 and VS02, 300 for the other cells)

Random multiplier paths: the real active multiplier values permuted along an AR(1) Gaussian-copula latent path (identical marginal = same mean, dispersion, clip mass; lag-1 rank autocorrelation matched by calibration; warm-up weeks fixed at 1), re-run through the engine. Rank = share of draws whose change is WORSE than the real one (bar 95%); p = (1 + draws at least as good)/(1 + N). Holm over the 12 cells on the ALL p.

| cell | n | ALL dMaxDD: real · placebo median [5%, 95%] | rank ALL · PRE · HOLD · L6M | worst-20 rank ALL | SD-change rank ALL | p ALL | Holm-adj p |
|---|---|---|---|---|---|---|---|
| VS01 | 1000 | -45% · -15% [-37%, +10%] | 100.0% · 100.0% · 66.2% · 49.6% | 98% | 93% | 0.0010 | 0.012 |
| VS02 | 1000 | -38% · -8% [-31%, +6%] | 98.0% · 98.0% · 43.7% · 19.3% | 83% | 82% | 0.0210 | 0.126 |
| VS03 | 300 | -38% · -17% [-38%, +18%] | 93.7% · 93.7% · 27.7% · 27.0% | 81% | 76% | 0.0664 | 0.282 |
| VS04 | 300 | -35% · -14% [-35%, +0%] | 94.7% · 94.7% · 12.5% · 26.2% | 63% | 38% | 0.0565 | 0.282 |
| VS05 | 300 | -45% · -16% [-37%, +9%] | 100.0% · 100.0% · 67.7% · 46.5% | 98% | 93% | 0.0033 | 0.033 |
| VS06 | 1000 | -45% · -15% [-37%, +10%] | 100.0% · 100.0% · 66.2% · 49.6% | 98% | 93% | 0.0010 | 0.012 |
| VS07 | 300 | -33% · -18% [-34%, +5%] | 93.3% · 93.3% · 32.7% · 54.7% | 91% | 46% | 0.0698 | 0.282 |
| VS08 | 300 | -46% · -15% [-37%, +7%] | 100.0% · 100.0% · 27.3% · 41.0% | 91% | 88% | 0.0033 | 0.033 |
| VS09 | 300 | -12% · -14% [-39%, +9%] | 46.3% · 46.3% · 21.0% · 73.0% | 55% | 38% | 0.5382 | 0.538 |
| VS10 | 300 | -14% · -5% [-24%, +4%] | 86.7% · 86.7% · 13.7% · 20.5% | 35% | 29% | 0.1362 | 0.282 |
| VS11 | 300 | -38% · -7% [-29%, +6%] | 99.3% · 99.3% · 43.0% · 18.7% | 81% | 80% | 0.0100 | 0.080 |
| VS12 | 300 | -38% · -7% [-29%, +6%] | 99.3% · 99.3% · 43.0% · 18.7% | 81% | 80% | 0.0100 | 0.080 |

Uniform-trim placebo (zero dispersion): the baseline at a constant lot scale through the engine lot table (integer rounding), same average volume:

| run | volume vs baseline | maxDD change L6M · HOLD · PRE · X' · ALL | mean change L6M · ALL |
|---|---|---|---|
| uni0.864_VS01 | 0.863 | +14% · -16% · -14% · -4% · -14% | -7.7 · -3.8 |
| uni0.916_VS02 | 0.895 | -47% · +2% · -5% · -8% · -5% | -6.9 · -2.6 |
| uni0.8_VS01 | 0.776 | -2% · -35% · -30% · -8% · -30% | -12.7 · -6.2 |
| uni0.9_VS01 | 0.875 | +14% · -17% · -13% · -3% · -13% | -7.4 · -4.1 |

Delayed / look-ahead placebo (the real multiplier path shifted by k weeks; k>0 = older information, k<0 = uses future vol): ALL maxDD change · L6M maxDD change · ALL mean change $k

| cell | k=-8 | -4 | -2 | -1 | 0 (real) | +1 | +2 | +4 | +8 |
|---|---|---|---|---|---|---|---|---|---|
| VS01 | -14% · +14% · -4.1 | -33% · -3% · -3.7 | -40% · +24% · -4.5 | -45% · +14% · -4.0 | -45% · +8% · -2.6 | -40% · +1% · -2.6 | -42% · +14% · -1.4 | -37% · +54% · -3.6 | -15% · +14% · -4.0 |
| VS02 | -9% · -49% · 0.2 | -33% · -49% · 0.8 | -28% · +22% · 0.2 | -29% · +10% · -0.5 | -38% · +0% · 0.3 | -37% · +22% · 0.6 | -27% · +22% · 0.6 | -25% · +22% · 0.6 | -6% · -37% · -0.8 |

Timing variant (D6 slot): Monday label day trades at the previous week's multiplier (rebuild Monday 18:00 ET instead of before Sunday 18:00 ET): ALL -44%, PRE -44%, L6M +23%, HOLD -22%; mean L6M -4.0, ALL -2.6.

## 4. Stationary-bootstrap CIs of the CHANGE (mean block 4 weeks, 4,000 resamples, same weeks in both series; point [95% CI]; worst-20 = sum of the 20 worst weeks (5 for L6M/HOLD, 3 for L3M))

**VS01**

| window | dMaxDD $k | dMaxDD % | dWorst-20 $k | dSD $k | dCalmar | dMean $k |
|---|---|---|---|---|---|---|
| L3M | +2.0 [-12.4, +17.3] | +9% [-58%, +204%] | -4.8 [-33.0, +23.2] | -5.4 [-9.5, -0.9] | -0.437 [-3.387, +1.359] | -7.0 [-12.7, -1.3] |
| L6M | +1.8 [-12.4, +3.6] | +8% [-58%, +15%] | +5.7 [-9.0, +34.0] | -4.3 [-8.3, -0.3] | -0.290 [-1.112, +2.337] | -3.9 [-8.2, -0.1] |
| HOLD | -23.9 [-36.3, +1.8] | -25% [-44%, +8%] | +44.7 [-8.3, +87.2] | -6.0 [-10.0, -1.2] | +0.083 [-0.416, +0.702] | -3.4 [-7.7, +0.3] |
| PRE | -107.4 [-165.4, -16.0] | -45% [-49%, -12%] | +237.5 [+123.9, +373.4] | -12.3 [-15.7, -9.0] | +0.049 [-0.019, +0.105] | -3.7 [-7.6, +0.1] |
| X' | +0.0 [-7.0, +31.2] | +0% [-5%, +26%] | -17.4 [-62.7, +14.4] | +2.7 [-0.7, +6.5] | +0.001 [-0.044, +0.017] | +0.1 [-1.4, +1.8] |
| ALL | -107.4 [-145.5, +1.3] | -45% [-47%, +1%] | +209.0 [+66.5, +366.6] | -7.6 [-10.6, -4.3] | +0.055 [-0.027, +0.085] | -2.6 [-4.9, -0.4] |

**VS02**

| window | dMaxDD $k | dMaxDD % | dWorst-20 $k | dSD $k | dCalmar | dMean $k |
|---|---|---|---|---|---|---|
| L3M | +13.7 [-4.3, +30.9] | +38% [-17%, +70%] | -8.9 [-18.2, +12.1] | +0.5 [-2.8, +3.2] | -0.164 [-0.461, +0.653] | -0.2 [-4.2, +4.2] |
| L6M | +0.0 [-9.8, +8.0] | +0% [-31%, +39%] | -0.7 [-23.8, +23.5] | +0.2 [-2.1, +2.6] | -0.039 [-0.983, +0.575] | -1.5 [-5.0, +1.8] |
| HOLD | -4.1 [-13.6, +6.7] | -5% [-19%, +17%] | +8.7 [-12.8, +32.5] | -1.9 [-4.9, +1.4] | -0.006 [-0.282, +0.102] | -2.1 [-5.5, +1.1] |
| PRE | -85.2 [-175.5, +19.1] | -38% [-52%, +13%] | +127.1 [-47.9, +255.8] | -5.6 [-10.0, -0.5] | +0.051 [-0.032, +0.100] | +0.9 [-4.2, +5.6] |
| X' | +0.0 [-20.0, +24.5] | +0% [-20%, +21%] | +1.7 [-38.4, +38.2] | +1.7 [-1.0, +4.3] | +0.013 [-0.026, +0.068] | +1.1 [-0.2, +2.9] |
| ALL | -85.2 [-140.5, +16.1] | -38% [-46%, +12%] | +114.9 [-17.0, +247.6] | -3.4 [-6.2, -0.3] | +0.050 [-0.023, +0.079] | +0.3 [-2.3, +2.8] |

Calmar level before→after (mean / maxDD, per window): VS01: L6M 1.80→1.51 PRE 0.10→0.15 X' 0.07→0.07 ALL 0.09→0.15; VS02: L6M 0.85→0.81 PRE 0.07→0.12 X' 0.09→0.11 ALL 0.08→0.13

## 5. Mean cost per window, equal-risk mean, lot-matched comparison

| cell | L3M | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|
| VS01 mean change $k (MDE) [95% CI] | -7.0 (11.5) [-12.7, -1.3] | -3.9 (6.3) [-8.2, -0.1] | -3.4 (6.3) [-7.7, +0.3] | -3.7 (5.7) [-7.6, +0.1] | 0.1 (2.7) [-1.4, +1.8] | -2.6 (3.3) [-4.9, -0.4] |
| VS01 EQUAL-RISK mean change (lot-table scale c=1.181, ALL worst-20 matched: ratio 1.013) | -4.3 (4.3) | 1.7 (5.0) | 2.0 (4.7) | 0.3 (4.2) | 1.1 (5.4) | 0.9 (2.8) |
| VS01 equal-risk maxDD change | +57% | +46% | -17% | -25% | +26% | -25% |
| VS02 mean change $k (MDE) [95% CI] | -0.2 (7.6) [-4.2, +4.2] | -1.5 (6.7) [-5.0, +1.8] | -2.1 (6.2) [-5.5, +1.1] | 0.9 (6.6) [-4.2, +5.6] | 1.1 (2.8) [-0.2, +2.9] | 0.3 (3.7) [-2.3, +2.8] |
| VS02 EQUAL-RISK mean change (lot-table scale c=1.097, ALL worst-20 matched: ratio 1.000) | 3.6 (9.9) | 5.6 (6.5) | 4.4 (6.0) | 1.8 (6.5) | 1.6 (3.7) | 2.3 (3.7) |
| VS02 equal-risk maxDD change | +19% | +29% | +7% | -18% | +9% | -18% |

Equal-risk reading: at the lot scale where the cell's ALL worst-20 equals the baseline's, the cell is c x larger than the baseline in lots, so the 'mean cost' of the unmatched cell is a pure de-leverage cost: the equal-risk line asks whether the same tail can be had with MORE mean. Both lines are inside their MDE in L6M; see the gate table for ALL/PRE.

**Lot-matched (the DS3_SIZING_VOLSCALE B2 comparison: scale so the average lots equal the baseline's; c = baseline volume / cell volume):**

| cell | c | maxDD change L6M · HOLD · PRE · X' · ALL | SD change L6M · HOLD · PRE · ALL | worst-20 change HOLD · PRE · ALL | mean change L6M · HOLD · PRE · ALL |
|---|---|---|---|---|---|
| VS01 | 1.158 | +46% · -17% · -31% · +16% · -31% | 3.7 · 2.3 · -3.8 · -0.0 | 5.0 · 118.7 · 47.8 | 1.8 · 2.1 · -1.1 · 0.2 |
| VS02 | 1.091 | +8% · +7% · -20% · +16% · -20% | -0.4 · -0.8 · -1.4 · 0.1 | 60.5 · 62.6 · 9.2 | 2.7 · 1.7 · 2.1 · 1.9 |

DS3_SIZING_VOLSCALE B2 (per-book, D3SL stack, lot-matched, HOLD): maxDD +81k, SD +10.1k, worst week -35.6k, mean +4.7k (placebo rank 1.00 on the mean, 0.01-0.10 on the risk measures); the DS3_SIZING_REGIME B2 line was maxDD +68k deeper in HOLD.

## 6. Behaviour in a vol-up regime and in a 2025-26-like regime

Weekly decomposition by multiplier bucket (VS01; baseline vs after; `forgone win` = sum of (before - after) over winning baseline weeks, `protected` = sum of (after - before) over losing baseline weeks, $k):

| window | bucket | weeks | mean before | mean after | SD before | SD after | sum of change | winning wks forgone | losing wks protected |
|---|---|---|---|---|---|---|---|---|---|
| ALL | m<0.80 (vol-up state) | 37 | 17.1 | 12.2 | 51.6 | 33.1 | -178.9 | 382.9 (22 wk) | 204.0 (15 wk) |
| ALL | 0.80-1.00 | 68 | 30.8 | 27.6 | 54.0 | 45.7 | -217.9 | 391.1 (49 wk) | 173.1 (19 wk) |
| ALL | 1.00-1.25 (calm) | 40 | 14.1 | 13.9 | 40.6 | 41.2 | -10.7 | -7.1 (23 wk) | -17.8 (17 wk) |
| ALL | m>1.25 (deep calm) | 4 | 6.5 | 12.7 | 56.9 | 75.4 | 25.1 | -41.7 (2 wk) | -16.7 (2 wk) |
| PRE | m<0.80 (vol-up state) | 36 | 16.7 | 12.1 | 52.3 | 33.5 | -167.0 | 371.0 (21 wk) | 204.0 (15 wk) |
| PRE | 0.80-1.00 | 34 | 30.7 | 27.3 | 61.5 | 51.8 | -116.0 | 238.0 (21 wk) | 122.0 (13 wk) |
| PRE | 1.00-1.25 (calm) | 5 | 28.3 | 26.9 | 42.4 | 43.9 | -7.4 | 0.7 (3 wk) | -6.7 (2 wk) |
| X' | 0.80-1.00 | 12 | 16.6 | 15.4 | 27.9 | 24.7 | -14.9 | 27.7 (10 wk) | 12.8 (2 wk) |
| X' | 1.00-1.25 (calm) | 28 | 3.5 | 3.4 | 32.0 | 33.3 | -3.1 | -4.5 (15 wk) | -7.6 (13 wk) |
| X' | m>1.25 (deep calm) | 4 | 6.5 | 12.7 | 56.9 | 75.4 | 25.1 | -41.7 (2 wk) | -16.7 (2 wk) |
| HOLD | m<0.80 (vol-up state) | 2 | 43.7 | 30.3 |  |  | -26.7 | 26.7 (2 wk) | 0.0 (0 wk) |
| HOLD | 0.80-1.00 | 23 | 35.4 | 31.9 | 53.7 | 45.7 | -80.5 | 125.4 (18 wk) | 44.9 (5 wk) |
| HOLD | 1.00-1.25 (calm) | 7 | 46.4 | 46.4 | 54.9 | 53.7 | -0.3 | -3.3 (5 wk) | -3.6 (2 wk) |
| L6M | m<0.80 (vol-up state) | 1 | 29.1 | 17.2 |  |  | -12.0 | 12.0 (1 wk) | 0.0 (0 wk) |
| L6M | 0.80-1.00 | 20 | 45.6 | 40.3 | 46.0 | 40.5 | -104.4 | 113.7 (17 wk) | 9.3 (3 wk) |
| L6M | 1.00-1.25 (calm) | 7 | 46.4 | 46.4 | 54.9 | 53.7 | -0.3 | -3.3 (5 wk) | -3.6 (2 wk) |

High-vol (m<0.85) AND winning weeks, VS01 / VS02 feed OFF:

| window | weeks | m<0.85 weeks | of which winning | mean baseline win | forgone per such week | forgone total | losses saved in m<0.85 losing weeks | all-weeks mean change |
|---|---|---|---|---|---|---|---|---|
| VS01 ALL | 149 | 58 | 34 | 49.9 | 14.0 | 474.5 | 284.1 | -2.6 |
| VS01 PRE | 75 | 50 | 28 | 54.9 | 15.5 | 435.2 | 270.8 | -3.9 |
| VS01 X' | 44 | 4 | 4 | 6.9 | 1.9 | 7.4 | 0.0 | 0.2 |
| VS01 HOLD | 32 | 5 | 3 | 62.9 | 15.5 | 46.6 | 13.3 | -3.4 |
| VS01 L6M | 28 | 3 | 2 | 65.2 | 15.9 | 31.8 | -1.5 | -4.2 |
| VS01 L3M | 14 | 3 | 2 | 65.2 | 15.9 | 31.8 | -1.5 | -6.8 |
| VS02 ALL | 149 | 58 | 31 | 40.4 | 2.3 | 72.1 | 209.3 | 0.3 |
| VS02 PRE | 75 | 50 | 27 | 43.6 | 3.7 | 99.2 | 195.3 | 0.7 |
| VS02 X' | 44 | 4 | 2 | 12.8 | -1.2 | -2.3 | 3.2 | 1.2 |
| VS02 HOLD | 32 | 5 | 3 | 40.4 | 1.6 | 4.9 | 10.8 | -2.5 |
| VS02 L6M | 28 | 3 | 2 | 24.6 | -12.4 | -24.8 | 1.2 | -1.9 |
| VS02 L3M | 14 | 3 | 2 | 24.6 | -12.4 | -24.8 | 1.2 | 0.0 |

Pools: weekly vol = SD of the week's daily stack P&L; calm = bottom 40% (60 wk, mean 14.9), hot = top 40% (60 wk, mean 30.1), hot-and-winning (42 wk, mean 55.1); HOLD vol 27.1 vs all 24.7, HOLD mean 38.3 vs all 22.3.

Regime simulations (1,000 paths each; real history to 2025-06 as the lead-in for the expanding median, then resampled 4-week blocks; after = m x before, a LINEAR approximation: corr with the engine weekly series 0.983, and it UNDERSTATES the engine's PRE cut: 160k vs 134k; the sim part only is scored):

| regime | mean before → after $k/wk | maxDD before → after $k | share of paths with a shallower maxDD | mean m | shock-window (last 12 wk) P&L before → after | m at shock start |
|---|---|---|---|---|---|---|
| A 2025-26-like (HOLD weeks, 40 wk, after the real history to 2025-06) | 38.3 → 36.1 | 84 → 81 | 68% | 0.94 |  |  |
| B vol-up shock (16 calm + 12 hot weeks) | 21.8 → 24.3 | 116 → 147 | 21% | 1.18 | 367 → 343 | 1.57 |
| C vol-up and wins (16 calm + 12 hot-and-winning) | 32.5 → 33.3 | 98 → 135 | 10% | 1.17 | 665 → 594 | 1.57 |
| D vol-up persists (4 calm + 24 hot weeks) | 28.1 → 23.7 | 107 → 89 | 81% | 0.84 | 366 → 281 | 0.74 |

**Reading.** (i) Vol-up regime that persists (sim D: 4 calm then 24 hot weeks): the rule works as advertised, maxDD 107→89k in 81% of paths, at a mean cost of 4.4k/wk (28.1→23.7); in the data this is PRE: 36 of the 37 weeks with m<0.8 are in PRE, where the m<0.8 weeks earned 16.7k/wk baseline and 12.1k after, forgoing 371k in 21 winning weeks to save 204k in 15 losing weeks. (ii) Vol-up after calm (sims B, C: m 1.57 at the shock start): maxDD 116→147k (shallower in only 21% of paths) and, if the hot weeks win (C), the rule first levers up then de-levers and ends 71k behind over the 12 weeks (665→594k) with a deeper drawdown (98→135k, shallower in 10%). The same sign is visible in the sample where calm preceded a loss: episodes 7 and 9 (m 1.25 and 1.23) lose 1.24x and 1.16x the baseline. (iii) A 2025-26-like regime (sim A: HOLD weeks after the real history, vol 10% above its median, big winning weeks): mean 38.3→36.1k/wk (-2.2k, -6%), maxDD 84→81k (shallower in 68% of paths); the data show the same: HOLD -3.4k and L6M -3.9k/wk (about 9% of a 35-45k/wk mean), essentially all from the 0.80-1.00 bucket (23 of 32 HOLD weeks, forgoing 125k in 18 winning weeks to protect 45k in 5 losing ones), and in the three m<0.85 weeks of L6M (two winning) it forgoes 15.9k per winning week (24% of 65k). So when vol is high and the stack wins, it forgoes roughly its de-leverage fraction of the win (8-25%), which is inside the MDE in the aggregate but is not protection: there is no L6M tail to protect (one 22.9k path).

**Why this version differs from, or does not differ from, the B2 failure (DS3_SIZING_VOLSCALE: per-book, D3SL stack, lot-matched, HOLD maxDD +81k, SD +10.1k, worst week -35.6k; DS3_SIZING_REGIME: HOLD +68k).** The mechanism is the same: the rule levers up after calm (m up to 1.55 here, 1.42-1.57 at the start of a simulated shock) and the first hot weeks hit at larger size; here that costs episodes 7 and 9 (+24% and +16% deeper), lot-matched VS01 deepens L6M maxDD +46% (22.9→33.5k) and SD +3.7k, and the simulated calm-then-shock paths are deeper in 79-90%. What differs is the outcome in HOLD, for three reasons that are not a repair: (1) A3's cell is unmatched (mean m 0.89, volume -14%), so it is a de-leverage, not B2's lot-matched leverage (about 13.6% more lots than the raw multiplier); lot-matched VS01 has HOLD maxDD -17%, SD +2.3k (B2: +81k, +10.1k). (2) One stack multiplier for all books (per-book VS07 is weaker: ALL -33%, L6M mean -7.3k beyond the MDE) on the composite with the running-max locks fed by the multiplier, instead of per-book multipliers on D3SL. (3) The HOLD sample here follows PRE's high-vol years, so the expanding median of the trailing SD is high and HOLD sits at m 0.8-1.25 (only 2 weeks below 0.8, none above 1.25), i.e. HOLD contains no calm-then-shock transition for the rule to fail on; B2's HOLD had one. The honest reading is that the -17% in HOLD and the -45% in PRE are coincidences of two vol-up stretches that preceded losses, and the sim B/C results are what a calm-then-shock regime does to the same rule.


## 7. D6 mapping and the Shadow monitor STOP rule (Shadow only; nothing live, no Sunday action)

**Weekly lot-multiplier policy line (VS01, stack scope, feed ON).**

- Input: the stack's TOTAL realised daily P&L x_d (all six books, net of costs, per LABEL day: the label day starts 18:00 ET the previous calendar evening) divided by the multiplier m that was applied to that day's week (so the SD is that of the UNSCALED-equivalent stack; the realised-P&L fixed point is tested below). One number per label day; no per-book series needed (the per-book cell VS07 is worse).
- Per ISO label week j: `s_j` = sample SD (ddof 1) of x_d over all label days of weeks j-8..j-1 (about 40 days; weeks j-8 and j-1 included, the week being set EXCLUDED). `H_j` = the set of all earlier `s_i` (i<j) that exist (they start at week 9 of the history). `m_j = 1.0` while |H_j| < 8 (the first 16 label weeks of any history) or `s_j` = 0, else `m_j = clip(median(H_j) / s_j, 0.5, 2.0)`. Backtest range 0.60-1.55, mean 0.89 (the clip never binds), so a D6 clip of 0.5-2.0 is a safety rail only.
- Apply: every row (book, session) of the label days of week j: `lots = max(1, floor(planned_lots x ER_mult x m_j + 0.5))` (integer half-up, minimum 1; planned_lots = book lots x session lot; ER_mult = the existing ER sizer multiplier, composed multiplicatively). Feed ON: the running-max day/week locks see the UNROUNDED `ER_mult x m_j` (their R thresholds move with it); feed OFF: the locks see ER_mult only (the OFF cell VS02, a different and weaker result, see the table).
- Timing: m_j must exist at the start of the Monday label day (Sunday 18:00 ET). Rebuild from Friday's close, i.e. any time after the Friday label day closes (Fri 17:00 ET) and before Sunday 18:00 ET. A Monday 18:00 ET rebuild means the Monday label day runs on the previous week's m; that variant is the 'timing variant' line in section 3 (its numbers are the cost of a one-day-late rebuild).
- Realised-P&L fixed point (what D6 can actually compute: realised P&L / its own m, one iteration): ALL maxDD change -41% (vs -45% on the unscaled series), PRE -41%, L6M +8%, HOLD -23%; mean L6M -6.8, ALL -3.1. Max |m1 - m0| = 0.08 (mean 0.02). The realised-basis version costs more mean in L6M (-6.8k vs -3.9k; MDE 6.3k): at the edge of the MDE.
- Latest multiplier in the sample (weeks 2025-49..2026-06): 202551: 0.84, 202552: 0.81, 202601: 0.79, 202602: 0.90, 202603: 0.93, 202604: 0.91, 202605: 0.87, 202606: 0.86  (for reference only; the post-cap weeks are not read).

**Monitor STOP rule (Shadow log; evaluated every Friday close; numbers fixed now from the backtest).** Log per week: unscaled composite P&L (shadow), scaled P&L (x m_j with the same rounding), m_j, s_j.
Backtest facts: weekly SD of the unscaled composite 50.3k, scaled 42.8k; weekly change (scaled - unscaled) mean -2.6k, SD 14.3k, cumulative -382.5k over 149 weeks; 3 weeks below -1.5 SD (-75k), all in PRE, m in force 0.63-0.84 in all three; 9 weeks with m>=1.15 (all in 2023), 6 with m>=1.2.
STOP (retire the Shadow, do not size) when ANY of:
- (a) COST: after at least 26 shadow weeks the cumulative (scaled - unscaled) P&L is below `-2.6k x n - 2 x 14.3k x sqrt(n)` (n weeks; two sigma worse than the backtest's own carry cost; at n=26: below -212k).
- (b) NO-HEDGE: of the first 4 weeks in which the unscaled composite loses more than 1.5 x 50k (week below -75k), the scaled P&L is better than the unscaled in fewer than 3 (the backtest: 3 of 3).
- (c) LEVER-UP LOSS (the B2 failure): 2 weeks within any 26 in which m_j >= 1.15 and the unscaled composite loses more than 1.0 x 50k (backtest: 1 such week, 2023-51, m 1.25, -66k).
- (d) DRAWDOWN: after 52 shadow weeks the scaled stack's own maxDD is not below the unscaled stack's maxDD over the same weeks by at least 10% (the claim is a cut; the backtest cut is -45% on one episode, +8% in L6M).
- (e) MISS: shadow lots differ from the formula (integer rounding, wrong week SD) in more than 10% of rows over 20 days.
PROMOTE (a Sunday decision, never automatic): only after 52 shadow weeks with (a)-(e) clear AND a forward drawdown episode of at least 100k in the unscaled composite in which the scaled series is shallower with m_j <= 0.9 at the peak. Until then it is a log.

## 8. Gate table and verdict (every failed gate named; all gates must pass for a strict RISK-KEEP)

**VS01 L8 c0.5-2.0 stack weekly, feed ON**

| gate | pass | numbers |
|---|---|---|
| G1 maxDD cut >=20% in ALL and PRE | PASS | ALL -45%, PRE -45% |
| G2 mean inside MDE (L6M and ALL) | PASS | L6M -3.9 (MDE 6.3), ALL -2.6 (MDE 3.3) |
| G3 L6M maxDD not deepened >5% | **FAIL** | L6M +8% |
| G4 PRE and X' agree (both cut >=20%) | **FAIL** | PRE -45%, X' +0% |
| G5 beats the AR(1) placebo (rank >=95%, ALL) | PASS | rank 100.0% (p 0.0010, n 1000) |
| G6 timing: real >= every shifted placebo (ALL) | **FAIL** | real -45% vs best shifted -45% (k=-1) |
| G7 survives LOEO (5/5 singles; all-five sign kept) | **FAIL** | 5/5 singles; all five removed: +2% |
| G8 bootstrap CI of the maxDD change <0 in PRE and ALL | **FAIL** | PRE CI [-49%,-12%], ALL [-47%,+1%] |
| G9 Holm-adjusted p<0.05 (12 cells) | PASS | Holm-adjusted p 0.012 (raw 0.0010) |
| G10 equal-risk mean inside MDE (ALL, PRE, L6M) | PASS | equal-risk dMean ALL 0.9 (MDE 2.8), PRE 0.3 (4.2), L6M 1.7 (5.0) |
| G11 realised-P&L fixed point keeps >=80% of the ALL cut | PASS | fixed point ALL -41% vs -45% |

**VS02 L8 c0.5-2.0 stack weekly, feed OFF**

| gate | pass | numbers |
|---|---|---|
| G1 maxDD cut >=20% in ALL and PRE | PASS | ALL -38%, PRE -38% |
| G2 mean inside MDE (L6M and ALL) | PASS | L6M -1.5 (MDE 6.7), ALL 0.3 (MDE 3.7) |
| G3 L6M maxDD not deepened >5% | PASS | L6M +0% |
| G4 PRE and X' agree (both cut >=20%) | **FAIL** | PRE -38%, X' +0% |
| G5 beats the AR(1) placebo (rank >=95%, ALL) | PASS | rank 98.0% (p 0.0210, n 1000) |
| G6 timing: real >= every shifted placebo (ALL) | PASS | real -38% vs best shifted -37% (k=1) |
| G7 survives LOEO (5/5 singles; all-five sign kept) | **FAIL** | 5/5 singles; all five removed: +10% |
| G8 bootstrap CI of the maxDD change <0 in PRE and ALL | **FAIL** | PRE CI [-52%,+13%], ALL [-46%,+12%] |
| G9 Holm-adjusted p<0.05 (12 cells) | **FAIL** | Holm-adjusted p 0.126 (raw 0.0210) |
| G10 equal-risk mean inside MDE (ALL, PRE, L6M) | PASS | equal-risk dMean ALL 2.3 (MDE 3.7), PRE 1.8 (6.5), L6M 5.6 (6.5) |
| G11 realised-P&L fixed point keeps >=80% of the ALL cut | n/a | VS01 only |

All 12 cells (failed gates):

| cell | failed gates | RISK-KEEP user definition (PRE/ALL reading) | (L6M reading) |
|---|---|---|---|
| VS01 L8 c0.5-2.0 stack weekly, feed ON | G3, G4, G6, G7, G8 | yes | NO |
| VS02 L8 c0.5-2.0 stack weekly, feed OFF | G4, G7, G8 | yes | NO |
| VS03 L4 (stack, ON) | G2, G3, G4, G5, G8 | yes | NO |
| VS04 L13 (stack, ON) | G3, G4, G5, G7, G8 | yes | NO |
| VS05 clip 0.5-1.5 (ON) | G3, G4, G7, G8 | yes | NO |
| VS06 clip 0.25-2.0 (ON) | G3, G4, G7, G8 | yes | NO |
| VS07 per-book L8 (ON) | G2, G4, G5, G8 | NO | NO |
| VS08 daily update, 40 days (ON) | G2, G3, G4, G8 | NO | NO |
| VS09 L4 (OFF) | G1, G4, G5, G7, G8 | NO | yes |
| VS10 L13 (OFF) | G1, G4, G5, G7, G8 | NO | NO |
| VS11 clip 0.5-1.5 (OFF) | G4, G7, G8 | yes | NO |
| VS12 clip 0.25-2.0 (OFF) | G4, G7, G8 | yes | NO |

**Verdict (every failed gate named; post-hoc, Shadow only, no PASS).**
- **VS01 (primary, feed ON): RISK-KEEP under the user definition (maxDD cut >= 20% with the mean inside its MDE) = YES on PRE/ALL, NO on L6M. Failed gates: G3 (L6M maxDD +8%, though a uniform 14% trim gives +14% on that 22.9k path, an integer-lot artefact), G4 'PRE and X' agree' (X' 0%: the 16-week warm-up covers the X' drawdown, so the gate cannot be passed), G6 timing (the k=-1 look-ahead shift gives -44.7% vs the real -44.5%: no timing sensitivity at 1-2 weeks), G7 'survives LOEO' (singles 5/5 but the cut falls to -18% with the 241k episode removed and to +2% with all five removed), G8 (ALL bootstrap CI [-47%, +1%]). Passed: G1, G2, G5 'beats placebo' (rank 100%, p 0.001), G9 (Holm 0.012; 0.052 over A3's 52 cells), G10 (equal-risk mean +0.9 / +0.3 / +1.7k ALL/PRE/L6M inside MDE), G11 (realised-P&L fixed point keeps -41% of -45%).**
- **VS02 (feed OFF twin): YES on PRE/ALL (-38%), NO on L6M; failed gates G4, G7 (-10% with the episode removed, +10% with five), G8 (PRE CI [-52%, +13%]), G9 (Holm 0.126).** The OFF twin does not deepen L6M (0%) and has a positive equal-risk mean (+2.3k ALL, +5.6k L6M, inside MDE), but its placebo evidence is weaker (98%).
- **Neighbourhood:** no cell passes the strict set. Feed ON: L4 (VS03) and per-book (VS07) breach the L6M mean MDE (G2: -7.1 vs 6.7, -7.3 vs 6.4); VS03/VS04/VS07 do not beat the placebo at 95% (93.7 / 94.7 / 93.3%); the daily update VS08 cuts ALL 46% but its ALL mean (-3.2k) is outside the MDE (3.0); VS05/VS06 are VS01 (the clip never binds: m 0.60-1.55). Feed OFF: L4 and L13 (VS09/VS10) cut ALL only 12-14% (rank 46% / 87%), VS11/VS12 are VS02. The 38-46% cuts therefore need the stack-level scope and a window of 8 weeks or a daily update.
- **Decision: Shadow log of VS01 (weekly stack multiplier, feed ON) and VS02 as its twin, no stack change, no Sunday action.** What is established: the rule beats random multipliers of the same distribution on the 241k episode (that is the A3 lead confirmed as a consistency result) and costs a de-leverage fraction of the mean. What is not: independence from that one episode, any protection in the recent windows, or protection against calm-then-shock (the B2 mode, which the simulations reproduce). Promotion needs forward evidence (STOP/PROMOTE rule in section 7).


## 9. Caveats and files
- Selection: A3 picked the stack-level L8 variant after PRE with L6M/HOLD already read (52 V cells); the p-values and CIs here are conditional on the pick, and the family (12 cells, 3 of which are identical series: the clip never binds, VS01 = VS06, VS05 differs in one week) is smaller than the selection history.
- ALL = PRE: one 241k episode; X' is untouched by every trailing-history rule by construction (the 16-week warm-up covers the X' drawdown), so the 'PRE and X' agree' gate cannot be passed by this rule and is reported, not waived.
- The multiplier is computed from the UNSCALED composite's daily SD (A3 definition, kept frozen); the realised-P&L fixed point is the D6-computable version.
- The regime simulations use the linear approximation after = m x before (understates the engine's PRE cut by about 26k).
- Code: `l2vast/ds3/code/volscale_decisive/` (vd_lib, vd_run, an_lib, an_fn, an_main, an_ep, an_reg, an_extra, mk_doc). Results: `l2vast/ds3/out/volscale_decisive/` (res_p1/p2/p3 pickles, main.pkl, regime.pkl, extra.pkl, eqrisk_info.json). Prereg sha256 in DECISIONS.md. DEAD_CELLS: appended after (program VOLSCALE_DEC), never rebuilt.
