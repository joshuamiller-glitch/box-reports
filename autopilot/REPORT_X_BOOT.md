# REPORT X_BOOT - 20,000-draw bootstraps for the HM VWAP-anchor variants and the B11 Track 2 insurance cells

**Task.** Bootstrap the weekly-Sharpe uplift and the net uplift of (1) HM VWAP resets at 17:00 / 18:00 / 19:00 ET versus the live 00:00 fixed UTC-4 reset, and (2) the two distinct B11 Track 2 INSURANCE cells, on the corrected engine, against two baselines: the LIVE pair (day lock 8R/2R/67%/0000, combined week floor -8R, per-book week rule off, TH off) and the default `B.Cfg()` pair (the 1.35/1.65/2.26 one). All rows were re-simulated here with the account model, each run in a fresh process (no `b10_core` import). Check: the hm_A row set (live HM) reproduces the corrected rows to a max daily difference of 0.00 (LIVE) / 0.00 (DEF) dollars.

**Method.** 20,000 paired resamples of the weekly P&L (variant and baseline share the resampled weeks), two schemes: week-resampled i.i.d., and 4-week moving blocks (circular). Per span (clean 2023-08..2025-07, H1 2025-08-01..2026-02-06, H2 2026-02-07..2026-10-13, all-in 2023-08..2026-10-13): net uplift (variant - baseline, $), weekly-Sharpe uplift (annualised sqrt(52)), 90% and 95% percentile CIs, P(uplift>0). 26-week rolling Sharpe share and the circular-shift rank are reported (shift null is reported only under the amended gates). Own matched nulls: for the HM anchors, the 23 other hourly fixed-UTC-4 resets (same HM logic, only the reset hour differs; this is the anchor-hour null: only 23 draws, so 'p95' is the 2nd-highest of 23); for Track 2, 200 random draws that scale the same number of accepted entries (2a same 75%: 3103 of 10298 accepted entries, 2d Globex/RTH 100/50: 3945 of 10298 accepted entries) by the same factor at random, re-simulated with the full account model. Note the real cells also change acceptance (entries lost to the per-book rules: 2a same 75%: 428, 2d Globex/RTH 100/50: 253), which the random draw does not replicate.

**Overlapping and tied cells.** Track 2 'same 75% / opp X' cells are numerically identical for every X in {100,75,50,25,0} (the opposite-direction branch is never exercised), so one cell stands for all five. The 'both books Globex/RTH 100/50' cell is the sixth INSURANCE cell.

## 1. HM VWAP anchor, 17:00 / 18:00 / 19:00 ET vs the live 00:00 reset

### Baseline: LIVE pair = Cfg(wk_floor=8, wk_loss_pb=None)

| cell | span | weeks | net uplift $ | Sharpe uplift | iid 90% CI net | iid 95% CI net | blk4 90% CI net | iid 90% CI Sharpe | iid 95% CI Sharpe | blk4 90% CI Sharpe | P(net>0) iid / blk4 | P(Sh>0) iid / blk4 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ET 17:00 vs live HM | clean | 105 | -114,509 | -0.09 | [-691,060, +464,051] | [-803,040, +578,003] | [-683,531, +466,143] | [-0.70, +0.54] | [-0.81, +0.66] | [-0.69, +0.55] | 0.37 / 0.37 | 0.41 / 0.40 |
| ET 17:00 vs live HM | H1 | 28 | 18,363 | -0.29 | [-264,349, +289,340] | [-321,260, +340,795] | [-266,987, +317,682] | [-1.73, +0.93] | [-2.02, +1.15] | [-1.62, +0.87] | 0.55 / 0.54 | 0.35 / 0.34 |
| ET 17:00 vs live HM | H2 | 36 | -18,147 | -0.21 | [-453,979, +426,976] | [-531,544, +513,185] | [-333,115, +287,041] | [-1.67, +1.31] | [-1.97, +1.63] | [-1.45, +0.85] | 0.47 / 0.46 | 0.41 / 0.37 |
| ET 17:00 vs live HM | all | 168 | -114,293 | -0.12 | [-894,866, +651,607] | [-1,034,059, +807,280] | [-799,186, +576,774] | [-0.64, +0.41] | [-0.75, +0.51] | [-0.60, +0.36] | 0.40 / 0.39 | 0.35 / 0.34 |
| ET 18:00 vs live HM | clean | 105 | -114,509 | -0.09 | [-700,350, +464,789] | [-816,120, +578,060] | [-685,692, +462,614] | [-0.70, +0.54] | [-0.82, +0.67] | [-0.70, +0.55] | 0.38 / 0.37 | 0.41 / 0.40 |
| ET 18:00 vs live HM | H1 | 28 | 18,363 | -0.29 | [-268,871, +291,413] | [-324,057, +343,970] | [-268,043, +319,303] | [-1.72, +0.93] | [-2.04, +1.16] | [-1.62, +0.88] | 0.54 / 0.53 | 0.36 / 0.34 |
| ET 18:00 vs live HM | H2 | 36 | -18,147 | -0.21 | [-454,946, +434,212] | [-532,472, +520,962] | [-335,441, +285,157] | [-1.69, +1.32] | [-1.98, +1.67] | [-1.46, +0.84] | 0.47 / 0.46 | 0.41 / 0.37 |
| ET 18:00 vs live HM | all | 168 | -114,293 | -0.12 | [-899,377, +667,568] | [-1,049,023, +815,982] | [-792,140, +574,026] | [-0.65, +0.42] | [-0.75, +0.52] | [-0.59, +0.35] | 0.41 / 0.39 | 0.36 / 0.34 |
| ET 19:00 vs live HM | clean | 105 | 79,974 | +0.07 | [-369,358, +523,662] | [-459,657, +609,926] | [-308,563, +470,677] | [-0.41, +0.58] | [-0.50, +0.68] | [-0.33, +0.50] | 0.62 / 0.63 | 0.61 / 0.62 |
| ET 19:00 vs live HM | H1 | 28 | -83,065 | -0.42 | [-433,867, +240,492] | [-508,955, +290,963] | [-490,059, +262,545] | [-2.27, +1.32] | [-2.71, +1.62] | [-2.49, +1.30] | 0.36 / 0.40 | 0.36 / 0.39 |
| ET 19:00 vs live HM | H2 | 36 | 248,848 | +0.40 | [-330,816, +837,333] | [-436,324, +952,034] | [-354,170, +818,013] | [-1.45, +2.20] | [-1.84, +2.58] | [-1.63, +2.25] | 0.76 / 0.76 | 0.65 / 0.64 |
| ET 19:00 vs live HM | all | 168 | 245,757 | +0.09 | [-571,280, +1,070,401] | [-727,167, +1,237,317] | [-570,719, +1,045,615] | [-0.47, +0.66] | [-0.58, +0.76] | [-0.48, +0.65] | 0.70 / 0.69 | 0.61 / 0.61 |

**Does the CI exclude zero?**
- **ET 17:00 vs live HM**: clean: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H1: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H2: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; all: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0
- **ET 18:00 vs live HM**: clean: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H1: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H2: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; all: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0
- **ET 19:00 vs live HM**: clean: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H1: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H2: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; all: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0

| cell | base | rolling 26-wk Sharpe >= baseline (share of windows) | circular-shift rank of the Sharpe uplift (reported only) | shift p95 |
|---|---|---|---|---|
| ET 17:00 vs live HM | LIVE | 29% | 100% | -0.24 |
| ET 18:00 vs live HM | LIVE | 29% | 100% | -0.24 |
| ET 19:00 vs live HM | LIVE | 41% | 100% | -0.03 |


### Baseline: default B.Cfg() (per-book -6R week rule on, no combined floor; the 1.35/1.65/2.26 pair)

| cell | span | weeks | net uplift $ | Sharpe uplift | iid 90% CI net | iid 95% CI net | blk4 90% CI net | iid 90% CI Sharpe | iid 95% CI Sharpe | blk4 90% CI Sharpe | P(net>0) iid / blk4 | P(Sh>0) iid / blk4 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ET 17:00 vs live HM | clean | 105 | -16,657 | +0.06 | [-633,886, +602,698] | [-750,904, +722,708] | [-604,916, +556,738] | [-0.62, +0.76] | [-0.75, +0.90] | [-0.58, +0.70] | 0.48 / 0.48 | 0.55 / 0.57 |
| ET 17:00 vs live HM | H1 | 28 | 109,432 | +0.41 | [-153,919, +369,494] | [-205,525, +415,777] | [-192,913, +409,951] | [-0.95, +1.25] | [-1.24, +1.42] | [-1.03, +1.35] | 0.76 / 0.72 | 0.69 / 0.67 |
| ET 17:00 vs live HM | H2 | 36 | 280,798 | +1.10 | [-149,285, +728,380] | [-228,958, +817,607] | [-32,830, +579,410] | [-0.52, +2.83] | [-0.84, +3.19] | [-0.15, +2.21] | 0.85 / 0.93 | 0.87 / 0.93 |
| ET 17:00 vs live HM | all | 168 | 373,572 | +0.34 | [-416,564, +1,175,504] | [-576,149, +1,337,713] | [-324,166, +1,057,054] | [-0.22, +0.89] | [-0.32, +1.01] | [-0.14, +0.79] | 0.78 / 0.81 | 0.84 / 0.88 |
| ET 18:00 vs live HM | clean | 105 | -16,657 | +0.06 | [-631,305, +600,012] | [-743,593, +727,526] | [-613,530, +558,363] | [-0.61, +0.75] | [-0.74, +0.90] | [-0.58, +0.69] | 0.48 / 0.48 | 0.56 / 0.56 |
| ET 18:00 vs live HM | H1 | 28 | 109,432 | +0.41 | [-156,551, +367,419] | [-208,211, +420,012] | [-195,338, +412,684] | [-0.94, +1.26] | [-1.23, +1.41] | [-1.05, +1.35] | 0.76 / 0.72 | 0.69 / 0.66 |
| ET 18:00 vs live HM | H2 | 36 | 280,798 | +1.10 | [-151,175, +729,212] | [-227,285, +818,814] | [-31,628, +577,582] | [-0.53, +2.82] | [-0.85, +3.17] | [-0.15, +2.21] | 0.85 / 0.93 | 0.87 / 0.93 |
| ET 18:00 vs live HM | all | 168 | 373,572 | +0.34 | [-415,153, +1,176,641] | [-554,071, +1,326,280] | [-323,271, +1,061,963] | [-0.21, +0.89] | [-0.31, +1.00] | [-0.14, +0.79] | 0.78 / 0.81 | 0.84 / 0.88 |
| ET 19:00 vs live HM | clean | 105 | 111,208 | +0.13 | [-344,641, +554,801] | [-435,958, +638,168] | [-335,351, +545,310] | [-0.34, +0.63] | [-0.43, +0.72] | [-0.33, +0.59] | 0.66 / 0.66 | 0.68 / 0.69 |
| ET 19:00 vs live HM | H1 | 28 | 88,919 | +0.70 | [-253,220, +433,150] | [-317,817, +502,132] | [-278,064, +447,397] | [-1.16, +2.21] | [-1.49, +2.48] | [-1.17, +2.15] | 0.67 / 0.66 | 0.74 / 0.75 |
| ET 19:00 vs live HM | H2 | 36 | 477,150 | +1.11 | [-63,561, +1,027,494] | [-157,559, +1,136,949] | [-99,988, +1,077,733] | [-0.62, +2.96] | [-0.97, +3.30] | [-0.84, +3.24] | 0.93 / 0.91 | 0.85 / 0.82 |
| ET 19:00 vs live HM | all | 168 | 677,277 | +0.45 | [-111,774, +1,479,541] | [-267,664, +1,635,429] | [-138,448, +1,543,571] | [-0.09, +1.00] | [-0.20, +1.11] | [-0.11, +1.04] | 0.92 / 0.91 | 0.91 / 0.90 |

**Does the CI exclude zero?**
- **ET 17:00 vs live HM**: clean: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H1: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H2: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; all: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0
- **ET 18:00 vs live HM**: clean: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H1: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H2: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; all: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0
- **ET 19:00 vs live HM**: clean: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H1: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H2: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; all: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0

| cell | base | rolling 26-wk Sharpe >= baseline (share of windows) | circular-shift rank of the Sharpe uplift (reported only) | shift p95 |
|---|---|---|---|---|
| ET 17:00 vs live HM | DEF | 65% | 100% | +0.10 |
| ET 18:00 vs live HM | DEF | 65% | 100% | +0.10 |
| ET 19:00 vs live HM | DEF | 60% | 100% | +0.28 |


### Anchor-hour null (own matched null): the ET anchor's uplift vs the 23 other fixed-clock hourly resets

| anchor   | base   | span   |   sh_uplift |   net_uplift |   null_sh_p95 |   null_sh_max |   rank_sh |   null_net_p95 |   rank_net | beats_p95_sh   |
|:---------|:-------|:-------|------------:|-------------:|--------------:|--------------:|----------:|---------------:|-----------:|:---------------|
| ET 17:00 | LIVE   | clean  |       -0.09 |   -114509.12 |          0.23 |          0.26 |      0.61 |      214744.22 |       0.30 | False          |
| ET 18:00 | LIVE   | clean  |       -0.09 |   -114509.12 |          0.23 |          0.26 |      0.61 |      214744.22 |       0.30 | False          |
| ET 19:00 | LIVE   | clean  |        0.07 |     79974.08 |          0.23 |          0.26 |      0.83 |      214744.22 |       0.78 | False          |
| ET 17:00 | DEF    | clean  |        0.06 |    -16657.28 |          0.18 |          0.30 |      0.52 |      202644.54 |       0.43 | False          |
| ET 18:00 | DEF    | clean  |        0.06 |    -16657.28 |          0.18 |          0.30 |      0.52 |      202644.54 |       0.43 | False          |
| ET 19:00 | DEF    | clean  |        0.13 |    111208.00 |          0.18 |          0.30 |      0.87 |      202644.54 |       0.78 | False          |
| ET 17:00 | LIVE   | H1     |       -0.29 |     18362.88 |          0.33 |          0.91 |      0.43 |      123452.99 |       0.57 | False          |
| ET 18:00 | LIVE   | H1     |       -0.29 |     18362.88 |          0.33 |          0.91 |      0.43 |      123452.99 |       0.57 | False          |
| ET 19:00 | LIVE   | H1     |       -0.42 |    -83064.64 |          0.33 |          0.91 |      0.26 |      123452.99 |       0.26 | False          |
| ET 17:00 | DEF    | H1     |        0.41 |    109432.00 |          0.72 |          0.97 |      0.65 |      196222.82 |       0.70 | False          |
| ET 18:00 | DEF    | H1     |        0.41 |    109432.00 |          0.72 |          0.97 |      0.65 |      196222.82 |       0.70 | False          |
| ET 19:00 | DEF    | H1     |        0.70 |     88919.04 |          0.72 |          0.97 |      0.91 |      196222.82 |       0.61 | False          |
| ET 17:00 | LIVE   | H2     |       -0.21 |    -18146.88 |          0.05 |          0.09 |      0.83 |       59441.63 |       0.78 | False          |
| ET 18:00 | LIVE   | H2     |       -0.21 |    -18146.88 |          0.05 |          0.09 |      0.83 |       59441.63 |       0.78 | False          |
| ET 19:00 | LIVE   | H2     |        0.40 |    248847.68 |          0.05 |          0.09 |      1.00 |       59441.63 |       1.00 | True           |
| ET 17:00 | DEF    | H2     |        1.10 |    280797.76 |          1.06 |          1.10 |      0.96 |      294228.06 |       0.87 | True           |
| ET 18:00 | DEF    | H2     |        1.10 |    280797.76 |          1.06 |          1.10 |      0.96 |      294228.06 |       0.87 | True           |
| ET 19:00 | DEF    | H2     |        1.11 |    477150.40 |          1.06 |          1.10 |      1.00 |      294228.06 |       1.00 | True           |
| ET 17:00 | LIVE   | all    |       -0.12 |   -114293.12 |          0.04 |          0.17 |      0.61 |      148887.10 |       0.61 | False          |
| ET 18:00 | LIVE   | all    |       -0.12 |   -114293.12 |          0.04 |          0.17 |      0.61 |      148887.10 |       0.61 | False          |
| ET 19:00 | LIVE   | all    |        0.09 |    245757.12 |          0.04 |          0.17 |      0.96 |      148887.10 |       0.96 | True           |
| ET 17:00 | DEF    | all    |        0.34 |    373572.48 |          0.36 |          0.46 |      0.87 |      446261.18 |       0.78 | False          |
| ET 18:00 | DEF    | all    |        0.34 |    373572.48 |          0.36 |          0.46 |      0.87 |      446261.18 |       0.78 | False          |
| ET 19:00 | DEF    | all    |        0.45 |    677277.44 |          0.36 |          0.46 |      0.96 |      446261.18 |       1.00 | True           |

'beats_p95_sh' = the anchor's Sharpe uplift is above the 95th percentile of the 23 fixed-clock hours' uplifts.

## 2. B11 Track 2 insurance cells vs the live pair

### Baseline: LIVE pair = Cfg(wk_floor=8, wk_loss_pb=None)

| cell | span | weeks | net uplift $ | Sharpe uplift | iid 90% CI net | iid 95% CI net | blk4 90% CI net | iid 90% CI Sharpe | iid 95% CI Sharpe | blk4 90% CI Sharpe | P(net>0) iid / blk4 | P(Sh>0) iid / blk4 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2a same 75% vs live pair | clean | 105 | -347,909 | -0.31 | [-684,686, -22,978] | [-757,012, +36,359] | [-759,726, +45,182] | [-0.66, +0.04] | [-0.74, +0.11] | [-0.70, +0.11] | 0.04 / 0.07 | 0.07 / 0.11 |
| 2a same 75% vs live pair | H1 | 28 | 25,938 | +0.21 | [-89,409, +133,908] | [-113,243, +151,860] | [-86,478, +128,283] | [-0.26, +0.76] | [-0.36, +0.89] | [-0.23, +0.62] | 0.66 / 0.67 | 0.78 / 0.81 |
| 2a same 75% vs live pair | H2 | 36 | 78,634 | +0.08 | [-350,499, +524,111] | [-428,536, +621,102] | [-259,345, +436,751] | [-1.22, +1.33] | [-1.48, +1.61] | [-1.04, +1.15] | 0.60 / 0.64 | 0.53 / 0.52 |
| 2a same 75% vs live pair | all | 168 | -243,336 | -0.13 | [-806,396, +316,108] | [-910,349, +442,407] | [-812,266, +325,621] | [-0.50, +0.24] | [-0.57, +0.31] | [-0.49, +0.24] | 0.23 / 0.24 | 0.28 / 0.28 |
| 2d Globex/RTH 100/50 vs live pair | clean | 105 | 144,336 | +0.32 | [-261,628, +571,981] | [-329,917, +662,553] | [-245,959, +552,713] | [-0.15, +0.86] | [-0.23, +0.98] | [-0.14, +0.86] | 0.71 / 0.72 | 0.86 / 0.87 |
| 2d Globex/RTH 100/50 vs live pair | H1 | 28 | -8,568 | -0.08 | [-195,804, +177,659] | [-232,964, +216,199] | [-189,662, +164,633] | [-1.00, +0.78] | [-1.22, +0.95] | [-0.90, +0.64] | 0.47 / 0.47 | 0.42 / 0.43 |
| 2d Globex/RTH 100/50 vs live pair | H2 | 36 | -151,704 | -0.44 | [-301,824, -15,611] | [-334,281, +7,111] | [-278,770, -34,929] | [-1.02, +0.03] | [-1.15, +0.11] | [-1.04, -0.02] | 0.03 / 0.01 | 0.06 / 0.04 |
| 2d Globex/RTH 100/50 vs live pair | all | 168 | -15,936 | +0.10 | [-486,328, +477,396] | [-570,106, +572,663] | [-475,448, +470,150] | [-0.24, +0.47] | [-0.31, +0.56] | [-0.23, +0.47] | 0.47 / 0.47 | 0.68 / 0.69 |

**Does the CI exclude zero?**
- **2a same 75% vs live pair**: clean: net below 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H1: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H2: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; all: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0
- **2d Globex/RTH 100/50 vs live pair**: clean: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H1: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H2: net below 0 (iid) / below 0 (4-wk block), Sharpe spans 0 / below 0; all: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0

| cell | base | rolling 26-wk Sharpe >= baseline (share of windows) | circular-shift rank of the Sharpe uplift (reported only) | shift p95 |
|---|---|---|---|---|
| 2a same 75% vs live pair | LIVE | 41% | 100% | -0.24 |
| 2d Globex/RTH 100/50 vs live pair | LIVE | 59% | 100% | -0.06 |


### Baseline: default B.Cfg() (per-book -6R week rule on, no combined floor; the 1.35/1.65/2.26 pair)

| cell | span | weeks | net uplift $ | Sharpe uplift | iid 90% CI net | iid 95% CI net | blk4 90% CI net | iid 90% CI Sharpe | iid 95% CI Sharpe | blk4 90% CI Sharpe | P(net>0) iid / blk4 | P(Sh>0) iid / blk4 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2a same 75% vs live pair | clean | 105 | -176,156 | -0.08 | [-558,415, +206,330] | [-627,288, +275,468] | [-657,539, +280,651] | [-0.50, +0.37] | [-0.58, +0.47] | [-0.56, +0.46] | 0.22 / 0.27 | 0.38 / 0.41 |
| 2a same 75% vs live pair | H1 | 28 | 94,642 | +0.62 | [-42,000, +231,959] | [-69,495, +261,530] | [-58,123, +257,658] | [+0.02, +1.05] | [-0.10, +1.14] | [-0.05, +1.01] | 0.87 / 0.84 | 0.96 / 0.94 |
| 2a same 75% vs live pair | H2 | 36 | 253,687 | +0.77 | [-165,284, +700,919] | [-240,912, +791,303] | [-79,919, +581,511] | [-0.59, +2.05] | [-0.86, +2.32] | [-0.42, +1.79] | 0.83 / 0.89 | 0.82 / 0.86 |
| 2a same 75% vs live pair | all | 168 | 172,173 | +0.24 | [-414,144, +782,717] | [-519,767, +910,324] | [-469,945, +796,759] | [-0.17, +0.65] | [-0.24, +0.73] | [-0.18, +0.67] | 0.68 / 0.68 | 0.83 / 0.83 |
| 2d Globex/RTH 100/50 vs live pair | clean | 105 | 175,967 | +0.35 | [-189,014, +553,777] | [-262,092, +625,339] | [-190,042, +552,024] | [-0.06, +0.80] | [-0.15, +0.90] | [-0.06, +0.82] | 0.79 / 0.78 | 0.92 / 0.92 |
| 2d Globex/RTH 100/50 vs live pair | H1 | 28 | 55,490 | +0.30 | [-143,401, +248,325] | [-181,874, +285,259] | [-132,832, +232,919] | [-0.61, +1.06] | [-0.82, +1.23] | [-0.50, +0.91] | 0.68 / 0.70 | 0.71 / 0.76 |
| 2d Globex/RTH 100/50 vs live pair | H2 | 36 | -82,672 | -0.17 | [-235,206, +71,469] | [-264,325, +100,677] | [-181,263, +16,769] | [-0.74, +0.36] | [-0.85, +0.48] | [-0.65, +0.24] | 0.19 / 0.08 | 0.30 / 0.25 |
| 2d Globex/RTH 100/50 vs live pair | all | 168 | 148,785 | +0.23 | [-294,296, +598,490] | [-376,165, +683,542] | [-278,066, +578,803] | [-0.08, +0.55] | [-0.13, +0.61] | [-0.07, +0.54] | 0.70 / 0.71 | 0.89 / 0.90 |

**Does the CI exclude zero?**
- **2a same 75% vs live pair**: clean: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H1: net spans 0 (iid) / spans 0 (4-wk block), Sharpe above 0 / spans 0; H2: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; all: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0
- **2d Globex/RTH 100/50 vs live pair**: clean: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H1: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; H2: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0; all: net spans 0 (iid) / spans 0 (4-wk block), Sharpe spans 0 / spans 0

| cell | base | rolling 26-wk Sharpe >= baseline (share of windows) | circular-shift rank of the Sharpe uplift (reported only) | shift p95 |
|---|---|---|---|---|
| 2a same 75% vs live pair | DEF | 71% | 100% | +0.05 |
| 2d Globex/RTH 100/50 vs live pair | DEF | 81% | 100% | +0.07 |


### Matched random null (200 draws: same number of accepted entries scaled by the same factor at random)

| cell                 | base   | span   |   real_sh_uplift |   null_sh_p95 |   null_sh_median |   rank_sh |   real_net_uplift |   null_net_p95 |   null_net_median |   rank_net | beats_p95_sh   | beats_p95_net   |
|:---------------------|:-------|:-------|-----------------:|--------------:|-----------------:|----------:|------------------:|---------------:|------------------:|-----------:|:---------------|:----------------|
| 2a same 75%          | LIVE   | clean  |            -0.31 |          0.07 |            -0.26 |      0.40 |        -347908.56 |       34174.24 |        -260815.88 |       0.26 | False          | False           |
| 2a same 75%          | LIVE   | H1     |             0.21 |          0.94 |             0.23 |      0.48 |          25938.08 |      205164.43 |          55625.08 |       0.40 | False          | False           |
| 2a same 75%          | LIVE   | H2     |             0.08 |          0.34 |            -0.19 |      0.78 |          78634.48 |      139795.37 |         -43036.04 |       0.83 | False          | False           |
| 2a same 75%          | LIVE   | all    |            -0.13 |          0.05 |            -0.15 |      0.58 |        -243336.00 |      104510.06 |        -248299.40 |       0.51 | False          | False           |
| 2a same 75%          | DEF    | clean  |            -0.08 |          0.26 |            -0.09 |      0.53 |        -176156.08 |      179176.98 |        -100871.04 |       0.34 | False          | False           |
| 2a same 75%          | DEF    | H1     |             0.62 |          1.26 |             0.56 |      0.56 |          94642.24 |      273441.28 |         109154.36 |       0.44 | False          | False           |
| 2a same 75%          | DEF    | H2     |             0.77 |          0.75 |             0.01 |      0.95 |         253686.64 |      251293.22 |          33876.16 |       0.95 | True           | True            |
| 2a same 75%          | DEF    | all    |             0.24 |          0.31 |             0.05 |      0.87 |         172172.80 |      386552.41 |          32474.32 |       0.73 | False          | False           |
| 2d Globex/RTH 100/50 | LIVE   | clean  |             0.32 |          0.13 |            -0.33 |      0.99 |         144335.84 |       20171.62 |        -371553.36 |       0.99 | True           | True            |
| 2d Globex/RTH 100/50 | LIVE   | H1     |            -0.08 |          1.46 |             0.34 |      0.26 |          -8568.00 |      277439.80 |          69326.80 |       0.28 | False          | False           |
| 2d Globex/RTH 100/50 | LIVE   | H2     |            -0.44 |          0.45 |            -0.47 |      0.52 |        -151704.00 |      166419.43 |        -150037.20 |       0.49 | False          | False           |
| 2d Globex/RTH 100/50 | LIVE   | all    |             0.10 |          0.13 |            -0.26 |      0.93 |         -15936.16 |      135614.02 |        -454550.00 |       0.90 | False          | False           |
| 2d Globex/RTH 100/50 | DEF    | clean  |             0.35 |          0.36 |            -0.13 |      0.94 |         175966.72 |      168124.90 |        -214486.80 |       0.95 | False          | True            |
| 2d Globex/RTH 100/50 | DEF    | H1     |             0.30 |          1.98 |             0.89 |      0.17 |          55490.08 |      390978.14 |         149707.20 |       0.23 | False          | False           |
| 2d Globex/RTH 100/50 | DEF    | H2     |            -0.17 |          0.84 |            -0.24 |      0.56 |         -82671.68 |      285555.28 |         -66062.32 |       0.47 | False          | False           |
| 2d Globex/RTH 100/50 | DEF    | all    |             0.23 |          0.46 |             0.01 |      0.80 |         148785.12 |      415183.56 |        -134107.44 |       0.79 | False          | False           |

## 3. Gate summary under the amended gates (own null p95 + bootstrap CI of the uplift; shift null reported only)

| cell | base | span | CI90 Sharpe iid excl. 0 (above) | CI90 Sharpe blk4 | own null p95 beaten | uplift sign |
|---|---|---|---|---|---|---|
| ET 17:00 vs live HM | LIVE | clean | no | no | no | -0.09 |
| ET 17:00 vs live HM | LIVE | H1 | no | no | no | -0.29 |
| ET 17:00 vs live HM | LIVE | H2 | no | no | no | -0.21 |
| ET 18:00 vs live HM | LIVE | clean | no | no | no | -0.09 |
| ET 18:00 vs live HM | LIVE | H1 | no | no | no | -0.29 |
| ET 18:00 vs live HM | LIVE | H2 | no | no | no | -0.21 |
| ET 19:00 vs live HM | LIVE | clean | no | no | no | +0.07 |
| ET 19:00 vs live HM | LIVE | H1 | no | no | no | -0.42 |
| ET 19:00 vs live HM | LIVE | H2 | no | no | yes | +0.40 |
| ET 17:00 vs live HM | DEF | clean | no | no | no | +0.06 |
| ET 17:00 vs live HM | DEF | H1 | no | no | no | +0.41 |
| ET 17:00 vs live HM | DEF | H2 | no | no | yes | +1.10 |
| ET 18:00 vs live HM | DEF | clean | no | no | no | +0.06 |
| ET 18:00 vs live HM | DEF | H1 | no | no | no | +0.41 |
| ET 18:00 vs live HM | DEF | H2 | no | no | yes | +1.10 |
| ET 19:00 vs live HM | DEF | clean | no | no | no | +0.13 |
| ET 19:00 vs live HM | DEF | H1 | no | no | no | +0.70 |
| ET 19:00 vs live HM | DEF | H2 | no | no | yes | +1.11 |
| 2a same 75% vs live pair | LIVE | clean | no | no | no | -0.31 |
| 2a same 75% vs live pair | LIVE | H1 | no | no | no | +0.21 |
| 2a same 75% vs live pair | LIVE | H2 | no | no | no | +0.08 |
| 2d Globex/RTH 100/50 vs live pair | LIVE | clean | no | no | yes | +0.32 |
| 2d Globex/RTH 100/50 vs live pair | LIVE | H1 | no | no | no | -0.08 |
| 2d Globex/RTH 100/50 vs live pair | LIVE | H2 | no | no | no | -0.44 |
| 2a same 75% vs live pair | DEF | clean | no | no | no | -0.08 |
| 2a same 75% vs live pair | DEF | H1 | yes | no | no | +0.62 |
| 2a same 75% vs live pair | DEF | H2 | no | no | yes | +0.77 |
| 2d Globex/RTH 100/50 vs live pair | DEF | clean | no | no | no | +0.35 |
| 2d Globex/RTH 100/50 vs live pair | DEF | H1 | no | no | no | +0.30 |
| 2d Globex/RTH 100/50 vs live pair | DEF | H2 | no | no | no | -0.17 |

## Caveats
- **ET 17:00 and ET 18:00 are the same variant.** CME has no bars between 17:00 and 18:00 ET (maintenance break), so a VWAP reset at 17:00 or 18:00 starts from the same first bar; their rows are identical to the dollar, and they count as one anchor, not two.
- **The circular-shift rank (1.00 everywhere) is uninformative for these cells.** The uplift series d = variant - baseline is a modification of the pair's own trades and is mechanically (negatively) correlated with the baseline weekly P&L; shifting d against the baseline therefore always looks worse than the aligned series. It is reported because the amended gates ask for it, and it is not used for any verdict.
- Rolling 26-week share is of all 168 weeks' windows (143 windows).
- Anchor variants other than the three requested are in `HM_ANCHOR_ALL.csv` (REPORT_HM_ANCHOR.md). The 17/18/19 ET rows here use the single slow-slope confirmation, as in that report.
- The anchor-hour null has only 23 draws; the Track 2 null has 200 and does not replicate acceptance changes. Both are matched-by-construction, not exact.
- Weekly P&L is attributed to the ISO week of the trading-day label, as elsewhere in this program. 4-week block bootstrap uses overlapping circular blocks.
- Fill model: the corrected 1-minute NT8-faithful engine, 1 tick/side + $34.88 commission (placeholder; live-fills file has not arrived).
- Runtime: about 18 minutes of compute: 54 account-model runs 131 s on 6 workers, 800 matched-null runs 825 s on 12 workers, bootstraps and report under 10 s (an earlier null attempt with per-task processes was abandoned as too slow after about 9 minutes).
## Reading (plain)
- **No cell clears the amended gates in all three spans on either baseline.** Every 90% CI for the Sharpe uplift spans zero in clean and H1 (the single exception, the 2a same-75% cell vs the default pair in H1, is excluded by the iid scheme only, lower bound +0.02, and not by the 4-week blocks).
- **HM anchors (17:00 = 18:00 ET, 19:00 ET).** Against the LIVE pair they lose in H1 (-0.29 for 17/18, -0.42 for 19:00) and clean (-0.09 / +0.07), with H2 only +0.40 for 19:00 (CI [-1.45, +2.20]; beats the 23-hour anchor null in H2 and all-in, but not in clean or H1). Against the default `B.Cfg()` pair the same anchors look better (H2 +1.10, all-in +0.34 / +0.45) and 19:00 beats the anchor-hour null p95 in H2 and all-in, but every CI spans zero and clean uplift is +0.06 / +0.13. The sign of the H1 uplift depends on which pair is the baseline, so the anchor effect is not separable from the week-rule configuration; no anchor is a survivor.
- **Track 2 same-75%.** Against the LIVE pair it costs clean net ($-348k; CI90 [-$685k, -$23k], excludes zero on the downside) and helps neither H1 nor H2 beyond noise; against the default pair it is positive in H1/H2 (+0.62 / +0.77; H2 beats its matched null) but spans zero in every span. Not a survivor.
- **Track 2 Globex/RTH 100/50.** Against the LIVE pair clean looks good (+0.32, beats its matched null p95 at rank 1.00), H1 is flat and H2 is -0.44 (CI90 [-1.02, +0.03]; the 4-week-block CI [-1.04, -0.02] excludes zero on the downside, net CI [-$302k, -$16k]). It fails in H2. Against the default pair H2 is -0.17.
- **Net.** Bootstrap uncertainty is large (28-36 weeks in H1/H2; a half-year Sharpe CI is about +-1.0). These cells stay NO / not FOUND; the 20,000-draw bootstraps do not rescue any of them.


DONE X_BOOT
