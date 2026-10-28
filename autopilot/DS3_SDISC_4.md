# DS3_SDISC_4 - cross-session conditioning (T-SESSION-DISCOVER item 4), agent D3SD34, 2026-10-28
Same prereg (sha256 c1e96d73..., DECISIONS.md) and PREHOLD (sha256 85eda956e4183927d7a9619cb1c4d65c2a49543b53a0daaf73876a9b6cacfba5); gates are known at the session open; options chosen on PRE only; one HOLD+X look for the whole list.

## VERDICT
- **180 gated cells (30 top-5 cells x 6 gates): the PRE choice gains +1.09 pts/trade in-sample on average, the same gate gives -0.44 on HOLD and -0.03 on X: the gates do not carry over.** 12 of 180 are positive in HOLD and in both HOLD halves with a positive kept mean (chance for three independent coin flips is 22.5 of 180); 4 have a HOLD bootstrap CI above zero for the gated-minus-ungated difference (chance at 2.5%: 4.5), 2 of those also pass the three-leg test.
- By gate (HOLD median gated minus ungated, pts/trade): G1 -0.34; G2 +0.01; G3 -0.26; G4 -0.88; G5 -0.35; G6 +0.28. The ASIA-range-size gate generalised to every session (G1, source range vs trailing median) is -0.34 median in HOLD, 9/30 positive; **no session shows a quiet/wide split that survives HOLD**. Day-of-week (drop the worst PRE weekday) is the only gate with a positive HOLD median (+0.28) and it is inside the noise (MDE 3.3).
- **Sizing cells (LONDON outcome -> NY-AM lots, 1.5x / 0.5x on the PRE-better option, 15 cells): HOLD effect CI includes zero in all 15; 5 positive point estimates, 5 with a positive 2023 span; no sizing rule is supported.** (Best HOLD +2.4 pts/trade MDE 10.)
- The 12 gated cells that pass the three-leg test are listed below for completeness; none is carried forward (selected out of 180 cells; 2 have a CI above zero against about 4.5 expected by chance; X span mixed). New session books from item 4: 0.

## 1. Gate definitions as run
Known at the open of the ENTRY session (source = previous session per the prereg): G1 source range > trailing-60 median; G2 source close > open; G3 source swept the high or low of its own source (yes in 44% of LONDON days and 76-100% in the other sessions: nearly degenerate, disclosed); G4 source close > its VWAP; G5 entry-session open > source close (gap up); G6 weekday (drop the PRE-worst weekday). For each of the top-5 PRE-ranked cells per session (dedup, PRE-selected first) and each gate, the option with the higher PRE MEAS mean (>= 60 trades) is the gated cell. Effect = kept mean minus ungated mean in the same window, week-bootstrap CI (1,000 draws), MDE80 = 2.8 SD.

## 2. Summary by gate (180 cells)
| gate | cells | mean PRE gain (in-sample) | median HOLD diff | mean HOLD diff | mean X diff | HOLD+halves positive | HOLD CI > 0 |
|---|---|---|---|---|---|---|---|
| G1 | 30 | +1.59 | -0.34 | -0.58 | -0.32 | 2 | 1 |
| G2 | 30 | +1.29 | +0.01 | -0.34 | -0.14 | 2 | 0 |
| G3 | 30 | -0.03 | -0.26 | -0.15 | +0.09 | 2 | 1 |
| G4 | 30 | +1.48 | -0.88 | -0.95 | +0.05 | 1 | 0 |
| G5 | 30 | +1.19 | -0.35 | -0.73 | -0.28 | 2 | 0 |
| G6 | 30 | +1.05 | +0.28 | +0.09 | +0.43 | 3 | 2 |

## 3. By session (180 cells; HOLD mean gated minus ungated)
| session | cells | mean HOLD diff | positive in HOLD | positive in X |
|---|---|---|---|---|
| ASIA | 30 | -0.45 | 10 | 12 |
| LONDON | 30 | -0.16 | 11 | 14 |
| PRE | 30 | -0.23 | 16 | 8 |
| NY-AM | 30 | -1.59 | 9 | 13 |
| NY-PM | 30 | +0.60 | 19 | 16 |
| CLOSE | 30 | -0.83 | 11 | 17 |

## 4. The 12 cells that pass HOLD + both halves (not carried forward)
| cell | session | gate | keep | PRE n | PRE kept mean | PRE ungated | HOLD kept/all n | HOLD kept MEAS | HOLD ungated | HOLD diff [CI] (MDE) | 25H2 | 2026 | X diff |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRNG|NYPM|CLOSE|SRF|p0|30s|40/20 | CLOSE | G1 | 0 | 90 | 2.02 | 0.98 | 40/78 | 3.50 | -4.05 | 7.55 [3.19, 12.11] (6.29) | 7.65 | 7.63 | 1.29 |
| PRNG|NYAM|NY-PM|SR|p0|1m|30/30 | NY-PM | G2 | 0 | 98 | 3.71 | 1.21 | 38/90 | 3.65 | -1.45 | 5.10 [-1.88, 12.77] (10.67) | 5.30 | 2.58 | -2.06 |
| PVWAP|ASIA|LKZ|SRF|p0|1m|40/20 | LONDON | G3 | 0 | 191 | 1.09 | 0.84 | 54/102 | 1.97 | -1.78 | 3.76 [0.38, 7.60] (5.24) | 3.76 | 4.42 | 1.80 |
| PPOC|LONDON|NY-AM|BC|p0|30s|30/60 | NY-AM | G4 | 1 | 275 | 4.85 | 2.60 | 126/203 | 0.65 | -2.31 | 2.96 [-0.82, 7.56] (6.10) | 2.01 | 10.84 | 1.82 |
| PPOC|LONDON|NY-AM|BC|p0|30s|30/60 | NY-AM | G2 | 1 | 261 | 4.95 | 2.60 | 126/203 | 0.65 | -2.31 | 2.96 [-0.47, 7.14] (5.37) | 1.50 | 13.72 | -0.89 |
| PRNG|NYAM|NY-PM|SR|p0|1m|30/30 | NY-PM | G6 | 0 | 191 | 1.68 | 1.21 | 71/90 | 1.00 | -1.45 | 2.45 [-0.32, 5.45] (4.08) | 2.38 | 2.58 | 1.28 |
| PRNG|LONDON|NY-AM|BC|p0|1m|50/50 | NY-AM | G5 | 1 | 179 | 5.26 | 5.08 | 92/174 | 1.61 | -0.54 | 2.16 [-2.59, 6.52] (6.74) | 1.31 | 11.61 | -0.29 |
| PPOC|LONDON|PRE|BC|p0|1m|40/20 | PRE | G5 | 0 | 185 | 0.76 | -0.06 | 83/132 | 1.59 | -0.21 | 1.80 [-0.39, 4.67] (3.52) | 2.26 | 0.74 | -0.86 |
| PVWAP|LONDON|PRE|BC|p0|1m|30/60 | PRE | G6 | 4 | 204 | 2.36 | 1.69 | 101/128 | 2.59 | 0.82 | 1.77 [-0.88, 5.06] (4.17) | 0.22 | 10.53 | -0.71 |
| PPOC|LONDON|PRE|BC|p0|1m|40/20 | PRE | G1 | 0 | 157 | 1.09 | -0.06 | 66/132 | 0.65 | -0.21 | 0.87 [-2.44, 4.11] (4.70) | 0.60 | 2.02 | -0.75 |
| PPOC|LONDON|PRE|BC|p0|1m|40/20 | PRE | G6 | 1 | 256 | 0.70 | -0.06 | 110/132 | 0.30 | -0.21 | 0.52 [-0.74, 1.77] (1.80) | 0.59 | 0.32 | 1.28 |
| PPOC|LONDON|PRE|BC|p0|1m|40/20 | PRE | G3 | 1 | 303 | 0.32 | -0.06 | 113/132 | 0.20 | -0.21 | 0.41 [-1.02, 1.72] (1.91) | 0.15 | 1.41 | -0.31 |

Two of these have a HOLD CI above zero and positive halves: PRNG|NYPM|CLOSE|SRF 30s 40/20 + G1=quiet (the ungated cell is -4.05 in HOLD, n=78; the gate turns it into +3.50 on 40 trades; PRE kept n = 90, X diff +1.3) and PVWAP|ASIA|LKZ|SRF 1m 40/20 + G3=no (LONDON entries; +1.97 on 54 of 102 trades; X +1.8). Each is one of 180 cells with MDE 5-6 pts per trade and an ungated base cell that loses, so the gain is a smaller loss avoided on the kept subset. Label: lead, untrusted, not carried.

## 5. Sizing cells - LONDON outcome -> NY-AM lots
S1 London return aligned with the trade side; S2 London range wide; S3 London swept the ASIA high or low (92% yes, degenerate). Multiplier 1.5 on the PRE-better option, 0.5 on the other. Effect = mean((w - 1) x MEAS pnl) per base trade (pts per 1 base lot).
| cell | condition (better option) | PRE eff | HOLD eff [CI] (MDE) | HOLD n | 25H2 | 2026 | X eff [CI] |
|---|---|---|---|---|---|---|---|
| PRNG|LONDON|NY-AM|BC|p0|1m|60/60 | S1=1 | 1.10 | -0.27 [-4.25, 3.71] (5.46) | 174 | -0.26 | -0.34 | 0.58 [-3.45, 4.61] |
| PRNG|LONDON|NY-AM|BC|p0|1m|60/60 | S2=0 | 2.87 | -1.38 [-6.13, 3.37] (6.53) | 174 | -1.25 | -2.08 | 1.39 [-2.10, 4.89] |
| PRNG|LONDON|NY-AM|BC|p0|1m|60/60 | S3=1 | 3.34 | 0.57 [-3.67, 4.82] (5.83) | 174 | -0.30 | 5.12 | -2.37 [-5.70, 0.96] |
| PRNG|LONDON|NY-AM|BC|p0|1m|50/50 | S1=1 | 0.80 | 0.32 [-2.86, 3.51] (4.37) | 174 | 0.45 | -0.34 | 0.15 [-3.38, 3.68] |
| PRNG|LONDON|NY-AM|BC|p0|1m|50/50 | S2=0 | 1.97 | -0.24 [-3.76, 3.29] (4.84) | 174 | -0.62 | 1.73 | -0.48 [-3.76, 2.80] |
| PRNG|LONDON|NY-AM|BC|p0|1m|50/50 | S3=1 | 2.50 | -1.03 [-4.61, 2.56] (4.92) | 174 | -1.34 | 0.60 | -1.96 [-5.10, 1.18] |
| PVWAP|LONDON|NYKZ|SRF|p0|1m|60/60 | S1=1 | 0.11 | 2.38 [-5.01, 9.77] (10.15) | 94 | 2.47 | 1.88 | 1.49 [-4.64, 7.61] |
| PVWAP|LONDON|NYKZ|SRF|p0|1m|60/60 | S2=0 | 0.19 | -1.63 [-7.57, 4.30] (8.15) | 94 | 0.61 | -15.59 | -2.50 [-6.77, 1.77] |
| PVWAP|LONDON|NYKZ|SRF|p0|1m|60/60 | S3=1 | 2.57 | -1.75 [-7.69, 4.19] (8.16) | 94 | -2.25 | 1.39 | -0.60 [-5.32, 4.13] |
| PVWAP|LONDON|NYKZ|BF|p0|1m|60/60 | S1=0 | 1.83 | -0.13 [-6.11, 5.86] (8.22) | 99 | -0.76 | 9.72 | -1.87 [-8.24, 4.49] |
| PVWAP|LONDON|NYKZ|BF|p0|1m|60/60 | S2=0 | 0.50 | -4.38 [-8.78, 0.02] (6.04) | 99 | -5.95 | 19.97 | -2.75 [-6.68, 1.18] |
| PVWAP|LONDON|NYKZ|BF|p0|1m|60/60 | S3=1 | 3.11 | -2.80 [-6.47, 0.88] (5.05) | 99 | -1.69 | -19.97 | -0.64 [-4.04, 2.76] |
| PPOC|LONDON|NY-AM|BC|p0|30s|30/60 | S1=1 | 0.50 | 1.58 [-1.20, 4.36] (3.82) | 203 | 1.55 | 1.81 | 0.93 [-1.38, 3.24] |
| PPOC|LONDON|NY-AM|BC|p0|30s|30/60 | S2=1 | 0.54 | 0.50 [-1.72, 2.73] (3.06) | 203 | 0.68 | -0.82 | -0.16 [-2.51, 2.19] |
| PPOC|LONDON|NY-AM|BC|p0|30s|30/60 | S3=1 | 0.41 | -1.20 [-3.56, 1.16] (3.23) | 203 | -1.47 | 0.83 | -2.86 [-4.82, -0.90] |

Reading: the three candidate NY-AM cells are themselves weak (X negative), so sizing them by the London outcome is moot; the S1 (London direction aligned with the trade) option on PPOC|LONDON|NY-AM|BC 30s 30/60 is the best-looking (HOLD +1.6, MDE 3.8, X +0.9, PRE +0.5), all CIs include zero.

## 6. Caveats
- Gate options were picked on PRE among 2 options (or 5 weekdays) per gate per cell, so the PRE gain is an upward-biased in-sample number by construction; HOLD/X is the test, and the HOLD/X mean is below zero.
- Gated cells keep 40-70% of the trades, so the HOLD gated means rest on 40-120 trades; the MDEs are 2-10 pts.
- Gates were evaluated only on the top-5 cells per session, as asked; the strong cells are those of item 3 and the candidates above, so a gate effect on a cell with a real edge is the relevant test and it fails to appear.