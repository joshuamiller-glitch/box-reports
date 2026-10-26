# PRED ROUND 84 - block I round 10 - I-unlocked-all

Best HOLDOUT F-R AUC: +15 POOLED 0.539 [0.51,0.57] | ASIA 0.609 [0.55,0.67] | LONDON 0.543 [0.47,0.61] | NY 0.523 [0.46,0.58]
Best HOLDOUT F-R AUC: +30 POOLED 0.519 [0.48,0.55] | ASIA 0.597 [0.54,0.65] | LONDON 0.518 [0.45,0.58] | NY 0.519 [0.47,0.57]
Best G HOLDOUT AUC: 0.553 [0.53,0.58]
Gap to FOUND: 0.051 AUC, 5 of 5 economic conditions short.
not found - short by 0.051 AUC and 5 of 5 economic conditions

prereg 1d25b6f283900f9eecc9833f13e4ad4b7270008426be83c3a9e51d0425f9adb0 ; trials added 4099892 ; truncation audit {'decisions': 480, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['I1', 'I9', 'I5', 'I6', 'I7', 'I1_sigu', 'I5_sigu', 'I6_sigu', 'I7_sigu']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| I5-rocket | +15 | ASIA | rf/pooled/BOTH | 0.585 [0.54,0.63] | 0.609 [0.55,0.67] | - | 0.599 | 0.602 | - | - | - | - | - | stack | promising: short by 0.051 AUC, 5 of 5 econ |
| I5-rocket | +30 | ASIA | logit2/pooled/BOTH | 0.578 [0.54,0.62] | 0.597 [0.54,0.65] | - | 0.594 | 0.598 | - | - | - | - | - | stack | promising: short by 0.063 AUC, 5 of 5 econ |
| I3P-searchnull | +20 | LONDON | logit2/pooled/xuI3P | 0.550 [0.50,0.60] | 0.589 [0.52,0.66] | - | 0.585 | 0.579 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +20 | ASIA | rf/pooled/BOTH | 0.570 [0.53,0.61] | 0.571 [0.51,0.63] | - | 0.568 | 0.563 | - | - | - | - | - | stack | short by 0.089 AUC, 5 of 5 econ |
| I1-tsfresh | +45 | NY | logit2/pooled/IONLY | 0.553 [0.51,0.60] | 0.571 [0.51,0.63] | - | 0.577 | 0.574 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | +60 | LONDON | gbt3/pooled/xuI2 | 0.537 [0.49,0.59] | 0.566 [0.50,0.63] | - | 0.561 | 0.543 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +30 | ASIA | stack/pooled/IONLY | 0.567 [0.52,0.61] | 0.566 [0.50,0.63] | - | 0.557 | 0.563 | - | - | - | - | - |  | short by 0.094 AUC, 5 of 5 econ |
| I2-gp | +45 | ASIA | logit2/pooled/xuI2 | 0.543 [0.50,0.59] | 0.566 [0.50,0.63] | - | 0.562 | 0.562 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +45 | ASIA | logit2/pooled/xuI4 | 0.539 [0.49,0.58] | 0.565 [0.50,0.63] | - | 0.566 | 0.567 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +5 | ASIA | gbt3/pooled/IONLY | 0.560 [0.52,0.60] | 0.562 [0.50,0.62] | - | 0.558 | 0.562 | - | - | - | - | - |  | short by 0.098 AUC, 5 of 5 econ |
| I1-tsfresh | +45 | ASIA | logit2/pooled/IONLY | 0.559 [0.51,0.60] | 0.555 [0.49,0.62] | - | 0.561 | 0.553 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | +20 | LONDON | gbt3/pooled/xuI2 | 0.536 [0.49,0.58] | 0.554 [0.49,0.62] | - | 0.554 | 0.542 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | sig | NY | logit2/xuI4 | 0.549 [0.53,0.57] | 0.553 [0.53,0.58] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3-interactions | pre | ASIA | stack/pooled/xuI3 | 0.537 [0.50,0.58] | 0.551 [0.49,0.61] | - | 0.537 | 0.552 | - | - | - | - | - | stack | short by 0.109 AUC, 5 of 5 econ |
| I9-normalised | +60 | ASIA | rf/pooled/IONLY | 0.547 [0.50,0.59] | 0.550 [0.49,0.62] | - | 0.548 | 0.540 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +60 | ASIA | rf/pooled/IONLY | 0.555 [0.51,0.60] | 0.549 [0.48,0.62] | - | 0.550 | 0.550 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | sig | NY | logit2/GBOTH | 0.547 [0.53,0.56] | 0.547 [0.52,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3-interactions | +45 | LONDON | logit2/pooled/xuI3 | 0.523 [0.48,0.57] | 0.547 [0.48,0.61] | - | 0.542 | 0.535 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | sig | NY | logit2/GBOTH | 0.547 [0.53,0.56] | 0.547 [0.52,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I7-signature | sig | NY | logit2/GBOTH | 0.546 [0.53,0.56] | 0.547 [0.52,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I5-rocket | +45 | ASIA | stack/pooled/BOTH | 0.551 [0.51,0.59] | 0.546 [0.49,0.61] | - | 0.555 | 0.532 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | pre | ASIA | stack/pooled/IONLY | 0.542 [0.51,0.58] | 0.545 [0.48,0.60] | - | 0.537 | 0.545 | - | - | - | - | - |  | short by 0.115 AUC, 5 of 5 econ |
| I6-wavelet | +10 | ASIA | rf/pooled/IONLY | 0.566 [0.52,0.61] | 0.545 [0.49,0.60] | - | 0.534 | 0.542 | - | - | - | - | - |  | short by 0.115 AUC, 5 of 5 econ |
| I2-gp | +5 | NY | logit2/pooled/xuI2 | 0.525 [0.48,0.57] | 0.544 [0.48,0.60] | - | 0.549 | 0.537 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | +5 | NY | stack/pertype/BOTH | 0.535 [0.49,0.58] | 0.544 [0.48,0.61] | - | 0.537 | 0.542 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +15 | LONDON | stack/pooled/xuI3 | 0.538 [0.49,0.59] | 0.543 [0.47,0.61] | - | 0.539 | 0.545 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +15 | ASIA | gbt3/pooled/IONLY | 0.564 [0.52,0.60] | 0.543 [0.48,0.60] | - | 0.540 | 0.546 | - | - | - | - | - |  | short by 0.117 AUC, 5 of 5 econ |
| I2-gp | +20 | NY | stack/pooled/xuI2 | 0.542 [0.50,0.59] | 0.542 [0.48,0.60] | - | 0.540 | 0.535 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +20 | NY | logit2/pooled/IONLY | 0.533 [0.49,0.57] | 0.541 [0.48,0.60] | - | 0.542 | 0.543 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +60 | ASIA | stack/pooled/BOTH | 0.559 [0.52,0.61] | 0.540 [0.47,0.61] | - | 0.535 | 0.524 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | +45 | POOLED | rf/pooled/xuI2 | 0.518 [0.49,0.54] | 0.539 [0.50,0.58] | - | 0.537 | 0.529 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | sig | NY | gbt3/GBOTH | 0.544 [0.53,0.56] | 0.539 [0.51,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | +15 | POOLED | logit2/pooled/xuI2 | 0.524 [0.50,0.55] | 0.539 [0.51,0.57] | - | 0.538 | 0.535 | - | - | - | - | - | stack | promising: short by 0.141 AUC, 5 of 5 econ |
| I2-gp | +10 | ASIA | rf/pooled/xuI2 | 0.560 [0.51,0.61] | 0.538 [0.47,0.60] | - | 0.533 | 0.535 | - | - | - | - | - | stack | short by 0.122 AUC, 5 of 5 econ |
| I2-gp | +60 | POOLED | logit2/pooled/xuI2 | 0.520 [0.50,0.54] | 0.538 [0.50,0.57] | - | 0.537 | 0.526 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +30 | ASIA | gbt3/pooled/xuI3 | 0.558 [0.52,0.60] | 0.537 [0.47,0.60] | - | 0.533 | 0.523 | - | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| I3P-searchnull | sig | LONDON | logit2/xuI3P | 0.523 [-,-] | 0.537 [0.51,0.56] | - | - | - | - | - | - | - | - | stack | short by 0.143 AUC, 5 of 5 econ |
| I4-autoencoder | pre | ASIA | rf/pooled/xuI4 | 0.539 [0.50,0.58] | 0.535 [0.48,0.59] | - | 0.526 | 0.536 | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| I6-wavelet | +5 | ASIA | rf/pooled/BOTH | 0.549 [0.51,0.59] | 0.535 [0.49,0.58] | - | 0.532 | 0.534 | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| I3P-searchnull | sig | LONDON | logit2/xuI3P | 0.522 [0.50,0.54] | 0.534 [0.51,0.56] | - | - | - | - | - | - | - | - | stack | short by 0.146 AUC, 5 of 5 econ |
| I2-gp | sig | NY | gbt3/xuI2 | 0.543 [0.52,0.56] | 0.534 [0.51,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I5-rocket | +5 | POOLED | rf/pooled/IONLY | 0.537 [0.51,0.56] | 0.534 [0.50,0.56] | - | 0.531 | 0.533 | - | - | - | - | - |  | short by 0.146 AUC, 5 of 5 econ |
| I3-interactions | sig | NY | logit2/xuI3 | 0.543 [0.53,0.56] | 0.533 [0.51,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I7-signature | +15 | ASIA | logit2/pooled/IONLY | 0.524 [0.48,0.57] | 0.533 [0.47,0.60] | - | 0.531 | 0.529 | - | - | - | - | - |  | short by 0.127 AUC, 5 of 5 econ |
| I6-wavelet | pre | NY | rf/pooled/BOTH | 0.528 [0.49,0.57] | 0.532 [0.47,0.59] | - | 0.540 | 0.530 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | pre | ASIA | gbt3/pooled/BOTH | 0.540 [0.50,0.58] | 0.531 [0.46,0.59] | - | 0.520 | 0.530 | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| I7-signature | sig | ASIA | logit2/GI1 | 0.525 [0.50,0.55] | 0.530 [0.50,0.56] | - | - | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| I6-wavelet | +20 | ASIA | gbt3/pooled/IONLY | 0.554 [0.51,0.60] | 0.530 [0.47,0.59] | - | 0.528 | 0.530 | - | - | - | - | - |  | dead (no gain over baseline) |
| I6-wavelet | pre | ASIA | stack/pooled/BOTH | 0.543 [0.51,0.58] | 0.530 [0.47,0.59] | - | 0.524 | 0.530 | - | - | - | - | - | stack | short by 0.130 AUC, 5 of 5 econ |
| I7-signature | sig | ASIA | logit2/GI1 | 0.523 [-,-] | 0.530 [0.50,0.55] | - | - | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| I4-autoencoder | +10 | LONDON | rf/pooled/xuI4 | 0.521 [0.48,0.56] | 0.530 [0.47,0.59] | - | 0.525 | 0.515 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | pre | NY | rf/pooled/xuI4 | 0.522 [0.47,0.57] | 0.529 [0.46,0.59] | - | 0.531 | 0.527 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +60 | ASIA | logit2/pooled/xuI3 | 0.554 [0.51,0.60] | 0.529 [0.46,0.60] | - | 0.517 | 0.507 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +10 | POOLED | rf/pooled/BOTH | 0.530 [0.51,0.56] | 0.529 [0.49,0.57] | - | 0.527 | 0.521 | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| I3P-searchnull | +15 | LONDON | gbt3/pooled/xuI3P | 0.527 [0.48,0.57] | 0.528 [0.46,0.59] | - | 0.528 | 0.518 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +20 | POOLED | rf/pooled/IONLY | 0.526 [0.50,0.55] | 0.528 [0.49,0.57] | - | 0.524 | 0.525 | - | - | - | - | - |  | short by 0.152 AUC, 5 of 5 econ |
| I9-normalised | +15 | ASIA | logit2/pooled/IONLY | 0.576 [0.53,0.62] | 0.528 [0.47,0.59] | - | 0.527 | 0.525 | - | - | - | - | - |  | short by 0.132 AUC, 5 of 5 econ |
| I4-autoencoder | +60 | POOLED | gbt3/pooled/xuI4 | 0.511 [0.49,0.54] | 0.528 [0.49,0.57] | - | 0.527 | 0.518 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +45 | POOLED | logit2/pooled/xuI3 | 0.513 [0.48,0.54] | 0.528 [0.49,0.56] | - | 0.528 | 0.518 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | +5 | POOLED | logit2/pooled/xuI2 | 0.517 [0.49,0.54] | 0.528 [0.49,0.56] | - | 0.526 | 0.522 | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| I4-autoencoder | +10 | POOLED | rf/pooled/xuI4 | 0.522 [0.50,0.55] | 0.528 [0.49,0.57] | - | 0.528 | 0.521 | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| I2-gp | pre | NY | logit2/pooled/xuI2 | 0.506 [0.46,0.56] | 0.528 [0.46,0.59] | - | 0.530 | 0.524 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +45 | ASIA | stack/pooled/xuI3 | 0.529 [0.49,0.58] | 0.527 [0.46,0.60] | - | 0.517 | 0.509 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +20 | LONDON | gbt3/pooled/xuI4 | 0.529 [0.49,0.57] | 0.527 [0.47,0.59] | - | 0.530 | 0.499 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | sig | POOLED/ST | logit2/xuI3 | 0.530 [0.52,0.54] | 0.526 [0.51,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I4-autoencoder | sig | NY | logit2/xuI4 | 0.518 [-,-] | 0.525 [0.50,0.55] | - | - | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| I3-interactions | +20 | NY | logit2/pooled/xuI3 | 0.506 [0.47,0.55] | 0.524 [0.47,0.58] | - | 0.517 | 0.516 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | sig | POOLED | logit2/xuI3 | 0.528 [0.52,0.54] | 0.524 [0.51,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I5-rocket | +10 | ASIA | stack/pooled/IONLY | 0.546 [0.51,0.58] | 0.524 [0.46,0.59] | - | 0.516 | 0.524 | - | - | - | - | - |  | short by 0.136 AUC, 5 of 5 econ |
| I5-rocket | +15 | POOLED | rf/pooled/IONLY | 0.535 [0.51,0.56] | 0.524 [0.49,0.56] | - | 0.523 | 0.524 | - | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| I9-normalised | +45 | NY | logit2/pooled/IONLY | 0.545 [0.50,0.59] | 0.524 [0.46,0.58] | - | 0.522 | 0.519 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +5 | ASIA | stack/pooled/IONLY | 0.543 [0.50,0.58] | 0.524 [0.46,0.59] | - | 0.516 | 0.523 | - | - | - | - | - |  | short by 0.136 AUC, 5 of 5 econ |
| I6-wavelet | +5 | POOLED | rf/pooled/BOTH | 0.518 [0.49,0.54] | 0.524 [0.49,0.56] | - | 0.523 | 0.516 | - | - | - | - | - | stack | short by 0.156 AUC, 5 of 5 econ |
| I4-autoencoder | +60 | ASIA | logit2/pooled/xuI4 | 0.513 [0.47,0.55] | 0.524 [0.46,0.59] | - | 0.518 | 0.520 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | sig | ASIA | logit2/xuI3 | 0.513 [-,-] | 0.523 [0.49,0.56] | - | - | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| I5-rocket | +15 | NY | logit2/pooled/BOTH | 0.534 [0.49,0.58] | 0.523 [0.46,0.58] | - | 0.525 | 0.513 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | sig | ASIA | logit2/xuI3 | 0.512 [0.49,0.54] | 0.523 [0.49,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I4-autoencoder | +10 | NY | rf/pooled/xuI4 | 0.525 [0.48,0.57] | 0.523 [0.46,0.59] | - | 0.527 | 0.521 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +30 | ASIA | logit2/pooled/xuI4 | 0.532 [0.49,0.58] | 0.523 [0.46,0.58] | - | 0.516 | 0.522 | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| I5-rocket | +20 | POOLED | rf/pooled/IONLY | 0.528 [0.50,0.55] | 0.522 [0.49,0.55] | - | 0.521 | 0.522 | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| I3-interactions | +60 | LONDON | gbt3/pooled/xuI3 | 0.498 [0.46,0.54] | 0.522 [0.47,0.57] | - | 0.522 | 0.499 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +45 | POOLED | rf/pooled/BOTH | 0.508 [0.48,0.53] | 0.522 [0.49,0.56] | - | 0.520 | 0.511 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +45 | NY | logit2/pooled/xuI3 | 0.496 [0.45,0.54] | 0.521 [0.45,0.60] | - | 0.525 | 0.513 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +10 | LONDON | logit2/pooled/xuI3P | 0.539 [0.50,0.58] | 0.521 [0.46,0.58] | - | 0.521 | 0.513 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | sig | LONDON | gbt3/GI1 | 0.526 [0.51,0.55] | 0.521 [0.49,0.55] | - | - | - | - | - | - | - | - |  | short by 0.159 AUC, 5 of 5 econ |
| I5-rocket | sig | NY | logit2/GBOTH | 0.515 [-,-] | 0.521 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| I2-gp | +15 | NY | rf/pooled/xuI2 | 0.505 [0.46,0.55] | 0.520 [0.45,0.59] | - | 0.529 | 0.514 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | sig | POOLED | gbt3/GI1 | 0.530 [0.52,0.54] | 0.520 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| I3-interactions | sig | POOLED/HM | rf/xuI3 | 0.533 [0.52,0.55] | 0.520 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I5-rocket | sig | ASIA | logit2/GI1 | 0.516 [-,-] | 0.520 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| I5-rocket | sig | ASIA | logit2/GI1 | 0.517 [0.50,0.54] | 0.520 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| I7-signature | sig | NY | logit2/GBOTH | 0.515 [-,-] | 0.520 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| I6-wavelet | sig | NY | logit2/GBOTH | 0.516 [-,-] | 0.520 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| I6-wavelet | +10 | NY | rf/pooled/BOTH | 0.528 [0.48,0.57] | 0.520 [0.45,0.59] | - | 0.519 | 0.517 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | sig | POOLED | logit2/xuI4 | 0.520 [0.51,0.53] | 0.520 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I9-normalised | +30 | ASIA | gbt3/pooled/BOTH | 0.559 [0.51,0.61] | 0.520 [0.46,0.58] | - | 0.505 | 0.509 | - | - | - | - | - | stack | short by 0.140 AUC, 5 of 5 econ |
| I1-tsfresh | +60 | ASIA | gbt3/pooled/BOTH | 0.533 [0.48,0.58] | 0.519 [0.46,0.58] | - | 0.516 | 0.502 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +30 | POOLED | gbt3/pooled/xuI3 | 0.516 [0.49,0.54] | 0.519 [0.48,0.55] | - | 0.511 | 0.498 | - | - | - | - | - | stack | promising: short by 0.161 AUC, 5 of 5 econ |
| I5-rocket | +30 | POOLED | gbt3/pooled/IONLY | 0.530 [0.51,0.55] | 0.519 [0.48,0.55] | - | 0.522 | 0.518 | - | - | - | - | - |  | promising: short by 0.161 AUC, 5 of 5 econ |
| I5-rocket | pre | ASIA | gbt3/pooled/BOTH | 0.539 [0.50,0.58] | 0.519 [0.46,0.58] | - | 0.509 | 0.518 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | sig | LONDON | gbt3/GI1 | 0.524 [-,-] | 0.519 [0.49,0.55] | - | - | - | - | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| I5-rocket | +30 | NY | rf/pooled/IONLY | 0.524 [0.48,0.57] | 0.519 [0.47,0.57] | - | 0.528 | 0.520 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +30 | LONDON | logit2/pooled/xuI3 | 0.528 [0.49,0.57] | 0.518 [0.45,0.58] | - | 0.517 | 0.490 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | pre | NY | logit2/pooled/BOTH | 0.520 [0.48,0.56] | 0.518 [0.47,0.57] | - | 0.521 | 0.514 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | sig | POOLED/ST | logit2/GBOTH | 0.518 [0.51,0.53] | 0.518 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | +15 | ASIA | logit2/pooled/IONLY | 0.561 [0.52,0.60] | 0.518 [0.46,0.57] | - | 0.509 | 0.509 | - | - | - | - | - |  | short by 0.142 AUC, 5 of 5 econ |
| I2-gp | +5 | LONDON | gbt3/pooled/xuI2 | 0.500 [0.45,0.55] | 0.518 [0.45,0.58] | - | 0.517 | 0.501 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +5 | LONDON | stack/pooled/BOTH | 0.532 [0.49,0.58] | 0.517 [0.45,0.58] | - | 0.512 | 0.502 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | +10 | NY | logit2/pooled/xuI2 | 0.490 [0.45,0.53] | 0.517 [0.45,0.58] | - | 0.529 | 0.509 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +10 | ASIA | logit2/pooled/IONLY | 0.546 [0.51,0.59] | 0.517 [0.46,0.57] | - | 0.511 | 0.519 | - | - | - | - | - |  | dead (no gain over baseline) |
| I5-rocket | sig | POOLED/ST | gbt3/GBOTH | 0.519 [0.51,0.53] | 0.517 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I4-autoencoder | sig | POOLED/ST | gbt3/xuI4 | 0.518 [0.51,0.53] | 0.517 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I9-normalised | pre | POOLED | logit2/pooled/BOTH | 0.514 [0.49,0.54] | 0.517 [0.49,0.54] | - | 0.517 | 0.515 | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| I7-signature | +15 | POOLED | gbt3/pooled/IONLY | 0.514 [0.49,0.54] | 0.517 [0.48,0.55] | - | 0.515 | 0.509 | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| I5-rocket | +15 | LONDON | stack/pooled/BOTH | 0.524 [0.48,0.57] | 0.517 [0.46,0.58] | - | 0.504 | 0.497 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +45 | POOLED | rf/pooled/BOTH | 0.511 [0.48,0.54] | 0.516 [0.48,0.55] | - | 0.515 | 0.505 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | sig | NY | gbt3/GBOTH | 0.516 [-,-] | 0.516 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| I7-signature | sig | POOLED | logit2/GBOTH | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I6-wavelet | sig | POOLED | logit2/GBOTH | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I4-autoencoder | +45 | LONDON | gbt3/pooled/xuI4 | 0.513 [0.47,0.56] | 0.516 [0.46,0.58] | - | 0.505 | 0.494 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +20 | ASIA | stack/pooled/xuI4 | 0.537 [0.50,0.57] | 0.516 [0.46,0.57] | - | 0.505 | 0.513 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | +30 | ASIA | logit2/pooled/xuI2 | 0.553 [0.51,0.60] | 0.515 [0.45,0.58] | - | 0.507 | 0.517 | - | - | - | - | - | stack | short by 0.145 AUC, 5 of 5 econ |
| I1-tsfresh | sig | POOLED/HM | rf/GI1 | 0.525 [0.51,0.54] | 0.515 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| I1-tsfresh | sig | POOLED/ST | gbt3/GI1 | 0.532 [0.52,0.55] | 0.515 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| I1-tsfresh | +5 | ASIA | rf/pertype/BOTH | 0.539 [0.49,0.58] | 0.515 [0.46,0.57] | - | 0.505 | 0.516 | - | - | - | - | - | stack | short by 0.145 AUC, 5 of 5 econ |
| I4-autoencoder | +5 | NY | gbt3/pooled/xuI4 | 0.510 [0.48,0.55] | 0.515 [0.47,0.56] | - | 0.524 | 0.507 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +10 | ASIA | rf/pooled/xuI3P | 0.532 [0.49,0.58] | 0.515 [0.45,0.58] | - | 0.518 | 0.502 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | +20 | POOLED | gbt3/pooled/xuI2 | 0.514 [0.49,0.54] | 0.515 [0.48,0.55] | - | 0.508 | 0.510 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | sig | POOLED/ST | gbt3/xuI2 | 0.521 [0.51,0.53] | 0.515 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | +15 | LONDON | gbt3/pooled/xuI2 | 0.510 [0.47,0.55] | 0.514 [0.45,0.57] | - | 0.506 | 0.507 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | +60 | ASIA | logit2/pooled/xuI2 | 0.522 [0.47,0.57] | 0.514 [0.45,0.58] | - | 0.509 | 0.505 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | sig | LONDON | rf/GI1 | 0.504 [0.48,0.53] | 0.514 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| I3P-searchnull | +5 | LONDON | logit2/pooled/xuI3P | 0.519 [0.48,0.56] | 0.514 [0.44,0.59] | - | 0.519 | 0.524 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | pre | POOLED | gbt3/pooled/BOTH | 0.518 [0.49,0.55] | 0.514 [0.48,0.55] | - | 0.511 | 0.511 | - | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| I6-wavelet | sig | LONDON | rf/GI1 | 0.503 [-,-] | 0.514 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| I2-gp | +45 | NY | rf/pooled/xuI2 | 0.486 [0.45,0.52] | 0.513 [0.46,0.57] | - | 0.512 | 0.511 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | sig | POOLED/HM | logit2/GBOTH | 0.518 [0.50,0.54] | 0.513 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | sig | NY | gbt3/xuI2 | 0.517 [-,-] | 0.513 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| I6-wavelet | sig | POOLED/HM | logit2/GBOTH | 0.518 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I7-signature | +10 | POOLED | gbt3/pooled/IONLY | 0.523 [0.50,0.55] | 0.513 [0.47,0.56] | - | 0.508 | 0.514 | - | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| I7-signature | +15 | LONDON | stack/pooled/BOTH | 0.533 [0.49,0.58] | 0.513 [0.45,0.58] | - | 0.500 | 0.487 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +15 | NY | rf/pooled/xuI3P | 0.530 [0.48,0.57] | 0.513 [0.44,0.57] | - | 0.514 | 0.507 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | sig | LONDON | gbt3/xuI3 | 0.512 [-,-] | 0.513 [0.48,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| I5-rocket | +45 | POOLED | rf/pooled/IONLY | 0.530 [0.50,0.55] | 0.512 [0.48,0.55] | - | 0.511 | 0.511 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +10 | LONDON | logit2/pooled/IONLY | 0.516 [0.48,0.56] | 0.512 [0.46,0.57] | - | 0.512 | 0.524 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | sig | LONDON | gbt3/xuI3 | 0.512 [0.49,0.53] | 0.512 [0.48,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| I3P-searchnull | pre | ASIA | stack/pooled/xuI3P | 0.541 [0.50,0.58] | 0.512 [0.45,0.57] | - | 0.503 | 0.509 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3-interactions | +30 | NY | gbt3/pooled/xuI3 | 0.508 [0.46,0.55] | 0.512 [0.44,0.59] | - | 0.508 | 0.497 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +45 | POOLED | rf/pooled/xuI4 | 0.507 [0.48,0.54] | 0.511 [0.47,0.55] | - | 0.511 | 0.500 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | +20 | ASIA | logit2/pooled/IONLY | 0.562 [0.52,0.61] | 0.510 [0.45,0.57] | - | 0.502 | 0.507 | - | - | - | - | - |  | WF-only (dead) |
| I3-interactions | sig | POOLED/ST | logit2/xuI3 | 0.513 [-,-] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| I3P-searchnull | +20 | POOLED | gbt3/pooled/xuI3P | 0.516 [0.49,0.54] | 0.509 [0.47,0.55] | - | 0.508 | 0.511 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I5-rocket | sig | POOLED | gbt3/GBOTH | 0.515 [0.51,0.52] | 0.509 [0.50,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I7-signature | pre | NY | rf/pooled/BOTH | 0.523 [0.47,0.57] | 0.509 [0.44,0.58] | - | 0.519 | 0.509 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +30 | POOLED | stack/pooled/IONLY | 0.521 [0.49,0.55] | 0.509 [0.47,0.55] | - | 0.507 | 0.503 | - | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| I4-autoencoder | pre | POOLED | rf/pooled/xuI4 | 0.511 [0.49,0.54] | 0.508 [0.47,0.54] | - | 0.504 | 0.507 | - | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| I3-interactions | sig | POOLED/HM | rf/xuI3 | 0.519 [-,-] | 0.508 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| I3-interactions | pre | POOLED | logit2/pooled/xuI3 | 0.510 [0.49,0.54] | 0.508 [0.47,0.54] | - | 0.505 | 0.506 | - | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| I6-wavelet | +5 | NY | gbt3/pooled/BOTH | 0.503 [0.47,0.54] | 0.508 [0.45,0.56] | - | 0.516 | 0.500 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | sig | POOLED/HM | rf/GBOTH | 0.517 [0.50,0.53] | 0.507 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3P-searchnull | +60 | ASIA | stack/pooled/xuI3P | 0.533 [0.49,0.58] | 0.507 [0.43,0.58] | - | 0.500 | 0.500 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | +10 | LONDON | gbt3/pooled/xuI2 | 0.497 [0.45,0.54] | 0.507 [0.45,0.56] | - | 0.509 | 0.502 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | sig | POOLED | gbt3/xuI2 | 0.516 [0.50,0.53] | 0.507 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I7-signature | +5 | NY | logit2/pooled/IONLY | 0.508 [0.46,0.55] | 0.507 [0.44,0.57] | - | 0.521 | 0.505 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | sig | POOLED | gbt3/GI1 | 0.513 [-,-] | 0.507 [0.49,0.52] | - | - | - | - | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| I9-normalised | +5 | ASIA | logit2/pooled/IONLY | 0.536 [0.50,0.58] | 0.507 [0.45,0.57] | - | 0.503 | 0.505 | - | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| I5-rocket | sig | POOLED/ST | gbt3/GBOTH | 0.504 [-,-] | 0.506 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I5-rocket | +45 | NY | rf/pooled/IONLY | 0.534 [0.49,0.58] | 0.506 [0.45,0.56] | - | 0.498 | 0.514 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | sig | POOLED | logit2/xuI3 | 0.509 [-,-] | 0.506 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I4-autoencoder | pre | LONDON | logit2/pooled/xuI4 | 0.496 [0.45,0.54] | 0.506 [0.45,0.56] | - | 0.506 | 0.499 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | sig | POOLED/ST | gbt3/xuI4 | 0.502 [-,-] | 0.506 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I7-signature | +15 | NY | gbt3/pooled/BOTH | 0.519 [0.47,0.57] | 0.506 [0.43,0.58] | - | 0.511 | 0.500 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +5 | POOLED | stack/pooled/IONLY | 0.514 [0.49,0.54] | 0.505 [0.46,0.55] | - | 0.503 | 0.497 | - | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| I6-wavelet | sig | POOLED/ST | logit2/GBOTH | 0.502 [-,-] | 0.505 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3P-searchnull | +15 | POOLED | gbt3/pooled/xuI3P | 0.520 [0.50,0.54] | 0.505 [0.47,0.54] | - | 0.504 | 0.500 | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| I4-autoencoder | sig | POOLED | logit2/xuI4 | 0.502 [-,-] | 0.505 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3P-searchnull | +5 | POOLED | rf/pooled/xuI3P | 0.509 [0.48,0.53] | 0.505 [0.47,0.54] | - | 0.505 | 0.509 | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| I4-autoencoder | sig | POOLED/HM | rf/xuI4 | 0.514 [0.50,0.53] | 0.505 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I4-autoencoder | +20 | NY | logit2/pooled/xuI4 | 0.521 [0.48,0.56] | 0.504 [0.44,0.57] | - | 0.513 | 0.501 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | sig | POOLED/ST | gbt3/xuI2 | 0.508 [-,-] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I6-wavelet | sig | ASIA | stack/GBOTH | 0.510 [0.49,0.54] | 0.504 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I5-rocket | pre | POOLED | gbt3/pooled/BOTH | 0.507 [0.48,0.53] | 0.504 [0.47,0.54] | - | 0.498 | 0.502 | - | - | - | - | - | stack | short by 0.176 AUC, 5 of 5 econ |
| I3-interactions | +60 | POOLED | logit2/pooled/xuI3 | 0.509 [0.48,0.53] | 0.504 [0.47,0.54] | - | 0.500 | 0.490 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | sig | POOLED/ST | rf/GI1 | 0.513 [0.50,0.53] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| I4-autoencoder | +15 | NY | logit2/pooled/xuI4 | 0.514 [0.47,0.56] | 0.504 [0.43,0.57] | - | 0.510 | 0.496 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | sig | ASIA | stack/GBOTH | 0.506 [-,-] | 0.503 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| I1-tsfresh | sig | POOLED/ST | gbt3/GI1 | 0.517 [-,-] | 0.503 [0.48,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| I3P-searchnull | +10 | POOLED | rf/pooled/xuI3P | 0.516 [0.49,0.54] | 0.503 [0.46,0.54] | - | 0.503 | 0.498 | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| I3-interactions | +15 | POOLED | stack/pooled/xuI3 | 0.517 [0.49,0.55] | 0.503 [0.47,0.54] | - | 0.501 | 0.502 | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| I7-signature | sig | POOLED | logit2/GBOTH | 0.501 [-,-] | 0.502 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I6-wavelet | sig | POOLED | logit2/GBOTH | 0.501 [-,-] | 0.502 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | +10 | POOLED | gbt3/pooled/xuI2 | 0.507 [0.48,0.53] | 0.502 [0.47,0.54] | - | 0.499 | 0.497 | - | - | - | - | - | stack | short by 0.178 AUC, 5 of 5 econ |
| I1-tsfresh | sig | POOLED/HM | rf/GI1 | 0.509 [-,-] | 0.502 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| I6-wavelet | +45 | LONDON | rf/pooled/BOTH | 0.512 [0.46,0.57] | 0.502 [0.43,0.58] | - | 0.502 | 0.484 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | sig | NY | logit2/xuI3 | 0.515 [-,-] | 0.502 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.178 AUC, 5 of 5 econ |
| I7-signature | +60 | ASIA | stack/pooled/IONLY | 0.543 [0.50,0.59] | 0.501 [0.44,0.56] | - | 0.485 | 0.476 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +20 | POOLED | gbt3/pooled/xuI4 | 0.514 [0.49,0.54] | 0.501 [0.46,0.54] | - | 0.500 | 0.489 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I9-normalised | +5 | LONDON | stack/pooled/IONLY | 0.523 [0.48,0.56] | 0.501 [0.45,0.56] | - | 0.500 | 0.489 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +15 | ASIA | stack/pooled/xuI3 | 0.531 [0.49,0.57] | 0.501 [0.44,0.56] | - | 0.499 | 0.500 | - | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| I9-normalised | +45 | POOLED | rf/pooled/IONLY | 0.516 [0.49,0.54] | 0.500 [0.47,0.54] | - | 0.499 | 0.499 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +5 | LONDON | stack/pooled/xuI3 | 0.540 [0.50,0.58] | 0.500 [0.44,0.56] | - | 0.497 | 0.481 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +60 | NY | gbt3/pooled/xuI3 | 0.496 [0.45,0.54] | 0.500 [0.43,0.57] | - | 0.484 | 0.497 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | sig | ASIA | rf/GI1 | 0.509 [-,-] | 0.500 [0.47,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| I1-tsfresh | sig | ASIA | rf/GI1 | 0.510 [0.49,0.54] | 0.500 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| I7-signature | +10 | NY | gbt3/pooled/IONLY | 0.518 [0.47,0.56] | 0.499 [0.43,0.57] | - | 0.501 | 0.500 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +5 | LONDON | stack/pooled/BOTH | 0.525 [0.48,0.57] | 0.499 [0.43,0.56] | - | 0.498 | 0.483 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | sig | POOLED | gbt3/GBOTH | 0.499 [-,-] | 0.498 [0.48,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I4-autoencoder | +10 | ASIA | stack/pooled/xuI4 | 0.541 [0.50,0.58] | 0.498 [0.43,0.57] | - | 0.485 | 0.492 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3P-searchnull | pre | LONDON | stack/pooled/xuI3P | 0.474 [0.43,0.52] | 0.498 [0.43,0.56] | - | 0.495 | 0.494 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +15 | NY | stack/pooled/BOTH | 0.516 [0.47,0.56] | 0.498 [0.43,0.57] | - | 0.501 | 0.494 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +30 | ASIA | gbt3/pooled/IONLY | 0.554 [0.52,0.59] | 0.498 [0.44,0.56] | - | 0.492 | 0.490 | - | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| I2-gp | +5 | ASIA | logit2/pooled/xuI2 | 0.515 [0.47,0.56] | 0.498 [0.44,0.56] | - | 0.492 | 0.497 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I7-signature | sig | POOLED/HM | logit2/GBOTH | 0.499 [-,-] | 0.498 [0.48,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I6-wavelet | +60 | LONDON | gbt3/pooled/IONLY | 0.535 [0.49,0.58] | 0.498 [0.42,0.57] | - | 0.499 | 0.505 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | sig | POOLED/HM | logit2/GBOTH | 0.499 [-,-] | 0.498 [0.48,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I5-rocket | pre | NY | gbt3/pooled/BOTH | 0.501 [0.46,0.54] | 0.497 [0.44,0.55] | - | 0.493 | 0.493 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +20 | POOLED | stack/pooled/IONLY | 0.524 [0.50,0.55] | 0.497 [0.46,0.54] | - | 0.494 | 0.493 | - | - | - | - | - |  | dead (no gain over baseline) |
| I3P-searchnull | sig | POOLED/HM | gbt3/xuI3P | 0.506 [0.49,0.52] | 0.497 [0.48,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3P-searchnull | +5 | ASIA | rf/pooled/xuI3P | 0.521 [0.48,0.56] | 0.497 [0.45,0.55] | - | 0.501 | 0.495 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | pre | LONDON | stack/pertype/BOTH | 0.524 [0.48,0.57] | 0.497 [0.43,0.56] | - | 0.495 | 0.480 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | sig | ASIA | stack/xuI4 | 0.502 [0.48,0.53] | 0.497 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | sig | ASIA | rf/xuI2 | 0.498 [0.48,0.52] | 0.496 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | sig | POOLED/HM | gbt3/xuI2 | 0.510 [0.49,0.52] | 0.496 [0.48,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3P-searchnull | pre | NY | logit2/pooled/xuI3P | 0.515 [0.47,0.56] | 0.496 [0.44,0.56] | - | 0.491 | 0.501 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | pre | LONDON | stack/pooled/xuI2 | 0.490 [0.45,0.53] | 0.496 [0.44,0.56] | - | 0.491 | 0.488 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +45 | ASIA | gbt3/pooled/IONLY | 0.517 [0.48,0.56] | 0.496 [0.44,0.55] | - | 0.493 | 0.492 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | sig | ASIA | rf/xuI3P | 0.501 [-,-] | 0.495 [0.46,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I4-autoencoder | sig | ASIA | stack/xuI4 | 0.499 [-,-] | 0.495 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | sig | POOLED | gbt3/xuI2 | 0.501 [-,-] | 0.495 [0.48,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | sig | ASIA | rf/xuI2 | 0.497 [-,-] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | +20 | POOLED | logit2/pertype/IONLY | 0.512 [0.49,0.54] | 0.495 [0.46,0.53] | - | 0.493 | 0.493 | - | - | - | - | - |  | dead (no gain over baseline) |
| I5-rocket | +10 | LONDON | logit2/pooled/IONLY | 0.526 [0.48,0.57] | 0.495 [0.44,0.55] | - | 0.495 | 0.504 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | sig | POOLED/ST | rf/GI1 | 0.502 [-,-] | 0.495 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| I1-tsfresh | +30 | ASIA | rf/pooled/IONLY | 0.537 [0.50,0.57] | 0.495 [0.44,0.55] | - | 0.493 | 0.483 | - | - | - | - | - |  | WF-only (dead) |
| I3P-searchnull | +60 | NY | stack/pooled/xuI3P | 0.513 [0.47,0.56] | 0.495 [0.44,0.55] | - | 0.497 | 0.494 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +20 | ASIA | gbt3/pooled/IONLY | 0.533 [0.49,0.57] | 0.495 [0.43,0.55] | - | 0.474 | 0.491 | - | - | - | - | - |  | dead (no gain over baseline) |
| I6-wavelet | pre | POOLED | stack/pooled/BOTH | 0.511 [0.49,0.54] | 0.495 [0.46,0.53] | - | 0.489 | 0.484 | - | - | - | - | - | stack | short by 0.185 AUC, 5 of 5 econ |
| I6-wavelet | +30 | POOLED | stack/pooled/IONLY | 0.524 [0.50,0.55] | 0.494 [0.46,0.53] | - | 0.491 | 0.489 | - | - | - | - | - |  | short by 0.186 AUC, 5 of 5 econ |
| I9-normalised | +5 | POOLED | stack/pooled/IONLY | 0.516 [0.49,0.54] | 0.494 [0.46,0.53] | - | 0.494 | 0.488 | - | - | - | - | - |  | short by 0.186 AUC, 5 of 5 econ |
| I3-interactions | pre | NY | logit2/pooled/xuI3 | 0.495 [0.45,0.54] | 0.494 [0.44,0.55] | - | 0.497 | 0.485 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +15 | POOLED | logit2/pooled/IONLY | 0.507 [0.48,0.53] | 0.494 [0.46,0.53] | - | 0.492 | 0.492 | - | - | - | - | - |  | short by 0.186 AUC, 5 of 5 econ |
| I3P-searchnull | sig | POOLED/HM | gbt3/xuI3P | 0.505 [-,-] | 0.494 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3P-searchnull | sig | ASIA | rf/xuI3P | 0.500 [0.48,0.52] | 0.494 [0.46,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I4-autoencoder | +5 | LONDON | stack/pooled/xuI4 | 0.519 [0.47,0.57] | 0.494 [0.43,0.55] | - | 0.489 | 0.480 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +60 | POOLED | logit2/pooled/IONLY | 0.522 [0.50,0.54] | 0.494 [0.46,0.53] | - | 0.494 | 0.490 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | sig | POOLED/HM | rf/GBOTH | 0.497 [-,-] | 0.493 [0.48,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | +10 | POOLED | logit2/pooled/IONLY | 0.511 [0.49,0.54] | 0.493 [0.46,0.53] | - | 0.495 | 0.493 | - | - | - | - | - |  | short by 0.187 AUC, 5 of 5 econ |
| I2-gp | +30 | POOLED | logit2/pooled/xuI2 | 0.498 [0.47,0.52] | 0.493 [0.46,0.52] | - | 0.489 | 0.486 | - | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| I3-interactions | +20 | LONDON | stack/pooled/xuI3 | 0.516 [0.47,0.56] | 0.493 [0.43,0.56] | - | 0.482 | 0.466 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +5 | NY | stack/pooled/xuI3 | 0.499 [0.45,0.55] | 0.493 [0.44,0.55] | - | 0.508 | 0.486 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +10 | ASIA | rf/pooled/xuI3 | 0.543 [0.50,0.59] | 0.492 [0.43,0.56] | - | 0.483 | 0.487 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3P-searchnull | sig | POOLED | gbt3/xuI3P | 0.497 [0.48,0.51] | 0.492 [0.48,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | +15 | POOLED | rf/pooled/IONLY | 0.513 [0.48,0.54] | 0.492 [0.45,0.54] | - | 0.488 | 0.488 | - | - | - | - | - |  | short by 0.188 AUC, 5 of 5 econ |
| I5-rocket | +5 | NY | logit2/pooled/BOTH | 0.527 [0.49,0.57] | 0.492 [0.44,0.55] | - | 0.501 | 0.488 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +20 | POOLED | stack/pooled/xuI3 | 0.509 [0.48,0.54] | 0.492 [0.45,0.53] | - | 0.485 | 0.477 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3-interactions | +10 | NY | stack/pooled/xuI3 | 0.515 [0.48,0.56] | 0.491 [0.43,0.55] | - | 0.504 | 0.497 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | sig | POOLED | gbt3/xuI3P | 0.497 [-,-] | 0.491 [0.48,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | +60 | NY | gbt3/pooled/xuI2 | 0.483 [0.44,0.53] | 0.490 [0.42,0.56] | - | 0.480 | 0.486 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | sig | LONDON | gbt3/GBOTH | 0.498 [0.48,0.51] | 0.490 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | +15 | NY | logit2/pooled/BOTH | 0.514 [0.47,0.56] | 0.490 [0.43,0.55] | - | 0.494 | 0.481 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +45 | LONDON | stack/pooled/IONLY | 0.516 [0.47,0.56] | 0.490 [0.42,0.55] | - | 0.482 | 0.461 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | sig | POOLED/ST | gbt3/xuI3P | 0.491 [0.48,0.51] | 0.489 [0.47,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3-interactions | +10 | LONDON | stack/pooled/xuI3 | 0.502 [0.46,0.54] | 0.489 [0.43,0.55] | - | 0.484 | 0.484 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +45 | ASIA | stack/pooled/BOTH | 0.530 [0.48,0.58] | 0.489 [0.42,0.56] | - | 0.478 | 0.473 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | sig | POOLED/HM | rf/xuI4 | 0.494 [-,-] | 0.489 [0.47,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | +20 | NY | logit2/pertype/IONLY | 0.517 [0.47,0.56] | 0.489 [0.42,0.55] | - | 0.491 | 0.485 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +10 | POOLED | stack/pooled/IONLY | 0.513 [0.49,0.54] | 0.489 [0.45,0.53] | - | 0.482 | 0.484 | - | - | - | - | - |  | short by 0.191 AUC, 5 of 5 econ |
| I3P-searchnull | sig | POOLED/ST | gbt3/xuI3P | 0.491 [-,-] | 0.489 [0.47,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | +5 | LONDON | stack/pooled/BOTH | 0.511 [0.47,0.56] | 0.489 [0.43,0.55] | - | 0.487 | 0.479 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | pre | LONDON | logit2/pooled/xuI3 | 0.513 [0.47,0.56] | 0.489 [0.42,0.55] | - | 0.487 | 0.492 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | +20 | ASIA | logit2/pooled/xuI2 | 0.509 [0.47,0.55] | 0.488 [0.43,0.54] | - | 0.480 | 0.493 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | +60 | LONDON | gbt3/pooled/BOTH | 0.519 [0.47,0.57] | 0.488 [0.43,0.55] | - | 0.483 | 0.468 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +5 | ASIA | logit2/pooled/xuI3 | 0.504 [0.46,0.55] | 0.488 [0.43,0.55] | - | 0.473 | 0.490 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3-interactions | +10 | POOLED | stack/pooled/xuI3 | 0.524 [0.50,0.55] | 0.488 [0.45,0.53] | - | 0.489 | 0.485 | - | - | - | - | - | stack | short by 0.192 AUC, 5 of 5 econ |
| I1-tsfresh | pre | POOLED | gbt3/pertype/IONLY | 0.499 [0.48,0.52] | 0.488 [0.45,0.53] | - | 0.486 | 0.488 | - | - | - | - | - |  | dead (no gain over baseline) |
| I4-autoencoder | +15 | ASIA | stack/pooled/xuI4 | 0.537 [0.50,0.57] | 0.488 [0.42,0.55] | - | 0.483 | 0.479 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I4-autoencoder | sig | LONDON | rf/xuI4 | 0.491 [0.47,0.51] | 0.487 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | pre | POOLED | stack/pooled/xuI2 | 0.491 [0.46,0.52] | 0.487 [0.45,0.52] | - | 0.485 | 0.484 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I5-rocket | sig | LONDON | gbt3/GBOTH | 0.496 [-,-] | 0.487 [0.46,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | +30 | POOLED | stack/pertype/IONLY | 0.507 [0.48,0.53] | 0.487 [0.45,0.53] | - | 0.482 | 0.481 | - | - | - | - | - |  | short by 0.193 AUC, 5 of 5 econ |
| I3P-searchnull | sig | NY | rf/xuI3P | 0.501 [0.48,0.52] | 0.487 [0.46,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I7-signature | +60 | LONDON | gbt3/pooled/BOTH | 0.513 [0.46,0.56] | 0.487 [0.42,0.56] | - | 0.479 | 0.479 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | +45 | LONDON | stack/pooled/xuI2 | 0.501 [0.45,0.56] | 0.486 [0.42,0.55] | - | 0.482 | 0.469 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +20 | POOLED | stack/pooled/BOTH | 0.513 [0.49,0.54] | 0.486 [0.45,0.52] | - | 0.482 | 0.488 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | sig | LONDON | gbt3/xuI2 | 0.492 [0.47,0.51] | 0.485 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | +15 | ASIA | gbt3/pooled/xuI2 | 0.540 [0.50,0.59] | 0.485 [0.43,0.54] | - | 0.475 | 0.478 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | pre | ASIA | stack/pooled/xuI2 | 0.503 [0.46,0.54] | 0.485 [0.43,0.54] | - | 0.478 | 0.486 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3P-searchnull | +20 | NY | gbt3/pooled/xuI3P | 0.492 [0.45,0.53] | 0.484 [0.43,0.54] | - | 0.491 | 0.489 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +45 | ASIA | stack/pooled/xuI3P | 0.517 [0.47,0.56] | 0.484 [0.42,0.55] | - | 0.485 | 0.467 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | sig | LONDON | rf/xuI4 | 0.489 [-,-] | 0.484 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3-interactions | +20 | ASIA | stack/pooled/xuI3 | 0.554 [0.51,0.60] | 0.484 [0.42,0.55] | - | 0.467 | 0.478 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I6-wavelet | +45 | ASIA | gbt3/pooled/IONLY | 0.532 [0.49,0.57] | 0.484 [0.41,0.55] | - | 0.483 | 0.479 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | sig | LONDON | rf/GI1 | 0.495 [0.47,0.52] | 0.483 [0.46,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| I3-interactions | +5 | POOLED | stack/pooled/xuI3 | 0.514 [0.49,0.54] | 0.483 [0.45,0.52] | - | 0.480 | 0.476 | - | - | - | - | - | stack | WF-only (dead) |
| I2-gp | sig | LONDON | gbt3/xuI2 | 0.491 [-,-] | 0.483 [0.46,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | +10 | ASIA | rf/pooled/BOTH | 0.543 [0.49,0.59] | 0.483 [0.42,0.55] | - | 0.482 | 0.476 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3P-searchnull | sig | NY | rf/xuI3P | 0.500 [-,-] | 0.482 [0.46,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I2-gp | sig | POOLED/HM | gbt3/xuI2 | 0.492 [-,-] | 0.482 [0.46,0.50] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| I9-normalised | +30 | LONDON | stack/pooled/BOTH | 0.517 [0.48,0.56] | 0.482 [0.41,0.55] | - | 0.481 | 0.458 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | sig | LONDON | rf/GI1 | 0.494 [-,-] | 0.482 [0.46,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| I7-signature | pre | LONDON | stack/pooled/BOTH | 0.508 [0.46,0.56] | 0.482 [0.42,0.54] | - | 0.469 | 0.470 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | +45 | POOLED | stack/pooled/IONLY | 0.519 [0.49,0.55] | 0.481 [0.44,0.52] | - | 0.476 | 0.466 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +20 | ASIA | logit2/pooled/IONLY | 0.545 [0.50,0.59] | 0.481 [0.42,0.54] | - | 0.476 | 0.478 | - | - | - | - | - |  | dead (no gain over baseline) |
| I9-normalised | +20 | NY | stack/pooled/BOTH | 0.501 [0.46,0.54] | 0.481 [0.42,0.55] | - | 0.481 | 0.477 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | pre | LONDON | stack/pooled/IONLY | 0.503 [0.46,0.55] | 0.480 [0.42,0.54] | - | 0.472 | 0.472 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3-interactions | +15 | NY | rf/pooled/xuI3 | 0.489 [0.45,0.53] | 0.480 [0.40,0.55] | - | 0.482 | 0.478 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | pre | POOLED | stack/pooled/xuI3P | 0.501 [0.48,0.53] | 0.480 [0.45,0.51] | - | 0.478 | 0.478 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I7-signature | +5 | LONDON | stack/pooled/BOTH | 0.510 [0.46,0.56] | 0.479 [0.41,0.54] | - | 0.473 | 0.463 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +5 | NY | rf/pooled/xuI3P | 0.509 [0.46,0.55] | 0.479 [0.41,0.55] | - | 0.476 | 0.485 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | pre | ASIA | stack/pooled/BOTH | 0.523 [0.49,0.56] | 0.478 [0.42,0.53] | - | 0.458 | 0.477 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I1-tsfresh | +10 | LONDON | stack/pertype/IONLY | 0.499 [0.45,0.55] | 0.478 [0.41,0.55] | - | 0.473 | 0.469 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | +10 | NY | stack/pertype/BOTH | 0.504 [0.46,0.55] | 0.477 [0.42,0.53] | - | 0.477 | 0.472 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +30 | LONDON | gbt3/pooled/IONLY | 0.525 [0.48,0.57] | 0.477 [0.42,0.54] | - | 0.491 | 0.481 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +10 | LONDON | stack/pooled/IONLY | 0.506 [0.46,0.56] | 0.476 [0.42,0.53] | - | 0.468 | 0.463 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | pre | LONDON | logit2/pooled/IONLY | 0.509 [0.46,0.55] | 0.476 [0.41,0.54] | - | 0.480 | 0.471 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +60 | LONDON | stack/pooled/IONLY | 0.519 [0.47,0.57] | 0.476 [0.41,0.54] | - | 0.474 | 0.460 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | pre | LONDON | stack/pooled/BOTH | 0.505 [0.46,0.55] | 0.476 [0.41,0.54] | - | 0.471 | 0.454 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +60 | POOLED | stack/pooled/xuI3P | 0.499 [0.47,0.53] | 0.475 [0.44,0.51] | - | 0.475 | 0.467 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +20 | LONDON | stack/pooled/BOTH | 0.500 [0.45,0.55] | 0.474 [0.41,0.53] | - | 0.474 | 0.461 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +15 | ASIA | gbt3/pooled/xuI3P | 0.504 [0.46,0.55] | 0.473 [0.40,0.54] | - | 0.480 | 0.471 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I6-wavelet | +60 | POOLED | stack/pooled/BOTH | 0.512 [0.48,0.54] | 0.473 [0.43,0.51] | - | 0.468 | 0.460 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +60 | NY | stack/pooled/xuI4 | 0.478 [0.43,0.53] | 0.473 [0.40,0.55] | - | 0.470 | 0.470 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +60 | NY | gbt3/pooled/IONLY | 0.523 [0.48,0.57] | 0.473 [0.41,0.53] | - | 0.468 | 0.488 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +60 | NY | gbt3/pooled/IONLY | 0.495 [0.45,0.54] | 0.471 [0.41,0.53] | - | 0.474 | 0.468 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +15 | LONDON | stack/pooled/BOTH | 0.494 [0.45,0.54] | 0.471 [0.41,0.53] | - | 0.457 | 0.462 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +60 | POOLED | stack/pooled/BOTH | 0.506 [0.48,0.54] | 0.471 [0.43,0.51] | - | 0.463 | 0.460 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +15 | POOLED | stack/pooled/BOTH | 0.507 [0.48,0.54] | 0.470 [0.43,0.51] | - | 0.462 | 0.458 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I7-signature | +10 | ASIA | gbt3/pooled/IONLY | 0.518 [0.48,0.56] | 0.469 [0.40,0.53] | - | 0.459 | 0.468 | - | - | - | - | - |  | dead (no gain over baseline) |
| I1-tsfresh | +5 | POOLED | stack/pertype/IONLY | 0.503 [0.48,0.53] | 0.468 [0.43,0.50] | - | 0.467 | 0.470 | - | - | - | - | - |  | dead (no gain over baseline) |
| I3P-searchnull | +60 | LONDON | logit2/pooled/xuI3P | 0.482 [0.44,0.53] | 0.467 [0.40,0.53] | - | 0.468 | 0.461 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | +15 | LONDON | rf/pooled/IONLY | 0.500 [0.45,0.55] | 0.466 [0.39,0.54] | - | 0.460 | 0.473 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +45 | POOLED | stack/pooled/xuI3P | 0.500 [0.48,0.52] | 0.466 [0.43,0.51] | - | 0.466 | 0.455 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +45 | NY | rf/pooled/xuI3P | 0.510 [0.47,0.55] | 0.466 [0.41,0.53] | - | 0.461 | 0.466 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +20 | NY | stack/pooled/BOTH | 0.509 [0.47,0.55] | 0.466 [0.40,0.53] | - | 0.474 | 0.463 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | +30 | LONDON | gbt3/pooled/xuI2 | 0.456 [0.42,0.50] | 0.466 [0.40,0.54] | - | 0.460 | 0.447 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +30 | NY | rf/pooled/IONLY | 0.497 [0.46,0.54] | 0.465 [0.40,0.53] | - | 0.462 | 0.464 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +45 | NY | gbt3/pooled/BOTH | 0.481 [0.44,0.52] | 0.462 [0.40,0.53] | - | 0.460 | 0.460 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +60 | LONDON | logit2/pooled/IONLY | 0.516 [0.48,0.55] | 0.462 [0.41,0.52] | - | 0.461 | 0.455 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +60 | LONDON | stack/pooled/xuI4 | 0.521 [0.47,0.57] | 0.462 [0.40,0.53] | - | 0.450 | 0.440 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +30 | POOLED | gbt3/pooled/IONLY | 0.498 [0.47,0.52] | 0.460 [0.43,0.49] | - | 0.460 | 0.456 | - | - | - | - | - |  | short by 0.220 AUC, 5 of 5 econ |
| I1-tsfresh | +60 | POOLED | stack/pooled/BOTH | 0.506 [0.48,0.53] | 0.460 [0.42,0.50] | - | 0.459 | 0.441 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +30 | ASIA | stack/pooled/xuI3P | 0.507 [0.47,0.55] | 0.460 [0.40,0.52] | - | 0.460 | 0.465 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I6-wavelet | +15 | LONDON | stack/pooled/BOTH | 0.510 [0.46,0.56] | 0.460 [0.40,0.52] | - | 0.448 | 0.440 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +60 | POOLED | stack/pooled/IONLY | 0.495 [0.47,0.52] | 0.459 [0.42,0.50] | - | 0.454 | 0.439 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | +30 | NY | logit2/pertype/IONLY | 0.491 [0.45,0.53] | 0.459 [0.40,0.52] | - | 0.465 | 0.461 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +30 | LONDON | logit2/pooled/xuI3P | 0.494 [0.45,0.53] | 0.458 [0.40,0.51] | - | 0.459 | 0.447 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +5 | POOLED | stack/pooled/xuI4 | 0.497 [0.47,0.52] | 0.458 [0.42,0.50] | - | 0.455 | 0.452 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I9-normalised | +5 | NY | logit2/pooled/BOTH | 0.481 [0.44,0.52] | 0.455 [0.39,0.52] | - | 0.454 | 0.454 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | +45 | LONDON | stack/pooled/IONLY | 0.504 [0.46,0.55] | 0.455 [0.40,0.52] | - | 0.449 | 0.432 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +10 | POOLED | stack/pooled/BOTH | 0.506 [0.48,0.53] | 0.455 [0.42,0.49] | - | 0.447 | 0.449 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3P-searchnull | +20 | ASIA | rf/pooled/xuI3P | 0.514 [0.47,0.55] | 0.454 [0.40,0.51] | - | 0.453 | 0.454 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I4-autoencoder | +15 | POOLED | stack/pooled/xuI4 | 0.507 [0.48,0.53] | 0.454 [0.41,0.50] | - | 0.447 | 0.442 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I7-signature | +30 | LONDON | stack/pooled/BOTH | 0.495 [0.45,0.54] | 0.454 [0.40,0.51] | - | 0.450 | 0.450 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +10 | LONDON | stack/pooled/BOTH | 0.503 [0.46,0.55] | 0.454 [0.40,0.51] | - | 0.447 | 0.438 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +30 | LONDON | stack/pooled/BOTH | 0.500 [0.46,0.54] | 0.454 [0.40,0.52] | - | 0.443 | 0.446 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +45 | LONDON | gbt3/pooled/IONLY | 0.517 [0.47,0.56] | 0.454 [0.40,0.51] | - | 0.451 | 0.454 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +60 | NY | gbt3/pooled/IONLY | 0.477 [0.44,0.52] | 0.453 [0.40,0.52] | - | 0.444 | 0.454 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +45 | LONDON | stack/pooled/BOTH | 0.506 [0.46,0.55] | 0.452 [0.39,0.52] | - | 0.436 | 0.429 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +15 | LONDON | stack/pooled/xuI4 | 0.498 [0.46,0.54] | 0.451 [0.39,0.51] | - | 0.432 | 0.427 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +5 | ASIA | stack/pooled/xuI4 | 0.517 [0.48,0.55] | 0.451 [0.39,0.51] | - | 0.441 | 0.451 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I3P-searchnull | +45 | LONDON | stack/pooled/xuI3P | 0.477 [0.44,0.52] | 0.451 [0.39,0.51] | - | 0.445 | 0.439 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +20 | LONDON | stack/pooled/IONLY | 0.504 [0.46,0.54] | 0.448 [0.40,0.50] | - | 0.447 | 0.433 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +20 | LONDON | stack/pooled/IONLY | 0.500 [0.46,0.55] | 0.446 [0.39,0.51] | - | 0.443 | 0.433 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | pre | NY | gbt3/pooled/IONLY | 0.489 [0.45,0.53] | 0.445 [0.38,0.50] | - | 0.445 | 0.445 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +15 | NY | stack/pooled/BOTH | 0.492 [0.45,0.54] | 0.443 [0.38,0.51] | - | 0.452 | 0.439 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +20 | NY | stack/pooled/BOTH | 0.505 [0.46,0.55] | 0.442 [0.37,0.51] | - | 0.437 | 0.440 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I2-gp | +30 | NY | stack/pooled/xuI2 | 0.476 [0.43,0.52] | 0.441 [0.38,0.50] | - | 0.445 | 0.433 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +10 | NY | rf/pooled/xuI3P | 0.474 [0.44,0.51] | 0.441 [0.38,0.50] | - | 0.450 | 0.436 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +20 | LONDON | stack/pooled/IONLY | 0.493 [0.45,0.53] | 0.438 [0.37,0.50] | - | 0.437 | 0.424 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | +20 | LONDON | stack/pooled/IONLY | 0.487 [0.44,0.53] | 0.437 [0.37,0.50] | - | 0.431 | 0.427 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +30 | POOLED | stack/pooled/xuI4 | 0.494 [0.47,0.52] | 0.437 [0.40,0.47] | - | 0.435 | 0.435 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I6-wavelet | +45 | NY | stack/pooled/IONLY | 0.492 [0.45,0.54] | 0.436 [0.37,0.50] | - | 0.433 | 0.433 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I9-normalised | +10 | NY | stack/pooled/BOTH | 0.493 [0.46,0.53] | 0.430 [0.37,0.49] | - | 0.433 | 0.432 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +30 | LONDON | stack/pooled/xuI4 | 0.503 [0.46,0.55] | 0.429 [0.38,0.49] | - | 0.431 | 0.426 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +30 | POOLED | stack/pooled/xuI3P | 0.484 [0.46,0.51] | 0.428 [0.39,0.47] | - | 0.427 | 0.429 | - | - | - | - | - | stack | dead (no gain over baseline) |
| I9-normalised | +60 | NY | stack/pooled/BOTH | 0.485 [0.44,0.53] | 0.427 [0.36,0.49] | - | 0.418 | 0.430 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | +30 | LONDON | stack/pooled/BOTH | 0.499 [0.45,0.55] | 0.425 [0.37,0.49] | - | 0.419 | 0.415 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I3P-searchnull | +30 | NY | rf/pooled/xuI3P | 0.498 [0.45,0.55] | 0.417 [0.35,0.49] | - | 0.413 | 0.420 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I6-wavelet | +30 | NY | stack/pooled/BOTH | 0.493 [0.44,0.54] | 0.408 [0.35,0.47] | - | 0.411 | 0.408 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +45 | NY | stack/pooled/xuI4 | 0.477 [0.44,0.52] | 0.404 [0.35,0.47] | - | 0.404 | 0.409 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I5-rocket | +10 | NY | rf/pooled/IONLY | 0.479 [0.43,0.52] | 0.403 [0.35,0.47] | - | 0.409 | 0.403 | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| I4-autoencoder | +30 | NY | stack/pooled/xuI4 | 0.478 [0.43,0.53] | 0.401 [0.34,0.47] | - | 0.412 | 0.400 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I1-tsfresh | +60 | NY | stack/pooled/BOTH | 0.489 [0.44,0.53] | 0.383 [0.33,0.44] | - | 0.381 | 0.379 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| I7-signature | +30 | NY | stack/pooled/BOTH | 0.473 [0.42,0.52] | 0.379 [0.31,0.45] | - | 0.389 | 0.372 | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |

One-sentence notes:
- I1-tsfresh 0 LONDON: I1-tsfresh: I1-BASE cond baseline hold 0.448 strata 0.440; delta +0.049
- I1-tsfresh 10 NY: I1-tsfresh: I1-BASE cond baseline hold 0.508 strata 0.509; delta -0.030
- I1-tsfresh 5 ASIA: I1-tsfresh: I1-BASE cond baseline hold 0.520 strata 0.519; delta -0.005
- I1-tsfresh 5 NY: I1-tsfresh: I1-BASE cond baseline hold 0.507 strata 0.509; delta +0.037
- I1-tsfresh 0 NY: I1-tsfresh: I1-BASE cond baseline hold 0.522 strata 0.526; delta -0.004
- I1-tsfresh 0 ASIA: I1-tsfresh: I1-BASE cond baseline hold 0.536 strata 0.526; delta -0.058
- I1-tsfresh 10 ASIA: I1-tsfresh: I1-BASE cond baseline hold 0.501 strata 0.490; delta -0.018
- I1-tsfresh 15 NY: I1-tsfresh: I1-BASE cond baseline hold 0.499 strata 0.503; delta -0.009
- I1-tsfresh 30 LONDON: I1-tsfresh: I1-BASE cond baseline hold 0.438 strata 0.444; delta -0.013
- I1-tsfresh 5 LONDON: I1-tsfresh: I1-BASE cond baseline hold 0.474 strata 0.464; delta +0.015
- I1-tsfresh 60 ASIA: I1-tsfresh: I1-BASE cond baseline hold 0.476 strata 0.460; delta +0.044
- I1-tsfresh 60 LONDON: I1-tsfresh: I1-BASE cond baseline hold 0.538 strata 0.534; delta -0.050
- I1-tsfresh 60 POOLED: I1-tsfresh: I1-BASE cond baseline hold 0.497 strata 0.492; delta -0.037
- I1-tsfresh 60 NY: I1-tsfresh: I1-BASE cond baseline hold 0.503 strata 0.505; delta -0.120
- I1-tsfresh 0 POOLED: I1-tsfresh: I1-BASE cond baseline hold 0.509 strata 0.507; delta -0.021
- I1-tsfresh 10 LONDON: I1-tsfresh: I1-BASE cond baseline hold 0.542 strata 0.541; delta -0.065
- I1-tsfresh 20 POOLED: I1-tsfresh: I1-BASE cond baseline hold 0.498 strata 0.490; delta -0.003
- I1-tsfresh 20 NY: I1-tsfresh: I1-BASE cond baseline hold 0.482 strata 0.489; delta +0.007
- I1-tsfresh 30 NY: I1-tsfresh: I1-BASE cond baseline hold 0.396 strata 0.404; delta +0.063
- I1-tsfresh 30 POOLED: I1-tsfresh: I1-BASE cond baseline hold 0.439 strata 0.437; delta +0.048
- I1-tsfresh 5 POOLED: I1-tsfresh: I1-BASE cond baseline hold 0.513 strata 0.508; delta -0.045
- I1-tsfresh 10 POOLED: I1-tsfresh: I1-BASE cond baseline hold 0.514 strata 0.515; delta -0.021
- I1-tsfresh 15 ASIA: I1-tsfresh: I1-BASE cond baseline hold 0.470 strata 0.458; delta +0.047
- I1-tsfresh 15 POOLED: I1-tsfresh: I1-BASE cond baseline hold 0.453 strata 0.443; delta +0.040
- I1-tsfresh 15 LONDON: I1-tsfresh: I1-BASE cond baseline hold 0.442 strata 0.425; delta +0.024
- I1-tsfresh 20 ASIA: I1-tsfresh: I1-BASE cond baseline hold 0.511 strata 0.491; delta -0.001
- I1-tsfresh 20 LONDON: I1-tsfresh: I1-BASE cond baseline hold 0.523 strata 0.528; delta -0.086
- I1-tsfresh 30 ASIA: I1-tsfresh: I1-BASE cond baseline hold 0.518 strata 0.510; delta -0.023
- I1-tsfresh 45 ASIA: I1-tsfresh: I1-BASE cond baseline hold 0.536 strata 0.534; delta +0.019
- I1-tsfresh 45 NY: I1-tsfresh: I1-BASE cond baseline hold 0.467 strata 0.460; delta +0.104
- I1-tsfresh 45 POOLED: I1-tsfresh: I1-BASE cond baseline hold 0.490 strata 0.488; delta -0.008
- I1-tsfresh 45 LONDON: I1-tsfresh: I1-BASE cond baseline hold 0.518 strata 0.509; delta -0.063
- I9-normalised 0 POOLED: I9-normalised: I1-BASE cond baseline hold 0.509 strata 0.507; delta +0.008
- I9-normalised 10 POOLED: I9-normalised: I1-BASE cond baseline hold 0.514 strata 0.515; delta -0.059
- I9-normalised 10 LONDON: I9-normalised: I1-BASE cond baseline hold 0.542 strata 0.541; delta -0.089
- I9-normalised 10 NY: I9-normalised: I1-BASE cond baseline hold 0.508 strata 0.509; delta -0.078
- I9-normalised 15 LONDON: I9-normalised: I1-BASE cond baseline hold 0.442 strata 0.425; delta +0.029
- I9-normalised 15 NY: I9-normalised: I1-BASE cond baseline hold 0.499 strata 0.503; delta -0.001
- I9-normalised 20 LONDON: I9-normalised: I1-BASE cond baseline hold 0.523 strata 0.528; delta -0.049
- I9-normalised 20 NY: I9-normalised: I1-BASE cond baseline hold 0.482 strata 0.489; delta -0.001
- I9-normalised 30 ASIA: I9-normalised: I1-BASE cond baseline hold 0.518 strata 0.510; delta +0.002
- I9-normalised 30 LONDON: I9-normalised: I1-BASE cond baseline hold 0.438 strata 0.444; delta +0.044
- I9-normalised 45 ASIA: I9-normalised: I1-BASE cond baseline hold 0.536 strata 0.534; delta -0.046
- I9-normalised 45 LONDON: I9-normalised: I1-BASE cond baseline hold 0.518 strata 0.509; delta -0.066
- I9-normalised 5 NY: I9-normalised: I1-BASE cond baseline hold 0.507 strata 0.509; delta -0.051
- I9-normalised 60 POOLED: I9-normalised: I1-BASE cond baseline hold 0.497 strata 0.492; delta -0.027
- I9-normalised 60 NY: I9-normalised: I1-BASE cond baseline hold 0.503 strata 0.505; delta -0.076
- I9-normalised 0 NY: I9-normalised: I1-BASE cond baseline hold 0.522 strata 0.526; delta -0.077
- I9-normalised 0 LONDON: I9-normalised: I1-BASE cond baseline hold 0.448 strata 0.440; delta +0.029
- I9-normalised 0 ASIA: I9-normalised: I1-BASE cond baseline hold 0.536 strata 0.526; delta +0.009
- I9-normalised 10 ASIA: I9-normalised: I1-BASE cond baseline hold 0.501 strata 0.490; delta +0.016
- I9-normalised 15 POOLED: I9-normalised: I1-BASE cond baseline hold 0.453 strata 0.443; delta +0.042
- I9-normalised 15 ASIA: I9-normalised: I1-BASE cond baseline hold 0.470 strata 0.458; delta +0.058
- I9-normalised 20 ASIA: I9-normalised: I1-BASE cond baseline hold 0.511 strata 0.491; delta -0.030
- I9-normalised 20 POOLED: I9-normalised: I1-BASE cond baseline hold 0.498 strata 0.490; delta +0.031
- I9-normalised 30 POOLED: I9-normalised: I1-BASE cond baseline hold 0.439 strata 0.437; delta +0.022
- I9-normalised 30 NY: I9-normalised: I1-BASE cond baseline hold 0.396 strata 0.404; delta +0.069
- I9-normalised 45 NY: I9-normalised: I1-BASE cond baseline hold 0.467 strata 0.460; delta +0.057
- I9-normalised 45 POOLED: I9-normalised: I1-BASE cond baseline hold 0.490 strata 0.488; delta +0.010
- I9-normalised 5 ASIA: I9-normalised: I1-BASE cond baseline hold 0.520 strata 0.519; delta -0.013
- I9-normalised 5 POOLED: I9-normalised: I1-BASE cond baseline hold 0.513 strata 0.508; delta -0.018
- I9-normalised 5 LONDON: I9-normalised: I1-BASE cond baseline hold 0.474 strata 0.464; delta +0.027
- I9-normalised 60 ASIA: I9-normalised: I1-BASE cond baseline hold 0.476 strata 0.460; delta +0.074
- I9-normalised 60 LONDON: I9-normalised: I1-BASE cond baseline hold 0.538 strata 0.534; delta -0.063
- I5-rocket 0 POOLED: I5-rocket: I1-BASE cond baseline hold 0.509 strata 0.507; delta -0.004
- I5-rocket 0 ASIA: I5-rocket: I1-BASE cond baseline hold 0.536 strata 0.526; delta -0.017
- I5-rocket 0 NY: I5-rocket: I1-BASE cond baseline hold 0.522 strata 0.526; delta -0.025
- I5-rocket 15 NY: I5-rocket: I1-BASE cond baseline hold 0.499 strata 0.503; delta +0.024
- I5-rocket 15 ASIA: I5-rocket: I1-BASE cond baseline hold 0.470 strata 0.458; delta +0.138
- I5-rocket 15 LONDON: I5-rocket: I1-BASE cond baseline hold 0.442 strata 0.425; delta +0.075
- I5-rocket 20 ASIA: I5-rocket: I1-BASE cond baseline hold 0.511 strata 0.491; delta +0.060
- I5-rocket 30 ASIA: I5-rocket: I1-BASE cond baseline hold 0.518 strata 0.510; delta +0.079
- I5-rocket 45 ASIA: I5-rocket: I1-BASE cond baseline hold 0.536 strata 0.534; delta +0.011
- I5-rocket 5 NY: I5-rocket: I1-BASE cond baseline hold 0.507 strata 0.509; delta -0.015
- I5-rocket 5 LONDON: I5-rocket: I1-BASE cond baseline hold 0.474 strata 0.464; delta +0.044
- I5-rocket 60 ASIA: I5-rocket: I1-BASE cond baseline hold 0.476 strata 0.460; delta +0.064
- I5-rocket 0 LONDON: I5-rocket: I1-BASE cond baseline hold 0.448 strata 0.440; delta +0.033
- I5-rocket 10 LONDON: I5-rocket: I1-BASE cond baseline hold 0.542 strata 0.541; delta -0.048
- I5-rocket 10 NY: I5-rocket: I1-BASE cond baseline hold 0.508 strata 0.509; delta -0.105
- I5-rocket 10 POOLED: I5-rocket: I1-BASE cond baseline hold 0.514 strata 0.515; delta -0.025
- I5-rocket 10 ASIA: I5-rocket: I1-BASE cond baseline hold 0.501 strata 0.490; delta +0.023
- I5-rocket 15 POOLED: I5-rocket: I1-BASE cond baseline hold 0.453 strata 0.443; delta +0.071
- I5-rocket 20 NY: I5-rocket: I1-BASE cond baseline hold 0.482 strata 0.489; delta +0.059
- I5-rocket 20 POOLED: I5-rocket: I1-BASE cond baseline hold 0.498 strata 0.490; delta +0.025
- I5-rocket 20 LONDON: I5-rocket: I1-BASE cond baseline hold 0.523 strata 0.528; delta -0.075
- I5-rocket 30 POOLED: I5-rocket: I1-BASE cond baseline hold 0.439 strata 0.437; delta +0.081
- I5-rocket 30 LONDON: I5-rocket: I1-BASE cond baseline hold 0.438 strata 0.444; delta +0.040
- I5-rocket 30 NY: I5-rocket: I1-BASE cond baseline hold 0.396 strata 0.404; delta +0.123
- I5-rocket 45 LONDON: I5-rocket: I1-BASE cond baseline hold 0.518 strata 0.509; delta -0.064
- I5-rocket 45 POOLED: I5-rocket: I1-BASE cond baseline hold 0.490 strata 0.488; delta +0.022
- I5-rocket 45 NY: I5-rocket: I1-BASE cond baseline hold 0.467 strata 0.460; delta +0.040
- I5-rocket 5 ASIA: I5-rocket: I1-BASE cond baseline hold 0.520 strata 0.519; delta +0.042
- I5-rocket 5 POOLED: I5-rocket: I1-BASE cond baseline hold 0.513 strata 0.508; delta +0.021
- I5-rocket 60 NY: I5-rocket: I1-BASE cond baseline hold 0.503 strata 0.505; delta -0.031
- I5-rocket 60 POOLED: I5-rocket: I1-BASE cond baseline hold 0.497 strata 0.492; delta -0.004
- I5-rocket 60 LONDON: I5-rocket: I1-BASE cond baseline hold 0.538 strata 0.534; delta -0.076
- I6-wavelet 0 NY: I6-wavelet: I1-BASE cond baseline hold 0.522 strata 0.526; delta +0.010
- I6-wavelet 0 POOLED: I6-wavelet: I1-BASE cond baseline hold 0.509 strata 0.507; delta -0.014
- I6-wavelet 0 ASIA: I6-wavelet: I1-BASE cond baseline hold 0.536 strata 0.526; delta -0.006
- I6-wavelet 0 LONDON: I6-wavelet: I1-BASE cond baseline hold 0.448 strata 0.440; delta +0.028
- I6-wavelet 10 POOLED: I6-wavelet: I1-BASE cond baseline hold 0.514 strata 0.515; delta +0.014
- I6-wavelet 10 NY: I6-wavelet: I1-BASE cond baseline hold 0.508 strata 0.509; delta +0.012
- I6-wavelet 15 POOLED: I6-wavelet: I1-BASE cond baseline hold 0.453 strata 0.443; delta +0.018
- I6-wavelet 15 LONDON: I6-wavelet: I1-BASE cond baseline hold 0.442 strata 0.425; delta +0.018
- I6-wavelet 15 NY: I6-wavelet: I1-BASE cond baseline hold 0.499 strata 0.503; delta -0.055
- I6-wavelet 20 NY: I6-wavelet: I1-BASE cond baseline hold 0.482 strata 0.489; delta -0.016
- I6-wavelet 30 LONDON: I6-wavelet: I1-BASE cond baseline hold 0.438 strata 0.444; delta +0.016
- I6-wavelet 30 NY: I6-wavelet: I1-BASE cond baseline hold 0.396 strata 0.404; delta +0.012
- I6-wavelet 45 POOLED: I6-wavelet: I1-BASE cond baseline hold 0.490 strata 0.488; delta +0.026
- I6-wavelet 45 LONDON: I6-wavelet: I1-BASE cond baseline hold 0.518 strata 0.509; delta -0.016
- I6-wavelet 5 NY: I6-wavelet: I1-BASE cond baseline hold 0.507 strata 0.509; delta +0.001
- I6-wavelet 5 POOLED: I6-wavelet: I1-BASE cond baseline hold 0.513 strata 0.508; delta +0.011
- I6-wavelet 5 ASIA: I6-wavelet: I1-BASE cond baseline hold 0.520 strata 0.519; delta +0.015
- I6-wavelet 5 LONDON: I6-wavelet: I1-BASE cond baseline hold 0.474 strata 0.464; delta +0.025
- I6-wavelet 60 POOLED: I6-wavelet: I1-BASE cond baseline hold 0.497 strata 0.492; delta -0.024
- I6-wavelet 10 ASIA: I6-wavelet: I1-BASE cond baseline hold 0.501 strata 0.490; delta +0.043
- I6-wavelet 10 LONDON: I6-wavelet: I1-BASE cond baseline hold 0.542 strata 0.541; delta -0.066
- I6-wavelet 15 ASIA: I6-wavelet: I1-BASE cond baseline hold 0.470 strata 0.458; delta +0.072
- I6-wavelet 20 ASIA: I6-wavelet: I1-BASE cond baseline hold 0.511 strata 0.491; delta +0.019
- I6-wavelet 20 POOLED: I6-wavelet: I1-BASE cond baseline hold 0.498 strata 0.490; delta -0.000
- I6-wavelet 20 LONDON: I6-wavelet: I1-BASE cond baseline hold 0.523 strata 0.528; delta -0.077
- I6-wavelet 30 ASIA: I6-wavelet: I1-BASE cond baseline hold 0.518 strata 0.510; delta -0.020
- I6-wavelet 30 POOLED: I6-wavelet: I1-BASE cond baseline hold 0.439 strata 0.437; delta +0.056
- I6-wavelet 45 ASIA: I6-wavelet: I1-BASE cond baseline hold 0.536 strata 0.534; delta -0.052
- I6-wavelet 45 NY: I6-wavelet: I1-BASE cond baseline hold 0.467 strata 0.460; delta -0.030
- I6-wavelet 60 LONDON: I6-wavelet: I1-BASE cond baseline hold 0.538 strata 0.534; delta -0.041
- I6-wavelet 60 NY: I6-wavelet: I1-BASE cond baseline hold 0.503 strata 0.505; delta -0.032
- I6-wavelet 60 ASIA: I6-wavelet: I1-BASE cond baseline hold 0.476 strata 0.460; delta +0.073
- I7-signature 0 POOLED: I7-signature: I1-BASE cond baseline hold 0.509 strata 0.507; delta +0.005
- I7-signature 0 ASIA: I7-signature: I1-BASE cond baseline hold 0.536 strata 0.526; delta -0.005
- I7-signature 0 NY: I7-signature: I1-BASE cond baseline hold 0.522 strata 0.526; delta -0.013
- I7-signature 0 LONDON: I7-signature: I1-BASE cond baseline hold 0.448 strata 0.440; delta +0.034
- I7-signature 15 NY: I7-signature: I1-BASE cond baseline hold 0.499 strata 0.503; delta +0.007
- I7-signature 15 LONDON: I7-signature: I1-BASE cond baseline hold 0.442 strata 0.425; delta +0.071
- I7-signature 20 POOLED: I7-signature: I1-BASE cond baseline hold 0.498 strata 0.490; delta -0.011
- I7-signature 20 NY: I7-signature: I1-BASE cond baseline hold 0.482 strata 0.489; delta -0.040
- I7-signature 30 LONDON: I7-signature: I1-BASE cond baseline hold 0.438 strata 0.444; delta +0.016
- I7-signature 30 NY: I7-signature: I1-BASE cond baseline hold 0.396 strata 0.404; delta -0.017
- I7-signature 45 NY: I7-signature: I1-BASE cond baseline hold 0.467 strata 0.460; delta -0.004
- I7-signature 45 POOLED: I7-signature: I1-BASE cond baseline hold 0.490 strata 0.488; delta +0.032
- I7-signature 5 LONDON: I7-signature: I1-BASE cond baseline hold 0.474 strata 0.464; delta +0.006
- I7-signature 60 LONDON: I7-signature: I1-BASE cond baseline hold 0.538 strata 0.534; delta -0.052
- I7-signature 10 POOLED: I7-signature: I1-BASE cond baseline hold 0.514 strata 0.515; delta -0.001
- I7-signature 10 ASIA: I7-signature: I1-BASE cond baseline hold 0.501 strata 0.490; delta -0.032
- I7-signature 10 NY: I7-signature: I1-BASE cond baseline hold 0.508 strata 0.509; delta -0.008
- I7-signature 10 LONDON: I7-signature: I1-BASE cond baseline hold 0.542 strata 0.541; delta -0.031
- I7-signature 15 POOLED: I7-signature: I1-BASE cond baseline hold 0.453 strata 0.443; delta +0.064
- I7-signature 15 ASIA: I7-signature: I1-BASE cond baseline hold 0.470 strata 0.458; delta +0.062
- I7-signature 20 ASIA: I7-signature: I1-BASE cond baseline hold 0.511 strata 0.491; delta -0.016
- I7-signature 20 LONDON: I7-signature: I1-BASE cond baseline hold 0.523 strata 0.528; delta -0.085
- I7-signature 30 POOLED: I7-signature: I1-BASE cond baseline hold 0.439 strata 0.437; delta +0.070
- I7-signature 30 ASIA: I7-signature: I1-BASE cond baseline hold 0.518 strata 0.510; delta +0.048
- I7-signature 45 ASIA: I7-signature: I1-BASE cond baseline hold 0.536 strata 0.534; delta -0.040
- I7-signature 45 LONDON: I7-signature: I1-BASE cond baseline hold 0.518 strata 0.509; delta -0.028
- I7-signature 5 NY: I7-signature: I1-BASE cond baseline hold 0.507 strata 0.509; delta +0.000
- I7-signature 5 POOLED: I7-signature: I1-BASE cond baseline hold 0.513 strata 0.508; delta -0.008
- I7-signature 5 ASIA: I7-signature: I1-BASE cond baseline hold 0.520 strata 0.519; delta +0.004
- I7-signature 60 NY: I7-signature: I1-BASE cond baseline hold 0.503 strata 0.505; delta -0.050
- I7-signature 60 POOLED: I7-signature: I1-BASE cond baseline hold 0.497 strata 0.492; delta -0.038
- I7-signature 60 ASIA: I7-signature: I1-BASE cond baseline hold 0.476 strata 0.460; delta +0.026
- I2-gp 0 NY: I2-gp: I1-BASE cond baseline hold 0.522 strata 0.526; delta +0.006
- I2-gp 0 POOLED: I2-gp: I1-BASE cond baseline hold 0.509 strata 0.507; delta -0.021
- I2-gp 0 ASIA: I2-gp: I1-BASE cond baseline hold 0.536 strata 0.526; delta -0.051
- I2-gp 0 LONDON: I2-gp: I1-BASE cond baseline hold 0.448 strata 0.440; delta +0.048
- I2-gp 10 POOLED: I2-gp: I1-BASE cond baseline hold 0.514 strata 0.515; delta -0.012
- I2-gp 10 LONDON: I2-gp: I1-BASE cond baseline hold 0.542 strata 0.541; delta -0.035
- I2-gp 10 NY: I2-gp: I1-BASE cond baseline hold 0.508 strata 0.509; delta +0.009
- I2-gp 10 ASIA: I2-gp: I1-BASE cond baseline hold 0.501 strata 0.490; delta +0.036
- I2-gp 15 ASIA: I2-gp: I1-BASE cond baseline hold 0.470 strata 0.458; delta +0.014
- I2-gp 15 LONDON: I2-gp: I1-BASE cond baseline hold 0.442 strata 0.425; delta +0.072
- I2-gp 15 POOLED: I2-gp: I1-BASE cond baseline hold 0.453 strata 0.443; delta +0.086
- I2-gp 15 NY: I2-gp: I1-BASE cond baseline hold 0.499 strata 0.503; delta +0.022
- I2-gp 20 POOLED: I2-gp: I1-BASE cond baseline hold 0.498 strata 0.490; delta +0.017
- I2-gp 20 LONDON: I2-gp: I1-BASE cond baseline hold 0.523 strata 0.528; delta +0.031
- I2-gp 20 ASIA: I2-gp: I1-BASE cond baseline hold 0.511 strata 0.491; delta -0.023
- I2-gp 20 NY: I2-gp: I1-BASE cond baseline hold 0.482 strata 0.489; delta +0.060
- I2-gp 30 LONDON: I2-gp: I1-BASE cond baseline hold 0.438 strata 0.444; delta +0.028
- I2-gp 30 POOLED: I2-gp: I1-BASE cond baseline hold 0.439 strata 0.437; delta +0.054
- I2-gp 30 ASIA: I2-gp: I1-BASE cond baseline hold 0.518 strata 0.510; delta -0.002
- I2-gp 30 NY: I2-gp: I1-BASE cond baseline hold 0.396 strata 0.404; delta +0.046
- I2-gp 45 ASIA: I2-gp: I1-BASE cond baseline hold 0.536 strata 0.534; delta +0.030
- I2-gp 45 POOLED: I2-gp: I1-BASE cond baseline hold 0.490 strata 0.488; delta +0.050
- I2-gp 45 NY: I2-gp: I1-BASE cond baseline hold 0.467 strata 0.460; delta +0.047
- I2-gp 45 LONDON: I2-gp: I1-BASE cond baseline hold 0.518 strata 0.509; delta -0.032
- I2-gp 5 LONDON: I2-gp: I1-BASE cond baseline hold 0.474 strata 0.464; delta +0.044
- I2-gp 5 POOLED: I2-gp: I1-BASE cond baseline hold 0.513 strata 0.508; delta +0.015
- I2-gp 5 ASIA: I2-gp: I1-BASE cond baseline hold 0.520 strata 0.519; delta -0.022
- I2-gp 5 NY: I2-gp: I1-BASE cond baseline hold 0.507 strata 0.509; delta +0.037
- I2-gp 60 LONDON: I2-gp: I1-BASE cond baseline hold 0.538 strata 0.534; delta +0.027
- I2-gp 60 NY: I2-gp: I1-BASE cond baseline hold 0.503 strata 0.505; delta -0.013
- I2-gp 60 POOLED: I2-gp: I1-BASE cond baseline hold 0.497 strata 0.492; delta +0.040
- I2-gp 60 ASIA: I2-gp: I1-BASE cond baseline hold 0.476 strata 0.460; delta +0.039
- I3-interactions 0 POOLED: I3-interactions: I1-BASE cond baseline hold 0.509 strata 0.507; delta -0.001
- I3-interactions 0 LONDON: I3-interactions: I1-BASE cond baseline hold 0.448 strata 0.440; delta +0.041
- I3-interactions 0 NY: I3-interactions: I1-BASE cond baseline hold 0.522 strata 0.526; delta -0.028
- I3-interactions 0 ASIA: I3-interactions: I1-BASE cond baseline hold 0.536 strata 0.526; delta +0.015
- I3-interactions 10 ASIA: I3-interactions: I1-BASE cond baseline hold 0.501 strata 0.490; delta -0.009
- I3-interactions 10 POOLED: I3-interactions: I1-BASE cond baseline hold 0.514 strata 0.515; delta -0.026
- I3-interactions 10 LONDON: I3-interactions: I1-BASE cond baseline hold 0.542 strata 0.541; delta -0.053
- I3-interactions 10 NY: I3-interactions: I1-BASE cond baseline hold 0.508 strata 0.509; delta -0.017
- I3-interactions 15 NY: I3-interactions: I1-BASE cond baseline hold 0.499 strata 0.503; delta -0.019
- I3-interactions 15 POOLED: I3-interactions: I1-BASE cond baseline hold 0.453 strata 0.443; delta +0.050
- I3-interactions 15 ASIA: I3-interactions: I1-BASE cond baseline hold 0.470 strata 0.458; delta +0.030
- I3-interactions 15 LONDON: I3-interactions: I1-BASE cond baseline hold 0.442 strata 0.425; delta +0.101
- I3-interactions 20 NY: I3-interactions: I1-BASE cond baseline hold 0.482 strata 0.489; delta +0.042
- I3-interactions 20 POOLED: I3-interactions: I1-BASE cond baseline hold 0.498 strata 0.490; delta -0.006
- I3-interactions 20 ASIA: I3-interactions: I1-BASE cond baseline hold 0.511 strata 0.491; delta -0.027
- I3-interactions 20 LONDON: I3-interactions: I1-BASE cond baseline hold 0.523 strata 0.528; delta -0.030
- I3-interactions 30 POOLED: I3-interactions: I1-BASE cond baseline hold 0.439 strata 0.437; delta +0.081
- I3-interactions 30 ASIA: I3-interactions: I1-BASE cond baseline hold 0.518 strata 0.510; delta +0.020
- I3-interactions 30 NY: I3-interactions: I1-BASE cond baseline hold 0.396 strata 0.404; delta +0.116
- I3-interactions 30 LONDON: I3-interactions: I1-BASE cond baseline hold 0.438 strata 0.444; delta +0.081
- I3-interactions 45 POOLED: I3-interactions: I1-BASE cond baseline hold 0.490 strata 0.488; delta +0.038
- I3-interactions 45 LONDON: I3-interactions: I1-BASE cond baseline hold 0.518 strata 0.509; delta +0.029
- I3-interactions 45 NY: I3-interactions: I1-BASE cond baseline hold 0.467 strata 0.460; delta +0.055
- I3-interactions 45 ASIA: I3-interactions: I1-BASE cond baseline hold 0.536 strata 0.534; delta -0.008
- I3-interactions 5 ASIA: I3-interactions: I1-BASE cond baseline hold 0.520 strata 0.519; delta -0.032
- I3-interactions 5 POOLED: I3-interactions: I1-BASE cond baseline hold 0.513 strata 0.508; delta -0.029
- I3-interactions 5 LONDON: I3-interactions: I1-BASE cond baseline hold 0.474 strata 0.464; delta +0.026
- I3-interactions 5 NY: I3-interactions: I1-BASE cond baseline hold 0.507 strata 0.509; delta -0.014
- I3-interactions 60 LONDON: I3-interactions: I1-BASE cond baseline hold 0.538 strata 0.534; delta -0.017
- I3-interactions 60 NY: I3-interactions: I1-BASE cond baseline hold 0.503 strata 0.505; delta -0.003
- I3-interactions 60 POOLED: I3-interactions: I1-BASE cond baseline hold 0.497 strata 0.492; delta +0.006
- I3-interactions 60 ASIA: I3-interactions: I1-BASE cond baseline hold 0.476 strata 0.460; delta +0.053
- I4-autoencoder 0 LONDON: I4-autoencoder: I1-BASE cond baseline hold 0.448 strata 0.440; delta +0.058
- I4-autoencoder 0 POOLED: I4-autoencoder: I1-BASE cond baseline hold 0.509 strata 0.507; delta -0.001
- I4-autoencoder 0 ASIA: I4-autoencoder: I1-BASE cond baseline hold 0.536 strata 0.526; delta -0.001
- I4-autoencoder 0 NY: I4-autoencoder: I1-BASE cond baseline hold 0.522 strata 0.526; delta +0.007
- I4-autoencoder 10 POOLED: I4-autoencoder: I1-BASE cond baseline hold 0.514 strata 0.515; delta +0.014
- I4-autoencoder 10 LONDON: I4-autoencoder: I1-BASE cond baseline hold 0.542 strata 0.541; delta -0.013
- I4-autoencoder 10 NY: I4-autoencoder: I1-BASE cond baseline hold 0.508 strata 0.509; delta +0.015
- I4-autoencoder 10 ASIA: I4-autoencoder: I1-BASE cond baseline hold 0.501 strata 0.490; delta -0.003
- I4-autoencoder 15 NY: I4-autoencoder: I1-BASE cond baseline hold 0.499 strata 0.503; delta +0.005
- I4-autoencoder 15 POOLED: I4-autoencoder: I1-BASE cond baseline hold 0.453 strata 0.443; delta +0.002
- I4-autoencoder 15 ASIA: I4-autoencoder: I1-BASE cond baseline hold 0.470 strata 0.458; delta +0.017
- I4-autoencoder 15 LONDON: I4-autoencoder: I1-BASE cond baseline hold 0.442 strata 0.425; delta +0.009
- I4-autoencoder 20 POOLED: I4-autoencoder: I1-BASE cond baseline hold 0.498 strata 0.490; delta +0.003
- I4-autoencoder 20 LONDON: I4-autoencoder: I1-BASE cond baseline hold 0.523 strata 0.528; delta +0.004
- I4-autoencoder 20 NY: I4-autoencoder: I1-BASE cond baseline hold 0.482 strata 0.489; delta +0.022
- I4-autoencoder 20 ASIA: I4-autoencoder: I1-BASE cond baseline hold 0.511 strata 0.491; delta +0.004
- I4-autoencoder 30 ASIA: I4-autoencoder: I1-BASE cond baseline hold 0.518 strata 0.510; delta +0.005
- I4-autoencoder 30 POOLED: I4-autoencoder: I1-BASE cond baseline hold 0.439 strata 0.437; delta -0.001
- I4-autoencoder 30 LONDON: I4-autoencoder: I1-BASE cond baseline hold 0.438 strata 0.444; delta -0.009
- I4-autoencoder 30 NY: I4-autoencoder: I1-BASE cond baseline hold 0.396 strata 0.404; delta +0.006
- I4-autoencoder 45 LONDON: I4-autoencoder: I1-BASE cond baseline hold 0.518 strata 0.509; delta -0.002
- I4-autoencoder 45 ASIA: I4-autoencoder: I1-BASE cond baseline hold 0.536 strata 0.534; delta +0.029
- I4-autoencoder 45 POOLED: I4-autoencoder: I1-BASE cond baseline hold 0.490 strata 0.488; delta +0.022
- I4-autoencoder 45 NY: I4-autoencoder: I1-BASE cond baseline hold 0.467 strata 0.460; delta -0.062
- I4-autoencoder 5 NY: I4-autoencoder: I1-BASE cond baseline hold 0.507 strata 0.509; delta +0.008
- I4-autoencoder 5 POOLED: I4-autoencoder: I1-BASE cond baseline hold 0.513 strata 0.508; delta -0.055
- I4-autoencoder 5 ASIA: I4-autoencoder: I1-BASE cond baseline hold 0.520 strata 0.519; delta -0.069
- I4-autoencoder 5 LONDON: I4-autoencoder: I1-BASE cond baseline hold 0.474 strata 0.464; delta +0.020
- I4-autoencoder 60 POOLED: I4-autoencoder: I1-BASE cond baseline hold 0.497 strata 0.492; delta +0.031
- I4-autoencoder 60 ASIA: I4-autoencoder: I1-BASE cond baseline hold 0.476 strata 0.460; delta +0.048
- I4-autoencoder 60 LONDON: I4-autoencoder: I1-BASE cond baseline hold 0.538 strata 0.534; delta -0.077
- I4-autoencoder 60 NY: I4-autoencoder: I1-BASE cond baseline hold 0.503 strata 0.505; delta -0.030
- I3P-searchnull 0 NY: I3P-searchnull: I1-BASE cond baseline hold 0.522 strata 0.526; delta -0.026
- I3P-searchnull 0 POOLED: I3P-searchnull: I1-BASE cond baseline hold 0.509 strata 0.507; delta -0.029
- I3P-searchnull 0 ASIA: I3P-searchnull: I1-BASE cond baseline hold 0.536 strata 0.526; delta -0.024
- I3P-searchnull 0 LONDON: I3P-searchnull: I1-BASE cond baseline hold 0.448 strata 0.440; delta +0.051
- I3P-searchnull 10 LONDON: I3P-searchnull: I1-BASE cond baseline hold 0.542 strata 0.541; delta -0.021
- I3P-searchnull 10 POOLED: I3P-searchnull: I1-BASE cond baseline hold 0.514 strata 0.515; delta -0.011
- I3P-searchnull 10 ASIA: I3P-searchnull: I1-BASE cond baseline hold 0.501 strata 0.490; delta +0.013
- I3P-searchnull 10 NY: I3P-searchnull: I1-BASE cond baseline hold 0.508 strata 0.509; delta -0.067
- I3P-searchnull 15 POOLED: I3P-searchnull: I1-BASE cond baseline hold 0.453 strata 0.443; delta +0.052
- I3P-searchnull 15 ASIA: I3P-searchnull: I1-BASE cond baseline hold 0.470 strata 0.458; delta +0.003
- I3P-searchnull 15 LONDON: I3P-searchnull: I1-BASE cond baseline hold 0.442 strata 0.425; delta +0.086
- I3P-searchnull 15 NY: I3P-searchnull: I1-BASE cond baseline hold 0.499 strata 0.503; delta +0.014
- I3P-searchnull 20 POOLED: I3P-searchnull: I1-BASE cond baseline hold 0.498 strata 0.490; delta +0.012
- I3P-searchnull 20 NY: I3P-searchnull: I1-BASE cond baseline hold 0.482 strata 0.489; delta +0.002
- I3P-searchnull 20 LONDON: I3P-searchnull: I1-BASE cond baseline hold 0.523 strata 0.528; delta +0.066
- I3P-searchnull 20 ASIA: I3P-searchnull: I1-BASE cond baseline hold 0.511 strata 0.491; delta -0.057
- I3P-searchnull 30 LONDON: I3P-searchnull: I1-BASE cond baseline hold 0.438 strata 0.444; delta +0.020
- I3P-searchnull 30 NY: I3P-searchnull: I1-BASE cond baseline hold 0.396 strata 0.404; delta +0.021
- I3P-searchnull 30 POOLED: I3P-searchnull: I1-BASE cond baseline hold 0.439 strata 0.437; delta -0.011
- I3P-searchnull 30 ASIA: I3P-searchnull: I1-BASE cond baseline hold 0.518 strata 0.510; delta -0.058
- I3P-searchnull 45 NY: I3P-searchnull: I1-BASE cond baseline hold 0.467 strata 0.460; delta -0.001
- I3P-searchnull 45 POOLED: I3P-searchnull: I1-BASE cond baseline hold 0.490 strata 0.488; delta -0.024
- I3P-searchnull 45 ASIA: I3P-searchnull: I1-BASE cond baseline hold 0.536 strata 0.534; delta -0.051
- I3P-searchnull 45 LONDON: I3P-searchnull: I1-BASE cond baseline hold 0.518 strata 0.509; delta -0.067
- I3P-searchnull 5 LONDON: I3P-searchnull: I1-BASE cond baseline hold 0.474 strata 0.464; delta +0.040
- I3P-searchnull 5 POOLED: I3P-searchnull: I1-BASE cond baseline hold 0.513 strata 0.508; delta -0.008
- I3P-searchnull 5 ASIA: I3P-searchnull: I1-BASE cond baseline hold 0.520 strata 0.519; delta -0.023
- I3P-searchnull 5 NY: I3P-searchnull: I1-BASE cond baseline hold 0.507 strata 0.509; delta -0.028
- I3P-searchnull 60 LONDON: I3P-searchnull: I1-BASE cond baseline hold 0.538 strata 0.534; delta -0.071
- I3P-searchnull 60 POOLED: I3P-searchnull: I1-BASE cond baseline hold 0.497 strata 0.492; delta -0.022
- I3P-searchnull 60 ASIA: I3P-searchnull: I1-BASE cond baseline hold 0.476 strata 0.460; delta +0.032
- I3P-searchnull 60 NY: I3P-searchnull: I1-BASE cond baseline hold 0.503 strata 0.505; delta -0.008
- I3-interactions -1 NY: G NY: GBASE hold 0.547; delta -0.014
- I3-interactions -1 NY: stop_vs_target variant of the stop_vs_rest-selected model
- I1-tsfresh -1 NY: G NY: GBASE hold 0.547; delta -0.007
- I1-tsfresh -1 NY: stop_vs_target variant of the stop_vs_rest-selected model
- I2-gp -1 NY: G NY: GBASE hold 0.547; delta -0.012
- I2-gp -1 NY: stop_vs_target variant of the stop_vs_rest-selected model
- I1-tsfresh -1 POOLED: G ST: GBASE hold 0.517; delta -0.002
- I1-tsfresh -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I6-wavelet -1 NY: G NY: GBASE hold 0.547; delta +0.000
- I6-wavelet -1 NY: stop_vs_target variant of the stop_vs_rest-selected model
- I5-rocket -1 NY: G NY: GBASE hold 0.547; delta +0.001
- I5-rocket -1 NY: stop_vs_target variant of the stop_vs_rest-selected model
- I4-autoencoder -1 NY: G NY: GBASE hold 0.547; delta +0.006
- I4-autoencoder -1 NY: stop_vs_target variant of the stop_vs_rest-selected model
- I7-signature -1 NY: G NY: GBASE hold 0.547; delta +0.000
- I7-signature -1 NY: stop_vs_target variant of the stop_vs_rest-selected model
- I3-interactions -1 POOLED: G HM: GBASE hold 0.506; delta +0.014
- I3-interactions -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I1-tsfresh -1 POOLED: G ALL: GBASE hold 0.516; delta +0.004
- I1-tsfresh -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I3-interactions -1 POOLED: G ST: GBASE hold 0.517; delta +0.010
- I3-interactions -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I3-interactions -1 POOLED: G ALL: GBASE hold 0.516; delta +0.008
- I3-interactions -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I1-tsfresh -1 POOLED: G HM: GBASE hold 0.506; delta +0.009
- I1-tsfresh -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I2-gp -1 POOLED: G ST: GBASE hold 0.517; delta -0.002
- I2-gp -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I2-gp -1 POOLED: G ALL: GBASE hold 0.516; delta -0.009
- I2-gp -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I1-tsfresh -1 LONDON: G LONDON: GBASE hold 0.484; delta +0.038
- I1-tsfresh -1 LONDON: stop_vs_target variant of the stop_vs_rest-selected model
- I2-gp -1 POOLED: G HM: GBASE hold 0.506; delta -0.010
- I2-gp -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I6-wavelet -1 POOLED: G HM: GBASE hold 0.506; delta +0.007
- I6-wavelet -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I7-signature -1 POOLED: G HM: GBASE hold 0.506; delta +0.007
- I7-signature -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I5-rocket -1 POOLED: G HM: GBASE hold 0.506; delta +0.001
- I5-rocket -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I4-autoencoder -1 POOLED: G HM: GBASE hold 0.506; delta -0.002
- I4-autoencoder -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I7-signature -1 POOLED: G ST: GBASE hold 0.517; delta -0.013
- I7-signature -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I5-rocket -1 POOLED: G ST: GBASE hold 0.517; delta +0.000
- I5-rocket -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I1-tsfresh -1 ASIA: G ASIA: GBASE hold 0.506; delta -0.007
- I1-tsfresh -1 ASIA: stop_vs_target variant of the stop_vs_rest-selected model
- I5-rocket -1 POOLED: G ALL: GBASE hold 0.516; delta -0.007
- I5-rocket -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I6-wavelet -1 POOLED: G ALL: GBASE hold 0.516; delta -0.000
- I6-wavelet -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I4-autoencoder -1 POOLED: G ALL: GBASE hold 0.516; delta +0.004
- I4-autoencoder -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I7-signature -1 POOLED: G ALL: GBASE hold 0.516; delta +0.000
- I7-signature -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I4-autoencoder -1 POOLED: G ST: GBASE hold 0.517; delta -0.000
- I4-autoencoder -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I7-signature -1 ASIA: G ASIA: GBASE hold 0.506; delta +0.024
- I7-signature -1 ASIA: stop_vs_target variant of the stop_vs_rest-selected model
- I6-wavelet -1 POOLED: G ST: GBASE hold 0.517; delta +0.001
- I6-wavelet -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I3P-searchnull -1 POOLED: G HM: GBASE hold 0.506; delta -0.010
- I3P-searchnull -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I3P-searchnull -1 NY: G NY: GBASE hold 0.547; delta -0.060
- I3P-searchnull -1 NY: stop_vs_target variant of the stop_vs_rest-selected model
- I5-rocket -1 ASIA: G ASIA: GBASE hold 0.506; delta +0.014
- I5-rocket -1 ASIA: stop_vs_target variant of the stop_vs_rest-selected model
- I3-interactions -1 LONDON: G LONDON: GBASE hold 0.484; delta +0.028
- I3-interactions -1 LONDON: stop_vs_target variant of the stop_vs_rest-selected model
- I6-wavelet -1 ASIA: G ASIA: GBASE hold 0.506; delta -0.002
- I6-wavelet -1 ASIA: stop_vs_target variant of the stop_vs_rest-selected model
- I3P-searchnull -1 LONDON: G LONDON: GBASE hold 0.484; delta +0.050
- I3P-searchnull -1 LONDON: stop_vs_target variant of the stop_vs_rest-selected model
- I7-signature -1 LONDON: G LONDON: GBASE hold 0.484; delta -0.000
- I7-signature -1 LONDON: stop_vs_target variant of the stop_vs_rest-selected model
- I3P-searchnull -1 ASIA: G ASIA: GBASE hold 0.506; delta -0.012
- I3P-searchnull -1 ASIA: stop_vs_target variant of the stop_vs_rest-selected model
- I5-rocket -1 LONDON: G LONDON: GBASE hold 0.484; delta +0.006
- I5-rocket -1 LONDON: stop_vs_target variant of the stop_vs_rest-selected model
- I3P-searchnull -1 POOLED: G ALL: GBASE hold 0.516; delta -0.024
- I3P-searchnull -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I4-autoencoder -1 ASIA: G ASIA: GBASE hold 0.506; delta -0.010
- I4-autoencoder -1 ASIA: stop_vs_target variant of the stop_vs_rest-selected model
- I3-interactions -1 ASIA: G ASIA: GBASE hold 0.506; delta +0.017
- I3-interactions -1 ASIA: stop_vs_target variant of the stop_vs_rest-selected model
- I2-gp -1 LONDON: G LONDON: GBASE hold 0.484; delta +0.002
- I2-gp -1 LONDON: stop_vs_target variant of the stop_vs_rest-selected model
- I2-gp -1 ASIA: G ASIA: GBASE hold 0.506; delta -0.010
- I2-gp -1 ASIA: stop_vs_target variant of the stop_vs_rest-selected model
- I4-autoencoder -1 LONDON: G LONDON: GBASE hold 0.484; delta +0.004
- I4-autoencoder -1 LONDON: stop_vs_target variant of the stop_vs_rest-selected model
- I6-wavelet -1 LONDON: G LONDON: GBASE hold 0.484; delta +0.030
- I6-wavelet -1 LONDON: stop_vs_target variant of the stop_vs_rest-selected model
- I3P-searchnull -1 POOLED: G ST: GBASE hold 0.517; delta -0.028
- I3P-searchnull -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
