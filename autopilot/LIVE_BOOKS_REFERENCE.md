## LIVE BOOKS AS REFERENCE (W-LIVEREF, 2026-11-19 01:41Z)

Each live D7 book run BARE (its own signal_fn from code/th_swap, on its live bar row: K7 tm180, M7 tm60, U7 tm600, P7/H7/A7/O7 tm60 with nom_s=60), plain 60/60 bracket, both sides, NO layers, through the same R0, own-stop (N = 1.5/2/3 stops per label day), and stages A/B/C of the R3 machinery: 30 / 200 / 1,000 same-count random-entry draws (seeds crc32(row+'live7_<BOOK>'+'r3rand<n>'+'0'), same gjob2.rand_signals), p = (1+k)/(1+n) on the last-26-week equal-risk R sum (stop 60), weakest-prior-year p on the minimum of the 2023/24/25 R per week. 'beats of 30' = draws strictly below the real series. Last data week index 189. Code: code/th_liveref/lr_run.py; raw JSON /mnt/l2/l2vast/_grid/liveref/ (Dallas).

| book | session | L6M trades | R0 pass? | own-stop (R1) pass? (1.5/2/3) | beats of 30 | p at 200 | p at 1,000 | weakest-prior-year p | L6M R | L6M pts | live engine $/wk (engine lots) | x1.75 live lots |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | Asia | 366 | fail | n/n/n | 22 | 0.299 | 0.3257 | 0.050 | -3.7 | -224 | 846 (n=373, 1 lot) | 1,480 |
| A7 | London (not traded live) | 336 | fail | n/n/n | 17 | 0.423 | 0.3916 | 0.259 | 2.9 | 173 | - | - |
| A7 | NYAM (not traded live) | 244 | fail | n/n/n | 11 | 0.612 | 0.5764 | 0.496 | -0.4 | -23 | - | - |
| A7 | NYPM (not traded live) | 204 | fail | n/n/n | 6 | 0.905 | 0.9001 | 0.900 | -23.8 | -1431 | - | - |
| H7 | Asia | 138 | fail | n/n/n | 27 | 0.109 | 0.0929 | 0.238 | 13.0 | 781 | 1,772 (n=143, 2 lot) | 3,101 |
| H7 | London (not traded live) | 133 | fail | n/n/n | 25 | 0.403 | 0.4236 | 0.086 | 1.7 | 104 | - | - |
| H7 | NYAM | 86 | fail | n/n/n | 28 | 0.045 | 0.0360 | 0.869 | 14.5 | 867 | 325 (n=38, 1 lot) | 569 |
| H7 | NYPM (not traded live) | 84 | fail | n/n/n | 14 | 0.562 | 0.5544 | 0.855 | -2.7 | -159 | - | - |
| K7 | Asia | 683 | fail | n/n/n | 28 | 0.025 | 0.0380 | 0.529 | 31.3 | 1875 | 3,416 (n=843, 1 lot) | 5,979 |
| K7 | London | 583 | fail | n/n/n | 5 | 0.761 | 0.7822 | 0.282 | -22.9 | -1371 | -175 (n=458, 1 lot) | -306 |
| K7 | NYAM | 509 | fail | n/n/n | 4 | 0.905 | 0.9161 | 0.270 | -32.7 | -1964 | -378 (n=187, 1 lot) | -662 |
| K7 | NYPM | 476 | fail | n/n/n | 13 | 0.627 | 0.6204 | 0.574 | -9.7 | -584 | 586 (n=156, 1 lot) | 1,025 |
| M7 | Asia (not traded live) | 593 | fail | n/n/n | 29 | 0.020 | 0.0220 | 0.005 | 35.0 | 2102 | - | - |
| M7 | London | 527 | fail | n/n/n | 11 | 0.682 | 0.7053 | 0.947 | -17.2 | -1030 | -380 (n=515, 1 lot) | -666 |
| M7 | NYAM | 469 | fail | n/n/n | 17 | 0.453 | 0.5015 | 0.033 | -3.9 | -232 | 417 (n=227, 1 lot) | 731 |
| M7 | NYPM (not traded live) | 410 | fail | n/n/n | 11 | 0.701 | 0.7103 | 0.423 | -15.9 | -956 | - | - |
| O7 | Asia (not traded live) | 0 | fail | n/n/n | 0 | 1.000 | 1.0000 | 1.000 | 0.0 | 0 | - | - |
| O7 | London (not traded live) | 0 | fail | n/n/n | 0 | 1.000 | 1.0000 | 1.000 | 0.0 | 0 | - | - |
| O7 | NYAM | 65 | fail | n/n/n | 21 | 0.234 | 0.2408 | 0.005 | 4.5 | 269 | 279 (n=45, 1 lot) | 488 |
| O7 | NYPM (not traded live) | 0 | fail | n/n/n | 0 | 1.000 | 1.0000 | 1.000 | 0.0 | 0 | - | - |
| P7 | Asia | 658 | fail | n/n/n | 28 | 0.040 | 0.0500 | 0.247 | 30.6 | 1838 | 8,919 (n=599, 2 lot) | 15,609 |
| P7 | London | 547 | fail | n/n/n | 27 | 0.080 | 0.0789 | 0.722 | 26.1 | 1568 | 998 (n=398, 1 lot) | 1,746 |
| P7 | NYAM | 523 | fail | n/n/n | 0 | 0.896 | 0.8711 | 0.466 | -31.0 | -1862 | 284 (n=43, 1 lot) | 497 |
| P7 | NYPM (not traded live) | 451 | fail | n/n/n | 11 | 0.637 | 0.6164 | 0.946 | -11.4 | -684 | - | - |
| U7 | Asia | 153 | fail | n/n/n | 26 | 0.075 | 0.0679 | 0.047 | 15.3 | 921 | 1,731 (n=155, 2 lot) | 3,029 |
| U7 | London | 131 | fail | n/n/n | 8 | 0.711 | 0.6703 | 0.678 | -4.6 | -277 | 1,093 (n=105, 2 lot) | 1,912 |
| U7 | NYAM (not traded live) | 80 | fail | n/n/n | 14 | 0.652 | 0.7093 | 0.006 | -4.9 | -296 | - | - |
| U7 | NYPM (not traded live) | 39 | fail | n/n/n | 18 | 0.318 | 0.3257 | 0.613 | 2.1 | 124 | - | - |

### Reading it
- No book passes R0 in any session. K7 Asia, P7 Asia/London, M7 Asia (not traded live), H7 NYAM have p(1,000) <= 0.05 on the L6M test, but each fails another R0 clause (prior-year RED in all of 2023-25 for K7 Asia; persistence < 0.60), so as a grid cell they would not survive. The live books are NOT better than the grid survivors on this test; Asia is where they look alive (K7, P7, M7, H7, U7).
- London K7/M7/U7, NYAM K7/P7 bare are negative on plain 60/60: the live dollars in those sessions come from the live bracket/exits/layers, not from the bare trigger.
- Engine $/wk is the JL3 exact engine, last 26 weeks to 2026-11-13 (net of fees, engine base lots; x1.75 = live lot multiplier), NEW_BOOK_ENGINE.md style. It is NOT comparable in size to the bare R column: the bare test is plain 60/60 with no layers.

### Caveats (honest)
- First-order screen. Brackets: live brackets differ (K7 59, P7 58, M7 59.5, engine 60); the harness uses plain 60/60 on every book, so this tests the trigger, not the live exit logic. Live exits (EMA/Supertrend/HMA lines, trails, near-target, cuts) are not in the test. H7's trail line is the HMA20 PROXY and is not used here at all.
- Fills/slippage as the harness ($4.84 RT, first print after bar close). P7/H7/A7/O7 are aggregated inside their signal functions from a 1-min base (tm60, nom_s=60); that matches the live aggregation by construction in th_swb/adapt but was not independently proven on this run. The live bar row for K7 is the tm180 clock-aligned grid row, M7 tm60, U7 tm600.
- The seven books are single parameter sets (live defaults); there is no selection, so the p-values are plain one-test p-values with no search penalty (they are not comparable to the family-best p-values of searched cells, which carry multiplicity).
- O7 trades only NYAM (09:30 start); zero signals in other sessions is by design. Sessions marked 'not traded live' are shown for completeness (the JL3 engine has no live trades there). Live engine session = the entry session in the JL3 trades.
- Own-stop columns use the grid table path (forward-path table) at N = 1.5/2/3; 'n' = fails R0 at that N.
