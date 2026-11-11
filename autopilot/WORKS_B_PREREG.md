# WORKS_B_PREREG - T-WORKS part B (W-B): causal chop/trend flag and regime-conditional exits (written before any scoring; shadow only, no PASS claims)

Base: LPB_BASE exact (live panel: P7 day cap 8,400, P7 7/4/4, P7 cut 40/5x/w5/p3), ROLL-fixed engine, S1b. Reference stacks: LPB_BASE and JN04RM. Windows: L1M, L3M, L6M, HOLD (202511-202604), PRE (202402-202506), X' (202304-202401); bi-weekly WF (26 weeks training) vs LPB_BASE and vs JN04RM; rule 2a floors as in DS3_C2_REGIME.md. Drawdown first (stack maxDD cut), then mean; equal-mean view reported.

## B1 flags (all computed causally at the SIGNAL second; code/th_works_b/wb_flags.py)
- LOT: lot_cold = P7 Calmar over the previous 10 weekdays < 1 (replicates JN04RM mLOT on 4,754 matched P7 signals: 100%); also thresholds 0.5 and 2, and 5/20-day windows.
- REG: atr_rel (5-min ATR vs 20-day norm; matches JN04RM mlog to 0.02 on 99.3%): hot = atr_rel >= {1.1, 1.3, 1.5, 1.8}; dead = atr_rel <= {0.6, 0.9}.
- ER: 5-min efficiency ratio over the last 20 bars, trend = er20 >= {0.25, 0.30, 0.35, 0.40}.
- STACK: Calmar of the all-book LPB daily P&L over 5/10/20 weekdays, cold = Calmar < 1 (and < 0).
- Family H: F_ER (day ER >= 0.30), F_ER2 (6.5 h ER >= 0.25), F_PRIOR (prior-day |c-o|/(h-l) >= 0.6).
- Combinations: ER and not-LOT-cold; ER or F_ER; hot and ER.
Separation score: (a) share of flagged-trend P7 signals in the live week 11-02..05 vs the distribution over all 43-month weeks (percentile of the live week); (b) per-trade P7 cut regret = pnl(no cut) - pnl(LPB cut) from the exact runs WB_C_NONE vs LPB_BASE matched on (book, signal second): mean regret by flag state, block bootstrap over weeks; (c) persistence: P(same state at the next P7 signal), median run length (signals), day-to-day agreement.

## B2 conditional loss cut (exact, one set per job via SZ-CORE queue; hook code/th_works_b/wb_hooks.py)
Cut cells: C0 = 40/5x/w5/p3 (LPB_BASE), V2 = 45/5x/w5/p10, C45P5 = 45/5x/w5/p5, A50 = 50/5x/w5/p3, NONE. Unconditional exact sets WB_C_NONE, WB_C_V2, WB_C_45P5, WB_C_A50 (set JSON = LPB_BASE with the P7 cut cell replaced, nothing else). Per-flag-per-threshold conditional screen = per-trade choice between the matched exact unconditional runs (ranking only; path divergence reported); the exact conditional hook sets are then run for the top cells of each flag family plus the reverse control. A cell may be promoted only on the drawdown-first rule above (L6M and PRE stack maxDD not worse than LPB_BASE, HOLD not deeper than -5%), never on a single window.
Live replay: every live cut and target of the frozen week 11-01..05 replayed with the flag state at the entry second (flag inputs: jn04_p7perf.csv shadow, frozen live file P&L, NQ 1-min state file). 11-09..11 live data: not on the box.

## B3 conditional profit protection
T-TRAIL-L2 lines (DS3_TRAIL_L2.md, best exact cell per book) switched ON only in chop/cold (and the reverse control), on the PTR engine hook (flag check per line). First-order screen on the LPB_BASE PTR cache (ptr_fo), exact for the top cells; P7 first, then K7/M7/U7. Caught/clipped counts per regime.

## B4/B5 near-target and brackets
Near-target take (within 3 pts = 12 ticks, 5 s stall) and the retarget family (NT kernel, code/th_exh_hi/nt_kern.py) scored by regime, with retarget on; bracket stop/target {60/60, 60/45, 60/90} by regime per book x session (first-order, then exact top cells).

Multiplicity: every cell reported, family size counted, placebo (random flag with the same on-rate, B=200) for the top cell of each family. Pages: DS3_WORKS_B.md every 4 h from 18:00Z, final by 2026-11-12 12:00Z.
