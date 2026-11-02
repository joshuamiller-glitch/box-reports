
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
