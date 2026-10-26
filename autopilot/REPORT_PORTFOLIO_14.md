# REPORT PORTFOLIO-14 (user directive PORTFOLIO-14, 2026-10-21)

Live configuration: P9 pair 14/14 (BENCH3 cost-corrected replay, windowed live pair) + K4-EXACT 17-cell ES-hedged (0.98). Weekly $, ISO weeks, OOS = 2024-02-01..2026-10-16 (142 ISO weeks 2024-W05..2026-W42), L8W = ISO weeks 2026-W35..W42 (Aug 24 - Oct 16).

| row | window | weeks | weekly mean | weekly SD | maxDD | worst week | P(DD>$200k) |
|---|---|---|---|---|---|---|---|
| pair alone (P9 14/14) | OOS | 142 | $49,634 | $122,959 | $278,847 | $-144,097 | 84.6% |
| pair alone (P9 14/14) | L8W | 8 | $49,203 | $131,983 | $199,556 | $-136,941 | 94.4% |
| pair+K4 scored edge, QtyScale 1.00 | OOS | 142 | $51,639 | $122,468 | $290,723 | $-141,931 | 81.7% |
| pair+K4 scored edge, QtyScale 1.00 | L8W | 8 | $49,850 | $129,743 | $185,490 | $-137,453 | 91.3% |
| pair+K4 0% edge, QtyScale 1.00 | OOS | 142 | $49,634 | $122,468 | $296,737 | $-143,936 | 84.4% |
| pair+K4 0% edge, QtyScale 1.00 | L8W | 8 | $47,845 | $129,743 | $191,504 | $-139,458 | 93.2% |
| pair+K4 scored edge, QtyScale 1.75 | OOS | 142 | $53,142 | $122,934 | $300,001 | $-146,945 | 76.9% |
| pair+K4 scored edge, QtyScale 1.75 | L8W | 8 | $50,335 | $128,232 | $176,877 | $-137,837 | 89.3% |
| pair+K4 0% edge, QtyScale 1.75 | OOS | 142 | $49,634 | $122,934 | $310,525 | $-150,453 | 86.4% |
| pair+K4 0% edge, QtyScale 1.75 | L8W | 8 | $46,827 | $128,232 | $185,465 | $-141,345 | 93.2% |

Method/caveats:
- Pair = exact P9 BENCH3 series (reproduced: OOS weekly mean $49,634 over 142 weeks, daily-path maxDD $396,989, Sharpe 2.91, worst week -$144,097); K4 = exact_fill_series_fee.pkl, k=0 fill, fee standard $4.84, hedged series (reproduced: Sharpe 1.1615, weekly mean $2,019, weekly SD $12,534, 141 weeks). K4 QtyScale 1.0 = the written file qty (nq_equiv_20pct, gross 2.85 NQ-eq, ES hedge 0.903) = the scored band sized to weekly SD $12.5k; 1.75 = x1.75 (live VPS runs 0.25). K4 is PROVISIONAL (best-of-F 0, H2 Sharpe 0.78), non-virgin, 671 OOS days.
- "0% edge" = K4 weekly series minus its mean (variance/correlation kept), as in REPORT_PORTFOLIO. maxDD = weekly-path max drawdown over the window (pair daily-path OOS maxDD is $397k). P(DD>$200k) = 4-week-block bootstrap, 20,000 draws, 52-week horizon (REPORT_PORTFOLIO method) from the window's weekly series; for L8W the resample pool is only the 8 weeks, so treat it as indicative.
- Weekly correlation pair vs K4: -0.09 (OOS), -0.38 (L8W, 8 points). Pair held at 14/14, no DD-matching.
