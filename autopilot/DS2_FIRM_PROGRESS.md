# DS2-FIRM v2 progress (trackFIRM) - append-only
2026-10-22T16:55Z START v2 (v1 void/unscored; nothing was frozen under v1). Built firmlib.py (l2vast/pairP2/firm/): regenerates trades on the 1-s path with per-signal stop/target (exact: reproduces ROWS_bench3 row-for-row), engine port reproduces the DS2 benchmark exactly (WF 24.8k/104.2k/399.4k/-137.1k at $4.36). CBOE VXN/VIX1D/VIX/VIX3M/VVIX csv downloaded (free).
ETA (first estimate): PREREG_DS2_FIRM_V2.md frozen ~18:00Z; Part 1 forecast table ~19:30Z; Parts 2-3 scored ~23:00Z; Parts 4-6 after 00:40Z (MORNING will carry Parts 1-3 + partial).

## interim 2026-10-22T17:13Z
## DS2-FIRM (user top priority; interim table every 2 h — maintained by trackFIRM between these markers)
INTERIM 1 (17:35Z). v2 prereg FROZEN (l2vast/PREREG_DS2_FIRM_V2.md + ADDENDUM A1; sha in DECISIONS). Part 1 forecast table DONE (43,552 instants, 5 targets x 9 models, WF rank corr log-RV 2h/4h/rest/session/day: ridge .90/.89/.87/.88/.79, LGB .91/.89/.87/.89/.78, HAR-intraday .90, prior .75, ATR20 .61). Part 2 scan DONE on APPROXIMATE P9 execution (417 regen row sets, 4,676 cells; regenerated on the 1-s path = exact; P9 slippage/flips mapped by resampling the 60-pt P9 deltas = approximation, direct L2 replay validation of firm cell + fixed40 running, months 2024-06/2026-09).
Benchmark @$4.84 (corrected P9, 14/14, tick clock): WF 24,975/wk SD 104.5k maxDD 401k worst -137k | L8W 34,191/wk SD 109k.
FIRST LOOK (approx, noisy, selection NOT yet nulled): firm cell (RIDGE/T2H/k=1.0/clamp, R$16.8k, cap 28) WF 7.2k/wk SD 104k maxDD 836k (size-cost surface bites: avg 17 lots, 24% of trades at 28 lots; without size cost 14.6k/wk) -> does NOT beat benchmark. Size-only control fixed-60 with 8 lots (R$10k): WF 28.4k SD 86k maxDD 376k L8W 42k (lock interplay: smaller size = locks bind less). Best vol-bracket cells at mean >= benchmark: ATR20/T2H/k1.0 unclamped R$12k cap14: WF 35.2k SD 91.7k maxDD ~(see report) -- single-look, expect it to die in nulls/replay.
ETA: Part 3 extras (3.3-3.6, 6.4, cost variants) ~19:00Z; nulls on finalists ~20:30Z; replay validation 2 months ~19:30Z; Parts 1-3 report REPORT_DS2_FIRM.md ~22:30Z (before 00:40Z MORNING); Parts 4-6 follow (meta-label ~02:00Z, portfolio ~04:00Z).

## interim 2026-10-22T17:31Z
## DS2-FIRM (user top priority; interim every 2 h — trackFIRM)
INTERIM 2 (17:45Z, 32 cores shared with 7 L2 replay workers + 10 null workers). Parts 1 (forecasts, trunc check 0 mismatches) and 2/3 full prereg grid already SCORED (4,671 cells + p3b 43 + p4 meta 9; speed message arrived after). Coarse 45-cell view below. HEADLINE: no coarse cell reaches the benchmark WF mean (25.0k/wk); vol-normalised brackets with R$ sizing lower the mean (size cost surface + tighter stops) and do not lower SD at equal mean; size-only control (fixed 60 pt, 8 lots) WF 28.4k/SD 86k/maxDD 376k/L8W 42k beats it (lock interplay). Best ATR20/prior-RV brackets at 14 lots: WF 30-36k SD 90-110k single-look, nulls pending (200 worlds, running). Approximation caveat: P9 execution mapped by resampled deltas; direct L2 replay validation (daily corr replay vs approx 0.98-0.99 in 2024-06) in progress for 8 months.
COARSE k x R$ TABLE (INTERIM 2, approx P9 execution; clamp [25,150], cap 28, 14/14-scale $/wk; WF mean/SD/maxDD/worst | L8W mean/SD/maxDD | SD-at-equal-WF-mean (scaled) )
BENCH @4.84: WF 25.0k/104.5k/401k/-137k | L8W 34.2k/109.4k/267k
-- forecast session-open ridge (horizon session):
k0.8 R$12.0k: WF 17.7/92/539/-138 | L8W 32.3/102/273 | scaled SD 130k (avg lots 9)
k0.8 R$16.8k: WF 18.5/109/703/-141 | L8W 13.6/108/285 | scaled SD 148k (avg lots 13)
k0.8 R$21.0k: WF 16.3/114/628/-144 | L8W 7.6/103/257 | scaled SD 175k (avg lots 17)
k1.0 R$12.0k: WF 8.8/80/561/-136 | L8W -2.6/98/327 | scaled SD 226k (avg lots 7)
k1.0 R$16.8k: WF 11.1/97/680/-137 | L8W -9.3/91/336 | scaled SD 217k (avg lots 11)
k1.0 R$21.0k: WF 15.0/104/487/-140 | L8W -5.9/85/288 | scaled SD 172k (avg lots 14)
k1.25 R$12.0k: WF 8.6/72/409/-135 | L8W 1.8/103/301 | scaled SD 210k (avg lots 6)
k1.25 R$16.8k: WF 12.8/90/643/-142 | L8W -5.1/121/352 | scaled SD 175k (avg lots 9)
k1.25 R$21.0k: WF 10.9/97/568/-137 | L8W -15.3/101/358 | scaled SD 222k (avg lots 11)
k1.5 R$12.0k: WF 6.3/73/552/-135 | L8W -22.8/85/327 | scaled SD 291k (avg lots 5)
k1.5 R$16.8k: WF 8.0/89/820/-137 | L8W -23.5/106/397 | scaled SD 279k (avg lots 8)
k1.5 R$21.0k: WF 6.4/101/941/-139 | L8W -11.5/116/344 | scaled SD 392k (avg lots 10)
k2.0 R$12.0k: WF -0.2/71/1164/-135 | L8W -23.1/85/323 | scaled SD nank (avg lots 4)
k2.0 R$16.8k: WF -1.4/86/1392/-140 | L8W -21.9/113/386 | scaled SD nank (avg lots 7)
k2.0 R$21.0k: WF 0.2/94/1560/-140 | L8W -19.5/104/315 | scaled SD 12779k (avg lots 8)
-- forecast prior-session RV (horizon session):
k0.8 R$12.0k: WF 17.1/89/489/-138 | L8W 33.9/97/300 | scaled SD 129k (avg lots 10)
k0.8 R$16.8k: WF 22.6/100/439/-141 | L8W 16.0/90/327 | scaled SD 111k (avg lots 14)
k0.8 R$21.0k: WF 21.3/107/611/-143 | L8W 21.4/105/333 | scaled SD 125k (avg lots 18)
k1.0 R$12.0k: WF 12.2/80/517/-136 | L8W 45.1/101/280 | scaled SD 165k (avg lots 8)
k1.0 R$16.8k: WF 7.4/96/576/-137 | L8W 10.1/116/339 | scaled SD 321k (avg lots 12)
k1.0 R$21.0k: WF 7.4/104/700/-142 | L8W -1.6/108/263 | scaled SD 353k (avg lots 15)
k1.25 R$12.0k: WF 6.4/76/468/-140 | L8W 11.0/122/320 | scaled SD 296k (avg lots 6)
k1.25 R$16.8k: WF 5.4/95/665/-137 | L8W -4.1/109/372 | scaled SD 439k (avg lots 9)
k1.25 R$21.0k: WF 7.7/103/810/-157 | L8W 4.6/121/282 | scaled SD 334k (avg lots 12)
k1.5 R$12.0k: WF 3.8/70/593/-135 | L8W 14.2/95/224 | scaled SD 456k (avg lots 6)
k1.5 R$16.8k: WF 7.2/89/702/-143 | L8W 11.5/118/319 | scaled SD 311k (avg lots 8)
k1.5 R$21.0k: WF 0.9/98/783/-137 | L8W -17.4/93/342 | scaled SD 2681k (avg lots 10)
k2.0 R$12.0k: WF 2.5/73/921/-135 | L8W -12.9/80/254 | scaled SD 723k (avg lots 5)
k2.0 R$16.8k: WF 9.2/91/1057/-136 | L8W -4.4/101/281 | scaled SD 245k (avg lots 7)
k2.0 R$21.0k: WF 5.6/99/1374/-137 | L8W 11.2/115/227 | scaled SD 440k (avg lots 9)
-- forecast ATR20 (horizon session):
k0.8 R$12.0k: WF 16.5/87/535/-140 | L8W 32.2/123/312 | scaled SD 133k (avg lots 9)
k0.8 R$16.8k: WF 18.3/103/655/-139 | L8W 41.7/131/345 | scaled SD 140k (avg lots 14)
k0.8 R$21.0k: WF 16.2/108/717/-141 | L8W 36.7/160/365 | scaled SD 167k (avg lots 17)
k1.0 R$12.0k: WF 10.2/85/440/-136 | L8W 30.8/118/276 | scaled SD 208k (avg lots 7)
k1.0 R$16.8k: WF 17.4/98/493/-137 | L8W 21.0/103/275 | scaled SD 141k (avg lots 11)
k1.0 R$21.0k: WF 16.4/104/571/-141 | L8W 21.2/121/324 | scaled SD 159k (avg lots 14)
k1.25 R$12.0k: WF 10.6/86/482/-136 | L8W -9.9/94/365 | scaled SD 203k (avg lots 6)
k1.25 R$16.8k: WF 15.1/101/649/-147 | L8W 14.6/93/258 | scaled SD 168k (avg lots 9)
k1.25 R$21.0k: WF 16.8/113/662/-140 | L8W -2.2/65/201 | scaled SD 169k (avg lots 11)
k1.5 R$12.0k: WF 5.5/76/617/-136 | L8W -17.8/97/370 | scaled SD 347k (avg lots 5)
k1.5 R$16.8k: WF 5.0/85/843/-136 | L8W -14.5/112/388 | scaled SD 422k (avg lots 8)
k1.5 R$21.0k: WF -1.0/99/1063/-145 | L8W -9.3/103/357 | scaled SD nank (avg lots 10)
k2.0 R$12.0k: WF -0.1/70/901/-135 | L8W -29.7/84/363 | scaled SD nank (avg lots 4)
k2.0 R$16.8k: WF -0.5/85/1177/-139 | L8W -32.8/105/413 | scaled SD nank (avg lots 7)
k2.0 R$21.0k: WF 0.9/96/1094/-137 | L8W -28.3/101/346 | scaled SD 2551k (avg lots 8)ETA: replay validation 18:15Z; nulls (200 worlds x 12 cells) 18:30Z; REPORT_DS2_FIRM.md Parts 1-3 ~20:30Z; Parts 4-6 ~00:00Z. Workers now: 7 replay + 10 null + 1 meta.

## 2026-10-22T17:54:37Z status (workers: 20 nulls + 8 meta-null + 1-2 builders = ~30 cores)
Done: prereg+A1+A2 frozen; Part 1 table + truncation check; Parts 2-3 full grid on approximate P9 execution (v1), direct L2 replay of firm cell (8 months) -> delta mapping v2 (abs monthly error 0.25 pts/trade, was 0.48) -> everything re-run on v2 (p23 4,676 cells, p3b 43, p4 meta 18, p5 ES/RTY/portfolio, p52 ensemble+stagger running); null N1 200 worlds x 14 finalist cells running (v2). ETA: p52 18:05Z, nulls 18:15Z, report build 18:45Z, MORNING block update 19:00Z.

## interim 2026-10-22T18:07Z
## DS2-FIRM (user top priority) — PARTS 1-3 REPORT DELIVERED: outputs/autopilot/REPORT_DS2_FIRM.md (interim 3; direct replay of the best candidate still running)
ANSWER: vol-normalising the pair does NOT lower weekly SD at equal weekly mean. Benchmark (corrected P9 @ $4.84, WF): 25.0k/wk, SD 104.5k, maxDD 401k, worst -137k; L8W 34.2k, SD 109k.
 - FIRM CELL (ridge 2h k=1.0, constant $16.8k/trade, cap 28): WF 5.5k/wk, SD 102k, maxDD 853k (S113 size cost eats half: cost-off 12.1k; avg 19 lots, 24% of trades at 28) -> at equal mean SD 460k. Fails.
 - Weekly SD is ~100-115k for EVERY bracket/size/parameter cell (the fixed-dollar lock regime sets it); what moves is mean and maxDD.
 - Best cell at equal mean (selection-contaminated, ~4,700 cells): ATR20 2h k=1.0 unclamped, R$10k cap28: WF 34.6k/SD 89.9k/maxDD 339k, L8W 55.2k; at equal mean SD 65k, maxDD 245k, worst -100k. Passes gates a,b,c (200-world shuffled-forecast null ranks 1.00) but FAILS gate d (bootstrap 90% CI of delta-mean [-1.2k,+19.7k]) and best-of-F (rank 0.79 vs 0.99998). Not a LEAD. Direct L2 replay of this cell (45 months) running, ETA ~21:30Z.
 - Size-only control (unchanged 60 pt, 8 lots): WF 28.4k/SD 86k/DD 376k, L8W 42k but IS 4.0k: lock interplay (DS2-15/50 family), not vol normalisation.
 - Meta-labeling: AUC 0.50 (no skill). ES/RTY: pair signal negative (-16k/-20k per wk). 20-cell ensemble: SD unchanged (~104k), gain = live cell below neighbourhood mean. Stagger: no.
 - Execution caveat: non-60 brackets use P9 execution mapped from direct L2 replay deltas (8 firm-cell months replayed; abs error 0.25 pts/trade ~ +-$3k/wk); trades/brackets/locks are exact on the 1-s tape.
 - 0 cells pass gates a-d + best-of-F. No frozen leads JSON, no shadow, no DS2_VOL_SPEC.md. Resources: lead may resume other tracks now (I hold 7 replay workers / ~50 GB).

## interim 2026-10-22T18:37Z
## DS2-FIRM v3 (top priority) - V3 FIRST (posted 18:37Z); v3 prereg frozen (PREREG_DS2_FIRM_V3.md); workers: 7 replay (V7, ETA ~21:30Z) + analysis
V3 READ: with the live fixed-dollar locks the weekly mean SATURATES at ~6-8 lots (WF 21-28k/wk) and does not rise to 14 or 20 lots (25.0k, 24.6k) while maxDD grows (401k->525k at 20); trades/wk collapse 82->25 as locks fire earlier. Locks OFF the mean is ~linear (marginal +2.3k/wk per lot at 14, falling) but SD 172k/maxDD 1.04M at 14 lots. So the locks, not the signal, set the weekly SD; the marginal lot above ~8-10 earns ~0 net in WF (NY session marginal lots LOSE: NY WF P&L 8.4k@8 -> 4.3k@14 -> 2.5k@20 as fewer NY trades survive the locks).
### V3 MARGINAL-LOT CURVE (live 60-pt pair, exact P9 points, live fixed-dollar locks, S113 size cost with credit below 14 lots; both books at L lots; 14/14-scale $/wk)

**A. live locks, S113 cost (credit<14)**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 2.7k/28.2k/197.5k | 16.0k | 48.8k | 259.1k | -125.2k | 2.37 | 82 |  | 22.6k | 79.6k | 209.7k | -87.6k |
| 6 | 3.5k/44.3k/323.7k | 21.4k | 70.3k | 378.9k | -134.5k | 2.19 | 72 | +2.67k | 22.7k | 113.9k | 327.3k | -134.4k |
| 8 | 4.0k/56.5k/411.7k | 28.4k | 86.3k | 375.6k | -136.8k | 2.38 | 61 | +3.54k | 42.0k | 111.7k | 274.6k | -122.5k |
| 10 | 11.7k/70.0k/360.7k | 25.3k | 103.1k | 381.7k | -148.6k | 1.77 | 51 | -1.59k | 34.4k | 100.7k | 259.4k | -92.0k |
| 12 | 14.8k/82.3k/360.5k | 26.5k | 109.1k | 372.7k | -138.4k | 1.75 | 43 | +0.65k | 39.3k | 82.9k | 204.6k | -95.8k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.79k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**B. live locks, S113 cost, NO credit below 14**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**C. live locks, size cost OFF**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.8k/101.3k/427.3k | 21.6k | 100.7k | 363.4k | -137.5k | 1.54 | 30 | -1.70k | 19.5k | 125.6k | 324.8k | -135.5k |
| 20 | 13.0k/115.1k/375.7k | 27.2k | 108.3k | 506.3k | -145.3k | 1.81 | 25 | +1.40k | 30.4k | 118.9k | 262.4k | -134.8k |

**D. LOCKS OFF (pure signal + bracket + size), S113 cost**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 3.2k/29.0k/197.5k | 17.0k | 49.1k | 279.8k | -123.8k | 2.49 | 84 |  | 19.9k | 82.4k | 213.5k | -102.3k |
| 6 | 4.2k/43.5k/301.7k | 24.4k | 73.7k | 424.6k | -187.9k | 2.39 | 84 | +3.71k | 28.5k | 123.5k | 324.2k | -154.9k |
| 8 | 4.9k/58.0k/409.4k | 31.1k | 98.2k | 572.8k | -253.4k | 2.28 | 84 | +3.35k | 36.1k | 164.6k | 437.5k | -208.4k |
| 10 | 5.3k/72.5k/520.7k | 37.1k | 122.7k | 724.3k | -320.4k | 2.18 | 84 | +2.99k | 42.8k | 205.6k | 553.5k | -262.9k |
| 12 | 5.2k/87.1k/635.6k | 42.3k | 147.2k | 879.2k | -388.9k | 2.07 | 84 | +2.63k | 48.6k | 246.7k | 672.1k | -318.3k |
| 14 | 4.9k/101.7k/754.2k | 46.9k | 171.8k | 1037.3k | -458.8k | 1.97 | 84 | +2.27k | 53.5k | 287.7k | 793.3k | -374.6k |
| 16 | 4.1k/116.2k/876.2k | 50.7k | 196.3k | 1236.2k | -530.2k | 1.86 | 84 | +1.91k | 57.5k | 328.7k | 917.2k | -431.9k |
| 20 | 1.6k/145.4k/1131.2k | 56.1k | 245.3k | 1753.3k | -677.4k | 1.65 | 84 | +1.36k | 62.7k | 410.5k | 1172.9k | -549.3k |

**E. Per entry session (uniform L both books, live locks): weekly realised P&L of the trades entered in each session / trades per week**

| lots | WF ASIA | WF LONDON | WF NY | L8W ASIA | L8W LONDON | L8W NY | IS ASIA | IS LONDON | IS NY |
|---|---|---|---|---|---|---|---|---|---|
| 4 | 6.7k (21) | 2.5k (23) | 6.8k (37) | 12.0k (29) | 8.6k (36) | 2.0k (39) | 1.4k (9) | 2.7k (10) | -1.3k (22) |
| 6 | 10.4k (21) | 3.2k (21) | 7.8k (30) | 20.4k (27) | 15.3k (31) | -13.0k (26) | 2.0k (9) | 3.4k (10) | -1.8k (21) |
| 8 | 14.5k (20) | 5.5k (18) | 8.4k (23) | 30.5k (28) | 15.4k (27) | -3.9k (18) | 2.4k (9) | 4.6k (10) | -3.0k (20) |
| 10 | 14.9k (19) | 3.0k (15) | 7.3k (16) | 23.2k (26) | 24.2k (21) | -12.9k (13) | 3.7k (9) | 5.0k (9) | 3.0k (16) |
| 12 | 16.0k (18) | 4.6k (13) | 5.9k (12) | 15.4k (25) | 44.6k (18) | -20.8k (8) | 5.0k (9) | 9.0k (9) | 0.8k (14) |
| 14 | 18.2k (17) | 2.5k (10) | 4.3k (8) | 30.0k (23) | 11.1k (13) | -6.9k (5) | 2.4k (9) | 10.3k (8) | 1.0k (10) |
| 16 | 14.6k (16) | 5.0k (8) | 2.1k (6) | 13.9k (19) | 16.0k (7) | -11.0k (3) | 1.0k (9) | 11.3k (7) | 2.9k (9) |
| 20 | 15.2k (15) | 6.8k (6) | 2.5k (4) | 14.3k (18) | 20.7k (6) | -3.6k (2) | -1.7k (8) | 8.9k (6) | 4.7k (7) |

**F. Size varied in ONE session only (other sessions 14 lots): WF weekly mean / maxDD (L8W mean)**

| lots in session | ASIA | LONDON | NY |
|---|---|---|---|
| 4 | 10.9k / 739.1k (13.4k) | 26.1k / 397.4k (15.0k) | 25.1k / 468.4k (37.1k) |
| 6 | 16.9k / 725.8k (66.3k) | 27.1k / 402.1k (16.9k) | 26.3k / 460.8k (36.9k) |
| 8 | 21.5k / 573.8k (61.0k) | 26.0k / 316.1k (33.9k) | 26.6k / 484.8k (36.1k) |
| 10 | 27.0k / 504.6k (63.6k) | 28.0k / 377.5k (50.1k) | 27.5k / 497.5k (33.7k) |
| 12 | 28.1k / 491.5k (56.6k) | 27.6k / 410.7k (49.0k) | 29.0k / 409.3k (32.7k) |
| 14 | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) |
| 16 | 28.0k / 393.0k (8.4k) | 26.5k / 439.7k (35.1k) | 24.4k / 433.8k (33.0k) |
| 20 | 25.0k / 390.5k (11.7k) | 25.6k / 604.3k (43.2k) | 26.2k / 444.9k (39.6k) |

## interim 2026-10-22T18:41Z
## DS2-FIRM v3 - V3 (marginal lot) posted earlier; V1 (locks) posted 18:41Z; next V4 ensemble, V2, V5, V6; workers: 7 replay (V7 ETA ~21:30Z) + 18 analysis
V3 headline (above in file): with live locks the weekly mean saturates at ~6-8 lots; marginal lot above 8-10 earns ~0 and costs maxDD.
V1 HEADLINE: locks OFF the live pair has WF 46.9k/wk, SD 171.8k, maxDD 1.04M, worst -459k. The give-back arm is THE truncating lock (alone: SD 135.6k, maxDD 494k, mean 36.6k; pb+cap+gb: SD 101.9k, maxDD 325k, mean 29.2k); per-book day and cap alone barely truncate (SD 149k/160k); week floor 8R alone does ~nothing for SD (162k) but trims worst week (-142k), and ON TOP of the other locks it costs 4.2k/wk mean and RAISES maxDD (325k -> 401k). PURE vol-normalisation effect (locks OFF, ATR20/T2H k1.0 unclamped, R$10k cap14 floor4): WF 37.5k/SD 101k/maxDD 440k vs live 46.9k/172k/1037k; at EQUAL mean SD 126.5k (-26%), maxDD 551k (-47%), worst -346k (-25%) -- the dollar locks mask it (with live locks both land at SD ~86-105k). RIDGE/T2H clamped and the firm cell are worse than the live pair even locks-off (equal-mean SD 430k / 309k): the benefit is specific to ATR20-scaled brackets. Vol-unit locks on the ATR20 cell cut SD to 55k but also the mean to 16k (threshold in the trade's own R$10k risk is tighter in dollars).
**Pure vol-normalisation effect (locks OFF), scaled to the live pair's locks-OFF WF mean 46.9k:**

| cell (locks OFF) | WF mean | WF SD | WF maxDD | WF worst | at equal mean (vs live locks-OFF): SD | maxDD | worst | L8W SD at same m |
|---|---|---|---|---|---|---|---|---|
| (a) live 60 pt / 14 lots (exact P9) | 46.9k | 171.8k | 1037.3k | -458.8k | **171.8k** | 1037.3k | -458.8k | 287.7k |
| (b) RIDGE/T2H k1.0 clamped bracket, 14 lots | 24.8k | 227.6k | 1283.4k | -586.8k | **430.1k** | 2425.6k | -1109.1k | 773.4k |
| (c) ATR20/T2H k1.0 unclamped, R$10k, cap14, floor4 | 37.5k | 101.1k | 440.0k | -276.5k | **126.5k** | 550.6k | -345.9k | 171.7k |
| (d) FIRM RIDGE/T2H k1.0, R$16.8k, cap28 | 26.9k | 177.4k | 957.8k | -361.7k | **308.7k** | 1666.7k | -629.5k | 451.2k |

## interim 2026-10-22T18:41Z
## DS2-FIRM v3 (top priority) - tables posted in order V3, V1, V4, ... (18:41Z); workers: 7 V7 replay (ETA ~21:30Z) + analysis pool; v3 prereg frozen
V3 READ: with the live fixed-dollar locks the weekly mean SATURATES at ~6-8 lots (WF 21-28k/wk) and does not rise to 14 or 20 lots (25.0k, 24.6k) while maxDD grows (401k->525k at 20); trades/wk collapse 82->25 as locks fire earlier. Locks OFF the mean is ~linear (marginal +2.3k/wk per lot at 14, falling) but SD 172k/maxDD 1.04M at 14 lots. So the locks, not the signal, set the weekly SD; the marginal lot above ~8-10 earns ~0 net in WF (NY session marginal lots LOSE: NY WF P&L 8.4k@8 -> 4.3k@14 -> 2.5k@20 as fewer NY trades survive the locks).
### V3 MARGINAL-LOT CURVE (live 60-pt pair, exact P9 points, live fixed-dollar locks, S113 size cost with credit below 14 lots; both books at L lots; 14/14-scale $/wk)

**A. live locks, S113 cost (credit<14)**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 2.7k/28.2k/197.5k | 16.0k | 48.8k | 259.1k | -125.2k | 2.37 | 82 |  | 22.6k | 79.6k | 209.7k | -87.6k |
| 6 | 3.5k/44.3k/323.7k | 21.4k | 70.3k | 378.9k | -134.5k | 2.19 | 72 | +2.67k | 22.7k | 113.9k | 327.3k | -134.4k |
| 8 | 4.0k/56.5k/411.7k | 28.4k | 86.3k | 375.6k | -136.8k | 2.38 | 61 | +3.54k | 42.0k | 111.7k | 274.6k | -122.5k |
| 10 | 11.7k/70.0k/360.7k | 25.3k | 103.1k | 381.7k | -148.6k | 1.77 | 51 | -1.59k | 34.4k | 100.7k | 259.4k | -92.0k |
| 12 | 14.8k/82.3k/360.5k | 26.5k | 109.1k | 372.7k | -138.4k | 1.75 | 43 | +0.65k | 39.3k | 82.9k | 204.6k | -95.8k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.79k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**B. live locks, S113 cost, NO credit below 14**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**C. live locks, size cost OFF**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.8k/101.3k/427.3k | 21.6k | 100.7k | 363.4k | -137.5k | 1.54 | 30 | -1.70k | 19.5k | 125.6k | 324.8k | -135.5k |
| 20 | 13.0k/115.1k/375.7k | 27.2k | 108.3k | 506.3k | -145.3k | 1.81 | 25 | +1.40k | 30.4k | 118.9k | 262.4k | -134.8k |

**D. LOCKS OFF (pure signal + bracket + size), S113 cost**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 3.2k/29.0k/197.5k | 17.0k | 49.1k | 279.8k | -123.8k | 2.49 | 84 |  | 19.9k | 82.4k | 213.5k | -102.3k |
| 6 | 4.2k/43.5k/301.7k | 24.4k | 73.7k | 424.6k | -187.9k | 2.39 | 84 | +3.71k | 28.5k | 123.5k | 324.2k | -154.9k |
| 8 | 4.9k/58.0k/409.4k | 31.1k | 98.2k | 572.8k | -253.4k | 2.28 | 84 | +3.35k | 36.1k | 164.6k | 437.5k | -208.4k |
| 10 | 5.3k/72.5k/520.7k | 37.1k | 122.7k | 724.3k | -320.4k | 2.18 | 84 | +2.99k | 42.8k | 205.6k | 553.5k | -262.9k |
| 12 | 5.2k/87.1k/635.6k | 42.3k | 147.2k | 879.2k | -388.9k | 2.07 | 84 | +2.63k | 48.6k | 246.7k | 672.1k | -318.3k |
| 14 | 4.9k/101.7k/754.2k | 46.9k | 171.8k | 1037.3k | -458.8k | 1.97 | 84 | +2.27k | 53.5k | 287.7k | 793.3k | -374.6k |
| 16 | 4.1k/116.2k/876.2k | 50.7k | 196.3k | 1236.2k | -530.2k | 1.86 | 84 | +1.91k | 57.5k | 328.7k | 917.2k | -431.9k |
| 20 | 1.6k/145.4k/1131.2k | 56.1k | 245.3k | 1753.3k | -677.4k | 1.65 | 84 | +1.36k | 62.7k | 410.5k | 1172.9k | -549.3k |

**E. Per entry session (uniform L both books, live locks): weekly realised P&L of the trades entered in each session / trades per week**

| lots | WF ASIA | WF LONDON | WF NY | L8W ASIA | L8W LONDON | L8W NY | IS ASIA | IS LONDON | IS NY |
|---|---|---|---|---|---|---|---|---|---|
| 4 | 6.7k (21) | 2.5k (23) | 6.8k (37) | 12.0k (29) | 8.6k (36) | 2.0k (39) | 1.4k (9) | 2.7k (10) | -1.3k (22) |
| 6 | 10.4k (21) | 3.2k (21) | 7.8k (30) | 20.4k (27) | 15.3k (31) | -13.0k (26) | 2.0k (9) | 3.4k (10) | -1.8k (21) |
| 8 | 14.5k (20) | 5.5k (18) | 8.4k (23) | 30.5k (28) | 15.4k (27) | -3.9k (18) | 2.4k (9) | 4.6k (10) | -3.0k (20) |
| 10 | 14.9k (19) | 3.0k (15) | 7.3k (16) | 23.2k (26) | 24.2k (21) | -12.9k (13) | 3.7k (9) | 5.0k (9) | 3.0k (16) |
| 12 | 16.0k (18) | 4.6k (13) | 5.9k (12) | 15.4k (25) | 44.6k (18) | -20.8k (8) | 5.0k (9) | 9.0k (9) | 0.8k (14) |
| 14 | 18.2k (17) | 2.5k (10) | 4.3k (8) | 30.0k (23) | 11.1k (13) | -6.9k (5) | 2.4k (9) | 10.3k (8) | 1.0k (10) |
| 16 | 14.6k (16) | 5.0k (8) | 2.1k (6) | 13.9k (19) | 16.0k (7) | -11.0k (3) | 1.0k (9) | 11.3k (7) | 2.9k (9) |
| 20 | 15.2k (15) | 6.8k (6) | 2.5k (4) | 14.3k (18) | 20.7k (6) | -3.6k (2) | -1.7k (8) | 8.9k (6) | 4.7k (7) |

**F. Size varied in ONE session only (other sessions 14 lots): WF weekly mean / maxDD (L8W mean)**

| lots in session | ASIA | LONDON | NY |
|---|---|---|---|
| 4 | 10.9k / 739.1k (13.4k) | 26.1k / 397.4k (15.0k) | 25.1k / 468.4k (37.1k) |
| 6 | 16.9k / 725.8k (66.3k) | 27.1k / 402.1k (16.9k) | 26.3k / 460.8k (36.9k) |
| 8 | 21.5k / 573.8k (61.0k) | 26.0k / 316.1k (33.9k) | 26.6k / 484.8k (36.1k) |
| 10 | 27.0k / 504.6k (63.6k) | 28.0k / 377.5k (50.1k) | 27.5k / 497.5k (33.7k) |
| 12 | 28.1k / 491.5k (56.6k) | 27.6k / 410.7k (49.0k) | 29.0k / 409.3k (32.7k) |
| 14 | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) |
| 16 | 28.0k / 393.0k (8.4k) | 26.5k / 439.7k (35.1k) | 24.4k / 433.8k (33.0k) |
| 20 | 25.0k / 390.5k (11.7k) | 25.6k / 604.3k (43.2k) | 26.2k / 444.9k (39.6k) |V3 headline (above in file): with live locks the weekly mean saturates at ~6-8 lots; marginal lot above 8-10 earns ~0 and costs maxDD.
V1 HEADLINE: locks OFF the live pair has WF 46.9k/wk, SD 171.8k, maxDD 1.04M, worst -459k. The give-back arm is THE truncating lock (alone: SD 135.6k, maxDD 494k, mean 36.6k; pb+cap+gb: SD 101.9k, maxDD 325k, mean 29.2k); per-book day and cap alone barely truncate (SD 149k/160k); week floor 8R alone does ~nothing for SD (162k) but trims worst week (-142k), and ON TOP of the other locks it costs 4.2k/wk mean and RAISES maxDD (325k -> 401k). PURE vol-normalisation effect (locks OFF, ATR20/T2H k1.0 unclamped, R$10k cap14 floor4): WF 37.5k/SD 101k/maxDD 440k vs live 46.9k/172k/1037k; at EQUAL mean SD 126.5k (-26%), maxDD 551k (-47%), worst -346k (-25%) -- the dollar locks mask it (with live locks both land at SD ~86-105k). RIDGE/T2H clamped and the firm cell are worse than the live pair even locks-off (equal-mean SD 430k / 309k): the benefit is specific to ATR20-scaled brackets. Vol-unit locks on the ATR20 cell cut SD to 55k but also the mean to 16k (threshold in the trade's own R$10k risk is tighter in dollars).
**Pure vol-normalisation effect (locks OFF), scaled to the live pair's locks-OFF WF mean 46.9k:**

| cell (locks OFF) | WF mean | WF SD | WF maxDD | WF worst | at equal mean (vs live locks-OFF): SD | maxDD | worst | L8W SD at same m |
|---|---|---|---|---|---|---|---|---|
| (a) live 60 pt / 14 lots (exact P9) | 46.9k | 171.8k | 1037.3k | -458.8k | **171.8k** | 1037.3k | -458.8k | 287.7k |
| (b) RIDGE/T2H k1.0 clamped bracket, 14 lots | 24.8k | 227.6k | 1283.4k | -586.8k | **430.1k** | 2425.6k | -1109.1k | 773.4k |
| (c) ATR20/T2H k1.0 unclamped, R$10k, cap14, floor4 | 37.5k | 101.1k | 440.0k | -276.5k | **126.5k** | 550.6k | -345.9k | 171.7k |
| (d) FIRM RIDGE/T2H k1.0, R$16.8k, cap28 | 26.9k | 177.4k | 957.8k | -361.7k | **308.7k** | 1666.7k | -629.5k | 451.2k |


v2 verdict (Parts 1-6) in autopilot/REPORT_DS2_FIRM.md; v3 report in autopilot/REPORT_DS2_FIRM_V3.md (building).

## interim 2026-10-22T18:47Z
## DS2-FIRM v3 (top priority) - tables posted in order V3, V1, V4, ... (18:47Z); workers: 7 V7 replay (ETA ~21:30Z) + analysis pool; v3 prereg frozen
V3 READ: with the live fixed-dollar locks the weekly mean SATURATES at ~6-8 lots (WF 21-28k/wk) and does not rise to 14 or 20 lots (25.0k, 24.6k) while maxDD grows (401k->525k at 20); trades/wk collapse 82->25 as locks fire earlier. Locks OFF the mean is ~linear (marginal +2.3k/wk per lot at 14, falling) but SD 172k/maxDD 1.04M at 14 lots. So the locks, not the signal, set the weekly SD; the marginal lot above ~8-10 earns ~0 net in WF (NY session marginal lots LOSE: NY WF P&L 8.4k@8 -> 4.3k@14 -> 2.5k@20 as fewer NY trades survive the locks).
### V3 MARGINAL-LOT CURVE (live 60-pt pair, exact P9 points, live fixed-dollar locks, S113 size cost with credit below 14 lots; both books at L lots; 14/14-scale $/wk)

**A. live locks, S113 cost (credit<14)**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 2.7k/28.2k/197.5k | 16.0k | 48.8k | 259.1k | -125.2k | 2.37 | 82 |  | 22.6k | 79.6k | 209.7k | -87.6k |
| 6 | 3.5k/44.3k/323.7k | 21.4k | 70.3k | 378.9k | -134.5k | 2.19 | 72 | +2.67k | 22.7k | 113.9k | 327.3k | -134.4k |
| 8 | 4.0k/56.5k/411.7k | 28.4k | 86.3k | 375.6k | -136.8k | 2.38 | 61 | +3.54k | 42.0k | 111.7k | 274.6k | -122.5k |
| 10 | 11.7k/70.0k/360.7k | 25.3k | 103.1k | 381.7k | -148.6k | 1.77 | 51 | -1.59k | 34.4k | 100.7k | 259.4k | -92.0k |
| 12 | 14.8k/82.3k/360.5k | 26.5k | 109.1k | 372.7k | -138.4k | 1.75 | 43 | +0.65k | 39.3k | 82.9k | 204.6k | -95.8k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.79k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**B. live locks, S113 cost, NO credit below 14**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**C. live locks, size cost OFF**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.8k/101.3k/427.3k | 21.6k | 100.7k | 363.4k | -137.5k | 1.54 | 30 | -1.70k | 19.5k | 125.6k | 324.8k | -135.5k |
| 20 | 13.0k/115.1k/375.7k | 27.2k | 108.3k | 506.3k | -145.3k | 1.81 | 25 | +1.40k | 30.4k | 118.9k | 262.4k | -134.8k |

**D. LOCKS OFF (pure signal + bracket + size), S113 cost**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 3.2k/29.0k/197.5k | 17.0k | 49.1k | 279.8k | -123.8k | 2.49 | 84 |  | 19.9k | 82.4k | 213.5k | -102.3k |
| 6 | 4.2k/43.5k/301.7k | 24.4k | 73.7k | 424.6k | -187.9k | 2.39 | 84 | +3.71k | 28.5k | 123.5k | 324.2k | -154.9k |
| 8 | 4.9k/58.0k/409.4k | 31.1k | 98.2k | 572.8k | -253.4k | 2.28 | 84 | +3.35k | 36.1k | 164.6k | 437.5k | -208.4k |
| 10 | 5.3k/72.5k/520.7k | 37.1k | 122.7k | 724.3k | -320.4k | 2.18 | 84 | +2.99k | 42.8k | 205.6k | 553.5k | -262.9k |
| 12 | 5.2k/87.1k/635.6k | 42.3k | 147.2k | 879.2k | -388.9k | 2.07 | 84 | +2.63k | 48.6k | 246.7k | 672.1k | -318.3k |
| 14 | 4.9k/101.7k/754.2k | 46.9k | 171.8k | 1037.3k | -458.8k | 1.97 | 84 | +2.27k | 53.5k | 287.7k | 793.3k | -374.6k |
| 16 | 4.1k/116.2k/876.2k | 50.7k | 196.3k | 1236.2k | -530.2k | 1.86 | 84 | +1.91k | 57.5k | 328.7k | 917.2k | -431.9k |
| 20 | 1.6k/145.4k/1131.2k | 56.1k | 245.3k | 1753.3k | -677.4k | 1.65 | 84 | +1.36k | 62.7k | 410.5k | 1172.9k | -549.3k |

**E. Per entry session (uniform L both books, live locks): weekly realised P&L of the trades entered in each session / trades per week**

| lots | WF ASIA | WF LONDON | WF NY | L8W ASIA | L8W LONDON | L8W NY | IS ASIA | IS LONDON | IS NY |
|---|---|---|---|---|---|---|---|---|---|
| 4 | 6.7k (21) | 2.5k (23) | 6.8k (37) | 12.0k (29) | 8.6k (36) | 2.0k (39) | 1.4k (9) | 2.7k (10) | -1.3k (22) |
| 6 | 10.4k (21) | 3.2k (21) | 7.8k (30) | 20.4k (27) | 15.3k (31) | -13.0k (26) | 2.0k (9) | 3.4k (10) | -1.8k (21) |
| 8 | 14.5k (20) | 5.5k (18) | 8.4k (23) | 30.5k (28) | 15.4k (27) | -3.9k (18) | 2.4k (9) | 4.6k (10) | -3.0k (20) |
| 10 | 14.9k (19) | 3.0k (15) | 7.3k (16) | 23.2k (26) | 24.2k (21) | -12.9k (13) | 3.7k (9) | 5.0k (9) | 3.0k (16) |
| 12 | 16.0k (18) | 4.6k (13) | 5.9k (12) | 15.4k (25) | 44.6k (18) | -20.8k (8) | 5.0k (9) | 9.0k (9) | 0.8k (14) |
| 14 | 18.2k (17) | 2.5k (10) | 4.3k (8) | 30.0k (23) | 11.1k (13) | -6.9k (5) | 2.4k (9) | 10.3k (8) | 1.0k (10) |
| 16 | 14.6k (16) | 5.0k (8) | 2.1k (6) | 13.9k (19) | 16.0k (7) | -11.0k (3) | 1.0k (9) | 11.3k (7) | 2.9k (9) |
| 20 | 15.2k (15) | 6.8k (6) | 2.5k (4) | 14.3k (18) | 20.7k (6) | -3.6k (2) | -1.7k (8) | 8.9k (6) | 4.7k (7) |

**F. Size varied in ONE session only (other sessions 14 lots): WF weekly mean / maxDD (L8W mean)**

| lots in session | ASIA | LONDON | NY |
|---|---|---|---|
| 4 | 10.9k / 739.1k (13.4k) | 26.1k / 397.4k (15.0k) | 25.1k / 468.4k (37.1k) |
| 6 | 16.9k / 725.8k (66.3k) | 27.1k / 402.1k (16.9k) | 26.3k / 460.8k (36.9k) |
| 8 | 21.5k / 573.8k (61.0k) | 26.0k / 316.1k (33.9k) | 26.6k / 484.8k (36.1k) |
| 10 | 27.0k / 504.6k (63.6k) | 28.0k / 377.5k (50.1k) | 27.5k / 497.5k (33.7k) |
| 12 | 28.1k / 491.5k (56.6k) | 27.6k / 410.7k (49.0k) | 29.0k / 409.3k (32.7k) |
| 14 | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) |
| 16 | 28.0k / 393.0k (8.4k) | 26.5k / 439.7k (35.1k) | 24.4k / 433.8k (33.0k) |
| 20 | 25.0k / 390.5k (11.7k) | 25.6k / 604.3k (43.2k) | 26.2k / 444.9k (39.6k) |V3 headline (above in file): with live locks the weekly mean saturates at ~6-8 lots; marginal lot above 8-10 earns ~0 and costs maxDD.
V1 HEADLINE: locks OFF the live pair has WF 46.9k/wk, SD 171.8k, maxDD 1.04M, worst -459k. The give-back arm is THE truncating lock (alone: SD 135.6k, maxDD 494k, mean 36.6k; pb+cap+gb: SD 101.9k, maxDD 325k, mean 29.2k); per-book day and cap alone barely truncate (SD 149k/160k); week floor 8R alone does ~nothing for SD (162k) but trims worst week (-142k), and ON TOP of the other locks it costs 4.2k/wk mean and RAISES maxDD (325k -> 401k). PURE vol-normalisation effect (locks OFF, ATR20/T2H k1.0 unclamped, R$10k cap14 floor4): WF 37.5k/SD 101k/maxDD 440k vs live 46.9k/172k/1037k; at EQUAL mean SD 126.5k (-26%), maxDD 551k (-47%), worst -346k (-25%) -- the dollar locks mask it (with live locks both land at SD ~86-105k). RIDGE/T2H clamped and the firm cell are worse than the live pair even locks-off (equal-mean SD 430k / 309k): the benefit is specific to ATR20-scaled brackets. Vol-unit locks on the ATR20 cell cut SD to 55k but also the mean to 16k (threshold in the trade's own R$10k risk is tighter in dollars).
**Pure vol-normalisation effect (locks OFF), scaled to the live pair's locks-OFF WF mean 46.9k:**

| cell (locks OFF) | WF mean | WF SD | WF maxDD | WF worst | at equal mean (vs live locks-OFF): SD | maxDD | worst | L8W SD at same m |
|---|---|---|---|---|---|---|---|---|
| (a) live 60 pt / 14 lots (exact P9) | 46.9k | 171.8k | 1037.3k | -458.8k | **171.8k** | 1037.3k | -458.8k | 287.7k |
| (b) RIDGE/T2H k1.0 clamped bracket, 14 lots | 24.8k | 227.6k | 1283.4k | -586.8k | **430.1k** | 2425.6k | -1109.1k | 773.4k |
| (c) ATR20/T2H k1.0 unclamped, R$10k, cap14, floor4 | 37.5k | 101.1k | 440.0k | -276.5k | **126.5k** | 550.6k | -345.9k | 171.7k |
| (d) FIRM RIDGE/T2H k1.0, R$16.8k, cap28 | 26.9k | 177.4k | 957.8k | -361.7k | **308.7k** | 1666.7k | -629.5k | 451.2k |

V4 HEADLINE: the 20-cell live-centred ensemble (fixed 60 pt, 14/14-equiv) is WF 35.9k/SD 104.4k/maxDD 351k, L8W 43.5k/99k/290k vs live 25.0k/104.5k/401k, 34.2k/109k/267k: +10.9k/wk (bootstrap CI vs live [+2.3k,+19.1k], better in 9 of 11 folds) but SD unchanged (every config ~104k), L8W maxDD +23k worse, IS WORSE (6.5k vs 13.7k), and it ranks only 0.88/0.97 among 100 random-neighbourhood ensembles (null) -> NOT a LEAD (gate c rank<0.95, gate b maxDD). Read: the live cell was tuned on 2023 data (IS 13.7k vs grid mean 3.4k) and sits below 20 of 25 grid neighbours in WF (IS/WF rank corr -0.22): regression to the neighbourhood mean, not variance reduction. Robust centre by IS+WF Sharpe: ST ATR132/mult1.8, HM 22x50 (selection-contaminated); walk-forward-chosen neighbourhood WF 29-33k, no better than the plain ensemble.
### V4 ENSEMBLE SCORED PROPERLY (fixed 60 pt, 14/14-equivalent, fractional lots - MNQ 1/10 granularity; no credit for small lots; P9 points exact for the live-cell rows, replay-delta mapping for the other cells)

| cell | WF mean | WF SD | WF maxDD | WF worst | WF Sharpe | L8W mean | L8W SD | L8W maxDD | IS mean | IS maxDD |
|---|---|---|---|---|---|---|---|---|---|---|
| BENCHMARK (live cell, exact) | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k |
| live cell re-run | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k |
| 10-cell ensemble around live | 34.1k | 102.5k | 348.3k | -137.4k | 2.40 | 43.4k | 90.8k | 279.5k | 6.7k | 599.4k |
| 20-cell ensemble around live | 35.9k | 104.4k | 350.9k | -138.1k | 2.48 | 43.5k | 99.2k | 289.7k | 6.5k | 586.6k |
| 40-cell ensemble around live | 32.5k | 105.6k | 501.9k | -136.9k | 2.22 | 30.0k | 101.6k | 333.9k | 8.1k | 506.1k |

**Distribution over the 25 centres (idx 2..6 x 2..6 of the 9x9 grids) and 75 random ST/HM centre combinations:**

| set | n | WF mean (mean / sd / min / max) | WF SD (mean) | WF maxDD (mean / sd) | L8W mean (mean) | IS mean (mean) |
|---|---|---|---|---|---|---|
v2 verdict (Parts 1-6) in autopilot/REPORT_DS2_FIRM.md; v3 report in autopilot/REPORT_DS2_FIRM_V3.md (building).

## interim 2026-10-22T18:49Z
## DS2-FIRM v3 (top priority) - tables posted in order V3, V1, V4, ... (18:49Z); workers: 7 V7 replay (ETA ~21:30Z) + analysis pool; v3 prereg frozen
V3 READ: with the live fixed-dollar locks the weekly mean SATURATES at ~6-8 lots (WF 21-28k/wk) and does not rise to 14 or 20 lots (25.0k, 24.6k) while maxDD grows (401k->525k at 20); trades/wk collapse 82->25 as locks fire earlier. Locks OFF the mean is ~linear (marginal +2.3k/wk per lot at 14, falling) but SD 172k/maxDD 1.04M at 14 lots. So the locks, not the signal, set the weekly SD; the marginal lot above ~8-10 earns ~0 net in WF (NY session marginal lots LOSE: NY WF P&L 8.4k@8 -> 4.3k@14 -> 2.5k@20 as fewer NY trades survive the locks).
### V3 MARGINAL-LOT CURVE (live 60-pt pair, exact P9 points, live fixed-dollar locks, S113 size cost with credit below 14 lots; both books at L lots; 14/14-scale $/wk)

**A. live locks, S113 cost (credit<14)**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 2.7k/28.2k/197.5k | 16.0k | 48.8k | 259.1k | -125.2k | 2.37 | 82 |  | 22.6k | 79.6k | 209.7k | -87.6k |
| 6 | 3.5k/44.3k/323.7k | 21.4k | 70.3k | 378.9k | -134.5k | 2.19 | 72 | +2.67k | 22.7k | 113.9k | 327.3k | -134.4k |
| 8 | 4.0k/56.5k/411.7k | 28.4k | 86.3k | 375.6k | -136.8k | 2.38 | 61 | +3.54k | 42.0k | 111.7k | 274.6k | -122.5k |
| 10 | 11.7k/70.0k/360.7k | 25.3k | 103.1k | 381.7k | -148.6k | 1.77 | 51 | -1.59k | 34.4k | 100.7k | 259.4k | -92.0k |
| 12 | 14.8k/82.3k/360.5k | 26.5k | 109.1k | 372.7k | -138.4k | 1.75 | 43 | +0.65k | 39.3k | 82.9k | 204.6k | -95.8k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.79k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**B. live locks, S113 cost, NO credit below 14**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**C. live locks, size cost OFF**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.8k/101.3k/427.3k | 21.6k | 100.7k | 363.4k | -137.5k | 1.54 | 30 | -1.70k | 19.5k | 125.6k | 324.8k | -135.5k |
| 20 | 13.0k/115.1k/375.7k | 27.2k | 108.3k | 506.3k | -145.3k | 1.81 | 25 | +1.40k | 30.4k | 118.9k | 262.4k | -134.8k |

**D. LOCKS OFF (pure signal + bracket + size), S113 cost**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 3.2k/29.0k/197.5k | 17.0k | 49.1k | 279.8k | -123.8k | 2.49 | 84 |  | 19.9k | 82.4k | 213.5k | -102.3k |
| 6 | 4.2k/43.5k/301.7k | 24.4k | 73.7k | 424.6k | -187.9k | 2.39 | 84 | +3.71k | 28.5k | 123.5k | 324.2k | -154.9k |
| 8 | 4.9k/58.0k/409.4k | 31.1k | 98.2k | 572.8k | -253.4k | 2.28 | 84 | +3.35k | 36.1k | 164.6k | 437.5k | -208.4k |
| 10 | 5.3k/72.5k/520.7k | 37.1k | 122.7k | 724.3k | -320.4k | 2.18 | 84 | +2.99k | 42.8k | 205.6k | 553.5k | -262.9k |
| 12 | 5.2k/87.1k/635.6k | 42.3k | 147.2k | 879.2k | -388.9k | 2.07 | 84 | +2.63k | 48.6k | 246.7k | 672.1k | -318.3k |
| 14 | 4.9k/101.7k/754.2k | 46.9k | 171.8k | 1037.3k | -458.8k | 1.97 | 84 | +2.27k | 53.5k | 287.7k | 793.3k | -374.6k |
| 16 | 4.1k/116.2k/876.2k | 50.7k | 196.3k | 1236.2k | -530.2k | 1.86 | 84 | +1.91k | 57.5k | 328.7k | 917.2k | -431.9k |
| 20 | 1.6k/145.4k/1131.2k | 56.1k | 245.3k | 1753.3k | -677.4k | 1.65 | 84 | +1.36k | 62.7k | 410.5k | 1172.9k | -549.3k |

**E. Per entry session (uniform L both books, live locks): weekly realised P&L of the trades entered in each session / trades per week**

| lots | WF ASIA | WF LONDON | WF NY | L8W ASIA | L8W LONDON | L8W NY | IS ASIA | IS LONDON | IS NY |
|---|---|---|---|---|---|---|---|---|---|
| 4 | 6.7k (21) | 2.5k (23) | 6.8k (37) | 12.0k (29) | 8.6k (36) | 2.0k (39) | 1.4k (9) | 2.7k (10) | -1.3k (22) |
| 6 | 10.4k (21) | 3.2k (21) | 7.8k (30) | 20.4k (27) | 15.3k (31) | -13.0k (26) | 2.0k (9) | 3.4k (10) | -1.8k (21) |
| 8 | 14.5k (20) | 5.5k (18) | 8.4k (23) | 30.5k (28) | 15.4k (27) | -3.9k (18) | 2.4k (9) | 4.6k (10) | -3.0k (20) |
| 10 | 14.9k (19) | 3.0k (15) | 7.3k (16) | 23.2k (26) | 24.2k (21) | -12.9k (13) | 3.7k (9) | 5.0k (9) | 3.0k (16) |
| 12 | 16.0k (18) | 4.6k (13) | 5.9k (12) | 15.4k (25) | 44.6k (18) | -20.8k (8) | 5.0k (9) | 9.0k (9) | 0.8k (14) |
| 14 | 18.2k (17) | 2.5k (10) | 4.3k (8) | 30.0k (23) | 11.1k (13) | -6.9k (5) | 2.4k (9) | 10.3k (8) | 1.0k (10) |
| 16 | 14.6k (16) | 5.0k (8) | 2.1k (6) | 13.9k (19) | 16.0k (7) | -11.0k (3) | 1.0k (9) | 11.3k (7) | 2.9k (9) |
| 20 | 15.2k (15) | 6.8k (6) | 2.5k (4) | 14.3k (18) | 20.7k (6) | -3.6k (2) | -1.7k (8) | 8.9k (6) | 4.7k (7) |

**F. Size varied in ONE session only (other sessions 14 lots): WF weekly mean / maxDD (L8W mean)**

| lots in session | ASIA | LONDON | NY |
|---|---|---|---|
| 4 | 10.9k / 739.1k (13.4k) | 26.1k / 397.4k (15.0k) | 25.1k / 468.4k (37.1k) |
| 6 | 16.9k / 725.8k (66.3k) | 27.1k / 402.1k (16.9k) | 26.3k / 460.8k (36.9k) |
| 8 | 21.5k / 573.8k (61.0k) | 26.0k / 316.1k (33.9k) | 26.6k / 484.8k (36.1k) |
| 10 | 27.0k / 504.6k (63.6k) | 28.0k / 377.5k (50.1k) | 27.5k / 497.5k (33.7k) |
| 12 | 28.1k / 491.5k (56.6k) | 27.6k / 410.7k (49.0k) | 29.0k / 409.3k (32.7k) |
| 14 | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) |
| 16 | 28.0k / 393.0k (8.4k) | 26.5k / 439.7k (35.1k) | 24.4k / 433.8k (33.0k) |
| 20 | 25.0k / 390.5k (11.7k) | 25.6k / 604.3k (43.2k) | 26.2k / 444.9k (39.6k) |V3 headline (above in file): with live locks the weekly mean saturates at ~6-8 lots; marginal lot above 8-10 earns ~0 and costs maxDD.
V1 HEADLINE: locks OFF the live pair has WF 46.9k/wk, SD 171.8k, maxDD 1.04M, worst -459k. The give-back arm is THE truncating lock (alone: SD 135.6k, maxDD 494k, mean 36.6k; pb+cap+gb: SD 101.9k, maxDD 325k, mean 29.2k); per-book day and cap alone barely truncate (SD 149k/160k); week floor 8R alone does ~nothing for SD (162k) but trims worst week (-142k), and ON TOP of the other locks it costs 4.2k/wk mean and RAISES maxDD (325k -> 401k). PURE vol-normalisation effect (locks OFF, ATR20/T2H k1.0 unclamped, R$10k cap14 floor4): WF 37.5k/SD 101k/maxDD 440k vs live 46.9k/172k/1037k; at EQUAL mean SD 126.5k (-26%), maxDD 551k (-47%), worst -346k (-25%) -- the dollar locks mask it (with live locks both land at SD ~86-105k). RIDGE/T2H clamped and the firm cell are worse than the live pair even locks-off (equal-mean SD 430k / 309k): the benefit is specific to ATR20-scaled brackets. Vol-unit locks on the ATR20 cell cut SD to 55k but also the mean to 16k (threshold in the trade's own R$10k risk is tighter in dollars).
**Pure vol-normalisation effect (locks OFF), scaled to the live pair's locks-OFF WF mean 46.9k:**

| cell (locks OFF) | WF mean | WF SD | WF maxDD | WF worst | at equal mean (vs live locks-OFF): SD | maxDD | worst | L8W SD at same m |
|---|---|---|---|---|---|---|---|---|
| (a) live 60 pt / 14 lots (exact P9) | 46.9k | 171.8k | 1037.3k | -458.8k | **171.8k** | 1037.3k | -458.8k | 287.7k |
| (b) RIDGE/T2H k1.0 clamped bracket, 14 lots | 24.8k | 227.6k | 1283.4k | -586.8k | **430.1k** | 2425.6k | -1109.1k | 773.4k |
| (c) ATR20/T2H k1.0 unclamped, R$10k, cap14, floor4 | 37.5k | 101.1k | 440.0k | -276.5k | **126.5k** | 550.6k | -345.9k | 171.7k |
| (d) FIRM RIDGE/T2H k1.0, R$16.8k, cap28 | 26.9k | 177.4k | 957.8k | -361.7k | **308.7k** | 1666.7k | -629.5k | 451.2k |

V4 HEADLINE: the 20-cell live-centred ensemble (fixed 60 pt, 14/14-equiv) is WF 35.9k/SD 104.4k/maxDD 351k, L8W 43.5k/99k/290k vs live 25.0k/104.5k/401k, 34.2k/109k/267k: +10.9k/wk (bootstrap CI vs live [+2.3k,+19.1k], better in 9 of 11 folds) but SD unchanged (every config ~104k), L8W maxDD +23k worse, IS WORSE (6.5k vs 13.7k), and it ranks only 0.88/0.97 among 100 random-neighbourhood ensembles (null) -> NOT a LEAD (gate c rank<0.95, gate b maxDD). Read: the live cell was tuned on 2023 data (IS 13.7k vs grid mean 3.4k) and sits below 20 of 25 grid neighbours in WF (IS/WF rank corr -0.22): regression to the neighbourhood mean, not variance reduction. Robust centre by IS+WF Sharpe: ST ATR132/mult1.8, HM 22x50 (selection-contaminated); walk-forward-chosen neighbourhood WF 29-33k, no better than the plain ensemble.
### V4 ENSEMBLE SCORED PROPERLY (fixed 60 pt, 14/14-equivalent, fractional lots - MNQ 1/10 granularity; no credit for small lots; P9 points exact for the live-cell rows, replay-delta mapping for the other cells)

| cell | WF mean | WF SD | WF maxDD | WF worst | WF Sharpe | L8W mean | L8W SD | L8W maxDD | IS mean | IS maxDD |
|---|---|---|---|---|---|---|---|---|---|---|
| BENCHMARK (live cell, exact) | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k |
| live cell re-run | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k |
| 10-cell ensemble around live | 34.1k | 102.5k | 348.3k | -137.4k | 2.40 | 43.4k | 90.8k | 279.5k | 6.7k | 599.4k |
| 20-cell ensemble around live | 35.9k | 104.4k | 350.9k | -138.1k | 2.48 | 43.5k | 99.2k | 289.7k | 6.5k | 586.6k |
| 40-cell ensemble around live | 32.5k | 105.6k | 501.9k | -136.9k | 2.22 | 30.0k | 101.6k | 333.9k | 8.1k | 506.1k |

**Distribution over the 25 centres (idx 2..6 x 2..6 of the 9x9 grids) and 75 random ST/HM centre combinations:**

| set | n | WF mean (mean / sd / min / max) | WF SD (mean) | WF maxDD (mean / sd) | L8W mean (mean) | IS mean (mean) |
|---|---|---|---|---|---|---|V2/V5 HEADLINE: down-only sizing on the unchanged 60 pt bracket is just the V3 curve (fixed60 8 lots: WF 28.4k/SD 86k/DD 376k; floors inert). The gain is ATR20 k=1.0 specific: ATR20/T2H unclamped k=1.0 R$8k cap14 floor4 WF 32.5k/SD 78.5k/maxDD 310k, L8W 74.1k/SD ~/178k (equal-mean SD 60k, maxDD 238k); R$10k 35.1k/86.4k/389k, L8W 54.0k/256k. 23 of 240 V5 usd-lock cells beat the benchmark on WF+L8W mean AND maxDD, ALL at k=1.0 (k=0.8/0.9/1.1/1.25 pass 0) -> the plateau is one grid step wide = fragile. Session-specific k and vol-unit locks do not rescue it (vol-unit locks cut SD to 55k but mean to 16k). Nulls (100 worlds) running.
V6: vol-target and Kelly/DD control on top of V2 reduce SD and mean together (table in REPORT_DS2_FIRM_V3.md).
  V6 / fixed60 / R10000 / base / usd: WF 28.4k/SD 86.3k/maxDD 375.6k
  V6 / fixed60 / R10000 / 3.3_vt60k / usd: WF 20.5k/SD 78.6k/maxDD 326.9k
  V6 / fixed60 / R10000 / 3.3_vt75k / usd: WF 26.0k/SD 88.1k/maxDD 379.6k
  V6 / fixed60 / R10000 / 3.3_vt90k / usd: WF 30.8k/SD 92.0k/maxDD 367.8k
  V6 / fixed60 / R10000 / 3.5_kelly0.25 / usd: WF 25.9k/SD 85.1k/maxDD 371.7k
  V6 / fixed60 / R10000 / 3.5_kelly0.25_dd / usd: WF 22.5k/SD 77.0k/maxDD 353.8k
  V6 / fixed60 / R10000 / 3.5_kelly0.5 / usd: WF 23.1k/SD 104.2k/maxDD 418.7k
  V6 / fixed60 / R10000 / 3.5_kelly0.5_dd / usd: WF 15.3k/SD 91.6k/maxDD 452.7k
  V6 / fixed60 / R10000 / 3.5_dd_only / usd: WF 22.1k/SD 78.2k/maxDD 375.8k
  V6 / ATR20_k1.0 / R12000 / base / usd: WF 35.9k/SD 93.2k/maxDD 410.7k
  V6 / ATR20_k1.0 / R12000 / 3.3_vt60k / usd: WF 30.9k/SD 83.1k/maxDD 354.3k
  V6 / ATR20_k1.0 / R12000 / 3.3_vt75k / usd: WF 31.2k/SD 87.3k/maxDD 465.7k
  V6 / ATR20_k1.0 / R12000 / 3.3_vt90k / usd: WF 32.2k/SD 90.8k/maxDD 421.8k
  V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.25 / usd: WF 36.0k/SD 83.3k/maxDD 348.8k
  V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.25_dd / usd: WF 31.4k/SD 76.5k/maxDD 271.6k
  V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.5 / usd: WF 32.6k/SD 96.2k/maxDD 460.5k
  V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.5_dd / usd: WF 30.9k/SD 89.4k/maxDD 442.2k
  V6 / ATR20_k1.0 / R12000 / 3.5_dd_only / usd: WF 30.3k/SD 83.7k/maxDD 426.8k
  V6 / ATR20_k1.0 / R10000 / base / usd: WF 35.1k/SD 86.4k/maxDD 388.5k
  V6 / ATR20_k1.0 / R10000 / 3.3_vt60k / usd: WF 31.5k/SD 78.2k/maxDD 340.1k
  V6 / ATR20_k1.0 / R10000 / 3.3_vt75k / usd: WF 33.4k/SD 86.8k/maxDD 406.2k
  V6 / ATR20_k1.0 / R10000 / 3.3_vt90k / usd: WF 29.6k/SD 90.0k/maxDD 460.2k
  V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.25 / usd: WF 36.0k/SD 83.3k/maxDD 348.8k
  V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.25_dd / usd: WF 31.4k/SD 76.5k/maxDD 271.6k
  V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.5 / usd: WF 32.6k/SD 96.2k/maxDD 460.5k
  V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.5_dd / usd: WF 30.9k/SD 89.4k/maxDD 442.2k
  V6 / ATR20_k1.0 / R10000 / 3.5_dd_only / usd: WF 31.0k/SD 77.8k/maxDD 316.2k
v2 verdict (Parts 1-6) in autopilot/REPORT_DS2_FIRM.md; v3 report in autopilot/REPORT_DS2_FIRM_V3.md (building).

## 2026-10-22T18:57:36Z v3 status: V3, V1, V4, V2, V5, V6 scored and posted (tables in MORNING block + REPORT_DS2_FIRM_V3.md draft). Workers: 7 (V7 replay, 24 of 45 months done, ETA ~20:10Z) + analysis pool idle. Interim V7 reconciliation (23 months): mapping overstates replay by +0.21 pts/trade (abs 0.48, worst month 1.7), daily corr 0.98. Nulls: V5 ATR20 k0.8-1.25 x 4 variants x 200 worlds done (k1.0 R$8k cap14: ranks 1.00/1.00; k1.1,1.25 ranks ~0.3-0.8).

## interim 2026-10-22T19:39Z
## DS2-FIRM v3 (top priority) - tables posted in order V3, V1, V4, ... (19:39Z); workers: 7 V7 replay (ETA ~21:30Z) + analysis pool; v3 prereg frozen
V3 READ: with the live fixed-dollar locks the weekly mean SATURATES at ~6-8 lots (WF 21-28k/wk) and does not rise to 14 or 20 lots (25.0k, 24.6k) while maxDD grows (401k->525k at 20); trades/wk collapse 82->25 as locks fire earlier. Locks OFF the mean is ~linear (marginal +2.3k/wk per lot at 14, falling) but SD 172k/maxDD 1.04M at 14 lots. So the locks, not the signal, set the weekly SD; the marginal lot above ~8-10 earns ~0 net in WF (NY session marginal lots LOSE: NY WF P&L 8.4k@8 -> 4.3k@14 -> 2.5k@20 as fewer NY trades survive the locks).
### V3 MARGINAL-LOT CURVE (live 60-pt pair, exact P9 points, live fixed-dollar locks, S113 size cost with credit below 14 lots; both books at L lots; 14/14-scale $/wk)

**A. live locks, S113 cost (credit<14)**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 2.7k/28.2k/197.5k | 16.0k | 48.8k | 259.1k | -125.2k | 2.37 | 82 |  | 22.6k | 79.6k | 209.7k | -87.6k |
| 6 | 3.5k/44.3k/323.7k | 21.4k | 70.3k | 378.9k | -134.5k | 2.19 | 72 | +2.67k | 22.7k | 113.9k | 327.3k | -134.4k |
| 8 | 4.0k/56.5k/411.7k | 28.4k | 86.3k | 375.6k | -136.8k | 2.38 | 61 | +3.54k | 42.0k | 111.7k | 274.6k | -122.5k |
| 10 | 11.7k/70.0k/360.7k | 25.3k | 103.1k | 381.7k | -148.6k | 1.77 | 51 | -1.59k | 34.4k | 100.7k | 259.4k | -92.0k |
| 12 | 14.8k/82.3k/360.5k | 26.5k | 109.1k | 372.7k | -138.4k | 1.75 | 43 | +0.65k | 39.3k | 82.9k | 204.6k | -95.8k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.79k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**B. live locks, S113 cost, NO credit below 14**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**C. live locks, size cost OFF**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.8k/101.3k/427.3k | 21.6k | 100.7k | 363.4k | -137.5k | 1.54 | 30 | -1.70k | 19.5k | 125.6k | 324.8k | -135.5k |
| 20 | 13.0k/115.1k/375.7k | 27.2k | 108.3k | 506.3k | -145.3k | 1.81 | 25 | +1.40k | 30.4k | 118.9k | 262.4k | -134.8k |

**D. LOCKS OFF (pure signal + bracket + size), S113 cost**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 3.2k/29.0k/197.5k | 17.0k | 49.1k | 279.8k | -123.8k | 2.49 | 84 |  | 19.9k | 82.4k | 213.5k | -102.3k |
| 6 | 4.2k/43.5k/301.7k | 24.4k | 73.7k | 424.6k | -187.9k | 2.39 | 84 | +3.71k | 28.5k | 123.5k | 324.2k | -154.9k |
| 8 | 4.9k/58.0k/409.4k | 31.1k | 98.2k | 572.8k | -253.4k | 2.28 | 84 | +3.35k | 36.1k | 164.6k | 437.5k | -208.4k |
| 10 | 5.3k/72.5k/520.7k | 37.1k | 122.7k | 724.3k | -320.4k | 2.18 | 84 | +2.99k | 42.8k | 205.6k | 553.5k | -262.9k |
| 12 | 5.2k/87.1k/635.6k | 42.3k | 147.2k | 879.2k | -388.9k | 2.07 | 84 | +2.63k | 48.6k | 246.7k | 672.1k | -318.3k |
| 14 | 4.9k/101.7k/754.2k | 46.9k | 171.8k | 1037.3k | -458.8k | 1.97 | 84 | +2.27k | 53.5k | 287.7k | 793.3k | -374.6k |
| 16 | 4.1k/116.2k/876.2k | 50.7k | 196.3k | 1236.2k | -530.2k | 1.86 | 84 | +1.91k | 57.5k | 328.7k | 917.2k | -431.9k |
| 20 | 1.6k/145.4k/1131.2k | 56.1k | 245.3k | 1753.3k | -677.4k | 1.65 | 84 | +1.36k | 62.7k | 410.5k | 1172.9k | -549.3k |

**E. Per entry session (uniform L both books, live locks): weekly realised P&L of the trades entered in each session / trades per week**

| lots | WF ASIA | WF LONDON | WF NY | L8W ASIA | L8W LONDON | L8W NY | IS ASIA | IS LONDON | IS NY |
|---|---|---|---|---|---|---|---|---|---|
| 4 | 6.7k (21) | 2.5k (23) | 6.8k (37) | 12.0k (29) | 8.6k (36) | 2.0k (39) | 1.4k (9) | 2.7k (10) | -1.3k (22) |
| 6 | 10.4k (21) | 3.2k (21) | 7.8k (30) | 20.4k (27) | 15.3k (31) | -13.0k (26) | 2.0k (9) | 3.4k (10) | -1.8k (21) |
| 8 | 14.5k (20) | 5.5k (18) | 8.4k (23) | 30.5k (28) | 15.4k (27) | -3.9k (18) | 2.4k (9) | 4.6k (10) | -3.0k (20) |
| 10 | 14.9k (19) | 3.0k (15) | 7.3k (16) | 23.2k (26) | 24.2k (21) | -12.9k (13) | 3.7k (9) | 5.0k (9) | 3.0k (16) |
| 12 | 16.0k (18) | 4.6k (13) | 5.9k (12) | 15.4k (25) | 44.6k (18) | -20.8k (8) | 5.0k (9) | 9.0k (9) | 0.8k (14) |
| 14 | 18.2k (17) | 2.5k (10) | 4.3k (8) | 30.0k (23) | 11.1k (13) | -6.9k (5) | 2.4k (9) | 10.3k (8) | 1.0k (10) |
| 16 | 14.6k (16) | 5.0k (8) | 2.1k (6) | 13.9k (19) | 16.0k (7) | -11.0k (3) | 1.0k (9) | 11.3k (7) | 2.9k (9) |
| 20 | 15.2k (15) | 6.8k (6) | 2.5k (4) | 14.3k (18) | 20.7k (6) | -3.6k (2) | -1.7k (8) | 8.9k (6) | 4.7k (7) |

**F. Size varied in ONE session only (other sessions 14 lots): WF weekly mean / maxDD (L8W mean)**

| lots in session | ASIA | LONDON | NY |
|---|---|---|---|
| 4 | 10.9k / 739.1k (13.4k) | 26.1k / 397.4k (15.0k) | 25.1k / 468.4k (37.1k) |
| 6 | 16.9k / 725.8k (66.3k) | 27.1k / 402.1k (16.9k) | 26.3k / 460.8k (36.9k) |
| 8 | 21.5k / 573.8k (61.0k) | 26.0k / 316.1k (33.9k) | 26.6k / 484.8k (36.1k) |
| 10 | 27.0k / 504.6k (63.6k) | 28.0k / 377.5k (50.1k) | 27.5k / 497.5k (33.7k) |
| 12 | 28.1k / 491.5k (56.6k) | 27.6k / 410.7k (49.0k) | 29.0k / 409.3k (32.7k) |
| 14 | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) |
| 16 | 28.0k / 393.0k (8.4k) | 26.5k / 439.7k (35.1k) | 24.4k / 433.8k (33.0k) |
| 20 | 25.0k / 390.5k (11.7k) | 25.6k / 604.3k (43.2k) | 26.2k / 444.9k (39.6k) |V3 headline (above in file): with live locks the weekly mean saturates at ~6-8 lots; marginal lot above 8-10 earns ~0 and costs maxDD.
V1 HEADLINE: locks OFF the live pair has WF 46.9k/wk, SD 171.8k, maxDD 1.04M, worst -459k. The give-back arm is THE truncating lock (alone: SD 135.6k, maxDD 494k, mean 36.6k; pb+cap+gb: SD 101.9k, maxDD 325k, mean 29.2k); per-book day and cap alone barely truncate (SD 149k/160k); week floor 8R alone does ~nothing for SD (162k) but trims worst week (-142k), and ON TOP of the other locks it costs 4.2k/wk mean and RAISES maxDD (325k -> 401k). PURE vol-normalisation effect (locks OFF, ATR20/T2H k1.0 unclamped, R$10k cap14 floor4): WF 37.5k/SD 101k/maxDD 440k vs live 46.9k/172k/1037k; at EQUAL mean SD 126.5k (-26%), maxDD 551k (-47%), worst -346k (-25%) -- the dollar locks mask it (with live locks both land at SD ~86-105k). RIDGE/T2H clamped and the firm cell are worse than the live pair even locks-off (equal-mean SD 430k / 309k): the benefit is specific to ATR20-scaled brackets. Vol-unit locks on the ATR20 cell cut SD to 55k but also the mean to 16k (threshold in the trade's own R$10k risk is tighter in dollars).
**Pure vol-normalisation effect (locks OFF), scaled to the live pair's locks-OFF WF mean 46.9k:**

| cell (locks OFF) | WF mean | WF SD | WF maxDD | WF worst | at equal mean (vs live locks-OFF): SD | maxDD | worst | L8W SD at same m |
|---|---|---|---|---|---|---|---|---|
| (a) live 60 pt / 14 lots (exact P9) | 46.9k | 171.8k | 1037.3k | -458.8k | **171.8k** | 1037.3k | -458.8k | 287.7k |
| (b) RIDGE/T2H k1.0 clamped bracket, 14 lots | 24.8k | 227.6k | 1283.4k | -586.8k | **430.1k** | 2425.6k | -1109.1k | 773.4k |
| (c) ATR20/T2H k1.0 unclamped, R$10k, cap14, floor4 | 37.5k | 101.1k | 440.0k | -276.5k | **126.5k** | 550.6k | -345.9k | 171.7k |
| (d) FIRM RIDGE/T2H k1.0, R$16.8k, cap28 | 26.9k | 177.4k | 957.8k | -361.7k | **308.7k** | 1666.7k | -629.5k | 451.2k |

V4 HEADLINE: the 20-cell live-centred ensemble (fixed 60 pt, 14/14-equiv) is WF 35.9k/SD 104.4k/maxDD 351k, L8W 43.5k/99k/290k vs live 25.0k/104.5k/401k, 34.2k/109k/267k: +10.9k/wk (bootstrap CI vs live [+2.3k,+19.1k], better in 9 of 11 folds) but SD unchanged (every config ~104k), L8W maxDD +23k worse, IS WORSE (6.5k vs 13.7k), and it ranks only 0.88/0.97 among 100 random-neighbourhood ensembles (null) -> NOT a LEAD (gate c rank<0.95, gate b maxDD). Read: the live cell was tuned on 2023 data (IS 13.7k vs grid mean 3.4k) and sits below 20 of 25 grid neighbours in WF (IS/WF rank corr -0.22): regression to the neighbourhood mean, not variance reduction. Robust centre by IS+WF Sharpe: ST ATR132/mult1.8, HM 22x50 (selection-contaminated); walk-forward-chosen neighbourhood WF 29-33k, no better than the plain ensemble.
### V4 ENSEMBLE SCORED PROPERLY (fixed 60 pt, 14/14-equivalent, fractional lots - MNQ 1/10 granularity; no credit for small lots; P9 points exact for the live-cell rows, replay-delta mapping for the other cells)

| cell | WF mean | WF SD | WF maxDD | WF worst | WF Sharpe | L8W mean | L8W SD | L8W maxDD | IS mean | IS maxDD |
|---|---|---|---|---|---|---|---|---|---|---|
| BENCHMARK (live cell, exact) | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k |
| live cell re-run | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k |
| 10-cell ensemble around live | 34.1k | 102.5k | 348.3k | -137.4k | 2.40 | 43.4k | 90.8k | 279.5k | 6.7k | 599.4k |
| 20-cell ensemble around live | 35.9k | 104.4k | 350.9k | -138.1k | 2.48 | 43.5k | 99.2k | 289.7k | 6.5k | 586.6k |
| 40-cell ensemble around live | 32.5k | 105.6k | 501.9k | -136.9k | 2.22 | 30.0k | 101.6k | 333.9k | 8.1k | 506.1k |

**Distribution over the 25 centres (idx 2..6 x 2..6 of the 9x9 grids) and 75 random ST/HM centre combinations:**

| set | n | WF mean (mean / sd / min / max) | WF SD (mean) | WF maxDD (mean / sd) | L8W mean (mean) | IS mean (mean) |
|---|---|---|---|---|---|---|V2/V5 HEADLINE: down-only sizing on the unchanged 60 pt bracket is just the V3 curve (fixed60 8 lots: WF 28.4k/SD 86k/DD 376k; floors inert). The gain is ATR20 k=1.0 specific: ATR20/T2H unclamped k=1.0 R$8k cap14 floor4 WF 32.5k/SD 78.5k/maxDD 310k, L8W 74.1k/SD ~/178k (equal-mean SD 60k, maxDD 238k); R$10k 35.1k/86.4k/389k, L8W 54.0k/256k. 23 of 240 V5 usd-lock cells beat the benchmark on WF+L8W mean AND maxDD, ALL at k=1.0 (k=0.8/0.9/1.1/1.25 pass 0) -> the plateau is one grid step wide = fragile. Session-specific k and vol-unit locks do not rescue it (vol-unit locks cut SD to 55k but mean to 16k). Nulls (100 worlds) running.
V6: vol-target and Kelly/DD control on top of V2 reduce SD and mean together (table in REPORT_DS2_FIRM_V3.md).
  V6 / fixed60 / R10000 / base / usd: WF 28.4k/SD 86.3k/maxDD 375.6k
  V6 / fixed60 / R10000 / 3.3_vt60k / usd: WF 20.5k/SD 78.6k/maxDD 326.9k
  V6 / fixed60 / R10000 / 3.3_vt75k / usd: WF 26.0k/SD 88.1k/maxDD 379.6k
  V6 / fixed60 / R10000 / 3.3_vt90k / usd: WF 30.8k/SD 92.0k/maxDD 367.8k
  V6 / fixed60 / R10000 / 3.5_kelly0.25 / usd: WF 25.9k/SD 85.1k/maxDD 371.7k
  V6 / fixed60 / R10000 / 3.5_kelly0.25_dd / usd: WF 22.5k/SD 77.0k/maxDD 353.8k
  V6 / fixed60 / R10000 / 3.5_kelly0.5 / usd: WF 23.1k/SD 104.2k/maxDD 418.7k
  V6 / fixed60 / R10000 / 3.5_kelly0.5_dd / usd: WF 15.3k/SD 91.6k/maxDD 452.7k
  V6 / fixed60 / R10000 / 3.5_dd_only / usd: WF 22.1k/SD 78.2k/maxDD 375.8k
  V6 / ATR20_k1.0 / R12000 / base / usd: WF 35.9k/SD 93.2k/maxDD 410.7k
  V6 / ATR20_k1.0 / R12000 / 3.3_vt60k / usd: WF 30.9k/SD 83.1k/maxDD 354.3k
  V6 / ATR20_k1.0 / R12000 / 3.3_vt75k / usd: WF 31.2k/SD 87.3k/maxDD 465.7k
  V6 / ATR20_k1.0 / R12000 / 3.3_vt90k / usd: WF 32.2k/SD 90.8k/maxDD 421.8k
  V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.25 / usd: WF 36.0k/SD 83.3k/maxDD 348.8k
  V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.25_dd / usd: WF 31.4k/SD 76.5k/maxDD 271.6k
  V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.5 / usd: WF 32.6k/SD 96.2k/maxDD 460.5k
  V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.5_dd / usd: WF 30.9k/SD 89.4k/maxDD 442.2k
  V6 / ATR20_k1.0 / R12000 / 3.5_dd_only / usd: WF 30.3k/SD 83.7k/maxDD 426.8k
  V6 / ATR20_k1.0 / R10000 / base / usd: WF 35.1k/SD 86.4k/maxDD 388.5k
  V6 / ATR20_k1.0 / R10000 / 3.3_vt60k / usd: WF 31.5k/SD 78.2k/maxDD 340.1k
  V6 / ATR20_k1.0 / R10000 / 3.3_vt75k / usd: WF 33.4k/SD 86.8k/maxDD 406.2k
  V6 / ATR20_k1.0 / R10000 / 3.3_vt90k / usd: WF 29.6k/SD 90.0k/maxDD 460.2k
  V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.25 / usd: WF 36.0k/SD 83.3k/maxDD 348.8k
  V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.25_dd / usd: WF 31.4k/SD 76.5k/maxDD 271.6k
  V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.5 / usd: WF 32.6k/SD 96.2k/maxDD 460.5k
  V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.5_dd / usd: WF 30.9k/SD 89.4k/maxDD 442.2k
  V6 / ATR20_k1.0 / R10000 / 3.5_dd_only / usd: WF 31.0k/SD 77.8k/maxDD 316.2kV7 DIRECT L2 REPLAY (45 months) of ATR20/T2H/k1.0 unclamped, R$10k cap14 floor4: WF 29.6k / SD 86.9k / maxDD 545.9k / worst -135k (benchmark 25.0k / 104.5k / 401.3k / -137k); L8W 70.9k / 78.0k / 170.7k (34.2k / 109.4k / 267.1k); IS -1.9k / 75.6k / 552.9k (13.7k / 95.9k / 407.3k). Path-table mapping said WF 34.0k/82.5k/431k: it overstates mean by 4-7k/wk and understates maxDD by 115-245k (daily corr 0.94-0.95). Replay verdict: SD -17% (at equal mean -30%), mean +4.6k with bootstrap CI [-6.9k,+13.7k] (gate d fails), WF maxDD +145k WORSE (gate a fails), L8W far better, IS negative (EM market execution on tight brackets) -> NOT a LEAD.
V3 VERDICT SUMMARY: live 14 lots not supported by the marginal-lot curve (flat 6-20 lots, SD/maxDD rise); give-back arm does the truncation; week floor 8R costs 4.2k/wk for no SD gain; ensemble gain = live cell is an in-sample pick regressing to neighbourhood (IS 13.7k vs grid 3.4k), SD unchanged; V6 vol-target/Kelly shrink lots (SD and mean together); only un-replayed single-look: Kelly0.25+DD on ATR20 base (WF 31.4k/76.5k/272k by mapping, read maxDD ~400-500k). 0 cells pass a-d + best-of-F; nothing live; no spec; no shadow. Full report: autopilot/REPORT_DS2_FIRM_V3.md

v2 verdict (Parts 1-6) in autopilot/REPORT_DS2_FIRM.md; v3 report in autopilot/REPORT_DS2_FIRM_V3.md (building).

## 2026-10-22T19:39:46Z v3 COMPLETE: REPORT_DS2_FIRM_V3.md delivered (order V3, V1, V4, V2/V5/V6, V7, verdict). All workers released (replay finished). 0 cells pass gates a-d + best-of-F on the direct replay.

## interim 2026-10-22T19:40Z
## DS2-FIRM v3 (top priority) - tables posted in order V3, V1, V4, ... (19:40Z); ALL DONE - report autopilot/REPORT_DS2_FIRM_V3.md; all workers released; v3 prereg frozen
V3 READ: with the live fixed-dollar locks the weekly mean SATURATES at ~6-8 lots (WF 21-28k/wk) and does not rise to 14 or 20 lots (25.0k, 24.6k) while maxDD grows (401k->525k at 20); trades/wk collapse 82->25 as locks fire earlier. Locks OFF the mean is ~linear (marginal +2.3k/wk per lot at 14, falling) but SD 172k/maxDD 1.04M at 14 lots. So the locks, not the signal, set the weekly SD; the marginal lot above ~8-10 earns ~0 net in WF (NY session marginal lots LOSE: NY WF P&L 8.4k@8 -> 4.3k@14 -> 2.5k@20 as fewer NY trades survive the locks).
### V3 MARGINAL-LOT CURVE (live 60-pt pair, exact P9 points, live fixed-dollar locks, S113 size cost with credit below 14 lots; both books at L lots; 14/14-scale $/wk)

**A. live locks, S113 cost (credit<14)**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 2.7k/28.2k/197.5k | 16.0k | 48.8k | 259.1k | -125.2k | 2.37 | 82 |  | 22.6k | 79.6k | 209.7k | -87.6k |
| 6 | 3.5k/44.3k/323.7k | 21.4k | 70.3k | 378.9k | -134.5k | 2.19 | 72 | +2.67k | 22.7k | 113.9k | 327.3k | -134.4k |
| 8 | 4.0k/56.5k/411.7k | 28.4k | 86.3k | 375.6k | -136.8k | 2.38 | 61 | +3.54k | 42.0k | 111.7k | 274.6k | -122.5k |
| 10 | 11.7k/70.0k/360.7k | 25.3k | 103.1k | 381.7k | -148.6k | 1.77 | 51 | -1.59k | 34.4k | 100.7k | 259.4k | -92.0k |
| 12 | 14.8k/82.3k/360.5k | 26.5k | 109.1k | 372.7k | -138.4k | 1.75 | 43 | +0.65k | 39.3k | 82.9k | 204.6k | -95.8k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.79k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**B. live locks, S113 cost, NO credit below 14**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**C. live locks, size cost OFF**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.8k/101.3k/427.3k | 21.6k | 100.7k | 363.4k | -137.5k | 1.54 | 30 | -1.70k | 19.5k | 125.6k | 324.8k | -135.5k |
| 20 | 13.0k/115.1k/375.7k | 27.2k | 108.3k | 506.3k | -145.3k | 1.81 | 25 | +1.40k | 30.4k | 118.9k | 262.4k | -134.8k |

**D. LOCKS OFF (pure signal + bracket + size), S113 cost**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 3.2k/29.0k/197.5k | 17.0k | 49.1k | 279.8k | -123.8k | 2.49 | 84 |  | 19.9k | 82.4k | 213.5k | -102.3k |
| 6 | 4.2k/43.5k/301.7k | 24.4k | 73.7k | 424.6k | -187.9k | 2.39 | 84 | +3.71k | 28.5k | 123.5k | 324.2k | -154.9k |
| 8 | 4.9k/58.0k/409.4k | 31.1k | 98.2k | 572.8k | -253.4k | 2.28 | 84 | +3.35k | 36.1k | 164.6k | 437.5k | -208.4k |
| 10 | 5.3k/72.5k/520.7k | 37.1k | 122.7k | 724.3k | -320.4k | 2.18 | 84 | +2.99k | 42.8k | 205.6k | 553.5k | -262.9k |
| 12 | 5.2k/87.1k/635.6k | 42.3k | 147.2k | 879.2k | -388.9k | 2.07 | 84 | +2.63k | 48.6k | 246.7k | 672.1k | -318.3k |
| 14 | 4.9k/101.7k/754.2k | 46.9k | 171.8k | 1037.3k | -458.8k | 1.97 | 84 | +2.27k | 53.5k | 287.7k | 793.3k | -374.6k |
| 16 | 4.1k/116.2k/876.2k | 50.7k | 196.3k | 1236.2k | -530.2k | 1.86 | 84 | +1.91k | 57.5k | 328.7k | 917.2k | -431.9k |
| 20 | 1.6k/145.4k/1131.2k | 56.1k | 245.3k | 1753.3k | -677.4k | 1.65 | 84 | +1.36k | 62.7k | 410.5k | 1172.9k | -549.3k |

**E. Per entry session (uniform L both books, live locks): weekly realised P&L of the trades entered in each session / trades per week**

| lots | WF ASIA | WF LONDON | WF NY | L8W ASIA | L8W LONDON | L8W NY | IS ASIA | IS LONDON | IS NY |
|---|---|---|---|---|---|---|---|---|---|
| 4 | 6.7k (21) | 2.5k (23) | 6.8k (37) | 12.0k (29) | 8.6k (36) | 2.0k (39) | 1.4k (9) | 2.7k (10) | -1.3k (22) |
| 6 | 10.4k (21) | 3.2k (21) | 7.8k (30) | 20.4k (27) | 15.3k (31) | -13.0k (26) | 2.0k (9) | 3.4k (10) | -1.8k (21) |
| 8 | 14.5k (20) | 5.5k (18) | 8.4k (23) | 30.5k (28) | 15.4k (27) | -3.9k (18) | 2.4k (9) | 4.6k (10) | -3.0k (20) |
| 10 | 14.9k (19) | 3.0k (15) | 7.3k (16) | 23.2k (26) | 24.2k (21) | -12.9k (13) | 3.7k (9) | 5.0k (9) | 3.0k (16) |
| 12 | 16.0k (18) | 4.6k (13) | 5.9k (12) | 15.4k (25) | 44.6k (18) | -20.8k (8) | 5.0k (9) | 9.0k (9) | 0.8k (14) |
| 14 | 18.2k (17) | 2.5k (10) | 4.3k (8) | 30.0k (23) | 11.1k (13) | -6.9k (5) | 2.4k (9) | 10.3k (8) | 1.0k (10) |
| 16 | 14.6k (16) | 5.0k (8) | 2.1k (6) | 13.9k (19) | 16.0k (7) | -11.0k (3) | 1.0k (9) | 11.3k (7) | 2.9k (9) |
| 20 | 15.2k (15) | 6.8k (6) | 2.5k (4) | 14.3k (18) | 20.7k (6) | -3.6k (2) | -1.7k (8) | 8.9k (6) | 4.7k (7) |

**F. Size varied in ONE session only (other sessions 14 lots): WF weekly mean / maxDD (L8W mean)**

| lots in session | ASIA | LONDON | NY |
|---|---|---|---|
| 4 | 10.9k / 739.1k (13.4k) | 26.1k / 397.4k (15.0k) | 25.1k / 468.4k (37.1k) |
| 6 | 16.9k / 725.8k (66.3k) | 27.1k / 402.1k (16.9k) | 26.3k / 460.8k (36.9k) |
| 8 | 21.5k / 573.8k (61.0k) | 26.0k / 316.1k (33.9k) | 26.6k / 484.8k (36.1k) |
| 10 | 27.0k / 504.6k (63.6k) | 28.0k / 377.5k (50.1k) | 27.5k / 497.5k (33.7k) |
| 12 | 28.1k / 491.5k (56.6k) | 27.6k / 410.7k (49.0k) | 29.0k / 409.3k (32.7k) |
| 14 | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) |
| 16 | 28.0k / 393.0k (8.4k) | 26.5k / 439.7k (35.1k) | 24.4k / 433.8k (33.0k) |
| 20 | 25.0k / 390.5k (11.7k) | 25.6k / 604.3k (43.2k) | 26.2k / 444.9k (39.6k) |V3 headline (above in file): with live locks the weekly mean saturates at ~6-8 lots; marginal lot above 8-10 earns ~0 and costs maxDD.
V1 HEADLINE: locks OFF the live pair has WF 46.9k/wk, SD 171.8k, maxDD 1.04M, worst -459k. The give-back arm is THE truncating lock (alone: SD 135.6k, maxDD 494k, mean 36.6k; pb+cap+gb: SD 101.9k, maxDD 325k, mean 29.2k); per-book day and cap alone barely truncate (SD 149k/160k); week floor 8R alone does ~nothing for SD (162k) but trims worst week (-142k), and ON TOP of the other locks it costs 4.2k/wk mean and RAISES maxDD (325k -> 401k). PURE vol-normalisation effect (locks OFF, ATR20/T2H k1.0 unclamped, R$10k cap14 floor4): WF 37.5k/SD 101k/maxDD 440k vs live 46.9k/172k/1037k; at EQUAL mean SD 126.5k (-26%), maxDD 551k (-47%), worst -346k (-25%) -- the dollar locks mask it (with live locks both land at SD ~86-105k). RIDGE/T2H clamped and the firm cell are worse than the live pair even locks-off (equal-mean SD 430k / 309k): the benefit is specific to ATR20-scaled brackets. Vol-unit locks on the ATR20 cell cut SD to 55k but also the mean to 16k (threshold in the trade's own R$10k risk is tighter in dollars).
**Pure vol-normalisation effect (locks OFF), scaled to the live pair's locks-OFF WF mean 46.9k:**

| cell (locks OFF) | WF mean | WF SD | WF maxDD | WF worst | at equal mean (vs live locks-OFF): SD | maxDD | worst | L8W SD at same m |
|---|---|---|---|---|---|---|---|---|
| (a) live 60 pt / 14 lots (exact P9) | 46.9k | 171.8k | 1037.3k | -458.8k | **171.8k** | 1037.3k | -458.8k | 287.7k |
| (b) RIDGE/T2H k1.0 clamped bracket, 14 lots | 24.8k | 227.6k | 1283.4k | -586.8k | **430.1k** | 2425.6k | -1109.1k | 773.4k |
| (c) ATR20/T2H k1.0 unclamped, R$10k, cap14, floor4 | 37.5k | 101.1k | 440.0k | -276.5k | **126.5k** | 550.6k | -345.9k | 171.7k |
| (d) FIRM RIDGE/T2H k1.0, R$16.8k, cap28 | 26.9k | 177.4k | 957.8k | -361.7k | **308.7k** | 1666.7k | -629.5k | 451.2k |

V4 HEADLINE: the 20-cell live-centred ensemble (fixed 60 pt, 14/14-equiv) is WF 35.9k/SD 104.4k/maxDD 351k, L8W 43.5k/99k/290k vs live 25.0k/104.5k/401k, 34.2k/109k/267k: +10.9k/wk (bootstrap CI vs live [+2.3k,+19.1k], better in 9 of 11 folds) but SD unchanged (every config ~104k), L8W maxDD +23k worse, IS WORSE (6.5k vs 13.7k), and it ranks only 0.88/0.97 among 100 random-neighbourhood ensembles (null) -> NOT a LEAD (gate c rank<0.95, gate b maxDD). Read: the live cell was tuned on 2023 data (IS 13.7k vs grid mean 3.4k) and sits below 20 of 25 grid neighbours in WF (IS/WF rank corr -0.22): regression to the neighbourhood mean, not variance reduction. Robust centre by IS+WF Sharpe: ST ATR132/mult1.8, HM 22x50 (selection-contaminated); walk-forward-chosen neighbourhood WF 29-33k, no better than the plain ensemble.
### V4 ENSEMBLE SCORED PROPERLY (fixed 60 pt, 14/14-equivalent, fractional lots - MNQ 1/10 granularity; no credit for small lots; P9 points exact for the live-cell rows, replay-delta mapping for the other cells)

| cell | WF mean | WF SD | WF maxDD | WF worst | WF Sharpe | L8W mean | L8W SD | L8W maxDD | IS mean | IS maxDD |
|---|---|---|---|---|---|---|---|---|---|---|
| BENCHMARK (live cell, exact) | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k |
| live cell re-run | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k |
| 10-cell ensemble around live | 34.1k | 102.5k | 348.3k | -137.4k | 2.40 | 43.4k | 90.8k | 279.5k | 6.7k | 599.4k |
| 20-cell ensemble around live | 35.9k | 104.4k | 350.9k | -138.1k | 2.48 | 43.5k | 99.2k | 289.7k | 6.5k | 586.6k |
| 40-cell ensemble around live | 32.5k | 105.6k | 501.9k | -136.9k | 2.22 | 30.0k | 101.6k | 333.9k | 8.1k | 506.1k |

**Distribution over the 25 centres (idx 2..6 x 2..6 of the 9x9 grids) and 75 random ST/HM centre combinations:**

| set | n | WF mean (mean / sd / min / max) | WF SD (mean) | WF maxDD (mean / sd) | L8W mean (mean) | IS mean (mean) |
|---|---|---|---|---|---|---|V2/V5 HEADLINE: down-only sizing on the unchanged 60 pt bracket is just the V3 curve (fixed60 8 lots: WF 28.4k/SD 86k/DD 376k; floors inert). The gain is ATR20 k=1.0 specific: ATR20/T2H unclamped k=1.0 R$8k cap14 floor4 WF 32.5k/SD 78.5k/maxDD 310k, L8W 74.1k/SD ~/178k (equal-mean SD 60k, maxDD 238k); R$10k 35.1k/86.4k/389k, L8W 54.0k/256k. 23 of 240 V5 usd-lock cells beat the benchmark on WF+L8W mean AND maxDD, ALL at k=1.0 (k=0.8/0.9/1.1/1.25 pass 0) -> the plateau is one grid step wide = fragile. Session-specific k and vol-unit locks do not rescue it (vol-unit locks cut SD to 55k but mean to 16k). Nulls (100 worlds) running.
V6: vol-target and Kelly/DD control on top of V2 reduce SD and mean together (table in REPORT_DS2_FIRM_V3.md).
  V6 / fixed60 / R10000 / base / usd: WF 28.4k/SD 86.3k/maxDD 375.6k
  V6 / fixed60 / R10000 / 3.3_vt60k / usd: WF 20.5k/SD 78.6k/maxDD 326.9k
  V6 / fixed60 / R10000 / 3.3_vt75k / usd: WF 26.0k/SD 88.1k/maxDD 379.6k
  V6 / fixed60 / R10000 / 3.3_vt90k / usd: WF 30.8k/SD 92.0k/maxDD 367.8k
  V6 / fixed60 / R10000 / 3.5_kelly0.25 / usd: WF 25.9k/SD 85.1k/maxDD 371.7k
  V6 / fixed60 / R10000 / 3.5_kelly0.25_dd / usd: WF 22.5k/SD 77.0k/maxDD 353.8k
  V6 / fixed60 / R10000 / 3.5_kelly0.5 / usd: WF 23.1k/SD 104.2k/maxDD 418.7k
  V6 / fixed60 / R10000 / 3.5_kelly0.5_dd / usd: WF 15.3k/SD 91.6k/maxDD 452.7k
  V6 / fixed60 / R10000 / 3.5_dd_only / usd: WF 22.1k/SD 78.2k/maxDD 375.8k
  V6 / ATR20_k1.0 / R12000 / base / usd: WF 35.9k/SD 93.2k/maxDD 410.7k
  V6 / ATR20_k1.0 / R12000 / 3.3_vt60k / usd: WF 30.9k/SD 83.1k/maxDD 354.3k
  V6 / ATR20_k1.0 / R12000 / 3.3_vt75k / usd: WF 31.2k/SD 87.3k/maxDD 465.7k
  V6 / ATR20_k1.0 / R12000 / 3.3_vt90k / usd: WF 32.2k/SD 90.8k/maxDD 421.8k
  V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.25 / usd: WF 36.0k/SD 83.3k/maxDD 348.8k
  V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.25_dd / usd: WF 31.4k/SD 76.5k/maxDD 271.6k
  V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.5 / usd: WF 32.6k/SD 96.2k/maxDD 460.5k
  V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.5_dd / usd: WF 30.9k/SD 89.4k/maxDD 442.2k
  V6 / ATR20_k1.0 / R12000 / 3.5_dd_only / usd: WF 30.3k/SD 83.7k/maxDD 426.8k
  V6 / ATR20_k1.0 / R10000 / base / usd: WF 35.1k/SD 86.4k/maxDD 388.5k
  V6 / ATR20_k1.0 / R10000 / 3.3_vt60k / usd: WF 31.5k/SD 78.2k/maxDD 340.1k
  V6 / ATR20_k1.0 / R10000 / 3.3_vt75k / usd: WF 33.4k/SD 86.8k/maxDD 406.2k
  V6 / ATR20_k1.0 / R10000 / 3.3_vt90k / usd: WF 29.6k/SD 90.0k/maxDD 460.2k
  V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.25 / usd: WF 36.0k/SD 83.3k/maxDD 348.8k
  V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.25_dd / usd: WF 31.4k/SD 76.5k/maxDD 271.6k
  V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.5 / usd: WF 32.6k/SD 96.2k/maxDD 460.5k
  V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.5_dd / usd: WF 30.9k/SD 89.4k/maxDD 442.2k
  V6 / ATR20_k1.0 / R10000 / 3.5_dd_only / usd: WF 31.0k/SD 77.8k/maxDD 316.2kV7 DIRECT L2 REPLAY (45 months) of ATR20/T2H/k1.0 unclamped, R$10k cap14 floor4: WF 29.6k / SD 86.9k / maxDD 545.9k / worst -135k (benchmark 25.0k / 104.5k / 401.3k / -137k); L8W 70.9k / 78.0k / 170.7k (34.2k / 109.4k / 267.1k); IS -1.9k / 75.6k / 552.9k (13.7k / 95.9k / 407.3k). Path-table mapping said WF 34.0k/82.5k/431k: it overstates mean by 4-7k/wk and understates maxDD by 115-245k (daily corr 0.94-0.95). Replay verdict: SD -17% (at equal mean -30%), mean +4.6k with bootstrap CI [-6.9k,+13.7k] (gate d fails), WF maxDD +145k WORSE (gate a fails), L8W far better, IS negative (EM market execution on tight brackets) -> NOT a LEAD.
V3 VERDICT SUMMARY: live 14 lots not supported by the marginal-lot curve (flat 6-20 lots, SD/maxDD rise); give-back arm does the truncation; week floor 8R costs 4.2k/wk for no SD gain; ensemble gain = live cell is an in-sample pick regressing to neighbourhood (IS 13.7k vs grid 3.4k), SD unchanged; V6 vol-target/Kelly shrink lots (SD and mean together); only un-replayed single-look: Kelly0.25+DD on ATR20 base (WF 31.4k/76.5k/272k by mapping, read maxDD ~400-500k). 0 cells pass a-d + best-of-F; nothing live; no spec; no shadow. Full report: autopilot/REPORT_DS2_FIRM_V3.md

v2 verdict (Parts 1-6) in autopilot/REPORT_DS2_FIRM.md; v3 report in autopilot/REPORT_DS2_FIRM_V3.md (building).

## interim 2026-10-22T20:11Z
## DS2-FIRM v4 (top priority) - tables in order W1, W3, W2, W4, W5, W6 (20:11Z); workers: 30 (W1 done), W3 starting; v4 prereg frozen; v3 report autopilot/REPORT_DS2_FIRM_V3.md (done)
W1 HEADLINE (exact engine, fixed 60/14, 160 runs + 1,000 placebo worlds; no L2 layer needed): the week floor 8R and the combined cap 8R do NOT earn their keep in WF. Live minus week floor: WF 29.2k (+4.2k) / maxDD 325k (-76k) / IS 18.8k vs 13.7k, maxDD 293k vs 407k, L8W identical (floor did not fire); CI of mean delta [+0.7k,+8.3k], 8/11 folds mean, 4/11 maxDD; real floor is WORSE than a random-time week lock (placebo rank 0.12 mean / 0.15 maxDD) - it fires at bad times; cost = worst week -211k vs -137k. Live minus cap AND week (per-book day + give-back only): WF 34.7k (+9.8k) / SD 111k / maxDD 325k (-76k), L8W 41.6k (+7.4k) / 267k (tie), IS 19.0k / 293k; CI [+5.3k,+15.1k], halves 14.1k/6.2k, 10/11 folds on mean, 4/11 on maxDD; worst week -211k. The give-back arm is the only lock with clear value (removing it: maxDD +245k); per-book rule mostly protects maxDD (+104k without it); 5R week floor ($84k) is worse than 8R on every line; arm 3R, keep 67 and Asia-only/RTH-only give-back raise mean in places but raise maxDD (Asia-only gb: WF 39.3k but maxDD 598k). White reality check over 128 configs: best-by-mean p=0.012 (gb_asia), best-by-maxDD p=0.999 (maxDD gains are not distinguishable from selection noise). Lock-flatten extra slip +1 pt moves means by <1.2k, no ranking change.
All 32 subsets (sorted by WF maxDD; the benchmark = pb+cap+gb+wk8). Folds: number of the 11 read windows in which the subset beats the benchmark on mean / on maxDD.**

| locks | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W SD | L8W maxDD | IS mean | IS maxDD | folds mean/DD better | WF d mean | WF d maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| pb+cap+gb | 29.2k | 101.9k | 325.0k | -211.3k | 34.2k | 109.4k | 267.1k | 18.8k | 293.4k | 8/4 | 4.2k | -76.3k |
| pb+gb | 34.7k | 111.3k | 325.0k | -211.3k | 41.6k | 123.4k | 267.1k | 19.0k | 293.4k | 10/4 | 9.8k | -76.3k |
| pb+gb+wk8 | 30.1k | 113.7k | 370.0k | -137.1k | 41.6k | 123.4k | 267.1k | 13.9k | 407.3k | 10/1 | 5.1k | -31.3k |
| pb+cap+gb+wk8 | 25.0k | 104.5k | 401.3k | -137.1k | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k | 0/0 | 0.0k | 0.0k |
| pb+gb+wk5 | 26.5k | 111.0k | 479.3k | -145.0k | 27.5k | 132.8k | 335.0k | 13.4k | 442.8k | 7/6 | 1.6k | 78.0k |
| pb+gb+wk8+wk5 | 26.5k | 111.0k | 479.3k | -145.0k | 27.5k | 132.8k | 335.0k | 13.4k | 442.8k | 7/6 | 1.6k | 78.0k |
| pb+cap+gb+wk8+wk5 | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 13.1k | 442.8k | 4/6 | -2.8k | 78.0k |
| pb+cap+gb+wk5 | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 13.1k | 442.8k | 4/6 | -2.8k | 78.0k |
| gb | 36.6k | 135.6k | 494.0k | -316.6k | 49.8k | 192.4k | 352.8k | 16.8k | 403.4k | 9/4 | 11.6k | 92.7k |
| cap+gb | 28.8k | 121.3k | 494.0k | -316.6k | 29.8k | 150.8k | 352.8k | 16.5k | 403.4k | 8/4 | 3.9k | 92.7k |
| gb+wk8 | 31.4k | 134.1k | 505.7k | -140.6k | 58.4k | 180.6k | 284.2k | 3.4k | 660.6k | 7/4 | 6.5k | 104.4k |
| cap+gb+wk8 | 24.0k | 119.9k | 505.7k | -140.6k | 38.4k | 136.9k | 284.2k | 3.1k | 660.6k | 6/4 | -1.0k | 104.4k |
| pb+cap+wk8 | 39.5k | 135.3k | 646.5k | -137.2k | 68.8k | 186.6k | 498.4k | 1.3k | 621.3k | 8/1 | 14.5k | 245.2k |
| pb+cap+wk5 | 36.9k | 127.8k | 663.3k | -97.6k | 71.2k | 175.0k | 352.8k | 0.0k | 498.2k | 7/1 | 11.9k | 262.0k |
| pb+cap+wk8+wk5 | 36.9k | 127.8k | 663.3k | -97.6k | 71.2k | 175.0k | 352.8k | 0.0k | 498.2k | 7/1 | 11.9k | 262.0k |
| pb+wk8+wk5 | 40.1k | 134.4k | 735.4k | -102.9k | 67.8k | 179.8k | 275.2k | -0.5k | 498.2k | 7/1 | 15.1k | 334.1k |
| pb+wk5 | 40.1k | 134.4k | 735.4k | -102.9k | 67.8k | 179.8k | 275.2k | -0.5k | 498.2k | 7/1 | 15.1k | 334.1k |
| pb+cap | 39.3k | 142.3k | 761.2k | -296.0k | 43.6k | 219.6k | 699.4k | 4.8k | 639.0k | 7/1 | 14.3k | 359.9k |
| pb+wk8 | 44.9k | 141.1k | 762.2k | -137.2k | 70.3k | 188.6k | 402.3k | 1.6k | 648.6k | 9/1 | 19.9k | 361.0k |
| cap+wk8+wk5 | 29.6k | 140.4k | 818.3k | -91.7k | 80.5k | 188.1k | 366.9k | -19.8k | 1363.6k | 5/1 | 4.7k | 417.0k |
| cap+wk5 | 29.6k | 140.4k | 818.3k | -91.7k | 80.5k | 188.1k | 366.9k | -19.8k | 1363.6k | 5/1 | 4.7k | 417.0k |
| wk5 | 34.1k | 150.4k | 818.3k | -91.7k | 76.4k | 193.3k | 256.5k | -19.8k | 1363.6k | 7/1 | 9.1k | 417.0k |
| wk8+wk5 | 34.1k | 150.4k | 818.3k | -91.7k | 76.4k | 193.3k | 256.5k | -19.8k | 1363.6k | 7/1 | 9.1k | 417.0k |
| cap+wk8 | 38.0k | 152.6k | 839.4k | -142.5k | 107.8k | 201.3k | 481.3k | -1.0k | 670.2k | 7/1 | 13.0k | 438.1k |
| wk8 | 41.7k | 161.9k | 885.6k | -142.5k | 106.6k | 208.7k | 369.0k | -0.5k | 670.2k | 8/1 | 16.8k | 484.3k |
| pb | 44.3k | 149.5k | 895.0k | -296.0k | 28.4k | 242.5k | 737.1k | 5.0k | 639.0k | 8/1 | 19.3k | 493.7k |
| cap | 43.1k | 160.4k | 903.6k | -458.8k | 71.4k | 256.4k | 772.4k | 4.3k | 754.2k | 8/2 | 18.1k | 502.3k |
| gb+wk5 | 28.2k | 127.5k | 935.8k | -89.3k | 33.5k | 179.3k | 223.5k | 0.4k | 866.0k | 5/5 | 3.2k | 534.6k |
| gb+wk8+wk5 | 28.2k | 127.5k | 935.8k | -89.3k | 33.5k | 179.3k | 223.5k | 0.4k | 866.0k | 5/5 | 3.2k | 534.6k |
| cap+gb+wk8+wk5 | 20.7k | 112.5k | 935.8k | -89.3k | 13.5k | 130.8k | 223.5k | -0.4k | 866.0k | 4/5 | -4.3k | 534.6k |
| cap+gb+wk5 | 20.7k | 112.5k | 935.8k | -89.3k | 13.5k | 130.8k | 223.5k | -0.4k | 866.0k | 4/5 | -4.3k | 534.6k |
| none | 46.9k | 171.8k | 1037.3k | -458.8k | 53.5k | 287.7k | 793.3k | 4.9k | 754.2k | 9/2 | 21.9k | 636.0k |

**What each lock earns: benchmark minus that lock (paired, exact), with 200 random-trigger placebo worlds** (placebo = the lock replaced by a random-time lock with the same in-situ fire frequency; rank = share of placebo worlds the REAL config beats; for maxDD rank = share of placebo worlds with a larger maxDD than the real config)

| lock removed | config without it | WF mean (delta vs live) | WF SD | WF maxDD (delta) | WF worst | L8W mean / maxDD | IS mean / maxDD | folds better: mean / maxDD | boot90 CI of weekly mean delta (without - live) | placebo WF mean (mean +- sd) / maxDD | real-vs-placebo rank mean / maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|
| pb | cap+gb+wk8 | 24.0k (-1.0k) | 119.9k | 505.7k (+104k) | -140.6k | 38.4k / 284.2k | 3.1k / 660.6k | 6 / 4 | [-8.0k, 6.3k], halves -2.2k/-0.0k | 22.1k +- 6.3k / 673.8k | 0.67 / 0.99 |
| cap | pb+gb+wk8 | 30.1k (+5.1k) | 113.7k | 370.0k (-31k) | -137.1k | 41.6k / 267.1k | 13.9k / 407.3k | 10 / 1 | [2.7k, 7.9k], halves 6.1k/4.3k | 29.9k +- 1.4k / 378.8k | 0.00 / 0.13 |
| gb | pb+cap+wk8 | 39.5k (+14.5k) | 135.3k | 646.5k (+245k) | -137.2k | 68.8k / 498.4k | 1.3k / 621.3k | 8 / 1 | [0.5k, 27.4k], halves 4.7k/22.6k | 33.5k +- 5.5k / 653.2k | 0.05 / 0.99 |
| wk8 | pb+cap+gb | 29.2k (+4.2k) | 101.9k | 325.0k (-76k) | -211.3k | 34.2k / 267.1k | 18.8k / 293.4k | 8 / 4 | [0.7k, 8.3k], halves 6.9k/2.0k | 27.4k +- 2.0k / 357.9k | 0.12 / 0.15 |
| cap+wk8 | pb+gb | 34.7k (+9.8k) | 111.3k | 325.0k (-76k) | -211.3k | 41.6k / 267.1k | 19.0k / 293.4k | 10 / 4 | [5.3k, 15.1k], halves 14.1k/6.2k | 31.9k +- 2.7k / 361.9k | 0.01 / 0.18 |

Week floor 5R ($84k) instead of 8R: WF 22.1k / SD 101.2k / maxDD 479.3k / worst -145.0k; L8W 20.1k / maxDD 335.0k - worse than 8R on every line.

**WEEK-FLOOR FINDING (confirmed on the exact engine).** Live minus the week floor (pb+cap+gb): WF 29.2k vs 25.0k (+4.2k/wk), maxDD 325.0k vs 401.3k (-76k), SD 101.9k vs 104.5k, worst week -211.3k vs -137.1k (the floor's one real job: it caps the worst week); IS 18.8k/293.4k vs 13.7k/407.3k; L8W identical (the floor did not fire in the last 8 weeks, so L8W cannot confirm or refute). Bootstrap 90% CI of the WF weekly mean delta [0.7k, 8.3k], halves 6.9k / 2.0k; better in 8 of 11 folds on mean and 4 of 11 on maxDD. Placebo (200 random-time week locks with the floor's in-situ fire frequency 0.135 per week): real floor ranks mean 0.125, maxDD 0.150 - the real floor fires at systematically worse times than random. Lock-flatten slip +1.0 pt on both configs: see sensitivity table. Weekly mean +4.2k and maxDD -76k WITHOUT the floor, bought at a worst week of -211.3k instead of -137.1k.

## interim 2026-10-22T20:38Z
## DS2-FIRM v4 (top priority) - tables in order W1, W3, W2, W4, W5, W6 (20:38Z); workers: 30 screening (riskeng) + 18 replay (union_w); v4 prereg frozen; v3 report autopilot/REPORT_DS2_FIRM_V3.md (done)
W1 HEADLINE (exact engine, fixed 60/14, 160 runs + 1,000 placebo worlds; no L2 layer needed): the week floor 8R and the combined cap 8R do NOT earn their keep in WF. Live minus week floor: WF 29.2k (+4.2k) / maxDD 325k (-76k) / IS 18.8k vs 13.7k, maxDD 293k vs 407k, L8W identical (floor did not fire); CI of mean delta [+0.7k,+8.3k], 8/11 folds mean, 4/11 maxDD; real floor is WORSE than a random-time week lock (placebo rank 0.12 mean / 0.15 maxDD) - it fires at bad times; cost = worst week -211k vs -137k. Live minus cap AND week (per-book day + give-back only): WF 34.7k (+9.8k) / SD 111k / maxDD 325k (-76k), L8W 41.6k (+7.4k) / 267k (tie), IS 19.0k / 293k; CI [+5.3k,+15.1k], halves 14.1k/6.2k, 10/11 folds on mean, 4/11 on maxDD; worst week -211k. The give-back arm is the only lock with clear value (removing it: maxDD +245k); per-book rule mostly protects maxDD (+104k without it); 5R week floor ($84k) is worse than 8R on every line; arm 3R, keep 67 and Asia-only/RTH-only give-back raise mean in places but raise maxDD (Asia-only gb: WF 39.3k but maxDD 598k). White reality check over 128 configs: best-by-mean p=0.012 (gb_asia), best-by-maxDD p=0.999 (maxDD gains are not distinguishable from selection noise). Lock-flatten extra slip +1 pt moves means by <1.2k, no ranking change.
All 32 subsets (sorted by WF maxDD; the benchmark = pb+cap+gb+wk8). Folds: number of the 11 read windows in which the subset beats the benchmark on mean / on maxDD.**

| locks | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W SD | L8W maxDD | IS mean | IS maxDD | folds mean/DD better | WF d mean | WF d maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| pb+cap+gb | 29.2k | 101.9k | 325.0k | -211.3k | 34.2k | 109.4k | 267.1k | 18.8k | 293.4k | 8/4 | 4.2k | -76.3k |
| pb+gb | 34.7k | 111.3k | 325.0k | -211.3k | 41.6k | 123.4k | 267.1k | 19.0k | 293.4k | 10/4 | 9.8k | -76.3k |
| pb+gb+wk8 | 30.1k | 113.7k | 370.0k | -137.1k | 41.6k | 123.4k | 267.1k | 13.9k | 407.3k | 10/1 | 5.1k | -31.3k |
| pb+cap+gb+wk8 | 25.0k | 104.5k | 401.3k | -137.1k | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k | 0/0 | 0.0k | 0.0k |
| pb+gb+wk5 | 26.5k | 111.0k | 479.3k | -145.0k | 27.5k | 132.8k | 335.0k | 13.4k | 442.8k | 7/6 | 1.6k | 78.0k |
| pb+gb+wk8+wk5 | 26.5k | 111.0k | 479.3k | -145.0k | 27.5k | 132.8k | 335.0k | 13.4k | 442.8k | 7/6 | 1.6k | 78.0k |
| pb+cap+gb+wk8+wk5 | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 13.1k | 442.8k | 4/6 | -2.8k | 78.0k |
| pb+cap+gb+wk5 | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 13.1k | 442.8k | 4/6 | -2.8k | 78.0k |
| gb | 36.6k | 135.6k | 494.0k | -316.6k | 49.8k | 192.4k | 352.8k | 16.8k | 403.4k | 9/4 | 11.6k | 92.7k |
| cap+gb | 28.8k | 121.3k | 494.0k | -316.6k | 29.8k | 150.8k | 352.8k | 16.5k | 403.4k | 8/4 | 3.9k | 92.7k |
| gb+wk8 | 31.4k | 134.1k | 505.7k | -140.6k | 58.4k | 180.6k | 284.2k | 3.4k | 660.6k | 7/4 | 6.5k | 104.4k |
| cap+gb+wk8 | 24.0k | 119.9k | 505.7k | -140.6k | 38.4k | 136.9k | 284.2k | 3.1k | 660.6k | 6/4 | -1.0k | 104.4k |
| pb+cap+wk8 | 39.5k | 135.3k | 646.5k | -137.2k | 68.8k | 186.6k | 498.4k | 1.3k | 621.3k | 8/1 | 14.5k | 245.2k |
| pb+cap+wk5 | 36.9k | 127.8k | 663.3k | -97.6k | 71.2k | 175.0k | 352.8k | 0.0k | 498.2k | 7/1 | 11.9k | 262.0k |
| pb+cap+wk8+wk5 | 36.9k | 127.8k | 663.3k | -97.6k | 71.2k | 175.0k | 352.8k | 0.0k | 498.2k | 7/1 | 11.9k | 262.0k |
| pb+wk8+wk5 | 40.1k | 134.4k | 735.4k | -102.9k | 67.8k | 179.8k | 275.2k | -0.5k | 498.2k | 7/1 | 15.1k | 334.1k |
| pb+wk5 | 40.1k | 134.4k | 735.4k | -102.9k | 67.8k | 179.8k | 275.2k | -0.5k | 498.2k | 7/1 | 15.1k | 334.1k |
| pb+cap | 39.3k | 142.3k | 761.2k | -296.0k | 43.6k | 219.6k | 699.4k | 4.8k | 639.0k | 7/1 | 14.3k | 359.9k |
| pb+wk8 | 44.9k | 141.1k | 762.2k | -137.2k | 70.3k | 188.6k | 402.3k | 1.6k | 648.6k | 9/1 | 19.9k | 361.0k |
| cap+wk8+wk5 | 29.6k | 140.4k | 818.3k | -91.7k | 80.5k | 188.1k | 366.9k | -19.8k | 1363.6k | 5/1 | 4.7k | 417.0k |
| cap+wk5 | 29.6k | 140.4k | 818.3k | -91.7k | 80.5k | 188.1k | 366.9k | -19.8k | 1363.6k | 5/1 | 4.7k | 417.0k |
| wk5 | 34.1k | 150.4k | 818.3k | -91.7k | 76.4k | 193.3k | 256.5k | -19.8k | 1363.6k | 7/1 | 9.1k | 417.0k |
| wk8+wk5 | 34.1k | 150.4k | 818.3k | -91.7k | 76.4k | 193.3k | 256.5k | -19.8k | 1363.6k | 7/1 | 9.1k | 417.0k |
| cap+wk8 | 38.0k | 152.6k | 839.4k | -142.5k | 107.8k | 201.3k | 481.3k | -1.0k | 670.2k | 7/1 | 13.0k | 438.1k |
| wk8 | 41.7k | 161.9k | 885.6k | -142.5k | 106.6k | 208.7k | 369.0k | -0.5k | 670.2k | 8/1 | 16.8k | 484.3k |
| pb | 44.3k | 149.5k | 895.0k | -296.0k | 28.4k | 242.5k | 737.1k | 5.0k | 639.0k | 8/1 | 19.3k | 493.7k |
| cap | 43.1k | 160.4k | 903.6k | -458.8k | 71.4k | 256.4k | 772.4k | 4.3k | 754.2k | 8/2 | 18.1k | 502.3k |
| gb+wk5 | 28.2k | 127.5k | 935.8k | -89.3k | 33.5k | 179.3k | 223.5k | 0.4k | 866.0k | 5/5 | 3.2k | 534.6k |
| gb+wk8+wk5 | 28.2k | 127.5k | 935.8k | -89.3k | 33.5k | 179.3k | 223.5k | 0.4k | 866.0k | 5/5 | 3.2k | 534.6k |
| cap+gb+wk8+wk5 | 20.7k | 112.5k | 935.8k | -89.3k | 13.5k | 130.8k | 223.5k | -0.4k | 866.0k | 4/5 | -4.3k | 534.6k |
| cap+gb+wk5 | 20.7k | 112.5k | 935.8k | -89.3k | 13.5k | 130.8k | 223.5k | -0.4k | 866.0k | 4/5 | -4.3k | 534.6k |
| none | 46.9k | 171.8k | 1037.3k | -458.8k | 53.5k | 287.7k | 793.3k | 4.9k | 754.2k | 9/2 | 21.9k | 636.0k |

**What each lock earns: benchmark minus that lock (paired, exact), with 200 random-trigger placebo worlds** (placebo = the lock replaced by a random-time lock with the same in-situ fire frequency; rank = share of placebo worlds the REAL config beats; for maxDD rank = share of placebo worlds with a larger maxDD than the real config)

| lock removed | config without it | WF mean (delta vs live) | WF SD | WF maxDD (delta) | WF worst | L8W mean / maxDD | IS mean / maxDD | folds better: mean / maxDD | boot90 CI of weekly mean delta (without - live) | placebo WF mean (mean +- sd) / maxDD | real-vs-placebo rank mean / maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|
| pb | cap+gb+wk8 | 24.0k (-1.0k) | 119.9k | 505.7k (+104k) | -140.6k | 38.4k / 284.2k | 3.1k / 660.6k | 6 / 4 | [-8.0k, 6.3k], halves -2.2k/-0.0k | 22.1k +- 6.3k / 673.8k | 0.67 / 0.99 |
| cap | pb+gb+wk8 | 30.1k (+5.1k) | 113.7k | 370.0k (-31k) | -137.1k | 41.6k / 267.1k | 13.9k / 407.3k | 10 / 1 | [2.7k, 7.9k], halves 6.1k/4.3k | 29.9k +- 1.4k / 378.8k | 0.00 / 0.13 |
| gb | pb+cap+wk8 | 39.5k (+14.5k) | 135.3k | 646.5k (+245k) | -137.2k | 68.8k / 498.4k | 1.3k / 621.3k | 8 / 1 | [0.5k, 27.4k], halves 4.7k/22.6k | 33.5k +- 5.5k / 653.2k | 0.05 / 0.99 |
| wk8 | pb+cap+gb | 29.2k (+4.2k) | 101.9k | 325.0k (-76k) | -211.3k | 34.2k / 267.1k | 18.8k / 293.4k | 8 / 4 | [0.7k, 8.3k], halves 6.9k/2.0k | 27.4k +- 2.0k / 357.9k | 0.12 / 0.15 |
| cap+wk8 | pb+gb | 34.7k (+9.8k) | 111.3k | 325.0k (-76k) | -211.3k | 41.6k / 267.1k | 19.0k / 293.4k | 10 / 4 | [5.3k, 15.1k], halves 14.1k/6.2k | 31.9k +- 2.7k / 361.9k | 0.01 / 0.18 |

Week floor 5R ($84k) instead of 8R: WF 22.1k / SD 101.2k / maxDD 479.3k / worst -145.0k; L8W 20.1k / maxDD 335.0k - worse than 8R on every line.

**WEEK-FLOOR FINDING (confirmed on the exact engine).** Live minus the week floor (pb+cap+gb): WF 29.2k vs 25.0k (+4.2k/wk), maxDD 325.0k vs 401.3k (-76k), SD 101.9k vs 104.5k, worst week -211.3k vs -137.1k (the floor's one real job: it caps the worst week); IS 18.8k/293.4k vs 13.7k/407.3k; L8W identical (the floor did not fire in the last 8 weeks, so L8W cannot confirm or refute). Bootstrap 90% CI of the WF weekly mean delta [0.7k, 8.3k], halves 6.9k / 2.0k; better in 8 of 11 folds on mean and 4 of 11 on maxDD. Placebo (200 random-time week locks with the floor's in-situ fire frequency 0.135 per week): real floor ranks mean 0.125, maxDD 0.150 - the real floor fires at systematically worse times than random. Lock-flatten slip +1.0 pt on both configs: see sensitivity table. Weekly mean +4.2k and maxDD -76k WITHOUT the floor, bought at a worst week of -211.3k instead of -137.1k.

V5 INTERIM (riskeng: new stateful 1-s engine reproduces the hard-lock benchmark within 0.1%: WF 24,978 vs 24,975, maxDD 401.6k vs 401.3k; 0.2 s per run).
A1 SOFT LOCKS (108 cells: day steps x give-back-touched lots x week-floor lots x scope; exact fixed-60 path; WF mean/SD/maxDD): live 25k/105k/402k; 0 of 108 beat live on WF mean AND maxDD; lowest-maxDD soft cells: d8-0|gb0|wk8|sc0 24k/100k/338k (L8W 14k/338k); d8-0|gb0|wk8|sc1 20k/108k/339k (L8W 33k/271k); d8-4|gb0|wk8|sc1 21k/109k/349k (L8W 31k/285k); d6-4|gb0|wk8|sc1 20k/105k/351k (L8W 32k/243k). Softening trades mean for DD at best 1:1 (d8-0|gb0|wk8: -1.0k mean, -64k maxDD, L8W much worse 14.1k) - every soft cell is below live on WF mean, none improves both windows.
C1/C2 RISK BUDGETS (no halts; locks OFF; WF mean/SD/maxDD/worst): NOLOCK 46.9k/171.8k/1037k/-459k; daily 30k 30.7k/128.5k/963k; daily 40k 35.2k/141.6k/1325k; daily 50k 37.1k/145.5k/1291k; weekly 100k 39.4k/154.0k/816k/-103k; weekly 134k 42.3k/160.7k/811k/-136k; weekly 170k 41.6k/167.2k/862k/-175k; day30k+wk100k 30.8k/123.7k/743k/-101k (best budget cell). Budgets cap the worst week (as the week floor) but do not cap maxDD (0.74-1.3M vs live 401k): a budget that only counts realized P&L and open stop risk cannot replace the give-back arm, which is the lock that controls drawdown.

## interim 2026-10-22T21:09Z
## DS2-FIRM v4 (top priority) - tables in order W1, W3, W2, W4, W5, W6 (21:09Z); workers: 12 (E1) + 14 replay (union_w, 18/45 months); v4 prereg frozen; v3 report autopilot/REPORT_DS2_FIRM_V3.md (done)
W1 HEADLINE (exact engine, fixed 60/14, 160 runs + 1,000 placebo worlds; no L2 layer needed): the week floor 8R and the combined cap 8R do NOT earn their keep in WF. Live minus week floor: WF 29.2k (+4.2k) / maxDD 325k (-76k) / IS 18.8k vs 13.7k, maxDD 293k vs 407k, L8W identical (floor did not fire); CI of mean delta [+0.7k,+8.3k], 8/11 folds mean, 4/11 maxDD; real floor is WORSE than a random-time week lock (placebo rank 0.12 mean / 0.15 maxDD) - it fires at bad times; cost = worst week -211k vs -137k. Live minus cap AND week (per-book day + give-back only): WF 34.7k (+9.8k) / SD 111k / maxDD 325k (-76k), L8W 41.6k (+7.4k) / 267k (tie), IS 19.0k / 293k; CI [+5.3k,+15.1k], halves 14.1k/6.2k, 10/11 folds on mean, 4/11 on maxDD; worst week -211k. The give-back arm is the only lock with clear value (removing it: maxDD +245k); per-book rule mostly protects maxDD (+104k without it); 5R week floor ($84k) is worse than 8R on every line; arm 3R, keep 67 and Asia-only/RTH-only give-back raise mean in places but raise maxDD (Asia-only gb: WF 39.3k but maxDD 598k). White reality check over 128 configs: best-by-mean p=0.012 (gb_asia), best-by-maxDD p=0.999 (maxDD gains are not distinguishable from selection noise). Lock-flatten extra slip +1 pt moves means by <1.2k, no ranking change.
All 32 subsets (sorted by WF maxDD; the benchmark = pb+cap+gb+wk8). Folds: number of the 11 read windows in which the subset beats the benchmark on mean / on maxDD.**

| locks | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W SD | L8W maxDD | IS mean | IS maxDD | folds mean/DD better | WF d mean | WF d maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| pb+cap+gb | 29.2k | 101.9k | 325.0k | -211.3k | 34.2k | 109.4k | 267.1k | 18.8k | 293.4k | 8/4 | 4.2k | -76.3k |
| pb+gb | 34.7k | 111.3k | 325.0k | -211.3k | 41.6k | 123.4k | 267.1k | 19.0k | 293.4k | 10/4 | 9.8k | -76.3k |
| pb+gb+wk8 | 30.1k | 113.7k | 370.0k | -137.1k | 41.6k | 123.4k | 267.1k | 13.9k | 407.3k | 10/1 | 5.1k | -31.3k |
| pb+cap+gb+wk8 | 25.0k | 104.5k | 401.3k | -137.1k | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k | 0/0 | 0.0k | 0.0k |
| pb+gb+wk5 | 26.5k | 111.0k | 479.3k | -145.0k | 27.5k | 132.8k | 335.0k | 13.4k | 442.8k | 7/6 | 1.6k | 78.0k |
| pb+gb+wk8+wk5 | 26.5k | 111.0k | 479.3k | -145.0k | 27.5k | 132.8k | 335.0k | 13.4k | 442.8k | 7/6 | 1.6k | 78.0k |
| pb+cap+gb+wk8+wk5 | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 13.1k | 442.8k | 4/6 | -2.8k | 78.0k |
| pb+cap+gb+wk5 | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 13.1k | 442.8k | 4/6 | -2.8k | 78.0k |
| gb | 36.6k | 135.6k | 494.0k | -316.6k | 49.8k | 192.4k | 352.8k | 16.8k | 403.4k | 9/4 | 11.6k | 92.7k |
| cap+gb | 28.8k | 121.3k | 494.0k | -316.6k | 29.8k | 150.8k | 352.8k | 16.5k | 403.4k | 8/4 | 3.9k | 92.7k |
| gb+wk8 | 31.4k | 134.1k | 505.7k | -140.6k | 58.4k | 180.6k | 284.2k | 3.4k | 660.6k | 7/4 | 6.5k | 104.4k |
| cap+gb+wk8 | 24.0k | 119.9k | 505.7k | -140.6k | 38.4k | 136.9k | 284.2k | 3.1k | 660.6k | 6/4 | -1.0k | 104.4k |
| pb+cap+wk8 | 39.5k | 135.3k | 646.5k | -137.2k | 68.8k | 186.6k | 498.4k | 1.3k | 621.3k | 8/1 | 14.5k | 245.2k |
| pb+cap+wk5 | 36.9k | 127.8k | 663.3k | -97.6k | 71.2k | 175.0k | 352.8k | 0.0k | 498.2k | 7/1 | 11.9k | 262.0k |
| pb+cap+wk8+wk5 | 36.9k | 127.8k | 663.3k | -97.6k | 71.2k | 175.0k | 352.8k | 0.0k | 498.2k | 7/1 | 11.9k | 262.0k |
| pb+wk8+wk5 | 40.1k | 134.4k | 735.4k | -102.9k | 67.8k | 179.8k | 275.2k | -0.5k | 498.2k | 7/1 | 15.1k | 334.1k |
| pb+wk5 | 40.1k | 134.4k | 735.4k | -102.9k | 67.8k | 179.8k | 275.2k | -0.5k | 498.2k | 7/1 | 15.1k | 334.1k |
| pb+cap | 39.3k | 142.3k | 761.2k | -296.0k | 43.6k | 219.6k | 699.4k | 4.8k | 639.0k | 7/1 | 14.3k | 359.9k |
| pb+wk8 | 44.9k | 141.1k | 762.2k | -137.2k | 70.3k | 188.6k | 402.3k | 1.6k | 648.6k | 9/1 | 19.9k | 361.0k |
| cap+wk8+wk5 | 29.6k | 140.4k | 818.3k | -91.7k | 80.5k | 188.1k | 366.9k | -19.8k | 1363.6k | 5/1 | 4.7k | 417.0k |
| cap+wk5 | 29.6k | 140.4k | 818.3k | -91.7k | 80.5k | 188.1k | 366.9k | -19.8k | 1363.6k | 5/1 | 4.7k | 417.0k |
| wk5 | 34.1k | 150.4k | 818.3k | -91.7k | 76.4k | 193.3k | 256.5k | -19.8k | 1363.6k | 7/1 | 9.1k | 417.0k |
| wk8+wk5 | 34.1k | 150.4k | 818.3k | -91.7k | 76.4k | 193.3k | 256.5k | -19.8k | 1363.6k | 7/1 | 9.1k | 417.0k |
| cap+wk8 | 38.0k | 152.6k | 839.4k | -142.5k | 107.8k | 201.3k | 481.3k | -1.0k | 670.2k | 7/1 | 13.0k | 438.1k |
| wk8 | 41.7k | 161.9k | 885.6k | -142.5k | 106.6k | 208.7k | 369.0k | -0.5k | 670.2k | 8/1 | 16.8k | 484.3k |
| pb | 44.3k | 149.5k | 895.0k | -296.0k | 28.4k | 242.5k | 737.1k | 5.0k | 639.0k | 8/1 | 19.3k | 493.7k |
| cap | 43.1k | 160.4k | 903.6k | -458.8k | 71.4k | 256.4k | 772.4k | 4.3k | 754.2k | 8/2 | 18.1k | 502.3k |
| gb+wk5 | 28.2k | 127.5k | 935.8k | -89.3k | 33.5k | 179.3k | 223.5k | 0.4k | 866.0k | 5/5 | 3.2k | 534.6k |
| gb+wk8+wk5 | 28.2k | 127.5k | 935.8k | -89.3k | 33.5k | 179.3k | 223.5k | 0.4k | 866.0k | 5/5 | 3.2k | 534.6k |
| cap+gb+wk8+wk5 | 20.7k | 112.5k | 935.8k | -89.3k | 13.5k | 130.8k | 223.5k | -0.4k | 866.0k | 4/5 | -4.3k | 534.6k |
| cap+gb+wk5 | 20.7k | 112.5k | 935.8k | -89.3k | 13.5k | 130.8k | 223.5k | -0.4k | 866.0k | 4/5 | -4.3k | 534.6k |
| none | 46.9k | 171.8k | 1037.3k | -458.8k | 53.5k | 287.7k | 793.3k | 4.9k | 754.2k | 9/2 | 21.9k | 636.0k |

**What each lock earns: benchmark minus that lock (paired, exact), with 200 random-trigger placebo worlds** (placebo = the lock replaced by a random-time lock with the same in-situ fire frequency; rank = share of placebo worlds the REAL config beats; for maxDD rank = share of placebo worlds with a larger maxDD than the real config)

| lock removed | config without it | WF mean (delta vs live) | WF SD | WF maxDD (delta) | WF worst | L8W mean / maxDD | IS mean / maxDD | folds better: mean / maxDD | boot90 CI of weekly mean delta (without - live) | placebo WF mean (mean +- sd) / maxDD | real-vs-placebo rank mean / maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|
| pb | cap+gb+wk8 | 24.0k (-1.0k) | 119.9k | 505.7k (+104k) | -140.6k | 38.4k / 284.2k | 3.1k / 660.6k | 6 / 4 | [-8.0k, 6.3k], halves -2.2k/-0.0k | 22.1k +- 6.3k / 673.8k | 0.67 / 0.99 |
| cap | pb+gb+wk8 | 30.1k (+5.1k) | 113.7k | 370.0k (-31k) | -137.1k | 41.6k / 267.1k | 13.9k / 407.3k | 10 / 1 | [2.7k, 7.9k], halves 6.1k/4.3k | 29.9k +- 1.4k / 378.8k | 0.00 / 0.13 |
| gb | pb+cap+wk8 | 39.5k (+14.5k) | 135.3k | 646.5k (+245k) | -137.2k | 68.8k / 498.4k | 1.3k / 621.3k | 8 / 1 | [0.5k, 27.4k], halves 4.7k/22.6k | 33.5k +- 5.5k / 653.2k | 0.05 / 0.99 |
| wk8 | pb+cap+gb | 29.2k (+4.2k) | 101.9k | 325.0k (-76k) | -211.3k | 34.2k / 267.1k | 18.8k / 293.4k | 8 / 4 | [0.7k, 8.3k], halves 6.9k/2.0k | 27.4k +- 2.0k / 357.9k | 0.12 / 0.15 |
| cap+wk8 | pb+gb | 34.7k (+9.8k) | 111.3k | 325.0k (-76k) | -211.3k | 41.6k / 267.1k | 19.0k / 293.4k | 10 / 4 | [5.3k, 15.1k], halves 14.1k/6.2k | 31.9k +- 2.7k / 361.9k | 0.01 / 0.18 |

Week floor 5R ($84k) instead of 8R: WF 22.1k / SD 101.2k / maxDD 479.3k / worst -145.0k; L8W 20.1k / maxDD 335.0k - worse than 8R on every line.

**WEEK-FLOOR FINDING (confirmed on the exact engine).** Live minus the week floor (pb+cap+gb): WF 29.2k vs 25.0k (+4.2k/wk), maxDD 325.0k vs 401.3k (-76k), SD 101.9k vs 104.5k, worst week -211.3k vs -137.1k (the floor's one real job: it caps the worst week); IS 18.8k/293.4k vs 13.7k/407.3k; L8W identical (the floor did not fire in the last 8 weeks, so L8W cannot confirm or refute). Bootstrap 90% CI of the WF weekly mean delta [0.7k, 8.3k], halves 6.9k / 2.0k; better in 8 of 11 folds on mean and 4 of 11 on maxDD. Placebo (200 random-time week locks with the floor's in-situ fire frequency 0.135 per week): real floor ranks mean 0.125, maxDD 0.150 - the real floor fires at systematically worse times than random. Lock-flatten slip +1.0 pt on both configs: see sensitivity table. Weekly mean +4.2k and maxDD -76k WITHOUT the floor, bought at a worst week of -211.3k instead of -137.1k.

V5 INTERIM (riskeng: new stateful 1-s engine reproduces the hard-lock benchmark within 0.1%: WF 24,978 vs 24,975, maxDD 401.6k vs 401.3k; 0.2 s per run).
A1 SOFT LOCKS (108 cells: day steps x give-back-touched lots x week-floor lots x scope; exact fixed-60 path; WF mean/SD/maxDD): live 25k/105k/402k; 0 of 108 beat live on WF mean AND maxDD; lowest-maxDD soft cells: d8-0|gb0|wk8|sc0 24k/100k/338k (L8W 14k/338k); d8-0|gb0|wk8|sc1 20k/108k/339k (L8W 33k/271k); d8-4|gb0|wk8|sc1 21k/109k/349k (L8W 31k/285k); d6-4|gb0|wk8|sc1 20k/105k/351k (L8W 32k/243k). Softening trades mean for DD at best 1:1 (d8-0|gb0|wk8: -1.0k mean, -64k maxDD, L8W much worse 14.1k) - every soft cell is below live on WF mean, none improves both windows.
C1/C2 RISK BUDGETS (no halts; locks OFF; WF mean/SD/maxDD/worst): NOLOCK 46.9k/171.8k/1037k/-459k; daily 30k 30.7k/128.5k/963k; daily 40k 35.2k/141.6k/1325k; daily 50k 37.1k/145.5k/1291k; weekly 100k 39.4k/154.0k/816k/-103k; weekly 134k 42.3k/160.7k/811k/-136k; weekly 170k 41.6k/167.2k/862k/-175k; day30k+wk100k 30.8k/123.7k/743k/-101k (best budget cell). Budgets cap the worst week (as the week floor) but do not cap maxDD (0.74-1.3M vs live 401k): a budget that only counts realized P&L and open stop risk cannot replace the give-back arm, which is the lock that controls drawdown.
V5 D1 JOINT SCREEN (riskeng, 17,280 of 20,160 cells so far: options live60 / live60_P9 / 4 ATR20 cells; W3 centre options pending the union replay): 0 cells meet the strict objective (WF mean >= benchmark AND maxDD <= 0.7 x benchmark). Closest: maxDD 0.72 x benchmark with mean >= benchmark. BEST EXACT CELL (fixed 60, corrected-P9 points, no L2 layer needed): per-book day rule LIVE, combined cap OFF, give-back arm 2R KEEP 67% armed only after >= 2 closed trades, week floor 12R (or off), session lots Asia 14 / London 10 / NY 10: WF 25.5k / SD 93.1k / maxDD 287k / worst -185k (benchmark 25.0k / 104.5k / 401k / -137k); L8W 56.1k / maxDD 183k (34.2k / 267k); IS 13.2k / 305k (13.7k / 407k). 500-world nulls: maxDD rank 1.00 vs placebo locks (placebo maxDD ~620k) and 1.00 vs random-subset down-sizing (mean rank 0.98); mean rank vs placebo locks only 0.42 (the gain is drawdown, not income). H1->H2 frozen holdout over all screened cells: 36% of H1 winners also beat live on H2 (top-5 frozen: all 5 beat live on H2 mean and maxDD). Parameter count 8 changes vs live; deflated Sharpe in the final report. NOT yet: strict-objective pass (none), direct replay of non-60 options, fold stability top-quartile counts, W3 centres.

## 2026-10-22T21:41:33Z v4/v5/v6 status. Frozen: PREREG_DS2_FIRM_V4 / V5 / V6 (sha256 in DECISIONS). Done: W1 (exact, 160 runs + 1,000 placebo worlds), W2 (mapping + replay of all survivors: DD sign flips), W3 mapping, W4 (exact), E1 (567 grid cells), V5 A/B/C blocks (riskeng, 0.1% validated), D1 17,280 of 20,160 cells (+500-world nulls on 8 finalists), V6 A-D (64 cells x2 bases), F1 learned policy (no skill, rank corr -0.02), E regime. In flight: union_w direct L2 replay of the W3 centre trades (32 of 45 months, ~14 workers, ETA ~22:45Z) -> W3 centre test, W5/W6, D1 centre options, nulls on top-20, E2. Memory guard: MemAvailable ~50 GB (killed duplicate replay workers).

## interim 2026-10-22T22:26Z
## DS2-FIRM v4 (top priority) - tables in order W1, W3, W2, W4, W5, W6 (22:26Z); V4/V5/V6 reports written; nulls (top-20, 500 worlds) and E2 finishing; v4 prereg frozen; v3 report autopilot/REPORT_DS2_FIRM_V3.md (done)
W1 HEADLINE (exact engine, fixed 60/14, 160 runs + 1,000 placebo worlds; no L2 layer needed): the week floor 8R and the combined cap 8R do NOT earn their keep in WF. Live minus week floor: WF 29.2k (+4.2k) / maxDD 325k (-76k) / IS 18.8k vs 13.7k, maxDD 293k vs 407k, L8W identical (floor did not fire); CI of mean delta [+0.7k,+8.3k], 8/11 folds mean, 4/11 maxDD; real floor is WORSE than a random-time week lock (placebo rank 0.12 mean / 0.15 maxDD) - it fires at bad times; cost = worst week -211k vs -137k. Live minus cap AND week (per-book day + give-back only): WF 34.7k (+9.8k) / SD 111k / maxDD 325k (-76k), L8W 41.6k (+7.4k) / 267k (tie), IS 19.0k / 293k; CI [+5.3k,+15.1k], halves 14.1k/6.2k, 10/11 folds on mean, 4/11 on maxDD; worst week -211k. The give-back arm is the only lock with clear value (removing it: maxDD +245k); per-book rule mostly protects maxDD (+104k without it); 5R week floor ($84k) is worse than 8R on every line; arm 3R, keep 67 and Asia-only/RTH-only give-back raise mean in places but raise maxDD (Asia-only gb: WF 39.3k but maxDD 598k). White reality check over 128 configs: best-by-mean p=0.012 (gb_asia), best-by-maxDD p=0.999 (maxDD gains are not distinguishable from selection noise). Lock-flatten extra slip +1 pt moves means by <1.2k, no ranking change.
All 32 subsets (sorted by WF maxDD; the benchmark = pb+cap+gb+wk8). Folds: number of the 11 read windows in which the subset beats the benchmark on mean / on maxDD.**

| locks | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W SD | L8W maxDD | IS mean | IS maxDD | folds mean/DD better | WF d mean | WF d maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| pb+cap+gb | 29.2k | 101.9k | 325.0k | -211.3k | 34.2k | 109.4k | 267.1k | 18.8k | 293.4k | 8/4 | 4.2k | -76.3k |
| pb+gb | 34.7k | 111.3k | 325.0k | -211.3k | 41.6k | 123.4k | 267.1k | 19.0k | 293.4k | 10/4 | 9.8k | -76.3k |
| pb+gb+wk8 | 30.1k | 113.7k | 370.0k | -137.1k | 41.6k | 123.4k | 267.1k | 13.9k | 407.3k | 10/1 | 5.1k | -31.3k |
| pb+cap+gb+wk8 | 25.0k | 104.5k | 401.3k | -137.1k | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k | 0/0 | 0.0k | 0.0k |
| pb+gb+wk5 | 26.5k | 111.0k | 479.3k | -145.0k | 27.5k | 132.8k | 335.0k | 13.4k | 442.8k | 7/6 | 1.6k | 78.0k |
| pb+gb+wk8+wk5 | 26.5k | 111.0k | 479.3k | -145.0k | 27.5k | 132.8k | 335.0k | 13.4k | 442.8k | 7/6 | 1.6k | 78.0k |
| pb+cap+gb+wk8+wk5 | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 13.1k | 442.8k | 4/6 | -2.8k | 78.0k |
| pb+cap+gb+wk5 | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 13.1k | 442.8k | 4/6 | -2.8k | 78.0k |
| gb | 36.6k | 135.6k | 494.0k | -316.6k | 49.8k | 192.4k | 352.8k | 16.8k | 403.4k | 9/4 | 11.6k | 92.7k |
| cap+gb | 28.8k | 121.3k | 494.0k | -316.6k | 29.8k | 150.8k | 352.8k | 16.5k | 403.4k | 8/4 | 3.9k | 92.7k |
| gb+wk8 | 31.4k | 134.1k | 505.7k | -140.6k | 58.4k | 180.6k | 284.2k | 3.4k | 660.6k | 7/4 | 6.5k | 104.4k |
| cap+gb+wk8 | 24.0k | 119.9k | 505.7k | -140.6k | 38.4k | 136.9k | 284.2k | 3.1k | 660.6k | 6/4 | -1.0k | 104.4k |
| pb+cap+wk8 | 39.5k | 135.3k | 646.5k | -137.2k | 68.8k | 186.6k | 498.4k | 1.3k | 621.3k | 8/1 | 14.5k | 245.2k |
| pb+cap+wk5 | 36.9k | 127.8k | 663.3k | -97.6k | 71.2k | 175.0k | 352.8k | 0.0k | 498.2k | 7/1 | 11.9k | 262.0k |
| pb+cap+wk8+wk5 | 36.9k | 127.8k | 663.3k | -97.6k | 71.2k | 175.0k | 352.8k | 0.0k | 498.2k | 7/1 | 11.9k | 262.0k |
| pb+wk8+wk5 | 40.1k | 134.4k | 735.4k | -102.9k | 67.8k | 179.8k | 275.2k | -0.5k | 498.2k | 7/1 | 15.1k | 334.1k |
| pb+wk5 | 40.1k | 134.4k | 735.4k | -102.9k | 67.8k | 179.8k | 275.2k | -0.5k | 498.2k | 7/1 | 15.1k | 334.1k |
| pb+cap | 39.3k | 142.3k | 761.2k | -296.0k | 43.6k | 219.6k | 699.4k | 4.8k | 639.0k | 7/1 | 14.3k | 359.9k |
| pb+wk8 | 44.9k | 141.1k | 762.2k | -137.2k | 70.3k | 188.6k | 402.3k | 1.6k | 648.6k | 9/1 | 19.9k | 361.0k |
| cap+wk8+wk5 | 29.6k | 140.4k | 818.3k | -91.7k | 80.5k | 188.1k | 366.9k | -19.8k | 1363.6k | 5/1 | 4.7k | 417.0k |
| cap+wk5 | 29.6k | 140.4k | 818.3k | -91.7k | 80.5k | 188.1k | 366.9k | -19.8k | 1363.6k | 5/1 | 4.7k | 417.0k |
| wk5 | 34.1k | 150.4k | 818.3k | -91.7k | 76.4k | 193.3k | 256.5k | -19.8k | 1363.6k | 7/1 | 9.1k | 417.0k |
| wk8+wk5 | 34.1k | 150.4k | 818.3k | -91.7k | 76.4k | 193.3k | 256.5k | -19.8k | 1363.6k | 7/1 | 9.1k | 417.0k |
| cap+wk8 | 38.0k | 152.6k | 839.4k | -142.5k | 107.8k | 201.3k | 481.3k | -1.0k | 670.2k | 7/1 | 13.0k | 438.1k |
| wk8 | 41.7k | 161.9k | 885.6k | -142.5k | 106.6k | 208.7k | 369.0k | -0.5k | 670.2k | 8/1 | 16.8k | 484.3k |
| pb | 44.3k | 149.5k | 895.0k | -296.0k | 28.4k | 242.5k | 737.1k | 5.0k | 639.0k | 8/1 | 19.3k | 493.7k |
| cap | 43.1k | 160.4k | 903.6k | -458.8k | 71.4k | 256.4k | 772.4k | 4.3k | 754.2k | 8/2 | 18.1k | 502.3k |
| gb+wk5 | 28.2k | 127.5k | 935.8k | -89.3k | 33.5k | 179.3k | 223.5k | 0.4k | 866.0k | 5/5 | 3.2k | 534.6k |
| gb+wk8+wk5 | 28.2k | 127.5k | 935.8k | -89.3k | 33.5k | 179.3k | 223.5k | 0.4k | 866.0k | 5/5 | 3.2k | 534.6k |
| cap+gb+wk8+wk5 | 20.7k | 112.5k | 935.8k | -89.3k | 13.5k | 130.8k | 223.5k | -0.4k | 866.0k | 4/5 | -4.3k | 534.6k |
| cap+gb+wk5 | 20.7k | 112.5k | 935.8k | -89.3k | 13.5k | 130.8k | 223.5k | -0.4k | 866.0k | 4/5 | -4.3k | 534.6k |
| none | 46.9k | 171.8k | 1037.3k | -458.8k | 53.5k | 287.7k | 793.3k | 4.9k | 754.2k | 9/2 | 21.9k | 636.0k |

**What each lock earns: benchmark minus that lock (paired, exact), with 200 random-trigger placebo worlds** (placebo = the lock replaced by a random-time lock with the same in-situ fire frequency; rank = share of placebo worlds the REAL config beats; for maxDD rank = share of placebo worlds with a larger maxDD than the real config)

| lock removed | config without it | WF mean (delta vs live) | WF SD | WF maxDD (delta) | WF worst | L8W mean / maxDD | IS mean / maxDD | folds better: mean / maxDD | boot90 CI of weekly mean delta (without - live) | placebo WF mean (mean +- sd) / maxDD | real-vs-placebo rank mean / maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|
| pb | cap+gb+wk8 | 24.0k (-1.0k) | 119.9k | 505.7k (+104k) | -140.6k | 38.4k / 284.2k | 3.1k / 660.6k | 6 / 4 | [-8.0k, 6.3k], halves -2.2k/-0.0k | 22.1k +- 6.3k / 673.8k | 0.67 / 0.99 |
| cap | pb+gb+wk8 | 30.1k (+5.1k) | 113.7k | 370.0k (-31k) | -137.1k | 41.6k / 267.1k | 13.9k / 407.3k | 10 / 1 | [2.7k, 7.9k], halves 6.1k/4.3k | 29.9k +- 1.4k / 378.8k | 0.00 / 0.13 |
| gb | pb+cap+wk8 | 39.5k (+14.5k) | 135.3k | 646.5k (+245k) | -137.2k | 68.8k / 498.4k | 1.3k / 621.3k | 8 / 1 | [0.5k, 27.4k], halves 4.7k/22.6k | 33.5k +- 5.5k / 653.2k | 0.05 / 0.99 |
| wk8 | pb+cap+gb | 29.2k (+4.2k) | 101.9k | 325.0k (-76k) | -211.3k | 34.2k / 267.1k | 18.8k / 293.4k | 8 / 4 | [0.7k, 8.3k], halves 6.9k/2.0k | 27.4k +- 2.0k / 357.9k | 0.12 / 0.15 |
| cap+wk8 | pb+gb | 34.7k (+9.8k) | 111.3k | 325.0k (-76k) | -211.3k | 41.6k / 267.1k | 19.0k / 293.4k | 10 / 4 | [5.3k, 15.1k], halves 14.1k/6.2k | 31.9k +- 2.7k / 361.9k | 0.01 / 0.18 |

Week floor 5R ($84k) instead of 8R: WF 22.1k / SD 101.2k / maxDD 479.3k / worst -145.0k; L8W 20.1k / maxDD 335.0k - worse than 8R on every line.

**WEEK-FLOOR FINDING (confirmed on the exact engine).** Live minus the week floor (pb+cap+gb): WF 29.2k vs 25.0k (+4.2k/wk), maxDD 325.0k vs 401.3k (-76k), SD 101.9k vs 104.5k, worst week -211.3k vs -137.1k (the floor's one real job: it caps the worst week); IS 18.8k/293.4k vs 13.7k/407.3k; L8W identical (the floor did not fire in the last 8 weeks, so L8W cannot confirm or refute). Bootstrap 90% CI of the WF weekly mean delta [0.7k, 8.3k], halves 6.9k / 2.0k; better in 8 of 11 folds on mean and 4 of 11 on maxDD. Placebo (200 random-time week locks with the floor's in-situ fire frequency 0.135 per week): real floor ranks mean 0.125, maxDD 0.150 - the real floor fires at systematically worse times than random. Lock-flatten slip +1.0 pt on both configs: see sensitivity table. Weekly mean +4.2k and maxDD -76k WITHOUT the floor, bought at a worst week of -211.3k instead of -137.1k.

V5 INTERIM (riskeng: new stateful 1-s engine reproduces the hard-lock benchmark within 0.1%: WF 24,978 vs 24,975, maxDD 401.6k vs 401.3k; 0.2 s per run).
A1 SOFT LOCKS (108 cells: day steps x give-back-touched lots x week-floor lots x scope; exact fixed-60 path; WF mean/SD/maxDD): live 25k/105k/402k; 0 of 108 beat live on WF mean AND maxDD; lowest-maxDD soft cells: d8-0|gb0|wk8|sc0 24k/100k/338k (L8W 14k/338k); d8-0|gb0|wk8|sc1 20k/108k/339k (L8W 33k/271k); d8-4|gb0|wk8|sc1 21k/109k/349k (L8W 31k/285k); d6-4|gb0|wk8|sc1 20k/105k/351k (L8W 32k/243k). Softening trades mean for DD at best 1:1 (d8-0|gb0|wk8: -1.0k mean, -64k maxDD, L8W much worse 14.1k) - every soft cell is below live on WF mean, none improves both windows.
C1/C2 RISK BUDGETS (no halts; locks OFF; WF mean/SD/maxDD/worst): NOLOCK 46.9k/171.8k/1037k/-459k; daily 30k 30.7k/128.5k/963k; daily 40k 35.2k/141.6k/1325k; daily 50k 37.1k/145.5k/1291k; weekly 100k 39.4k/154.0k/816k/-103k; weekly 134k 42.3k/160.7k/811k/-136k; weekly 170k 41.6k/167.2k/862k/-175k; day30k+wk100k 30.8k/123.7k/743k/-101k (best budget cell). Budgets cap the worst week (as the week floor) but do not cap maxDD (0.74-1.3M vs live 401k): a budget that only counts realized P&L and open stop risk cannot replace the give-back arm, which is the lock that controls drawdown.
V5 D1 JOINT SCREEN (riskeng, 17,280 of 20,160 cells so far: options live60 / live60_P9 / 4 ATR20 cells; W3 centre options pending the union replay): 0 cells meet the strict objective (WF mean >= benchmark AND maxDD <= 0.7 x benchmark). Closest: maxDD 0.72 x benchmark with mean >= benchmark. BEST EXACT CELL (fixed 60, corrected-P9 points, no L2 layer needed): per-book day rule LIVE, combined cap OFF, give-back arm 2R KEEP 67% armed only after >= 2 closed trades, week floor 12R (or off), session lots Asia 14 / London 10 / NY 10: WF 25.5k / SD 93.1k / maxDD 287k / worst -185k (benchmark 25.0k / 104.5k / 401k / -137k); L8W 56.1k / maxDD 183k (34.2k / 267k); IS 13.2k / 305k (13.7k / 407k). 500-world nulls: maxDD rank 1.00 vs placebo locks (placebo maxDD ~620k) and 1.00 vs random-subset down-sizing (mean rank 0.98); mean rank vs placebo locks only 0.42 (the gain is drawdown, not income). H1->H2 frozen holdout over all screened cells: 36% of H1 winners also beat live on H2 (top-5 frozen: all 5 beat live on H2 mean and maxDD). Parameter count 8 changes vs live; deflated Sharpe in the final report. NOT yet: strict-objective pass (none), direct replay of non-60 options, fold stability top-quartile counts, W3 centres.V4/V5/V6 STATUS (reports: autopilot/REPORT_DS2_FIRM_V4.md, _V5.md, _V6.md): 
 W1 (exact): live minus week floor +4.2k/wk WF, maxDD -76k (placebo rank 0.12/0.15: fires at worse-than-random times); live minus cap AND week floor: WF 34.7k (+9.8k), maxDD 325k (-76k), IS 19.0k/294k, L8W 41.6k/267k (tie); worst week -211k vs -137k. Direct-replay-policy check: +8.8k / -24k. 
 W3 centres FAIL direct replay (honest centre: maxDD +13k worse than the replay-policy live pair, L8W 29.0k vs 45.8k); live cell rank 67/75 in WF but 22/75 in IS (grid flat and noisy). W2 ATR brackets at 14/14/14 flip the DD sign on replay (539-566k vs 371k). W4: London/NY 10 lots beats random down-sizing (rank >= 0.96). W5: 2 of 60 joint cells beat the replay-policy live pair on both windows (both fixed-60 pb+gb with London/NY 10/8-10 lots). W6: ATR cells hold on DD but fail mean/IS.
 V5: strict objective (mean >= benchmark AND maxDD <= 0.7x) met by 0 of 23,040 screened cells; closest 0.72x. Best exact cell (BEST5): per-book rule live, cap OFF, give-back keep 67% armed after 2 trades, week floor 12R, London/NY 10 lots: WF 25.5k/93.1k/287k, L8W 56.1k/183k, IS 13.2k/305k, 500-world maxDD ranks 1.00; deflated Sharpe 0.66 (34% noise) vs 0.82 for the 3-parameter 'remove cap and week floor'. Soft locks (A1) lose mean for no DD; budgets cap the week not the maxDD; F1 live-fill reconciliation PENDING (no live file).
 V6: A-D cells on the exact path: none beats BEST on mean AND maxDD in both windows; vs LIVE the D3/C2/C3/D1 cells that help are weaker than removing cap+week floor; learned lock policy has no skill (rank corr -0.02); regime selectors drift to lock-free presets (maxDD 0.46-0.97M). B2/B3/C3-6J/F2 not run (stated).

## 2026-10-22T22:46:29Z v4+v5+v6 COMPLETE: REPORT_DS2_FIRM_V4.md, _V5.md, _V6.md delivered. Workers released (replays done, nulls done). Pending: F1 (live StratTrades file), data_free extensions for V6 C3/E3 (need prereg addenda before scoring).

## interim 2026-10-22T22:46Z
## DS2-FIRM v4 (top priority) - tables in order W1, W3, W2, W4, W5, W6 (22:46Z); ALL v4/v5/v6 DONE - workers released; v4 prereg frozen; v3 report autopilot/REPORT_DS2_FIRM_V3.md (done)
W1 HEADLINE (exact engine, fixed 60/14, 160 runs + 1,000 placebo worlds; no L2 layer needed): the week floor 8R and the combined cap 8R do NOT earn their keep in WF. Live minus week floor: WF 29.2k (+4.2k) / maxDD 325k (-76k) / IS 18.8k vs 13.7k, maxDD 293k vs 407k, L8W identical (floor did not fire); CI of mean delta [+0.7k,+8.3k], 8/11 folds mean, 4/11 maxDD; real floor is WORSE than a random-time week lock (placebo rank 0.12 mean / 0.15 maxDD) - it fires at bad times; cost = worst week -211k vs -137k. Live minus cap AND week (per-book day + give-back only): WF 34.7k (+9.8k) / SD 111k / maxDD 325k (-76k), L8W 41.6k (+7.4k) / 267k (tie), IS 19.0k / 293k; CI [+5.3k,+15.1k], halves 14.1k/6.2k, 10/11 folds on mean, 4/11 on maxDD; worst week -211k. The give-back arm is the only lock with clear value (removing it: maxDD +245k); per-book rule mostly protects maxDD (+104k without it); 5R week floor ($84k) is worse than 8R on every line; arm 3R, keep 67 and Asia-only/RTH-only give-back raise mean in places but raise maxDD (Asia-only gb: WF 39.3k but maxDD 598k). White reality check over 128 configs: best-by-mean p=0.012 (gb_asia), best-by-maxDD p=0.999 (maxDD gains are not distinguishable from selection noise). Lock-flatten extra slip +1 pt moves means by <1.2k, no ranking change.
All 32 subsets (sorted by WF maxDD; the benchmark = pb+cap+gb+wk8). Folds: number of the 11 read windows in which the subset beats the benchmark on mean / on maxDD.**

| locks | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W SD | L8W maxDD | IS mean | IS maxDD | folds mean/DD better | WF d mean | WF d maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| pb+cap+gb | 29.2k | 101.9k | 325.0k | -211.3k | 34.2k | 109.4k | 267.1k | 18.8k | 293.4k | 8/4 | 4.2k | -76.3k |
| pb+gb | 34.7k | 111.3k | 325.0k | -211.3k | 41.6k | 123.4k | 267.1k | 19.0k | 293.4k | 10/4 | 9.8k | -76.3k |
| pb+gb+wk8 | 30.1k | 113.7k | 370.0k | -137.1k | 41.6k | 123.4k | 267.1k | 13.9k | 407.3k | 10/1 | 5.1k | -31.3k |
| pb+cap+gb+wk8 | 25.0k | 104.5k | 401.3k | -137.1k | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k | 0/0 | 0.0k | 0.0k |
| pb+gb+wk5 | 26.5k | 111.0k | 479.3k | -145.0k | 27.5k | 132.8k | 335.0k | 13.4k | 442.8k | 7/6 | 1.6k | 78.0k |
| pb+gb+wk8+wk5 | 26.5k | 111.0k | 479.3k | -145.0k | 27.5k | 132.8k | 335.0k | 13.4k | 442.8k | 7/6 | 1.6k | 78.0k |
| pb+cap+gb+wk8+wk5 | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 13.1k | 442.8k | 4/6 | -2.8k | 78.0k |
| pb+cap+gb+wk5 | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 13.1k | 442.8k | 4/6 | -2.8k | 78.0k |
| gb | 36.6k | 135.6k | 494.0k | -316.6k | 49.8k | 192.4k | 352.8k | 16.8k | 403.4k | 9/4 | 11.6k | 92.7k |
| cap+gb | 28.8k | 121.3k | 494.0k | -316.6k | 29.8k | 150.8k | 352.8k | 16.5k | 403.4k | 8/4 | 3.9k | 92.7k |
| gb+wk8 | 31.4k | 134.1k | 505.7k | -140.6k | 58.4k | 180.6k | 284.2k | 3.4k | 660.6k | 7/4 | 6.5k | 104.4k |
| cap+gb+wk8 | 24.0k | 119.9k | 505.7k | -140.6k | 38.4k | 136.9k | 284.2k | 3.1k | 660.6k | 6/4 | -1.0k | 104.4k |
| pb+cap+wk8 | 39.5k | 135.3k | 646.5k | -137.2k | 68.8k | 186.6k | 498.4k | 1.3k | 621.3k | 8/1 | 14.5k | 245.2k |
| pb+cap+wk5 | 36.9k | 127.8k | 663.3k | -97.6k | 71.2k | 175.0k | 352.8k | 0.0k | 498.2k | 7/1 | 11.9k | 262.0k |
| pb+cap+wk8+wk5 | 36.9k | 127.8k | 663.3k | -97.6k | 71.2k | 175.0k | 352.8k | 0.0k | 498.2k | 7/1 | 11.9k | 262.0k |
| pb+wk8+wk5 | 40.1k | 134.4k | 735.4k | -102.9k | 67.8k | 179.8k | 275.2k | -0.5k | 498.2k | 7/1 | 15.1k | 334.1k |
| pb+wk5 | 40.1k | 134.4k | 735.4k | -102.9k | 67.8k | 179.8k | 275.2k | -0.5k | 498.2k | 7/1 | 15.1k | 334.1k |
| pb+cap | 39.3k | 142.3k | 761.2k | -296.0k | 43.6k | 219.6k | 699.4k | 4.8k | 639.0k | 7/1 | 14.3k | 359.9k |
| pb+wk8 | 44.9k | 141.1k | 762.2k | -137.2k | 70.3k | 188.6k | 402.3k | 1.6k | 648.6k | 9/1 | 19.9k | 361.0k |
| cap+wk8+wk5 | 29.6k | 140.4k | 818.3k | -91.7k | 80.5k | 188.1k | 366.9k | -19.8k | 1363.6k | 5/1 | 4.7k | 417.0k |
| cap+wk5 | 29.6k | 140.4k | 818.3k | -91.7k | 80.5k | 188.1k | 366.9k | -19.8k | 1363.6k | 5/1 | 4.7k | 417.0k |
| wk5 | 34.1k | 150.4k | 818.3k | -91.7k | 76.4k | 193.3k | 256.5k | -19.8k | 1363.6k | 7/1 | 9.1k | 417.0k |
| wk8+wk5 | 34.1k | 150.4k | 818.3k | -91.7k | 76.4k | 193.3k | 256.5k | -19.8k | 1363.6k | 7/1 | 9.1k | 417.0k |
| cap+wk8 | 38.0k | 152.6k | 839.4k | -142.5k | 107.8k | 201.3k | 481.3k | -1.0k | 670.2k | 7/1 | 13.0k | 438.1k |
| wk8 | 41.7k | 161.9k | 885.6k | -142.5k | 106.6k | 208.7k | 369.0k | -0.5k | 670.2k | 8/1 | 16.8k | 484.3k |
| pb | 44.3k | 149.5k | 895.0k | -296.0k | 28.4k | 242.5k | 737.1k | 5.0k | 639.0k | 8/1 | 19.3k | 493.7k |
| cap | 43.1k | 160.4k | 903.6k | -458.8k | 71.4k | 256.4k | 772.4k | 4.3k | 754.2k | 8/2 | 18.1k | 502.3k |
| gb+wk5 | 28.2k | 127.5k | 935.8k | -89.3k | 33.5k | 179.3k | 223.5k | 0.4k | 866.0k | 5/5 | 3.2k | 534.6k |
| gb+wk8+wk5 | 28.2k | 127.5k | 935.8k | -89.3k | 33.5k | 179.3k | 223.5k | 0.4k | 866.0k | 5/5 | 3.2k | 534.6k |
| cap+gb+wk8+wk5 | 20.7k | 112.5k | 935.8k | -89.3k | 13.5k | 130.8k | 223.5k | -0.4k | 866.0k | 4/5 | -4.3k | 534.6k |
| cap+gb+wk5 | 20.7k | 112.5k | 935.8k | -89.3k | 13.5k | 130.8k | 223.5k | -0.4k | 866.0k | 4/5 | -4.3k | 534.6k |
| none | 46.9k | 171.8k | 1037.3k | -458.8k | 53.5k | 287.7k | 793.3k | 4.9k | 754.2k | 9/2 | 21.9k | 636.0k |

**What each lock earns: benchmark minus that lock (paired, exact), with 200 random-trigger placebo worlds** (placebo = the lock replaced by a random-time lock with the same in-situ fire frequency; rank = share of placebo worlds the REAL config beats; for maxDD rank = share of placebo worlds with a larger maxDD than the real config)

| lock removed | config without it | WF mean (delta vs live) | WF SD | WF maxDD (delta) | WF worst | L8W mean / maxDD | IS mean / maxDD | folds better: mean / maxDD | boot90 CI of weekly mean delta (without - live) | placebo WF mean (mean +- sd) / maxDD | real-vs-placebo rank mean / maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|
| pb | cap+gb+wk8 | 24.0k (-1.0k) | 119.9k | 505.7k (+104k) | -140.6k | 38.4k / 284.2k | 3.1k / 660.6k | 6 / 4 | [-8.0k, 6.3k], halves -2.2k/-0.0k | 22.1k +- 6.3k / 673.8k | 0.67 / 0.99 |
| cap | pb+gb+wk8 | 30.1k (+5.1k) | 113.7k | 370.0k (-31k) | -137.1k | 41.6k / 267.1k | 13.9k / 407.3k | 10 / 1 | [2.7k, 7.9k], halves 6.1k/4.3k | 29.9k +- 1.4k / 378.8k | 0.00 / 0.13 |
| gb | pb+cap+wk8 | 39.5k (+14.5k) | 135.3k | 646.5k (+245k) | -137.2k | 68.8k / 498.4k | 1.3k / 621.3k | 8 / 1 | [0.5k, 27.4k], halves 4.7k/22.6k | 33.5k +- 5.5k / 653.2k | 0.05 / 0.99 |
| wk8 | pb+cap+gb | 29.2k (+4.2k) | 101.9k | 325.0k (-76k) | -211.3k | 34.2k / 267.1k | 18.8k / 293.4k | 8 / 4 | [0.7k, 8.3k], halves 6.9k/2.0k | 27.4k +- 2.0k / 357.9k | 0.12 / 0.15 |
| cap+wk8 | pb+gb | 34.7k (+9.8k) | 111.3k | 325.0k (-76k) | -211.3k | 41.6k / 267.1k | 19.0k / 293.4k | 10 / 4 | [5.3k, 15.1k], halves 14.1k/6.2k | 31.9k +- 2.7k / 361.9k | 0.01 / 0.18 |

Week floor 5R ($84k) instead of 8R: WF 22.1k / SD 101.2k / maxDD 479.3k / worst -145.0k; L8W 20.1k / maxDD 335.0k - worse than 8R on every line.

**WEEK-FLOOR FINDING (confirmed on the exact engine).** Live minus the week floor (pb+cap+gb): WF 29.2k vs 25.0k (+4.2k/wk), maxDD 325.0k vs 401.3k (-76k), SD 101.9k vs 104.5k, worst week -211.3k vs -137.1k (the floor's one real job: it caps the worst week); IS 18.8k/293.4k vs 13.7k/407.3k; L8W identical (the floor did not fire in the last 8 weeks, so L8W cannot confirm or refute). Bootstrap 90% CI of the WF weekly mean delta [0.7k, 8.3k], halves 6.9k / 2.0k; better in 8 of 11 folds on mean and 4 of 11 on maxDD. Placebo (200 random-time week locks with the floor's in-situ fire frequency 0.135 per week): real floor ranks mean 0.125, maxDD 0.150 - the real floor fires at systematically worse times than random. Lock-flatten slip +1.0 pt on both configs: see sensitivity table. Weekly mean +4.2k and maxDD -76k WITHOUT the floor, bought at a worst week of -211.3k instead of -137.1k.

V5 INTERIM (riskeng: new stateful 1-s engine reproduces the hard-lock benchmark within 0.1%: WF 24,978 vs 24,975, maxDD 401.6k vs 401.3k; 0.2 s per run).
A1 SOFT LOCKS (108 cells: day steps x give-back-touched lots x week-floor lots x scope; exact fixed-60 path; WF mean/SD/maxDD): live 25k/105k/402k; 0 of 108 beat live on WF mean AND maxDD; lowest-maxDD soft cells: d8-0|gb0|wk8|sc0 24k/100k/338k (L8W 14k/338k); d8-0|gb0|wk8|sc1 20k/108k/339k (L8W 33k/271k); d8-4|gb0|wk8|sc1 21k/109k/349k (L8W 31k/285k); d6-4|gb0|wk8|sc1 20k/105k/351k (L8W 32k/243k). Softening trades mean for DD at best 1:1 (d8-0|gb0|wk8: -1.0k mean, -64k maxDD, L8W much worse 14.1k) - every soft cell is below live on WF mean, none improves both windows.
C1/C2 RISK BUDGETS (no halts; locks OFF; WF mean/SD/maxDD/worst): NOLOCK 46.9k/171.8k/1037k/-459k; daily 30k 30.7k/128.5k/963k; daily 40k 35.2k/141.6k/1325k; daily 50k 37.1k/145.5k/1291k; weekly 100k 39.4k/154.0k/816k/-103k; weekly 134k 42.3k/160.7k/811k/-136k; weekly 170k 41.6k/167.2k/862k/-175k; day30k+wk100k 30.8k/123.7k/743k/-101k (best budget cell). Budgets cap the worst week (as the week floor) but do not cap maxDD (0.74-1.3M vs live 401k): a budget that only counts realized P&L and open stop risk cannot replace the give-back arm, which is the lock that controls drawdown.
V5 D1 JOINT SCREEN (riskeng, 17,280 of 20,160 cells so far: options live60 / live60_P9 / 4 ATR20 cells; W3 centre options pending the union replay): 0 cells meet the strict objective (WF mean >= benchmark AND maxDD <= 0.7 x benchmark). Closest: maxDD 0.72 x benchmark with mean >= benchmark. BEST EXACT CELL (fixed 60, corrected-P9 points, no L2 layer needed): per-book day rule LIVE, combined cap OFF, give-back arm 2R KEEP 67% armed only after >= 2 closed trades, week floor 12R (or off), session lots Asia 14 / London 10 / NY 10: WF 25.5k / SD 93.1k / maxDD 287k / worst -185k (benchmark 25.0k / 104.5k / 401k / -137k); L8W 56.1k / maxDD 183k (34.2k / 267k); IS 13.2k / 305k (13.7k / 407k). 500-world nulls: maxDD rank 1.00 vs placebo locks (placebo maxDD ~620k) and 1.00 vs random-subset down-sizing (mean rank 0.98); mean rank vs placebo locks only 0.42 (the gain is drawdown, not income). H1->H2 frozen holdout over all screened cells: 36% of H1 winners also beat live on H2 (top-5 frozen: all 5 beat live on H2 mean and maxDD). Parameter count 8 changes vs live; deflated Sharpe in the final report. NOT yet: strict-objective pass (none), direct replay of non-60 options, fold stability top-quartile counts, W3 centres.V4/V5/V6 STATUS (reports: autopilot/REPORT_DS2_FIRM_V4.md, _V5.md, _V6.md): 
 W1 (exact): live minus week floor +4.2k/wk WF, maxDD -76k (placebo rank 0.12/0.15: fires at worse-than-random times); live minus cap AND week floor: WF 34.7k (+9.8k), maxDD 325k (-76k), IS 19.0k/294k, L8W 41.6k/267k (tie); worst week -211k vs -137k. Direct-replay-policy check: +8.8k / -24k. 
 W3 centres FAIL direct replay (honest centre: maxDD +13k worse than the replay-policy live pair, L8W 29.0k vs 45.8k); live cell rank 67/75 in WF but 22/75 in IS (grid flat and noisy). W2 ATR brackets at 14/14/14 flip the DD sign on replay (539-566k vs 371k). W4: London/NY 10 lots beats random down-sizing (rank >= 0.96). W5: 2 of 60 joint cells beat the replay-policy live pair on both windows (both fixed-60 pb+gb with London/NY 10/8-10 lots). W6: ATR cells hold on DD but fail mean/IS.
 V5: strict objective (mean >= benchmark AND maxDD <= 0.7x) met by 0 of 23,040 screened cells; closest 0.72x. Best exact cell (BEST5): per-book rule live, cap OFF, give-back keep 67% armed after 2 trades, week floor 12R, London/NY 10 lots: WF 25.5k/93.1k/287k, L8W 56.1k/183k, IS 13.2k/305k, 500-world maxDD ranks 1.00; deflated Sharpe 0.66 (34% noise) vs 0.82 for the 3-parameter 'remove cap and week floor'. Soft locks (A1) lose mean for no DD; budgets cap the week not the maxDD; F1 live-fill reconciliation PENDING (no live file).
 V6: A-D cells on the exact path: none beats BEST on mean AND maxDD in both windows; vs LIVE the D3/C2/C3/D1 cells that help are weaker than removing cap+week floor; learned lock policy has no skill (rank corr -0.02); regime selectors drift to lock-free presets (maxDD 0.46-0.97M). B2/B3/C3-6J/F2 not run (stated).

## 2026-10-23T14:17Z F1 live-vs-replay (data/live push): live stop-join rate 8/17 = 0.47 (95% CI 0.23-0.72) vs replay 0.78; 1 rejected join attempt(s); stop exits -2.01 pt vs stop level (replay -0.52); entry slip PENDING. Addendum in REPORT_DS2_FIRM_V5.md (marker F1-ADDENDUM).

## PBDAY (2026-10-23 15:35Z)
PREREG_PBDAY frozen (sha 28745a4c...), 19 cells + 9,000 null worlds + 11-fold stability + walk-forward l + frozen holdout + bootstrap + DSR (n=3,601) + interaction table done. Verdict: relaxing the per-book day loss is NOT SUPPORTED in either layer (live: WF -0.3k..-2.9k/wk, maxDD +7..26%, worst day -101k -> -134k..-221k; Set B: +0.3k..+2.4k/wk, CI spans 0, shuffled-date rank 0.00-0.20, 6/11 folds). Set B itself is the only supported lever (+8.1k vs live, CI [+1.8k,+15.1k]). REPORT_PBDAY.md. Code: firm/riskeng_pb.py, pbd_run.py, pbd_stats.py; out/pbday/.

## 2026-10-23T22:13Z F1 live-vs-replay (data/live push): live stop-join rate 8/17 = 0.47 (95% CI 0.23-0.72) vs replay 0.78; 1 rejected join attempt(s); stop exits -2.01 pt vs stop level (replay -0.52); entry slip PENDING. Addendum in REPORT_DS2_FIRM_V5.md (marker F1-ADDENDUM).

## 2026-10-26T22:14Z F1 live-vs-replay (data/live push): live stop-join rate 8/20 = 0.40 (95% CI 0.19-0.64) vs replay 0.78; 1 rejected join attempt(s); stop exits -2.45 pt vs stop level (replay -0.52); entry slip PENDING. Addendum in REPORT_DS2_FIRM_V5.md (marker F1-ADDENDUM).
