# CONFLUENCE_DEFS_CF4 (W-CF4, Block 2 / Block 4). Auto-built by code/th_confl_cf4/c4_page.py

Key: `sid` = <book>_<sig_ns> (JN05W2 trades.parquet; W-CF1 entry-table id to be mapped by sig_ns). Files: /mnt/l2/l2vast/_confl/cols_cf4/cf4_<sub>.parquet. int8 columns: 1 yes, 0 no, -1 unknown. Raw value of the indicator beside each: `v_<ind>_<tf>` (float32).
Column name: c4_<indicator>_<tf>_<cond>, tf in 1m,3m,5m,15m,60m,1d. Bars: 1m from /mnt/l2/l2vast/_th_sz/bars1m_NQ.npz; HTF bars aligned to epoch (daily = Globex day, 18:00 ET); a bar is used only if its END <= signal second (completed bars only; no repainting anywhere).
Conditions (template): `side` state on trade side (x vs mid, or sign of the state); `sig` x on trade side of its signal line; `rise` x moving with the trade vs 1 bar ago; `fresh5` fresh signal (cross of signal line / midline / explicit event) with the trade within the last 5 bars, `fresh1` on the last bar; `ewith`/`eagainst` in the extreme zone on / against the trade side (z1,z2 = two zone sets); `eleave` left the zone against the trade within 3 bars; `eenter` entered the with-trade extreme within 3 bars; `nodiv`/`divwith` no divergence against / divergence in favour at the last two fractal swings (k=2) of that TF; `mtf_n` (raw count 0-6), `mtf_ge4`, `mtf_all` = number of timeframes (1,3,5,15,60,1d) where `side` is yes. unsigned indicators: `hi`,`lo_z`,`hi_z`,`rise`. Fast/slow variants are suffixed F / S (standard published setting has no suffix).

## B2-A momentum / oscillators: 3144 condition columns, 71 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|
| wt | PUBLIC LazyBear WaveTrend (10,21) | osc |
| wtF | PUBLIC LazyBear WaveTrend (6,12) | osc |
| wtS | PUBLIC LazyBear WaveTrend (14,30) | osc |
| sqzm_mom | PUBLIC LazyBear squeeze momentum value (20) | osc |
| sqzm_on | PUBLIC: BB(20,2) inside KC(20,1.5 SMA-TR) | osc |
| sqzm_bright | PUBLIC 4-colour histogram: positive rising / negative falling | osc |
| sqzmF_mom | PUBLIC LazyBear squeeze momentum value (12) | osc |
| sqzmF_on | PUBLIC: BB(12,2) inside KC(12,1.5 SMA-TR) | osc |
| sqzmF_bright | PUBLIC 4-colour histogram: positive rising / negative falling | osc |
| sqzmS_mom | PUBLIC LazyBear squeeze momentum value (34) | osc |
| sqzmS_on | PUBLIC: BB(34,2) inside KC(34,1.5 SMA-TR) | osc |
| sqzmS_bright | PUBLIC 4-colour histogram: positive rising / negative falling | osc |
| mcwt | APPROXIMATION of Market Cipher B: WT(9,12,3); dots = WT cross while WT2 beyond +-53 (ev) | osc |
| mcmf | APPROXIMATION: money flow = SMA60 of 150*(close-open)/(high-low) | osc |
| mc_comp | APPROXIMATION: WT1>WT2, money flow>0, RSI14>50 all agree (+1/-1) | osc |
| mc_comp2 | APPROXIMATION: sum of 3 signs | osc |
| qqe | PUBLIC QQE (RSI 14, SF 5, factor 4.236), trailing line by Wilder-ATR of smoothed RSI | osc |
| qqeF | PUBLIC QQE (RSI 7, SF 3, factor 3.000), trailing line by Wilder-ATR of smoothed RSI | osc |
| qqeS | PUBLIC QQE (RSI 21, SF 8, factor 4.236), trailing line by Wilder-ATR of smoothed RSI | osc |
| qqemod | APPROXIMATION of QQE Mod (Mihkel00): RSI6 sf5 factor3; colour bar = RSI-50 beyond +-3 AND outside BB(50,0.35) of the QQE line | osc |
| qqemod_hist | QQE Mod histogram RSI(6)-50 | osc |
| rsima14 | PUBLIC RSI(14) vs its SMA14; divergence at last fractal swing in template | osc |
| rsima7 | PUBLIC RSI(7) vs its SMA14; divergence at last fractal swing in template | osc |
| rsima21 | PUBLIC RSI(21) vs its SMA14; divergence at last fractal swing in template | osc |
| crsi | PUBLIC Connors RSI(3,2,100) | osc |
| crsiF | variant (2,2,50) | osc |
| srsi | PUBLIC StochRSI(14,14,3,3) | osc |
| srsiF | PUBLIC StochRSI(14,8,3,3) | osc |
| srsiS | PUBLIC StochRSI(14,21,3,3) | osc |
| stc | PUBLIC Schaff Trend Cycle (23,50,10,0.5) | osc |
| stcF | PUBLIC Schaff Trend Cycle (12,26,6,0.5) | osc |
| stcS | PUBLIC Schaff Trend Cycle (34,70,14,0.5) | osc |
| kst | PUBLIC Pring KST (10, 15, 20, 30) | osc |
| kstF | PUBLIC Pring KST (5, 8, 10, 15) | osc |
| kstS | PUBLIC Pring KST (20, 30, 40, 60) | osc |
| copp | PUBLIC Coppock WMA10(ROC14+ROC11) | osc |
| coppF | PUBLIC Coppock WMA6(ROC8+ROC6) | osc |
| coppS | PUBLIC Coppock WMA15(ROC21+ROC15) | osc |
| rvi | PUBLIC Ehlers/Donald Dorsey RVI(10), signal SWMA4 | osc |
| rviF | PUBLIC Ehlers/Donald Dorsey RVI(5), signal SWMA4 | osc |
| rviS | PUBLIC Ehlers/Donald Dorsey RVI(20), signal SWMA4 | osc |
| elder_bull | PUBLIC Elder Bull Power = high - EMA13 | osc |
| elder_bear | PUBLIC Elder Bear Power = low - EMA13 | osc |
| elder_impulse | PUBLIC Elder Impulse: EMA13 slope and MACD(12,26,9) hist slope both up (green) / down (red) | osc |
| elderF_bull | PUBLIC Elder Bull Power = high - EMA8 | osc |
| elderF_bear | PUBLIC Elder Bear Power = low - EMA8 | osc |
| elderF_impulse | PUBLIC Elder Impulse: EMA8 slope and MACD(12,26,9) hist slope both up (green) / down (red) | osc |
| elderS_bull | PUBLIC Elder Bull Power = high - EMA26 | osc |
| elderS_bear | PUBLIC Elder Bear Power = low - EMA26 | osc |
| elderS_impulse | PUBLIC Elder Impulse: EMA26 slope and MACD(12,26,9) hist slope both up (green) / down (red) | osc |
| smie | APPROXIMATION: SMI Ergodic = TSI(5,20) scaled 0-1, signal EMA5 | osc |
| smieF | APPROXIMATION: SMI Ergodic = TSI(3,10) scaled 0-1, signal EMA5 | osc |
| smieS | APPROXIMATION: SMI Ergodic = TSI(8,34) scaled 0-1, signal EMA5 | osc |
| smi | PUBLIC Blau SMI (10,3,3), signal EMA10 | osc |
| smiF | PUBLIC Blau SMI (5,3,3), signal EMA10 | osc |
| smiS | PUBLIC Blau SMI (21,5,5), signal EMA10 | osc |
| tsi | PUBLIC True Strength Index (25,13) signal EMA7 | osc |
| tsiF | PUBLIC True Strength Index (13,7) signal EMA7 | osc |
| tsiS | PUBLIC True Strength Index (40,20) signal EMA7 | osc |
| kvo | PUBLIC Klinger (34,55,13), cm resets on trend change | osc |
| kvoF | PUBLIC Klinger (14,28,7), cm resets on trend change | osc |
| kvoS | PUBLIC Klinger (55,89,21), cm resets on trend change | osc |
| chop | PUBLIC Choppiness Index(14); >61.8 choppy, <38.2 trending | osc |
| chopF | PUBLIC Choppiness Index(7); >61.8 choppy, <38.2 trending | osc |
| chopS | PUBLIC Choppiness Index(28); >61.8 choppy, <38.2 trending | osc |
| ker_abs | PUBLIC Kaufman efficiency ratio(10) | osc |
| ker_dir | signed Kaufman ER(10): direction x efficiency | osc |
| kerF_abs | PUBLIC Kaufman efficiency ratio(5) | osc |
| kerF_dir | signed Kaufman ER(5): direction x efficiency | osc |
| kerS_abs | PUBLIC Kaufman efficiency ratio(30) | osc |
| kerS_dir | signed Kaufman ER(30): direction x efficiency | osc |

## B2-B trend followers: 3330 condition columns, 103 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|
| utbot | PUBLIC UT Bot Alerts key=1 ATR=10 (close vs trailing stop; ev = buy/sell cross) | trend |
| utbotF | PUBLIC UT Bot Alerts key=1 ATR=5 (close vs trailing stop; ev = buy/sell cross) | trend |
| utbotS | PUBLIC UT Bot Alerts key=2 ATR=14 (close vs trailing stop; ev = buy/sell cross) | trend |
| chand | PUBLIC Chandelier Exit(22, ATR x3), ratcheting stops, dir flips when close crosses opposite stop | trend |
| chandF | PUBLIC Chandelier Exit(10, ATR x2), ratcheting stops, dir flips when close crosses opposite stop | trend |
| chandS | PUBLIC Chandelier Exit(44, ATR x4), ratcheting stops, dir flips when close crosses opposite stop | trend |
| ssl | PUBLIC SSL Channel(10): close > SMA(high) -> up, < SMA(low) -> down | trend |
| sslhyb | APPROXIMATION of SSL Hybrid (Mihkel00): baseline HMA60 side AND SSL(10) agree; exit SSL2 omitted | trend |
| sslF | PUBLIC SSL Channel(5): close > SMA(high) -> up, < SMA(low) -> down | trend |
| sslS | PUBLIC SSL Channel(20): close > SMA(high) -> up, < SMA(low) -> down | trend |
| hull | PUBLIC Hull Suite HMA(55) vs HMA 2 bars ago | trend |
| hull_px | price vs HMA(55) | trend |
| hullF | PUBLIC Hull Suite HMA(21) vs HMA 2 bars ago | trend |
| hullF_px | price vs HMA(21) | trend |
| hullS | PUBLIC Hull Suite HMA(89) vs HMA 2 bars ago | trend |
| hullS_px | price vs HMA(89) | trend |
| rfilt | PUBLIC Range Filter Buy&Sell (period 100, mult 3) | trend |
| rfilt_dir | filter direction (upward / downward run) | trend |
| rfiltF | PUBLIC Range Filter Buy&Sell (period 50, mult 2) | trend |
| rfiltF_dir | filter direction (upward / downward run) | trend |
| rfiltS | PUBLIC Range Filter Buy&Sell (period 200, mult 4) | trend |
| rfiltS_dir | filter direction (upward / downward run) | trend |
| halft | PUBLIC HalfTrend (everget/Alex Orekhov) amplitude=2 dev=2: trend flips on SMA(high/low) vs max-low/min-high and close vs prior bar extreme | trend |
| halftF | PUBLIC HalfTrend (everget/Alex Orekhov) amplitude=1 dev=2: trend flips on SMA(high/low) vs max-low/min-high and close vs prior bar extreme | trend |
| halftS | PUBLIC HalfTrend (everget/Alex Orekhov) amplitude=5 dev=2: trend flips on SMA(high/low) vs max-low/min-high and close vs prior bar extreme | trend |
| stA | PUBLIC Supertrend ATR(10) x3 on HL2 | trend |
| stAF | PUBLIC Supertrend ATR(7) x2 on HL2 | trend |
| stAS | PUBLIC Supertrend ATR(22) x4 on HL2 | trend |
| stA21 | PUBLIC Supertrend ATR(10) x2 on HL2 | trend |
| stP | PUBLIC Pivot Point SuperTrend (LonesomeTheBlue) pivot period 2 factor 3 atr 10 | trend |
| stPF | PUBLIC Pivot Point SuperTrend (LonesomeTheBlue) pivot period 1 factor 2 atr 10 | trend |
| stPS | PUBLIC Pivot Point SuperTrend (LonesomeTheBlue) pivot period 4 factor 4 atr 10 | trend |
| alligator | PUBLIC Williams Alligator 13/8/5 SMMA shifts 8/5/3, awake = lips>teeth>jaw (or reverse) | trend |
| alli_spread | lips - jaw in ATR (mouth opening) | trend |
| fractal_brk | PUBLIC Williams fractals (5-bar, confirmed 2 bars later): state = direction of last close break of the latest confirmed fractal | trend |
| fractal_alli | Williams: fractal break on the correct side of the Alligator teeth | trend |
| hilo | PUBLIC Gann HiLo Activator SMA(high/low,10) | trend |
| hiloF | PUBLIC Gann HiLo Activator SMA(high/low,5) | trend |
| hiloS | PUBLIC Gann HiLo Activator SMA(high/low,20) | trend |
| mcg_px | PUBLIC McGinley Dynamic N=14 | trend |
| mcg_slope | PUBLIC McGinley Dynamic N=14 (slope of the line) | trend |
| mcgF_px | PUBLIC McGinley Dynamic N=8 | trend |
| mcgF_slope | PUBLIC McGinley Dynamic N=8 (slope of the line) | trend |
| mcgS_px | PUBLIC McGinley Dynamic N=30 | trend |
| mcgS_slope | PUBLIC McGinley Dynamic N=30 (slope of the line) | trend |
| t3_px | PUBLIC Tillson T3 n=5 b=0.7 | trend |
| t3_slope | PUBLIC Tillson T3 n=5 b=0.7 (slope of the line) | trend |
| t3F_px | PUBLIC Tillson T3 n=3 b=0.7 | trend |
| t3F_slope | PUBLIC Tillson T3 n=3 b=0.7 (slope of the line) | trend |
| t3S_px | PUBLIC Tillson T3 n=10 b=0.7 | trend |
| t3S_slope | PUBLIC Tillson T3 n=10 b=0.7 (slope of the line) | trend |
| zlema_px | PUBLIC ZLEMA n=21 lag=(n-1)/2 | trend |
| zlema_slope | PUBLIC ZLEMA n=21 lag=(n-1)/2 (slope of the line) | trend |
| zlemaF_px | PUBLIC ZLEMA n=9 lag=(n-1)/2 | trend |
| zlemaF_slope | PUBLIC ZLEMA n=9 lag=(n-1)/2 (slope of the line) | trend |
| zlemaS_px | PUBLIC ZLEMA n=50 lag=(n-1)/2 | trend |
| zlemaS_slope | PUBLIC ZLEMA n=50 lag=(n-1)/2 (slope of the line) | trend |
| alma_px | PUBLIC ALMA window 9 offset 0.85 sigma 6 | trend |
| alma_slope | PUBLIC ALMA window 9 offset 0.85 sigma 6 (slope of the line) | trend |
| almaF_px | PUBLIC ALMA window 6 offset 0.85 sigma 6 | trend |
| almaF_slope | PUBLIC ALMA window 6 offset 0.85 sigma 6 (slope of the line) | trend |
| almaS_px | PUBLIC ALMA window 50 offset 0.85 sigma 6 | trend |
| almaS_slope | PUBLIC ALMA window 50 offset 0.85 sigma 6 (slope of the line) | trend |
| alma_x | ALMA9 vs ALMA50 | trend |
| nwe | APPROXIMATION: causal NW envelope, one-sided Gaussian kernel h=8 over 4h bars, band = 3*SMA100(|c-yhat|); z=(c-yhat)/band*3; ev = re-entry through band | trend |
| nweF | APPROXIMATION: causal NW envelope, one-sided Gaussian kernel h=4 over 4h bars, band = 3*SMA100(|c-yhat|); z=(c-yhat)/band*3; ev = re-entry through band | trend |
| nweS | APPROXIMATION: causal NW envelope, one-sided Gaussian kernel h=16 over 4h bars, band = 3*SMA100(|c-yhat|); z=(c-yhat)/band*3; ev = re-entry through band | trend |
| lrc | PUBLIC OLS regression channel 100, +-2 residual sd (exact window OLS) | trend |
| lrc_slope | OLS slope per bar in ATR | trend |
| lrcF | PUBLIC OLS regression channel 50, +-2 residual sd (exact window OLS) | trend |
| lrcF_slope | OLS slope per bar in ATR | trend |
| lrcS | PUBLIC OLS regression channel 200, +-2 residual sd (exact window OLS) | trend |
| lrcS_slope | OLS slope per bar in ATR | trend |
| seb | PUBLIC Standard Error Bands(21): SMA3 of linreg +-2 SE; z = distance in band half-widths | trend |
| sebF | PUBLIC Standard Error Bands(13): SMA3 of linreg +-2 SE; z = distance in band half-widths | trend |
| sebS | PUBLIC Standard Error Bands(55): SMA3 of linreg +-2 SE; z = distance in band half-widths | trend |
| turt20 | PUBLIC Turtle system (entry 20-bar breakout on close, exit 10-bar opposite extreme; flat state=0) | trend |
| don20_pos | PUBLIC Donchian(20) position -1..1 | trend |
| turt55 | PUBLIC Turtle system (entry 55-bar breakout on close, exit 20-bar opposite extreme; flat state=0) | trend |
| don55_pos | PUBLIC Donchian(55) position -1..1 | trend |
| turt10 | PUBLIC Turtle system (entry 10-bar breakout on close, exit 5-bar opposite extreme; flat state=0) | trend |
| don10_pos | PUBLIC Donchian(10) position -1..1 | trend |
| ichi_cloud | PUBLIC Ichimoku (9,26,52) price vs cloud (cloud at t = span computed 26 bars earlier) | trend |
| ichi_tk | tenkan-kijun cross | trend |
| ichi_kj | price vs kijun | trend |
| ichi_chikou | chikou clear: close vs close 26 bars ago | trend |
| ichi_futcloud | future cloud colour: senkou A vs B computed now (displaced +26, known at t) | trend |
| ichi_thick | cloud thickness in ATR | trend |
| ichi_score | Ichimoku score -5..5 (cloud, TK, price>kijun, chikou, future cloud); ewith = |score|>=4 with the trade | trend |
| ichiF_cloud | PUBLIC Ichimoku (6,13,26) price vs cloud (cloud at t = span computed 13 bars earlier) | trend |
| ichiF_tk | tenkan-kijun cross | trend |
| ichiF_kj | price vs kijun | trend |
| ichiF_chikou | chikou clear: close vs close 13 bars ago | trend |
| ichiF_futcloud | future cloud colour: senkou A vs B computed now (displaced +13, known at t) | trend |
| ichiF_thick | cloud thickness in ATR | trend |
| ichiF_score | Ichimoku score -5..5 (cloud, TK, price>kijun, chikou, future cloud); ewith = |score|>=4 with the trade | trend |
| ichiS_cloud | PUBLIC Ichimoku (12,30,60) price vs cloud (cloud at t = span computed 30 bars earlier) | trend |
| ichiS_tk | tenkan-kijun cross | trend |
| ichiS_kj | price vs kijun | trend |
| ichiS_chikou | chikou clear: close vs close 30 bars ago | trend |
| ichiS_futcloud | future cloud colour: senkou A vs B computed now (displaced +30, known at t) | trend |
| ichiS_thick | cloud thickness in ATR | trend |
| ichiS_score | Ichimoku score -5..5 (cloud, TK, price>kijun, chikou, future cloud); ewith = |score|>=4 with the trade | trend |

## B2-C smart-money / price action: 2030 condition columns, 103 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|
| struct | APPROXIMATION of ICT/LuxAlgo structure: fractal pivots k=3 confirmed k bars late; BOS = close beyond the last unbroken pivot in trend direction; state = trend after last break; ev = BOS | smc |
| choch | CHoCH: close beyond last unbroken pivot AGAINST the prior trend (k=3); ev = CHoCH, x = trend after | smc |
| ob_in | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| ob_near | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| ob_cnt | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; count of active support minus resistance zones | smc |
| ob_dsup | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; ATR distance to nearest support below (unsigned feature) | smc |
| ob_dres | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; ATR distance to nearest resistance above (unsigned feature) | smc |
| brk_in | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| brk_near | APPROXIMATION order block (k=3): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; flipped zone within 1 ATR on the trade side | smc |
| structF | APPROXIMATION of ICT/LuxAlgo structure: fractal pivots k=2 confirmed k bars late; BOS = close beyond the last unbroken pivot in trend direction; state = trend after last break; ev = BOS | smc |
| chochF | CHoCH: close beyond last unbroken pivot AGAINST the prior trend (k=2); ev = CHoCH, x = trend after | smc |
| obF_in | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| obF_near | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| obF_cnt | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; count of active support minus resistance zones | smc |
| obF_dsup | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; ATR distance to nearest support below (unsigned feature) | smc |
| obF_dres | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; ATR distance to nearest resistance above (unsigned feature) | smc |
| brkF_in | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| brkF_near | APPROXIMATION order block (k=2): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; flipped zone within 1 ATR on the trade side | smc |
| structS | APPROXIMATION of ICT/LuxAlgo structure: fractal pivots k=5 confirmed k bars late; BOS = close beyond the last unbroken pivot in trend direction; state = trend after last break; ev = BOS | smc |
| chochS | CHoCH: close beyond last unbroken pivot AGAINST the prior trend (k=5); ev = CHoCH, x = trend after | smc |
| obS_in | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| obS_near | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| obS_cnt | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; count of active support minus resistance zones | smc |
| obS_dsup | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; ATR distance to nearest support below (unsigned feature) | smc |
| obS_dres | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; ATR distance to nearest resistance above (unsigned feature) | smc |
| brkS_in | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| brkS_near | APPROXIMATION order block (k=5): last opposite-colour candle before the structure-break leg; active until a close through it, then becomes a breaker; flipped zone within 1 ATR on the trade side | smc |
| fvg_in | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| fvg_near | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| fvg_cnt | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; count of active support minus resistance zones | smc |
| fvg_dsup | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; ATR distance to nearest support below (unsigned feature) | smc |
| fvg_dres | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; ATR distance to nearest resistance above (unsigned feature) | smc |
| ifvg_in | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| ifvg_near | PUBLIC 3-candle fair value gap >= 0.15 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; flipped zone within 1 ATR on the trade side | smc |
| fvgF_in | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| fvgF_near | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| fvgF_cnt | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; count of active support minus resistance zones | smc |
| fvgF_dsup | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; ATR distance to nearest support below (unsigned feature) | smc |
| fvgF_dres | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; ATR distance to nearest resistance above (unsigned feature) | smc |
| ifvgF_in | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| ifvgF_near | PUBLIC 3-candle fair value gap >= 0.05 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; flipped zone within 1 ATR on the trade side | smc |
| fvgS_in | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| fvgS_near | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| fvgS_cnt | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; count of active support minus resistance zones | smc |
| fvgS_dsup | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; ATR distance to nearest support below (unsigned feature) | smc |
| fvgS_dres | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; ATR distance to nearest resistance above (unsigned feature) | smc |
| ifvgS_in | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| ifvgS_near | PUBLIC 3-candle fair value gap >= 0.50 ATR (gap known at the close of candle 3); inverted FVG = gap closed through; flipped zone within 1 ATR on the trade side | smc |
| sd_in | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| sd_near | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| sd_cnt | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; count of active support minus resistance zones | smc |
| sd_dsup | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; ATR distance to nearest support below (unsigned feature) | smc |
| sd_dres | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; ATR distance to nearest resistance above (unsigned feature) | smc |
| sdflip_in | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| sdflip_near | APPROXIMATION supply/demand: fractal(k=3) bar zone [low, body-top] with departure >= 1.5 ATR within k bars; flipped zone within 1 ATR on the trade side | smc |
| sdF_in | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| sdF_near | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| sdF_cnt | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; count of active support minus resistance zones | smc |
| sdF_dsup | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; ATR distance to nearest support below (unsigned feature) | smc |
| sdF_dres | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; ATR distance to nearest resistance above (unsigned feature) | smc |
| sdflipF_in | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| sdflipF_near | APPROXIMATION supply/demand: fractal(k=2) bar zone [low, body-top] with departure >= 1.0 ATR within k bars; flipped zone within 1 ATR on the trade side | smc |
| sdS_in | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; in = price inside an active support (+1) / resistance (-1) zone of this family; ev = first retest (zone untouched since birth) | smc |
| sdS_near | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; near = nearest support within 1 ATR below (+1) / resistance within 1 ATR above (-1); both cancels | smc |
| sdS_cnt | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; count of active support minus resistance zones | smc |
| sdS_dsup | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; ATR distance to nearest support below (unsigned feature) | smc |
| sdS_dres | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; ATR distance to nearest resistance above (unsigned feature) | smc |
| sdflipS_in | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; INVERTED/flipped zones (zone closed through becomes opposite-side zone): price inside | smc |
| sdflipS_near | APPROXIMATION supply/demand: fractal(k=5) bar zone [low, body-top] with departure >= 2.0 ATR within k bars; flipped zone within 1 ATR on the trade side | smc |
| sfp | PUBLIC swing-failure pattern: bar trades through an unswept fractal(k=3) pivot and CLOSES back inside (+1 long = low swept) | smc |
| eqsweep | liquidity sweep of EQUAL highs/lows (two pivots within 0.10 ATR) with close back inside | smc |
| eqpool_up | ATR distance to nearest unswept equal-highs pool above | smc |
| eqpool_dn | ATR distance to nearest unswept equal-lows pool below | smc |
| sfpF | PUBLIC swing-failure pattern: bar trades through an unswept fractal(k=2) pivot and CLOSES back inside (+1 long = low swept) | smc |
| eqsweepF | liquidity sweep of EQUAL highs/lows (two pivots within 0.15 ATR) with close back inside | smc |
| eqpool_upF | ATR distance to nearest unswept equal-highs pool above | smc |
| eqpool_dnF | ATR distance to nearest unswept equal-lows pool below | smc |
| sfpS | PUBLIC swing-failure pattern: bar trades through an unswept fractal(k=5) pivot and CLOSES back inside (+1 long = low swept) | smc |
| eqsweepS | liquidity sweep of EQUAL highs/lows (two pivots within 0.10 ATR) with close back inside | smc |
| eqpool_upS | ATR distance to nearest unswept equal-highs pool above | smc |
| eqpool_dnS | ATR distance to nearest unswept equal-lows pool below | smc |
| pd | PUBLIC premium/discount: position in dealing range [last pivot low, last pivot high] (k=5); x=0.5-pos (+ = discount, good for longs) | smc |
| ote | PUBLIC OTE: retracement 62-79% of the last impulse leg between pivots (k=5); +1 long (leg up, pulled back), -1 short | smc |
| ote_wide | retracement 50-79% | smc |
| pdF | PUBLIC premium/discount: position in dealing range [last pivot low, last pivot high] (k=2); x=0.5-pos (+ = discount, good for longs) | smc |
| oteF | PUBLIC OTE: retracement 62-79% of the last impulse leg between pivots (k=2); +1 long (leg up, pulled back), -1 short | smc |
| ote_wideF | retracement 50-79% | smc |
| pdS | PUBLIC premium/discount: position in dealing range [last pivot low, last pivot high] (k=10); x=0.5-pos (+ = discount, good for longs) | smc |
| oteS | PUBLIC OTE: retracement 62-79% of the last impulse leg between pivots (k=10); +1 long (leg up, pulled back), -1 short | smc |
| ote_wideS | retracement 50-79% | smc |
| kz_asia | PUBLIC (ICT) ICT Asia kill zone 20:00-24:00 ET (bar open time) | smc |
| kz_london | PUBLIC (ICT) London open kill zone 02:00-05:00 ET (bar open time) | smc |
| kz_nyam | PUBLIC (ICT) NY open kill zone 07:00-10:00 ET (bar open time) | smc |
| kz_nyam2 | PUBLIC (ICT) NY AM 08:30-11:00 ET (bar open time) | smc |
| kz_lclose | PUBLIC (ICT) London close kill zone 10:00-12:00 ET (bar open time) | smc |
| kz_sb_am | PUBLIC (ICT) Silver Bullet 10:00-11:00 ET (bar open time) | smc |
| kz_sb_pm | PUBLIC (ICT) Silver Bullet 14:00-15:00 ET (bar open time) | smc |
| po3_asia | APPROXIMATION power-of-three: Asia range 20:00-24:00 ET; manipulation = sweep of Asia high/low after 02:00 with close back inside; +1 long/-1 short | smc |
| po3_asia_conf | po3_asia and price already beyond the Asia range midpoint (distribution started) | smc |
| po3_london | NY-session manipulation of the London range (02:00-08:00 ET) after 08:30: sweep and close back inside | smc |
| mopen | PUBLIC price vs ICT midnight open (00:00 ET) | smc |
| o830 | price vs 08:30 ET open | smc |
| o930 | price vs 09:30 ET open | smc |

## B2-D volume: 598 condition columns, 34 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|
| rvol | PUBLIC relative volume = bar volume / mean of the same clock bucket over the previous 20 sessions | volume |
| rvol_dir | relative volume signed by the bar colour | volume |
| delta | EXACT bar delta = aggressor buy volume - sell volume (cf2_sec tape) | volume |
| delta_ratio | EXACT delta / volume | volume |
| cvd | EXACT rolling CVD over 10 bars | volume |
| cvdF | EXACT rolling CVD over 5 bars | volume |
| cvdS | EXACT rolling CVD over 30 bars | volume |
| cvd_ema | EXACT cumulative delta minus its EMA20 (delta divergence vs price at the last two swings is the nodiv/divwith condition) | volume |
| vsa_absorb | APPROXIMATION effort vs result: volume > 1.5x avg with spread < 0.6 ATR; absorption of an up bar = -1, of a down bar = +1 | volume |
| vsa_nodemand | APPROXIMATION VSA: no-demand = up bar, narrow spread, volume below both previous bars (-1); no-supply mirror (+1) | volume |
| vsa_climax | APPROXIMATION VSA climax: ultra volume (>2.5x), wide spread, close off the extreme against the bar direction; selling climax +1, buying climax -1 | volume |
| vsa_upthrust | APPROXIMATION VSA upthrust (-1): new 10-bar high, close in lower 30%, volume > 1.5x; spring/test (+1) mirror | volume |
| vsa_stopvol | APPROXIMATION stopping volume: high volume bar closing in the opposite part of its range (+1 down bar closing high) | volume |
| wy_spring_ut | APPROXIMATION Wyckoff (causal) spring (+1): low pierces the 40-bar box low, close back inside; upthrust (-1) mirror | volume |
| wy_sos_sow | APPROXIMATION Wyckoff (causal) sign of strength (+1): close above the box on >1.5x volume and wide spread; sign of weakness (-1) mirror | volume |
| wy_phase | APPROXIMATION Wyckoff phase tag = direction of the last spring/SOS (+) or upthrust/SOW (-) within the last 20 bars | volume |
| vp_psess | APPROXIMATION/PUBLIC volume profile: 1-pt bins of typical price (H+L+C)/3 weighted by 1m volume; POC = max bin; VA = 70% of volume expanding from POC toward the larger neighbour; HVN/LVN = peaks >= 1.3x / valleys <= 0.6x of the mean of a 5-bin smoothed profile; window psess | volume |
| vp_dsess | APPROXIMATION/PUBLIC volume profile: 1-pt bins of typical price (H+L+C)/3 weighted by 1m volume; POC = max bin; VA = 70% of volume expanding from POC toward the larger neighbour; HVN/LVN = peaks >= 1.3x / valleys <= 0.6x of the mean of a 5-bin smoothed profile; window dsess | volume |
| vp_fr240 | APPROXIMATION/PUBLIC volume profile: 1-pt bins of typical price (H+L+C)/3 weighted by 1m volume; POC = max bin; VA = 70% of volume expanding from POC toward the larger neighbour; HVN/LVN = peaks >= 1.3x / valleys <= 0.6x of the mean of a 5-bin smoothed profile; window fr240 | volume |
| vp_fr1440 | APPROXIMATION/PUBLIC volume profile: 1-pt bins of typical price (H+L+C)/3 weighted by 1m volume; POC = max bin; VA = 70% of volume expanding from POC toward the larger neighbour; HVN/LVN = peaks >= 1.3x / valleys <= 0.6x of the mean of a 5-bin smoothed profile; window fr1440 | volume |
| vp_frsw | APPROXIMATION/PUBLIC volume profile: 1-pt bins of typical price (H+L+C)/3 weighted by 1m volume; POC = max bin; VA = 70% of volume expanding from POC toward the larger neighbour; HVN/LVN = peaks >= 1.3x / valleys <= 0.6x of the mean of a 5-bin smoothed profile; window frsw | volume |
| avwap_asia_open | PUBLIC anchored VWAP from asia_open (typical price x volume, 1m) | volume |
| avwap_london_open | PUBLIC anchored VWAP from london_open (typical price x volume, 1m) | volume |
| avwap_ny_open | PUBLIC anchored VWAP from ny_open (typical price x volume, 1m) | volume |
| avwap_nypm_open | PUBLIC anchored VWAP from nypm_open (typical price x volume, 1m) | volume |
| avwap_midnight | PUBLIC anchored VWAP from midnight (typical price x volume, 1m) | volume |
| avwap_week_open | PUBLIC anchored VWAP from week_open (typical price x volume, 1m) | volume |
| avwap_month_open | PUBLIC anchored VWAP from month_open (typical price x volume, 1m) | volume |
| avwap_swing_hi_15m | PUBLIC anchored VWAP from swing_hi_15m (typical price x volume, 1m) | volume |
| avwap_swing_lo_15m | PUBLIC anchored VWAP from swing_lo_15m (typical price x volume, 1m) | volume |
| avwap_swing_hi_60m | PUBLIC anchored VWAP from swing_hi_60m (typical price x volume, 1m) | volume |
| avwap_swing_lo_60m | PUBLIC anchored VWAP from swing_lo_60m (typical price x volume, 1m) | volume |
| avwap_pd_high | PUBLIC anchored VWAP from pd_high (typical price x volume, 1m) | volume |
| avwap_pd_low | PUBLIC anchored VWAP from pd_low (typical price x volume, 1m) | volume |

## B2-C2 IRL/ERL sweeps (Addendum 5 Step B): 334 condition columns, 0 indicator series (x6 timeframes)

| series | formula status | family |
|---|---|---|

## IRL / ERL (Addendum 5) - PRE-REGISTERED DEFINITIONS IRL_ERL_V0 (frozen before any Step A aggregate was computed; not tuned afterwards)
Code: code/th_confl_cf4/c4_irl_lib.py (ranges, scan, post-sweep metrics), c4_irl_events.py (events), c4_irl_score.py (tables). Events: /mnt/l2/l2vast/_confl/irl/ev_<variant>.parquet (ctrl=True rows are the random-level control).
Bars: NQ 1m (/mnt/l2/l2vast/_th_sz/bars1m_NQ.npz), sweep bars 1/3/5/15 min built from them, epoch-aligned, a bar is visible only after its end. ET sessions: asia 18:00-02:00, london 02:00-09:30, ny 09:30-16:00 (16:00-18:00 'gap'). ATR unit everywhere = 5-min ATR(14, Wilder) at the confirming close.
RANGES (13 definitions, each scored separately; values known only from completed bars): a_pd prior RTH day (09:30-16:00 ET) high/low, valid until the next RTH close; b_ps prior session high/low (the session that ended last: NY->Asia->London->NY); b_cs60 current session running high/low (bars before the poke bar), active once the session is 60 min old; c_on overnight range 18:00-09:30 valid 09:30-16:00; d_wk prior week (Sun 18:00-Fri 17:00 ET) high/low; e<TF>_<s> dealing range on 15/60/240-min bars = last confirmed major swing high and low (fractal strength s=10 or 20 bars each side, confirmed s bars late; invalid if high<=low); f_or30/f_or60 opening range of each session (first 30/60 min of Asia, London, NY) valid from its end to session end. NOT implemented (stated): 'equal highs/lows AT the range extreme' as an extra external level (the extreme itself only).
LEVELS: EXTERNAL = the range's own high/low. INTERNAL = (minor) confirmed fractal pivots of strength p (2/3/5) on the sweep bars, (eq) equal highs/lows = a pivot within 0.1 ATR of an earlier unswept same-side pivot within 24 h (level = the more extreme of the two), (fvg) far edge of an unfilled 3-candle FVG >= 0.1 ATR (bull FVG bottom, bear FVG top); an internal level must lie strictly inside (RL,RH) of the range at the confirming close. A level can carry several tags (external to one range, internal to a larger one): tag_<range> = 1 external, 2 internal, 0 neither. Levels live 24 h (ranges: until the range value changes), and a level is consumed by its FIRST touch.
SWEEP: first bar whose high (low) reaches the level; if it trades beyond by >= thr (1 tick 0.25 / 2 pts / 0.1 ATR of the sweep bar) and within W bars (1/2/3/5, counting the poke bar) a bar CLOSES back on the original side, the sweep is stamped at that close (entry = that close, fade direction d = -1 for a high swept, +1 for a low). A touch smaller than thr, or no close back within W bars, is not a sweep. Recorded per sweep: poke depth (extreme - level), bars from poke to close back, volume over the poke bars, delta (APPROXIMATION: close-location-value delta per bar x volume; exact tape delta joins later), ET time, session.
HEADLINE = sweep bars 5 min, thr 2 pts, W 3, minor pivot p 3. One-at-a-time sensitivities: tf 1/3/15, thr tick / 0.1 ATR, W 1/2/5, p 2/5.
MEASURES after the confirming close, horizons 15/30/60/120 min (1m bars): fav = max favourable excursion for the fade; net = fade return at the horizon close; mae = max adverse excursion for a fade entered at the close back inside; cont = 1 if any 1m close re-closes beyond the swept level (continuation); stop = 1 if adverse reaches the poke extreme +2 pts. All in points, divided by ATR in the tables.
CONTROLS: (1) ext vs int matched on poke depth (terciles), time of day (ET hour) and volatility (ATR terciles), cell-weighted difference with week-block bootstrap CI; (2) random levels: each real level is replaced by a level at the SAME distance from the price at its birth on a random side (2 seeds), pushed through the identical sweep scan and tags.
WORKED NQ EXAMPLES (headline). EXTERNAL: 2026-10-01 20:30 ET (Globex day 10-02, Asia) 5-min close back below the prior-day high: level 27151.25 (a_pd high; also external to b_ps and e15; internal to d_wk), poke high 27187.75 (36.5 pts beyond, 3 bars, 2 closes beyond), confirmed close 27112.25, fade short d=-1. INTERNAL: 2026-09-30 19:20 ET (Asia) a confirmed minor swing low at 27032.00 (inside prior-day and prior-session ranges, tags internal) poked to 27022.00 (10 pts) and closed back above; confirmed close 27039.75, fade long d=+1.
