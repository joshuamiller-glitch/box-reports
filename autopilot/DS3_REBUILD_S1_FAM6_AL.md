# DS3_REBUILD_S1_FAM6_AL - Stage 1 family 6 (T-ALPHA forecasts, leaders, breadth) scored on hypothetical RAW trades (W-AL1 / W-AL2)

VERDICT (data ends 2026-10-30; FIRST PASS, placeholder raw outcomes = hyp1m rows of signals_all: own bracket, 1-min path, no layers; Stage 0 exact-engine raw trades will replace them): 10,752 tests (condition x outcome x book x session x window) across 38 cells; 128 (1.2%) exceed the per-cell shifted-time nonsense 99th percentile (1% expected by construction); 9 test-rows keep the same sign with |t|>2 in BOTH L6M and HOLD. Read the survivors table for what, if anything, stands.

Outcome per signal = R (= hyp P&L / stop), MAE (pts), MFE (pts) of the hypothetical raw trade; effect = mean(top tercile of the trade-side-signed condition) - mean(bottom tercile) within book x session x window; t with signal-day-clustered SE; bar = 99th percentile of |t| of the SAME conditions taken from 11/23/37/60/90 days earlier (same persistence, wrong time) in that cell. Conditions: NQ forecast fca_5/15/60/240/480/close, fcpa and tercile, agreement count (mine; /mnt/l2/l2vast/_alpha/rebuild_fam6_alpha_conditions.parquet); leaders ES/RTY/YM/ZN/ZB/6E/GC/CL/NKD... returns 1/5/15/60 min and z, NQ-ES gap and lead/lag, agreement counts (W-AL2 file leaders_signals.parquet). Windows L6M (2026-05..10) and HOLD (2025-11..2026-04).

## Pass share by family and window (expected 1%)

| fam                          | window   |   tests |   passes |   pass_share |
|:-----------------------------|:---------|--------:|---------:|-------------:|
| NQ forecast (T-ALPHA)        | HOLD     |     687 |        7 |        0.01  |
| NQ forecast (T-ALPHA)        | L6M      |     765 |        6 |        0.008 |
| NQ-ES gap / lead-lag (W-AL2) | HOLD     |     348 |        2 |        0.006 |
| NQ-ES gap / lead-lag (W-AL2) | L6M      |     360 |        4 |        0.011 |
| agreement (W-AL2)            | HOLD     |     435 |        0 |        0     |
| agreement (W-AL2)            | L6M      |     504 |        0 |        0     |
| leaders (W-AL2)              | HOLD     |    3597 |       57 |        0.016 |
| leaders (W-AL2)              | L6M      |    4056 |       52 |        0.013 |

## Rows with same sign and |t|>2 in both L6M and HOLD (top 40 by min |t|)

book  session               cond outcome  HOLD  L6M  mint
  K7        0  lead_NQ_r60_bps_s     MFE  4.06 4.17  4.06
  K7        0   nqes_gap60_bps_s     MFE  3.16 3.19  3.16
  K7        0 lead_RTY_r60_bps_s     MFE  2.81 2.84  2.81
  K7        0  lead_ES_r60_bps_s     MFE  3.87 2.55  2.55
  K7        4   lead_GC_r5_bps_s     MAE  2.59 2.30  2.30
  K7        4       lead_GC_z5_s     MAE  2.28 2.37  2.28
  K7        0  lead_NQ_r15_bps_s     MAE  4.83 2.25  2.25
  K7        0      lead_NQ_z60_s       R  2.05 2.20  2.05
  K7        0   nqes_gap60_bps_s       R  2.60 2.03  2.03

## Cells passing the nonsense bar in the recent window (L6M), top 30 by |t|

book  session               cond outcome    n  effect     t  bar99
  K7        0  lead_NQ_r60_bps_s     MFE 1568    7.32  4.17   2.76
  K7        0      lead_NQ_z60_s     MFE 1568    6.19  3.73   2.76
  K7        5  lead_ES_r60_bps_s     MAE  508   14.19  3.68   2.46
  K7        5      lead_6E_z60_s       R  508    0.40  3.40   2.46
  M7        1      lead_GC_z60_s     MAE 1744   -8.57 -3.34   2.24
  K7        1   lead_ZB_r5_bps_s       R 1574    0.22  3.32   2.50
  K7        0   nqes_gap60_bps_s     MFE 1568    5.99  3.19   2.76
  K7        4             fct_15     MFE  668    7.96  3.13   3.00
  P7        5              fca_c       R  772   -0.48 -3.13   2.77
  K7        4            fcpa_15     MFE  668    9.73  3.12   3.00
  K7        0     lead_RTY_z60_s     MFE 1568    5.92  3.11   2.76
  K7        1  lead_ZN_r60_bps_s       R 1574    0.22  3.08   2.50
  M7        1  lead_GC_r60_bps_s     MAE 1744   -7.74 -3.05   2.24
  K7        1  lead_ZN_r15_bps_s     MFE 1574    5.39  3.03   2.50
  K7        1      lead_ZN_z60_s       R 1574    0.21  3.00   2.50
  M7        2      lead_CL_z60_s     MFE  431   14.32  2.99   2.80
  M7        2      lead_CL_z60_s       R  431    0.54  2.98   2.80
  K7        1      lead_ZN_z15_s     MFE 1574    4.98  2.94   2.50
  M7        4         nqes_open5     MFE  902    7.43  2.93   2.89
  M7        2      lead_CL_z60_s     MAE  431  -13.31 -2.92   2.80
  K7        1      lead_ZN_z60_s     MAE 1574   -5.70 -2.89   2.50
  P7        1        nqes_open60     MFE 2324    5.92  2.88   2.11
  K7        0 lead_RTY_r60_bps_s     MFE 1568    5.43  2.84   2.76
  K7        5  lead_6E_r60_bps_s       R  508    0.34  2.84   2.46
  K7        1  lead_ZN_r60_bps_s     MFE 1574    5.25  2.83   2.50
  M7        1      lead_6E_z60_s     MAE 1744   -7.20 -2.81   2.24
  K7        1   lead_ZB_r5_bps_s     MFE 1574    4.59  2.80   2.50
  M7        1  lead_6E_r60_bps_s     MAE 1744   -7.21 -2.74   2.24
  K7        1  lead_ZN_r60_bps_s     MAE 1574   -5.55 -2.73   2.50
  K7        1      lead_ZN_z60_s     MFE 1574    5.13  2.71   2.50

## Feeds D7 lacks (flagged, not dropped)
- NQ forecast (mine): needs 1-min bars of NQ, ES, RTY, YM (NT8/CQG; YM may need a subscription); ridge version = 90-coefficient formula.
- Leaders ES/RTY/YM: same bars. ZN, ZB, 6E, GC, CL, NKD, 6J: each needs its own market-data subscription (not on D7 today); NQ-ES gap and lead/lag need ES only.

