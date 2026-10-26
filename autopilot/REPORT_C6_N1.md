# REPORT C6-N1 - ex-ante regime switch for the pair

Registered in PREREG_AUTOPILOT.md (CYCLE 6). Verdict: **NO. 0 FOUND, 0 LEAD.** The pair's weekly P&L is not separated by any pre-registered market-state variable in a way that persists from 2014-2022 into 2023-2026, and the one rule the protocol selects idles the pair and loses Sharpe in every read span.

## Protocol (as registered)
- Fit span: weeks from 2014-01-06 to 2022-12-26 (first year dropped so every state variable exists), pair P&L from the C3-H2 1-minute engine (live rules, 8/8, 1 tick/side; its fidelity to the live 1-second engine is 90% entry match, weekly correlation 0.83-0.91). Read spans: clean 2023-08..2025-07, H1, H2 on the **live corrected-engine series** B.Cfg(wk_floor=8, wk_loss_pb=None), computed in a clean process (live all-in net $2,685,011 from 2023-08, weekly Sharpe 1.86; clean 1.46 / H1 2.83 / H2 2.30). Read once.
- State variables (computed from NQ RTH daily bars built from the purchased 1-minute data, using data up to the last RTH close before the week's Monday): 20- and 60-day variance ratio (q=5) of daily returns (vr20, vr60); 20-day realised vol (rv20) and its 60-day percentile (rv20_pct60); 20-day mean daily range / close (adr20) and its 250-day percentile (adr20_pct250); 20-day mean |RTH gap| (gap20); 20-day volume 250-day percentile (vol20_pct250); trailing 4 / 13-week pair Sharpe (benchmark). Level variables (rv20, adr20, gap20) are not stationary across 2014-2026; they are in the registered list and kept.
- Rule family (120 rules, exposure >= 30% in fit): variable x cut {33rd, 50th, 67th percentile of the fit-span distribution, applied as an absolute threshold later} x direction {high or low favourable} x outside weight {0, 0.5}. Selected by weekly Sharpe of the switched pair on the fit span only.

## 1. Descriptive table - pair weekly Sharpe by tercile of each state variable (terciles cut on the 2014-2022 distribution; n/a = no weeks in that tercile in that span)
| var          | tercile   |   2014-2022 (1-min engine) |   clean (live) |   H1 (live) |   H2 (live) |
|:-------------|:----------|---------------------------:|---------------:|------------:|------------:|
| adr20        | high      |                      -1.47 |           2.47 |        1.87 |        2.01 |
| adr20        | low       |                      -0.05 |           0.85 |        4.59 |      nan    |
| adr20        | mid       |                      -0.53 |           1.13 |        2.28 |        1.85 |
| adr20_pct250 | high      |                      -1.09 |           2.4  |        1.87 |        1.53 |
| adr20_pct250 | low       |                      -0.2  |           1.57 |        2.91 |        0.56 |
| adr20_pct250 | mid       |                      -0.98 |           0.18 |        2.77 |        3.15 |
| gap20        | high      |                      -1.4  |           2.4  |        4.03 |        2.32 |
| gap20        | low       |                      -0.06 |           2.56 |        4.93 |      nan    |
| gap20        | mid       |                      -0.62 |           0.88 |        1.59 |        2.18 |
| pair_sh13    | high      |                      -1.5  |           1.35 |        2.83 |        2.3  |
| pair_sh13    | low       |                      -0.62 |           3.03 |      nan    |      nan    |
| pair_sh13    | mid       |                      -0.4  |           1.62 |      nan    |      nan    |
| pair_sh4     | high      |                      -1.47 |           0.98 |        2.59 |        1.52 |
| pair_sh4     | low       |                      -0.37 |           3.38 |      nan    |      nan    |
| pair_sh4     | mid       |                      -0.77 |           1.55 |        3.2  |        4.21 |
| rv20         | high      |                      -1.69 |           2.71 |      nan    |        1.66 |
| rv20         | low       |                       0.31 |           3.32 |        3.07 |      nan    |
| rv20         | mid       |                      -0.54 |           0.58 |        3.14 |        2.28 |
| rv20_pct60   | high      |                      -1.03 |           1.3  |        3.68 |        1.51 |
| rv20_pct60   | low       |                      -0.31 |           1.22 |        1.96 |        2.59 |
| rv20_pct60   | mid       |                      -1.03 |           2.06 |        2.8  |        3.46 |
| vol20_pct250 | high      |                      -1.52 |           1.21 |        2.68 |      nan    |
| vol20_pct250 | low       |                      -0.57 |           2.04 |        2.7  |        2.21 |
| vol20_pct250 | mid       |                      -0.34 |           0.18 |        3.06 |        4.22 |
| vr20         | high      |                      -0.76 |           1.07 |        6.38 |        1.19 |
| vr20         | low       |                      -1.04 |           1.67 |        0.97 |        2.99 |
| vr20         | mid       |                      -0.61 |           1.69 |        1.83 |        2.47 |
| vr60         | high      |                      -0.4  |           2.05 |        2.14 |        0.7  |
| vr60         | low       |                      -1.08 |           1.2  |        2.48 |        2.11 |
| vr60         | mid       |                      -0.94 |           1.23 |        3.55 |        4.35 |

Reading: the pair loses in **every tercile of every variable** in 2014-2022 (the only positive cell is low realised vol, Sharpe +0.31) and is profitable in almost every tercile of every variable in 2023-2026. The sign of the pair's edge tracks the era, not any state variable. The within-variable ordering of terciles does not persist: of 21 variable x span comparisons with all three terciles populated, 12 have a tercile rank correlation of at least +0.5 between the fit span and the read span, and the fit-span high-minus-low spreads are small (|spread| <= 2.0 and mostly < 1) against read-span spreads of either sign (see `n1_results.pkl` / PERS). Level variables push the 2023-2026 weeks into the high tercile (vol and range are higher than in 2014-2019), so e.g. rv20-low is populated in only 12% of clean weeks and 3% of H2.

## 2. The selected rule (fit on 2014-2022 only)
**rv20, low favourable, cut at the 33% fit percentile = 0.00794, outside weight 0.0**: trade the pair only when 20-day realised vol of NQ daily returns is below 0.79% a day. Fit-span weekly Sharpe +0.18 (the unswitched pair is -0.78 over 2013-2022), fit exposure 33% of weeks. The in-sample best rule has a Sharpe of only +0.18.

## 3. Read on clean / H1 / H2 (live series) - the switch
| span | live Sharpe | switched Sharpe | uplift | live worst week | switched worst week | live net $ | switched net $ | exposure | uplift at 2x slippage | bootstrap 90% CI of uplift | full-pipeline shift-null p95 / rank | random same-exposure null p95 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.10 | -0.36 | -81,874 | -77,153 | 1,329,959 | 322,794 | 12% | +0.03 | [-1.60, 0.86] | +0.13 / 69% | +0.18 |
| H1 | 2.83 | 1.61 | -1.22 | -78,287 | -42,870 | 593,797 | 164,610 | 29% | -1.13 | [-3.89, 0.87] | +0.31 / 41% | +0.21 |
| H2 | 2.30 | 1.20 | -1.09 | -82,524 | -0 | 761,254 | 116,706 | 3% | -0.99 | [n/a, n/a] | +0.34 / 39% | +0.43 |
| all | 1.86 | 1.22 | -0.63 | -82,524 | -77,153 | 2,685,011 | 604,110 | 12% | -0.36 | [-1.62, 0.27] | -0.09 / 63% | -0.17 |

- The rule leaves the pair on in only 12% of clean weeks, 29% of H1 and 3% of H2, because 2023-2026 volatility sits above the 2014-2019 cut. Net falls 76%, 72%, 85%.
- The uplift is negative in every span (clean -0.36, H1 -1.22, H2 -1.09, all-in -0.63). It is inside the full-pipeline null (the whole selection repeated under 678 circular shifts of all state variables against the pair): ranks 69% / 41% / 39% / 63%. The random same-exposure switch null (1,000 draws) has a similar centre.
- Bootstrap: the 90% interval of the all-in uplift is [-1.62, 0.27]; H2 has too few active weeks for an interval.
- Plateau (cut percentile +-10 points): both neighbours also lose (all-in uplift -1.56, -0.59); 0 of 2 keep 75% of an uplift that is not there.
- Rolling 26-week Sharpe of the switched pair is at or above the live pair in 17% of windows.
- All 120 fitted rules were also read once for transparency: only 1 of 120 has a positive uplift on clean, H1 and H2 together, and it is not the fit's choice.

## 4. Sensitivity (non-gating): stationary variables only
Restricting the family to ratio / percentile / trailing-Sharpe variables (vr20, vr60, rv20_pct60, adr20_pct250, vol20_pct250, pair_sh4, pair_sh13) selects **adr20_pct250**, rule (5, 0.3333333333333333, 'lo', 0.0), with a fit-span Sharpe of -0.14 - no stationary state produces a positive pair Sharpe in 2014-2022. Read uplift: clean -0.44, H1 -0.60, H2 -2.03, all-in -0.76; null ranks 62% / 64% / 9%. Same conclusion.

## 5. Gates (FOUND, adapted for a change to the pair)
| gate | result |
|---|---|
| Pre-registered | yes (before the run) |
| Selection on the fit span only; clean/H1/H2 read once | yes |
| Weekly Sharpe up >= 0.10 on clean, H1 and H2 separately | **FAIL** (-0.36 / -1.22 / -1.09) |
| Worst week not worse | clean and H1 better, H2 "better" only because the pair is flat (3% exposure); not meaningful |
| Own null p95 (full-pipeline circular shift) and bootstrap CI above zero | **FAIL** (ranks 69% / 41% / 39%; CI includes zero) |
| Plateau and 2x slippage | **FAIL** (neighbours lose; 2x-slippage uplift also negative: clean +0.03, H1 -1.13, H2 -0.99) |
| Executable / implementable | would need a weekly state computation (NQ daily realised vol from the data feed) and a size multiplier input in DualStrat (small code change); not recommended |

## 6. What this says about the C3-H2 finding
The pair's lack of edge in 2013-2022 and its edge in 2024-2026 are **not explained by** volatility level or change, range, trend persistence (variance ratio), gap size, volume, or by its own trailing performance. Within each era the terciles do not order the pair's results consistently across eras. The practical reading: with these observables the live pair cannot be switched on and off by regime; the edge looks period-specific. Sizing and monitoring (D3 sections 1 and 3) are the tools left, not a state switch.

Fill model: 1-minute engine for the fit span (stop-first, 1 tick/side + commission), live 1-second engine for the read spans. Limits: the 2014-2022 pair series comes from the 1-minute engine (90% entry fidelity); the switch scales the whole week's P&L (a close approximation to scaling contracts for the week); only one selected rule is the candidate.
Runtime: about 10 seconds of compute for the whole analysis (4.8 s main run), plus feature building. Code: `ap_c6_n1_feat.py`, `ap_c6_n1_live.py`, `ap_c6_n1_main.py`, `ap_c6_n1_rep.py`; data `outputs/autopilot/c6/n1/`.

DONE C6_N1
