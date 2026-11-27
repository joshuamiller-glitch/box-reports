# GIVEBACK_COUNT: trades that were up >= 50 / 70 / 90% of the target distance and then closed at a loss or a full stop (W-PLAN-NY, order 1625Z item 4, 27 Nov 16:36Z)

ANSWER FIRST: every live book gives profit back, and the dollars are largest in the wide 120/120 and 90/30 NY AM books. Per year at the trade lots (gross, from the peak to the close): NY-NODE (Le4fede95, 90/30) 221 trades reached 70% and closed at a loss or stop, $1.71M from peak in 42 months ($479k/yr), realised loss on them $1.23M ($344k/yr); NY-BLOCK $1.33M ($372k/yr); NY-VALUE $1.11M; NY-FIB (120/120) 73 trades, $1.05M ($295k/yr), of which 19 reached 90% ($275k, $77k/yr); NY-SOPEN 51 trades $668k ($187k/yr). Asia is small: AS-RSI 33 trades $152k, AS-NR7 32 trades $202k. NY PM (bare 1-lot table, scaled to set lots below) is large for NP-ATRFADE and NP-DIVFADE.

DEFINITION: peak = best price from the fill to the engine exit (1-s tape, trade prices); up share = peak / target distance; counted if share >= p and the trade closed with gross < 0 or exit name Stop. Given back = (peak points - final points) x lots x $20, before fees; realised = gross $ of those trades. Window: 2023-04..2026-10 (42 months, Nov 2025 off); L3M = Aug-Oct 2026; per year n / $k given back.
SOURCES: Asia and NY AM = exact engine trades of the live mixes (entries3, live set lots, PICKC sizes). NY PM = the PLAN_NP bare-bracket table (1 lot, not the engine trades); columns marked x use the set lots from BOOK_STEMS for scale. LONDON: no trade table on this box (W-PLAN-AS to supply; not computed here). THIS WEEK (23-27 Nov): NOT COVERED: the engine months end 2026-10 and this week's live fills are not in any table on this box; days covered = none, so the live NY-FIB case of 27 Nov is not in these counts.

| stem (session MFn) | bracket stop/target | lots | trades | n >=50% / 70% / 90% | $ from peak, 42 mo, >=50% / 70% / 90% | realised $ >=70% / >=90% | L3M n / $ (>=70%) | per year n/$k (>=70%): 2023 / 2024 / 2025 / 2026 | $/yr from peak >=70% |
|---|---|---|---|---|---|---|---|---|---|
| AS-NR7 (Asia MF1) | 40/80 | 3 | 1875 | 108 / 32 / 1 | 600k / 202k / 5k | -69k / -0k | 2 / 11k | 1/6 / 2/20 / 8/53 / 21/123 | 56k |
| AS-RSI (Asia MF2) | 60/60 | 3 | 609 | 66 / 33 / 9 | 303k / 152k / 40k | -29k / -1k | 3 / 9k | 1/6 / 4/19 / 7/30 / 21/97 | 43k |
| AS-VWAPBRK (Asia MF3) | 45/45 | 3 | 2479 | 76 / 10 / 2 | 379k / 65k / 19k | -33k / -8k | 0 / 0k | 1/5 / 1/5 / 3/23 / 5/33 | 18k |
| AS-VWAPBAND (Asia MF4) | 30/30 | 3 | 879 | 19 / 1 / 0 | 46k / 2k / 0k | -1k / 0k | 1 / 2k | 0/0 / 0/0 / 0/0 / 1/2 | 1k |
| NY-FIB (NY AM MF1) | 120/120 | 3 | 1611 | 160 / 73 / 19 | 2115k / 1055k / 275k | -473k / -117k | 3 / 34k | 3/47 / 16/212 / 32/440 / 22/356 | 295k |
| NY-VALUE (NY AM MF2) | 60/60 | 3 | 1951 | 271 / 149 / 40 | 1983k / 1108k / 324k | -551k / -155k | 10 / 75k | 23/160 / 25/189 / 45/368 / 56/391 | 310k |
| NY-SOPEN (NY AM MF3) | 120/120 | 3 | 965 | 106 / 51 / 13 | 1324k / 668k / 192k | -282k / -71k | 5 / 96k | 3/40 / 14/160 / 16/182 / 18/286 | 187k |
| NY-NODE (NY AM MF4) | 90/30 | 3 | 3230 | 384 / 221 / 87 | 2822k / 1715k / 748k | -1230k / -530k | 15 / 104k | 26/183 / 49/337 / 74/582 / 72/612 | 479k |
| NY-OFI (NY AM MF5) | 60/60 | 2 | 2535 | 357 / 194 / 46 | 1573k / 892k / 233k | -436k / -104k | 10 / 42k | 23/104 / 47/214 / 62/295 / 62/280 | 249k |
| NY-BLOCK (NY AM MF6) | 90/30 | 3 | 2862 | 340 / 181 / 61 | 2459k / 1332k / 514k | -947k / -367k | 13 / 115k | 34/220 / 50/333 / 48/370 / 49/408 | 372k |
| NY-BOLL (NY AM MF7) | 120/60 | 1 | 868 | 87 / 39 / 10 | 234k / 110k / 30k | -62k / -16k | 2 / 8k | 6/17 / 11/33 / 10/25 / 12/36 | 31k |
| NY-EMA (NY AM MF8) | 80/40 | 1 | 894 | 113 / 56 / 18 | 217k / 114k / 37k | -73k / -23k | 3 / 5k | 10/17 / 17/35 / 14/29 / 15/32 | 32k |
| NY-AVWAP (NY AM MF9) | 80/40 | 2 | 672 | 76 / 36 / 12 | 283k / 137k / 51k | -83k / -30k | 2 / 7k | 3/8 / 15/56 / 9/38 / 9/35 | 38k |
| NP-ATRFADE (NY PM MF1) | 30/30 | 3x | 6684 | 1007 / 498 / 140 | 2936k / 1570k / 468k | -822k / -230k | 32 / 103k | 93/96 / 150/156 / 134/140 / 121/131 | 439k |
| NP-ZN (NY PM MF2) | 120/120 | 1x | 1827 | 120 / 46 / 13 | 350k / 151k / 46k | -58k / -17k | 3 / 9k | 3/9 / 8/25 / 20/69 / 15/48 | 42k |
| NP-YM (NY PM MF3) | 80/40 | 3x | 1530 | 206 / 90 / 29 | 899k / 428k / 141k | -244k / -75k | 1 / 4k | 23/27 / 29/48 / 21/34 / 17/33 | 119k |
| NP-DIVFADE (NY PM MF4) | 60/60 | 3x | 5941 | 627 / 284 / 80 | 3145k / 1606k / 496k | -755k / -223k | 24 / 131k | 43/73 / 54/94 / 104/206 / 83/162 | 449k |
| NP-MACD (NY PM NPMACD) | 90/30 | 1x | 3590 | 434 / 217 / 67 | 596k / 310k / 97k | -201k / -59k | 15 / 22k | 41/51 / 75/94 / 59/91 / 42/75 | 87k |
| NP-CONF (NY PM NPCONF) | 90/90 | 1x | 1722 | 134 / 52 / 9 | 311k / 134k / 27k | -58k / -12k | 5 / 10k | 5/12 / 9/23 / 20/53 / 18/45 | 37k |

Per-year n/$k at >=50% and >=90% are in the csv (/mnt/l2/l2vast/_plan_ny/giveback_table.csv on server C). Per-year cells above are n / $k from peak at the trade lots (NP cells are at 1 lot: multiply by the lots column).

READING. (1) Share of all trades that reached 70% of target and closed at a loss or stop: NY-FIB 4.5%, NY-NODE 6.8%, NY-BLOCK 6.3%, NY-VALUE 7.6%, NY-SOPEN 5.3%, NY-OFI 7.7%, Asia 0.1-5.4%, NP-ATRFADE 7.5%, NP-DIVFADE 4.8% (n70 / trades). (2) At 90% then loss: NY-NODE 87 trades, NY-BLOCK 61, NY-OFI 46, NY-VALUE 40, NY-FIB 19, NY-SOPEN 13. (3) The sums are the cost of NOT protecting; protection also cuts winners: see PLAN_NY.md, near-miss exact rows (lock 0.8 on NY-FIB / NY-VALUE / NY-SOPEN made the mix drawdown deeper; trail 13.9 pt from 70% of target on NY-OFI was the only weak positive). (4) Asia and NY AM figures are the exact engine trades; NY PM is a bare 1-lot table (scaled in the total columns only), London is missing.
