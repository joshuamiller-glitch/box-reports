# REPORT N1-RT_ZB_ZT-30m-MR PAPER-ALL flag (ORDER 10-19 item 3), 2026-10-19

## Verdict
**GENUINE price event, no data bug, no engine bug. The z of +8.15 is a statistics/freeze artifact.** Two real defects were found and fixed in the PAPER-ALL layer (not in the N1 engine or the family matrix): (1) the "frozen" OOS interval, weekly SD and common-size factor g included the live week W42 itself (stored OOS series run to 20261016, FIRST_LIVE is 20261012); (2) the row's OOS series is flat in 92% of weeks (11 of 141), so its weekly SD / g are set by a handful of active weeks and the Gaussian z and the N-row z lines do not apply. After the fix the W42 figure is not smaller, it is larger ($138,296, z 11.0 against a clean frozen SD), because the week's P&L is real and the corrected SD is smaller. Nothing is promoted (1 scored week; needs 6+ and the multiplicity line). The family is NOT a gate a-d passer before or after (gate b null rank 0.86, gate d no OOS P&L in H1).

## What happened in W42 (per day and leg)
Cell #077 = DOL (equal-dollar) hedge, W=12, z-entry 3.0, exit z crosses 0, max hold 36 bars; it is the only cell with tilt weight (1.0) at the 2026-07-31 refit.
- 10-12, 10-13, 10-15, 10-16: flat, $0. 10-14: one trade, +$5,303 per $1M-per-leg book (engine) / +$5,307 (independent script).
- 10-14 08:30 ET bar: ZB 104.09 -> 102.69 (-1.35% in 30 min, 10,057 contracts in the first minute vs ~500 before), ZT 101.88 -> 101.56. Spread z = -3.23 at the 09:00 close, so the cell went long ZB / short ZT at 09:00 (ZB 102.75, ZT 101.55), flat at the 11:30 close (ZB 103.47, ZT 101.71).
- Leg split at $1M per leg (9.7 ZB, 4.9 ZT): ZB +$6,995, ZT -$1,613, costs about -$80. The ZB leg is 130% of the P&L. "Dollar balanced" ZB/ZT is a ~5:1 duration bet on ZB, not a market-neutral spread (ZB daily vol is about 5x ZT), so the PREREG statement of near-zero net exposure is wrong for DOL cells; the drift-matched null is what protects the test.
- It is a mean-reversion bounce after a violent 08:30 ET data-release sell-off in the long bond (volume and gradual prints, not a bad tick). The 3-sigma entry fired on a real 2-to-3 sigma day: the cell's unit daily SD is $739, so +$5,303 is a 7.2-sigma day for that cell, but a single trade out of a sparse book.

## (a) data and code checks, all clean
- Raw 1-minute ZB/ZT prints 08:20..09:10 ET on 10-14 inspected: continuous, high volume, same instrument id (42009118 / 42413280) all week. No roll in October (Dec contracts; Sep->Dec roll was end-Aug), no iid change in W42. ZB multiplier 1000/tick 1/32, ZT 2000/tick 1/256: correct in SPEC.
- No look-ahead: position at bar t is decided from the z at the close of bar t and earns bar t+1's return (_daily uses prev). 30m bins are labelled by bin start in ET (DST handled by tz_convert); session label = ET+6h.
- Independent re-derivation: autopilot/n1rt_flag/indep_check.py rebuilds cell #077 from the raw 1-minute files (own bar builder, own z, own exit rule, dollar P&L from explicit contract counts, costs 1 tick/side/leg + $2.18/contract/side). Over 968 days since 2023-02 vs the stored matrix column: correlation 1.0000, max daily difference $5, totals -48,580 vs -48,597, W42 $5,307 vs $5,303. (My first draft missed the short-side exit and differed; fixed, the engine was right.)

## (b) scaling to common size
- PAPERALL P&L = (w/unit_daily_sd) @ X * g. One weighted cell: X(10-14) $5,303 / $739 * g. Frozen g = 14,238 (weekly SD of the OOS series in family units 0.880 = 12,534/14,238). $5,303/739*14,238 = $102,157. Unit/multiplier handling is correct; there is no weight-normalisation error.
- The size is huge because the OOS series is sparse: weekly SD 12,534 at common size means active weeks are +-$30-90k. Frozen OOS: mean $1,767/wk, SD $12,534, p5/p95 = 0/0 (degenerate interval), max OOS week $88,507, and the OOS series contained W42 itself ($102,157 is its own maximum). Against the frozen band every active week is outside [0,0].
- Cleaned freeze (OOS cut at 20261009): SD in units 0.880 -> 0.650, g 14,238 -> 19,275, so W42 = $138,296 (z 11.03, 9.6 times the largest prior |week| in SD units 9.56). Implied book at that size: about $26M per leg, roughly 254 ZB and 129 ZT contracts, for a strategy active on 8% of weeks. That sizing rule is mechanically consistent but is not an investable size for a sparse book.

## (c) other families
- Same code path: all 252 scored N1 families share ap_n1.py; the engine matched the independent script, so no N1 matrix is wrong and none were rebuilt. Other RT families: most MR are all-zero in OOS (NaN Sharpe, no fit edge); ZB_ZF/ZB_ZT MOM traded W42 negatively (-1.8, -2.2 units) and are not affected beyond the freeze contamination.
- The freeze contamination is general: 155 of 169 PAPER-ALL rows had OOS series through 20261016. For ordinary rows the effect is tiny (g changes 0.2-0.4%; median ratio 0.997). Only N1-RT_ZB_ZT-30m-MR is material (g x1.354, |z| vs clean SD > 3). 8 further rows are sparse (<30% active weeks), listed in n1rt_flag/cross_rows_w42.csv (e.g. N2-ISM_S-RANGE-MET, M2R3-RENKO-ES, several M2-D-YM/ES-*-ffw-T3).
- Only N1 gates a-d passer in FAMILY_RESULTS is N1-EN_HO_RB-5m-MR (best-of-F rank 0.15, not passing the multiplicity line); its W42 contribution is below 0.14 Sharpe, nothing changes.

## Re-scoring of N1-RT_ZB_ZT-30m-MR (METHOD-2 12/3/3 tilt, same custom drift-matched null, 200 reps, n1rt_flag/rescore_ex_w42.py)
| window | OOS Sharpe | net (units) | null rank | boot_lo | gates a b c d | PASS |
|---|---|---|---|---|---|---|
| to 20261016 (as posted; reproduced) | 1.016 | 17.62 | 0.86 | 0.026 | T F T F | no |
| to 20261009 (ex W42) | 0.821 | 10.44 | 0.86 | 0.002 | T F T F | no |
Corrected OOS Sharpe 0.82. Gate b fails (rank 0.86 < 0.95), gate d fails (net_h1 = 0: no OOS trades in the first half), best-of-F rank 0.0. Gates are not softened and FAMILY_RESULTS was not edited (family-level result, pass/fail unchanged; the window convention to 20261016 is the M2 default for every family, the ex-W42 figures are recorded here).

## Fix diff summary (code/census/night_ins/ap_m2_paperall.py; backup autopilot/n1rt_flag/ap_m2_paperall.py.bak)
1. OOS_CUT = 20261009: freeze() now cuts each stored OOS series at the day before FIRST_LIVE before computing g, weekly mean/SD/p5-p95, cum_band, oos_weekly.
2. recut subcommand: re-derives those fields for all 168 stored rows from the cut OOS (weights, flags, fit window untouched; fixed seed 20261019 for the band bootstrap). Backup of the old frozen file: autopilot/n1rt_flag/PRED_PAPERALL.pre_recut.json.
3. SPARSE_FRAC = 0.30: rows flat in >70% of OOS weeks get a SPARSE OOS flag and cannot reach nominal/CONFIRMED promotion on z (stricter, not looser).
4. Rescored: ap_m2_paperall.py score -> PAPERALL_WEEKS.csv, LEAGUE.json (asof 20261016). N1 row: before cum $102,157 / z 8.15 / z-line 3.34; after $138,296 / z 11.03, status "n/a (<6 weeks)", SPARSE flag. No row is nominal or confirmed. (ap_forward_score.py --refresh concerns the lead strategies, not PAPER-ALL, and was not needed.)

## What a +8 z week needs to mean anything
Nothing yet: it is one trade on one data-release day in a book active 8% of weeks, evaluated against an SD that exists only because of a few such days. The row's own OOS history has 11 comparable active weeks (max $88.5k, several negative: -13.8k, -14.4k). Treat as a rare-event tail row; the promotion needs 6+ weeks, the corrected multiplicity line, and for sparse rows a heavy-tailed (bootstrap) threshold rather than the Gaussian z line. Not promoted.

Files: outputs/autopilot/n1rt_flag/{indep_check.py, indep_daily_cell077.csv, rescore_ex_w42.py, cross_rows.py, cross_rows_w42.csv, PRED_PAPERALL.pre_recut.json}.
