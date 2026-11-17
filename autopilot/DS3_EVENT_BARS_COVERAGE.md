# DS3_EVENT_BARS_COVERAGE (W-BAR; regenerated)
VERDICT (data ends 2026-11-13; ): registry coverage list; 20 coverage rows of the 1802Z order mapped to registry ids below. built = parquet exists; property-screened = row in DS3_BAR_PROPS; scored/survivor columns are filled by W-SWA/W-SWB book-on-bar pages (none yet).

20-row map: time=time_s,time_m; tick=tick; volume=vol; dollar=dol; volume-clock=vsess; tick-imbalance=tib,trb; volume/dollar-imbalance=vib,dib; run=trb,vrb,drb; range=rng; Renko/UniRenko=renko,mrenko,urenko,frenko,wrenko; delta=dlt,cdr; volatility-normalised=vnorm; quote/mid=qmid,micro (W-BAR2); book-event clock=bmsg (W-BAR2); directional-change/CUSUM=dchg,cusum; point-and-figure/Kagi/line-break=pnf,kagi,lbrk; profile periods=tpo (W-BAR2); footprint=vfp (W-BAR2); anchored=anch (W-BAR2); smoothing transforms=ha,smooth (W-BAR2).

| id | family | builder | status | NT8 native or custom | scored by books | survivor |
|---|---|---|---|---|---|---|
| time_s | TIME | W-BAR | built / property-screened | native Second (NT8 Period Type Second) | not yet | - |
| time_m | TIME | W-BAR | built / property-screened | native Minute | not yet | - |
| tick | ACTIVITY | W-BAR | built / property-screened | native Tick | not yet | - |
| vol | ACTIVITY | W-BAR | built / property-screened | native Volume | not yet | - |
| dol | ACTIVITY | W-BAR | built / property-screened | custom BarsType (user already has one): sum(Close*20*Volume) threshold | not yet | - |
| vsess | ACTIVITY | W-BAR | built / property-screened | custom BarsType (volume threshold set at session start from a trailing table) | not yet | - |
| tsf | ACTIVITY | W-BAR | built / property-screened | custom BarsType (filter on tick size) | not yet | - |
| tib | INFORMATION | W-BAR | built / property-screened | custom BarsType (stateful EWMA; buildable, new code) | not yet | - |
| vib | INFORMATION | W-BAR | built / property-screened | custom BarsType (stateful EWMA; buildable, new code) | not yet | - |
| dib | INFORMATION | W-BAR | built / property-screened | custom BarsType (stateful EWMA; buildable, new code) | not yet | - |
| trb | INFORMATION | W-BAR | built / property-screened | custom BarsType (new code) | not yet | - |
| vrb | INFORMATION | W-BAR | built / property-screened | custom BarsType (new code) | not yet | - |
| drb | INFORMATION | W-BAR | built / property-screened | custom BarsType (new code) | not yet | - |
| dlt | INFORMATION | W-BAR | built / property-screened | custom BarsType (NT8 DeltaBars style; buildable) | not yet | - |
| cdr | INFORMATION | W-BAR | built / property-screened | custom BarsType | not yet | - |
| vnorm | INFORMATION | W-BAR | built / property-screened | custom BarsType | not yet | - |
| cusum | INFORMATION | W-BAR | built / property-screened | custom BarsType (event-driven) | not yet | - |
| dchg | INFORMATION | W-BAR | built / property-screened | custom BarsType (zigzag-like; same as swing by ticks) | not yet | - |
| rng | PRICE | W-BAR | built / property-screened | native Range (verify: NT8 closes when range reaches N ticks; see step C) | not yet | - |
| renko | PRICE | W-BAR | built / property-screened | native Renko | not yet | - |
| mrenko | PRICE | W-BAR | built / property-screened | custom BarsType (MedianRenko / MeanRenko third-party) | not yet | - |
| urenko | PRICE | W-BAR | built / property-screened | custom BarsType (user has UniRenko) | not yet | - |
| frenko | PRICE | W-BAR | built / property-screened | custom BarsType (FlexRenko/HybridRenko third-party) | not yet | - |
| wrenko | PRICE | W-BAR | built / property-screened | custom BarsType (BetterRenko third-party) | not yet | - |
| pnf | PRICE | W-BAR | built / property-screened | native PointAndFigure | not yet | - |
| kagi | PRICE | W-BAR | built / property-screened | native Kagi | not yet | - |
| lbrk | PRICE | W-BAR | built / property-screened | native LineBreak (3 lines; N-line custom) | not yet | - |
| swing | PRICE | W-BAR | built / property-screened | custom BarsType (ZigZag-style) | not yet | - |
| mom | PRICE | W-BAR | built / property-screened | custom BarsType (MomentumBars third-party) | not yet | - |
| trend | PRICE | W-BAR | planned | custom BarsType (TrendBars third-party) | not yet | - |
| pasl | PRICE | W-BAR | planned | custom BarsType | not yet | - |
| rngor | COMPOSITE | W-BAR2 | planned | custom BarsType | not yet | - |
| volor | COMPOSITE | W-BAR2 | planned | custom BarsType | not yet | - |
| dltor | COMPOSITE | W-BAR2 | planned | custom BarsType | not yet | - |
| ha | SMOOTHING | W-BAR2 | built | native HeikenAshi (BarsType) / custom for event bases | not yet | - |
| smooth | SMOOTHING | W-BAR2 | planned | custom BarsType or indicator on the base | not yet | - |
| vfp | FOOTPRINT | W-BAR2 | built | native Volumetric (NT8 Volumetric bars type) | not yet | - |
| tpo | PROFILE | W-BAR2 | built | custom (Market Profile) | not yet | - |
| anch | ANCHORED | W-BAR2 | built | custom BarsType | not yet | - |
| qmid | ACTIVITY(book) | W-BAR2 | planned | custom BarsType (L1 quote events; NT8 supports OnMarketData) | not yet | - |
| micro | ACTIVITY(book) | W-BAR2 | planned | custom BarsType | not yet | - |
| bmsg | ACTIVITY(book) | W-BAR2 | planned | custom BarsType (needs L3/depth messages; NT8 OnMarketDepth) | not yet | - |
| entropy | INFORMATION(book) | W-BAR2 | built | custom BarsType | not yet | - |
| sessrng | SESSION-RELATIVE | W-BAR2 | built | custom BarsType | not yet | - |
