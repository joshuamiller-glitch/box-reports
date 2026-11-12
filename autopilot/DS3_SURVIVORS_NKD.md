# DS3_SURVIVORS_NKD - NKD top-of-book imbalance near-zone take (W-CX2, 2026-11-12; Shadow only, no PASS claim)
Prereg: autopilot/NKD_SURVIVOR_PREREG.md (sha line in DECISIONS.md). Rule: at the first second a P7/U7 trade's mid excursion reaches 80% of target, take at market (mid - 1.2 pt) when NKD bid-size share against the trade (side*(bsz/(bsz+asz)-0.5)) <= 0.

## 1. First-order history test (frame: LPB_BASE zone trades, take80 vs live; per week; windows L6M 2026-05-12..10-30, HOLD 2025-11-11..2026-10-30, GAP 2025-07..10, PRE 2024-02..2025-06, X' 2023-04..2024-01)
Data fault found and fixed first: the chain2 history test (00:08Z) read an NKD file that held only 2023-04..2024-03 in sec/, so L6M cells were empty (n 0) and HOLD was partial. The L6M-package NKD file (2026-05-01..11-10) was re-ingested into sec_l6m/ and the history test rerun (code/th_cross/cx_nkd_hist2.py; per-second array /mnt/l2/l2vast/_th_cross/nkd_imb_sec.npy). Earlier chain2 PRE/X'/HOLD(partial) lines in DS3_CROSS.md stand for PRE/X' only; its HOLD numbers (+1,609) are superseded.

| cell gain, $/wk | L6M | HOLD | GAP | PRE | X' |
|---|---|---|---|---|---|
| P7+U7 nkd_imb<=0 take | +5,251 | +4,034 | **-3,437** | +445 | -1,080 |
| placebo (perm within book-month) mean / q95 | +1,363 / +3,230 | +1,290 / +2,562 | -1,886 / -586 | +654 / +1,640 | -705 / +134 |
| P7 alone | +4,464 | +3,268 | -2,354 | +289 | -519 |
| U7 alone | +786 | +767 | -1,084 | +156 | -562 |
| K7+M7 control | -1,291 | -968 | -1,480 | -1,082 | +3 |
| family max-stat, best of 30 cells: actual / q95 / p | +5,251 / +3,583 / 0.000 | +4,034 / +2,680 / 0.000 | +146 / +1,035 / 0.50 | +1,427 / +1,924 / 0.54 | +288 / +991 / 0.77 |

Bi-weekly WF (30 cells, trailing 52 weeks, OOS from 2024-07, 61 refits): total +$1,286/wk, but by period: 2024-07..2025-06 +516/wk (27 refits), **GAP 2025-07..10 -2,228/wk (8 refits)**, 2025-11..2026-04 +2,095/wk, L6M +4,237/wk.
Trader test P7+U7 (first-order): L6M 52 give-backs converted (+$340k), 344 fills clipped (-$203k), net +$137k/26 wk; HOLD net +$210k; GAP net -$60k (17 wk); PRE net +$33k (74 wk).

Reading: the lead is real inside 2025-11..2026-10 (placebo and family p 0.000 on L6M and HOLD) and reverses sign in GAP (2025-07..10, significantly worse than placebo) and is null/negative before. It is a RECENT-ONLY pattern that fails PRE/X'/GAP on the standing tolerance rule; the 2023-24 and mid-2025 history do not support it. Family correction: 1 cell of 336 (screen) / best of 30 (history): survives only on the two recent windows.
