# CROSS_INSTRUMENT_VERDICTS: other instruments turning against a winning trade, per book (W-SUNDAY-LS, exact engine, live mix)

Method SIMPLE-RULE-IN-LIVE-MIX (code/th_ls/ls_mgr.py, xi rules = the XI1 idea of W-DYNC on a book that enters with its own stop and no target, with a give-back floor g67a50 underneath; thresholds fixed before scoring): every 15 s, while the trade is in profit (best >= 0.3 x the old target distance), the 5-minute move of ES, RTY, YM (each in sigma of its own 60-s moves over the previous 2 h, scaled to 5 min) is against the trade by >= k for all valid leaders (>= 2 valid). xi10all / xi15all = leave at market at k = 1.0 / 1.5; xi10tight = move the stop to keep 80% of the peak instead (k = 1.0); xi10ext = like xi10all but also needs one of ZN ZB 6J 6E NKD CL GC beyond 1.0 sigma against (risk-off polarity: ZN ZB 6J GC up, NKD 6E CL down). Combined sets x7 (g67a70 + xi10tight) and cbA (g67a70 + trail 1.0 + xi10tight + level-13 take) contain xi10tight. Feeds: quote mids ES RTY NQ, bar closes YM NKD 6J ZB 6E (stale up to 150 s), 1-s ZN CL GC, lag 1 s.
Scoring = whole live mix with the one book changed vs the live mix as run on the SAME months (the xi family starts 2023-09 because the age feed has no ES / RTY mids before 2023-08; months that failed in the engine are dropped from both rows); dollars after 4.84 x lots; weekly drawdown. Gaps: + = better (income higher, drawdown shallower).
VERDICT RULE (stated before reading): HELPS = max DD and worst week not worse than the live bracket AND income >= 0.97 x live AND weekly DD not worse in >= 2 of the 3 full years (2023-25); HURTS = max DD or worst week deeper by more than 5% of the live value, or income < 0.90 x live; NEUTRAL = everything else. The book verdict is the best PURE xi code (xi10all, xi15all, xi10ext, xi10tight; each sits on the g67a50 give-back floor, whose own gap is printed so the xi effect can be read as the difference) by (verdict, then max DD gap); x7 and cbA also carry a g67a70 floor / trail / level take, so their verdicts mix those effects and are shown only in the last column and the full list.

| book | best xi code | verdict | months | income gap | max DD gap | worst-week gap | L6M inc / DD | L3M inc / DD | DD better in n of 3 years | all xi codes (verdicts) |
|---|---|---|---|---|---|---|---|---|---|---|
| AS-NR7 | xi15all | **HURTS** | 36 | -311k (-34.3%) | -17k | +2k | -120k / -1k | -72k / -6k | 1 | base g67a50 alone: inc -270k DD -0k; cbA HURTS, x7 HURTS, xi10all HURTS, xi10ext HURTS, xi10tight HURTS, xi15all HURTS |
| AS-RSI | xi10all | **HURTS** | 37 | -38k (-4.1%) | -4k | +0k | -21k / -4k | -3k / +7k | 2 | base g67a50 alone: inc -22k DD -4k; cbA HURTS, x7 HURTS, xi10all HURTS, xi10ext HURTS, xi10tight HURTS, xi15all HURTS |
| AS-VWAPBRK | xi10all | **NEUTRAL** | 37 | +86k (+9.4%) | +7k | -2k | -21k / +4k | -26k / -1k | 3 | base g67a50 alone: inc +197k DD +7k; cbA NEUTRAL, x7 HELPS, xi10all NEUTRAL, xi10ext NEUTRAL, xi10tight NEUTRAL, xi15all HURTS |
| LO-CRUDE | xi10ext | **HURTS** | 37 | -332k (-36.1%) | -56k | -0k | -184k / -9k | -38k / -10k | 1 | base g67a50 alone: inc -304k DD -49k; cbA HURTS, x7 HURTS, xi10all HURTS, xi10ext HURTS, xi10tight HURTS, xi15all HURTS |
| LO-ZB | xi10ext | **HURTS** | 37 | -251k (-27.2%) | -8k | -1k | -49k / -6k | -8k / -6k | 0 | base g67a50 alone: inc -150k DD -16k; cbA HURTS, x7 HURTS, xi10all HURTS, xi10ext HURTS, xi10tight HURTS, xi15all HURTS |
| NP-CONF | xi10tight | **HELPS** | 37 | -32k (-2.2%) | +10k | +20k | -30k / -5k | +15k / -2k | 2 | base g67a50 alone: inc -30k DD +0k; cbA NEUTRAL, x7 HELPS, xi10all HELPS, xi10ext NEUTRAL, xi10tight HELPS, xi15all NEUTRAL |
| NP-MACD | xi15all | **HURTS** | 37 | -63k (-5.4%) | +2k | -6k | -113k / -7k | -42k / +0k | 2 | base g67a50 alone: inc -118k DD +2k; cbA NEUTRAL, x7 NEUTRAL, xi10all HURTS, xi10ext HURTS, xi10tight HURTS, xi15all HURTS |
| NP-YM | xi10all | **HURTS** | 37 | -218k (-20.8%) | -8k | -3k | -36k / -3k | -39k / -8k | 1 | base g67a50 alone: inc -181k DD -11k; cbA HURTS, x7 HURTS, xi10all HURTS, xi10ext HURTS, xi10tight HURTS, xi15all HURTS |
| NP-ZN | xi15all | **HELPS** | 37 | -21k (-2.0%) | +39k | +0k | -52k / -3k | +13k / +2k | 2 | base g67a50 alone: inc -29k DD +21k; cbA HELPS, x7 HELPS, xi10all NEUTRAL, xi10ext NEUTRAL, xi10tight NEUTRAL, xi15all HELPS |
| NY-FIB | xi15all | **HURTS** | 37 | -622k (-19.5%) | -49k | +3k | -187k / -24k | -149k / -26k | 1 | base g67a50 alone: inc -533k DD -37k; cbA HURTS, x7 HURTS, xi10all HURTS, xi10ext HURTS, xi10tight HURTS, xi15all HURTS |
| NY-NODE | xi10tight | **HURTS** | 37 | -189k (-5.9%) | -9k | -2k | -123k / -5k | +40k / +3k | 1 | base g67a50 alone: inc -254k DD -9k; cbA NEUTRAL, x7 HELPS, xi10all HURTS, xi10ext HURTS, xi10tight HURTS, xi15all HURTS |
| NY-OFI | xi15all | **NEUTRAL** | 37 | +0k (+0.0%) | +4k | +9k | -25k / +6k | -15k / -4k | 1 | base g67a50 alone: inc +10k DD +6k; cbA HURTS, x7 HELPS, xi10all NEUTRAL, xi10ext NEUTRAL, xi10tight NEUTRAL, xi15all NEUTRAL |
| NY-VALUE | xi15all | **HURTS** | 37 | -417k (-13.1%) | +0k | +10k | -157k / -5k | -115k / -18k | 2 | base g67a50 alone: inc -381k DD +4k; cbA HURTS, x7 HURTS, xi10all HURTS, xi10ext HURTS, xi10tight HURTS, xi15all HURTS |

Books with NO usable xi months: none (every book has the xi rows on 2023-09 .. 2026-10 except single failed months). Months used per book are in the table.

Counts: HELPS 2, NEUTRAL 2, HURTS 9 books (by best code).

## Every xi row

| book | code | verdict | income gap | max DD gap | worst-week gap | L6M inc / DD | L3M inc / DD | DD better yrs |
|---|---|---|---|---|---|---|---|---|
| AS-NR7 | cbA | HURTS | -340k | -57k | +4k | -130k / +9k | -69k / +5k | 0 |
| AS-NR7 | x7 | HURTS | -328k | -67k | +2k | -131k / +6k | -65k / +5k | 0 |
| AS-NR7 | xi10all | HURTS | -382k | -40k | +4k | -147k / +3k | -72k / -2k | 0 |
| AS-NR7 | xi10ext | HURTS | -395k | -44k | +2k | -135k / +4k | -71k / -2k | 0 |
| AS-NR7 | xi10tight | HURTS | -381k | -43k | +4k | -149k / +3k | -72k / -2k | 0 |
| AS-NR7 | xi15all | HURTS | -311k | -17k | +2k | -120k / -1k | -72k / -6k | 1 |
| AS-RSI | cbA | HURTS | -34k | -5k | -1k | -6k / -4k | -1k / +10k | 1 |
| AS-RSI | x7 | HURTS | -45k | -5k | -1k | -6k / -4k | +3k / +9k | 1 |
| AS-RSI | xi10all | HURTS | -38k | -4k | +0k | -21k / -4k | -3k / +7k | 2 |
| AS-RSI | xi10ext | HURTS | -31k | -4k | +0k | -21k / -4k | -2k / +7k | 1 |
| AS-RSI | xi10tight | HURTS | -39k | -4k | +0k | -21k / -4k | -3k / +7k | 1 |
| AS-RSI | xi15all | HURTS | -24k | -4k | -0k | -28k / -2k | -12k / +7k | 1 |
| AS-VWAPBRK | cbA | NEUTRAL | +157k | +11k | -1k | +45k / +13k | +3k / +8k | 2 |
| AS-VWAPBRK | x7 | HELPS | +107k | +19k | +1k | -22k / +1k | +1k / +9k | 2 |
| AS-VWAPBRK | xi10all | NEUTRAL | +86k | +7k | -2k | -21k / +4k | -26k / -1k | 3 |
| AS-VWAPBRK | xi10ext | NEUTRAL | +114k | +5k | -2k | -15k / +4k | -20k / -1k | 2 |
| AS-VWAPBRK | xi10tight | NEUTRAL | +97k | +7k | -2k | -21k / +3k | -26k / -2k | 3 |
| AS-VWAPBRK | xi15all | HURTS | +139k | +12k | -8k | -9k / +4k | -12k / -1k | 3 |
| LO-CRUDE | cbA | HURTS | -423k | -79k | +8k | -192k / -11k | -63k / -11k | 0 |
| LO-CRUDE | x7 | HURTS | -330k | -102k | -3k | -103k / -6k | +13k / -7k | 0 |
| LO-CRUDE | xi10all | HURTS | -335k | -64k | -3k | -173k / -9k | -28k / -10k | 1 |
| LO-CRUDE | xi10ext | HURTS | -332k | -56k | -0k | -184k / -9k | -38k / -10k | 1 |
| LO-CRUDE | xi10tight | HURTS | -337k | -66k | -3k | -174k / -9k | -28k / -10k | 1 |
| LO-CRUDE | xi15all | HURTS | -325k | -60k | +5k | -179k / -9k | -36k / -10k | 1 |
| LO-ZB | cbA | HURTS | -229k | -31k | +16k | -2k / -0k | +2k / -1k | 0 |
| LO-ZB | x7 | HURTS | -277k | -29k | +12k | -19k / +2k | +30k / +1k | 0 |
| LO-ZB | xi10all | HURTS | -270k | -9k | -1k | -50k / -6k | -6k / -7k | 0 |
| LO-ZB | xi10ext | HURTS | -251k | -8k | -1k | -49k / -6k | -8k / -6k | 0 |
| LO-ZB | xi10tight | HURTS | -287k | -17k | -1k | -50k / -6k | -6k / -7k | 0 |
| LO-ZB | xi15all | HURTS | -196k | -21k | -1k | -61k / -4k | -15k / -5k | 0 |
| NP-CONF | cbA | NEUTRAL | -59k | +18k | +19k | -37k / -3k | +11k / -3k | 2 |
| NP-CONF | x7 | HELPS | -35k | +17k | +19k | -39k / -3k | +9k / -3k | 2 |
| NP-CONF | xi10all | HELPS | -32k | +10k | +20k | -30k / -5k | +15k / -2k | 2 |
| NP-CONF | xi10ext | NEUTRAL | -57k | +8k | +20k | -36k / -4k | +15k / -2k | 1 |
| NP-CONF | xi10tight | HELPS | -32k | +10k | +20k | -30k / -5k | +15k / -2k | 2 |
| NP-CONF | xi15all | NEUTRAL | -76k | +2k | +19k | -38k / -4k | +10k / -2k | 1 |
| NP-MACD | cbA | NEUTRAL | -31k | -7k | +1k | -52k / -8k | -9k / +3k | 1 |
| NP-MACD | x7 | NEUTRAL | +9k | -1k | +0k | -42k / -5k | +7k / +3k | 1 |
| NP-MACD | xi10all | HURTS | -63k | -0k | -6k | -113k / -7k | -40k / +0k | 1 |
| NP-MACD | xi10ext | HURTS | -61k | +2k | -6k | -115k / -7k | -43k / +0k | 2 |
| NP-MACD | xi10tight | HURTS | -63k | -0k | -6k | -112k / -7k | -40k / +0k | 1 |
| NP-MACD | xi15all | HURTS | -63k | +2k | -6k | -113k / -7k | -42k / +0k | 2 |
| NP-YM | cbA | HURTS | -164k | +11k | -5k | -26k / -1k | -25k / -6k | 1 |
| NP-YM | x7 | HURTS | -95k | +28k | -3k | -5k / -2k | -22k / -6k | 2 |
| NP-YM | xi10all | HURTS | -218k | -8k | -3k | -36k / -3k | -39k / -8k | 1 |
| NP-YM | xi10ext | HURTS | -231k | -10k | -3k | -33k / -0k | -36k / -5k | 1 |
| NP-YM | xi10tight | HURTS | -212k | -8k | -3k | -36k / -3k | -39k / -8k | 1 |
| NP-YM | xi15all | HURTS | -213k | -9k | -3k | -31k / -0k | -36k / -5k | 0 |
| NP-ZN | cbA | HELPS | +29k | +30k | +0k | -62k / -5k | -16k / -0k | 3 |
| NP-ZN | x7 | HELPS | +39k | +30k | +0k | -73k / -8k | -13k / -0k | 3 |
| NP-ZN | xi10all | NEUTRAL | -71k | +29k | -1k | -95k / -3k | -22k / -0k | 3 |
| NP-ZN | xi10ext | NEUTRAL | -22k | +30k | -1k | -89k / -3k | -23k / +2k | 3 |
| NP-ZN | xi10tight | NEUTRAL | -70k | +29k | -1k | -95k / -3k | -22k / -0k | 3 |
| NP-ZN | xi15all | HELPS | -21k | +39k | +0k | -52k / -3k | +13k / +2k | 2 |
| NY-FIB | cbA | HURTS | -645k | -96k | +4k | +26k / -48k | -62k / -5k | 1 |
| NY-FIB | x7 | HURTS | -802k | -75k | +4k | -71k / -44k | -38k / -3k | 1 |
| NY-FIB | xi10all | HURTS | -629k | -73k | +4k | -129k / -24k | -110k / -29k | 1 |
| NY-FIB | xi10ext | HURTS | -649k | -91k | +4k | -167k / -24k | -150k / -29k | 1 |
| NY-FIB | xi10tight | HURTS | -617k | -73k | +4k | -132k / -24k | -112k / -29k | 1 |
| NY-FIB | xi15all | HURTS | -622k | -49k | +3k | -187k / -24k | -149k / -26k | 1 |
| NY-NODE | cbA | NEUTRAL | +60k | +23k | -3k | -23k / -8k | +39k / +4k | 3 |
| NY-NODE | x7 | HELPS | +157k | +23k | +9k | -20k / -11k | +45k / +2k | 3 |
| NY-NODE | xi10all | HURTS | -183k | -9k | -2k | -122k / -5k | +42k / +3k | 1 |
| NY-NODE | xi10ext | HURTS | -181k | -9k | -2k | -119k / -5k | +44k / +3k | 1 |
| NY-NODE | xi10tight | HURTS | -189k | -9k | -2k | -123k / -5k | +40k / +3k | 1 |
| NY-NODE | xi15all | HURTS | -184k | -10k | -2k | -109k / -5k | +44k / +3k | 1 |
| NY-OFI | cbA | HURTS | +40k | -20k | +5k | -25k / +3k | -24k / -6k | 2 |
| NY-OFI | x7 | HELPS | +6k | +0k | +10k | -52k / +0k | -20k / -1k | 2 |
| NY-OFI | xi10all | NEUTRAL | -17k | -6k | +12k | -28k / +6k | -14k / -5k | 1 |
| NY-OFI | xi10ext | NEUTRAL | -17k | -6k | +12k | -30k / +6k | -13k / -5k | 1 |
| NY-OFI | xi10tight | NEUTRAL | -11k | -3k | +12k | -28k / +6k | -14k / -5k | 1 |
| NY-OFI | xi15all | NEUTRAL | +0k | +4k | +9k | -25k / +6k | -15k / -4k | 1 |
| NY-VALUE | cbA | HURTS | -393k | -28k | -3k | -163k / -11k | -130k / -32k | 2 |
| NY-VALUE | x7 | HURTS | -253k | -33k | +12k | -125k / -4k | -87k / -3k | 2 |
| NY-VALUE | xi10all | HURTS | -410k | -6k | +10k | -168k / -5k | -118k / -18k | 2 |
| NY-VALUE | xi10ext | HURTS | -457k | -2k | +10k | -174k / -5k | -118k / -18k | 2 |
| NY-VALUE | xi10tight | HURTS | -400k | -6k | +11k | -166k / -5k | -116k / -18k | 2 |
| NY-VALUE | xi15all | HURTS | -417k | +0k | +10k | -157k / -5k | -115k / -18k | 2 |

## Other methods on the Asia MF1 (AS-NR7), labelled by method (not re-scored here, same exact engine, different design; see the files)
- LEARNED LOOP (loop C, W-DYNML, both sides, 15-s decisions): autopilot/LOOPC_BEHAVIOUR.md and LOOPC_MODEL_AS_MF1.md: the apparent edge came from a stop-fill bug and a long-only comparison; with both fixed the loop lifts the no-target safety-only run (engine $6k to $57k per lot) but is far below the book's own bracket + target ($130k per lot whole forward). Method verdict: no edge over the bracket.
- XI1 SIMPLE RULES on bare entries (W-DYNC / W-DYNH rows XIk10/15/20 all/half/own, variants B / C / D, alone-bare sets TL3_DX_AS_MF1_XIk*_A): per-set tables in autopilot/ALGO_REPORT.md (19 of 42 months done when I read it); the bare Asia MF1 manager rows there are STILL RUNNING and not PASS.
- Landscape rows of this page (xi on the book with its own stop, inside the live mix): the AS-NR7 line above.

Caveat: the "base g67a50 alone" figures are over the base set's own months (2023-04..2026-10), not the xi months, so they are only a rough yardstick for the floor under the xi rows. The month counts of the xi rows are in the table (AS-NR7: 36, one month failed in the engine).
