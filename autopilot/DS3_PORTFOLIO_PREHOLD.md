# DS3_PORTFOLIO_PREHOLD - T-PORTFOLIO pre-holdout text (D3PF, 2026-10-27). PRE window 2024-02-01..2025-06-30 only; written before the holdout look.
Prereg sha256 e97cd0164994d174319bf437adcc29a6334972123bc1e4233e996b8ea4223e23 (l2vast/ds3/prereg/T-PORTFOLIO_prereg.md). Frozen PRE solves (exact MILP, gap <= 0.1%, local-search cross-check): l2vast/ds3/out/portfolio/pre_<variant>.json.

- A_cap30: {KB 14, MV 2, DN 14} PRE mean 56163, SD 116970, maxDD 316505, worst -200968
- B_cap30: {KB 6, SM 2, MV 2, MA 3, DN 4, CR_cons 6, B3 1, RSI2T 3} PRE mean 30019, SD 51337, maxDD 105088, worst -71934
- A_cap20: {KB 14, DN 6} PRE mean 38833, SD 83119, maxDD 271092, worst -127464
- B_cap20: {KB 5, SM 1, MV 2, DN 9, CR_cons 3} PRE mean 30313, SD 61640, maxDD 128880, worst -105340

Comparators PRE: DS2_10_10_7 mean 23675 maxDD 537851, DS2_plus_KB10_SM10 mean 52717 maxDD 591503

These PRE-solved allocations are the ones tested once on HOLD (2025-07-01..2026-10-16). Variants (WT, PE2, CR_map, EM, cap50) frozen in the same directory. Gates G1-G6 as in the prereg.
