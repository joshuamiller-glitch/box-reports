# PRED ROUND 18 - block X5 round 2 - X21-cost-aware-target+X24-late-info-ensemble+X25-noise-robust-selection

Best HOLDOUT F-R AUC: +15 POOLED 0.516 [0.47,0.56] | ASIA 0.546 [0.49,0.61] | LONDON 0.499 [0.42,0.58] | NY 0.542 [0.45,0.62]
Best HOLDOUT F-R AUC: +30 POOLED 0.529 [0.49,0.57] | ASIA 0.552 [0.49,0.62] | LONDON 0.515 [0.43,0.60] | NY 0.554 [0.46,0.65]
Best G HOLDOUT AUC: 0.625 [0.56,0.70]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 2e9780ba85136b1a0dc55700eedf318e445181ff0d70acadaf1de140b4d0556d ; trials added 270 ; truncation audit {'decisions': 0, 'mismatches': 0, 'fixed_and_rerun': False, 'note': 'X21/X25 use R0 G matrix (FAILPRED R9); X24 inputs are FAILPRED OOS predictions'} ; holdout scored True ; feature store ['l2vast/pred/store/X22_geo_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X25-noise-robust-selection | sig | LONDON/ST | X25R:stack | 0.629 [0.59,0.67] | 0.625 [0.56,0.70] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | NY/ST | X25R:stack | 0.586 [0.54,0.64] | 0.625 [0.56,0.69] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | NY | X25R:stack | 0.583 [0.54,0.62] | 0.608 [0.55,0.66] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | LONDON | X25R:stack | 0.607 [0.57,0.64] | 0.603 [0.56,0.65] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | LONDON/HM | X25R:stack | 0.586 [0.54,0.63] | 0.587 [0.53,0.64] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | NY/HM | X25R:stack | 0.577 [0.53,0.63] | 0.585 [0.51,0.67] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +60 | NY | S2c | 0.521 [0.44,0.60] | 0.583 [0.50,0.67] | - | 0.602 | 0.848 | - | - | - | - | - | stack | locked label (reference only) |
| X25-noise-robust-selection | sig | POOLED/ST | X25R:stack | 0.579 [0.56,0.60] | 0.583 [0.55,0.62] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | POOLED | X25R:stack | 0.574 [0.55,0.59] | 0.580 [0.55,0.61] | - | - | - | N | 277 | -35290 | - | 2/5 |  | locked label (reference only) |
| X25-noise-robust-selection | sig | POOLED/HM | X25R:stack | 0.569 [0.54,0.59] | 0.580 [0.54,0.62] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | ASIA/HM | X25R:stack | 0.558 [0.52,0.59] | 0.576 [0.52,0.63] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +45 | NY | S2c | 0.516 [0.44,0.60] | 0.562 [0.45,0.66] | - | 0.580 | 0.815 | - | - | - | - | - | stack | locked label (reference only) |
| X25-noise-robust-selection | sig | ASIA | X25R:stack | 0.545 [0.51,0.58] | 0.557 [0.51,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +20 | NY | S2c | 0.526 [0.45,0.61] | 0.556 [0.46,0.64] | - | 0.556 | 0.821 | - | - | - | - | - | stack | locked label (reference only) |
| X21-cost-aware-target | sig | LONDON/HM | X21C2:stack | 0.511 [0.47,0.55] | 0.555 [0.49,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +30 | NY | S2c | 0.521 [0.44,0.60] | 0.554 [0.46,0.65] | - | 0.580 | 0.813 | - | - | - | - | - | stack | locked label (reference only) |
| X24-late-info-ensemble | +30 | ASIA | S2c | 0.577 [0.53,0.63] | 0.552 [0.49,0.62] | - | 0.531 | 0.539 | - | - | - | - | - | stack | locked label (reference only) |
| X21-cost-aware-target | sig | LONDON/HM | X21C2:stack | 0.506 [0.46,0.55] | 0.550 [0.48,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +15 | ASIA | S2c | 0.568 [0.52,0.62] | 0.546 [0.49,0.61] | - | 0.532 | 0.547 | - | - | - | - | - | stack | locked label (reference only) |
| X24-late-info-ensemble | +20 | ASIA | S2c | 0.567 [0.52,0.61] | 0.545 [0.49,0.60] | - | 0.531 | 0.542 | - | - | - | - | - | stack | locked label (reference only) |
| X21-cost-aware-target | sig | NY/ST | X21C2:stack | 0.509 [0.46,0.56] | 0.544 [0.48,0.62] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +45 | ASIA | S2c | 0.556 [0.50,0.61] | 0.543 [0.48,0.61] | - | 0.523 | 0.527 | - | - | - | - | - | stack | locked label (reference only) |
| X24-late-info-ensemble | +15 | NY | S2c | 0.513 [0.44,0.58] | 0.542 [0.45,0.62] | - | 0.538 | 0.796 | - | - | - | - | - | stack | locked label (reference only) |
| X25-noise-robust-selection | sig | ASIA/ST | X25R:stack | 0.535 [0.50,0.57] | 0.541 [0.49,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | LONDON | X21C2:stack | 0.490 [0.45,0.53] | 0.539 [0.49,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | ASIA/HM | X21C2:stack | 0.517 [0.48,0.55] | 0.537 [0.48,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | POOLED/HM | X21C2:stack | 0.528 [0.50,0.55] | 0.535 [0.50,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +45 | POOLED | S2c | 0.514 [0.48,0.55] | 0.535 [0.49,0.58] | - | 0.526 | 0.702 | - | - | - | - | - | stack | locked label (reference only) |
| X21-cost-aware-target | sig | LONDON | X21C2:stack | 0.486 [0.45,0.52] | 0.534 [0.48,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +10 | ASIA | S2c | 0.562 [0.51,0.61] | 0.534 [0.47,0.59] | - | 0.510 | 0.525 | - | - | - | - | - | stack | locked label (reference only) |
| X21-cost-aware-target | sig | POOLED/HM | X21C2:stack | 0.522 [0.50,0.55] | 0.534 [0.49,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +45 | LONDON | S2c | 0.489 [0.43,0.55] | 0.533 [0.45,0.63] | - | 0.539 | 0.689 | - | - | - | - | - | stack | locked label (reference only) |
| X21-cost-aware-target | sig | NY/HM | X21C2:stack | 0.569 [0.51,0.63] | 0.533 [0.46,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | ASIA/HM | X21C2:stack | 0.520 [0.48,0.56] | 0.532 [0.47,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +60 | POOLED | S2c | 0.509 [0.48,0.54] | 0.531 [0.49,0.57] | - | 0.517 | 0.707 | - | - | - | - | - | stack | locked label (reference only) |
| X24-late-info-ensemble | +30 | POOLED | S2c | 0.514 [0.49,0.55] | 0.529 [0.49,0.57] | - | 0.517 | 0.700 | - | 631 | 0 | - | 1/5 | stack | locked label (reference only) |
| X21-cost-aware-target | sig | POOLED | X21C2:stack | 0.507 [0.49,0.53] | 0.529 [0.50,0.56] | - | - | - | N | 4682 | 114766 | - | 1/5 |  | locked label (reference only) |
| X24-late-info-ensemble | +10 | NY | S2c | 0.498 [0.43,0.57] | 0.528 [0.45,0.61] | - | 0.574 | 0.755 | - | - | - | - | - | stack | locked label (reference only) |
| X21-cost-aware-target | sig | NY | X21C2:stack | 0.529 [0.49,0.57] | 0.527 [0.47,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | ASIA | X21C2:stack | 0.509 [0.48,0.54] | 0.527 [0.48,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | NY | X21C2:stack | 0.534 [0.50,0.57] | 0.526 [0.47,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | POOLED | X21C2:stack | 0.510 [0.49,0.53] | 0.526 [0.50,0.55] | - | - | - | N | 4682 | 114766 | - | 1/5 |  | locked label (reference only) |
| X24-late-info-ensemble | +60 | LONDON | S2c | 0.483 [0.43,0.54] | 0.525 [0.45,0.61] | - | 0.529 | 0.692 | - | - | - | - | - | stack | locked label (reference only) |
| X24-late-info-ensemble | +60 | ASIA | S2c | 0.533 [0.48,0.59] | 0.525 [0.46,0.58] | - | 0.490 | 0.505 | - | - | - | - | - | stack | locked label (reference only) |
| X21-cost-aware-target | sig | POOLED/ST | X21C2:stack | 0.493 [0.47,0.52] | 0.523 [0.49,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | ASIA | X21C2:stack | 0.510 [0.48,0.54] | 0.523 [0.48,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | NY/ST | X21C2:stack | 0.507 [0.45,0.56] | 0.521 [0.45,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | LONDON/ST | X21C2:stack | 0.470 [0.43,0.52] | 0.520 [0.46,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | ASIA/ST | X21C2:stack | 0.503 [0.47,0.54] | 0.518 [0.47,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +20 | POOLED | S2c | 0.507 [0.48,0.54] | 0.518 [0.47,0.56] | - | 0.504 | 0.700 | - | 258 | 0 | - | 1/5 | stack | locked label (reference only) |
| X21-cost-aware-target | sig | POOLED/ST | X21C2:stack | 0.493 [0.47,0.52] | 0.516 [0.48,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | LONDON/ST | X21C2:stack | 0.466 [0.42,0.51] | 0.516 [0.45,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +15 | POOLED | S2c | 0.509 [0.48,0.54] | 0.516 [0.47,0.56] | - | 0.501 | 0.694 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| X24-late-info-ensemble | +30 | LONDON | S2c | 0.476 [0.42,0.54] | 0.515 [0.43,0.60] | - | 0.504 | 0.685 | - | - | - | - | - | stack | locked label (reference only) |
| X21-cost-aware-target | sig | ASIA/ST | X21C2:stack | 0.502 [0.47,0.54] | 0.514 [0.47,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X21-cost-aware-target | sig | NY/HM | X21C2:stack | 0.554 [0.50,0.61] | 0.508 [0.44,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +10 | LONDON | S2c | 0.490 [0.44,0.55] | 0.505 [0.43,0.58] | - | 0.487 | 0.664 | - | - | - | - | - | stack | locked label (reference only) |
| X25-noise-robust-selection | sig | NY/ST | X25A:stack | 0.522 [0.46,0.58] | 0.505 [0.43,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | ASIA/ST | X25A:stack | 0.492 [0.46,0.53] | 0.502 [0.46,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +10 | POOLED | S2c | 0.502 [0.47,0.53] | 0.500 [0.46,0.54] | - | 0.489 | 0.668 | - | 1140 | 0 | - | 1/5 | stack | locked label (reference only) |
| X25-noise-robust-selection | sig | LONDON/HM | X25A:stack | 0.471 [0.42,0.52] | 0.500 [0.43,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X24-late-info-ensemble | +15 | LONDON | S2c | 0.481 [0.42,0.54] | 0.499 [0.42,0.58] | - | 0.482 | 0.678 | - | - | - | - | - | stack | locked label (reference only) |
| X24-late-info-ensemble | +20 | LONDON | S2c | 0.475 [0.41,0.53] | 0.497 [0.42,0.58] | - | 0.475 | 0.682 | - | - | - | - | - | stack | locked label (reference only) |
| X25-noise-robust-selection | sig | POOLED/ST | X25A:stack | 0.490 [0.47,0.51] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | ASIA | X25A:stack | 0.496 [0.46,0.53] | 0.485 [0.44,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | POOLED | X25A:stack | 0.487 [0.47,0.51] | 0.478 [0.45,0.51] | - | - | - | N | 940 | 19381 | - | 2/5 |  | locked label (reference only) |
| X25-noise-robust-selection | sig | LONDON | X25A:stack | 0.466 [0.43,0.51] | 0.478 [0.42,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | NY | X25A:stack | 0.497 [0.46,0.54] | 0.469 [0.41,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | POOLED/HM | X25A:stack | 0.484 [0.46,0.51] | 0.468 [0.43,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | ASIA/HM | X25A:stack | 0.501 [0.46,0.54] | 0.465 [0.41,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | LONDON/ST | X25A:stack | 0.461 [0.41,0.51] | 0.455 [0.38,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X25-noise-robust-selection | sig | NY/HM | X25A:stack | 0.466 [0.41,0.51] | 0.422 [0.34,0.50] | - | - | - | N | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- X21-cost-aware-target -1 POOLED: c2 label (pts<2), scored vs stop_vs_target; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 ASIA: c2 label (pts<2), scored vs stop_vs_target; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 LONDON: c2 label (pts<2), scored vs stop_vs_target; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 NY: c2 label (pts<2), scored vs stop_vs_target; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 POOLED: c2 label (pts<2), scored vs stop_vs_target; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 ASIA: c2 label (pts<2), scored vs stop_vs_target; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 LONDON: c2 label (pts<2), scored vs stop_vs_target; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 NY: c2 label (pts<2), scored vs stop_vs_target; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 POOLED: c2 label (pts<2), scored vs stop_vs_target; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 ASIA: c2 label (pts<2), scored vs stop_vs_target; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 LONDON: c2 label (pts<2), scored vs stop_vs_target; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 NY: c2 label (pts<2), scored vs stop_vs_target; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 POOLED: c2 label (pts<2), scored vs stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 ASIA: c2 label (pts<2), scored vs stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 LONDON: c2 label (pts<2), scored vs stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 NY: c2 label (pts<2), scored vs stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 POOLED: c2 label (pts<2), scored vs stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 ASIA: c2 label (pts<2), scored vs stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 LONDON: c2 label (pts<2), scored vs stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 NY: c2 label (pts<2), scored vs stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 POOLED: c2 label (pts<2), scored vs stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 ASIA: c2 label (pts<2), scored vs stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 LONDON: c2 label (pts<2), scored vs stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X21-cost-aware-target -1 NY: c2 label (pts<2), scored vs stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 POOLED: stability tau .8 stop_vs_target; stable set empty after fold 6; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 ASIA: stability tau .8 stop_vs_target; stable set empty after fold 6; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 LONDON: stability tau .8 stop_vs_target; stable set empty after fold 6; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 NY: stability tau .8 stop_vs_target; stable set empty after fold 6; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 POOLED: stability tau .8 stop_vs_target; stable set empty after fold 6; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 ASIA: stability tau .8 stop_vs_target; stable set empty after fold 6; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 LONDON: stability tau .8 stop_vs_target; stable set empty after fold 6; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 NY: stability tau .8 stop_vs_target; stable set empty after fold 6; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 POOLED: stability tau .8 stop_vs_target; stable set empty after fold 6; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 ASIA: stability tau .8 stop_vs_target; stable set empty after fold 6; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 LONDON: stability tau .8 stop_vs_target; stable set empty after fold 6; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 NY: stability tau .8 stop_vs_target; stable set empty after fold 6; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 POOLED: stability tau .8 stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 ASIA: stability tau .8 stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 LONDON: stability tau .8 stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 NY: stability tau .8 stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 POOLED: stability tau .8 stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 ASIA: stability tau .8 stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 LONDON: stability tau .8 stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 NY: stability tau .8 stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 POOLED: stability tau .8 stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 ASIA: stability tau .8 stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 LONDON: stability tau .8 stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X25-noise-robust-selection -1 NY: stability tau .8 stop_vs_rest; holdout AUC within 0.03 of 0.5, below R0 same-label baseline+0.02; dead
- X24-late-info-ensemble 10 POOLED: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 10 ASIA: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 10 LONDON: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 10 NY: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 15 POOLED: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 15 ASIA: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 15 LONDON: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 15 NY: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 20 POOLED: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 20 ASIA: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 20 LONDON: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 20 NY: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 30 POOLED: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 30 ASIA: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 30 LONDON: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 30 NY: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 45 POOLED: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 45 ASIA: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 45 LONDON: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 45 NY: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 60 POOLED: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 60 ASIA: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 60 LONDON: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
- X24-late-info-ensemble 60 NY: stage-2 mean-logit ensemble adds nothing: conditional holdout AUC ~0.51-0.55, equal to stage-1; dead
