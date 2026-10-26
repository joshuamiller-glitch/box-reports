# REPORT B12 - multi-hour time-exit holds (2/4/6 h, no bracket) of the pair's own ST/HM signals, separate book
**Verdict: NO. FOUND 0, LEAD 0. Best clean additive uplift at 20% share is +0.063 (HM 4h reverse) against the +0.10 gate; H1 -0.05, H2 +0.01; 2013-2026 standalone weekly Sharpe of the three carried cells is -0.44 / -0.41 / -0.08.**
Runtime about 15 s (1-minute engine, pool of 5). Pre-registered in PREREG_AUTOPILOT.md (section B12) before the first run.

## Protocol
- Engine: 1-minute NQ long series (series_NQ_long.npz, back-adjusted), d1_f4_core style: signals C.signals (ST 120/2.0 + EMA200, HM 20/55 close-VWAP + EMA200, same entry-block windows), entry at next-bar open, exit at the open of the first bar >= entry+H or the 16:55 ET forced flat (no overnight), NO stop or target, no day/week locks. 1-second engine not used (no tick data on box). Fidelity: 91.2% of live ST entries (7,641) and 91.8% of live HM entries (5,448) in ROWS_corrected_engine.parquet are matched by an engine signal within 1 minute; with no intrabar stop the 1-minute fill model is much less sensitive than for the bracketed pair, but the signal timing caveat remains.
- Fill model: entry/exit at bar open, 8 NQ lots (pair size), slippage 1 tick/side (2 ticks/side for the slippage test), commission $34.88 per 8-lot round trip. Sleeve scaled by one constant so its CLEAN weekly sd equals the pair's clean weekly sd (additive: P + s*S; constant-risk: (1-s)P + sS).
- Pair: B.Cfg(wk_floor=8, wk_loss_pb=None) from ROWS_corrected_engine.parquet via t3_score (clean process). Spans clean 2023-08..2025-07, H1 to 2026-02-06, H2 to 2026-10-13.
- Grid: 18 cells = books {ST, HM, ST+HM} x H {2,4,6} h x re-entry {R0 ignore while in trade, R1 reverse on opposite signal}. Selection on clean only (rank by 20% additive uplift, clean standalone Sharpe > 0), top 3 carried; H1/H2 read once for those 3.

## Stage 1 (clean only, all 18 cells; additive 20% uplift of weekly Sharpe)
HM H4 R1 +0.063; HM H6 R1 +0.022; HM H4 R0 +0.002; HM H2 R1 -0.010; every ST and ST+HM cell negative (-0.03 to -0.24). No cell reaches +0.10 on clean, so no cell can pass; the three carried cells were nevertheless scored in full as pre-registered.

## Stage 2 (top 3, read once)
| cell | trades pair window | uplift@20% clean / H1 / H2 / all | uplift@20% 2x slip (all) | standalone Sharpe clean / H1 / H2 / all | 2013-26 standalone | wd corr | corr all | own random-entry null p95 (rank) | boot 90% CI @20% | plateau (H x0.75 / x1.25 all-in uplift) | constant-risk verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| HM H4 R1 | 7,107 | +0.063 / -0.050 / +0.010 / +0.025 | -0.035 | 1.02 / 0.36 / 0.53 / 0.78 | -0.44 | -0.65 | +0.26 | 0.50 (0.99) | [-0.15, +0.19] | -0.029 / -0.010 | NO |
| HM H6 R1 | 6,574 | +0.022 / -0.054 / -0.156 / -0.036 | -0.090 | 0.80 / 0.38 / 0.07 / 0.53 | -0.41 | -0.62 | +0.28 | 0.49 (0.96) | [-0.22, +0.15] | +0.042 / -0.033 | NO |
| HM H4 R0 | 3,727 | +0.002 / -0.469 / -0.284 / -0.123 | -0.158 | 0.67 / -0.42 / 0.45 / 0.38 | -0.08 | -0.04 | +0.36 | 0.54 (0.90) | [-0.35, +0.09] | -0.087 / -0.237 | NO |

Uplifts at 10/30/50% follow the same pattern (HM H4 R1: clean +0.04/+0.08/+0.08, H1 -0.01/-0.12/-0.32, H2 +0.02/-0.03/-0.17); all-in worst week is worse by +2.7% to +34% (HM H4 R1) and +27% to +170% (HM H4 R0), i.e. above the risk share for the R0 cell. The circular-shift null rank is 0.0 for every cell and share (reported, not gating). Standalone, the sleeves have large drawdowns (HM H4 R1 all-in maxDD $571k, worst week -$335k at pair-equivalent size) and a negative 2013-2026 weekly Sharpe: the standalone pair-window Sharpe is regime luck of 2023-2026 (same finding as C3-H2).

## Insurance metric set (HM H4 R1, all-in, vs pair; pair = Sharpe 1.86, MAR 9.59, CVaR5 -$79.2k, CVaR10 -$78.2k, maxDD $280k, worst week -$82.5k, Sortino 3.63, 42.9% neg weeks)
- Additive 20%: Sharpe 1.88, Sortino 3.89, MAR 9.43, CVaR5 -$83.2k, CVaR10 -$78.9k, maxDD $311k, worst week -$91.2k, neg weeks 42.3%. Clean 1.52 / H1 2.78 / H2 2.30 (pair clean 1.46 / H1 2.83 / H2 2.30).
- Constant-risk 20%: Sharpe 1.88, net -10.7%, CVaR5 +14.5% better, worst week +8.4% better, maxDD 8.8% better; clean 1.53 / H1 2.74 / H2 2.29; INSURANCE verdict NO (needs >= 20% improvement).
- Full per-span tables for all three cells: outputs/autopilot/b12/stage2_top3.csv.

## Gate checklist (HM H4 R1, headline 20%)
1. Pre-registered before first run: PASS. 2. Clean-only selection, H1/H2 read once: PASS (process). 3. Uplift >= +0.10 on clean/H1/H2: FAIL (+0.063 / -0.050 / +0.010). 4. Own random-entry null p95: standalone 0.78 > 0.50 pass, but bootstrap lower bound -0.15: FAIL. 5. Plateau 0/2, 2x slippage uplift -0.035: FAIL. 6. Worst-decile corr -0.65 (<= +0.30): PASS (it is negative, but the sleeve's worst-decile mean is only +$3.5k on 17 weeks and it does not offset a loss). 7. Executable: yes in principle (NT8 strategy: take the pair's ST/HM flip signals, market entry, time exit at 4 h or 16:55 ET, no stop; margin about the same as 8 NQ lots per open book); moot given 3-5.
Overall: NO.

## Executability and margin
NinjaTrader Brokerage via Rithmic, NQ, 8 lots per open book (unprotected, no stop, so intraday risk is unbounded by the bracket; a 4 h hold of 8 lots moves about $0.8k per NQ point per 100 pts... i.e. a 100-pt move is $16k); margin about the pair's. Would need a new NT8 strategy or a DualStrat mode with a time-exit instead of the bracket. Not recommended.

## Caveats
1-minute engine (91% of live entries matched within 1 minute); 18-cell grid, 3 carried; plateau tested on hold only (+-25%), not on the signal parameters.
DONE B12
