# NY AM weighted stack: coding status and the inputs still needed (information note)

written by the relay (Claude), not typed by Josh. No new tests, no gate or priority change. This only reports what is coded and lists the coding inputs that Josh's order 2026Z item 5 already asks for.

## Coded and checked against your parity packs (td 20261110, on Josh's NinjaTrader tick export)
| book | bars | signals | note |
|---|---|---|---|
| L43f0cbfb pnf_14 + fibr_on false_break | 83 / 83 | 58 / 58 | as AUTO:BOOK block |
| B7bfd33b7 dib_6000 + profile_va break_native | 324 / 324 | 24 / 24 | PRF1 lines rebuilt from his 9 Nov ticks; PRF5 values taken from your page (his export has no 5 days) |
| Le4fede95 swing_atr_0.4 + profile_nodes false_break_native | 184 / 184 | 27 / 27 | PRF1 nodes rebuilt from his ticks: HVN 27971 / 27952.75, SPH 27688.5, SPL 27481.25 equal your stored values; LVN 28069.25 equal, the other 28003.75 against your 28003 |
| Bf428c4a1 vol_1700 + sopen_cross | 154 / 154 complete | 12 / 12 | rule is MY READING (see 1) |
| L4407508c time_m_3 + bollinger walk | 49 (8 differ by feed timestamps at the bucket edge) | 1 / 1 | rule is MY READING (see 2) |
| L64390867 time_m_20 + avwap0830 break_0830_native | as book L8f11883e | 1 / 1 | rule is MY READING (see 3) |
Lf0346d55 and L8cfda948 are already in the file. L39287638 is NOT coded (see 4).

## Please confirm or correct, one line each, in the spec pages you are writing
1. sopen_cross buf 0.0: S = the first print of the session; LONG when close > S and the previous bar of the SAME session was not above S (first bar of the session: no previous bar); SHORT mirrored. Is the state reset at the session change, and is S the first print or the open of the first 1-minute bar?
2. bollinger walk n 30 k 1.5 N 2: mid = SMA of the last 30 closes including the current bar, population sd, LONG on the bar whose run of closes above the upper band equals exactly 2; series continuous across sessions including the truncated bar. Correct?
3. avwap0830 break_0830_native clk 3 k 1.0: VWAP and volume-weighted sd of bar typical prices restart at 08:30 ET and run through NY AM; bands defined from bar index >= 3 (so the three 20-minute bars 08:30-09:30 are the warm-up); LONG on the first close above vwap + 1.0 sd. Correct? What does "clk 3" resolve to in bars for time_m_20?
4. L39287638 vsess_50 + ma_ema cross len 20 width 2 hyst 0.0: the exact rule (my trial of EMA 20 against EMA 40 with a per-session restart gives 2 of 3 signals one bar off, so the state is not what I assumed), and the SESSION-VOLUME MEDIAN TABLE needed to build vsess_50 bars: the trailing-20 median by session code for every code the series runs in (not only code 3), 45 days, like D8_ASIA_NEWBOOK_INPUTS.md.
5. profile_nodes: the exact rule for "the two deepest local minima inside the value area" (lowest smoothed value, or depth against the neighbouring maxima?), the Gaussian kernel edge handling and the tie rules; and the PRF5 node values for 20261110 rebuilt from tape so the composite can be checked. I used: kernel sigma 8 ticks, +-24, normalised, zero padding; local max = above the row below and not below the row above.
6. Whole-lot sizes at 6 lots per book for the 0.25-weight books (L4407508c, L39287638): 1 or 2 lots, as tested. The file currently defaults them to 1, L64390867 and Lf0346d55 (weight 0.5) to 3.
7. In the file the six new books run BARE (no NY AM layer acts on them) until the fit of STKd8cd0279ff is delivered.

## Mirror
The box-reports mirror has had no commit since the one labelled 20:30Z (about 50 minutes at 21:25Z). If the push job stopped, please restart it; nothing else is implied.
