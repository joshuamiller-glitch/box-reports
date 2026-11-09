# DS3_TH_S4_ZONES_S1B - S4: the zone layer on the S1b base (S345-RUN, 2026-11-09)

**Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF**

Prereg: autopilot/DS3_TH_S345_S1B_PREREG.md. Supersedes DS3_TH_STATE_S4_ZONES.md (S1 timer base, untouched). Windows as of 2026-10-31, carrying weeks dropped, drawdown first, post-hoc, Shadow only, no PASS claims.

Method: zone features from a replay of the replica own PoiSet (8 live lines) on the 1-min bars at each trade signal second (the V13T feats.npz matches only 46-71% of replica signals). Replay vs the half inferred from base lots: agree 88.5% (recall 59%, precision 76%, 8253 informative trades). Reference = the base as it stands (live zone HALF inside the lots). Half cells halve lots (rounded, min 1) on top of the live half; skip cells drop the signal; FIRST-ORDER. Placebo = same count at random within book x session (100 draws for the rank column; 300 draws for the family null).

## Summary (S1B-COMB; maxDD cut vs the base zone layer on L6M / HOLD / MID / PRE / X', + = shallower)
- Half-type leads: all six cut maxDD on L6M, PRE and X' on all three bases (S1B-COMB: open20 +45 / +28 / +19 / +41 / +31, open40 +48 / +29 / +20 / +34 / +20, open60 +41 / +13 / +20 / +34 / +28, openA40 +48 / +34 / +26 / +37 / +31, openA60 +46 / +27 / +22 / +35 / +18, sopen40 +40 / +18 / +20 / +35 / +23). Cut > 0 on every window on every base: open20 half, open40 half, openA40 half, openA60 half, sopen40 half (open60 HOLD/MID is -2 / +2 on NOCUT). They give up $/wk (d mean L6M -8368 to -2094 on COMB) and halve 47-81% of trades. Placebo (random same-count halving within book x session) ranks COMB L6M/PRE: open20 0.77/0.66; open40 0.99/0.81; open60 0.98/0.98; openA40 0.90/0.74; openA60 0.96/0.67; sopen40 0.90/0.91. Ranks >= .95 on L6M and PRE on all three bases: open60 half (the others sit below .95 on at least one window/base, the VOLUME pattern of the published page).
- Family null (300 draws, max over 16 cells, z-standardised): smallest p_family on L6M 0.29 (open40 half) and on PRE 0.53 (open60 half); half cells have own-draw p L6M 0.18 / 0.02 / 0.02 / 0.05 / 0.06 / 0.05; random halving of the same count gets most of the cut for open20 / openA40 / sopen40, while open40 and open60 beat their own placebo (own p .02) but not the max over 16 cells (conservative, cells treated as independent). Best half cell by min(L6M, HOLD, PRE) cut: openA40 half (+48 / +34 / +26 / +37 / +31).
- Skip-type leads (nA, rho60): do not hold up: nA40>=1 / nA60>=1 skip L6M cut -16.8 / -11.1 on COMB (published +5 / +36), rho60>=2 +2.6 (published +41); sign differs by base on PRE (NOCUT PRE: nA40>=1 -26.8, nA60>=1 -25.3). Not reproduced (the PoiSet replay has a different freshness set than V13T).
- Walk-forward (monthly 2024-01..2026-10, 26 trailing weeks, 7-day embargo, picks lowest maxDD among the 16 cells): OOS maxDD cut +35.1% vs the base layer, mean -3735 $/wk (COMB); picks: open20 half 16, openA60 half 8, openA40 half 6, nA60>=3 skip 2, rho60>=2 skip 2. Held-out live week (frozen file, first-order, same replay): see the live table; no losing day for the base or for the half cells.
- Live zone layer itself (ZOFF = undo the live half), cut vs base: -8.6 / -2.8 / -18.1 (L6M / PRE / X') on COMB; removing it deepens drawdown on L6M, PRE and X-prime on COMB and NOCUT (UNIF: see table).

## S1B-COMB

Table (S1B-COMB): maxDD cut vs the base zone layer by window (+ = shallower), mean change, placebo rank (share of draws with a smaller cut). MDE of the base L6M weekly mean 32105. [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| cell | share of trades | L1M cut% | L2M cut% | L3M cut% | L6M cut% | HOLD cut% | MID cut% | PRE cut% | X' cut% | d mean L6M/PRE | placebo rank L6M/PRE |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ZOFF | 0.07 | -8.6 | -8.6 | -8.6 | -8.6 | -12.6 | -1.6 | -2.8 | -18.1 | +1642 / -66 |  |
| ZREPLAY | 0.15 | -6.2 | -6.2 | -6.2 | -6.2 | -7.6 | +20.8 | +0.7 | -4.9 | +205 / +210 |  |
| open20 half | 0.81 | +44.8 | +44.8 | +44.8 | +44.8 | +27.6 | +18.7 | +40.6 | +31.0 | -8368 / -4657 | 0.77 / 0.66 |
| open40 half | 0.62 | +49.3 | +49.3 | +49.3 | +47.6 | +28.7 | +19.8 | +34.2 | +20.3 | -4668 / -3101 | 0.99 / 0.81 |
| open60 half | 0.47 | +44.5 | +44.5 | +44.5 | +41.0 | +13.3 | +19.7 | +34.1 | +28.5 | -2094 / -1732 | 0.98 / 0.98 |
| openA40 half | 0.73 | +50.3 | +50.3 | +50.3 | +47.9 | +33.7 | +25.5 | +36.9 | +30.7 | -5425 / -4110 | 0.90 / 0.74 |
| openA60 half | 0.65 | +47.7 | +47.7 | +47.7 | +46.0 | +26.6 | +22.0 | +35.1 | +18.2 | -5203 / -3536 | 0.96 / 0.67 |
| sopen40 half | 0.58 | +40.0 | +40.0 | +40.0 | +40.0 | +17.5 | +20.3 | +34.8 | +23.0 | -3032 / -3291 | 0.90 / 0.91 |
| nA20>=2 skip | 0.04 | -6.0 | -6.0 | -6.0 | -6.0 | +0.0 | +0.2 | -0.9 | +14.0 | +204 / -237 | 0.26 / 0.27 |
| nA20>=3 skip | 0.01 | +0.9 | +0.9 | +0.9 | +0.9 | +0.0 | +0.0 | +0.0 | -2.3 | +322 / -277 | 0.47 / 0.40 |
| nA40>=1 skip | 0.27 | -16.8 | -16.8 | -16.8 | -16.8 | +6.3 | +39.0 | +8.6 | +9.8 | -11200 / -3584 | 0.12 / 0.25 |
| nA40>=2 skip | 0.11 | -0.8 | -0.8 | -0.8 | -0.8 | +7.2 | +31.8 | -2.3 | +26.6 | -2572 / -194 | 0.32 / 0.18 |
| nA40>=3 skip | 0.04 | +0.8 | +0.8 | +0.8 | +0.8 | +0.0 | +20.5 | +0.0 | +20.9 | -184 / -927 | 0.47 / 0.41 |
| nA60>=1 skip | 0.35 | -11.1 | -11.1 | -11.1 | -11.1 | +0.6 | +62.5 | +11.7 | +5.7 | -11807 / -4681 | 0.07 / 0.20 |
| nA60>=2 skip | 0.16 | -3.5 | -3.5 | -3.5 | -3.5 | +17.0 | +19.9 | +3.6 | +33.8 | -4027 / -1628 | 0.31 / 0.28 |
| nA60>=3 skip | 0.07 | +0.2 | +0.2 | +0.2 | +0.2 | +2.5 | +22.1 | +0.7 | +31.9 | +448 / -1350 | 0.37 / 0.35 |
| rho60>=2 skip | 0.24 | +2.6 | +2.6 | +2.6 | +2.6 | -8.1 | +45.5 | +14.7 | +4.3 | -6329 / -1798 | 0.21 / 0.43 |

## S1B-NOCUT

Table (S1B-NOCUT): maxDD cut vs the base zone layer by window (+ = shallower), mean change, placebo rank (share of draws with a smaller cut). MDE of the base L6M weekly mean 37020. [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| cell | share of trades | L1M cut% | L2M cut% | L3M cut% | L6M cut% | HOLD cut% | MID cut% | PRE cut% | X' cut% | d mean L6M/PRE | placebo rank L6M/PRE |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ZOFF | 0.08 | -9.1 | -9.1 | -9.1 | -9.1 | -5.6 | -5.6 | -15.1 | -22.1 | +1373 / +32 |  |
| ZREPLAY | 0.15 | -3.9 | -3.9 | -3.9 | -3.9 | +9.3 | +9.3 | -4.4 | -7.2 | +479 / +196 |  |
| open20 half | 0.80 | +36.6 | +36.6 | +36.6 | +36.6 | +22.9 | +22.9 | +27.6 | +32.4 | -5066 / -4063 | 0.61 / 0.27 |
| open40 half | 0.61 | +39.1 | +39.1 | +39.1 | +39.1 | +12.2 | +12.2 | +38.0 | +26.6 | -1058 / -2539 | 0.92 / 0.94 |
| open60 half | 0.47 | +34.3 | +34.3 | +34.3 | +34.3 | -2.3 | +2.4 | +36.8 | +33.8 | +541 / -1179 | 0.96 / 1.00 |
| openA40 half | 0.73 | +41.0 | +41.0 | +41.0 | +41.0 | +16.5 | +16.5 | +41.2 | +31.8 | -1281 / -3123 | 0.87 / 0.99 |
| openA60 half | 0.65 | +34.4 | +34.4 | +34.4 | +34.4 | +12.1 | +12.1 | +42.5 | +22.9 | -1940 / -2453 | 0.80 / 1.00 |
| sopen40 half | 0.58 | +31.2 | +31.2 | +31.2 | +31.2 | +11.3 | +11.3 | +36.3 | +29.0 | -453 / -2931 | 0.78 / 0.96 |
| nA20>=2 skip | 0.04 | -2.1 | -2.1 | -2.1 | -2.1 | +5.1 | +5.1 | +0.0 | +10.4 | +513 / -189 | 0.29 / 0.52 |
| nA20>=3 skip | 0.01 | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 | -2.3 | +340 / -196 | 0.40 / 0.50 |
| nA40>=1 skip | 0.27 | -1.4 | -1.4 | -1.4 | -1.4 | +13.8 | +41.1 | -26.8 | +21.1 | -11045 / -3981 | 0.18 / 0.03 |
| nA40>=2 skip | 0.11 | +3.3 | +3.3 | +3.3 | +3.3 | +17.7 | +24.2 | -10.1 | +15.5 | -1662 / -102 | 0.31 / 0.23 |
| nA40>=3 skip | 0.04 | -3.1 | -3.1 | -3.1 | -3.1 | +11.1 | +11.1 | +0.0 | +16.9 | -277 / -639 | 0.19 / 0.55 |
| nA60>=1 skip | 0.35 | +14.3 | +14.3 | +14.3 | +13.6 | +26.5 | +62.1 | -25.3 | +27.2 | -9685 / -5268 | 0.33 / 0.04 |
| nA60>=2 skip | 0.16 | +14.2 | +14.2 | +14.2 | +4.6 | +18.8 | +23.5 | -36.7 | +27.9 | -2724 / -1553 | 0.33 / 0.03 |
| nA60>=3 skip | 0.07 | +1.3 | +1.3 | +1.3 | +1.3 | +16.0 | +21.7 | -1.6 | +15.1 | +1328 / -1377 | 0.29 / 0.47 |
| rho60>=2 skip | 0.23 | +27.5 | +27.5 | +27.5 | +24.7 | +35.6 | +54.8 | +2.7 | -2.8 | -5185 / -2807 | 0.74 / 0.38 |

## S1B-UNIF

Table (S1B-UNIF): maxDD cut vs the base zone layer by window (+ = shallower), mean change, placebo rank (share of draws with a smaller cut). MDE of the base L6M weekly mean 33838. [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| cell | share of trades | L1M cut% | L2M cut% | L3M cut% | L6M cut% | HOLD cut% | MID cut% | PRE cut% | X' cut% | d mean L6M/PRE | placebo rank L6M/PRE |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ZOFF | 0.08 | -2.7 | -2.7 | -2.7 | -2.7 | -10.1 | -10.1 | -8.7 | -25.1 | +1851 / +141 |  |
| ZREPLAY | 0.15 | +2.6 | +2.6 | +2.6 | +2.6 | +2.3 | +13.8 | -4.1 | -9.0 | +1242 / +292 |  |
| open20 half | 0.81 | +40.9 | +40.9 | +40.9 | +40.9 | +17.2 | +17.2 | +31.1 | +31.0 | -4360 / -4422 | 0.80 / 0.48 |
| open40 half | 0.62 | +35.9 | +35.9 | +35.9 | +35.9 | +9.8 | +9.8 | +32.6 | +27.9 | -1354 / -2678 | 0.86 / 0.83 |
| open60 half | 0.47 | +31.5 | +31.5 | +31.5 | +31.5 | +8.8 | +8.8 | +36.0 | +36.2 | +598 / -1309 | 0.97 / 0.97 |
| openA40 half | 0.73 | +37.9 | +37.9 | +37.9 | +37.9 | +12.5 | +12.5 | +35.7 | +31.7 | -2002 / -3373 | 0.78 / 0.85 |
| openA60 half | 0.65 | +35.9 | +35.9 | +35.9 | +35.9 | +11.1 | +11.1 | +37.0 | +22.2 | -2196 / -2737 | 0.80 / 0.87 |
| sopen40 half | 0.58 | +28.1 | +28.1 | +28.1 | +28.1 | +11.5 | +11.5 | +31.8 | +28.8 | -246 / -2964 | 0.66 / 0.85 |
| nA20>=2 skip | 0.04 | -1.1 | -1.1 | -1.1 | -1.1 | +2.4 | +7.7 | +0.0 | +10.2 | +472 / -285 | 0.34 / 0.40 |
| nA20>=3 skip | 0.01 | +0.0 | +0.0 | +0.0 | +0.0 | +1.2 | +1.2 | +0.0 | -2.6 | +259 / -121 | 0.43 / 0.45 |
| nA40>=1 skip | 0.27 | +10.8 | +10.8 | +10.8 | +10.8 | +19.2 | +53.7 | -7.9 | +16.6 | -7082 / -4719 | 0.33 / 0.08 |
| nA40>=2 skip | 0.11 | +3.8 | +3.8 | +3.8 | +3.8 | +12.8 | +27.4 | -8.8 | +16.7 | -712 / +6 | 0.41 / 0.08 |
| nA40>=3 skip | 0.04 | -2.2 | -2.2 | -2.2 | -2.2 | +6.7 | +14.5 | +0.0 | +17.7 | -351 / -662 | 0.24 / 0.35 |
| nA60>=1 skip | 0.35 | +17.2 | +17.2 | +17.2 | +17.2 | +24.9 | +64.4 | -7.9 | +25.2 | -6493 / -5961 | 0.31 / 0.06 |
| nA60>=2 skip | 0.16 | +14.1 | +14.1 | +14.1 | +14.1 | +19.6 | +20.6 | -1.4 | +29.5 | -700 / -1467 | 0.52 / 0.18 |
| nA60>=3 skip | 0.07 | +0.7 | +0.7 | +0.7 | +0.7 | +6.5 | +8.4 | -0.3 | +16.2 | +1075 / -1380 | 0.39 / 0.37 |
| rho60>=2 skip | 0.23 | +24.6 | +24.6 | +24.6 | +24.6 | +23.4 | +53.5 | +3.7 | -10.5 | -2727 / -3451 | 0.74 / 0.14 |

## Family null and walk-forward (S1B-COMB)

Family null (statistic = maxDD cut vs the base layer; own = share of own-placebo draws at least as good; family = same against the max over 16 cells). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| cell | window | cut_obs | null_mean | null_sd | p_own | p_family |
|--|--|--|--|--|--|--|
| open20 half | L6M | 44.8 | 36.7 | 8.6 | 0.18 | 0.93 |
| open40 half | L6M | 47.6 | 26.2 | 11.5 | 0.02 | 0.29 |
| open60 half | L6M | 41.0 | 19.2 | 13.0 | 0.02 | 0.42 |
| openA40 half | L6M | 47.9 | 32.9 | 9.9 | 0.05 | 0.56 |
| openA60 half | L6M | 46.0 | 28.8 | 11.5 | 0.06 | 0.57 |
| sopen40 half | L6M | 40.0 | 24.0 | 11.5 | 0.05 | 0.66 |
| nA20>=2 skip | L6M | -6.0 | 2.5 | 11.3 | 0.76 | 1.00 |
| nA20>=3 skip | L6M | 0.86 | 0.79 | 6.1 | 0.46 | 1.00 |
| nA40>=1 skip | L6M | -16.8 | 12.5 | 22.8 | 0.88 | 1.00 |
| nA40>=2 skip | L6M | -0.82 | 5.0 | 18.5 | 0.64 | 1.00 |
| nA40>=3 skip | L6M | 0.85 | 3.0 | 11.5 | 0.59 | 1.00 |
| nA60>=1 skip | L6M | -11.1 | 23.7 | 22.5 | 0.93 | 1.00 |
| nA60>=2 skip | L6M | -3.5 | 8.8 | 21.0 | 0.77 | 1.00 |
| nA60>=3 skip | L6M | 0.24 | 4.2 | 14.5 | 0.59 | 1.00 |
| rho60>=2 skip | L6M | 2.6 | 13.9 | 21.4 | 0.72 | 1.00 |
| open20 half | PRE | 40.6 | 36.2 | 6.5 | 0.25 | 0.98 |
| open40 half | PRE | 34.2 | 26.9 | 8.7 | 0.18 | 0.96 |
| open60 half | PRE | 34.1 | 20.2 | 8.5 | 0.07 | 0.54 |
| openA40 half | PRE | 36.9 | 32.1 | 7.8 | 0.28 | 0.99 |
| openA60 half | PRE | 35.1 | 29.9 | 8.5 | 0.29 | 0.99 |
| sopen40 half | PRE | 34.8 | 24.7 | 8.4 | 0.12 | 0.86 |
| nA20>=2 skip | PRE | -0.85 | 3.2 | 7.4 | 0.69 | 1.00 |
| nA20>=3 skip | PRE | 0.00 | 0.46 | 3.6 | 0.57 | 1.00 |
| nA40>=1 skip | PRE | 8.6 | 19.7 | 16.7 | 0.75 | 1.00 |
| nA40>=2 skip | PRE | -2.3 | 9.7 | 12.6 | 0.82 | 1.00 |
| nA40>=3 skip | PRE | 0.00 | 2.7 | 7.9 | 0.64 | 1.00 |
| nA60>=1 skip | PRE | 11.7 | 21.6 | 18.9 | 0.70 | 1.00 |
| nA60>=2 skip | PRE | 3.6 | 14.2 | 14.2 | 0.75 | 1.00 |
| nA60>=3 skip | PRE | 0.71 | 4.6 | 10.2 | 0.66 | 1.00 |
| rho60>=2 skip | PRE | 14.7 | 18.4 | 15.8 | 0.59 | 1.00 |

Walk-forward OOS (weekly, carrying weeks dropped). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| series | n_weeks | mean_wk | maxdd | worst20 | mde | cut_vs_ref_pct | dmean_vs_ref |
|--|--|--|--|--|--|--|--|
| REF(base) | 133 | 17664.8 | 140288.2 | -1045576.1 | 10046.2 | 0.00 | 0.00 |
| open20 half | 133 | 12956.7 | 83330.9 | -693229.2 | 6774.0 | 40.6 | -4708.0 |
| open40 half | 133 | 14600.2 | 92287.4 | -766648.9 | 7606.5 | 34.2 | -3064.6 |
| open60 half | 133 | 15517.3 | 92445.5 | -802603.4 | 8235.2 | 34.1 | -2147.5 |
| openA40 half | 133 | 14033.3 | 88493.8 | -701785.0 | 7093.7 | 36.9 | -3631.4 |
| openA60 half | 133 | 14306.4 | 91016.0 | -718075.3 | 7349.9 | 35.1 | -3358.4 |
| sopen40 half | 133 | 14568.2 | 91491.6 | -779286.8 | 7835.4 | 34.8 | -3096.5 |
| nA20>=2 skip | 133 | 17031.9 | 141487.0 | -1067620.9 | 10158.1 | -0.90 | -632.9 |
| nA20>=3 skip | 133 | 17420.9 | 140288.2 | -1039065.8 | 10034.2 | 0.00 | -243.9 |
| nA40>=1 skip | 133 | 12437.7 | 128260.2 | -979148.6 | 9071.6 | 8.6 | -5227.0 |
| nA40>=2 skip | 133 | 16390.0 | 143529.6 | -999206.2 | 9951.5 | -2.3 | -1274.7 |
| nA40>=3 skip | 133 | 16565.9 | 140288.2 | -1068943.0 | 10150.3 | 0.00 | -1098.9 |
| nA60>=1 skip | 133 | 11654.6 | 123884.7 | -924140.0 | 8908.0 | 11.7 | -6010.2 |
| nA60>=2 skip | 133 | 15386.2 | 135191.8 | -1037614.7 | 9801.4 | 3.6 | -2278.6 |
| nA60>=3 skip | 133 | 16294.2 | 139288.2 | -1024752.4 | 10073.6 | 0.70 | -1370.6 |
| rho60>=2 skip | 133 | 14436.0 | 119681.9 | -941766.2 | 9391.7 | 14.7 | -3228.7 |
| WF | 133 | 13929.4 | 91016.0 | -745964.8 | 7357.4 | 35.1 | -3735.3 |

## Held-out live week (frozen file, 180 rows, replay features at the live signal seconds, first-order lots)

| cell | n_trades | share_trades | live_week_total | live_week_maxdd_daily | worst_day |
|--|--|--|--|--|--|
| REF(base) | 180 | 0.00 | 104810.0 | 0.00 | 16660.0 |
| open20 half | 180 | 0.95 | 68886.7 | 0.00 | 8630.4 |
| open40 half | 180 | 0.89 | 79698.4 | 0.00 | 8630.4 |
| open60 half | 180 | 0.78 | 85286.6 | 0.00 | 8630.4 |
| openA40 half | 180 | 0.90 | 78496.7 | 0.00 | 8630.4 |
| openA60 half | 180 | 0.81 | 85517.4 | 0.00 | 8630.4 |
| sopen40 half | 180 | 1.00 | 68332.6 | 0.00 | 7428.7 |
| nA20>=2 skip | 180 | 0.00 | 104810.0 | 0.00 | 16660.0 |
| nA20>=3 skip | 180 | 0.00 | 104810.0 | 0.00 | 16660.0 |
| nA40>=1 skip | 180 | 0.10 | 74295.0 | 0.00 | 5620.0 |
| nA40>=2 skip | 180 | 0.02 | 103705.0 | 0.00 | 16660.0 |
| nA40>=3 skip | 180 | 0.00 | 104810.0 | 0.00 | 16660.0 |
| nA60>=1 skip | 180 | 0.19 | 51715.0 | 2630.0 | -2630.0 |
| nA60>=2 skip | 180 | 0.04 | 96440.0 | 0.00 | 17105.0 |
| nA60>=3 skip | 180 | 0.01 | 101210.0 | 0.00 | 16660.0 |
| rho60>=2 skip | 180 | 0.19 | 52915.0 | 1430.0 | -1430.0 |

Half cells halve nearly every live trade (the replay finds no untouched line within the band for most live signals in that week), so the total falls by the halved exposure; maxDD stays 0 except for the skip cells that remove winners (nA60>=1, rho60>=2 produce a losing day). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

## Zone leads on the S1b base vs the published V13Y verdicts and vs the S1 (timer) page

Tie = same sign on L6M and PRE and both within 20 points of the published cut; flip = sign change on L6M or PRE (|new| >= 5). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| lead | published V13Y L6M/PRE/X' (label) | S1 timer COMB L6M/PRE/X' | S1b COMB L6M/PRE/X' | verdict vs published | cut > 0 on all windows, all 3 S1b bases | placebo L6M/PRE: COMB, NOCUT, UNIF |
|--|--|--|--|--|--|--|
| open20 half | +41 / +17 / +9 (VOLUME) | +35.6 / +42.2 / +28.4 | +44.8 / +40.6 / +31.0 | same signs, size differs | yes | 0.77/0.66 / 0.61/0.27 / 0.80/0.48 |
| open60 half | +42 / +4 / +33 (VOLUME) | +26.3 / +36.1 / +24.4 | +41.0 / +34.1 / +28.5 | same signs, size differs | no | 0.98/0.98 / 0.96/1.00 / 0.97/0.97 |
| openA40 half | +35 / +20 / +41 (VOLUME) | +35.5 / +39.8 / +30.4 | +47.9 / +36.9 / +30.7 | TIES | yes | 0.90/0.74 / 0.87/0.99 / 0.78/0.85 |
| sopen40 half | +41 / +11 / +21 (NOISE) | +26.3 / +37.9 / +20.0 | +40.0 / +34.8 / +23.0 | same signs, size differs | yes | 0.90/0.91 / 0.78/0.96 / 0.66/0.85 |
| rho60>=2 skip | +41 / +1 / +36 (VOLUME ONE-WEEK) | -20.1 / +15.2 / +4.3 | +2.6 / +14.7 / +4.3 | same signs, size differs | no | 0.21/0.43 / 0.74/0.38 / 0.74/0.14 |
| nA60>=1 skip | +36 / -36 / +7 (NOISE ONE-WEEK) | -28.4 / +10.8 / +7.5 | -11.1 / +11.7 / +5.7 | FLIP | no | 0.07/0.20 / 0.33/0.04 / 0.31/0.06 |
| nA40>=1 skip | +5 / -5 / -4 (NOISE (v1.2 assumed); sA40>=1 pub: 36/0/-5 NOISE ONE-WEEK) | -15.0 / +6.8 / +9.6 | -16.8 / +8.6 / +9.8 | FLIP | no | 0.12/0.25 / 0.18/0.03 / 0.33/0.08 |

## Caveats
- First-order lots; replay features not the V13T SET8 lines (skip leads not reproduced); half-type cells halve 70-95%% of trades so a drawdown cut is expected from exposure alone, which the placebo and family null are there to price; entries not live-matched; PRE-PROOF.
