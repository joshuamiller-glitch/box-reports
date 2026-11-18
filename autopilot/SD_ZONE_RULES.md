# SD_ZONE_RULES: supply/demand zones exactly as coded (trig_levels_sd5 / sd15 / sd60)
Read from code/th_grid/triggers_d/fd_sd.py (zones) and lv_sd_base.py (triggers). Written 2026-11-18, data end 2026-11-13. Numbers below are the constants in the code.

**1. Bars and life.** Zones are drawn on TIME bars only: the 1-minute chart bars aggregated to 5, 15 or 60 minutes (3 modules). Not drawn on tick/volume/renko bars; the bar row of the grid only decides where the trigger fires against the zone lines. A zone lives 3 days (5m), 10 days (15m), 30 days (60m) from formation, then expires. Zones found over 3.6 years: 1,143 (5m), 343 (15m), 106 (60m).

**2. Base.** The 1 to 3 bars right before the impulse bar (take bars back from the impulse while each has range < 0.7 x ATR14, max 3). ATR14 = Wilder average of true range on the same aggregated bars, value of the bar before the impulse. No rule on body size, overlap, or base height vs impulse. Switchable: no (constants).

**3. Impulse.** One bar (so speed = 1 bar by construction): body (|close-open|) >= 1.5 x ATR14 and body >= 0.6 x its range; direction = colour. Quality filter DEP (= body / ATR) can be raised to 2.5 (grid D). It does not have to close beyond the base and does not have to break a swing; "broke structure" is only a recorded feature (close beyond the prior 8-bar high/low before the base).

**4. Lines (body-to-wick, fixed).** Demand: distal = lowest low of the base bars; proximal = highest body edge (max of open, close) of the base bars. Supply: distal = highest high; proximal = lowest body edge. Shapes by the bar BEFORE the base (leg-in colour) and the impulse direction: RBR (up, up) = 1 and DBR (down, up) = 2 are demand; RBD (up, down) = 3 and DBD (down, down) = 4 are supply. Continuation = RBR, DBD; reversal = DBR, RBD. The code records the type; it does not filter by it.

**5. Freshness and death (aggregated bars only, never inside a bar).** TEST = a completed bar after formation whose low <= proximal (demand) or high >= proximal (supply): any touch of the proximal line, no penetration percentage. Counted per bar, TST shown 0, 1, 2 (3 or more tests display as 2: not yet separated). Grid F: 0 = untested only, 2 = tested up to 2. DEAD = a completed bar CLOSES beyond the distal line (demand: close < distal; supply: close > distal), zero tolerance. A zone already containing price is not used (price must be outside the proximal line).
Selected zone per minute: the NEAREST live demand below / supply above the previous minute close.

**6. Quality features (stored per bar, not scored yet; used as filters only via F and D).** DEP (impulse body / ATR), NB (base bars 1-3), TST (0-2), ST (structure break 0/1), LOC (zone mid position in the range of the 60 bars before the base: 0 discount, 1 premium), TYP (1-4), nesting flags (lower-timeframe zone proximal inside a higher-timeframe zone: 5 in 15, 5 in 60, 15 in 60), room = distance in bar-ranges to the opposing zone proximal (sd*_dSprox / dDprox) and to the nearest line of any level type (lv_any_dU / dD). Columns in feat_d/rows (see GRID_STATUS).

**7. Entries tested (8 variants x grid = 40 sets per module; "plain" widths in 5-point units, "native" in the bar's trailing median range).** All enter at the CLOSE of the signal bar (harness fills the first tape print after it). A true resting limit at the proximal line is NOT what is tested.
- reject (8 sets): bar touches the proximal line within tol (0 or 0.5 units), prior close was outside, bar closes back outside; long at demand, short at supply. F in {0,2} x D in {1.5,2.5} x tol in {0,0.5}.
- reject_flow (4): same plus bar delta (buy minus sell volume of the bar) > 0 for long / < 0 for short; this is the only order-flow confirmation built. Absorption and book-wall confirmations are NOT built.
- break (4): n = 1 or 2 closes beyond the DISTAL line (zone failure), trade the break (short through demand, long through supply); F in {0,2}, D = 1.5.
- retest (4): zone broken through distal (F2, D1.5), then within M = 3 or 6 bars a retest of the line from the other side that rejects (tol 0 or 0.5): trade the flipped zone.
Sets per scale: 8 + 4 + 4 + 4 = 20; x plain and native = 8 variants, 40 sets.

**8. Stop / target.** In the grid today: the harness brackets (plain 60/60, symmetric 8/15/30 x u, asymmetric 10/20, 20/10, 15/30 x u, u = trailing median bar range, clipped 10-120 points). Zone bracket exists as a function zone_bracket(bars, sig) in each module: stop = distance to the distal line plus 1 u beyond it (u in points, not ticks); target = distance to the nearest opposing zone proximal line (F2, D1.5); NaN if none. The harness mode that uses it is NOT built (asked W-GRIDA / W-GRIDE; I do not edit gcore.py). No R-multiple targets coded.

**9. Versus D7 PoiSet zones.** PoiSet (live) keeps single price LINES (prior-day mid, RTH camarilla H3, 1h Kijun, 4h CRT mid, 4h Keltner upper, OTE 62/70.5/79 of 15m swings) and acts on them with HALF-size or skip lot rules while a trade runs toward an untouched line. S/D zones are proximal/distal pairs found from base-then-impulse structure, with freshness and quality features, used as entries (and later a bracket), not as lot rules.

**10. Switchable now vs not.** Switchable (grid parameters): F (test allowance), D (departure 1.5 or 2.5 ATR), tol, n, M, plain vs native widths. NOT yet switchable (fixed constants, need a rebuild of fd_sd.py): wick-to-wick vs body-to-wick, base max bars (3) and base range limit (0.7 ATR), body/range 0.6, test definition (penetration %), death tolerance, age limits. I will turn these into parameters when the user states his convention.

**11. Not yet built from order 23:08Z.** zone-aware bracket mode in the harness (waiting W-GRIDA/E); true limit-at-proximal fill; absorption and book-wall confirmations (wall data exists to 11-13); zone-quality feature ranking per session (needs pass-2 trade output); S/D heat row and page section (code ready, no S/D result yet: modules just entered the queue); zones on non-time bars; counting 3+ tests; penetration-% tests.


---
# V2 (2026-11-18 00:30Z, order 00:06Z): every definition is a parameter (fd_sd2.py). The v1 rules above stay as the row "strict".
**Definition parameters (DEFS in fd_sd2.py; all switchable by editing one dict or adding a DEFS entry):** Lmax (impulse leg 1-5 bars), xatr (leg net move >= X x ATR: 1.0/1.5/2.0), kbase (leg net move >= K x base height: 3), prog (net progress / leg range 0.6-0.8), gapfvg (require a 3-bar gap inside the leg), brk (require structure break), Bmax (base 1-6 bars), base_atr (each base bar range <= 0.5/0.7/1.0 x ATR), base_frac (base height <= f x leg), single (single-candle base = order block), conv (0 body-to-wick, 1 wick-to-wick, 2 body-to-body), p50 (proximal at the 50% line), tmode (test = touch / 25% / 50% penetration), dmode (dead = close beyond distal / wick beyond distal by `ticks`), ticks, age (days). Tests allowed (F: 0 first touch, 2 up to 2, 9 any) is chosen at use time.
**Named definitions:** strict (v1), A loose (3-bar leg, 1.0 ATR, base up to 6 bars), B medium (1.5 ATR, 0.7), C tight (2.0 ATR), D (leg >= 3 x base height), E order block, Aww / Abb / Ap50 / Apen / Awick (A with that convention), Agap, Abrk.
**Bars:** time 1/2/3/5/15/30/60 min and non-time rows rng_28, renko_28, vol_1100 (zones drawn on that bar series; vsess row not yet). Multi-timeframe nesting flags exist (5 in 15, 5 in 60, 15 in 60) in the per-bar store.
**Entries (market + resting limit, W-GRIDE contract):** rej, rej_flow, rej_zone (stop distal + 4 ticks, target opposing zone proximal with room >= 2R else skipped, or 2R), lim_prox (limit at proximal, armed within 4 u, rests 4 bars, 1-tick trade-through), lim_mid (limit at 50% line), break, retest. Signal columns emitted: stop_pts, target_pts, limit_px (NaN = market), expiry_bars. Stop ticks (4), reach (4 u), expiry (4 bars) are constants in lv_sdx_base.py for pass 1; stop 1-8 ticks / 0.25-1 x zone height and R targets 1R/3R are the next grid step.
**Modules (pass 1, 8):** trig_levels_sdx3/5/15/30/60 (definitions A, B, E) and sdx_rng28 / sdx_vol1100 / sdx_renko28 (B, E); sdx variants of conventions (Aww, Abb, Ap50, Apen, Awick, Agap, Abrk) have lines built on 5m and 15m and enter the grid as the next module group. Not yet: absorption and book-wall confirmation entries, queue-aware fills, session-volume bars, zone-quality ranking per session (needs pass-2 trade output).
**Density (zones formed per trading day per session and first touches per day; full table autopilot/SD_DENSITY.md):**

|   tf | defn   |   per_day |   zones_London |   zones_NYAM |   zones_NYPM |   firsttouch_London |   firsttouch_NYAM |   firsttouch_NYPM |
|-----:|:-------|----------:|---------------:|-------------:|-------------:|--------------------:|------------------:|------------------:|
|    5 | strict |      1.23 |           0.38 |         0.09 |         0.14 |                0.32 |              0.13 |              0.1  |
|    5 | A      |     34.93 |          10.66 |         3.44 |         6.46 |                9.39 |              3.59 |              5.17 |
|    5 | B      |      6.99 |           1.94 |         0.6  |         1.21 |                1.61 |              0.66 |              0.81 |
|    5 | E      |     48.37 |          15.92 |         6.66 |         7.6  |               13.79 |              6.42 |              6.14 |
|    5 | Agap   |     13.11 |           3.54 |         1.27 |         2.54 |                3.2  |              1.37 |              1.87 |
|    5 | Abrk   |     19.32 |           5.85 |         1.89 |         3.56 |                5.16 |              2.11 |              2.67 |
|   15 | strict |      0.37 |           0.13 |         0.03 |         0.06 |                0.08 |              0.06 |              0.02 |
|   15 | A      |     10.16 |           3.6  |         0.74 |         2    |                2.95 |              1.25 |              1.27 |
|   15 | B      |      1.91 |           0.64 |         0.09 |         0.34 |                0.46 |              0.27 |              0.15 |
|   15 | E      |     15.26 |           5.48 |         2.66 |         2.65 |                4.21 |              2.56 |              2.05 |
|   15 | Agap   |      3.87 |           1.15 |         0.21 |         0.74 |                0.98 |              0.49 |              0.41 |
|   15 | Abrk   |      5.84 |           2.12 |         0.5  |         0.96 |                1.65 |              0.87 |              0.59 |
|   30 | strict |      0.21 |           0.07 |         0.02 |         0.03 |                0.03 |              0.05 |              0.01 |
|   30 | A      |      4.71 |           1.88 |         0.42 |         0.74 |                1.18 |              0.8  |              0.39 |
|   30 | B      |      0.98 |           0.42 |         0.07 |         0.1  |                0.18 |              0.2  |              0.05 |
|   30 | E      |      7.18 |           2.28 |         1.46 |         1.53 |                1.4  |              1.29 |              1.17 |
|   30 | Agap   |      1.85 |           0.73 |         0.18 |         0.22 |                0.47 |              0.33 |              0.12 |
|   30 | Abrk   |      2.89 |           1.22 |         0.37 |         0.35 |                0.69 |              0.56 |              0.23 |
