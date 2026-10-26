# REPORT Q31 - weekly time-series momentum / reversal switched by the variance-ratio regime (14 outrights)

**Verdict: NO. FOUND 0.** Pre-registered (PREREG_AUTOPILOT.md 'BATCH 5, Part 2'). For each of ES RTY YM GC CL ZN ZB 6E 6J HG SI NG HO RB: variance ratio VR(5) of ADR-scaled daily changes over {40, 60, 100} days (known before Monday); if VR > 1 follow, if VR < 1 fade the previous {1, 4}-week change; Monday 08:00 ET open to Friday 15:00 ET open, equal ADR-risk legs, 1 tick/side + $4.36 per contract. 6 regime cells plus 4 unconditional follow/fade controls (controls are never selected). Selection (clean-only): positive weekly Sharpe in both clean halves and >= 80 non-zero weeks: 3 cells pass ((1w, VR40), (1w, VR60), (4w, VR60)), all scored below.

| cell | clean | half A | half B | 2013-22 net | 2013-22 gross | non-zero weeks (clean) |
|---|---|---|---|---|---|---|
| 4w, VR60 regime | 1.09 | 0.61 | 1.50 | -0.27 | +0.03 | 97 |
| 4w, VR40 regime | 0.11 | 0.56 | -0.27 | +0.04 | +0.35 | 97 |
| 1w VR40 / VR60 / VR100 regime | see q31_cells.csv | | | | | 97 |
| controls (1w/4w follow/fade) | -0.57 / 0.09 / 0.12 / -0.53 | | | | | 97 |

The selected cell: standalone all-in Sharpe 0.54; additive uplift at 20% share +0.17 clean / +0.01 H1 / -0.14 H2 (all-in +0.08), bootstrap lower bound -0.10, worst week +33.6% (above the 20% allowance), 2x-slippage all-in uplift +0.03, worst-decile correlation -0.18. ERA flag: negative pre-2023 net (-0.27; gross +0.03: cost-negative at best). None of the three passes H1/H2: uplift at 20% (clean / H1 / H2): (4w, VR60) +0.17 / +0.01 / -0.14; (1w, VR60) +0.06 / -0.27 / -0.26; (1w, VR40) +0.06 / +0.08 / -0.36. The variance-ratio gate does not turn momentum/reversal into a stable weekly rule on these 14 markets; the unconditional controls are also flat.

Look-ahead check: VR computed on data through the previous Friday (shift 1), previous-week change uses the last completed Friday close, entry at Monday's open. Library: not saved (no cell passed beyond the rule; series in outputs/autopilot/l/q31_*.csv).

Code ap_q31_vr.py. DONE Q31
