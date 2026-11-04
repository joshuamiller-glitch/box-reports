# DS3_TH_COST - cost and latency sensitivity of the TH-L2 loss cut (DIS-AX), BASE-4, 2026-11-04T22:41Z

Research only, nothing live, no PASS, no engine edits. Scope note l2vast/ds3/prereg/DISAX_scope.md sha256 371a8908c9f97489855ea85ac4752e8efee49c33624069d6def8e3d7b0b5b0e3 (DECISIONS.md, before any outcome). Engine: ZL-2's DIS-AB reference (d7_v13t run_v13t_ts2 hooks through ab_lib.run; all switches at the live ts2 reference); tie-out: the TH-on, s = 0, k = 0 run reproduces $2,520,149.07 over 935 label days exactly, TH-off $2,243,132.77. Code l2vast/ds3/code/disax/ (ax_run.py, ax_an.py, ax_doc.py; a wrapper on d7_v13t._ex_t / _sh_t, no engine file edited); data /mnt/l2/l2vast/ds3_base4/ax_out_*.pkl, ax_tab.csv.

## Answer for the user
**The +18.1k/week post-cap TH-L2 gain is not robust to realistic cut-exit costs, and over the full 2023-26 history it is already about zero.** In the engine the cut is one market exit of all lots at the trigger-second tape price with a cost of 0.80 pt per lot. Each extra point of cut-exit slippage costs about $5.2k/week after the cap: the gain falls from +18076 to +12902 (+1 pt), +7761 (+2 pts), +2498 (+3 pts) and -7219 (+5 pts); it halves at about 2 pts extra and reaches ZERO at 3.5 pts extra (total cost about 4.3 pts per lot). Over 2023-04..2026-10 (carrying weeks dropped) the gain is only +2029/week at the engine cost and reaches zero at 0.69 pts extra (total about 1.5 pts). For scale: the live stop-join exit costs 2.45 pt versus the 0.80 market frame (1.65 pt more) and the cut is a market order into a book that has just pulled at least 30x its median liquidity, so its real cost is more likely above than below 0.80; at +1.65 pts the post-cap gain is about +9560/week and the 2023-26 gain about -2732/week. No measured cut fill exists (no live log of TH-L2 firings, DS3_TH_OOS.md), so the true cost is n/a. Latency does not hurt in this tape: a fill 1-3 s after the trigger changes the post-cap gain by +502 to +1492 (on average the price recovers a little in the seconds after the trigger, so a later fill is slightly better), so cost, not latency, is the exposure. Under the fixed reading rule: not "robust" (the gain is below half at s = 2) and not "fragile" by the break-even test for the post-cap window (3.5 pts), but fragile for the whole history (0.7 pt).

## 1. How the engine models the cut exit (read from code)
* Source of the exit price: the L2CUT library table K (l2vast/ds3/code/l2cut/lc_rows.py) stores, for each trade-second row where the adverse excursion is at least 15 points, `cut` = the exit-price difference in points per lot relative to the original exit if the position is closed at that second on the 1-second path, with a market-exit cost of 0.995 pt embedded (lc_inj.shift: `mkt=0.995`). The rule is evaluated by `fire_mask` on stored per-second features: adverse (upnl <= -30) AND the pulled-support measure over the 5-s window p5 >= 30 x max(median level, 1); the first such second of a trade fires. `_compose_d7` (d7lib) then adds dN x filled lots at that second and sets the exit second to the trigger second.
* Cost frame: run_v13t sets `SHIFT[0] = 0.995 - xcost` and adds it to every cut delta, so with the live model xcost = 0.80 the cut costs 0.80 pt per lot (stop-exit cost 2.45 for the join, native 1.28, are separate: `stopcost` / STOPREL). The 0.242 pt/lot fee: not visible in this code path, so whether it is inside 0.995 / 0.80 is UNVERIFIED; the s = 0.242 run below prices it explicitly.
* Timing: the trigger second and the fill second are the same second (zero latency; the condition is evaluated on that second's data and the fill is the tape price of that second). Multi-lot: all lots exit at one price at one second (no 1 lot / 2 s slicing of the cut); what the live D7 code does for a multi-lot cut (PE has 7 lots) is UNVERIFIED (no D7 source on the box; the 2 s slice rule is documented for ENTRIES in the live fill model, DS3_P3_EXEC.md).
* Comparators: DS3_P3_EXEC.md: entry latency and slicing costs are small (within about +-$90/week at live lots per line) and the stop-fill lever (native 1.28 vs join 2.45) is worth +$3,097/week on the six books; DS3_LIVE_RECON.md: live join stops were 1.23 pt/lot worse than replay (n = 21). A cut fill measured in the live account: none exists.

## 2. TH contribution (full stack minus TH off), $ per week, by cut-exit slippage (extra pts per lot on top of 0.80) and latency (seconds after the trigger)
Post-cap = label days 2026-02-07..2026-10-30, carrying weeks dropped (25 weeks); 2023-26 = 2023-04..2026-10, carrying weeks dropped (148 weeks).
| extra slippage s | latency k | post-cap TH gain | 2023-26 TH gain | stack maxDD L6M | HOLD | PRE |
|--|--|--|--|--|--|--|
| TH off | - | 0 | 0 | +90456 | +91353 | +174642 |
| 0.0 | 0 | +18076 | +2029 | +62576 | +122025 | +75057 |
| 1.0 | 0 | +12902 | -851 | +68471 | +136361 | +83371 |
| 2.0 | 0 | +7761 | -3745 | +75028 | +161375 | +91684 |
| 3.0 | 0 | +2498 | -6444 | +83618 | +182418 | +99998 |
| 5.0 | 0 | -7219 | -11806 | +96455 | +296898 | +152266 |
| 0.0 | 1 | +18579 | +2074 | +64070 | +122422 | +72667 |
| 1.0 | 1 | +13289 | -927 | +69966 | +134099 | +82006 |
| 2.0 | 1 | +8313 | -3634 | +75585 | +162159 | +89133 |
| 3.0 | 1 | +3429 | -6311 | +84655 | +182498 | +97365 |
| 5.0 | 1 | -5586 | -11598 | +94596 | +284791 | +157711 |
| 0.0 | 2 | +18630 | +2162 | +66060 | +123131 | +75468 |
| 1.0 | 2 | +13648 | -818 | +72116 | +133031 | +83701 |
| 2.0 | 2 | +9496 | -3343 | +77192 | +148327 | +91933 |
| 3.0 | 2 | +3748 | -6169 | +83474 | +179132 | +100166 |
| 5.0 | 2 | -4300 | -11318 | +95491 | +255790 | +144109 |
| 0.0 | 3 | +19568 | +2218 | +65602 | +121064 | +75344 |
| 1.0 | 3 | +14968 | -431 | +71487 | +135105 | +84755 |
| 2.0 | 3 | +9261 | -3273 | +77493 | +155835 | +90814 |
| 3.0 | 3 | +3501 | -6140 | +85916 | +178905 | +99046 |
| 5.0 | 3 | -5306 | -11390 | +96078 | +280227 | +144275 |
| 0.242 (fee only) | 0 | +16725 | +1197 | +63501 | +124501 | +77069 |

maxDD is the full-stack weekly-cumulative maxDD in the harness windows (carrying weeks dropped). At the engine cost the cut LOWERS the L6M and PRE maxDD (TH off: +90456 and +174642) and RAISES the HOLD maxDD ($122025 vs $91353 with TH off, the PE-led W06-W09 episode), and every extra point of cut slippage deepens all three (s = 3: L6M +83618, HOLD +182418, PRE +99998; s = 5: HOLD +296898).

## 3. Break-even slippage (extra pts per lot at which the TH gain is zero; linear interpolation)
| latency k | post-cap | 2023-26 |
|--|--|--|
| 0 s | 3.51 (total cost about 4.31 pt/lot) | 0.69 (total about 1.49) |
| 1 s | 3.76 (total cost about 4.56 pt/lot) | 0.69 (total about 1.49) |
| 2 s | 3.93 (total cost about 4.73 pt/lot) | 0.73 (total about 1.53) |
| 3 s | 3.80 (total cost about 4.60 pt/lot) | 0.84 (total about 1.64) |

## 4. By book (post-cap TH gain, $/week, k = 0)
| extra s | KB | PE | SM | HM | MV | PB |
|--|--|--|--|--|--|--|
| 0.0 | +2090 | +11851 | +1122 | +2363 | +626 | +24 |
| 1.0 | +1163 | +9161 | +760 | +1737 | +57 | +24 |
| 2.0 | +437 | +6237 | +399 | +1100 | -437 | +24 |
| 3.0 | -991 | +4086 | +37 | +476 | -1134 | +24 |
| 5.0 | -2522 | -1277 | -686 | -824 | -1935 | +24 |
2023-26 TH gain by book ($/week, k = 0):
| extra s | KB | PE | SM | HM | MV | PB |
|--|--|--|--|--|--|--|
| 0.0 | +159 | +1832 | +256 | +19 | -277 | +39 |
| 1.0 | -363 | +313 | +39 | -312 | -568 | +39 |
| 2.0 | -866 | -1227 | -178 | -654 | -859 | +39 |
| 3.0 | -1462 | -2465 | -395 | -988 | -1174 | +39 |
| 5.0 | -2474 | -5105 | -829 | -1709 | -1729 | +39 |
PE carries the post-cap gain (+11851 of +18076 at s = 0) and stays positive longest (about 4.6 extra pts); MV and KB turn negative first (MV at about 1 pt, KB between 2 and 3 pts post-cap); over 2023-26 PE (+1.8k), SM (+0.3k) and KB (+0.2k) are the positive books at s = 0, MV is negative, and PE turns negative above about 1.2 pts.

## 5. Slicing of a multi-lot cut (lot j exits at trigger + 2j s; planned lots per row, approximation)
| extra s | k | slicing | post-cap TH gain | 2023-26 TH gain | HOLD maxDD |
|--|--|--|--|--|--|
| 0.0 | 0 | no | +18076 | +2029 | +122025 |
| 0.0 | 0 | 1 lot / 2 s | +18417 | +2198 | +125976 |
| 1.0 | 0 | no | +12902 | -851 | +136361 |
| 1.0 | 0 | 1 lot / 2 s | +13703 | -582 | +133016 |
| 2.0 | 0 | no | +7761 | -3745 | +161375 |
| 2.0 | 0 | 1 lot / 2 s | +9136 | -3332 | +145300 |
| 0.0 | 1 | no | +18579 | +2074 | +122422 |
| 0.0 | 1 | 1 lot / 2 s | +18887 | +2249 | +125249 |
Slicing the exit does not change the picture (the average of the later slices is within about +-$0.6k/week of the single exit); the exposure is the per-lot cost, which scales with the lots (PE 7).

## 6. Missing hooks (nothing edited)
* A per-book or per-lots cut-cost parameter (the cost is one global SHIFT; my wrapper adds the sweep outside the engine files). * A latency parameter for the cut in the engine (implemented here as a path-price wrapper using the stored per-trade 1-s path; the lock engine's exit second is moved with it). * A true slicing of the cut by LIVE lots (the 70/30 split and PE-confirmation add-on lots are not in the planned-lots approximation). * A measured liquidity-conditioned cut cost: needs the live TH-L2 cut log (DS3_TH_OOS.md: none exists) and fills with order type and per-slice prices (DS3_LIVE_RECON.md section 1 columns). * A separate fee line for cuts.

## Limits
* The sweep adds a constant adverse cost to every cut; real cost is likely larger when the book has just pulled liquidity and in the PE multi-lot case, and smaller on quiet fires. * Latency uses the 1-s path price k seconds later (a positive average move after the cut); it is an average over cuts, with no per-cut microstructure. * Post-cap is 25 weeks of one regime (DS3_TH_OOS.md: 2024 +2.6k, 2025 -4.8k, 2026 +13.7k); the 2023-26 gain here is ++2029/week at the engine cost. * Stop-exit comparators are quoted, not rerun.
