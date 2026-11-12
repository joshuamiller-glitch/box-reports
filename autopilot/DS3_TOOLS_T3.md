# DS3_TOOLS_T3 — T-TOOLS families T3 internals, T4 news timestamps, T5 other CME data (W-TL3). Page 1, 2026-11-12 ~20:00Z. Shadow only, no PASS claim.
Standing rule (lead relay of user addendum 19:35Z): best feature per use with honest evidence; a null family is logged and the next hypothesis starts at once (autopilot/T3_HYPOTHESIS_LOG.md, append-only); placebo / family null / trend-week clause stay on. Spend: nothing bought by W-TL3; ceiling $400 of the $1,500; the lead executes purchases (code/th_tools/buy_t345.py: `quote` | `buy <ITEM_ID>`).

## 0. Headline
- **Best feature so far (T5 free proxy, protection/entry skip): NQ mid-size aggressor flow.** At a P7 signal, signed volume (in the trade direction) of 3-9-lot prints over the previous 30 s in the top decile (>= 56 contracts, threshold from pre-2025-11 data only) -> skip the entry. First-order on 5,011 taken P7 trades: L6M +$585/wk, HOLD +$632, GAP +$277, PRE +$165 (all four positive); in the 20 best weeks -$431/wk, in the 20 worst weeks +$1,262/wk; 425 trades skipped (8.5%); flagged trades average -$63.5 per lot vs +$75.6 for the rest; frozen live week: 0 of 53 P7 trades flagged (no trend-week cost there). At the user's x1.75 lots multiply the dollars by 1.75 (about +$1.0k/wk L6M).
- **Strength: WEAK LEAD, not a result.** 9 of 126 cells are positive in L6M+HOLD+PRE vs 0.8 on average under within-month permutation (p95 3, max 5, 100 draws) so the family is above its null; but the best cell's worst-window gain (+$223/wk) is above the null best only at p = 0.085 (200 draws), it is concentrated in NY-AM (net of flagged -$27.9k L6M / -$40.3k HOLD / -$17.2k PRE), P7 only, first-order (first-order screens have repeatedly overstated vs exact), P7 state cut assumed on (live cut is not firing). Not yet exact, no scorecard, no WF: next in the queue (section 5).
- T3: 4-index-futures breadth proxy is a null family (W-S S2); official TICK/ADD/VOLD history was not found for sale; whole-market breadth quoted, not bought (not justified yet).
- T4: no cheap second-level headline sample confirmed; nothing bought.
- T5: statistics (OI, settlement, volume) quoted at $0.14 for NQ+ES L12M (recommend buy); MNQ/MES trades quoted; CVOL and block trades are CME DataMine only (user decision).

## 1. T3 INTERNALS
**Official series.** TICK/ADD/VOLD are computed exchange indices; Databento does not sell them (S2 note in DS3_SCREENS.md). Candidates found by search, none verified for $ADD/$VOLD: Barchart (premium membership advertises $TICK 1-minute history download; ADD/VOLD not confirmed; subscription = needs the user), FirstRate Data (NYSE Composite 1-min from 2008 = index price only), Tick Data / Intrinio / Nasdaq equity tick history (raw prints, a build project). No purchase made; a recurring membership is outside the authority.
**Stand-in options and cost (Databento quotes, GLBX/DBEQ, 2026-05-01..2026-11-11 unless stated):** DBEQ.BASIC whole-market ohlcv-1m L6M $339.31 (10.4 GB), L3M $177.07 (5.4 GB); one month (Oct 2026): DBEQ.BASIC $74.15, XNAS.BASIC $48.89, XNYS.PILLAR $16.30 (single-venue prints, not whole market). Within the $400 ceiling only L6M DBEQ ($339) or L3M ($177) fits and would leave almost nothing for T4/T5.
**Evidence on proxies already owned:** four-index-futures breadth (NQ ES RTY YM, W-S S2, 5,442 cells): entry skip best-cell family p 0.70; loss-cut confirm 61 cells beat the live rule in every window vs chance 62.6 (p95 76), best-cell p 0.02 but count at chance; early cut and near-zone null; best nominal cell s2_brd30 <= 0 on all books L6M cut 27.7% / +$2,407/wk, HOLD +0.7% / +$596, PRE 11.2% / +$639, X' -0.6% / +$39, worst-20 weeks +$2,179/wk, best-20 weeks +$133/wk: noise-level by the family test. ETF/megacap breadth (T-CROSS L6M package on disk) is not scored yet by W-S.
**Closeness of the stand-in to the official series:** cannot be measured: the official TICK/ADD history is not on the box; the 4-futures vote is a PROXY only.
**Recommendation (T3):** do NOT buy whole-market bars yet. Score the owned ETF/megacap breadth first (H2 in the log); buy L3M DBEQ ($177) only if that proxy is non-null.

## 2. T4 NEWS TIMESTAMPS
Found: Benzinga historical news (Benzinga says its archive is 84 TB); Alpaca's news API (Benzinga-sourced per Alpaca's material) returns `created_at` as RFC-3339 with second precision (docs example `2026-10-21T15:02:10Z`), `start` accepts nanosecond-precision strings; history start date and plan (free vs paid) are NOT stated in the docs. Benzinga direct pricing is not public (sales contact). No sample was obtained here and nothing was bought. The scheduled-release calendar (DISCOVER_CALENDAR.csv) remains the only real-time-labelled event set; the price-based shock detector (W-S S4) is a null family (best-cell p 0.35 loss-cut confirm, 0.88 early cut). Next: user-side check of an Alpaca news sample (free key) or a Benzinga trial; one month would suffice to compare shock labels.

## 3. T5 OTHER CME DATA
| item | source | quote | note |
|--|--|--|--|
| NQ + ES statistics (settlement, open interest, cleared volume) L12M | Databento GLBX statistics | $0.10 + $0.04 | recommend buy; daily OI change feature |
| NQ trades L6M | GLBX trades | $68.75 | NQ prints already in the owned state base from MBP-10: not needed |
| ES trades L6M / L3M | GLBX trades | $77.22 / $38.92 | ES state base has no print sizes |
| MES trades L6M / L3M | GLBX trades | $64.79 / $30.49 (about $10 per month) | micro flow |
| MNQ trades L6M / L3M / L1M | GLBX trades | $229.10 / $117.77 / $60.87 | retail-size flow vs NQ |
| CVOL EOD (up to 9 y) and intraday (15 s, from 2022-08-08) | CME DataMine | price on request | not Databento; user decision |
| CME block trades (from 2008) | CME DataMine | price on request | not Databento; user decision |
Free proxy done first (H1): the small-lot vs large-lot split of NQ's own prints (what MNQ/MES would add is retail-size flow from a separate book). Lead: the cheapest useful next buy is MNQ + MES L1M (about $71) to test whether MNQ's own aggressor flow adds to the NQ mid-size flow signal, plus the $0.14 statistics; do not buy MNQ L6M ($229) before that pilot.

## 4. Event / feature tables
Top cells by worst-window gain (first-order skip, P7, $ per week of the window, thresholds from pre-2025-11; best/worst-20 = effect in the 20 best / worst P7 weeks of the whole history, $ per week):
| feature | thr pct | n skipped | L6M | HOLD | GAP | PRE | best-20 wk | worst-20 wk |
|--|--|--|--|--|--|--|--|--|
| d_small_300 | p90 | 483 | +1665 | +223 | +253 | +261 | -3277 | +1447 |
| vol_60 | p90 | 384 | +336 | +396 | +1665 | +218 | -456 | +1888 |
| **d_mid_30** | **p90** | **425** | **+585** | **+632** | **+277** | **+165** | **-431** | **+1262** |
| vol_30 | p90 | 400 | +235 | +141 | +1476 | +250 | -739 | +1869 |
| d_mid_60 | p80 | 896 | +1242 | +1169 | +830 | +52 | -1463 | +2682 |
Family: 126 cells (21 features x 6 thresholds), 9 pass L6M+HOLD+PRE; null (100 within-month permutations) mean 0.8, p95 3, max 5; best-cell p 0.085. Sanity: signed flow vs trade P&L correlation -0.014 (flow is not a linear predictor; the effect is the extreme tail). Chance expectation of passes: 0.8 of 126.
NY-AM carries the effect; Asia flagged 27 trades (net +, i.e. skipping them LOST money in L6M/HOLD: +$14.3k/+$18.2k), London 39.

## 5. What runs next
1. Exact set `TL3_P7_MIDFLOW30_P90` on JN05W2 and JN05W2_NOCUT (hook = outermost entry skip, W-F1 pattern) L6M then HOLD/GAP/PRE/X', WF, scorecard a-e, acceptance, trend-week clause; only if the lead wants it (an exact queue slot at the TOOLS tag, quota 6, now in PRIORITY.txt after GAPS; backup PRIORITY.txt.bak_tl3).
2. Same feature on K7/U7/M7 and by session; size-class thresholds 2/10 vs 3/9 variants; combination with the P7 re-entry context tag (fresh/rechase).
3. T3: score ETF/megacap breadth (owned) first. T4: user sample. T5: statistics + MNQ/MES pilot when the lead buys.

## 6. T6 live path (candidate only)
- Feed: none new. DS7 already receives every NQ print in OnMarketData (price, size, bid/ask aggressor side).
- Sidecar/feature name: `nq_midflow30` = sum over prints in the previous 30 s of aggressor_sign * size for prints of 3-9 contracts; update on every print (rolling sum); read at the signal second; skip P7 when (side * nq_midflow30) >= 56 (to be re-fit bi-weekly on trailing 26 weeks, rule 2a candidate).
- Monthly cost: $0. Break-even: any positive effect; honest expected value at the user's lots first-order +$1.0k/wk L6M, overstated by first-order screens, evidence weak (p 0.085).
- D7 must read: per-print size class counters (3 rolling sums) and the signed rule; a v1.9 spec with 5 worked rows follows if the exact set survives.

## 7. Update ~20:40Z (lead's follow-up order)
- **Exact stage launched (tl_drive.py nohup):** identity gate TL3_ID99 202610 (must equal JN05W2: 598 trades, net 25,943.82), then L6M chains (3+3 months per set) for TL3/TL3N/TL3J_M30_S, TL3_M30_H, M30_ALL, M10_S, M120_S, S30_S (1-2 lots), L30_S (10-29), X30_S (>=10), M30_KUM and the NOCUT/J identity sets; tag TOOLS (quota 6; regex TL[123][NJK]?_). Score: `python3 -I code/th_nextf/score_nf.py --ref JN05W2 TL3_M30_S ...` (trend-week clause, WF, scorecard, acceptance on the shared tools). No exact rows yet. Placebo / family null at the exact stage = the within-month permutation of section 4 plus the variants' count above.
- **MNQ/MES pilot items added** to buy_t345.py: T5_MNQ_TRADES_L1M $40.39, T5_MES_TRADES_L1M $10.12 (2026-10-01..11-01, together $50.51). Run when the exact mid-flow shows life.
- **NQ statistics regime flag (owned L12M):** NULL on 12 months (0 of 36 cells positive in L6M and HOLD; permutation null mean 0.1, p95 1). History before 2025-11 is not owned: T5_NQ_STATS_PRE (2023-04..2025-10, quote $0.0x) lets four windows run: recommended.
- **T4 access:** Alpaca and Benzinga news endpoints answer 401 without a key; a free Alpaca key is a user account action; nothing pulled. Non-blocking Barchart note logged in MORNING_FLAGS.md.
