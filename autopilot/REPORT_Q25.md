# REPORT Q25 - literature-prior seasonal intraday drift on energy and grains (fixed rules, no selection)

**Verdict: NO. FOUND 0, LEAD 0.** Six pre-registered rules, none tuned: RB long mid-Feb to May and short mid-Sep to Nov, HO long Oct-Jan, NG long Oct-Jan and short Mar-May, ZC and ZS short Jun-Aug and long Feb-Apr, ZW short Jun-Jul; trade the day-session drift every in-season day (energy 08:30-14:00 ET, NG 09:00-14:00, grains 10:30-13:00), 1 contract vol-matched to the pair's clean weekly sigma, time exit, no stop (PREREG_AUTOPILOT.md 'BATCH 4', Q25). No cell was selected, so no false-survivor test; the null is 100 draws of the same number of random in-calendar days with random sides.

| instrument | trades 2013-26 | Sharpe clean / H1 / H2 / all-in | own null p95 (all-in) | uplift@20% clean / H1 / H2 | wd corr | 2013-22 weekly Sharpe gross / net / price-scaled | worst trade per 1 contract |
|---|---|---|---|---|---|---|---|
| RB | 1,702 | 0.65 / -0.10 / -0.64 / 0.08 | 0.92 | +0.09 / -0.07 / -0.37 | +0.42 | +0.06 / -0.04 / -0.03 | -$13,449 |
| HO | 1,107 | -0.74 / -0.02 / +1.39 / -0.04 | 0.75 | -0.19 / -0.00 / +0.26 | -0.22 | -0.02 / -0.09 / -0.09 | -$9,496 |
| NG | 2,010 | 0.45 / 1.19 / 1.10 / 0.69 | 0.38 | +0.03 / +0.27 / +0.13 | +0.52 | -0.47 / -0.87 / -0.94 | -$7,414 |
| ZC | 1,755 | -1.76 / -0.44 / -2.70 / -1.86 | -1.15 | -0.38 / -0.04 / -0.84 | -0.28 | +0.33 / -1.15 / -1.20 | -$2,529 |
| ZS | 1,756 | -1.55 / -1.30 / -1.21 / -1.42 | 0.05 | -0.34 / -0.36 / -0.43 | -0.33 | +0.20 / -0.58 / -0.64 | -$4,879 |
| ZW | 588 | 0.02 / n.a. / 0.40 / 0.13 | 0.11 | -0.03 / 0.00 / -0.07 | +0.30 | +0.48 / -0.01 / -0.03 | -$1,629 |

Only NG beats its null (0.69 vs 0.38, driven by H1 and H2) and its uplift is +0.03 on clean, so it does not meet the +0.10 gate; its 2013-22 weekly Sharpe is negative (net -0.87). No insurance set or constant-risk framing is reported because no rule passes any gate. ERA flags: RB, HO, ZC, ZS, ZW 'gross-positive or flat, cost-negative pre-2023'; NG 'negative pre-2023'. Look-ahead check: the rules use calendar dates only; entries at the open of the window start; no data after the signal row is used. Executability: all CME contracts (NT8 via Rithmic expected); worst-trade figures above are per ONE contract (no sleeve size was set because nothing passed).

Code ap_q25_inst.py, ap_q25_score.py (code/census/night_ins); data outputs/autopilot/l/q25_*.pkl, q25_scores.csv.

DONE Q25
