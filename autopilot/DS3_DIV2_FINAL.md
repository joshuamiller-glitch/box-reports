# DS3_DIV2_FINAL - T-DIVERSIFY-2 (chosen by what the stack lacks) - main, from D3D2A/B/C/D/E/F (2026-10-28)
No CONFIRMED rule; section H (portfolio solve, Sim specs) therefore has nothing to assemble. The stack's own 20 worst weeks lose -$3.53M (2023-04..2026-02-06; audit window to 2026-10-16: -$3.74M).

## The audit line (A)
The stack loses on 438 of 917 days (48%), 64% of losing-day $ on range days, in 12 of 46 half-hour entry slots (03:30, 05:00, 05:30, 07:00, 08:00, 11:30, 12:00, 13:00, 14:30, 16:30, 22:00, 23:30 ET), and is idle only in its own entry-blocked slots. Worst 20 weeks are chop weeks; all books but SM lose together.

## One verdict line per family
- A audit: done (DS3_DIV2_A_AUDIT.md). G internals: NEEDS (intraday VIX, NYSE TICK/ADD/VOLD not on disk; NT8 forward recording / CBOE DataShop).
- B pairs (47 cells): 47 DEAD, 0 replicate; mean reversion loses its cost (NQ/ES -$3.7k/wk), laggard catch-up has the wrong sign. Post-hoc lead (needs own prereg): relative-strength continuation 10:00/11:30.
- C scheduled events (60 cells): 1 PASS / 1 CANDIDATE / 1 LEAD / 57 DEAD. PASS = NQ fade of first 5-min move after CPI/NFP 08:30 (+$133/trade, n=53, mean < MDE 172, best-of-24 p 0.43, ~21 trades/yr, loses in stack's worst weeks) - not CONFIRMED; lead for a fresh prereg on post-2026-02-06 data.
- D stack-state books (16 cells): 16 DEAD. Re-entry does not rescue Trade Health loss side.
- E MBO seven: corr to stack ~0 (-0.09..+0.10), no edge established (all means < MDE), hedge not shown (null p 0.21-0.69).
- F night session (12 cells): 12 DEAD. Lead NQ AS_SHORT (short Tokyo open 15 min) positive every window but inside MDE; stack Sharpe +0.056, flips negative at 2x cost.

## The one number: $ in the stack's 20 worst weeks at 20% risk
No CONFIRMED rule, so the honest figure is $0 from confirmed rules. Best cells regardless of verdict (all best-of-N picks, upper-end): MBO H300000_cd_extratrees_Q575 +$129k (p 0.21); NQ AS_SHORT +$135k; D1_C60 +$127.8k (loses money overall). Against the stack's -$3.3M..-$3.5M, an offset of ~4%.
