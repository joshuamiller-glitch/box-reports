# DS3_SD34 PREHOLD list (PRE-only; hashed before HOLD/X were read)
sha256 of out/sd34/PREHOLD.json: 85eda956e4183927d7a9619cb1c4d65c2a49543b53a0daaf73876a9b6cacfba5

base cell-sessions: 78 (PRE-selected top 25 per session 45 + top 10 per session regardless of verdict + top 5 for gating); gated cells 180; sizing cells 15.

Duplicates removed: cell-sessions with an identical entry set (killzone clones, NYKZ/PRE etc.) keep the plain session window.

| session | cell | PRE n | PRE MEAS mean | PRE effect | t | selected | list |
|---|---|---|---|---|---|---|---|
| ASIA | FH|own|ASIA|BF|p0|30s|30/60 | 440 | 1.23 | 3.46 | 1.83 | no | top10 |
| LONDON | FH|own|LONDON|SR|p0|1m|20/20 | 505 | -0.26 | 2.03 | 2.56 | no | top10 |
| LONDON | PPOC|ASIA|LKZ|SR|p0|1m|40/20 | 355 | 0.07 | 2.56 | 2.32 | yes | sel |
| LONDON | PPOC|ASIA|LKZ|SR|p0|30s|40/20 | 360 | 0.47 | 2.94 | 2.42 | yes | sel,top10 |
| LONDON | PPOC|ASIA|LONDON|BC|p0|30s|40/20 | 493 | -0.63 | 2.00 | 2.41 | no | top10 |
| LONDON | PPOC|ASIA|LONDON|BF|p0|30s|60/60 | 486 | 0.32 | 2.73 | 2.43 | yes | sel,top10 |
| LONDON | PPOC|ASIA|LONDON|SR|p0|1m|40/20 | 441 | 0.74 | 3.41 | 3.36 | yes | sel,top10,top5 |
| LONDON | PPOC|ASIA|LONDON|SR|p0|30s|40/20 | 453 | 0.93 | 3.55 | 3.32 | yes | sel,top10,top5 |
| NY-AM | PPOC|LONDON|NY-AM|BC|p0|1m|30/60 | 454 | 1.43 | 3.36 | 2.08 | yes | sel |
| NY-AM | PPOC|LONDON|NY-AM|BC|p0|30s|30/60 | 470 | 2.60 | 4.53 | 2.95 | yes | sel,top10,top5 |
| NY-AM | PPOC|LONDON|NY-AM|BF|p0|1m|40/40 | 440 | 1.16 | 3.28 | 2.07 | yes | sel |
| NY-AM | PPOC|LONDON|NYKZ|BC|p0|1m|20/40 | 194 | 2.31 | 4.40 | 2.22 | yes | sel |
| NY-AM | PPOC|LONDON|NYKZ|BC|p0|30s|20/40 | 192 | 2.58 | 4.61 | 2.56 | yes | sel,top10 |
| NY-AM | PPOC|LONDON|NYKZ|BC|p0|30s|30/30 | 192 | 1.18 | 3.32 | 2.22 | yes | sel |
| NY-AM | PPOC|LONDON|NYKZ|SRF|p0|1m|40/40 | 174 | 4.15 | 6.24 | 2.65 | yes | sel,top10 |
| NY-AM | PPOC|LONDON|NYKZ|SRF|p0|1m|60/60 | 174 | 7.75 | 9.84 | 2.42 | yes | sel |
| NY-AM | PPOC|LONDON|NYKZ|SRF|p0|30s|40/40 | 187 | 2.30 | 4.40 | 2.18 | yes | sel |
| NY-AM | PPOC|LONDON|NYKZ|SRF|p0|30s|50/50 | 187 | 3.61 | 5.71 | 2.12 | yes | sel |
| NY-AM | PPOC|LONDON|NYKZ|SRF|p0|30s|60/60 | 187 | 5.40 | 7.46 | 2.00 | yes | sel |
| NY-AM | PPOC|LONDON|NYKZ|SR|p0|1m|40/40 | 192 | 3.07 | 5.18 | 2.30 | yes | sel |
| PRE | PPOC|LONDON|PRE|BC|p0|1m|40/20 | 333 | -0.06 | 2.45 | 2.20 | no | top10,top5 |
| PRE | PPOC|LONDON|PRE|BC|p0|30s|60/60 | 352 | 0.03 | 2.11 | 1.75 | no | top10 |
| PRE | PPOC|LONDON|PRE|BF|p0|1m|30/60 | 342 | 2.08 | 4.43 | 2.07 | yes | sel,top10,top5 |
| NY-PM | PPOC|NYAM|NY-PM|BH|p0|1m|40/20 | 291 | 0.15 | 2.53 | 2.08 | yes | sel,top10,top5 |
| NY-PM | PPOC|NYAM|NY-PM|SR|p0|30s|40/20 | 348 | 0.55 | 2.89 | 2.33 | yes | sel,top10,top5 |
| CLOSE | PPOC|NYPM|CLOSE|BF|p0|1m|20/60 | 422 | 0.39 | 1.71 | 1.17 | no | top10 |
| CLOSE | PPOC|NYPM|CLOSE|SRF|p0|30s|40/40 | 356 | 0.12 | 1.43 | 1.05 | no | top10 |
| ASIA | PPOC|prevNY|ASIA|BC|p0|30s|20/20 | 328 | -0.94 | 1.22 | 2.41 | no | top10,top5 |
| ASIA | PPOC|prevNY|ASIA|BC|p0|30s|20/60 | 328 | 1.71 | 3.72 | 2.18 | yes | sel,top10,top5 |
| ASIA | PPOC|prevNY|ASIA|BC|p0|30s|60/60 | 328 | 0.72 | 2.97 | 2.75 | yes | sel,top10,top5 |
| ASIA | PPOC|prevNY|ASIA|BF|p0|30s|20/20 | 312 | -0.50 | 1.67 | 2.34 | no | top10 |
| ASIA | PPOC|prevNY|ASIA|BF|p0|30s|20/60 | 312 | 2.39 | 4.40 | 2.27 | yes | sel,top10,top5 |
| ASIA | PPOC|prevNY|ASIA|SRF|p0|1m|20/60 | 246 | 2.23 | 4.21 | 2.07 | yes | sel,top10,top5 |
| NY-AM | PRNG|LONDON|NY-AM|BC|p0|1m|30/60 | 374 | 3.69 | 5.64 | 2.83 | yes | sel,top10 |
| NY-AM | PRNG|LONDON|NY-AM|BC|p0|1m|40/40 | 374 | 2.80 | 4.93 | 2.67 | yes | sel,top10 |
| NY-AM | PRNG|LONDON|NY-AM|BC|p0|1m|50/50 | 374 | 5.08 | 7.20 | 3.45 | yes | sel,top10,top5 |
| NY-AM | PRNG|LONDON|NY-AM|BC|p0|1m|60/60 | 374 | 6.24 | 8.32 | 3.49 | yes | sel,top10,top5 |
| NY-AM | PRNG|LONDON|NY-AM|BC|p0|30s|30/60 | 386 | 2.22 | 4.17 | 2.14 | yes | sel |
| NY-AM | PRNG|LONDON|NY-AM|BC|p0|30s|40/40 | 386 | 3.03 | 5.14 | 2.66 | yes | sel,top10 |
| NY-AM | PRNG|LONDON|NY-AM|BC|p0|30s|50/50 | 386 | 2.34 | 4.44 | 2.12 | yes | sel |
| NY-AM | PRNG|LONDON|NY-AM|BC|p0|30s|60/60 | 386 | 3.86 | 5.93 | 2.48 | yes | sel |
| NY-AM | PRNG|LONDON|NYKZ|BC|p0|1m|30/60 | 213 | 4.63 | 6.63 | 2.36 | yes | sel |
| NY-AM | PRNG|LONDON|NYKZ|BC|p0|30s|30/60 | 214 | 3.98 | 5.96 | 2.20 | yes | sel |
| PRE | PRNG|LONDON|PRE|BH|p0|1m|20/60 | 165 | 2.20 | 4.74 | 1.81 | no | top10 |
| PRE | PRNG|LONDON|PRE|BH|p0|1m|30/30 | 165 | 1.42 | 4.03 | 1.70 | no | top10 |
| NY-PM | PRNG|NYAM|NY-PM|SRF|p0|1m|20/20 | 196 | 0.89 | 3.11 | 2.24 | yes | sel,top10,top5 |
| NY-PM | PRNG|NYAM|NY-PM|SR|p0|1m|20/20 | 235 | -0.21 | 2.00 | 1.69 | no | top10 |
| NY-PM | PRNG|NYAM|NY-PM|SR|p0|1m|30/30 | 235 | 1.21 | 3.30 | 1.99 | no | top10,top5 |
| NY-PM | PRNG|NYAM|NY-PM|SR|p0|1m|40/20 | 235 | 0.35 | 2.67 | 1.70 | no | top10 |
| CLOSE | PRNG|NYPM|CLOSE|SRF|p0|30s|40/20 | 165 | 0.98 | 2.47 | 1.49 | no | top10,top5 |
| LONDON | PVWAP|ASIA|LKZ|SRF|p0|1m|40/20 | 332 | 0.84 | 3.35 | 3.12 | yes | sel,top10,top5 |
| LONDON | PVWAP|ASIA|LKZ|SRF|p0|30s|40/20 | 350 | 1.04 | 3.55 | 3.24 | yes | sel,top10,top5 |
| LONDON | PVWAP|ASIA|LKZ|SR|p0|1m|40/20 | 380 | 0.73 | 3.25 | 2.60 | yes | sel,top10,top5 |
| LONDON | PVWAP|ASIA|LONDON|SRF|p0|1m|40/20 | 429 | -0.02 | 2.65 | 2.75 | no | top10 |
| NY-AM | PVWAP|LONDON|NYKZ|BF|p0|1m|60/60 | 211 | 7.15 | 9.21 | 3.02 | yes | sel,top10,top5 |
| NY-AM | PVWAP|LONDON|NYKZ|SRF|p0|1m|60/60 | 198 | 7.84 | 9.92 | 3.15 | yes | sel,top10,top5 |
| NY-AM | PVWAP|LONDON|NYKZ|SRF|p0|30s|60/60 | 208 | 5.58 | 7.63 | 2.16 | yes | sel |
| PRE | PVWAP|LONDON|PRE|BC|p0|1m|30/60 | 267 | 1.69 | 3.96 | 2.00 | yes | sel,top10,top5 |
| PRE | PVWAP|LONDON|PRE|BC|p0|1m|40/20 | 267 | 0.40 | 2.88 | 2.43 | yes | sel,top10,top5 |
| PRE | PVWAP|LONDON|PRE|BF|p0|30s|20/20 | 284 | -0.37 | 1.84 | 1.82 | no | top10,top5 |
| PRE | PVWAP|LONDON|PRE|BF|p0|30s|40/20 | 284 | -0.18 | 2.27 | 1.78 | no | top10 |
| NY-PM | PVWAP|NYAM|NY-PM|BH|p0|1m|20/40 | 305 | 0.76 | 2.74 | 1.68 | no | top10 |
| NY-PM | PVWAP|NYAM|NY-PM|SRF|p0|30s|60/60 | 325 | 2.53 | 4.52 | 1.98 | no | top10,top5 |
| NY-PM | PVWAP|NYAM|NY-PM|SR|p0|1m|20/20 | 355 | -0.59 | 1.63 | 1.84 | no | top10 |
| NY-PM | PVWAP|NYAM|NY-PM|SR|p0|30s|30/30 | 369 | -0.30 | 1.83 | 1.74 | no | top10 |
| ASIA | PVWAP|prevNY|AKZ|BC|p0|1m|30/60 | 162 | 2.52 | 4.98 | 1.97 | no | top10 |
| ASIA | PVWAP|prevNY|ASIA|BC|p0|30s|20/60 | 255 | 1.66 | 3.69 | 1.94 | no | top10 |
| ASIA | PVWAP|prevNY|ASIA|BC|p0|30s|30/60 | 255 | 1.93 | 4.16 | 1.93 | no | top10 |
| CLOSE | SOPEN|own|CLOSE|EXR|k0.5|30s|20/40 | 294 | 0.22 | 1.79 | 1.23 | no | top10 |
| CLOSE | SOPEN|own|CLOSE|EXR|k0.5|30s|30/30 | 294 | 1.63 | 3.11 | 1.74 | no | top10,top5 |
| CLOSE | SOPEN|own|CLOSE|EXR|k0.5|30s|30/60 | 294 | 2.72 | 3.71 | 1.66 | no | top10,top5 |
| CLOSE | SOPEN|own|CLOSE|EXR|k0.5|30s|40/40 | 294 | 1.25 | 2.57 | 1.25 | no | top10,top5 |
| CLOSE | SOPEN|own|CLOSE|EXR|k0.5|30s|50/50 | 294 | 1.72 | 2.91 | 1.18 | no | top10 |
| CLOSE | SOPEN|own|CLOSE|EXR|k0.5|30s|60/60 | 294 | 3.17 | 4.23 | 1.64 | no | top10,top5 |
| CLOSE | SOPEN|own|CLOSE|EX|k0.5|1m|50/50 | 292 | 1.48 | 2.71 | 1.14 | no | top10 |
| LONDON | SOPEN|own|LONDON|EX|k1|1m|30/60 | 107 | 5.79 | 8.01 | 2.05 | yes | sel |
| LONDON | SOPEN|own|LONDON|EX|k1|1m|40/40 | 107 | 5.53 | 8.13 | 2.33 | yes | sel |
| PRE | SOPEN|own|PRE|EXR|k0.5|1m|30/60 | 266 | 2.77 | 4.89 | 1.69 | no | top10 |