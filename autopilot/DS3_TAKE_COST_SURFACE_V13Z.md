# TAKE-RULE COST MODEL AND BREAK-EVEN SURFACE ON V13Z (BASE-4, 2026-11-02T12:04Z)

Episodes lookup: DS3_ZONES_EPISODES_V13Y.md.

## 1. Cost model behind the basis-N take-line result
| item | engine value | evidence |
|---|---|---|
| baseline TARGET exit (basis N) | no cost (limit fills at nominal; engine o0 = pts_lib - 0.242) | DS3_MISSED_FINAL / DS3_BASIS_LIVE: touched targets filled at nominal 11 of 11 (95% lower bound 0.72), +0.01 pt, n = 17 (LIVE_RECON); NOT published: the fill rate of targets the path touched |
| baseline STOP exit | 1.01 pt (join fills at the stop in the research path) | LIVE_CAL_SUMMARY: stop-class exits 2.45 pt worse than nominal live (n = 21, SE ~0.75; join 0.52 better, fallback 4.46 worse, fallback share 0.57); LIVE-P9 basis charges 2.45 instead of 1.01 |
| early TAKE exit (market) | 0.995 pt (BASE-3 market cost, `MKT`) | market-class exits live: 0.80 +/- 0.22 pt vs path (LossExit +0.80, fallback +0.86), DS3_BASIS_LIVE: market-class exits kept at M ~1.0 pt; no profit-take-specific live number |
| TIGHTEN breach exit | 1.01 pt (`STOPC`) | same stop-class evidence |
| TH-L2 loss cut | exit-price difference vs the original exit, market cost ~1 pt; no fill credit | LossExit +0.80 live |
| target-fill 'correction' of basis M | fill_cost_pts 1.4 / 1.5 / 4.2 / 4.3 (mean 3.39 on target rows) charged to the baseline target exits on M ONLY | research-path measurement; contradicted by live (targets fill at nominal) |
Under V13Z (nfix) an early take on a would-be target trade earns exactly (open profit at the exit second - 0.995) - 0.242 against a baseline of pts_lib - 0.242: the early exit gives up the rest of the move to the target and pays the market cost, with no fill credit. Stress parameters (V13Z options): `xcost` = early-exit cost in pts (default 0.995; applied to every take / tighten), `tshort` = target-fill shortfall in pts per lot charged to EVERY baseline target exit that is not exited early (default 0 = basis N; 3.4 ~ basis M mean). The shortfall also hits the lines-off arm, so the comparison is like for like.

## 2. Break-even surface (1-s grid, V13Z, lock frames separately)
Cell = maxDD cut (positive = shallower) / d mean $k/wk vs lines OFF at the SAME target shortfall. PAYS = cut > 0 AND d mean >= 0; CUT = cut > 0 but mean < 0; MEAN = mean >= 0 only; NO = neither.

### LOCK NONE (headline) - gated five lines - F9
| early-exit cost (pts) | target shortfall 0.0 | target shortfall 1.0 | target shortfall 2.0 | target shortfall 3.4 |
|---|---|---|---|---|
| xcost 0.0 | NO -7% / -17.5 | CUT +7% / -13.8 | CUT +24% / -11.0 | CUT +28% / -7.6 |
| xcost 0.5 | NO -22% / -19.8 | NO -10% / -16.1 | CUT +13% / -13.2 | CUT +19% / -9.7 |
| xcost 1.0 | NO -32% / -21.7 | NO -17% / -18.0 | CUT +6% / -15.1 | CUT +13% / -11.6 |
| xcost 2.0 | NO -55% / -25.6 | NO -34% / -21.9 | NO -7% / -18.7 | CUT +2% / -15.6 |
| xcost 3.0 | NO -83% / -29.6 | NO -58% / -25.8 | NO -27% / -22.7 | NO -16% / -19.5 |

### LOCK NONE (headline) - gated five lines - L6M
| early-exit cost (pts) | target shortfall 0.0 | target shortfall 1.0 | target shortfall 2.0 | target shortfall 3.4 |
|---|---|---|---|---|
| xcost 0.0 | NO -7% / -15.9 | CUT +7% / -11.8 | CUT +24% / -8.9 | CUT +28% / -5.7 |
| xcost 0.5 | NO -22% / -18.2 | NO -10% / -14.2 | CUT +13% / -11.2 | CUT +19% / -7.8 |
| xcost 1.0 | NO -32% / -20.1 | NO -17% / -16.0 | CUT +6% / -13.0 | CUT +13% / -9.7 |
| xcost 2.0 | NO -55% / -24.1 | NO -34% / -19.9 | NO -7% / -16.5 | CUT +2% / -13.6 |
| xcost 3.0 | NO -83% / -28.1 | NO -58% / -23.8 | NO -27% / -20.5 | NO -16% / -17.6 |

### LOCK NONE (headline) - gated five lines - PRE
| early-exit cost (pts) | target shortfall 0.0 | target shortfall 1.0 | target shortfall 2.0 | target shortfall 3.4 |
|---|---|---|---|---|
| xcost 0.0 | NO -6% / -8.8 | NO -31% / -7.6 | NO -34% / -5.9 | NO -48% / -3.8 |
| xcost 0.5 | NO -7% / -9.7 | NO -31% / -8.5 | NO -35% / -6.8 | NO -59% / -4.8 |
| xcost 1.0 | NO -35% / -11.2 | NO -48% / -9.6 | NO -58% / -8.0 | NO -80% / -5.9 |
| xcost 2.0 | NO -89% / -13.5 | NO -102% / -12.0 | NO -117% / -10.4 | NO -131% / -8.2 |
| xcost 3.0 | NO -139% / -16.1 | NO -153% / -14.5 | NO -168% / -13.0 | NO -188% / -10.9 |

### LOCK NONE (headline) - plain 0.70 take - F9
| early-exit cost (pts) | target shortfall 0.0 | target shortfall 1.0 | target shortfall 2.0 | target shortfall 3.4 |
|---|---|---|---|---|
| xcost 0.0 | CUT +15% / -5.2 | CUT +27% / -0.8 | PAYS +43% / +2.6 | PAYS +49% / +7.1 |
| xcost 0.5 | CUT +7% / -7.6 | CUT +20% / -3.2 | PAYS +38% / +0.6 | PAYS +45% / +4.8 |
| xcost 1.0 | CUT +2% / -9.0 | CUT +16% / -4.6 | CUT +35% / -0.9 | PAYS +42% / +3.4 |
| xcost 2.0 | NO -13% / -12.9 | CUT +3% / -8.3 | CUT +25% / -4.8 | CUT +33% / -0.5 |
| xcost 3.0 | NO -32% / -16.9 | NO -13% / -12.6 | CUT +12% / -9.0 | CUT +21% / -4.7 |

### LOCK NONE (headline) - plain 0.70 take - L6M
| early-exit cost (pts) | target shortfall 0.0 | target shortfall 1.0 | target shortfall 2.0 | target shortfall 3.4 |
|---|---|---|---|---|
| xcost 0.0 | CUT +15% / -5.8 | CUT +27% / -0.9 | PAYS +43% / +2.8 | PAYS +49% / +6.8 |
| xcost 0.5 | CUT +7% / -7.9 | CUT +20% / -3.0 | PAYS +38% / +0.7 | PAYS +45% / +4.7 |
| xcost 1.0 | CUT +2% / -9.2 | CUT +16% / -4.4 | CUT +35% / -0.6 | PAYS +42% / +3.4 |
| xcost 2.0 | NO -13% / -12.9 | CUT +3% / -8.0 | CUT +25% / -4.3 | CUT +33% / -0.3 |
| xcost 3.0 | NO -32% / -17.1 | NO -13% / -12.3 | CUT +12% / -8.5 | CUT +21% / -4.6 |

### LOCK NONE (headline) - plain 0.70 take - PRE
| early-exit cost (pts) | target shortfall 0.0 | target shortfall 1.0 | target shortfall 2.0 | target shortfall 3.4 |
|---|---|---|---|---|
| xcost 0.0 | CUT +28% / -3.3 | CUT +29% / -1.3 | PAYS +31% / +0.9 | PAYS +34% / +3.9 |
| xcost 0.5 | CUT +25% / -4.5 | CUT +27% / -2.5 | CUT +28% / -0.3 | PAYS +31% / +2.7 |
| xcost 1.0 | CUT +12% / -5.9 | CUT +14% / -3.9 | CUT +15% / -1.7 | PAYS +19% / +1.3 |
| xcost 2.0 | CUT +3% / -8.3 | CUT +4% / -6.3 | CUT +5% / -4.0 | CUT +8% / -1.1 |
| xcost 3.0 | NO -18% / -10.6 | NO -17% / -8.6 | NO -16% / -6.4 | NO -13% / -3.2 |

### 12R - gated five lines - F9
| early-exit cost (pts) | target shortfall 0.0 | target shortfall 1.0 | target shortfall 2.0 | target shortfall 3.4 |
|---|---|---|---|---|
| xcost 0.0 | CUT +7% / -13.1 | CUT +13% / -8.4 | CUT +17% / -7.7 | CUT +17% / -5.5 |
| xcost 0.5 | CUT +2% / -14.6 | CUT +13% / -10.1 | CUT +17% / -9.4 | CUT +20% / -7.4 |
| xcost 1.0 | CUT +3% / -16.3 | CUT +11% / -11.1 | CUT +15% / -10.3 | CUT +17% / -8.3 |
| xcost 2.0 | NO -2% / -19.9 | CUT +5% / -15.1 | CUT +10% / -13.9 | CUT +16% / -12.0 |
| xcost 3.0 | NO -3% / -21.2 | CUT +5% / -16.3 | CUT +10% / -15.1 | CUT +12% / -14.4 |

### 12R - gated five lines - L6M
| early-exit cost (pts) | target shortfall 0.0 | target shortfall 1.0 | target shortfall 2.0 | target shortfall 3.4 |
|---|---|---|---|---|
| xcost 0.0 | CUT +7% / -10.6 | CUT +13% / -7.5 | CUT +17% / -6.5 | CUT +17% / -4.7 |
| xcost 0.5 | CUT +2% / -12.2 | CUT +13% / -8.7 | CUT +17% / -7.8 | CUT +20% / -5.7 |
| xcost 1.0 | CUT +3% / -13.3 | CUT +11% / -10.0 | CUT +15% / -8.9 | CUT +17% / -7.0 |
| xcost 2.0 | NO -2% / -18.1 | CUT +5% / -14.9 | CUT +10% / -13.3 | CUT +16% / -11.4 |
| xcost 3.0 | NO -3% / -20.0 | CUT +5% / -16.7 | CUT +10% / -15.2 | CUT +12% / -15.2 |

### 12R - gated five lines - PRE
| early-exit cost (pts) | target shortfall 0.0 | target shortfall 1.0 | target shortfall 2.0 | target shortfall 3.4 |
|---|---|---|---|---|
| xcost 0.0 | NO -175% / -6.6 | NO -148% / -5.5 | NO -78% / -3.7 | NO -30% / -1.8 |
| xcost 0.5 | NO -168% / -6.8 | NO -149% / -5.9 | NO -86% / -4.2 | NO -35% / -2.4 |
| xcost 1.0 | NO -167% / -7.2 | NO -159% / -6.5 | NO -94% / -4.9 | NO -41% / -3.0 |
| xcost 2.0 | NO -188% / -9.3 | NO -206% / -9.0 | NO -129% / -7.4 | NO -61% / -5.3 |
| xcost 3.0 | NO -242% / -10.9 | NO -230% / -10.2 | NO -145% / -8.4 | NO -102% / -7.3 |

### 12R - plain 0.70 take - F9
| early-exit cost (pts) | target shortfall 0.0 | target shortfall 1.0 | target shortfall 2.0 | target shortfall 3.4 |
|---|---|---|---|---|
| xcost 0.0 | CUT +19% / -2.0 | PAYS +25% / +3.2 | PAYS +30% / +4.3 | PAYS +33% / +6.8 |
| xcost 0.5 | CUT +17% / -5.9 | CUT +24% / -0.6 | PAYS +28% / +0.5 | PAYS +31% / +3.0 |
| xcost 1.0 | CUT +15% / -6.8 | CUT +22% / -1.5 | CUT +27% / -0.3 | PAYS +29% / +2.0 |
| xcost 2.0 | CUT +3% / -10.3 | CUT +10% / -5.0 | CUT +16% / -3.8 | CUT +18% / -1.4 |
| xcost 3.0 | NO -6% / -13.3 | CUT +2% / -9.4 | CUT +8% / -8.2 | CUT +17% / -5.5 |

### 12R - plain 0.70 take - L6M
| early-exit cost (pts) | target shortfall 0.0 | target shortfall 1.0 | target shortfall 2.0 | target shortfall 3.4 |
|---|---|---|---|---|
| xcost 0.0 | CUT +19% / -4.0 | CUT +25% / -0.2 | PAYS +30% / +1.3 | PAYS +33% / +3.7 |
| xcost 0.5 | CUT +17% / -6.6 | CUT +24% / -2.8 | CUT +28% / -1.2 | PAYS +31% / +1.1 |
| xcost 1.0 | CUT +15% / -7.2 | CUT +22% / -3.5 | CUT +27% / -1.9 | PAYS +29% / +0.4 |
| xcost 2.0 | CUT +3% / -10.0 | CUT +10% / -6.3 | CUT +16% / -4.7 | CUT +18% / -2.3 |
| xcost 3.0 | NO -6% / -12.9 | CUT +2% / -9.2 | CUT +8% / -7.6 | CUT +17% / -4.9 |

### 12R - plain 0.70 take - PRE
| early-exit cost (pts) | target shortfall 0.0 | target shortfall 1.0 | target shortfall 2.0 | target shortfall 3.4 |
|---|---|---|---|---|
| xcost 0.0 | NO -52% / -0.7 | MEAN -45% / +0.1 | MEAN -7% / +2.0 | PAYS +26% / +4.3 |
| xcost 0.5 | NO -59% / -1.2 | NO -52% / -0.4 | MEAN -11% / +1.5 | PAYS +23% / +3.7 |
| xcost 1.0 | NO -74% / -2.1 | NO -66% / -1.3 | MEAN -23% / +0.6 | PAYS +14% / +2.9 |
| xcost 2.0 | NO -89% / -3.6 | NO -81% / -2.8 | NO -33% / -1.0 | PAYS +7% / +1.3 |
| xcost 3.0 | NO -115% / -6.0 | NO -106% / -5.2 | NO -53% / -3.3 | NO -8% / -0.8 |

### Break-even target shortfall (d mean = 0) by interpolation; d mean at shortfall 0 / 1 / 2 / 3.4
| lock | rule | window | early-exit cost | d mean $k/wk at 0 / 1 / 2 / 3.4 | break-even target shortfall (pts) |
|---|---|---|---|---|---|
| none | gated five lines | F9 | 1.0 | -21.7 / -18.0 / -15.1 / -11.6 | >3.4 |
| none | gated five lines | F9 | 2.0 | -25.6 / -21.9 / -18.7 / -15.6 | >3.4 |
| none | gated five lines | L6M | 1.0 | -20.1 / -16.0 / -13.0 / -9.7 | >3.4 |
| none | gated five lines | L6M | 2.0 | -24.1 / -19.9 / -16.5 / -13.6 | >3.4 |
| none | gated five lines | PRE | 1.0 | -11.2 / -9.6 / -8.0 / -5.9 | >3.4 |
| none | gated five lines | PRE | 2.0 | -13.5 / -12.0 / -10.4 / -8.2 | >3.4 |
| none | plain 0.70 take | F9 | 1.0 | -9.0 / -4.6 / -0.9 / +3.4 | 2.3 |
| none | plain 0.70 take | F9 | 2.0 | -12.9 / -8.3 / -4.8 / -0.5 | >3.4 |
| none | plain 0.70 take | L6M | 1.0 | -9.2 / -4.4 / -0.6 / +3.4 | 2.2 |
| none | plain 0.70 take | L6M | 2.0 | -12.9 / -8.0 / -4.3 / -0.3 | >3.4 |
| none | plain 0.70 take | PRE | 1.0 | -5.9 / -3.9 / -1.7 / +1.3 | 2.8 |
| none | plain 0.70 take | PRE | 2.0 | -8.3 / -6.3 / -4.0 / -1.1 | >3.4 |
| 12R | gated five lines | F9 | 1.0 | -16.3 / -11.1 / -10.3 / -8.3 | >3.4 |
| 12R | gated five lines | F9 | 2.0 | -19.9 / -15.1 / -13.9 / -12.0 | >3.4 |
| 12R | gated five lines | L6M | 1.0 | -13.3 / -10.0 / -8.9 / -7.0 | >3.4 |
| 12R | gated five lines | L6M | 2.0 | -18.1 / -14.9 / -13.3 / -11.4 | >3.4 |
| 12R | gated five lines | PRE | 1.0 | -7.2 / -6.5 / -4.9 / -3.0 | >3.4 |
| 12R | gated five lines | PRE | 2.0 | -9.3 / -9.0 / -7.4 / -5.3 | >3.4 |
| 12R | plain 0.70 take | F9 | 1.0 | -6.8 / -1.5 / -0.3 / +2.0 | 2.2 |
| 12R | plain 0.70 take | F9 | 2.0 | -10.3 / -5.0 / -3.8 / -1.4 | >3.4 |
| 12R | plain 0.70 take | L6M | 1.0 | -7.2 / -3.5 / -1.9 / +0.4 | 3.2 |
| 12R | plain 0.70 take | L6M | 2.0 | -10.0 / -6.3 / -4.7 / -2.3 | >3.4 |
| 12R | plain 0.70 take | PRE | 1.0 | -2.1 / -1.3 / +0.6 / +2.9 | 1.7 |
| 12R | plain 0.70 take | PRE | 2.0 | -3.6 / -2.8 / -1.0 / +1.3 | 2.6 |


How to use: compare with your own live fills: (a) the average cost of your market profit-take exits vs the price at the signal second (xcost), (b) the average shortfall of touched-target limit fills vs nominal (tshort). If your targets fill at nominal (tshort ~ 0, 11/11 so far), read the first column. Stop cost (2.45 live vs 1.01 modelled) is NOT varied here; raising it helps early exits by +0.1..+0.6 pt per trade (DS3_BASIS_LIVE).
