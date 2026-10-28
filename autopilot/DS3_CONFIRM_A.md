# DS3_CONFIRM_A - cross-instrument replication of the two frozen NQ rules on ES, YM, RTY (D3CFA, 2026-10-28)

Research only; no live / execution / chart change; no download or purchase; UNTOUCHED never read. Prereg: autopilot/DECISIONS.md line 'D3CFA PREREG' (master sha256 a0b648f556d6201509bb7d410111554d51fc9ffae017a956e976f6f9b21580a3; DR5M group b912e242518d04f2360062507b4737b3d3c535a9f95b79bd0fa9f9357600f00e, RVW1 group 8f9003e2a6dc42b60ce785ee4110bf8cd9f3d919cb482ca4acdc4d1795fe02a7; files l2vast/ds3/prereg/CFA_DR5M_prereg.md, CFA_RVW1_prereg.md; 2 rules x 4 instruments = 8 cells, F = 8). Pre-holdout texts DS3_CFA_DR5M_PREHOLD.md (sha 28cce9fc...5fe66) and DS3_CFA_RVW1_PREHOLD.md (sha fa1b6de6...5a6f6); one main-holdout look per group plus the 2023-span read, all logged (tracks DS3_CFA_DR5M, DS3_CFA_RVW1, _SPAN2). Code l2vast/ds3/code/cfa/ (cfa_core, cfa_run, cfa_prereg, cfa_score, cfa_pretext, cfa_report); outputs l2vast/ds3/out/cfa/.

## Verdict (headline)
**DR5m replicates on 0 of 3 instruments; RVW1 replicates on 0 of 3.** Pooled 3-instrument rows (ES+YM+RTY, equal $1,000 risk each): DR5m WF -$221/wk [-795, +352] (MDE 820), one-sided p 0.775, best-of-8 adjusted p 1.00; RVW1 WF -$359/wk [-986, +269] (MDE 896), p 0.869, best-of-8 adjusted p 1.00. Pass needed >= 2 independent instruments, same sign, CI above 0: not met by either rule, on any instrument, by either R1 or R2. Both NQ reference rows reproduce positive on this same basis (DR5m WF +$443/wk [152, 733]; RVW1 +$402/wk [127, 677]) and, as the rules were found on NQ, that is the in-sample row, not confirmation: by the directive's rule this is NQ-only = **lucky fit, do not pursue** (as a live or sizing candidate; the NQ forward-register rows stay as they are). Task E (Sim spec on pass) NOT triggered for either rule; the DR5m codeable spec was written regardless: autopilot/DS3_SPEC_TOPEN_DR5m.md.

Reading with power in mind (MDE beside every mean): the individual WF MDEs are about $350-415 per week, similar to the NQ means themselves, so single-instrument nulls alone are "inconclusive". What they do rule out: the 95% upper CI bound of the WF mean is below the NQ WF mean on every non-NQ row (DR5m ES +326, YM +152, RTY +113 vs NQ +443; RVW1 ES +234, YM +167, RTY -2 vs NQ +402), and for the pooled rows far below 3x the NQ mean. So an effect as large as NQ's is excluded at the 95% two-sided level on each instrument separately (the NQ mean is selection-inflated, so the correct benchmark is lower, e.g. the half-size HOLD of $261/$267; at that size ES DR5m (+326 upper) and ES RVW1 (+234) cannot be excluded, YM/RTY can).

Gross-versus-cost note (RVW1 only): on ES the direction placebo (a) effect is positive (+$275/wk, CI [41, 525], rank 0.93) and the random-clock placebo (b) +$360 (CI [63, 665]), i.e. the pulled-toward-VWAP direction is better than a coin flip, but the net mean after the bar-proxy fills and fees is -$14/wk and 2x-cost is -$147: ES carries a small directional tilt that costs consume. It is not a replication (net mean CI contains 0; HOLD -$131; 2023 -$46).

## What was run (frozen, no grid, no re-tuning, no neighbours)
- Rules exactly as DS3_SPEC_TOPEN_DR5m_pb1_rm0.5_X60_75.md and DS3_SPEC_RVW1_F30.md v2 (full frozen text in the prereg files). Constants (stop/target 60/75, 30/30 NQ pts) x k (warm-up median 5-min range ratio, out/xi/k_scale.json, as D3CX: ES 0.2553, YM 1.7872, RTY 0.1277), rounded to the tick, floor 4 ticks; DR5m stop/target ES 15.25/19.25 pt, YM 107/134 pt, RTY 7.7/9.6 pt; RVW1 ES 7.75 pt, YM 54 pt, RTY 3.8 pt. Equal $1,000 risk at the stop. D3CX conservative fills: market +1 tick, stop +2 ticks, limit/target only on a 1-tick trade-through (no credit), flat 16:00 (spec). No lock engine / stack / cap. Replay class R2 (1-min bars; ES/YM/RTY have no tick or L2 on disk).
- Fee labels (on every row): ES $4.84 RT NT-published = SOLID; NQ $4.84 = PROXY (reference row); **RTY and YM $4.84 = WEAK proxies (ES value; FEES.md has no standard RTY/YM numbers)**, so RTY, YM and POOL are capped at CANDIDATE and 2x-cost is shown on every row.
- Data windows: scoring series 2023-02-10..2026-10-16 (cross-asset data end; nothing needed lay beyond it; warm-up from 2022-06-01). WFPRE 2024-02-01..2025-06-30, WF 2024-02-01..2026-10-16, HOLD 2025-07-01..2026-10-16, 2023 span 2023-04-01..2024-01-31.
- Identity audits (bars-only ports vs the study event lists, NQ): DR5m 430 of 430 common events identical in side and entry minute (study 432, port 518 incl. 86 warm-up-2022 days); RVW1 619 of 619 signal days identical in side (study 621, the two extra are after the data end 2026-10-16). Fill-model differences make the NQ dollars differ from the study's L2 numbers by design.
- Placebos: (a) random direction, same clock; (b) random clock, same rule (DR5m origin U[11:00, 11:30]; RVW1 anchor U[11:00, 13:00]); 40 draws each, week-bootstrap CI, MDE beside each.
- Gates and calls as in the prereg: tier by D3CX-style gates (WFPRE gates + hold, span2, best-of-N with F = 8); R1 = WF mean > 0, WF CI lower > 0, HOLD mean > 0 (the directive's pass); R2 = R1 + both placebo CIs above 0 on WF + WF 2x-cost mean > 0. Best-of-8 p = min(1, 8 x one-sided p).

## Per-instrument results
### DR5m_pb1_rm0.5 X60_75 (open)

| row | trades/wk (WF) | fill rate | WF $/wk [95% CI] (MDE) | HOLD $/wk [CI] (MDE) | 2023 span $/wk [CI] (MDE) | WF at 2x cost | tier | failed gates | R1 / R2 | p (1-sided) / x8 |
|---|---|---|---|---|---|---|---|---|---|---|
| NQ (reference; fee PROXY) | 2.3 | 1.00 | 443 [152, 733] (MDE 415) | 261 [-157, 679] (MDE 598) | 157 [-333, 647] (MDE 700) | 424 | DEAD | year_share | Y / Y | 0.001 / 0.011 |
| ES (fee solid) | 2.2 | 1.00 | 55 [-216, 326] (MDE 387) | -36 [-416, 344] (MDE 542) | -107 [-632, 419] (MDE 751) | -58 | DEAD | beats_a, beats_b, year_share, hold, span2, best_of_N | n / n | 0.346 / 1.000 |
| YM (fee WEAK proxy) | 2.2 | 1.00 | -114 [-380, 152] (MDE 380) | -124 [-540, 291] (MDE 593) | -53 [-478, 371] (MDE 607) | -174 | DEAD (capped) | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | n / n | 0.800 / 1.000 |
| RTY (fee WEAK proxy) | 2.2 | 1.00 | -162 [-438, 113] (MDE 393) | 140 [-257, 536] (MDE 567) | -153 [-681, 374] (MDE 753) | -273 | DEAD (capped) | mean_up, beats_a, beats_b, cost2x_pre, year_share, span2, best_of_N | n / n | 0.876 / 1.000 |
| POOL ES+YM+RTY (WEAK) | 6.7 | 1.00 | -221 [-795, 352] (MDE 820) | -21 [-867, 825] (MDE 1,208) | -314 [-1,314, 687] (MDE 1,430) | -505 | DEAD (capped) | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | n / n | 0.775 / 1.000 |

Placebos (WF window, 40 draws; effect = real minus mean of draws, weekly $; rank = share of draws below the real; MDE beside each):

| row | (a) random direction, same clock: effect [CI] (MDE) rank | (b) random clock, same rule: effect [CI] (MDE) rank | HOLD (a) effect rank | HOLD (b) effect rank | WFPRE (a)/(b) effect | paired-a WF R/trade [CI] (MDE) |
|---|---|---|---|---|---|---|
| NQ | 383 [107, 653] (391) 0.97 | 489 [172, 788] (435) 1.00 | 314 0.97 | 366 1.00 | 441 / 594 | +0.165 [+0.048, +0.282] (0.167) |
| ES | 126 [-145, 359] (366) 0.85 | 141 [-150, 415] (418) 0.90 | 74 0.57 | 94 0.72 | 172 / 182 | +0.057 [-0.063, +0.177] (0.171) |
| YM | -112 [-352, 125] (362) 0.23 | -33 [-308, 242] (420) 0.42 | -153 0.17 | 104 0.72 | -74 / -157 | -0.051 [-0.168, +0.067] (0.168) |
| RTY | -71 [-318, 178] (356) 0.25 | -147 [-449, 124] (409) 0.07 | 149 0.88 | 193 0.88 | -270 / -453 | -0.032 [-0.150, +0.087] (0.169) |
| POOL | -58 [-610, 441] (768) 0.40 | -39 [-670, 568] (916) 0.45 | 69 0.57 | 391 0.93 | -172 / -428 | -0.009 [-0.077, +0.060] (0.098) |

By calendar year (mean $/wk over the weeks of the year, trades in brackets; 2023 from 2023-02-10, 2026 to 2026-10-16):

| row | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|
| NQ | 45 (106) | 683 (123) | 530 (123) | 22 (95) |
| ES | -252 (129) | 239 (121) | 66 (114) | -201 (89) |
| YM | -42 (129) | -143 (113) | -149 (120) | 18 (89) |
| RTY | -276 (122) | -304 (114) | -84 (125) | -41 (87) |
| POOL | -571 (380) | -209 (348) | -166 (359) | -223 (265) |

Weekly WF P&L correlations: NQ-YM +0.21, NQ-RTY +0.15, ES-NQ +0.42, ES-YM +0.34, ES-RTY +0.13, RTY-YM +0.28.

### RVW1|F30 v2 (close, resting limit)

| row | trades/wk (WF) | fill rate | WF $/wk [95% CI] (MDE) | HOLD $/wk [CI] (MDE) | 2023 span $/wk [CI] (MDE) | WF at 2x cost | tier | failed gates | R1 / R2 | p (1-sided) / x8 |
|---|---|---|---|---|---|---|---|---|---|---|
| NQ (reference; fee PROXY) | 3.0 | 0.96 | 402 [127, 677] (MDE 393) | 267 [-99, 633] (MDE 523) | 235 [-218, 689] (MDE 648) | 356 | DEAD | year_share | Y / Y | 0.002 / 0.017 |
| ES (fee solid) | 3.0 | 0.92 | -14 [-263, 234] (MDE 356) | -131 [-450, 187] (MDE 455) | -46 [-436, 345] (MDE 558) | -147 | DEAD | cost2x_pre, year_share, hold, span2 | n / n | 0.545 / 1.000 |
| YM (fee WEAK proxy) | 2.9 | 0.93 | -87 [-341, 167] (MDE 363) | -103 [-464, 257] (MDE 515) | -131 [-578, 316] (MDE 639) | -192 | DEAD (capped) | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | n / n | 0.750 / 1.000 |
| RTY (fee WEAK proxy) | 2.8 | 0.91 | -257 [-512, -2] (MDE 364) | -669 [-990, -349] (MDE 457) | -170 [-601, 260] (MDE 616) | -405 | DEAD (capped) | beats_b, cost2x_pre, year_share, hold, span2 | n / n | 0.976 / 1.000 |
| POOL ES+YM+RTY (WEAK) | 8.7 | 0.92 | -359 [-986, 269] (MDE 896) | -904 [-1,696, -111] (MDE 1,132) | -347 [-1,375, 680] (MDE 1,468) | -744 | DEAD (capped) | cost2x_pre, year_share, hold, span2 | n / n | 0.869 / 1.000 |

Placebos (WF window, 40 draws; effect = real minus mean of draws, weekly $; rank = share of draws below the real; MDE beside each):

| row | (a) random direction, same clock: effect [CI] (MDE) rank | (b) random clock, same rule: effect [CI] (MDE) rank | HOLD (a) effect rank | HOLD (b) effect rank | WFPRE (a)/(b) effect | paired-a WF R/trade [CI] (MDE) |
|---|---|---|---|---|---|---|
| NQ | 486 [200, 767] (396) 1.00 | 524 [205, 837] (447) 1.00 | 338 0.95 | 447 1.00 | 614 / 587 | +0.145 [+0.058, +0.233] (0.125) |
| ES | 275 [41, 525] (354) 0.93 | 360 [63, 665] (430) 1.00 | 104 0.70 | 277 0.95 | 426 / 431 | +0.067 [-0.017, +0.151] (0.120) |
| YM | 110 [-145, 370] (366) 0.82 | 193 [-81, 483] (400) 0.93 | 93 0.62 | 80 0.80 | 125 / 293 | +0.031 [-0.055, +0.117] (0.123) |
| RTY | 15 [-233, 254] (368) 0.50 | 65 [-201, 323] (392) 0.70 | -463 0.00 | -302 0.07 | 449 / 397 | -0.006 [-0.097, +0.085] (0.129) |
| POOL | 400 [-210, 1,049] (905) 0.97 | 619 [-61, 1,328] (989) 1.00 | -267 0.28 | 55 0.60 | 1,000 / 1,121 | +0.032 [-0.019, +0.082] (0.072) |

By calendar year (mean $/wk over the weeks of the year, trades in brackets; 2023 from 2023-02-10, 2026 to 2026-10-16):

| row | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|
| NQ | 248 (166) | 300 (152) | 607 (169) | 254 (123) |
| ES | -53 (154) | -70 (162) | 258 (157) | -241 (124) |
| YM | -57 (154) | -203 (150) | 6 (163) | -88 (108) |
| RTY | -187 (159) | -44 (146) | -334 (147) | -404 (120) |
| POOL | -297 (467) | -317 (458) | -70 (467) | -733 (352) |

Weekly WF P&L correlations: NQ-YM +0.37, NQ-RTY +0.34, ES-NQ +0.65, ES-YM +0.65, ES-RTY +0.42, RTY-YM +0.52.

## Gate failures, one line per cell (never softened)
- DR5m NQ DEAD: year_share only (WFPRE gain 75 percent in 2024; every other gate passes, R1 and R2 true, best-of-N p95 385 beaten); this is the reference row. ES DEAD: beats_a, beats_b, year_share, hold, span2, best_of_N (WF mean +55, CI [-216, 326], MDE 387). YM DEAD (capped): mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N (WF -114, MDE 380). RTY DEAD (capped): mean_up, beats_a, beats_b, cost2x_pre, year_share, span2, best_of_N (WF -162, HOLD +140 inside its MDE 567). POOL DEAD: all but min_n.
- RVW1 NQ DEAD: year_share only (63 percent of the WFPRE gain in one year), R1 and R2 true. ES DEAD: cost2x_pre, year_share, hold, span2 (WF -14, MDE 356; note WFPRE mean was +92). YM DEAD (capped): mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N (WF -87, MDE 363). RTY DEAD (capped): beats_b, cost2x_pre, year_share, hold, span2 (WF -257 [-512, -2] MDE 364; HOLD -669 [-990, -349], an outright negative). POOL DEAD: cost2x_pre, year_share, hold, span2 (HOLD -904 [-1,696, -111] MDE 1,132).
- year_share is evaluated on a 2-calendar-year selection window (2024-02..2025-06) as in D3CX; any positive-gain row with one dominant year fails it, so it is a weak discriminator here, and no tier turns on it alone except the two NQ reference rows, which stay DEAD by the prereg.

## Independence caveat
ES, NQ, YM and RTY are index futures with correlated flow: weekly WF P&L correlations for DR5m are +0.13 to +0.42; for RVW1 +0.34 to +0.65 (ES-NQ 0.65, ES-YM 0.65, RTY-YM 0.52 above the prereg 0.5 flag). A pass on RVW1 would therefore have counted as weaker than independent evidence; moot since there is none.

## What this does and does not say
- It says: with the frozen NQ constants scaled by volatility, on the D3CX conservative fills, ES/YM/RTY do not show either edge in 2024-02..2026-10 (nor in the 2023 span), and the NQ-sized effect is excluded on each separately; the NQ result is not corroborated by independent instruments, so by the directive both rules are NQ-only, "lucky fit, do not pursue".
- It does not say the NQ rows are zero: they are positive here (DR5m HOLD +$261 [-157, 679], 2023 +$157; RVW1 HOLD +$267 [-99, 633], 2023 +$235), i.e. the NQ edge halves out of the selection window as already known and remains within its own MDE in HOLD. The NQ forward-register shadow rows stay as specified; no change is recommended or made.
- Limits: ES/YM/RTY on 1-min bars with bar-proxy touches (RVW1 limit at the last print, fill needs a 1-tick trade-through; DR5m market at next open), no L2 queue or book data, so an edge that depends on NQ-specific microstructure (queue position, touch-join credit that the NQ direct replay gave DR5m) cannot be tested here; k-scaling is the D3CX standard and not tuned; WEAK fee proxies on RTY/YM; MDE about $350-415/wk per instrument means a true effect of half the NQ WF mean would not be detected on a single instrument (the pooled MDE is $820-896).

## Disclosures
- No bug found in the ports; both identity audits above passed. No fix needed.
- Code was written and smoke-tested on counts, bar times, fill rates and the two identity audits only (no P&L printed) before the prereg line; the first full P&L numbers read were the WFPRE-only pre texts, then the single holdout/2023 read in FINAL. The identity audits against the study event lists (NQ) were run AFTER the FINAL scoring (they read event days and sides only, no P&L); results as above, no definition changed.
- Interpretations fixed in the prereg before scoring: pullback scan to the 10:29 bar (study harness), entry at the next bar open, flat at 16:00 (the spec's harness exit; D3CX used 16:54), stop/target from the fill including the entry tick, RVW1 limit price = close of the 15:29 bar with 1-tick trade-through fill, fill-bar stop counted / target not credited, eligibility >= 385 of 390 RTH bars, Median5 with minimum 10 prior sessions and 2022 warm-up.
- Looks: group DR5M and RVW1 each one main-holdout look; the 2023-span read at the same look (tracks logged as _SPAN2); ledger trials +8 (total 68,229 after both appends).
- Not tested: stack add, lock engine, 50-contract cap, margin (items C/D of the directive), RVW1 queue-position execution (item B).
