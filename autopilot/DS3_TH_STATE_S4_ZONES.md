# DS3_TH_STATE_S4_ZONES - S4: the zone layer on the TH-L2-S engine base (S345-RUN, 2026-11-09)

**Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF**

**Summary (zone layer, FIRST-ORDER lots scaling, replica PoiSet features; 100-draw placebos)**
- The live zone half itself (ZOFF = undo it): cut -1.0 / -2.5 / -19.1% on L6M / PRE / X' (S1-COMB): undoing it deepens drawdown; UNIF and PLAIN6060 the same sign on PRE and X'.
- Half-type leads (open20 / open40 / open60 / openA40 / openA60 / sopen40 half) keep a positive cut on every window of every base (one exception: open60 half HOLD on PLAIN6060, -8.4%): S1-COMB L6M +26 to +36%, PRE +36 to +42%, X' +17 to +30%, HOLD +5 to +30%. They halve 47-81% of all trades, so the mean falls by 2.6k-9.2k/wk on L6M (S1-COMB) and the placebo (same count at random within book x session) is the test: ranks L6M / PRE open20 0.69 / 0.69, openA40 0.71 / 0.85, sopen40 0.82 / 0.91, open40 0.93 / 0.83, open60 0.94 / 0.98 on S1-COMB; open40 0.98 / 0.97 and open60 0.93 / 0.98 on PLAIN6060, open60 0.95 / 0.99 on S1-UNIF. Only open40 / open60 reach ranks near or above 0.95, on PRE for open60 on all three bases; the others remain inside the VOLUME band (random halving gives a similar cut).
- Skip-type leads (nA20 / nA40 / nA60 >= k, rho60 >= 2) do not survive: L6M cut is negative or zero on S1-COMB (nA40>=1 -15%, nA60>=1 -28%, rho60>=2 -20%) with placebo ranks 0.05-0.22; PRE is positive but small (+7 to +15%) and the ranks are 0.2-0.4. The same flip is already present on the replica HOLD base (S345_PREP: nA60>=1 L6M +1.8, rho60>=2 +16.7 vs published +36 / +41), so it is not caused by the TH-L2-S cut: the V13T 8-line freshness features and the replica PoiSet differ and the skip results do not tie across engines.
- Versus the published V13Y verdicts: openA40 half TIES; open20, open60, sopen40 half same signs but PRE much larger on this base; rho60>=2, nA60>=1 and nA40>=1 skips FLIP on L6M (nA60>=1 also on PRE: published -36, new +11). No lead is labelled above VOLUME/NOISE: halving cuts DD mostly by cutting risk, placebo ranks stay below 0.95 except open40 / open60.
- Caveats: zone features come from the replica PoiSet replay (88.9% agreement with the zone half inferred from base lots; V13T feats.npz matches only 46-71% of the replica signals); pnl at the new lots is per-lot scaling (first-order; the exact engine zone-half re-run was not built); entries not live-matched.

Zone features: the replica own PoiSet (8 live lines) replayed on the 1-min bars at each trade signal second (not the V13T feats.npz, which matches only 46-71% of replica signals). Replay vs the half inferred from base lots: agree S1-COMB 89.0%, S1-UNIF 88.9%, PLAIN6060 88.9%.
Reference = the base as it stands (its live zone HALF inside the lots). Half cells halve lots (rounded, min 1) on top of the live half; skip cells drop the signal. Placebo: same count at random within book x session, 100 draws, rank = share of draws with a smaller maxDD cut. Cuts are carrying-week-dropped; mean effects are per week.


## S1-COMB

Table (S1-COMB): maxDD cut vs the base zone layer by window (+ = shallower), mean change, placebo ranks. Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF

| cell | share of trades | L1M cut% | L2M cut% | L3M cut% | L6M cut% | HOLD cut% | MID cut% | PRE cut% | X' cut% | d mean L6M/PRE | placebo rank L6M/PRE |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ZOFF | 0.07 | -11.3 | -11.3 | -11.3 | -1.0 | -12.5 | +2.6 | -2.5 | -19.1 | +2062 / -79 |  |
| ZREPLAY | 0.15 | -7.9 | -7.9 | -7.9 | -4.4 | -6.5 | +18.9 | +0.9 | -5.3 | +380 / +179 |  |
| open20 half | 0.81 | +47.4 | +47.4 | +47.4 | +35.6 | +24.5 | +24.5 | +42.2 | +28.4 | -9166 / -4587 | 0.69 / 0.69 |
| open40 half | 0.61 | +48.4 | +48.4 | +48.4 | +34.9 | +19.5 | +24.5 | +37.2 | +19.1 | -5244 / -3067 | 0.93 / 0.83 |
| open60 half | 0.47 | +45.5 | +45.5 | +45.5 | +26.3 | +5.4 | +26.7 | +36.1 | +24.4 | -2593 / -1686 | 0.94 / 0.98 |
| openA40 half | 0.73 | +55.5 | +55.5 | +55.5 | +35.5 | +29.6 | +29.6 | +39.8 | +30.4 | -6364 / -4054 | 0.71 / 0.85 |
| openA60 half | 0.65 | +52.2 | +52.2 | +52.2 | +33.0 | +25.4 | +25.4 | +37.9 | +17.2 | -5890 / -3478 | 0.88 / 0.82 |
| sopen40 half | 0.58 | +38.9 | +38.9 | +38.9 | +26.3 | +8.1 | +22.6 | +37.9 | +20.0 | -3569 / -3296 | 0.82 / 0.91 |
| nA20>=2 skip | 0.04 | -5.4 | -5.4 | -5.4 | +0.0 | +0.1 | +0.1 | -0.8 | +14.5 | +493 / -246 | 0.54 / 0.30 |
| nA20>=3 skip | 0.01 | +1.3 | +1.3 | +1.3 | +0.0 | +0.0 | +0.0 | +0.0 | -2.5 | +322 / -277 | 0.38 / 0.34 |
| nA40>=1 skip | 0.27 | -26.7 | -26.7 | -26.7 | -15.0 | +13.5 | +28.1 | +6.8 | +9.6 | -10972 / -3384 | 0.16 / 0.21 |
| nA40>=2 skip | 0.11 | -13.1 | -13.1 | -13.1 | -2.6 | +7.7 | +31.7 | -2.2 | +22.5 | -2300 / -67 | 0.63 / 0.18 |
| nA40>=3 skip | 0.04 | -2.2 | -2.2 | -2.2 | +0.0 | +0.9 | +17.7 | +0.0 | +16.7 | -189 / -875 | 0.62 / 0.30 |
| nA60>=1 skip | 0.35 | -41.3 | -41.3 | -41.3 | -28.4 | -10.1 | +58.1 | +10.8 | +7.5 | -12152 / -4444 | 0.11 / 0.32 |
| nA60>=2 skip | 0.16 | -13.6 | -13.6 | -13.6 | -10.0 | +20.1 | +20.9 | +3.2 | +30.2 | -3990 / -1484 | 0.22 / 0.26 |
| nA60>=3 skip | 0.07 | -7.0 | -7.0 | -7.0 | -0.7 | +3.2 | +22.1 | +0.7 | +30.3 | +437 / -1164 | 0.50 / 0.38 |
| rho60>=2 skip | 0.24 | -32.4 | -32.4 | -32.4 | -20.1 | -10.7 | +26.5 | +15.2 | +4.3 | -7262 / -1557 | 0.05 / 0.43 |

## S1-UNIF

Table (S1-UNIF): maxDD cut vs the base zone layer by window (+ = shallower), mean change, placebo ranks. Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF

| cell | share of trades | L1M cut% | L2M cut% | L3M cut% | L6M cut% | HOLD cut% | MID cut% | PRE cut% | X' cut% | d mean L6M/PRE | placebo rank L6M/PRE |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ZOFF | 0.07 | -3.5 | -3.5 | -3.5 | +1.5 | -9.4 | -9.4 | -7.4 | -26.4 | +2309 / +129 |  |
| ZREPLAY | 0.15 | +3.3 | +3.3 | +3.3 | -1.8 | +2.0 | +13.6 | -2.7 | -9.4 | +1443 / +273 |  |
| open20 half | 0.81 | +42.5 | +42.5 | +42.5 | +33.1 | +18.6 | +18.6 | +36.9 | +30.8 | -4942 / -4216 | 0.48 / 0.59 |
| open40 half | 0.62 | +39.9 | +39.9 | +39.9 | +31.8 | +9.3 | +9.3 | +40.6 | +27.7 | -1708 / -2504 | 0.92 / 0.90 |
| open60 half | 0.47 | +37.0 | +37.0 | +37.0 | +25.0 | +9.9 | +9.9 | +42.9 | +36.3 | +246 / -1062 | 0.95 / 0.99 |
| openA40 half | 0.73 | +44.3 | +44.3 | +44.3 | +36.0 | +13.4 | +13.4 | +43.7 | +31.6 | -2401 / -3204 | 0.83 / 0.92 |
| openA60 half | 0.65 | +42.7 | +42.7 | +42.7 | +29.7 | +11.1 | +11.1 | +44.7 | +21.6 | -2568 / -2573 | 0.75 / 0.97 |
| sopen40 half | 0.58 | +32.6 | +32.6 | +32.6 | +25.0 | +10.7 | +10.7 | +38.8 | +28.6 | -637 / -2848 | 0.75 / 0.94 |
| nA20>=2 skip | 0.04 | -1.4 | -1.4 | -1.4 | +0.0 | +2.3 | +7.5 | +0.0 | +10.7 | +470 / -248 | 0.42 / 0.45 |
| nA20>=3 skip | 0.01 | +0.0 | +0.0 | +0.0 | +0.0 | +1.2 | +1.2 | +0.0 | -2.7 | +259 / -122 | 0.35 / 0.43 |
| nA40>=1 skip | 0.27 | +1.0 | +1.0 | +1.0 | -3.9 | +25.7 | +53.7 | -11.2 | +17.4 | -7750 / -4374 | 0.24 / 0.05 |
| nA40>=2 skip | 0.11 | +4.8 | +4.8 | +4.8 | +0.4 | +15.5 | +26.3 | -8.9 | +17.6 | -711 / +158 | 0.39 / 0.07 |
| nA40>=3 skip | 0.04 | -2.9 | -2.9 | -2.9 | +0.0 | +6.5 | +13.8 | +0.0 | +16.9 | -427 / -625 | 0.45 / 0.37 |
| nA60>=1 skip | 0.35 | +4.9 | +4.9 | +4.9 | -2.1 | +27.0 | +64.1 | -10.2 | +26.4 | -7344 / -5561 | 0.15 / 0.06 |
| nA60>=2 skip | 0.16 | +9.0 | +9.0 | +9.0 | -5.7 | +18.7 | +21.8 | -1.4 | +30.9 | -1199 / -1257 | 0.21 / 0.21 |
| nA60>=3 skip | 0.07 | +0.8 | +0.8 | +0.8 | -0.5 | +6.3 | +7.9 | -0.4 | +17.0 | +1018 / -1289 | 0.47 / 0.28 |
| rho60>=2 skip | 0.23 | +6.8 | +6.8 | +6.8 | +7.6 | +21.7 | +53.4 | +1.5 | -11.0 | -3341 / -3257 | 0.47 / 0.18 |

## PLAIN6060

Table (PLAIN6060): maxDD cut vs the base zone layer by window (+ = shallower), mean change, placebo ranks. Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF

| cell | share of trades | L1M cut% | L2M cut% | L3M cut% | L6M cut% | HOLD cut% | MID cut% | PRE cut% | X' cut% | d mean L6M/PRE | placebo rank L6M/PRE |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ZOFF | 0.08 | -10.2 | -10.2 | -10.2 | -10.2 | -0.2 | -0.2 | -17.9 | -23.0 | +1429 / +55 |  |
| ZREPLAY | 0.15 | -4.4 | -4.4 | -4.4 | -4.4 | +12.4 | +12.4 | -9.3 | -7.5 | +327 / +185 |  |
| open20 half | 0.80 | +35.1 | +35.1 | +35.1 | +35.1 | +26.5 | +26.5 | +26.4 | +32.4 | -5464 / -3836 | 0.67 / 0.28 |
| open40 half | 0.61 | +38.5 | +38.5 | +38.5 | +37.2 | +9.9 | +9.9 | +39.0 | +26.3 | -1388 / -2368 | 0.98 / 0.97 |
| open60 half | 0.46 | +33.2 | +33.2 | +33.2 | +25.6 | -8.4 | +2.0 | +34.7 | +33.9 | +132 / -1021 | 0.93 / 0.98 |
| openA40 half | 0.73 | +40.0 | +40.0 | +40.0 | +40.0 | +18.6 | +18.6 | +37.5 | +31.8 | -1658 / -2952 | 0.93 / 0.90 |
| openA60 half | 0.65 | +33.3 | +33.3 | +33.3 | +32.9 | +13.7 | +13.7 | +40.6 | +22.4 | -2365 / -2299 | 0.85 / 0.99 |
| sopen40 half | 0.58 | +29.7 | +29.7 | +29.7 | +25.6 | +8.0 | +10.6 | +38.2 | +28.9 | -900 / -2783 | 0.65 / 0.95 |
| nA20>=2 skip | 0.04 | -2.3 | -2.3 | -2.3 | -2.3 | +5.6 | +5.6 | -1.0 | +10.8 | +438 / -159 | 0.41 / 0.59 |
| nA20>=3 skip | 0.01 | +0.0 | +0.0 | +0.0 | -0.0 | +0.0 | +0.0 | -3.5 | -2.4 | +340 / -196 | 0.49 / 0.29 |
| nA40>=1 skip | 0.27 | -1.5 | -1.5 | -1.5 | -1.5 | +27.7 | +44.5 | -24.8 | +22.0 | -11037 / -3631 | 0.20 / 0.03 |
| nA40>=2 skip | 0.11 | +3.6 | +3.6 | +3.6 | +1.0 | +28.5 | +28.5 | -7.5 | +16.2 | -1667 / +8 | 0.44 / 0.37 |
| nA40>=3 skip | 0.04 | -3.5 | -3.5 | -3.5 | -3.5 | +13.5 | +13.5 | -3.6 | +16.2 | -282 / -610 | 0.40 / 0.36 |
| nA60>=1 skip | 0.35 | +14.8 | +14.8 | +14.8 | +9.6 | +35.6 | +64.1 | -20.6 | +27.0 | -9509 / -4818 | 0.30 / 0.07 |
| nA60>=2 skip | 0.16 | +15.7 | +15.7 | +15.7 | -8.2 | +23.0 | +28.0 | -39.4 | +29.0 | -2635 / -1375 | 0.19 / 0.01 |
| nA60>=3 skip | 0.07 | +1.3 | +1.3 | +1.3 | +1.3 | +26.1 | +26.1 | +0.5 | +15.7 | +1316 / -1281 | 0.64 / 0.59 |
| rho60>=2 skip | 0.23 | +22.5 | +22.5 | +22.5 | +15.3 | +39.7 | +57.2 | +0.9 | -2.9 | -4995 / -2522 | 0.53 / 0.33 |

## Zone leads on the new base vs the published V13Y verdicts (ZONES3_LEAD_REGISTER, single path)

Tie = same sign on L6M and PRE and both within 20 points of the published cut; flip = sign change on L6M or PRE (new |cut| >= 5); otherwise same-sign-different-size. "Survives" = cut > 0 on L6M, HOLD, MID, PRE and X' on all three bases. nA40>=1 is compared with both published nA40>=1 (v1.2-assumed) and sA40>=1 rows. [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| lead | published V13Y L6M/PRE/X' (label) | new S1-COMB L6M/PRE/X' | verdict vs published | survives on all 3 bases | placebo rank L6M/PRE: COMB, UNIF, PLAIN |
|--|--|--|--|--|--|
| open20 half | +41 / +17 / +9 (VOLUME) | +35.6 / +42.2 / +28.4 | same signs, size differs | yes | 0.69/0.69 / 0.48/0.59 / 0.67/0.28 |
| open60 half | +42 / +4 / +33 (VOLUME) | +26.3 / +36.1 / +24.4 | same signs, size differs | no | 0.94/0.98 / 0.95/0.99 / 0.93/0.98 |
| openA40 half | +35 / +20 / +41 (VOLUME) | +35.5 / +39.8 / +30.4 | TIES | yes | 0.71/0.85 / 0.83/0.92 / 0.93/0.90 |
| sopen40 half | +41 / +11 / +21 (NOISE) | +26.3 / +37.9 / +20.0 | same signs, size differs | yes | 0.82/0.91 / 0.75/0.94 / 0.65/0.95 |
| rho60>=2 skip | +41 / +1 / +36 (VOLUME ONE-WEEK) | -20.1 / +15.2 / +4.3 | FLIP | no | 0.05/0.43 / 0.47/0.18 / 0.53/0.33 |
| nA60>=1 skip | +36 / -36 / +7 (NOISE ONE-WEEK) | -28.4 / +10.8 / +7.5 | FLIP | no | 0.11/0.32 / 0.15/0.06 / 0.30/0.07 |
| nA40>=1 skip | +5 / -5 / -4 (NOISE (v1.2 assumed); sA40>=1 pub: 36/0/-5 NOISE ONE-WEEK) | -15.0 / +6.8 / +9.6 | FLIP | no | 0.16/0.21 / 0.24/0.05 / 0.20/0.03 |

Live zone layer itself (ZOFF = undo the live half): cut -1.0 / -2.5 / -19.1 on L6M / PRE / X' (S1-COMB), so removing it deepens drawdown most in X'.
