# DS3_UW_FLOWALERTS - UW flow alerts as entry triggers and filters (W-FA)

**VERDICT: in progress.**

Updated 2026-11-13T23:48Z by fa_cycle.sh (loop, every 3 h). Research/shadow only. No PASS claims. Prereg: autopilot/FLOWALERTS_PREREG.md (sha in DECISIONS.md).

## 1. How deep is the alert history (honest)

The alert endpoint honours time windows: full per-day history exists for 2024-10-01..2026-11-12 (553 weekday files per ticker, IWM QQQ SPY DIA NVDA AAPL MSFT AMZN META GOOGL TSLA). Index options: SPXW and SPX alerts exist from about 2025-03-03 (nothing before), NDX/NDXP return ZERO alerts on this plan (NDX flow is only available as tape trades since 2025-07-21, used as proxy below). Metals/oil ETFs (GLD GDX SLV USO XLE XOP): alerts returned rows for current dates; not pulled by W-UB3 (phase FM never ran); not part of this deliverable unless added later. CAVEAT FIXED: the first pull (W-UB3 phase F) stopped at 2,400 rows per day (12 pages) and walked newest first, so on busy days (QQQ/SPY from 2026-09-21, NVDA TSLA 9-10 days, META 2) only the afternoon survived; W-FA re-pulled those days deep (up to 80 pages) into /mnt/l2/l2vast/_uwfa/raw/ which supersedes. Alert rules present: RepeatedHits (+Ascending/DescendingFill, VolumeOverOi, OtmEarningsFloor) - the "repeated hits on the same strike" feature is the alert rule itself plus a causal 30-min same-chain count (rep30).

| ticker | alerts | days | first | last | med_per_day | max_day | days_ge_2400_after_fix | deep_repull_days |
|---|---|---|---|---|---|---|---|---|
| IWM | 68191 | 532 | 20241001 | 20261112 | 64.0 | 1573 | 0 | 0 |
| SPXW | 236001 | 423 | 20250310 | 20261112 | 223.0 | 10914 | 0 | 444 |
| SPX | 33140 | 423 | 20250310 | 20261112 | 70.0 | 361 | 0 | 444 |
| NVDA | 217878 | 531 | 20241001 | 20261112 | 236.0 | 8059 | 9 | 9 |
| AAPL | 65534 | 531 | 20241001 | 20261112 | 58.0 | 1629 | 0 | 0 |
| MSFT | 39422 | 531 | 20241001 | 20261112 | 43.0 | 1575 | 0 | 0 |
| AMZN | 49052 | 531 | 20241001 | 20261112 | 51.0 | 1273 | 0 | 0 |
| META | 62853 | 531 | 20241001 | 20261112 | 64.0 | 4136 | 2 | 2 |
| GOOGL | 35543 | 531 | 20241001 | 20261112 | 39.0 | 1044 | 0 | 0 |
| TSLA | 243808 | 531 | 20241001 | 20261112 | 299.0 | 4418 | 10 | 10 |

Timestamps: usable at created_at + 120 s (ASSUMED). Measured created_at minus trade end_time = median 7 s (that is alert creation lag, not delivery lag). Forward register: running (pid in ps: fwd_alerts.py), no RTH session recorded yet (first session Mon 2026-11-16 09:25 ET); measured delivery lag (our arrival minus created_at) will be reported here.

Tape proxies (same features from every trade >= $50k, /uw/tape_big, since 2025-07-21; multileg removed; UW sweep tag is empty in this file, so sweep/block cannot be proxied; ask/bid side from the tape tag; no OI so no opening proxy): groups T_SPX T_NDX T_QQQ T_SPY T_IWM T_MEGA7 T_NVDA T_TSLA run through the identical screen (window OLDER is only 2025-07..2026-05 for them).
