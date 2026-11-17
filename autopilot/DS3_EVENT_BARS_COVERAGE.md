# DS3_EVENT_BARS_COVERAGE (W-BAR; regenerated every 30 min from the registry and the swap pages)
VERDICT (data ends 2026-11-13; pick rule: trailing 6M, validated by rolling walk-forward on the swap pages): coverage of the 20 requested bar families and the full registry. built = parquet exists; property-screened = row in DS3_BAR_PROPS; scored = the type appears in a ranked table of DS3_BAR_SWAP_A/B (count of book-session sections); survivor = appears with gate = yes. Nothing is a pick here.

## 20-row table
| # | family | registry ids | built | scored (sections) | survivor (gate yes) | NT8 |
|---|---|---|---|---|---|---|
| 1 | time | time_s,time_m | 2/2 | 6 | - | native |
| 2 | tick | tick | 1/1 | 2 | - | native |
| 3 | volume | vol | 1/1 | 2 | - | native |
| 4 | dollar | dol | 1/1 | 3 | - | custom |
| 5 | volume-clock | vsess | 1/1 | 4 | - | custom |
| 6 | tick-imbalance | tib,trb | 2/2 | 5 | - | custom |
| 7 | volume/dollar-imbalance | vib,dib | 2/2 | 4 | - | custom |
| 8 | run | trb,vrb,drb | 3/3 | 7 | - | custom |
| 9 | range | rng | 1/1 | 1 | - | native |
| 10 | Renko/UniRenko | renko,mrenko,urenko,frenko,wrenko | 5/5 | 13 | - | custom/native |
| 11 | delta | dlt,cdr | 2/2 | 3 | - | custom |
| 12 | volatility-normalised | vnorm | 1/1 | 1 | - | custom |
| 13 | quote/mid | qmid,micro | 2/2 | 0 | - | custom |
| 14 | book-event clock | bmsg | 1/1 | 0 | - | custom |
| 15 | directional-change/CUSUM | dchg,cusum | 2/2 | 3 | - | custom |
| 16 | point-and-figure/Kagi/line-break | pnf,kagi,lbrk | 3/3 | 5 | - | native |
| 17 | profile periods | tpo | 1/1 | 0 | - | custom |
| 18 | footprint | vfp | 1/1 | 0 | - | native |
| 19 | anchored | anch | 1/1 | 0 | - | custom |
| 20 | smoothing transforms | ha,smooth | 1/2 | 0 | - | custom/native |

## Full registry
| id | family | builder | status | NT8 native or custom | scored sections | survivor |
|---|---|---|---|---|---|---|
| time_s | TIME | W-BAR | built / property-screened | native Second (NT8 Period Type Second) | 0 | - |
| time_m | TIME | W-BAR | built / property-screened | native Minute | 6 | - |
| tick | ACTIVITY | W-BAR | built / property-screened | native Tick | 2 | - |
| vol | ACTIVITY | W-BAR | built / property-screened | native Volume | 2 | - |
| dol | ACTIVITY | W-BAR | built / property-screened | custom BarsType (user already has one): sum(Close*20*Volume) threshold | 3 | - |
| vsess | ACTIVITY | W-BAR | built / property-screened | custom BarsType (volume threshold set at session start from a trailing table) | 4 | - |
| tsf | ACTIVITY | W-BAR | built / property-screened | custom BarsType (filter on tick size) | 3 | - |
| tib | INFORMATION | W-BAR | built / property-screened | custom BarsType (stateful EWMA; buildable, new code) | 2 | - |
| vib | INFORMATION | W-BAR | built / property-screened | custom BarsType (stateful EWMA; buildable, new code) | 1 | - |
| dib | INFORMATION | W-BAR | built / property-screened | custom BarsType (stateful EWMA; buildable, new code) | 3 | - |
| trb | INFORMATION | W-BAR | built / property-screened | custom BarsType (new code) | 3 | - |
| vrb | INFORMATION | W-BAR | built / property-screened | custom BarsType (new code) | 2 | - |
| drb | INFORMATION | W-BAR | built / property-screened | custom BarsType (new code) | 2 | - |
| dlt | INFORMATION | W-BAR | built / property-screened | custom BarsType (NT8 DeltaBars style; buildable) | 3 | - |
| cdr | INFORMATION | W-BAR | built / property-screened | custom BarsType | 0 | - |
| vnorm | INFORMATION | W-BAR | built / property-screened | custom BarsType | 1 | - |
| cusum | INFORMATION | W-BAR | built / property-screened | custom BarsType (event-driven) | 1 | - |
| dchg | INFORMATION | W-BAR | built / property-screened | custom BarsType (zigzag-like; same as swing by ticks) | 2 | - |
| rng | PRICE | W-BAR | built / property-screened | native Range (verify: NT8 closes when range reaches N ticks; see step C) | 1 | - |
| renko | PRICE | W-BAR | built / property-screened | native Renko | 1 | - |
| mrenko | PRICE | W-BAR | built / property-screened | custom BarsType (MedianRenko / MeanRenko third-party) | 6 | - |
| urenko | PRICE | W-BAR | built / property-screened | custom BarsType (user has UniRenko) | 2 | - |
| frenko | PRICE | W-BAR | built / property-screened | custom BarsType (FlexRenko/HybridRenko third-party) | 2 | - |
| wrenko | PRICE | W-BAR | built / property-screened | custom BarsType (BetterRenko third-party) | 2 | - |
| pnf | PRICE | W-BAR | built / property-screened | native PointAndFigure | 2 | - |
| kagi | PRICE | W-BAR | built / property-screened | native Kagi | 2 | - |
| lbrk | PRICE | W-BAR | built / property-screened | native LineBreak (3 lines; N-line custom) | 1 | - |
| swing | PRICE | W-BAR | built / property-screened | custom BarsType (ZigZag-style) | 0 | - |
| trend | PRICE | W-BAR | built | custom BarsType (NT8 TrendBars-style) | 0 | - |
| mom | PRICE | W-BAR | built / property-screened | custom BarsType (MomentumBars third-party) | 0 | - |
| pasl | PRICE | W-BAR | built | custom BarsType | 0 | - |
| rngor | COMPOSITE | W-BAR2 | built | custom BarsType | 0 | - |
| volor | COMPOSITE | W-BAR2 | built | custom BarsType | 0 | - |
| dltor | COMPOSITE | W-BAR2 | built | custom BarsType | 0 | - |
| ha | SMOOTHING | W-BAR2 | built | native HeikenAshi (BarsType) / custom for event bases | 0 | - |
| smooth | SMOOTHING | W-BAR2 | planned | custom BarsType or indicator on the base | 0 | - |
| vfp | FOOTPRINT | W-BAR2 | built | native Volumetric (NT8 Volumetric bars type) | 0 | - |
| tpo | PROFILE | W-BAR2 | built | custom (Market Profile) | 0 | - |
| anch | ANCHORED | W-BAR2 | built | custom BarsType | 0 | - |
| qmid | ACTIVITY(book) | W-BAR2 | built | custom BarsType (L1 quote events; NT8 supports OnMarketData) | 0 | - |
| micro | ACTIVITY(book) | W-BAR2 | built | custom BarsType | 0 | - |
| bmsg | ACTIVITY(book) | W-BAR2 | built | custom BarsType (needs L3/depth messages; NT8 OnMarketDepth) | 0 | - |
| entropy | INFORMATION(book) | W-BAR2 | built | custom BarsType | 0 | - |
| sessrng | SESSION-RELATIVE | W-BAR2 | built | custom BarsType | 0 | - |
