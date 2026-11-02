
## S4a section (appended): phase-averaged cuts, V13X, K=5 lock-reset phases (week key shifted -2..+2 label days; Z3 estimator), cut of weekly-cumulative maxDD vs the shipped V13X layer at the same phase
Mask (all cells): poi_core.features(stream parquet, D7 engine d rows)[:,0] (fresh-ahead distance) <= D; HALF frame: minus the rows already in the shipped 7-line layer (z7); SKIP frame: all fired rows. 'vol' in S4a tables = planned-LOT volume share acted on (HALF counts 0.5), not a row share: SWG|f3L|15s D40 half fires on 42,423 of 88,490 rows (38.6k after removing z7), = 24 % of planned lot volume halved.
| cell (lock none) | L6M by phase s=-2..+2 | mean | PRE by phase | mean | X' by phase | mean |
|--|--|--|--|--|--|--|
| SWG f3L 15s D40 half | +.51 +.44 +.45 +.41 +.40 | +.44 | +.08 +.18 +.06 +.16 +.12 | +.12 | +.39 +.24 +.41 +.46 +.45 | +.39 |
| EQL tight 5m D40 skip | +.12 +.12 +.14 +.11 +.13 | +.12 | +.13 +.05 +.11 +.11 +.11 | +.10 | +.43 +.41 +.41 +.37 +.34 | +.39 |
| FIB ote705_dn 15m D20 skip | +.10 +.14 +.17 +.14 +.17 | +.14 | +.19 +.09 +.11 +.16 +.18 | +.15 | +.01 -.11 +.07 +.13 +.09 | +.04 |
| MAS bb_mid 4h D20 skip | +.08 +.15 +.12 +.09 +.02 | +.09 | +.08 +.08 +.07 +.08 +.08 | +.08 | +.09 -.01 +.11 +.08 +.02 | +.06 |
Equal-risk (lot scale so ALL worst-20 = base, lock none): SWG f3L 15s D40 half cut L6M +.12, PRE -.39, X' +.15 (S4a, stage 2): the same sign as Z3's equal-risk PRE worse. With lock 12 the same cells lose their PRE/X' cuts (see DS3_ZONES_3_S4A.md section 12).


# Z3 section - PHASE-AVERAGED drawdown estimator (written ~10:00Z 2026-11-02; V13X; no PASS claims; S4a section above/below is its own)
**Method.** Lock phase = the week key of every label day shifted by s in {-2,-1,0,+1,+2} label days (the combined 12R lock and the per-book week floors reset on different days). Each variant is run at all 5 phases; the cut vs the shipped layer is computed PAIRED at the same phase and then averaged (PA cut); spread = SD across phases. The PA noise band = 95th percentile of |PA cut| of information-free perturbations (random 2% / 5% of live rows halved), 40 draws x 5 phases per frame. Files `out/zones3/s3_v13x/phase_*.pkl|csv`, code `zones3_s3/phase9*.py`, `phase_an.py`.
## 1 The phase alone is the dominant noise
Shipped-layer maxDD across the 5 phases (mean, SD, range $k): lock-off L6M 150 (10.6; 133-164), PRE 183 (6.6; 173-191), X' 135 (15.1; 119-162), MID 55 (5.8; 46-63); lock 12R L6M 104 (23.1; 74-140), HOLD 118 (16.9; 88-140), MID 57 (24.0; 21-83), PRE 190 (47.0; 118-252), X' 118 (48.2; 50-174). A +-2-day shift of the 12R lock reset moves the shipped maxDD by up to a factor 2 (PRE 118k to 252k); the lock-off frame is 3-8x calmer. Any single-phase 12R maxDD is a draw from this spread.
## 2 Phase-averaged noise band (95th pct |PA cut|), HEADLINE lock-off
| window | flip 2% | flip 5% | SD of PA cut (flip 2%) | n draws |
|---|---|---|---|---|
| L3M | 0.206 | 0.221 | 0.095 | 40 |
| L6M | 0.127 | 0.177 | 0.062 | 40 |
| HOLD | 0.121 | 0.166 | 0.060 | 40 |
| MID | 0.198 | 0.324 | 0.088 | 40 |
| PRE | 0.180 | 0.302 | 0.083 | 40 |
| X | 0.127 | 0.186 | 0.067 | 40 |

Lock 12R:
| window | flip 2% | flip 5% | SD of PA cut (flip 2%) | n draws |
|---|---|---|---|---|
| L3M | 0.081 | 0.119 | 0.040 | 40 |
| L6M | 0.103 | 0.176 | 0.054 | 40 |
| HOLD | 0.085 | 0.125 | 0.046 | 40 |
| MID | 0.174 | 0.255 | 0.086 | 40 |
| PRE | 0.119 | 0.139 | 0.051 | 40 |
| X | 0.170 | 0.162 | 0.074 | 40 |

Compared with the single-path band (flip 2% / 5%): lock-off L6M 16/21 -> PA 13/18, PRE 22/26 -> PA 18/30, X' 15/25 -> PA 13/19 (modest shrink); lock 12R L6M 31/37 -> PA 10/18, PRE 21/28 -> PA 12/14, X' 21/29 -> PA 17/16 (large shrink: most 12R noise is lock phase). Rule on the PA statistic: PA cut > PA band in L6M AND in PRE or X'.
## 3 Shipped layer vs no layer vs 12 random same-size half-lot layers (phase-averaged, paired; rank = share of random layers the shipped layer beats)
Lock-off: shipped reduces maxDD vs none by +2% L6M, +2% HOLD, +36% MID, +16% PRE, +24% X'; random layers +18 / +9 / +20 / +9 / +13%; ranks 0.42 / 0.42 / 0.75 / 0.67 / 0.75; ulcer ranks 0.33 / 0.33 / 0.67 / 0.75 / 0.50; CVaR-10% ranks 0.33 / 0.50 / 0.33 / 1.00 / 0.75. Lock 12R: shipped -6 / -2 / +21 / +15 / +25% vs random +9 / +3 / +4 / +8 / +12%; ranks 0.42 / 0.25 / 0.92 / 0.75 / 0.83. **The shipped layer is not distinguishable from a random same-size half-lot layer in L6M/HOLD in either frame and only weakly better in MID/PRE/X' (n = 12 layers; the one rank of 1.00 is CVaR-10% in PRE).** Its benefit is the older windows, consistent with the earlier smooth-measure result.
## 4 Phase-averaged cuts of the leads (vs shipped; mean change in L6M)
Lock-off (headline), Z3 cells: ALL7 skip L6M +0.2% PRE -5% X' -7%; ALL7 re-target L6M +23% (+-3) L3M +44% but PRE -44% MID -45% X' -60%; OTE705 skip L6M -5%; kijun1h wt L6M -15% X' +24%; camH3 wt -10%; bar4hmid wt L6M +6.7% PRE -1.7% X' -23%; O62_30 d5 L6M -2% X' -25%. **No Z3 cell is above the PA band in L6M AND (PRE or X').**
Other agents' masks re-run phase-averaged (lock-off):
| lead | L3M | L6M | HOLD | MID | PRE | X' | mean change L6M ($/wk) |
|---|---|---|---|---|---|---|---|
| S5 sopen40 half | +36% | +51% | +36% | +28% | +24% | +9% | -7212 |
| S5 open20 half | +18% | +53% | +53% | +35% | +29% | -2% | -12196 |
| S5 nA60>=1 skip | -6% | +44% | +35% | +29% | -1% | +31% | -7100 |
| S5 openA40 half | +24% | +36% | +36% | +17% | +38% | +28% | -9410 |
| S5 rho60>=2 skip | -15% | +46% | +25% | -1% | +7% | +27% | -478 |
| S4A DEV|day_L|so_far D40 half | +49% | +60% | +21% | +12% | -41% | +26% | -174 |
| S4A DEV|on_L|so_far D20 half | +35% | +50% | +34% | +7% | -19% | +25% | +1809 |
| S4A SWG|f3L|15s D40 half | +21% | +44% | +33% | +3% | +12% | +39% | -1908 |
| S4A ARR|iplFVG|15s D20 skip | -38% | +53% | +37% | +10% | -39% | +43% | +857 |
| S4A ARR|iplFVG|15s D40 half | +20% | +42% | +40% | +23% | -27% | +27% | +186 |
| S4A FIB|ret50|1h D40 skip | -30% | +13% | +13% | -3% | -6% | +24% | +142 |
| S4A MAS|bb_mid|4h D20 skip | +14% | +10% | +9% | +8% | +7% | +13% | +611 |

Lock 12R:
| lead | L3M | L6M | HOLD | MID | PRE | X' | mean change L6M ($/wk) |
|---|---|---|---|---|---|---|---|
| S5 sopen40 half | +16% | +36% | +27% | -24% | +4% | -18% | -6997 |
| S5 open20 half | +40% | +47% | +52% | +36% | +32% | +4% | -9711 |
| S5 nA60>=1 skip | +12% | +29% | +23% | +5% | +11% | -48% | -5425 |
| S5 openA40 half | +31% | +24% | +33% | +43% | +29% | +16% | -7417 |
| S5 rho60>=2 skip | +18% | +28% | +24% | -20% | +6% | -4% | -2559 |
| S4A DEV|day_L|so_far D40 half | +22% | +34% | +19% | -1% | -32% | +21% | -2278 |
| S4A DEV|on_L|so_far D20 half | +6% | +11% | +11% | -13% | -17% | +22% | -2189 |
| S4A SWG|f3L|15s D40 half | -10% | +24% | +27% | +14% | +2% | +32% | -2305 |
| S4A ARR|iplFVG|15s D20 skip | +18% | +42% | +48% | +37% | -36% | +9% | +1184 |
| S4A ARR|iplFVG|15s D40 half | +20% | +26% | +21% | +16% | +1% | +27% | +999 |
| S4A FIB|ret50|1h D40 skip | -22% | -6% | -7% | -20% | -16% | -1% | -1812 |
| S4A MAS|bb_mid|4h D20 skip | -3% | -2% | +1% | +3% | +4% | -8% | -493 |

Band-passers in lock-off (PA flip-5 band L6M 17.7 / PRE 30 / X' 18.6): S5 openA40 half (L6M +36, PRE +38, X' +28; flags 66k of 88k rows = VOLUME, placebo ranks 0.55 / 0.95 / 0.60), S5 sopen40 and open20 half (rows 49k / 72k flagged: VOLUME), S4A SWG|f3L|15s D40 half (L6M +44, X' +39, PRE +12), S4A ARR iplFVG D20 skip (L6M +53, X' +43 but PRE -39, MID +10): see 5.
## 5 SWG|f3L|15s D40 half (S4a stream; the lead flag of 09:30Z) - resolved: VOLUME / FRAGILE, not a lead
* Mask: poi_core.features(stream, d)[:,0] <= 40 minus the 10,760 shipped-layer rows = 38,585 rows (43.6% of d rows; S4a confirmed the same mask; its '24%' is the planned-lot volume share with halves counted 0.5). Action half (extra_mult 0.5).
* Phase-averaged cut vs shipped, lock-off: L3M +21, L6M +44, HOLD +33, MID +3, PRE +12, X' +39% (S4a: L6M +44, PRE +12, X' +39: identical); lock 12R: -10 / +24 / +27 / +14 / +1.5 / +32%.
* Equal-risk (lots x1.372 so ALL-window worst-20 equals the shipped layer's), lock-off, phase-averaged (cell vs shipped: mean | maxDD $k | Calmar | ulcer $k): L6M 31.7k vs 26.4k | 123 vs 150 (-18%) | 0.26 vs 0.18 | 56 vs 72; HOLD 26.6k vs 24.2k | 143 vs 150 | 0.19 vs 0.16; MID 13.7k vs 12.9k | 74.7 vs 54.5 (+37% worse) | 0.21 vs 0.24 | 36 vs 24; PRE 8.2k vs 9.6k | 231.6 vs 183.1 (+27% worse) | 0.036 vs 0.053 | 93 vs 81; X' 0.4k vs -1.0k | 113 vs 135 (-16%) | 0.004 vs -0.008. S4a's equal-risk (its own scaling): L6M +12%, PRE -39%, X' +15% (same sign: PRE worse). **No-harm check FAILS: PRE and MID are worse than -band at equal risk.**
* Volume-matched placebo (100 draws; the same number of rows per book x session as the real mask, i.e. 38.6k rows halved at random, minus shipped-layer rows; 5 phases each; rank = share of placebo draws the real PA cut strictly beats; 'share at least as good' = 1 - rank approx): lock-off L3M 0.89, L6M 0.82 (placebo mean cut +26.5%), HOLD 0.75, MID 0.47, PRE 0.62, X' 0.95 (placebo mean +8.6%); lock 12R (15 draws) L6M 0.87, HOLD 0.93, MID 0.67, PRE 0.40, X' 1.00. A random half-lot layer of the same row count already cuts the L6M maxDD by 26% on average in lock-off: the L6M cut is VOLUME.
* Definition sensitivity (half, lock-off, PA cut): D 15 / 20 / 30 / 50 / 60: L6M +45 / +52 / +58 / +44 / +43%, X' +27 / +33 / +33 / +39 / +39%, PRE -16 / -41 / +2 / +5 / +10%, MID -8 / -3 / -12 / -1 / +3%. L6M and X' are stable in D (volume), PRE flips sign with D (FRAGILE in PRE). Skip instead of half: PRE -13..-39%, MID -59..-210% (much worse).
* Mirror (swing HIGH f3H 15s, half): L6M +6 / +5 / -13%, X' -11 / -17 / -10%, PRE +8 / +12 / +13% at D 20 / 30 / 40: the support-side (swing-low) lines carry the recent cut, the resistance-side mirror does not; its PRE is mildly positive.
* One-week check (lock-off, drop each of the 5 worst weeks of the shipped drawdown episode, per phase): L6M cut stays +31..+42%, X' +12..+39%, PRE -5..+19% (lock 12R: L6M falls to -18..+23%).
**Verdict: VOLUME / FRAGILE. The L6M cut equals what a random half-lot layer of the same size gives (rank 0.82), PRE is not significant (rank 0.62, sign flips with D) and is 27% worse at equal risk, X' alone reaches rank 0.95 (one window of six). The 09:30Z flag is withdrawn as a lead; keep as a weak X'-only candidate.**
## 6 Answer to the lead's question
Does anything survive the phase-averaged band in L6M AND PRE or X' and also a volume-matched placebo and the equal-risk check? **No** (lock-off headline and lock 12R). Passing the PA band is easy for any lot-reducing layer (S5 open masks, SWG f3L, ARR iplFVG skip); none of them is distinguishable from a random half-lot layer of the same row count in L6M and none passes the equal-risk no-harm check in PRE and MID. The shipped layer itself is also within the random-layer distribution in L6M/HOLD.
## 7 Rank convention
rank = share of placebo (or random-layer) draws that the real cell's phase-averaged cut strictly beats; 'share at least as good' = share of draws with cut >= real. 100+ draws for the SWG cell lock-off, 15 lock 12R, 12 random layers for the shipped layer, 20 draws for the other leads (S5, S4A) in phase_plc2_table_L0.csv (ranks 0.55-0.95).


# Z3 section 2 - V13Y (fixed base) phase-averaged results (written ~09:55Z 2026-11-02; supersedes the V13X numbers of the Z3 section above)
* Noise band: see DS3_ZONES_3_NOISE.md V13Y section (K=9, 50 draws): lock-off flip2/flip5 L6M 15.5/20, PRE 11.5/16, X' 14/22 %; lock 12R L6M 11/25, PRE 13/15, X' 10/13 %.
* Shipped layer vs 12 random same-size layers: lock-off maxDD ranks L6M 0.33, HOLD 0.33, MID 0.75, PRE 0.92, X' 0.58 (CVaR PRE 1.00, X' 0.83); lock 12R L3M 0.17, L6M 0.33, HOLD 0.42, MID 0.92, PRE 0.83, X' 0.50.
* Phase-averaged cuts of the Z3 leads on V13Y (lock-off, K=9, vs shipped): ALL7 skip L6M -10% PRE -1% X' +10%; ALL7 re-target L6M +4% PRE -41%; OTE705 skip L6M -6% X' +12%; kijun1h wt L6M +3.6% (SD 0.3%) PRE -4.5% X' +6.7%; camH3 wt L6M -6% PRE +2.5% X' +7.6%; bar4hmid wt L6M +3.2% PRE -1.3% X' -1.3%. Lock 12R: ALL7 re-target L6M +23% (SD 18%) X' -25%; O62_30 d5 L6M +21% (SD 8%), PRE +2%, X' 0%; others |cut| < 8%. **None is above the V13Y phase-averaged band (lock-off L6M 15.5-20%, PRE 11.5-16%, X' 14-22%) in L6M AND PRE or X'.**

# Z3 section 3 - V13Y: the two MEAN-type leads on smooth measures, and O62_30 d5 (written ~11:10Z 2026-11-02; phase-averaged K=9 for the mean leads, K=5 for O62_30 d5; band = V13Y phase-averaged noise band + smooth-measure bands in `out/zones3/s3_v13y/smooth_band.csv`)
Masks: BT = ZL-1 `mask_BT_swing_F10_4h_D40.npy` (2,819 rows), LP = ZL-2 `A40|TLP_p25_4h` from `ds3_zl/features_tape/masks_cells_new.npz` (5,110 rows; the cell ZL-2 scores as A40__TLP_p25_4h__skip; if its LP_AGAINST variant is a different file the owner should re-send the path), UNION = BT | LP; action skip (extra_skip). Equal-risk = lot search so the ALL-window worst-20 equals the shipped layer's (tolerance 1.5%).
**Lock-off (headline), vs shipped, phase-averaged (cut = maxDD cut; ulcer / CVaR-10% / mean = change, $k per week; ulcer < 0 and CVaR > 0 are improvements):**
| mask | window | maxDD cut | ulcer | CVaR-10% | mean |
|---|---|---|---|---|---|
| BT | L6M / HOLD / MID / PRE / X' | -11.8 / -11.4 / +24.4 / +2.8 / -11.2% | +4.3 / +0.7 / -4.6 / -1.2 / +0.8 | -5.0 / -2.5 / +7.0 / -0.8 / +1.0 | +1.8 / +1.8 / +2.7 / +1.3 / +0.7 |
| LP | L6M / HOLD / MID / PRE / X' | +18.6 / +12.5 / -17.8 / +8.9 / +3.5% | -11.5 / -6.5 / -0.1 / -6.2 / +4.8 | +6.9 / +0.3 / -1.4 / +0.3 / +0.2 | +3.2 / +1.8 / +1.0 / -0.5 / -1.7 |
| UNION | L6M / HOLD / MID / PRE / X' | +10.2 / +6.6 / +10.5 / +14.3 / -1.4% | -8.0 / -6.9 / -4.1 / -8.1 / +3.1 | -0.2 / -2.2 / +4.4 / -0.4 / -0.2 | +4.9 / +3.5 / +3.1 / +0.9 / -1.5 |
Noise bands, lock-off (flip 2% / flip 5%): maxDD L6M 15.7/19.9%, PRE 11.4/17.4%, X' 15.9/23%; ulcer L6M 9.4/11.8k, HOLD 5.3/7.5k, PRE 5.9/8.9k, X' 3.7/6.1k; CVaR-10% L6M 4.4/5.2k, HOLD 3.0/4.1k, PRE 1.5/3.5k; mean L6M 1.5/2.8k, HOLD 1.1/2.0k, PRE 0.75/1.4k.
* Equal-risk lot scale in lock-off = 1.00 for all three (the skipped rows are not in the worst-20 weeks), so the equal-risk mean = the unit-lot mean change above: BT +1.8k (L6M), LP +3.2k, UNION +4.9k per week.
* **BT: improves the mean but NOT the risk measures** (L6M maxDD -12%, ulcer +4.3k, CVaR -5.0k): a mean-only lead, confirming ZL-1.
* **LP: improves the smooth measures lock-off in L6M and PRE** - ulcer -11.5k (band 9.4-11.8k) L6M, -6.2k PRE (band 5.9-8.9k), HOLD -6.5k (5.3-7.5k); CVaR +6.9k L6M (band 4.4-5.2k, passes), mean +3.2k L6M (band 1.5-2.8k, passes) - but the maxDD cut (L6M +18.6%, PRE +8.9%) is below its band, MID -17.8%, X' ulcer +4.8k (worse), mean -0.5k PRE / -1.7k X'. At the flip-2 band LP passes ulcer in L6M, HOLD, PRE and CVaR/mean in L6M; at the flip-5 band it is on the line. **Label: smooth-measure LEAD-weak, lock-off only (L6M=HOLD one episode; X' and MID do not agree).**
* UNION: ulcer -8.0 / -6.9 / -8.1k (L6M / HOLD / PRE; band 9.4/5.3/5.9 at flip 2%: passes HOLD and PRE only), maxDD cut +10 / +7 / +14%, mean +4.9k L6M, +0.9k PRE: **both skips together improve ulcer in L6M, HOLD, PRE and the mean without hurting CVaR much, but nothing clears the maxDD band; X' is flat/worse.** Risk-adjusted: yes in ulcer terms at the flip-2 band, no at the flip-5 band; it is not a drawdown lead.
* Lock 12R (frame in which the single-path noise is 3x larger): BT worse on every measure (L6M maxDD -26%, ulcer +12k); LP flat (+6% L6M, ulcer -1.7k, PRE -3%); UNION flat/worse; equal-risk lot scales 1.02 / 1.06 / 1.11 and the equal-risk UNION is -16% L6M / -24% PRE: **the 12R frame does not show the LP/UNION smooth-measure gain (LOCK-OFF-ONLY).**
**Answer: skipping BT and/or LP rows improves the MEAN (BT +1.8k, LP +3.2k, both +4.9k per week in L6M), and LP (and the union) improves ulcer/CVaR in L6M and PRE in the lock-off frame at the lower band, but not maxDD beyond the band and not in the 12R frame; the equal-risk statement is the same (worst-20 is unchanged by these skips). Mean-type, not drawdown-type.**
## O62_30 d5 on V13Y (OTE-62 unit re-fired 5 minutes later), lock-off, phase-averaged K=5, matched placebo 30 draws (same number of rows per book x session x td-bin x side stratum from the non-zone pool, distances from the unit's own pool, d5 applied; the shipped B73 is kept on the real OTE-62 rows in the placebo - approximate)
| window | PA cut (SD over phases) | placebo mean / rank | band flip-5 | mean change | equal-risk ulcer |
|---|---|---|---|---|---|
| L3M | +27.4% (1.9) | -33% / 1.00 | 33.5% | +3.6k | -6.3k |
| L6M | +23.2% (1.1) | -5.6% / 0.90 | 19.9% | +2.8k | -16.6k |
| HOLD | +20.2% (5.1) | -7.8% / 1.00 | 19.1% | +1.4k | -10.0k |
| MID | -47.1% (28.4) | -6.4% / 0.00 | 36.6% | -1.2k | +3.0k |
| PRE | -3.1% (3.2) | -3.9% / 0.30 | 17.4% | -0.2k | +1.4k |
| X' | +5.7% (1.4) | -3.9% / 0.93 | 23.0% | +0.8k | -1.7k |
Equal-risk lot scale 1.00 (worst-20 unchanged), so equal-risk = unit lots. **L6M, HOLD, L3M clear the band and beat the matched placebo (0.90 / 1.00 / 1.00); PRE is flat (-3%), X' +6% is below band, and MID is -47% (placebo rank 0.00, below -band): the no-harm check fails in MID and the rule (PRE or X' above band) fails.** L6M = HOLD is the same recent episode (the ONE-WEEK drop test was not run for this cell). Label: (recent windows only), MID-harm; not a lead; 12R: L6M +21%, PRE +2%, X' 0% (K=9, no placebo).

# Z3 section 4 - S5 sopen40 half decided properly (V13Y, lock-off, phase-averaged K=9; written ~11:35Z 2026-11-02): VOLUME + EQUAL-RISK-HARM, not a survivor
Mask `S5/masks/mask_sopen40.npy` (48,862 rows = 55.2%, halve lots). (1) SIZE-MATCHED NULL: 60 random half-lot layers with the same number of rows per book x session x td-bin x side stratum, 9 phases each. Null cut mean / SD / 95th pct |cut|: L3M -10% / 27% / 51%; L6M +33% / 19% / 61%; HOLD +23% / 12% / 37%; MID -31% / 36% / 89%; PRE -4% / 25% / 57%; X' +14% / 24% / 46%. Real sopen40 PA cut and rank among the null: L3M +40% (0.98), L6M +53% (0.83), HOLD +22% (0.47), MID -18% (0.63), PRE +15% (0.83), X' +24% (0.62). Inside the size-matched band in L6M, PRE and X'.
(2) EQUAL-RISK (lots x1.274 so ALL-window worst-20 equals shipped), PA K=5, vs shipped (mean | maxDD | Calmar | ulcer): L6M 23.4k vs 27.8k | 69.9k vs 116.2k (-40%) | 0.34 vs 0.24 | 30.6k vs 56.3k; HOLD 22.3k vs 24.6k | 98.9k vs 117.5k (-16%) | 0.23 vs 0.21; MID 15.2k vs 17.9k | 45.3k vs 30.1k (+50% worse) | 0.34 vs 0.60; PRE 5.6k vs 11.7k (-52%) | 169k vs 137k (+23% worse) | 0.033 vs 0.085 | 71.5k vs 61.5k; X' 3.4k vs 2.3k | 71.5k vs 75.1k | 0.048 vs 0.031. Against 10 random 55% layers each at its own equal-risk scale (1.09-1.38; phase 0; share of random layers the real cell beats): maxDD L6M 0.70, HOLD 0.80, MID 0.90, PRE 0.90, X' 0.60; ulcer 0.80/0.80/0.80/0.30/0.50; mean 0.20/0.20/0.40/0.00/1.00; Calmar 0.60/0.60/0.70/0.20/1.00. A little better than a random volume cut on maxDD, clearly worse than the shipped layer in PRE and MID (no-harm fails), lower mean than random layers in L6M/HOLD/PRE.
(3) Leave-episode-out (V13Y lock-none top-3 episodes per window, DS3_ZONES_EPISODES_V13Y.md; weeks peak..trough dropped): L6M 53% -> 51% (drop W27-38), 53% (W20-23), 53% (W40-42), all three 26% (null 18.5%); PRE 15.5% -> 11.5 / 27 / 15%, all three 7% (null -22%); X' 24% -> 29 / 24 / 24%, all three -9% (null -29%); HOLD 22% -> 53% (drop W05-07/2026), -0.6% (drop the Sept episode W27-38), 22%: the HOLD/L6M cut is carried by the Sept 2026 episode.
(4) Per book x session (phase 0, unit lots, d_mean $/wk and maxDD ship -> cell $k): L6M PE -3.8k (104 -> 54), HM -2.3k, KB -1.2k, SM -0.4k, MV/PB +0.1k; Asia -7.7k (64 -> 31), London -0.2k (70 -> 40), NY-AM -0.5k, NY-PM +0.9k (49 -> 25). PRE: PE -5.4k (126 -> 112), KB -0.7k; Asia -3.2k, NY-AM -4.0k (68 -> 40), London +0.6k. X': PE +1.7k (93 -> 67), NY-AM +1.2k.
**Verdict: VOLUME (size-matched null) + EQUAL-RISK-HARM (PRE, MID). Not a survivor; do not flag.**

# Z3 section 5 - LP_AGAINST natural masks and the S4A band-passers missing on V13Y (written ~12:20Z 2026-11-02; V13Y, K=9 phase-averaged, vs shipped; PA noise band flip-2 / flip-5 and smooth-measure bands from `smooth_band.csv`)
**LP natural-reading masks (lock-off, headline; unit lots = equal-risk, lot scale 1.00):**
| mask | rows | maxDD cut L6M / HOLD / MID / PRE / X' | ulcer L6M / PRE / X' ($k) | CVaR-10% L6M ($k) | mean L6M / PRE ($k/wk) |
|---|---|---|---|---|---|
| ZL-2 LP_AGAINST fixscan | 2,081 | +12.4 / +9.9 / -16.1 / +2.5 / -13.7% | -7.5 / -5.2 / +2.6 | +2.4 | +1.8 / +0.7 |
| ZL-1 clean-room primary | 1,937 | +9.7 / +7.9 / -16.1 / +4.2 / -13.8% | -6.6 / -6.3 / +4.8 | -0.0 | +1.7 / +0.4 |
| BT + LP_AGAINST | | +2.1 / -0.2 / +13.6 / +4.3 / -15.6% | -2.4 / -4.8 / +1.7 | -3.2 | +3.3 / +1.8 |
Bands (lock-off, flip-2 / flip-5): maxDD L6M 16/20, PRE 11/17, X' 16/23; ulcer L6M 9.4/11.8k, PRE 5.9/8.9k; CVaR L6M 4.4/5.2k; mean L6M 1.5/2.8k, PRE 0.75/1.4k. **The natural-reading LP_AGAINST masks are weaker than the any-side LP mask (A40|TLP_p25_4h): maxDD below band, ulcer improvement just under the flip-2 band, CVaR below band, mean +1.7-1.8k (about the flip-2 mean band), X' worse (-14%, ulcer +2.6..+4.8k). Lock 12R: LPAG L6M +7.5%, PRE +10.6% (band 13%), ulcer PRE -9.2k (band 9.1k at flip 2): nothing beyond band. Verdict: mean-type with a weak ulcer gain in L6M and PRE, X' contradicts; not a drawdown lead.**
**S4A cells that were band passers on the V13X defect base and were missing on V13Y (K=9):** lock-off ARR|iplFVG|15s D20 half: L6M +28%, PRE -59%, X' +23% (not a pass); SWG|f3L|15s D20 half: L6M +48%, PRE -11%, X' +22% (fails: X' just under 23%, PRE negative); DEV|on_L|so_far D40 half: L6M +61%, HOLD +5%, MID -43%, PRE -46%, X' +26% (nominal band pass via X', FRAGILE: PRE and MID badly negative). Lock 12R: ARR D20 half L6M +20%, PRE -25%; SWG D20 half L6M +10%, X' +40%; DEV on_L D40 half L6M +47%, PRE -13%, X' +21% (nominal pass, PRE negative).
