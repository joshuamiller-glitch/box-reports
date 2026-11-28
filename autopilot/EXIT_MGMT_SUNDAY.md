FIRST LINE: NINE BOOKS ARE MOSTLY DRIFT (Josh order 1622Z, lead list): AS-VWAPBAND (Asia MF4), LO-IMB (London MF2), NP-ATRFADE (NY PM MF1), NP-DIVFADE (NY PM MF4), NY-SOPEN (NY AM MF3), NY-BLOCK (NY AM MF6), NY-BOLL (NY AM MF7), NY-EMA (NY AM MF8), NY-AVWAP (NY AM MF9). Four are long-only: LO-IMB (London MF2), NY-BLOCK (NY AM MF6), NY-BOLL (NY AM MF7), NY-AVWAP (NY AM MF9). Three of them have a LARGE stop (NY AM MF3 120/120, MF7 120/60, MF6 90/30; London MF3 120/60 is MOSTLY DRIFT in the W-SUNDAY-WB table). Alternatives for Josh: smaller size until managed (mix row d), or removal (mix row c): both tested below.

# EXIT_MGMT_SUNDAY: protection price list, one simple rule, keys for the build (W-SUNDAY, 27 Nov 21:04Z)

## ANSWER FIRST (exact engine, live mix with live layers and live lots, 42 months; Nov 2025 off)
1. NO protection rule pays in the mix. Five simple rules were run on every edge book (11 live books plus NP-MACD and NP-CONF, own units of target): breakeven after 50% / 70% of target (be50, be70), keep 50% of the peak once the peak is 50% / 70% of target (pl50k50, pl70k50), trail 0.25 of the target behind the best once 70% is covered (nt70k25). Summed over 12 edge books: be70 gives up 4.4% of income and the max DD gets $133k DEEPER, worst week +$3k; nt70k25 6.3% / $100k deeper / +$12k; pl70k50 7.9% / $131k deeper / -$14k; be50 9.2% / $222k deeper; pl50k50 11.4% / $236k deeper / -$27k (section 1). Winning-week share is unchanged (about 61-64% in every row). Weekly standard deviation falls by $5-12k summed: the only smoothing found.
2. THE ONE SIMPLE SETTING (same rule, each book's own units): BE70 = breakeven after 70% of the target (stop to entry + 0 pt). It is the cheapest of the five (4.4% of income) and is passed by the PY filter on 7 of the 12 books; it is WEAK, and nothing in the price list beats the live row on drawdown: all session mixes with BE70 on every edge book at once: NY AM income -13.0% with max DD $214k vs $164k live; London -24.1% (DD $282k vs $213k); NY PM -3.0% (DD equal); Asia +9.4% (DD equal; READING: the live Asia LK/TK entries that BE70 replaces were costing income) (section 3). Per-book best rules are in the side column (section 4), not the pick.
3. GIVE-BACK COUNT (section 2): the breakeven rules do NOT reduce the number of trades that give back more than half of their peak (NY-FIB all 42 months: live 480, be50 751, be70 583: they turn big peaks into small wins and more trades into scratch exits), the peak-keep and trail rules hold or lower it (pl50k50 423, pl70k50 470, nt70k25 421). The 27 Nov NY-FIB type trade (peak >= 90% of target then a loss): live 18 trades in 42 months, be50 4, be70 5, pl50k50 / pl70k50 / nt70k25 0.
4. LOSS SIDE: tested exact singles exist only for NY AM and London (CU/CX/SCR/NFT/zones/bell exits, L6M screen in section 4, WEAK); Asia and NY PM loss-side families were parked 27 Nov 18:00Z (restore requested): their live loss rules (AS MF2 scratch 45/5, AS MF4 cut 24, NY PM CU 30/96/80/60) stay as the loss side until the rows run: READING.
5. Nine books are MOSTLY DRIFT (first line); mixes a/b/c/d in SUNDAY_MIX_ROWS.md: NY AM removing all nine cuts income 36% and does not cut max DD; at 1 lot (row d) NY AM income -21% with max DD $185k vs $201k.
6. RE-ENTRY GATE (order 1940Z, exact engine, section 3 rows "+gate"): after a protection exit the same book may not re-enter in the same direction until price trades back through the exit level or 15 minutes pass (W-DYNH key reentry exit_level_or_15m). It changes almost nothing: NY AM be70 income -13.0% -> -13.2%, max DD $214k -> $214k, worst week equal; nt70k25 -17.4% -> -16.8%, DD $230k -> $233k; London be70 -24.1% -> -25.1%; Asia be70 identical (0 blocked signals); NY PM be70 -3.0% -> -3.2%. Blocked signals over 42 months: NY AM be70 19, nt70k25 132; London 1 / 13; Asia 0 / 34; NY PM 1 / 0. The gate does not change the picture: the recommendation stays BE70, WEAK, without the gate.


## 1. PRICE LIST per book (exact engine, live mix with its live layers and live lots, 42 months, Nov 2025 off; reference = the live mix as run; the tested book's own live LK/TK entries are REPLACED by the rule)
Columns: "income given up" positive = cost; DD/worst-week/sd changes positive = smoother (a minus sign = DEEPER / more swing than live). PY FAIL = some prior year (2023-2025) mix income < 90% of live or that year's weekly-chain DD > 1.15x deeper. Rules: be50/be70 = breakeven after 50/70% of the target; pl50k50/pl70k50 = once the peak reaches 50/70% of target keep 50% of the best open profit (stop = entry + 0.5 x best excursion, resting stop, ratchet); nt70k25 = once 70% of target is covered trail 0.25 x target distance behind the best price.

| book | rule | income given up | max DD change | worst week change | weekly st.dev. change | win-week share (live) | L3M cost / DD | L6M cost / DD | PY |
|---|---|---|---|---|---|---|---|---|---|
| AS-NR7 (Asia MF1) | be50 | +12k (1.3%) | +0k | -6k | +0k | 63% (61%) | +10k / +6k | -36k / +8k | FAIL |
| AS-NR7 (Asia MF1) | be70 | +37k (4.1%) | -0k | -6k | -0k | 61% (61%) | +22k / +3k | +27k / +5k | ok |
| AS-NR7 (Asia MF1) | nt70k25 | +216k (23.6%) | -12k | -2k | +0k | 58% (61%) | +53k / +9k | +97k / +12k | FAIL |
| AS-NR7 (Asia MF1) | pl50k50 | +147k (16.0%) | -10k | -1k | +1k | 60% (61%) | +27k / +7k | +41k / +9k | FAIL |
| AS-NR7 (Asia MF1) | pl70k50 | +124k (13.6%) | -10k | -2k | +0k | 60% (61%) | +38k / +7k | +37k / +11k | FAIL |
| AS-RSI (Asia MF2) | be50 | +32k (3.5%) | -10k | +0k | -0k | 60% (61%) | +3k / +2k | -0k / +0k | ok |
| AS-RSI (Asia MF2) | be70 | -2k (-0.2%) | -6k | +0k | -0k | 62% (61%) | -8k / +9k | -19k / +0k | ok |
| AS-RSI (Asia MF2) | nt70k25 | -15k (-1.6%) | -10k | -0k | +0k | 62% (61%) | +3k / +10k | -19k / +1k | FAIL |
| AS-RSI (Asia MF2) | pl50k50 | +46k (5.0%) | -5k | -1k | +0k | 62% (61%) | +16k / +5k | +39k / -3k | ok |
| AS-RSI (Asia MF2) | pl70k50 | +1k (0.1%) | -5k | +0k | +0k | 63% (61%) | -2k / +10k | -10k / -0k | ok |
| AS-VWAPBRK (Asia MF3) | be50 | -34k (-3.7%) | -0k | -5k | -1k | 58% (61%) | -53k / +8k | -41k / -8k | FAIL |
| AS-VWAPBRK (Asia MF3) | be70 | -102k (-11.2%) | +16k | -2k | -1k | 60% (61%) | -34k / +7k | -13k / -6k | ok |
| AS-VWAPBRK (Asia MF3) | nt70k25 | -114k (-12.5%) | +16k | -1k | -2k | 61% (61%) | -13k / -1k | +3k / -7k | ok |
| AS-VWAPBRK (Asia MF3) | pl50k50 | -58k (-6.4%) | +14k | -10k | -1k | 60% (61%) | -12k / +6k | -7k / +9k | FAIL |
| AS-VWAPBRK (Asia MF3) | pl70k50 | -71k (-7.8%) | +8k | -0k | -1k | 61% (61%) | -21k / +7k | -1k / -10k | ok |
| LO-CRUDE (London MF1) | be50 | +266k (29.1%) | -31k | +8k | +2k | 62% (64%) | +79k / -11k | +189k / -12k | FAIL |
| LO-CRUDE (London MF1) | be70 | +172k (18.8%) | -38k | +4k | +1k | 64% (64%) | +39k / -2k | +143k / -1k | FAIL |
| LO-CRUDE (London MF1) | nt70k25 | +246k (26.9%) | -52k | +9k | +1k | 63% (64%) | +40k / -5k | +144k / -5k | FAIL |
| LO-CRUDE (London MF1) | pl50k50 | +318k (34.8%) | -45k | -2k | +2k | 64% (64%) | +63k / -12k | +199k / -12k | FAIL |
| LO-CRUDE (London MF1) | pl70k50 | +248k (27.2%) | -31k | -3k | +1k | 63% (64%) | +41k / -3k | +144k / -2k | FAIL |
| LO-ZB (London MF3) | be50 | +150k (16.4%) | -93k | -6k | -0k | 66% (64%) | -27k / +8k | -3k / -5k | FAIL |
| LO-ZB (London MF3) | be70 | +48k (5.3%) | -31k | -8k | +0k | 66% (64%) | -33k / +3k | -14k / +1k | FAIL |
| LO-ZB (London MF3) | nt70k25 | +99k (10.8%) | +5k | +5k | -1k | 65% (64%) | -14k / -2k | -36k / -2k | FAIL |
| LO-ZB (London MF3) | pl50k50 | +139k (15.2%) | -35k | -4k | -1k | 63% (64%) | +21k / +1k | +17k / +2k | FAIL |
| LO-ZB (London MF3) | pl70k50 | +179k (19.6%) | -41k | +4k | -1k | 62% (64%) | -3k / +2k | -10k / +2k | FAIL |
| NP-ZN (NY PM MF2) | be50 | +33k (2.9%) | -14k | +0k | -0k | 65% (64%) | +28k / -1k | +49k / +0k | ok |
| NP-ZN (NY PM MF2) | be70 | +45k (4.0%) | -17k | +0k | -0k | 64% (64%) | +12k / +0k | +36k / +0k | ok |
| NP-ZN (NY PM MF2) | nt70k25 | -11k (-1.0%) | +4k | +0k | -0k | 63% (64%) | -13k / +0k | +12k / -3k | FAIL |
| NP-ZN (NY PM MF2) | pl50k50 | +49k (4.4%) | +3k | +0k | -1k | 64% (64%) | +7k / +1k | +92k / -28k | ok |
| NP-ZN (NY PM MF2) | pl70k50 | -6k (-0.5%) | +0k | +0k | +0k | 64% (64%) | -8k / +0k | +33k / -5k | ok |
| NP-YM (NY PM MF3) | be50 | +136k (12.1%) | -9k | -1k | -0k | 62% (64%) | +29k / +0k | +10k / +4k | FAIL |
| NP-YM (NY PM MF3) | be70 | -13k (-1.2%) | +16k | -1k | +0k | 64% (64%) | +4k / +0k | -13k / +2k | FAIL |
| NP-YM (NY PM MF3) | nt70k25 | +79k (7.0%) | +17k | -2k | +0k | 64% (64%) | +12k / -1k | +11k / -1k | FAIL |
| NP-YM (NY PM MF3) | pl50k50 | +185k (16.4%) | -21k | -2k | -0k | 64% (64%) | +29k / -2k | +21k / +2k | FAIL |
| NP-YM (NY PM MF3) | pl70k50 | +72k (6.4%) | +15k | -2k | +0k | 64% (64%) | +11k / +0k | +1k / -1k | FAIL |
| NP-MACD (NY PM (OFF) MF5) | be50 | +195k (16.1%) | -2k | -6k | +1k | 60% (62%) | +33k / -3k | +82k / -8k | FAIL |
| NP-MACD (NY PM (OFF) MF5) | be70 | +102k (8.4%) | -5k | -5k | +0k | 61% (62%) | -2k / -1k | +40k / -12k | FAIL |
| NP-MACD (NY PM (OFF) MF5) | nt70k25 | +127k (10.5%) | -11k | -4k | +1k | 60% (62%) | +3k / +3k | +63k / -12k | FAIL |
| NP-MACD (NY PM (OFF) MF5) | pl50k50 | +206k (17.1%) | -8k | -9k | +1k | 60% (62%) | +39k / -1k | +105k / -7k | FAIL |
| NP-MACD (NY PM (OFF) MF5) | pl70k50 | +141k (11.7%) | -16k | -5k | +1k | 59% (62%) | +6k / +1k | +59k / -13k | FAIL |
| NY-FIB (NY AM MF1) | be50 | +294k (8.4%) | -23k | +0k | +2k | 62% (62%) | +19k / -20k | +249k / +1k | FAIL |
| NY-FIB (NY AM MF1) | be70 | +149k (4.3%) | -16k | +0k | +2k | 61% (62%) | +56k / -17k | +208k / +4k | ok |
| NY-FIB (NY AM MF1) | nt70k25 | +502k (14.4%) | -60k | +0k | +2k | 57% (62%) | +75k / -39k | +13k / -17k | FAIL |
| NY-FIB (NY AM MF1) | pl50k50 | +588k (16.8%) | -89k | +0k | +4k | 61% (62%) | +66k / -15k | +68k / +6k | FAIL |
| NY-FIB (NY AM MF1) | pl70k50 | +482k (13.8%) | -24k | +0k | +3k | 61% (62%) | +74k / -19k | +70k / +2k | FAIL |
| NY-VALUE (NY AM MF2) | be50 | +325k (9.3%) | -22k | +4k | +4k | 61% (62%) | +135k / -17k | +222k / -11k | FAIL |
| NY-VALUE (NY AM MF2) | be70 | +220k (6.3%) | -1k | -4k | +1k | 61% (62%) | +100k / -6k | +126k / -7k | ok |
| NY-VALUE (NY AM MF2) | nt70k25 | +234k (6.7%) | -10k | +2k | +1k | 62% (62%) | +65k / +1k | +68k / -5k | FAIL |
| NY-VALUE (NY AM MF2) | pl50k50 | +452k (12.9%) | -19k | -7k | +3k | 61% (62%) | +153k / -21k | +199k / -9k | FAIL |
| NY-VALUE (NY AM MF2) | pl70k50 | +258k (7.4%) | -20k | -13k | +1k | 61% (62%) | +67k / +2k | +73k / -5k | FAIL |
| NY-NODE (NY AM MF4) | be50 | +622k (17.8%) | -17k | +28k | +3k | 63% (62%) | +27k / +10k | +136k / +6k | FAIL |
| NY-NODE (NY AM MF4) | be70 | +325k (9.3%) | -44k | +23k | +2k | 62% (62%) | +17k / +5k | +22k / -5k | FAIL |
| NY-NODE (NY AM MF4) | nt70k25 | +96k (2.7%) | +10k | -4k | +1k | 62% (62%) | -54k / +3k | -2k / -10k | FAIL |
| NY-NODE (NY AM MF4) | pl50k50 | +433k (12.4%) | -25k | +2k | +3k | 62% (62%) | -32k / +0k | +113k / -3k | FAIL |
| NY-NODE (NY AM MF4) | pl70k50 | +284k (8.1%) | +7k | -2k | +2k | 61% (62%) | -52k / +2k | -11k / -10k | FAIL |
| NY-OFI (NY AM MF5) | be50 | +0k (0.0%) | -0k | +10k | +0k | 63% (62%) | +26k / -15k | -15k / +2k | FAIL |
| NY-OFI (NY AM MF5) | be70 | -20k (-0.6%) | -6k | +3k | -0k | 63% (62%) | +15k / -1k | -8k / +2k | ok |
| NY-OFI (NY AM MF5) | nt70k25 | -72k (-2.0%) | +3k | +11k | +0k | 64% (62%) | -4k / -2k | -8k / +0k | ok |
| NY-OFI (NY AM MF5) | pl50k50 | +6k (0.2%) | +4k | +8k | +0k | 64% (62%) | +2k / -3k | -14k / +5k | FAIL |
| NY-OFI (NY AM MF5) | pl70k50 | +21k (0.6%) | -14k | +9k | +0k | 63% (62%) | +4k / -2k | +17k / +3k | ok |

CROSS-BOOK (sum over books with the rule complete):
| rule | books | income given up (% of live) | sum max DD gain | sum worst-week gain | sum weekly sd gain | gain per $ given up (DD+worst wk) |
|---|---|---|---|---|---|---|
| be50 | 12 | +2032k (9.2%) | -222k | +25k | +10k | -0.10 |
| be70 | 12 | +961k (4.4%) | -133k | +3k | +6k | -0.13 |
| nt70k25 | 12 | +1388k (6.3%) | -100k | +12k | +5k | -0.06 |
| pl50k50 | 12 | +2511k (11.4%) | -236k | -27k | +12k | -0.10 |
| pl70k50 | 12 | +1733k (7.9%) | -131k | -14k | +6k | -0.08 |


## 2. HOW MANY TRADES GAVE BACK MORE THAN 50% OF THEIR PEAK (peak >= 30% of target; replayed 1-s tape; live row vs each rule; count / dollars given back, all 42 months | L6M | L3M)

| book | live | be50 | be70 | pl50k50 | pl70k50 | nt70k25 |
|---|---|---|---|---|---|---|
| AS-NR7 (Asia MF1) | 438 / $1678k ; 138 / $642k ; 66 / $268k | 502 / $1644k ; 158 / $592k ; 72 / $257k | 449 / $1679k ; 143 / $644k ; 63 / $268k | 513 / $1319k ; 184 / $503k ; 80 / $236k | 449 / $1503k ; 144 / $561k ; 64 / $235k | 358 / $1339k ; 101 / $476k ; 51 / $222k |
| AS-RSI (Asia MF2) | 154 / $569k ; 44 / $181k ; 16 / $63k | 199 / $570k ; 59 / $177k ; 23 / $68k | 166 / $572k ; 46 / $172k ; 17 / $61k | 169 / $344k ; 66 / $124k ; 22 / $50k | 152 / $449k ; 50 / $141k ; 18 / $58k | 100 / $351k ; 20 / $85k ; 9 / $42k |
| AS-VWAPBRK (Asia MF3) | 350 / $1259k ; 92 / $383k ; 32 / $130k | 891 / $2264k ; 291 / $747k ; 116 / $300k | 700 / $2269k ; 224 / $770k ; 89 / $297k | 816 / $1566k ; 292 / $538k ; 101 / $191k | 694 / $1929k ; 238 / $675k ; 87 / $242k | 439 / $1604k ; 125 / $527k ; 48 / $197k |
| LO-CRUDE (London MF1) | 242 / $2119k ; 36 / $396k ; 20 / $209k | 572 / $2333k ; 130 / $566k ; 62 / $280k | 410 / $2369k ; 86 / $548k ; 38 / $252k | 585 / $1616k ; 142 / $404k ; 63 / $205k | 455 / $2031k ; 97 / $459k ; 43 / $220k | 174 / $1465k ; 26 / $305k ; 14 / $158k |
| LO-ZB (London MF3) | 532 / $1591k ; 106 / $405k ; 51 / $195k | 976 / $1902k ; 253 / $517k ; 119 / $249k | 709 / $1767k ; 168 / $456k ; 80 / $217k | 778 / $1260k ; 228 / $359k ; 111 / $184k | 663 / $1521k ; 159 / $374k ; 79 / $194k | 459 / $1324k ; 83 / $307k ; 40 / $157k |
| NP-ZN (NY PM MF2) | 141 / $996k ; 23 / $172k ; 15 / $97k | 188 / $1103k ; 41 / $234k ; 22 / $118k | 161 / $1042k ; 36 / $224k ; 20 / $111k | 106 / $570k ; 19 / $121k ; 10 / $52k | 121 / $770k ; 23 / $154k ; 13 / $64k | 112 / $732k ; 17 / $128k ; 10 / $50k |
| NP-YM (NY PM MF3) | 273 / $1299k ; 29 / $154k ; 12 / $44k | 556 / $1304k ; 63 / $138k ; 30 / $63k | 388 / $1301k ; 41 / $136k ; 20 / $52k | 251 / $656k ; 31 / $61k ; 11 / $20k | 269 / $956k ; 26 / $93k ; 11 / $29k | 197 / $876k ; 18 / $83k ; 8 / $26k |
| NP-CONF (NY PM (OFF) MF5) | n/a ; n/a ; n/a | 384 / $1535k ; 73 / $304k ; 39 / $148k | 323 / $1543k ; 61 / $288k ; 30 / $123k | 210 / $746k ; 41 / $160k ; 21 / $79k | 260 / $1163k ; 46 / $209k ; 23 / $91k | 224 / $1093k ; 40 / $206k ; 21 / $88k |
| NP-MACD (NY PM (OFF) MF5) | 463 / $2142k ; 57 / $311k ; 32 / $160k | 1111 / $2149k ; 176 / $343k ; 87 / $182k | 752 / $2188k ; 114 / $330k ; 57 / $150k | 505 / $1105k ; 103 / $189k ; 48 / $105k | 479 / $1609k ; 79 / $240k ; 38 / $103k | 331 / $1461k ; 40 / $200k ; 20 / $83k |
| NY-FIB (NY AM MF1) | 480 / $4577k ; 94 / $1118k ; 41 / $409k | 751 / $5223k ; 192 / $1420k ; 75 / $556k | 583 / $4918k ; 128 / $1259k ; 54 / $503k | 423 / $2946k ; 95 / $677k ; 41 / $265k | 470 / $4013k ; 104 / $995k ; 42 / $406k | 421 / $3868k ; 83 / $899k ; 41 / $414k |
| NY-VALUE (NY AM MF2) | 542 / $3301k ; 103 / $667k ; 42 / $258k | 1030 / $3851k ; 238 / $865k ; 98 / $379k | 756 / $3669k ; 164 / $785k ; 66 / $325k | 501 / $1977k ; 104 / $389k ; 47 / $167k | 524 / $2726k ; 94 / $533k ; 38 / $211k | 432 / $2535k ; 75 / $469k ; 33 / $194k |
| NY-NODE (NY AM MF4) | 605 / $3946k ; 123 / $862k ; 46 / $296k | 2246 / $4909k ; 520 / $1078k ; 208 / $406k | 1371 / $4615k ; 304 / $966k ; 111 / $367k | 1034 / $2656k ; 286 / $602k ; 96 / $214k | 851 / $3433k ; 204 / $672k ; 66 / $243k | 505 / $3009k ; 92 / $546k ; 34 / $210k |
| NY-OFI (NY AM MF5) | 691 / $2524k ; 118 / $468k ; 51 / $184k | 1188 / $2646k ; 204 / $473k ; 98 / $229k | 921 / $2658k ; 163 / $490k ; 76 / $218k | 504 / $1260k ; 95 / $234k ; 41 / $104k | 605 / $1899k ; 115 / $363k ; 52 / $158k | 516 / $1787k ; 90 / $335k ; 44 / $147k |

## 3. SESSION MIXES: all edge books of the session on ONE rule at once vs the live mix as run (exact engine)

| session | rule | status | income vs live | max DD (live) | worst week (live) | weekly sd | win-week share (live) | L3M inc / DD | L6M inc / DD | by year income gap 23/24/25/26 |
|---|---|---|---|---|---|---|---|---|---|---|
| NY | be70 | ok | -453k (-13.0%) | -214k (-164k) | -75k (-110k) | +5k | 61% (62%) | -152k / -17k | -238k / -0k | +16k/-34k/-11k/-425k |
| NY | be70+gate | ok | -462k (-13.2%) | -214k (-164k) | -75k (-110k) | +6k | 61% (62%) | -152k / -17k | -261k / -0k | +16k/-34k/+3k/-448k |
| NY | nt70k25 | ok | -609k (-17.4%) | -230k (-164k) | -102k (-110k) | +4k | 61% (62%) | -54k / -19k | -5k / -3k | -61k/-227k/-29k/-292k |
| NY | nt70k25+gate | ok | -588k (-16.8%) | -233k (-164k) | -100k (-110k) | +4k | 62% (62%) | -63k / -20k | -12k / -3k | -129k/-241k/+62k/-280k |
| LO | be70 | ok | -220k (-24.1%) | -282k (-213k) | -112k (-107k) | +1k | 64% (64%) | -6k / -2k | -130k / -6k | -21k/-4k/-135k/-60k |
| LO | be70+gate | ok | -229k (-25.1%) | -282k (-213k) | -112k (-107k) | +1k | 64% (64%) | -11k / -2k | -134k / -6k | -21k/-9k/-135k/-65k |
| LO | nt70k25 | ok | -345k (-37.7%) | -267k (-213k) | -94k (-107k) | +1k | 60% (64%) | -26k / -0k | -108k / +0k | -24k/-89k/-132k/-100k |
| LO | nt70k25+gate | ok | -351k (-38.5%) | -271k (-213k) | -94k (-107k) | +0k | 60% (64%) | -20k / -0k | -105k / +0k | -24k/-96k/-135k/-96k |
| AS | be70 | ok | +86k (9.4%) | -66k (-68k) | -40k (-37k) | -1k | 60% (61%) | +16k / +14k | +6k / -5k | +15k/+21k/+44k/+7k |
| AS | be70+gate | ok | +86k (9.4%) | -66k (-68k) | -40k (-37k) | -1k | 60% (61%) | +16k / +14k | +6k / -5k | +15k/+21k/+44k/+7k |
| AS | nt70k25 | ok | -88k (-9.6%) | -59k (-68k) | -41k (-37k) | -1k | 59% (61%) | -45k / -0k | -84k / -24k | +20k/+5k/-36k/-77k |
| AS | nt70k25+gate | ok | -90k (-9.8%) | -73k (-68k) | -41k (-37k) | -1k | 60% (61%) | -36k / -0k | -73k / -21k | +20k/+2k/-27k/-85k |
| NP | be70 | ok | -34k (-3.0%) | -128k (-127k) | -45k (-44k) | +0k | 65% (64%) | -16k / +0k | -26k / +2k | -2k/+20k/-12k/-40k |
| NP | be70+gate | ok | -37k (-3.2%) | -128k (-127k) | -45k (-44k) | +0k | 65% (64%) | -16k / +0k | -26k / +2k | -5k/+20k/-12k/-40k |
| NP | nt70k25 | ok | -51k (-4.5%) | -110k (-127k) | -46k (-44k) | +0k | 64% (64%) | -2k / -1k | -17k / -0k | -13k/+27k/-43k/-23k |
| NP | nt70k25+gate | ok | -50k (-4.5%) | -110k (-127k) | -46k (-44k) | +0k | 64% (64%) | -2k / -1k | -17k / -0k | -12k/+27k/-43k/-23k |


Drift-book mixes a/b/c/d (live / long-only removed / all nine removed = new BASE / nine at 1 lot): autopilot/SUNDAY_MIX_ROWS.md (W-SUNDAY-MX).


## 4. SIDE COLUMN: best finished setting per book and side on the L6M rows (L6M-only screen, NOT a pick; tk/cu/cx/sc/nf/zones families of Asia and NY PM were parked 27 Nov 18:00Z, only NY AM and London have the loss side run)

| book | side | best L6M settings (income gap L6M / max DD gap L6M / worst-week gap L6M) |
|---|---|---|
| NY-FIB (NY AM MF1) | loss | sc50_10 (-94k / +10k / +10k); zh30 (-2k / +0k / +0k) |
| NY-FIB (NY AM MF1) | profit | pl50k50 (-68k / +6k / +6k); nt80k25 (-57k / +4k / +4k) |
| NY-VALUE (NY AM MF2) | loss | zs30 (+17k / +0k / +0k); cx80 (-17k / +0k / +0k) |
| NY-VALUE (NY AM MF2) | profit | lk90p10 (-9k / +0k / +0k); lk80p10 (-102k / +0k / +0k) |
| NY-NODE (NY AM MF4) | loss | cut15 (-66k / +6k / +6k); zh30 (+2k / -2k / -2k) |
| NY-NODE (NY AM MF4) | profit | nt70k15 (+34k / +6k / +6k); be50 (-136k / +6k / +6k) |
| NY-OFI (NY AM MF5) | loss | e30 (-6k / +8k / +8k); cx40 (-42k / +3k / +3k) |
| NY-OFI (NY AM MF5) | profit | lk50p10 (-11k / +7k / +7k); lk50p20 (-25k / +9k / +9k) |
| LO-CRUDE (London MF1) | loss | e15 (-12k / +0k / +0k); sc67_10 (-65k / +0k / +0k) |
| LO-CRUDE (London MF1) | profit | tk95 (-2k / -0k / -0k); lk90p0 (-42k / -2k / -2k) |
| LO-ZB (London MF3) | loss | sc50_10 (+35k / +1k / +1k); e15 (+16k / +0k / +0k) |
| LO-ZB (London MF3) | profit | tk80 (+106k / +7k / +7k); nt70k15 (+48k / +4k / +4k) |
| AS-NR7 (Asia MF1) | profit | pl50k50 (-41k / +9k / +9k); pl70k50 (-37k / +11k / +7k) |
| AS-RSI (Asia MF2) | profit | nt70k15 (+21k / +1k / +7k); pl70k75 (+19k / +1k / +7k) |
| AS-VWAPBRK (Asia MF3) | profit | pl50k50 (+7k / +9k / +4k); lk65p0 (+17k / -5k / -10k) |
| NP-ZN (NY PM MF2) | profit | nt70k25 (-12k / -3k / +1k); lk65p20 (-29k / +0k / +0k) |
| NP-YM (NY PM MF3) | profit | lk65p10 (+5k / +2k / +2k); be50 (-10k / +4k / +4k) |
| NP-MACD (NY PM (OFF) MF5) | profit | lk80p20 (-21k / -6k / -1k); nt80k25 (-10k / -7k / -2k) |

## 5. KEYS FOR THE BUILD (exact engine definitions: autopilot/EXIT_MGMT_KEYS.md, W-DYNA; every line below SPEC = read from the engine code, READING = my reading)

The recommended simple rule BE70 on every edge book, in the book's own units (arm level = 0.70 x target distance in points; stop goes to entry + 0 pt, rounded to the tick by the engine, resting stop order, ratchet only, whole position at 1/2/3/6 lots; the book's own live LK/TK entry is removed when BE70 is loaded: SPEC). New keys (not in the live file, a few lines to add in NT8): BE=<pct>:<offset_pts> (W-DYNH dx_multi recipe be50 [pct, off ticks]), PL=<arm_pct>:<keep> (peaklock), NT=<pct>:<k> (neartgt: k x target distance behind the best). Order of evaluation: engine bracket orders see the print first; then Trade Health policy lines / ec_hooks cuts / ev_profit LK-TK; the dx_multi stop ratchet runs after the mf_multi layer on the same print (READING: first rule to request an exit wins, a stop move never loosens). Per-bar match rows: autopilot/EXIT_MGMT_SUNDAY_MATCH.md (W-DYNA, DONE: BE70 on all 13 edge books, one SAVED and one COST trade each, plus PL70K50 and NT70K25 on NY-FIB and NY-NODE; engine fills go through the fill model, not at the level).

| book | stop / target pts | live lots (set) | BE70 string | PL70K50 string | NT70K25 string | live profit/loss keys that BE70 replaces |
|---|---|---|---|---|---|---|
| AS-NR7 (Asia MF1) | 40 / 80 | see BOOK_STEMS.md | BE=0.70:0 (arm 56.0 pt) | PL=0.70:0.50 (arm 56.0 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 56.0 pt, trail 20.0 pt behind best) | LK=[[0.8, 10.0]] |
| AS-RSI (Asia MF2) | 60 / 60 | see BOOK_STEMS.md | BE=0.70:0 (arm 42.0 pt) | PL=0.70:0.50 (arm 42.0 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 42.0 pt, trail 15.0 pt behind best) | SCR={'d': 45, 's': 5}; LK=[[0.8, 0.0]]; TK=[0.95, 30] |
| AS-VWAPBRK (Asia MF3) | 45 / 45 | see BOOK_STEMS.md | BE=0.70:0 (arm 31.5 pt) | PL=0.70:0.50 (arm 31.5 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 31.5 pt, trail 11.2 pt behind best) | TK=[0.5, 15] |
| LO-CRUDE (London MF1) | 90 / 30 | see BOOK_STEMS.md | BE=0.70:0 (arm 21.0 pt) | PL=0.70:0.50 (arm 21.0 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 21.0 pt, trail 7.5 pt behind best) | none |
| LO-ZB (London MF3) | 120 / 60 | see BOOK_STEMS.md | BE=0.70:0 (arm 42.0 pt) | PL=0.70:0.50 (arm 42.0 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 42.0 pt, trail 15.0 pt behind best) | none |
| NP-ZN (NY PM MF2) | 120 / 120 | see BOOK_STEMS.md | BE=0.70:0 (arm 84.0 pt) | PL=0.70:0.50 (arm 84.0 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 84.0 pt, trail 30.0 pt behind best) | CU={'d': 96.0} |
| NP-YM (NY PM MF3) | 80 / 40 | see BOOK_STEMS.md | BE=0.70:0 (arm 28.0 pt) | PL=0.70:0.50 (arm 28.0 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 28.0 pt, trail 10.0 pt behind best) | CU={'d': 80.0} |
| NP-CONF (NY PM (OFF) MF5) | 90 / 90 | see BOOK_STEMS.md | BE=0.70:0 (arm 63.0 pt) | PL=0.70:0.50 (arm 63.0 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 63.0 pt, trail 22.5 pt behind best) | none |
| NP-MACD (NY PM (OFF) MF5) | 90 / 30 | see BOOK_STEMS.md | BE=0.70:0 (arm 21.0 pt) | PL=0.70:0.50 (arm 21.0 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 21.0 pt, trail 7.5 pt behind best) | none |
| NY-FIB (NY AM MF1) | 120 / 120 | see BOOK_STEMS.md | BE=0.70:0 (arm 84.0 pt) | PL=0.70:0.50 (arm 84.0 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 84.0 pt, trail 30.0 pt behind best) | none |
| NY-VALUE (NY AM MF2) | 60 / 60 | see BOOK_STEMS.md | BE=0.70:0 (arm 42.0 pt) | PL=0.70:0.50 (arm 42.0 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 42.0 pt, trail 15.0 pt behind best) | none |
| NY-NODE (NY AM MF4) | 90 / 30 | see BOOK_STEMS.md | BE=0.70:0 (arm 21.0 pt) | PL=0.70:0.50 (arm 21.0 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 21.0 pt, trail 7.5 pt behind best) | none |
| NY-OFI (NY AM MF5) | 60 / 60 | see BOOK_STEMS.md | BE=0.70:0 (arm 42.0 pt) | PL=0.70:0.50 (arm 42.0 pt, stop = entry + 0.5 x best) | NT=0.70:0.25 (arm 42.0 pt, trail 15.0 pt behind best) | none |

NY-FIB 27 Nov trade (peak about 94% of the 120-pt target, then a full stop): BE70, PL50K50, PL70K50 and NT70K25 all arm at or before 94% (84 pt for 70%), so the stop would have been at entry or better instead of -120 pt: READING (fill at the resting stop; gap risk not modelled). BE50 arms at 60 pt; a lock LK90 (108 pt) also arms at a 112.8-pt peak (software market exit on touch). Exact counts of >=90% peak trades that closed at a loss under each rule: see section 2 note and SUNDAY_GIVEBACK_RULES.md.


## 6. LINKS
- Wide-bracket drift tables: autopilot/SUNDAY_WIDE_BRACKET.md (W-SUNDAY-WB, drift null by side) and autopilot/WIDE_BRACKET_EDGE.md (W-PLAN-AS): the two do not agree on every book; the nine MOSTLY DRIFT books are the lead list of 1622Z.
- Give-back counts by window: autopilot/SUNDAY_GIVEBACK_COUNT.md and SUNDAY_GIVEBACK_RULES.md.
- Mix rows a/b/c/d: autopilot/SUNDAY_MIX_ROWS.md. Landscape / stop-only rows: autopilot/SUNDAY_LANDSCAPE.md (W-SUNDAY-LS; NOT READY unless that file exists). Cross-instrument and prediction rules: autopilot/MGMT_DESIGN.md, LEAD_FINDER.md, ALGO_REPORT.md (W-DYNC / W-DYNH / W-DYNML verdicts: NOT READY per book unless stated there).
- Full single-setting list of finished sets: autopilot/SUNDAY_SETS_ALL.md (W-DYNQ).

<!-- JOINT-MIXES-BEGIN -->
## Joint session mixes (W-SUNDAY-MX; full tables autopilot/SUNDAY_JOINT_MIXES.md)
- NY AM (42 months): lowest max DD = drift removed / node (-$137,104 vs live -$200,647), income $2,450,021 vs live $3,498,291; best income = live / node ($3,615,376, DD -$180,710).
- Asia (42 months): lowest max DD = replacement book / vwaplate50 (-$57,774 vs live -$67,941), income $1,216,508 vs live $914,998; best income = replacement book / vwap ($1,301,812, DD -$59,708).
- NY PM (37 months): lowest max DD = drift removed / late50 (-$54,114 vs live -$134,363), income $846,757 vs live $1,047,175; best income = replacement book / znconf ($1,451,235, DD -$72,379).
- London (42 months): lowest max DD = drift at 1 lot / late75 (-$128,414 vs live -$224,333), income $727,063 vs live $913,621; best income = live / late50 ($988,772, DD -$198,304).
<!-- JOINT-MIXES-END -->
