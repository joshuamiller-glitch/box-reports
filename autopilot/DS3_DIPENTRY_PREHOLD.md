# DS3_DIPENTRY_PREHOLD - PRE-only (2024-02..2025-06), selection window; HOLD/X'/2026 not read for any scoring
Prereg sha256 9f73c2f9... + addendum 2 sha 8645ea77...; cells 2,072 (+11 ADD2). Lot-matched stack delta vs market entry, $/week at live lots, 75 PRE weeks.
## Families (PRE stack mean $/wk delta; best / median / n>0 of n)
                   n     best   median  npos
fam                                         
A1_timer         264  15083.0 -20810.0    30
A2_timer_thru1    24 -11299.0 -30185.0     0
B1_gate         1064  33303.0 -31417.0     6
B2_pair          560  33061.0 -24239.0    33
C_staged          76  -7223.0 -25408.0     0
D_learned         84 -14727.0 -35261.0     0

White RC (PRE weekly stack deltas, all 2072 cells): max t 1.48, p 0.849.

## Top 10 PRE cells (stack)
          fam       gate  lv mode  br      mean        lo        hi       mde  fillrate  ptgt_fill  ptgt_base_on_fill
1020  B1_gate  BIG_PRINT   0  lim   0  33302.60 -11240.32  76309.68  62976.21      0.61       0.51               0.55
1412  B2_pair      PAIR1   0  lim   0  33060.54 -13618.02  79084.99  67133.65      0.54       0.51               0.55
1408  B2_pair      PAIR1   0  mkt   0  32585.84 -14115.29  78586.83  66759.78      0.54       0.51               0.55
1016  B1_gate  BIG_PRINT   0  mkt   0  30828.84 -13816.64  74336.16  63309.52      0.62       0.51               0.55
1410  B2_pair      PAIR1   0  mkt   2  29786.98 -23548.51  81310.29  77138.20      0.54       0.51               0.55
1414  B2_pair      PAIR1   0  lim   2  28070.00 -25543.63  79258.75  77406.29      0.54       0.51               0.55
1022  B1_gate  BIG_PRINT   0  lim   2  27358.74 -22177.34  74389.14  68968.90      0.61       0.51               0.55
1464  B2_pair      PAIR2   0  mkt   0  25360.81 -29239.67  78109.06  77477.69      0.35       0.52               0.59
1468  B2_pair      PAIR2   0  lim   0  24153.36 -30756.11  77325.41  77638.64      0.35       0.52               0.59
1018  B1_gate  BIG_PRINT   0  mkt   2  22996.51 -26546.74  70326.24  69595.94      0.62       0.51               0.55

## Per-book PRE-best cell (>=100 fills), book RC
DN: cid 6 mean 586/wk t 0.21 fills 1748 RC p 0.998 share cells>0 0.00
HM: cid 3 mean 6002/wk t 1.18 fills 1268 RC p 0.804 share cells>0 0.13
KB: cid 1576 mean 4587/wk t 1.16 fills 1471 RC p 0.556 share cells>0 0.07
MA: cid 1855 mean 3938/wk t 0.62 fills 538 RC p 0.911 share cells>0 0.06
MV: cid 400 mean 7558/wk t 1.43 fills 2378 RC p 0.913 share cells>0 0.07
PB: cid 1750 mean 15512/wk t 2.32 fills 1380 RC p 0.180 share cells>0 0.89
PE: cid 1464 mean 7603/wk t 1.66 fills 1219 RC p 0.622 share cells>0 0.57
SM: cid 1191 mean 2790/wk t 1.24 fills 796 RC p 0.900 share cells>0 0.13
ST: cid 1020 mean 13652/wk t 2.35 fills 1776 RC p 0.481 share cells>0 0.09
WT: cid 1591 mean 11795/wk t 2.80 fills 612 RC p 0.067 share cells>0 0.87

## Random-gate ranks (B1 market bracket 0, 133 cells): share >=0.95 0.060, >=0.90 0.075

## Walk-forward PRE (quarterly refit, 12m trailing / expanding)
{"trail12m": {"PRE": {"mean": 1957.1, "lo": -37541.2, "hi": 40219.0, "mde": 55801.4, "nw": 75, "n_applied": 15464}, "placebo_rank": 1.0, "placebo_mean": -17602.084676256924, "n_choices": 110, "n_refits_books": 110}, "expanding": {"PRE": {"mean": -18096.6, "lo": -59660.6, "hi": 21358.6, "mde": 57683.0, "nw": 75, "n_applied": 16777}, "placebo_rank": 0.65, "placebo_mean": -21096.621082327958, "n_choices": 104, "n_refits_books": 110}}

## Engine PRE (per-book best cell vs market, exact lock engine)
{"ST": {"cid": 1020, "pre_mean": 7226.57558437602, "lo": -5582.096352322894, "hi": 19413.63651068573, "mde": 17395.71629727567, "nblk": 342, "nkept": 2517, "base_kept": 3206}, "HM": {"cid": 3, "pre_mean": 5672.368005523677, "lo": -5264.590531584685, "hi": 16541.622733379103, "mde": 15514.437941306485, "nblk": 69, "nkept": 1694, "base_kept": 2898}, "WT": {"cid": 1591, "pre_mean": 5525.69184028727, "lo": -1918.2017991767902, "hi": 12872.346601446481, "mde": 10685.11733664437, "nblk": 44, "nkept": 1003, "base_kept": 4669}, "KB": {"cid": 1576, "pre_mean": 907.818610267326, "lo": -5784.356533005439, "hi": 7499.564255881807, "mde": 9607.515981201965, "nblk": 199, "nkept": 2006, "base_kept": 3251}, "SM": {"cid": 1191, "pre_mean": 1629.1804642838536, "lo": -2569.351746833466, "hi": 6016.885721897674, "mde": 6055.508412544294, "nblk": 26, "nkept": 1437, "base_kept": 1568}, "PE": {"cid": 1464, "pre_mean": -1317.7817116287065, "lo": -8548.799667091285, "hi": 5685.174928691564, "mde": 10141.305742403716, "nblk": 374, "nkept": 1933, "base_kept": 3160}}