# DS3_ZONES_3_SCALEOUT - scale-out vs the resting 70/30 add on V13T_LIVE (ZL-3, E2 half; prereg l2vast/ds3/prereg/ZL3_SCALEOUT_prereg.md sha e7811d4e4268872fc0bce41160a62b3f742993d30cac8f4493e25e2a325d6685)
Base V13T_LIVE (lines off, lock none, add cancelled on any exit, market exits 0.80, stops 2.45 worse). Scale-out = market sale of 30% / 50% of the position at the second after the first 1-s close with unrealised >= 0.5 / 0.7 of the target distance (V13T.inject kind scale_out, only rows with an exit price in the library, i.e. 21,806 / 18,962 rows), rest to its own exit. A = shipped split (the base). C = market entry (no split) + scale-out. D = shipped split + scale-out. maxDD cut vs the base L3M / L6M / HOLD / MID / PRE / X' %; d mean L6M and d mean PRE ($/wk, MDE).
| cell | maxDD cut vs base | d mean L6M (MDE) | d mean PRE (MDE) |
|---|---|---|---|
| B market | -20 / +19 / +19 / -104 / -19 / +5 | +0.9k (7.9k) | +2.3k (3.7k) |
| C market+SO pct 0.5 frac 0.3 | -17 / +13 / +13 / +20 / -0 / +1 | -4.0k (8.7k) | -2.0k (4.5k) |
| C market+SO pct 0.5 frac 0.5 | -7 / +17 / +17 / -2 / -4 / -2 | -6.7k (12.7k) | -6.0k (6.4k) |
| C market+SO pct 0.7 frac 0.3 | -5 / +15 / +15 / +31 / -1 / +9 | -3.6k (7.1k) | -0.8k (4.3k) |
| C market+SO pct 0.7 frac 0.5 | +10 / +15 / +15 / +21 / +9 / +12 | -6.1k (9.7k) | -2.2k (5.8k) |
| D split+SO pct 0.5 frac 0.3 | +15 / +24 / +14 / -25 / +16 / +14 | -2.2k (7.8k) | -4.8k (4.8k) |
| D split+SO pct 0.5 frac 0.5 | +29 / +38 / +18 / -47 / -2 / +15 | -5.0k (12.5k) | -6.3k (5.4k) |
| D split+SO pct 0.7 frac 0.3 | +22 / +2 / +2 / -3 / +8 / +15 | -3.8k (6.2k) | -1.7k (3.4k) |
| D split+SO pct 0.7 frac 0.5 | +32 / +17 / +17 / -3 / +9 / +16 | -5.9k (9.6k) | -4.0k (5.4k) |
Placebo (same number of rows scale out 50% at a RANDOM second inside the trade, 10 seeds):
| | | |
|---|---|---|
| placebo C market+SO (n=10) | median cut L6M +4 / PRE -19 / X' -47 | median d mean L6M -10.1k |
| placebo D split+SO (n=10) | median cut L6M +6 / PRE -33 / X' -29 | median d mean L6M -10.1k |
Equal risk (lots scaled until the worst-20 sum of ALL equals the base), pct 0.7 / frac 0.5: **C market + scale-out** lscale 1.24: total $3.500M vs base $3.482M (+0.5%), maxDD cut L3M / L6M / HOLD / MID / PRE / X' = -5 / +17 / +17 / +39 / -23 / +20 %, L6M mean -$1.8k (MDE 7.4k); **D split + scale-out** lscale 1.11: total $3.098M (-11%), cuts +25 / +27 / +26 / +3 / -16 / +13 %, L6M mean -$2.1k.
## Reading
* Scale-out lowers L6M / HOLD drawdown by 13-38% in every cell and costs 2-7k per week of mean (inside MDE except the D 0.5/0.5 PRE mean, -6.3k vs MDE 5.4k): it is a SIZE reduction on winners. The random-timing placebo costs about $10k/wk and is clearly worse in PRE and X' (median PRE -19% / -33%, X' -47% / -29%), so the trigger on a favourable excursion is better than random timing, as expected.
* At equal risk the best replacement (market entry + 0.7 / 0.5 scale-out) earns the same total as the shipped split (+0.5%) with a deeper PRE (-23%) and a shallower MID (+39%); adding scale-out on top of the split loses 11% of total at equal risk. **No cell beats the shipped 70/30 split on a risk-adjusted basis: scale-out is not a better use of the position than the resting add; combined it just reduces size.** Label: NO EDGE (volume), consistent with the split decision (DS3_D7_SPLIT_DECISION.md).
* Not done: tighten / trailing stop variants (S4b's half), other pct / frac values (prereg fixed the 2 x 2 grid).
