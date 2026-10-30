# DS3_CONFIRM_BARS - bar types as the confirmation (CONFIRM-LAYER addendum 2 + T-BARS-ALL store), BAR-STORE

Scope: every bar type in the store (355 + 82 specs, 7 stages) used as the second confirmation on the held signal of the ten engine books (KB PE SM HM MV PB DN ST WT MA; CR has no 1-s path), 2023-04-03 .. 2026-02-06, UNTOUCHED never read. Mechanics (a) market at the bar close, (b) resting limit at the confirming bar's body mid / open / against-extreme, (c1) dip 3/5/8/10 pts AND confirmation, (c2) limit at the bar open once a 3/8-pt dip started, (d) bar-type state already in favour at the signal (filter), each on the 70/30 base and the pure-wait base, bases N and M. (e) count-as-sizer and the structure-stop style of (f) are NOT done (stage S5, needs the engine to take a structure stop); capacity (depth at fills) and the vol-tercile regime split are NOT computed (flagged in the header table). 1-s and 3-s latency, 200-draw placebo, RC/Romano-Wolf, DSR, PBO, neighbours, breakeven slippage and top-5% share were computed for the best candidate per book per stage (the QUANT layer; other candidates carry only the 4-7 draw placebo and the program RC).

Primary number: pts per planned lot (= per contract of the planned 1-lot position) of the cell minus the 70/30 plain 3-pt dip floor on the same trades (N basis = no target-fill correction; M basis beside it in the parquet). SE week-clustered, MDE = 2.8 SE. Fill rate = share of signals where the confirmation entry (or the 30% add) happened; for the pure-wait base the unfilled signals are NOT traded (value 0) - their floor P&L is the skipped-signal cost/benefit (see below). Fixed-distance rules, splits and re-based targets are STRUCTURE, not L2 edge.

## Verdict
Selected cell x book pairs per stage and tier (selection on PRE u X' only against the floor; one recent look per stage):

| stage | content | PASS | CANDIDATE | CANDIDATE-RECENT | BEST-AVAILABLE-NEGATIVE |
|---|---|---|---|---|---|
| S1 | HA (15s,30s,45s,2m,10m,30m,1h) + sub-minute candle anatomy | 0 | 12 | 17 | 63 |
| S2 | renko / UniRenko / median+ATR renko / Kagi / P&F / zig-zag (line break + smoothed bars: see S2c) | 0 | 6 | 8 | 71 |
| S2b | range / tick / volume / dollar / delta / mixed / momentum-net / imbalance and run bars | 0 | 5 | 11 | 104 |
| S3 | footprint rules on 15s/30s/1m/5m | 0 | 5 | 19 | 96 |
| S4 | T-BARS-ALL extension types (phantom range, grid/hybrid renko, reversal, entropy, Delta-Pro, session-fraction, HA of activity bars, VWAP cross, L2-event, absorption bars) | 0 | 4 | 9 | 107 |
| S1c | HA 1m/3m/5m/15m (re-score after the store defect) | 0 | 5 | 14 | 101 |
| S2c | line break, LinReg, Hull, momentum colour, Kase-proxy (re-score after the store defect) | 0 | 3 | 12 | 105 |

No bar-type confirmation is a PASS: the cumulative-multiplicity-adjusted p is ~1.0 for every cell (p x 153,000 trials; DSR <= 0.31; Romano-Wolf p >= 0.422; the stage PBO is 0.20-0.69), and every best cell sits inside its own MDE except where the table says otherwise. The floor (70/30 plain 3-pt dip split) has NOT moved. Of the 37 best-candidate cells put through the 200-draw time-matched random-confirmation placebo, 7 rank in the top 10 of 201 in BOTH L6M and HOLD and are >= 0 in L6M, HOLD, PRE and X' (listed as LEADS in out/confirm/bars/THP_bars_candidates.txt, not merged into THP_POLICY.txt); the rest do no better than random confirmations.

Honest reading: waiting for a bar-type confirmation does not buy a better entry than the plain 3-pt dip floor on this data once multiplicity is counted; the cells that survive the placebo are LEADS to watch forward (all on the 70/30 base: HA, LinReg, dollar-bar and range-bar states used as FILTERS, plus two HA limits; the gain is mostly which signals are skipped or which add is taken), not entry rules.

## Section-5 header: best candidate per book per stage (QUANT layer)
| stage | book | cell (plain words below) | d vs floor L6M [week-block CI] | L3M / L6M / HOLD / PRE / X' | trades/wk | fire | RC p (stage) | Romano-Wolf p | DSR | PBO (stage) | placebo rank L6M / HOLD (of 201) | nbr mean (sizes / same spec) | breakeven slip (pts) | capacity | top5% share | stack corr | regime | pos quarters | latency 1s / 3s L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S1 | KB | `ha|30s|flip|a|near|X3|W0|N` | +1.27 [-1.31, +4.55] | +3.07 / +1.27 / +0.91 / +0.39 / +0.76 | 45 | 0.89 | 0.59 | 0.97 | 0.001 | 0.26 | 18/201 / 27/201 | -0.16 / +0.16 | 1.42 | not computed | 0.46 | -0.50 | session table below (vol tercile not computed) | 9/12 | +0.69 / +0.75 |
| S1 | MV | `ha|2m|strong|d|near|X3|W0|N` | +0.72 [-1.01, +2.41] | +0.83 / +0.72 / +0.88 / +0.21 / +2.02 | 40 | 0.68 | 0.83 | 0.98 | 0.026 | 0.26 | 58/201 / 74/201 | -0.94 / -1.72 | 1.05 | not computed | 0.32 | -0.44 | session table below (vol tercile not computed) | 11/12 | +0.56 / +0.65 |
| S1 | PE | `tc|45s|three_bar|a|near|X3|W0|N` | +2.58 [+0.11, +4.71] | +4.32 / +2.58 / +2.28 / +1.02 / -0.05 | 43 | 0.74 | 0.47 | 0.68 | 0.038 | 0.26 | 2/201 / 2/201 | +1.04 / +1.13 | 3.49 | not computed | 0.27 | -0.40 | session table below (vol tercile not computed) | 9/12 | +2.13 / +2.60 |
| S1 | ST | `ha|10m|three|d|near|X3|A70|N` | +0.32 [-1.12, +1.65] | +1.87 / +0.32 / +0.35 / +0.20 / +1.13 | 45 | 0.70 | 0.94 | 0.99 | 0.003 | 0.26 | 1/201 / 3/201 | -1.43 / -1.61 | 0.45 | not computed | 0.39 | -0.47 | session table below (vol tercile not computed) | 8/12 | +0.27 / +0.14 |
| S1 | WT | `tc|15s|engulf|b|mid|X3|W0|N` | +0.18 [-1.09, +1.43] | -0.45 / +0.18 / +0.38 / +0.13 / +0.69 | 61 | 0.63 | 0.89 | 0.99 | 0.003 | 0.26 | 5/201 / 15/201 | +0.03 / +0.18 | 0.29 | not computed | 0.35 | -0.69 | session table below (vol tercile not computed) | 6/12 | +0.16 / +0.15 |
| S1c | DN | `ha|3m|three|b|mid|X3|A70|N` | +0.82 [-0.32, +2.07] | +0.51 / +0.82 / +1.05 / +0.38 / +0.32 | 25 | 0.51 | 0.80 | 0.80 | 0.026 | 0.28 | 4/201 / 2/201 | -0.55 / -0.26 | 1.60 | not computed | 0.29 | -0.50 | session table below (vol tercile not computed) | 9/12 | +0.81 / +0.72 |
| S1c | HM | `ha|1m|strong|d|near|X3|A70|N` | +0.77 [-0.80, +2.31] | +2.22 / +0.77 / +0.71 / +0.23 / -0.06 | 32 | 0.76 | 0.86 | 0.86 | 0.001 | 0.28 | 10/201 / 22/201 | -1.70 / -0.75 | 1.02 | not computed | 0.53 | -0.26 | session table below (vol tercile not computed) | 6/12 | +0.58 / +0.22 |
| S1c | KB | `ha|1m|flip|c2|mid|X3|A70|N` | +0.87 [-0.13, +2.05] | +1.64 / +0.87 / +0.78 / +0.15 / +0.38 | 45 | 0.62 | 0.57 | 0.72 | 0.007 | 0.28 | 1/201 / 3/201 | +0.15 / +0.09 | 1.39 | not computed | 0.42 | -0.46 | session table below (vol tercile not computed) | 8/12 | +0.83 / +0.67 |
| S1c | MV | `ha|3m|strong|d|near|X3|W0|N` | +0.20 [-1.14, +1.55] | +0.87 / +0.20 / +0.42 / +0.31 / +1.80 | 40 | 0.69 | 0.99 | 1.00 | 0.013 | 0.28 | 74/201 / 105/201 | -0.58 / -1.55 | 0.29 | not computed | 0.34 | -0.46 | session table below (vol tercile not computed) | 9/12 | +0.25 / +0.30 |
| S1c | PE | `ha|15m|flip|d|near|X3|A70|N` | +1.11 [-0.55, +2.55] | +1.93 / +1.11 / +0.86 / +0.55 / +0.40 | 43 | 0.70 | 0.62 | 0.84 | 0.011 | 0.28 | 7/201 / 6/201 | -0.04 / -0.03 | 1.59 | not computed | 0.38 | -0.49 | session table below (vol tercile not computed) | 7/12 | +1.06 / +0.96 |
| S1c | WT | `ha|15m|two|d|near|X3|W0|N` | +0.39 [-0.62, +1.45] | +0.46 / +0.39 / +0.35 / -0.11 / +0.86 | 61 | 0.73 | 0.87 | 0.95 | 0.002 | 0.28 | 2/201 / 11/201 | -0.50 / -1.86 | 0.54 | not computed | 0.46 | -0.48 | session table below (vol tercile not computed) | 7/12 | +0.35 / +0.32 |
| S2 | DN | `renkomed|m1|n2|d|near|X3|A70|N` | +0.22 [-0.92, +1.31] | +1.37 / +0.22 / +0.13 / +0.94 / +0.10 | 25 | 0.85 | 0.93 | 1.00 | 0.032 | 0.56 | 30/201 / 41/201 | n/a / -0.12 | 0.26 | not computed | 1.00 | -0.14 | session table below (vol tercile not computed) | 8/12 | +0.12 / -0.11 |
| S2 | HM | `renko|8|rev|b|far|X3|A70|N` | +0.22 [-0.89, +1.73] | +0.55 / +0.22 / +0.10 / +0.28 / -0.34 | 32 | 0.82 | 0.98 | 0.99 | 0.000 | 0.56 | 3/201 / 3/201 | -0.14 / -0.60 | 0.27 | not computed | 0.71 | -0.27 | session table below (vol tercile not computed) | 7/12 | +0.27 / +0.11 |
| S2 | KB | `kagi|32|rev|d|near|X3|W0|N` | +0.44 [-2.14, +3.12] | +1.50 / +0.44 / +0.56 / +0.15 / +1.67 | 45 | 0.67 | 0.82 | 1.00 | 0.002 | 0.56 | 10/201 / 16/201 | -1.55 / +0.08 | 0.66 | not computed | 0.33 | -0.61 | session table below (vol tercile not computed) | 7/12 | +0.36 / +0.53 |
| S2 | PE | `renko|6|n3|b|far|X3|W0|N` | +0.74 [-0.89, +2.22] | +1.74 / +0.74 / +0.55 / +0.82 / +0.50 | 43 | 0.87 | 0.60 | 0.98 | 0.027 | 0.56 | 42/201 / 43/201 | +0.09 / -0.02 | 0.85 | not computed | 0.49 | -0.55 | session table below (vol tercile not computed) | 8/12 | +0.73 / +0.87 |
| S2 | WT | `renko|4|n3|b|mid|X3|W0|N` | +0.37 [-0.51, +1.24] | +0.54 / +0.37 / +0.83 / +0.01 / +1.10 | 61 | 0.80 | 0.98 | 0.98 | 0.018 | 0.56 | 13/201 / 7/201 | -0.46 / -0.18 | 0.46 | not computed | 0.55 | -0.53 | session table below (vol tercile not computed) | 8/12 | +0.23 / +0.45 |
| S2b | DN | `dol|100M|beyond_prior|a|near|X3|A70|N` | +0.35 [-0.25, +0.84] | +0.32 / +0.35 / +0.41 / +0.74 / -0.05 | 25 | 0.97 | 0.96 | 0.96 | 0.175 | 0.42 | 120/201 / 120/201 | +0.31 / +0.01 | 0.36 | not computed | 0.52 | -0.14 | session table below (vol tercile not computed) | 7/12 | +0.37 / +0.49 |
| S2b | HM | `dol|4G|close_fav|d|near|X3|A70|N` | +0.64 [-1.10, +2.51] | +0.72 / +0.64 / +0.61 / +0.04 / +0.36 | 32 | 0.64 | 0.82 | 0.95 | 0.001 | 0.42 | 8/201 / 14/201 | -1.06 / -0.70 | 0.99 | not computed | 0.33 | -0.53 | session table below (vol tercile not computed) | 7/12 | +0.64 / +0.71 |
| S2b | KB | `range|8|close_fav|d|near|X3|A70|N` | +0.30 [-2.13, +2.74] | +0.81 / +0.30 / +0.16 / +0.47 / +0.81 | 45 | 0.68 | 0.88 | 1.00 | 0.002 | 0.42 | 2/201 / 8/201 | -1.08 / -0.13 | 0.44 | not computed | 0.38 | -0.54 | session table below (vol tercile not computed) | 6/12 | +0.13 / +0.33 |
| S2b | MV | `range|8|two|c2|mid|X8|W0|N` | +0.47 [-1.06, +2.14] | +0.64 / +0.47 / +0.71 / +0.29 / +1.62 | 40 | 0.74 | 0.65 | 1.00 | 0.009 | 0.42 | 42/201 / 41/201 | -1.19 / -0.23 | 0.64 | not computed | 0.39 | -0.56 | session table below (vol tercile not computed) | 8/12 | +0.57 / +0.33 |
| S2b | PE | `vol|2000|close_fav|c2|mid|X3|W0|N` | +0.91 [-0.96, +2.62] | +1.92 / +0.91 / +0.59 / +0.61 / +0.75 | 43 | 0.71 | 0.82 | 0.97 | 0.006 | 0.42 | 37/201 / 68/201 | +0.58 / -0.09 | 1.28 | not computed | 0.34 | -0.63 | session table below (vol tercile not computed) | 8/12 | +0.99 / +0.84 |
| S2b | WT | `dol|2G|two|d|near|X3|A70|N` | +0.75 [-0.36, +1.87] | +1.29 / +0.75 / +0.67 / +0.24 / +1.07 | 61 | 0.50 | 0.95 | 0.95 | 0.018 | 0.42 | 1/201 / 2/201 | -0.43 / -0.49 | 1.49 | not computed | 0.26 | -0.72 | session table below (vol tercile not computed) | 8/12 | +0.70 / +0.69 |
| S2c | DN | `lb|1m_n3|rev|c2|mid|X3|A70|N` | +0.01 [-1.14, +1.33] | +0.01 / +0.01 / +0.44 / +0.44 / +0.59 | 25 | 0.48 | 0.62 | 1.00 | 0.010 | 0.20 | 37/201 / 24/201 | -0.78 / -0.60 | 0.03 | not computed | 0.32 | -0.51 | session table below (vol tercile not computed) | 10/12 | +0.06 / +0.03 |
| S2c | HM | `lb|1m_n2|cont|d|near|X3|A70|N` | +0.21 [-1.27, +1.68] | +0.05 / +0.21 / +0.01 / +0.24 / -0.69 | 32 | 0.84 | 0.99 | 0.99 | 0.000 | 0.20 | 45/201 / 67/201 | -1.04 / -0.32 | 0.25 | not computed | 0.94 | -0.23 | session table below (vol tercile not computed) | 5/12 | +0.57 / +0.32 |
| S2c | KB | `linreg|1m|flip|b|mid|X3|A70|N` | +0.35 [-0.43, +1.18] | +0.70 / +0.35 / +0.26 / +0.01 / +0.22 | 45 | 0.61 | 0.68 | 0.93 | 0.000 | 0.20 | 47/201 / 49/201 | +0.21 / +0.03 | 0.57 | not computed | 0.32 | -0.34 | session table below (vol tercile not computed) | 6/12 | +0.31 / +0.23 |
| S2c | MV | `lb|5m_n2|cont|d|near|X3|W0|N` | +0.20 [-1.27, +1.58] | +0.57 / +0.20 / +0.24 / +0.53 / +0.92 | 40 | 0.75 | 0.52 | 0.99 | 0.005 | 0.20 | 142/201 / 174/201 | -0.26 / +0.18 | 0.26 | not computed | 0.40 | -0.46 | session table below (vol tercile not computed) | 7/12 | +0.16 / +0.21 |
| S2c | PE | `linreg|15m|flip|d|near|X3|A70|N` | +0.79 [-0.77, +2.26] | +1.43 / +0.79 / +0.69 / +0.38 / +0.76 | 43 | 0.75 | 0.79 | 0.97 | 0.006 | 0.20 | 4/201 / 2/201 | -0.36 / +0.09 | 1.07 | not computed | 0.47 | -0.49 | session table below (vol tercile not computed) | 7/12 | +0.74 / +0.66 |
| S2c | WT | `linreg|1m|flip|d|near|X3|W0|N` | +0.19 [-0.66, +1.05] | -0.04 / +0.19 / +0.28 / +0.12 / +0.51 | 61 | 0.87 | 0.94 | 0.99 | 0.005 | 0.20 | 92/201 / 96/201 | -0.12 / -0.40 | 0.23 | not computed | 0.67 | -0.46 | session table below (vol tercile not computed) | 9/12 | +0.16 / +0.24 |
| S3 | DN | `tc|15s|delta_fav|a|near|X3|A70|N` | +0.66 [+0.15, +1.17] | +0.72 / +0.66 / +0.68 / +0.70 / -0.04 | 25 | 0.97 | 0.42 | 0.42 | 0.307 | 0.21 | 47/201 / 48/201 | +0.20 / -0.16 | 0.68 | not computed | 0.63 | -0.05 | session table below (vol tercile not computed) | 10/12 | +0.74 / +0.59 |
| S3 | HM | `tc|1m|poc_mig|c1|near|X3|W0|N` | +0.28 [-2.10, +2.78] | -0.43 / +0.28 / +0.58 / +0.26 / +0.00 | 32 | 0.86 | 0.88 | 0.98 | 0.001 | 0.21 | 29/201 / 19/201 | -1.15 / -1.67 | 0.32 | not computed | 0.51 | -0.39 | session table below (vol tercile not computed) | 7/12 | -0.13 / +0.06 |
| S3 | KB | `tc|15s|delta_div_res|a|near|X3|W0|N` | +1.34 [-0.83, +3.50] | +2.48 / +1.34 / +1.21 / +0.77 / -0.78 | 45 | 0.86 | 0.58 | 0.86 | 0.004 | 0.21 | 22/201 / 20/201 | -0.67 / +0.42 | 1.55 | not computed | 0.37 | -0.51 | session table below (vol tercile not computed) | 9/12 | +1.55 / +1.24 |
| S3 | MV | `tc|15s|delta_strong|b|mid|X3|W0|N` | +0.29 [-1.27, +1.78] | -0.19 / +0.29 / +0.39 / +0.85 / +0.48 | 40 | 0.84 | 0.55 | 1.00 | 0.022 | 0.21 | 58/201 / 49/201 | -0.74 / +0.35 | 0.34 | not computed | 0.53 | -0.28 | session table below (vol tercile not computed) | 9/12 | +0.39 / +0.19 |
| S3 | PE | `tc|30s|delta_strong|b|far|X3|W0|N` | +0.83 [-0.84, +2.48] | +1.69 / +0.83 / +0.70 / +0.70 / +0.06 | 43 | 0.75 | 0.29 | 0.96 | 0.005 | 0.21 | 77/201 / 67/201 | +0.70 / -0.03 | 1.10 | not computed | 0.35 | -0.65 | session table below (vol tercile not computed) | 7/12 | +0.71 / +0.72 |
| S3 | WT | `tc|15s|delta_strong|c1|near|X5|W0|N` | +0.21 [-0.95, +1.42] | +0.52 / +0.21 / +0.48 / +0.12 / +0.85 | 61 | 0.77 | 0.91 | 1.00 | 0.006 | 0.21 | 114/201 / 90/201 | -0.32 / -0.06 | 0.27 | not computed | 0.47 | -0.60 | session table below (vol tercile not computed) | 5/12 | +0.35 / +0.31 |
| S4 | DN | `entropy|300|beyond_prior|a|near|X3|A70|N` | +0.48 [-0.62, +1.34] | -0.04 / +0.48 / +0.50 / +0.69 / +0.07 | 25 | 0.96 | 0.97 | 1.00 | 0.163 | 0.69 | 56/201 / 65/201 | +0.29 / -0.19 | 0.50 | not computed | 0.50 | -0.13 | session table below (vol tercile not computed) | 10/12 | +0.76 / +0.37 |
| S4 | KB | `entropy|1000|close_fav|a|near|X3|W0|N` | +0.95 [-0.84, +2.90] | +2.28 / +0.95 / +0.80 / +0.57 / +0.61 | 45 | 0.91 | 0.85 | 0.96 | 0.025 | 0.69 | 88/201 / 91/201 | -0.50 / -0.26 | 1.04 | not computed | 0.49 | -0.47 | session table below (vol tercile not computed) | 9/12 | +1.13 / +0.78 |
| S4 | WT | `hybridrenko|8|n2|b|mid|X3|W0|N` | +0.62 [-0.35, +1.51] | +0.45 / +0.62 / +0.76 / -0.03 / +1.13 | 61 | 0.82 | 0.92 | 0.92 | 0.055 | 0.69 | 2/201 / 5/201 | +0.27 / -0.12 | 0.76 | not computed | 0.59 | -0.55 | session table below (vol tercile not computed) | 8/12 | +0.63 / +0.47 |

Plain sentences (the best candidate per book per stage):
* PE: waiting for a tc 45s (three_bar) on the PE signal and entering at market when the confirmation prints, pure-wait base adds +2.58 pts per contract in L6M (MDE 3.3, fill 74%, L3M +4.32, HOLD +2.28, PRE +1.02, X' -0.05); placebo rank 2 of 201, Romano-Wolf p 0.68; tier after QUANT: LEAD (placebo-beaten, not significant after multiplicity).
* KB: waiting for a tc 15s (delta_div_res) on the KB signal and entering at market when the confirmation prints, pure-wait base adds +1.34 pts per contract in L6M (MDE 3.1, fill 86%, L3M +2.48, HOLD +1.21, PRE +0.77, X' -0.78); placebo rank 22 of 201, Romano-Wolf p 0.86; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* KB: waiting for a ha 30s (colour flip) on the KB signal and entering at market when the confirmation prints, pure-wait base adds +1.27 pts per contract in L6M (MDE 4.3, fill 89%, L3M +3.07, HOLD +0.91, PRE +0.39, X' +0.76); placebo rank 18 of 201, Romano-Wolf p 0.97; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* PE: waiting for a ha 15m (colour flip) on the PE signal and taking the signal only if the state is already in favour, 70/30 base adds +1.11 pts per contract in L6M (MDE 2.1, fill 70%, L3M +1.93, HOLD +0.86, PRE +0.55, X' +0.40); placebo rank 7 of 201, Romano-Wolf p 0.84; tier after QUANT: LEAD (placebo-beaten, not significant after multiplicity).
* KB: waiting for a entropy 1000 (bar close in favour) on the KB signal and entering at market when the confirmation prints, pure-wait base adds +0.95 pts per contract in L6M (MDE 2.7, fill 91%, L3M +2.28, HOLD +0.80, PRE +0.57, X' +0.61); placebo rank 88 of 201, Romano-Wolf p 0.96; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* PE: waiting for a vol 2000 (bar close in favour) on the PE signal and resting a limit at the bar open once a 3-pt dip has started, pure-wait base adds +0.91 pts per contract in L6M (MDE 2.6, fill 71%, L3M +1.92, HOLD +0.59, PRE +0.61, X' +0.75); placebo rank 37 of 201, Romano-Wolf p 0.97; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* KB: waiting for a ha 1m (colour flip) on the KB signal and resting a limit at the bar open once a 3-pt dip has started, 70/30 base adds +0.87 pts per contract in L6M (MDE 1.5, fill 62%, L3M +1.64, HOLD +0.78, PRE +0.15, X' +0.38); placebo rank 1 of 201, Romano-Wolf p 0.72; tier after QUANT: LEAD (placebo-beaten, not significant after multiplicity).
* PE: waiting for a tc 30s (delta_strong) on the PE signal and resting a limit at the confirming bar's against-extreme, pure-wait base adds +0.83 pts per contract in L6M (MDE 2.4, fill 75%, L3M +1.69, HOLD +0.70, PRE +0.70, X' +0.06); placebo rank 77 of 201, Romano-Wolf p 0.96; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* DN: waiting for a ha 3m (three in a row) on the DN signal and resting a limit at the confirming bar's open/base, 70/30 base adds +0.82 pts per contract in L6M (MDE 1.8, fill 51%, L3M +0.51, HOLD +1.05, PRE +0.38, X' +0.32); placebo rank 4 of 201, Romano-Wolf p 0.80; tier after QUANT: LEAD (placebo-beaten, not significant after multiplicity).
* PE: waiting for a linreg 15m (colour flip) on the PE signal and taking the signal only if the state is already in favour, 70/30 base adds +0.79 pts per contract in L6M (MDE 2.2, fill 75%, L3M +1.43, HOLD +0.69, PRE +0.38, X' +0.76); placebo rank 4 of 201, Romano-Wolf p 0.97; tier after QUANT: LEAD (placebo-beaten, not significant after multiplicity).
* HM: waiting for a ha 1m (first strong body) on the HM signal and taking the signal only if the state is already in favour, 70/30 base adds +0.77 pts per contract in L6M (MDE 2.3, fill 76%, L3M +2.22, HOLD +0.71, PRE +0.23, X' -0.06); placebo rank 10 of 201, Romano-Wolf p 0.86; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* WT: waiting for a dol 2G (two in a row) on the WT signal and taking the signal only if the state is already in favour, 70/30 base adds +0.75 pts per contract in L6M (MDE 1.6, fill 50%, L3M +1.29, HOLD +0.67, PRE +0.24, X' +1.07); placebo rank 1 of 201, Romano-Wolf p 0.95; tier after QUANT: LEAD (placebo-beaten, not significant after multiplicity).
* PE: waiting for a renko 6 (third brick in favour) on the PE signal and resting a limit at the confirming bar's against-extreme, pure-wait base adds +0.74 pts per contract in L6M (MDE 2.3, fill 87%, L3M +1.74, HOLD +0.55, PRE +0.82, X' +0.50); placebo rank 42 of 201, Romano-Wolf p 0.98; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* MV: waiting for a ha 2m (first strong body) on the MV signal and taking the signal only if the state is already in favour, pure-wait base adds +0.72 pts per contract in L6M (MDE 2.4, fill 68%, L3M +0.83, HOLD +0.88, PRE +0.21, X' +2.02); placebo rank 58 of 201, Romano-Wolf p 0.98; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* DN: waiting for a tc 15s (delta_fav) on the DN signal and entering at market when the confirmation prints, 70/30 base adds +0.66 pts per contract in L6M (MDE 0.7, fill 97%, L3M +0.72, HOLD +0.68, PRE +0.70, X' -0.04); placebo rank 47 of 201, Romano-Wolf p 0.42; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* HM: waiting for a dol 4G (bar close in favour) on the HM signal and taking the signal only if the state is already in favour, 70/30 base adds +0.64 pts per contract in L6M (MDE 2.5, fill 64%, L3M +0.72, HOLD +0.61, PRE +0.04, X' +0.36); placebo rank 8 of 201, Romano-Wolf p 0.95; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* WT: waiting for a hybridrenko 8 (second brick in favour) on the WT signal and resting a limit at the confirming bar's open/base, pure-wait base adds +0.62 pts per contract in L6M (MDE 1.3, fill 82%, L3M +0.45, HOLD +0.76, PRE -0.03, X' +1.13); placebo rank 2 of 201, Romano-Wolf p 0.92; tier after QUANT: LEAD (placebo-beaten, not significant after multiplicity).
* DN: waiting for a entropy 300 (close beyond the prior bar's extreme) on the DN signal and entering at market when the confirmation prints, 70/30 base adds +0.48 pts per contract in L6M (MDE 1.4, fill 96%, L3M -0.04, HOLD +0.50, PRE +0.69, X' +0.07); placebo rank 56 of 201, Romano-Wolf p 1.00; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* MV: waiting for a range 8 (two in a row) on the MV signal and resting a limit at the bar open once a 8-pt dip has started, pure-wait base adds +0.47 pts per contract in L6M (MDE 2.2, fill 74%, L3M +0.64, HOLD +0.71, PRE +0.29, X' +1.62); placebo rank 42 of 201, Romano-Wolf p 1.00; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* KB: waiting for a kagi 32 (reversal brick/line) on the KB signal and taking the signal only if the state is already in favour, pure-wait base adds +0.44 pts per contract in L6M (MDE 3.8, fill 67%, L3M +1.50, HOLD +0.56, PRE +0.15, X' +1.67); placebo rank 10 of 201, Romano-Wolf p 1.00; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* WT: waiting for a ha 15m (two in a row) on the WT signal and taking the signal only if the state is already in favour, pure-wait base adds +0.39 pts per contract in L6M (MDE 1.5, fill 73%, L3M +0.46, HOLD +0.35, PRE -0.11, X' +0.86); placebo rank 2 of 201, Romano-Wolf p 0.95; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* WT: waiting for a renko 4 (third brick in favour) on the WT signal and resting a limit at the confirming bar's open/base, pure-wait base adds +0.37 pts per contract in L6M (MDE 1.3, fill 80%, L3M +0.54, HOLD +0.83, PRE +0.01, X' +1.10); placebo rank 13 of 201, Romano-Wolf p 0.98; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* DN: waiting for a dol 100M (close beyond the prior bar's extreme) on the DN signal and entering at market when the confirmation prints, 70/30 base adds +0.35 pts per contract in L6M (MDE 0.8, fill 97%, L3M +0.32, HOLD +0.41, PRE +0.74, X' -0.05); placebo rank 120 of 201, Romano-Wolf p 0.96; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* KB: waiting for a linreg 1m (colour flip) on the KB signal and resting a limit at the confirming bar's open/base, 70/30 base adds +0.35 pts per contract in L6M (MDE 1.1, fill 61%, L3M +0.70, HOLD +0.26, PRE +0.01, X' +0.22); placebo rank 47 of 201, Romano-Wolf p 0.93; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* ST: waiting for a ha 10m (three in a row) on the ST signal and taking the signal only if the state is already in favour, 70/30 base adds +0.32 pts per contract in L6M (MDE 1.9, fill 70%, L3M +1.87, HOLD +0.35, PRE +0.20, X' +1.13); placebo rank 1 of 201, Romano-Wolf p 0.99; tier after QUANT: LEAD (placebo-beaten, not significant after multiplicity).
* KB: waiting for a range 8 (bar close in favour) on the KB signal and taking the signal only if the state is already in favour, 70/30 base adds +0.30 pts per contract in L6M (MDE 3.4, fill 68%, L3M +0.81, HOLD +0.16, PRE +0.47, X' +0.81); placebo rank 2 of 201, Romano-Wolf p 1.00; tier after QUANT: LEAD (placebo-beaten, not significant after multiplicity).
* MV: waiting for a tc 15s (delta_strong) on the MV signal and resting a limit at the confirming bar's open/base, pure-wait base adds +0.29 pts per contract in L6M (MDE 2.3, fill 84%, L3M -0.19, HOLD +0.39, PRE +0.85, X' +0.48); placebo rank 58 of 201, Romano-Wolf p 1.00; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* HM: waiting for a tc 1m (poc_mig) on the HM signal and entering at market once the dip of 3 pts and the confirmation both hold, pure-wait base adds +0.28 pts per contract in L6M (MDE 3.4, fill 86%, L3M -0.43, HOLD +0.58, PRE +0.26, X' +0.00); placebo rank 29 of 201, Romano-Wolf p 0.98; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* HM: waiting for a renko 8 (reversal brick/line) on the HM signal and resting a limit at the confirming bar's against-extreme, 70/30 base adds +0.22 pts per contract in L6M (MDE 1.9, fill 82%, L3M +0.55, HOLD +0.10, PRE +0.28, X' -0.34); placebo rank 3 of 201, Romano-Wolf p 0.99; tier after QUANT: LEAD (placebo-beaten, not significant after multiplicity).
* DN: waiting for a renkomed m1 (second brick in favour) on the DN signal and taking the signal only if the state is already in favour, 70/30 base adds +0.22 pts per contract in L6M (MDE 1.6, fill 85%, L3M +1.37, HOLD +0.13, PRE +0.94, X' +0.10); placebo rank 30 of 201, Romano-Wolf p 1.00; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* HM: waiting for a lb 1m_n2 (continuation brick/line) on the HM signal and taking the signal only if the state is already in favour, 70/30 base adds +0.21 pts per contract in L6M (MDE 2.1, fill 84%, L3M +0.05, HOLD +0.01, PRE +0.24, X' -0.69); placebo rank 45 of 201, Romano-Wolf p 0.99; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* WT: waiting for a tc 15s (delta_strong) on the WT signal and entering at market once the dip of 5 pts and the confirmation both hold, pure-wait base adds +0.21 pts per contract in L6M (MDE 1.6, fill 77%, L3M +0.52, HOLD +0.48, PRE +0.12, X' +0.85); placebo rank 114 of 201, Romano-Wolf p 1.00; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* MV: waiting for a ha 3m (first strong body) on the MV signal and taking the signal only if the state is already in favour, pure-wait base adds +0.20 pts per contract in L6M (MDE 1.9, fill 69%, L3M +0.87, HOLD +0.42, PRE +0.31, X' +1.80); placebo rank 74 of 201, Romano-Wolf p 1.00; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* MV: waiting for a lb 5m_n2 (continuation brick/line) on the MV signal and taking the signal only if the state is already in favour, pure-wait base adds +0.20 pts per contract in L6M (MDE 2.0, fill 75%, L3M +0.57, HOLD +0.24, PRE +0.53, X' +0.92); placebo rank 142 of 201, Romano-Wolf p 0.99; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* WT: waiting for a linreg 1m (colour flip) on the WT signal and taking the signal only if the state is already in favour, pure-wait base adds +0.19 pts per contract in L6M (MDE 1.2, fill 87%, L3M -0.04, HOLD +0.28, PRE +0.12, X' +0.51); placebo rank 92 of 201, Romano-Wolf p 0.99; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* WT: waiting for a tc 15s (engulf) on the WT signal and resting a limit at the confirming bar's open/base, pure-wait base adds +0.18 pts per contract in L6M (MDE 1.8, fill 63%, L3M -0.45, HOLD +0.38, PRE +0.13, X' +0.69); placebo rank 5 of 201, Romano-Wolf p 0.99; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).
* DN: waiting for a lb 1m_n3 (reversal brick/line) on the DN signal and resting a limit at the bar open once a 3-pt dip has started, 70/30 base adds +0.01 pts per contract in L6M (MDE 1.8, fill 48%, L3M +0.01, HOLD +0.44, PRE +0.44, X' +0.59); placebo rank 37 of 201, Romano-Wolf p 1.00; tier after QUANT: CANDIDATE-RECENT (not placebo-beaten at 200 draws).

## Which bar types and mechanics help in the selection windows (PRE u X', all books, ALL sessions, N basis, delta vs the 70/30 floor per planned lot; no recent data used)
| mechanic | base | mean delta vs floor | fill | floor P&L on kept signals | floor P&L on skipped signals |
|---|---|---|---|---|---|
| a | A70 | -0.16 | 79% | +4.02 | -13.47 |
| a | W0 | -0.41 | 79% | +4.02 | -13.47 |
| b | A70 | -0.12 | 64% | -4.60 | +24.67 |
| b | W0 | -0.54 | 64% | -4.60 | +24.67 |
| c1 | A70 | -0.14 | 68% | -0.45 | +16.59 |
| c1 | W0 | -0.56 | 68% | -0.45 | +16.59 |
| c2 | A70 | -0.17 | 58% | -8.11 | +27.19 |
| c2 | W0 | -0.71 | 58% | -8.11 | +27.19 |
| d | A70 | -0.31 | 61% | +1.43 | +0.89 |
| d | W0 | -0.47 | 61% | +1.43 | +0.89 |

Reading: on the pure-wait base (W0) the average cell is positive only because the signals it never enters (the original stop or an opposite signal arrives before the confirmation) have a negative floor P&L; that is a skip/filter effect of the hold-dies-at-the-stop rule, not a better entry price. On the 70/30 base the confirmation only moves the 30% add, so the achievable gain is bounded by that slice.

Mean delta by bar-type family (PRE u X', all cells):

| family | cells | mean delta |
|---|---|---|
| trb | 88 | -0.19 |
| vrb | 88 | -0.20 |
| kagi | 88 | -0.22 |
| hybridrenko | 264 | -0.22 |
| gridrenko | 264 | -0.23 |
| renko | 594 | -0.24 |
| tib | 88 | -0.24 |
| unirenko | 594 | -0.24 |
| momnet | 132 | -0.24 |
| pnf | 176 | -0.25 |
| rvbars | 176 | -0.25 |
| entropy | 198 | -0.26 |
| rangeph | 198 | -0.28 |
| mixed | 198 | -0.28 |
| vib | 88 | -0.29 |
| drb | 88 | -0.30 |
| zigzag | 66 | -0.34 |
| tick | 528 | -0.35 |
| tc | 1122 | -0.35 |
| range | 462 | -0.36 |
| renkomed | 88 | -0.36 |
| dol | 396 | -0.36 |
| vol | 396 | -0.37 |
| linreg | 88 | -0.39 |
| l2ev | 44 | -0.40 |
| sessfrac | 88 | -0.41 |
| deltapro | 88 | -0.42 |
| hax | 396 | -0.42 |
| dib | 88 | -0.43 |
| ha | 1210 | -0.47 |
| hull | 88 | -0.48 |
| lb | 396 | -0.49 |
| momcol | 88 | -0.53 |
| kaseproxy | 88 | -0.55 |
| delta | 264 | -0.57 |
| renkoatr | 176 | -0.64 |
| absb | 44 | -0.76 |
| vwapc | 44 | -0.81 |

## Session cells (ALL books pooled by book x session; best selected cell with n >= 150, recent look, N basis)
Cells positive in L6M, HOLD, PRE and X' (selected for that book x session, n >= 150 L6M trades); a session cell is registered, never killed by a pooled number, but none is beyond its MDE (see MDE in the parquet rec_*.parquet):

| book | session | cell | stage | L3M | L6M | HOLD | PRE | X' | n L6M |
|---|---|---|---|---|---|---|---|---|---|
| PE | nypm | `pnf|b16_r2|rev|d|near|X3|A70|N` | S2 | +10.91 | +7.01 | +6.76 | +1.13 | +4.29 | 230 |
| HM | nypm | `deltapro|500|imb_sign|c2|mid|X8|W0|N` | S4 | +8.54 | +5.99 | +5.95 | +1.43 | +2.59 | 178 |
| PE | nyam | `tc|45s|three_bar|b|near|X3|W0|N` | S1 | +4.48 | +5.33 | +4.57 | +0.79 | +0.56 | 352 |
| MV | nypm | `ha|10m|dojiflip|d|near|X3|W0|N` | S1 | +10.43 | +5.14 | +3.92 | +1.59 | +1.28 | 202 |
| MV | london | `tc|45s|three_bar|a|near|X3|W0|N` | S1 | +4.75 | +4.92 | +4.32 | +0.89 | +1.24 | 229 |
| KB | nyam | `tick|2000|two|a|near|X3|W0|N` | S2b | +8.93 | +4.92 | +4.54 | +0.60 | +2.04 | 391 |
| WT | nypm | `unirenko|16|n2|c2|mid|X3|W0|N` | S2 | +6.17 | +4.39 | +4.94 | +0.85 | +1.14 | 298 |
| PB | nypm | `dol|800M|two|b|near|X3|W0|N` | S2b | +4.57 | +4.19 | +3.27 | +1.46 | +0.47 | 163 |
| DN | nyam | `linreg|3m|flip|b|near|X3|A70|N` | S2c | +1.92 | +4.15 | +3.38 | +0.11 | +0.54 | 229 |
| KB | nypm | `hax|tick_233|two|b|mid|X3|W0|N` | S4 | +4.95 | +3.91 | +3.62 | +0.50 | +2.73 | 235 |
| ST | asia | `tc|30s|stacked|b|mid|X3|W0|N` | S3 | +5.14 | +3.53 | +4.92 | +0.66 | +2.37 | 311 |
| ST | nypm | `tc|30s|three_bar|a|near|X3|W0|N` | S1 | +4.74 | +3.53 | +3.52 | +1.09 | +0.12 | 220 |
| KB | asia | `tc|1m|delta_fav|b|mid|X3|W0|N` | S3 | +4.88 | +2.87 | +2.82 | +0.38 | +0.70 | 335 |
| MV | asia | `hax|vol_2000|strong|d|near|X3|A70|N` | S4 | +2.82 | +2.73 | +4.07 | +0.02 | +1.70 | 305 |
| PE | london | `vol|5000|beyond_prior|d|near|X3|A70|N` | S2b | +1.19 | +2.68 | +1.95 | +1.38 | +4.43 | 221 |
| WT | london | `dol|4G|beyond_prior|a|near|X3|W0|N` | S2b | +3.14 | +2.68 | +2.84 | +0.29 | +0.36 | 402 |
| HM | london | `vol|5000|close_fav|d|near|X3|A70|N` | S2b | +1.60 | +2.39 | +3.04 | +0.32 | +1.49 | 209 |
| PE | asia | `ha|1m|flip|d|near|X3|A70|N` | S1c | +3.55 | +2.38 | +2.33 | +1.09 | +0.98 | 327 |
| PB | nyam | `unirenko|10|n2|b|near|X3|W0|N` | S2 | +1.69 | +2.07 | +3.25 | +0.01 | +0.38 | 221 |
| ST | nyam | `vol|2000|close_fav|a|near|X3|W0|N` | S2b | +2.87 | +1.89 | +1.49 | +0.07 | +1.42 | 423 |
| MV | nyam | `tc|15s|delta_div_res|b|far|X3|W0|N` | S3 | +2.17 | +1.88 | +2.46 | +0.38 | +2.77 | 330 |
| DN | london | `gridrenko|4|rev|d|near|X3|A70|N` | S4 | +0.26 | +1.67 | +2.25 | +0.52 | +0.71 | 150 |
| KB | london | `dol|4G|close_fav|a|near|X3|W0|N` | S2b | +3.83 | +1.39 | +1.74 | +1.15 | +4.58 | 234 |
| PB | london | `hax|vol_2000|two|d|near|X3|W0|N` | S4 | +4.94 | +1.11 | +0.91 | +1.93 | +1.08 | 191 |
| HM | nyam | `renkomed|m1|n3|d|near|X3|A70|N` | S2 | +3.27 | +1.11 | +1.33 | +0.09 | +0.52 | 223 |

## Defects, limits, what was not done
* Store defect (found with RC-1): ha 1m/3m/5m/15m, LinReg/Hull/momentum/Kase-proxy and line-break sets were built from time candles appended 2-3x; fixed, rebuilt, and re-scored as S1c/S2c with a new prereg; the old scores are void and excluded from every table here.
* Not scored (too dense, did not finish): renko|2|n3 and unirenko|2|rev (about 15 million events each).
* Run-bar naming: trb/vrb/drb span-50 series are stored as size s30 (prereg listed s50; same bars).
* Tape vs library volume differs by 1-4% on 22 of 726 days (flag vol_ok=False in _meta_*.parquet); on those days prints are placed by tape second.
* Open of a time bar = first print (cf_engine uses the previous close when contiguous); H/L/C/ek identical to cf_engine.build_bars.
* Imbalance/run bars use a diffusive-buffer stabiliser (pure LdP thresholds collapse); definitions in l2vast/ds3/code/bars/SPECS.md. "Kase" bars are a proxy (ATR-normalised momentum), not the proprietary indicator.
* The "beyond the signal bar's extreme" rule is approximated by "closes beyond the prior bar's extreme" (first such bar after the signal).
* L3M = 2025-11-06..2026-02-06 is reported beside L6M/HOLD and never used for selection; RECENT_WINS rows (L3M positive vs floor, any tier) are in l2vast/ds3/out/recent_wins/BAR-STORE.csv with the multiplicity "selected k of N program cells".
* Section 4 of the BARS directive (the live engines re-derived on every bar type) is BAR-ENG's; this report is the confirmation use only. Bar store location and format: l2vast/ds3/code/bars/README.md; streams for CF-COMBO: rankings out/confirm/rankings/bars_<stage>_<book>.parquet (PRE+X' only) and events via bars_events.events_for -> cf_engine.Events / save_stream.
