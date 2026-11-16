# USER: LIVE FAULT ROOT CAUSE (11-16, measured in the Output log), saved verbatim
NinjaTrader delivers every NQ depth event AND every NQ tick once per NQ data series in D7 (13 series: bip 0,1,2,3,6..14). So in live, since the alt-bar slots and extra series were added, each depth Add/Remove was applied 13 times and each print's volume was booked 13 times in the state engine. v1.9c uses only the primary-series copy (first minute: 79,162 depth events used, 949,932 copies dropped; 11,877 ticks used, 142,524 dropped; book usable 99%).
Consequences for research:
1. Every live-vs-engine comparison of book or volume features before today is void (pulled_mult, delta_mult, tot_rel, imb5/10, ahead_rel, MedLevel, the L2 entry gate).
2. EV: date when live first had more than one NQ series (v1.x history in the DS7.cs header) and re-read the live-vs-engine gap from that date.
3. The engine was right. No change to the engine.
