# DS3_BRACKET_DD_D - T-BRACKET-DD Parts D (partial exits), C (target by room), E (time) on TL3_EV_JN05W2JL2 (W-BD2)
> VALIDATION (W-DV, FIRST PASS, 2026-11-16): trials counted BD parts C 5 + D 8 + E 10 + F 22 engine cells, N_used from replay (TRIALS_LEDGER.csv TB-BDC..F); correction not applied (cells have 1-12 months, too short for RC / SPA on a common window); PBO not fitted; number shown is IN-SAMPLE; data end 2026-10-31.
**VERDICT (data ends 2026-10-31; FIRST PASS, rebuilt 16:04Z UTC): NO candidate qualifies yet (see per-candidate rows; some are not finished). Not finished candidates are listed as such; no row is called a lead without its 6 controls. Dollars BASE lots; live = x1.75; $4.84 = FEES.md RT repriced (net - lots x 3.66).**

Status per candidate (windows with real + 6 controls all finished): C M7 london lvl k1.0: none; C H7 asia har k1.0: none; C K7 nypm lvl k0.8: none; C M7 london har k0.5: none; D K7 nyam X15 T58 BE1 (Step1 b): none; D K7 nyam X40 T85 BE1: none; D M7 london X20 TR15: none; D K7 london X40 T85 BE1: none; D M7 nyam X40 T85 BE0: none; D K7 london X40 T58 BE0: none; D U7 london X40 T85 BE0: none; E U7 asia tstop60<5: none; E U7 asia tstop30<5: none; E U7 london tstop30<5: none; E U7 london tstop60<5: none; E M7 london steps60: none; E K7 london tstop30<5: none

Definitions. Reference = TL3_EV_JN05W2JL2 (final, 43 months), live layers unchanged. Windows: HOLD 2025-11-01..2026-04-30; HP = HOLD path 2025-11-17..2025-12-10; L6M 2026-05..10; L3M 2026-08..10; GAP 2026-02-07..04-30; PRE 2024-10..2025-06; X' 2023-04..2024-01 (same definitions as DS3_BRACKET_BUILD). DD = whole-stack max drawdown of cumulative daily $ (Globex day of exit). Placebo (3 seeds) = the same rule applied to a pseudo-random subset of ALL signals (every book x session) with the same expected count as the cell (share of all signals). Matched random control (3 seeds) = the same rule on a pseudo-random 50% of the cell's own book x session signals (same book x session x month mix, half the count: read against half the real effect). Pass (addendum): DD cut > 0 vs reference, beats ALL 6 controls on DD cut, d mean not below -5% of the reference mean, in HOLD and L6M; neighbours must agree (surface). Lots at live values: the rules change no lots (stop unchanged; the breakeven stop only follows the partial), so the constant-risk column (lots x baseStop/newStop) equals the live-lots column.

## Window HOLD (20251101..20260430)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | n/a | not finished |
| C H7 asia har k1.0 | not finished | n/a | not finished |
| C K7 nypm lvl k0.8 | not finished | n/a | not finished |
| C M7 london har k0.5 | not finished | n/a | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | n/a | not finished |
| D K7 nyam X40 T85 BE1 | not finished | n/a | not finished |
| D M7 london X20 TR15 | not finished | n/a | not finished |
| D K7 london X40 T85 BE1 | not finished | n/a | not finished |
| D M7 nyam X40 T85 BE0 | not finished | n/a | not finished |
| D K7 london X40 T58 BE0 | not finished | n/a | not finished |
| D U7 london X40 T85 BE0 | not finished | n/a | not finished |
| E U7 asia tstop60<5 | DD -67360 (ref -74402; +9.5%), worst wk -35178 (ref -31211), d mean -536/wk (live x1.75 -938; $4.84 -538; -6.4% of ref), n 3217 (3219) | n/a | not finished (controls 3/6 done) |
| E U7 asia tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop60<5 | not finished | n/a | not finished |
| E M7 london steps60 | not finished | n/a | not finished |
| E K7 london tstop30<5 | not finished | n/a | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | -0.3% / -145 | +14.3% / -306 | +3.4% / +290 | n/f | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window HP (20251117..20251210)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | n/a | not finished |
| C H7 asia har k1.0 | not finished | n/a | not finished |
| C K7 nypm lvl k0.8 | not finished | n/a | not finished |
| C M7 london har k0.5 | not finished | n/a | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | n/a | not finished |
| D K7 nyam X40 T85 BE1 | not finished | n/a | not finished |
| D M7 london X20 TR15 | not finished | n/a | not finished |
| D K7 london X40 T85 BE1 | not finished | n/a | not finished |
| D M7 nyam X40 T85 BE0 | not finished | n/a | not finished |
| D K7 london X40 T58 BE0 | not finished | n/a | not finished |
| D U7 london X40 T85 BE0 | not finished | n/a | not finished |
| E U7 asia tstop60<5 | DD -67360 (ref -74402; +9.5%), worst wk -34178 (ref -31211), d mean +2054/wk (live x1.75 +3594; $4.84 +2051; +12.1% of ref), n 408 (407) | n/a | not finished (controls 4/6 done) |
| E U7 asia tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop60<5 | not finished | n/a | not finished |
| E M7 london steps60 | not finished | n/a | not finished |
| E K7 london tstop30<5 | not finished | n/a | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | -0.3% / -73 | +14.3% / +3099 | +3.4% / +735 | +6.7% / +1448 | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window L6M (20260501..20261031)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | not finished | not finished |
| C H7 asia har k1.0 | not finished | not finished | not finished |
| C K7 nypm lvl k0.8 | not finished | not finished | not finished |
| C M7 london har k0.5 | not finished | not finished | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | not finished | not finished |
| D K7 nyam X40 T85 BE1 | not finished | not finished | not finished |
| D M7 london X20 TR15 | not finished | not finished | not finished |
| D K7 london X40 T85 BE1 | not finished | not finished | not finished |
| D M7 nyam X40 T85 BE0 | not finished | not finished | not finished |
| D K7 london X40 T58 BE0 | not finished | not finished | not finished |
| D U7 london X40 T85 BE0 | not finished | not finished | not finished |
| E U7 asia tstop60<5 | not finished | not finished | not finished |
| E U7 asia tstop30<5 | not finished | not finished | not finished |
| E U7 london tstop30<5 | not finished | not finished | not finished |
| E U7 london tstop60<5 | not finished | not finished | not finished |
| E M7 london steps60 | not finished | not finished | not finished |
| E K7 london tstop30<5 | not finished | not finished | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window L3M (20260801..20261031)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | not finished | not finished |
| C H7 asia har k1.0 | not finished | not finished | not finished |
| C K7 nypm lvl k0.8 | not finished | not finished | not finished |
| C M7 london har k0.5 | not finished | not finished | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | not finished | not finished |
| D K7 nyam X40 T85 BE1 | not finished | not finished | not finished |
| D M7 london X20 TR15 | not finished | not finished | not finished |
| D K7 london X40 T85 BE1 | not finished | not finished | not finished |
| D M7 nyam X40 T85 BE0 | not finished | not finished | not finished |
| D K7 london X40 T58 BE0 | not finished | not finished | not finished |
| D U7 london X40 T85 BE0 | not finished | not finished | not finished |
| E U7 asia tstop60<5 | not finished | not finished | not finished |
| E U7 asia tstop30<5 | not finished | not finished | not finished |
| E U7 london tstop30<5 | not finished | not finished | not finished |
| E U7 london tstop60<5 | not finished | not finished | not finished |
| E M7 london steps60 | not finished | not finished | not finished |
| E K7 london tstop30<5 | not finished | not finished | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window GAP (20260207..20260430)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | n/a | not finished |
| C H7 asia har k1.0 | not finished | n/a | not finished |
| C K7 nypm lvl k0.8 | not finished | n/a | not finished |
| C M7 london har k0.5 | not finished | n/a | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | n/a | not finished |
| D K7 nyam X40 T85 BE1 | not finished | n/a | not finished |
| D M7 london X20 TR15 | not finished | n/a | not finished |
| D K7 london X40 T85 BE1 | not finished | n/a | not finished |
| D M7 nyam X40 T85 BE0 | not finished | n/a | not finished |
| D K7 london X40 T58 BE0 | not finished | n/a | not finished |
| D U7 london X40 T85 BE0 | not finished | n/a | not finished |
| E U7 asia tstop60<5 | DD -66335 (ref -54615; -21.5%), worst wk -35178 (ref -30852), d mean -2312/wk (live x1.75 -4046; $4.84 -2310; -23.6% of ref), n 1603 (1613) | n/a | not finished (controls 3/6 done) |
| E U7 asia tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop60<5 | not finished | n/a | not finished |
| E M7 london steps60 | not finished | n/a | not finished |
| E K7 london tstop30<5 | not finished | n/a | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | -7.3% / -201 | -5.7% / -1337 | +0.0% / +571 | n/f | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window PRE (20241001..20250630)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | n/a | not finished |
| C H7 asia har k1.0 | not finished | n/a | not finished |
| C K7 nypm lvl k0.8 | not finished | n/a | not finished |
| C M7 london har k0.5 | not finished | n/a | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | n/a | not finished |
| D K7 nyam X40 T85 BE1 | not finished | n/a | not finished |
| D M7 london X20 TR15 | not finished | n/a | not finished |
| D K7 london X40 T85 BE1 | not finished | n/a | not finished |
| D M7 nyam X40 T85 BE0 | not finished | n/a | not finished |
| D K7 london X40 T58 BE0 | not finished | n/a | not finished |
| D U7 london X40 T85 BE0 | not finished | n/a | not finished |
| E U7 asia tstop60<5 | not finished | n/a | not finished |
| E U7 asia tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop60<5 | not finished | n/a | not finished |
| E M7 london steps60 | not finished | n/a | not finished |
| E K7 london tstop30<5 | not finished | n/a | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window X' (20230401..20240131)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | n/a | not finished |
| C H7 asia har k1.0 | not finished | n/a | not finished |
| C K7 nypm lvl k0.8 | not finished | n/a | not finished |
| C M7 london har k0.5 | not finished | n/a | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | n/a | not finished |
| D K7 nyam X40 T85 BE1 | not finished | n/a | not finished |
| D M7 london X20 TR15 | not finished | n/a | not finished |
| D K7 london X40 T85 BE1 | not finished | n/a | not finished |
| D M7 nyam X40 T85 BE0 | not finished | n/a | not finished |
| D K7 london X40 T58 BE0 | not finished | n/a | not finished |
| D U7 london X40 T85 BE0 | not finished | n/a | not finished |
| E U7 asia tstop60<5 | not finished | n/a | not finished |
| E U7 asia tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop60<5 | not finished | n/a | not finished |
| E M7 london steps60 | not finished | n/a | not finished |
| E K7 london tstop30<5 | not finished | n/a | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

