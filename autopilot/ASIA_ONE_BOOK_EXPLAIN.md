# ASIA ONE-BOOK EXPLAIN (W-COMBO, order 0735Z; information only, no rule or gate change; engine runs: none; stack sets that the loops had already built and that landed are used, anything else is labelled APPROXIMATE). Base lots, 1 lot, Asia all-new base.

## (1) Why nothing was added to L385f4f2e.J502 (current stack: L6M ulcer 469 / max DD -1915 / worst wk -1600 / $2157 per wk; best single book mean $2456)

The five candidate adds with the best return per unit ulcer whose two-book stack set had landed (15 such candidates in total); the rule that rejects is the ADD rule (stack mean >= best single book, return per unit ulcer +1%, max DD and worst week within +15% after scaling to the current ulcer; L3M shown, not a gate):

| candidate | stack L6M ulcer / max DD / worst wk / $ per wk | L3M $/wk | stack ulcer vs J502 alone | clause(s) that reject it |
|---|---|---|---|---|
| L7c368a4f | 2636 / -7977 / -5463 / 4182 | 4038 | x5.6 | return per unit ulcer -65% (needs +1%) |
| L15f14deb | 2469 / -7462 / -5081 / 3580 | 3317 | x5.3 | return per unit ulcer -68% (needs +1%) |
| M7423c0d9 | 2192 / -7458 / -4003 / 3059 | 3224 | x4.7 | return per unit ulcer -70% (needs +1%) |
| L7f41b347 | 2791 / -9771 / -6289 / 3819 | 3736 | x5.9 | return per unit ulcer -70% (needs +1%) |
| L1edb9fab | 2864 / -8592 / -5463 / 3908 | 3907 | x6.1 | return per unit ulcer -70% (needs +1%) |

Over all 15 landed candidates: fail the mean clause 1, the +1% return-per-ulcer clause 15, the max-DD guard 0, the worst-week guard 0.
PLAIN WORDS: the clause that rejects EVERY candidate is the return per unit of ulcer, NOT the 15% drawdown guards: L385f4f2e.J502 alone earns $2157 per week at an L6M ulcer of 469 = 4.60 dollars per week per unit of ulcer; every two-book stack has an ulcer of x4.5 to x8.5 of that (median x5.9) and earns 0.83 to 1.59 dollars per unit (the second book alone has an ulcer of thousands), i.e. 65% to 82% below the first book, far from the +1% needed. The max-DD and worst-week guards are met by all 15 candidates (0 fail) because they are measured after scaling the stack down to the current tiny ulcer; so it is NOT true that the guard can never be met: it is the first book's very high return per unit ulcer (from a quiet L6M, 166 trades) that no combination can beat. One candidate also fails the mean clause (a stack mean below the best single book, $2456).

## (2) Side by side, all windows (ulcer / max DD / worst wk / $ per wk); BARE D7 Asia stack beside each at the SAME L6M drawdown (bare lots scaled by k)

**(i) L385f4f2e.J502 alone (TL3_ALN_AS_L385f4f2e_P2JCX502)**: own persistence 0.65; controls beaten (30, 27, 30) (L6M drawdown-first / L3M / ulcer-only)

| window | stack | BARE D7 at the same L6M drawdown (x0.04) |
|---|---|---|
| L6M | 469 / -1915 / -1600 / 2157 | 469 / -1153 / -755 / 202 |
| L3M | 519 / -1915 / -219 / 2514 | 436 / -998 / -637 / 114 |
| Y2023 | 2327 / -4696 / -2024 / 40 | 731 / -1195 / -292 / -6 |
| Y2024 | 4263 / -11407 / -3539 / 217 | 332 / -917 / -289 / 50 |
| Y2025 | 4368 / -10172 / -3904 / 179 | 697 / -1380 / -525 / 45 |

**(ii) previous final (pool 27): L7c368a4f + La010c3eb (TL3_ALN_AS_STKd89353ef89, _CANF)**: own persistence 0.68; controls beaten (27, 16, 29)

| window | stack | BARE D7 at the same L6M drawdown (x0.36) |
|---|---|---|
| L6M | 4789 / -14639 / -9096 / 3848 | 4789 / -11770 / -7703 / 2062 |
| L3M | 4700 / -14639 / -8658 / 3853 | 4453 / -10181 / -6499 / 1163 |
| Y2023 | 2746 / -7215 / -2853 / 660 | 7455 / -12191 / -2979 / -58 |
| Y2024 | 7791 / -22530 / -6082 / 1078 | 3392 / -9360 / -2950 / 506 |
| Y2025 | 12684 / -28865 / -16300 / 633 | 7110 / -14076 / -5353 / 464 |

**(iii) OPTION C = asia-stay main FINAL, pool 35: L7c368a4f + L578701ed + L385f4f2e.J502 (EXACT stack set TL3_ALN_AS_STKd88bbb46dc landed)**: own persistence 0.70; controls beaten (30, 19, 30)

| window | stack | BARE D7 at the same L6M drawdown (x0.38) |
|---|---|---|
| L6M | 4930 / -13326 / -7847 / 6056 | 4930 / -12115 / -7930 / 2122 |
| L3M | 6275 / -13326 / -6941 / 4446 | 4584 / -10480 / -6690 / 1198 |
| Y2023 | 3347 / -10314 / -6247 / 963 | 7674 / -12549 / -3067 / -60 |
| Y2024 | 7859 / -23992 / -5607 / 1011 | 3491 / -9635 / -3037 / 520 |
| Y2025 | 7320 / -21203 / -16459 / 1221 | 7319 / -14490 / -5510 / 478 |

## (3) Trade count and concentration of L385f4f2e.J502 (events = J502 filtered stream; trades = engine trades of its base set)

| window | events | trades | trades per month | weeks with >= 1 trade / weeks in window | best 5 days: share of the window's profit | best month: share |
|---|---|---|---|---|---|---|
| L6M | 199 | 166 | 27.7 | 27 / 27 | 23% | 25% (202609) |
| L3M | 97 | 76 | 25.3 | 13 / 13 | 36% | 44% (202609) |
| Y2023 | 98 | 76 | 8.4 | 35 / 39 | 358% | 176% (202307) |
| Y2024 | 173 | 141 | 11.8 | 48 / 53 | 66% | 41% (202409) |
| Y2025 | 214 | 186 | 16.9 | 49 / 49 | 115% | 89% (202506) |

Profit per week (window mean): L6M $2157; the gain per trade matters, not only fewer trades: L6M $351 per trade, 2023 $20, 2024 $82, 2025 $47.

## (4) Labels
- L385f4f2e.J502 alone = **LEAD: one book, prior years thin (2023 +$40/wk), fits pending** (W-P2A caveat: its plain _CANC base is $476/wk in L6M).
- L7c368a4f + La010c3eb = **previous final (pool 27)**, still a spec-draft candidate (controls 27/16/29, own persistence 0.68).
- The v1 freeze text shows BOTH so Josh chooses; the two-book stack is not dropped from the spec draft.