# REPORT C2-G1 - exit management of the pair (breakeven / trail / scale-out / time stop)

**Verdict: NO. Every one of the 23 pre-registered cells loses money against the live exits on clean, H1 and H2. None qualifies for selection; nothing to verify; 0 FOUND, 0 LEAD.**

Corrected NT8-faithful engine (REPORT_ENGINE_RECON.md), 8/8, 1 tick/side + NT8 commission $34.88, 

**Verdict key.** SURVIVES = (a) H2 net >= +5% and H2 max DD <= -10% vs the baseline row, (b) H1 net >= 90% and H1 DD <= +10%, (c) clean net >= 95% of baseline (matched null pending unless stated). INSURANCE = not SURVIVES, all-in cost >= -5% and one of all-in CVaR5 / worst week +25% or max DD +20% better, with clean and H1 CVaR5 and DD not worse. NO otherwise.

## What was run
- Pre-registered grid (PREREG_AUTOPILOT.md, cycle 2): breakeven stop after +{20,30,40} pts (stop to entry / entry+2) = 6 cells; trail {20,30} after +{30,40} = 4; scale half out at +{30,40} with the rest to 60/stop = 2; time stop {60,120,240} min = 3; 8 combos. 23 cells + the live baseline row.
- Engine: the D2-E5 exact 1-second re-simulator (live rows reproduced exactly: baseline rebuilt on the 1-s path matches the live daily series to the cent in both configs, max |dx| = 0.0) with the exit management added. Triggers use the favourable extreme of PREVIOUS seconds (active from the next second), the adverse level is checked first inside a second, stop-type exits fill at their level (as the live +-60 stop does), time stops exit at the second close, 1 tick/side + $34.88 as live.
- Scope: **7,664 of 13,089 rows (59%) are managed** (own-bracket stop/target rows). The 5,425 rows closed by an opposite entry (netting), a time block, or another lot's order keep their live exit, because their exit is an account-level FIFO event that the single-row path cannot reproduce. Management of those rows, and the knock-on effect of an earlier exit on later netting, is not modelled.
- Live rules re-applied on top (b11_nt8 / d1_core fast pass): per-book 5R/-2R, day lock 8R/2R/67%/0000, combined week floor -8R, per-book week rule off. Scoring key: standard SURVIVES/INSURANCE key (rep_common.make) against the live baseline row, which is the first row. The pair was computed with the baseline rebuilt in this process; the second table repeats the verdict against B.Cfg() (per-book -6R week rule on, no combined floor) as the robustness line.
- Weight handling for scale-out: two rows with weights {0.5, 0.5} (b11 WGT), so locks mark each tranche.

## Table (baseline row first), live config
| cell | verdict | clean net | clean Sh | H1 net | H1 Sh | H2 net | H2 Sh | all-in net vs live | all-in worst wk | all-in max DD |
|---|---|---|---|---|---|---|---|---|---|---|
| BASELINE live (reproduces the live rows) | BASELINE | 1,330k | 1.46 | 594k | 2.83 | 761k | 2.30 | +0% | -83k | 280k |
| BE after +20, stop to entry | NO | -1,872k | -2.24 | -160k | -0.86 | -802k | -2.79 | -206% | -86k | 2,861k |
| BE after +20, stop to entry+2 | NO | -2,220k | -2.82 | -235k | -1.28 | -1,012k | -3.70 | -229% | -84k | 3,491k |
| BE after +30, stop to entry | NO | -552k | -0.61 | 320k | 1.59 | -564k | -1.74 | -130% | -83k | 838k |
| BE after +30, stop to entry+2 | NO | -676k | -0.75 | 311k | 1.49 | -433k | -1.33 | -130% | -82k | 844k |
| BE after +40, stop to entry | NO | 319k | 0.35 | 334k | 1.47 | -340k | -1.00 | -88% | -83k | 555k |
| BE after +40, stop to entry+2 | NO | 322k | 0.35 | 261k | 1.11 | -197k | -0.57 | -86% | -83k | 549k |
| TRAIL 20 after +30 | NO | -2,358k | -3.28 | -173k | -0.80 | -974k | -3.81 | -231% | -82k | 3,545k |
| TRAIL 30 after +30 | NO | -1,619k | -2.08 | 166k | 0.74 | -718k | -2.17 | -181% | -81k | 2,185k |
| TRAIL 20 after +40 | NO | -1,265k | -1.63 | -94k | -0.38 | -827k | -3.05 | -181% | -84k | 2,205k |
| TRAIL 30 after +40 | NO | -646k | -0.77 | 41k | 0.17 | -409k | -1.22 | -138% | -86k | 1,125k |
| SCALE half at +30, rest to 60/stop | NO | -645k | -0.83 | 198k | 0.97 | -218k | -0.62 | -125% | -85k | 744k |
| SCALE half at +40, rest to 60/stop | NO | -66k | -0.08 | 314k | 1.52 | -37k | -0.11 | -92% | -83k | 647k |
| TIME stop 60 min | NO | -2,768k | -3.71 | -314k | -1.50 | -202k | -0.66 | -222% | -80k | 3,302k |
| TIME stop 120 min | NO | -1,641k | -1.93 | -19k | -0.09 | 63k | 0.21 | -159% | -82k | 1,764k |
| TIME stop 240 min | NO | -172k | -0.20 | 126k | 0.57 | 679k | 2.09 | -76% | -83k | 649k |
| COMBO scale half +30, BE +30 on rest | NO | -1,609k | -2.15 | 50k | 0.24 | -690k | -2.19 | -184% | -86k | 2,268k |
| COMBO scale half +40, BE +30 on rest | NO | -1,549k | -1.92 | 70k | 0.34 | -690k | -2.16 | -181% | -82k | 2,192k |
| COMBO BE +30 + time 120 | NO | -2,390k | -2.98 | -118k | -0.61 | -747k | -2.39 | -221% | -81k | 3,298k |
| COMBO trail 30 after +40 + time 120 | NO | -2,406k | -3.20 | -207k | -0.97 | -809k | -2.76 | -227% | -84k | 3,475k |
| COMBO scale half +30, trail 30 after +40 on rest | NO | -1,544k | -2.15 | -101k | -0.45 | -870k | -2.84 | -194% | -83k | 2,531k |
| COMBO BE +20 + scale half +40 | NO | -2,454k | -3.18 | -300k | -1.59 | -1,158k | -4.38 | -246% | -85k | 3,913k |
| COMBO BE +40 off 2 + time 240 | NO | -909k | -1.05 | 12k | 0.06 | -248k | -0.73 | -143% | -83k | 1,231k |
| COMBO scale half +30 + time 120 | NO | -2,867k | -4.07 | -257k | -1.30 | -551k | -1.72 | -237% | -81k | 3,707k |

## Same cells against B.Cfg() (robustness): net change vs that baseline, by span
| cell | verdict | clean net | H1 net | H2 net | all-in net |
|---|---|---|---|---|---|
| BASELINE live (reproduces the live rows) | BASELINE | +0% | +0% | +0% | +0% |
| BE after +20, stop to entry | NO | -243% | -173% | -198% | -216% |
| BE after +20, stop to entry+2 | NO | -275% | -188% | -217% | -242% |
| BE after +30, stop to entry | NO | -145% | -56% | -132% | -125% |
| BE after +30, stop to entry+2 | NO | -159% | -57% | -126% | -131% |
| BE after +40, stop to entry | NO | -71% | -60% | -111% | -81% |
| BE after +40, stop to entry+2 | NO | -72% | -82% | -112% | -86% |
| TRAIL 20 after +30 | NO | -290% | -152% | -222% | -245% |
| TRAIL 30 after +30 | NO | -226% | -104% | -179% | -190% |
| TRAIL 20 after +40 | NO | -182% | -128% | -194% | -176% |
| TRAIL 30 after +40 | NO | -133% | -120% | -145% | -135% |
| SCALE half at +30, rest to 60/stop | NO | -160% | -75% | -114% | -131% |
| SCALE half at +40, rest to 60/stop | NO | -103% | -63% | -84% | -90% |
| TIME stop 60 min | NO | -326% | -205% | -105% | -236% |
| TIME stop 120 min | NO | -206% | -132% | -64% | -149% |
| TIME stop 240 min | NO | -98% | -93% | -10% | -69% |
| COMBO scale half +30, BE +30 on rest | NO | -227% | -122% | -185% | -196% |
| COMBO scale half +40, BE +30 on rest | NO | -217% | -105% | -183% | -187% |
| COMBO BE +30 + time 120 | NO | -276% | -152% | -168% | -221% |
| COMBO trail 30 after +40 + time 120 | NO | -273% | -181% | -172% | -226% |
| COMBO scale half +30, trail 30 after +40 on rest | NO | -229% | -145% | -196% | -204% |
| COMBO BE +20 + scale half +40 | NO | -302% | -185% | -245% | -264% |
| COMBO BE +40 off 2 + time 240 | NO | -157% | -134% | -122% | -143% |
| COMBO scale half +30 + time 120 | NO | -321% | -186% | -154% | -245% |

## Why: the live pair's edge sits in the trades that run
Trade-level (points per trade, rows whose exit changed; baseline vs managed):
| cell | rows changed | live mean pts | managed mean pts | total pts change |
|---|---|---|---|---|
| BE after +20, stop to entry | 3515 | +16.0 | +0.0 | -56,220 |
| BE after +20, stop to entry+2 | 3701 | +18.2 | +2.0 | -59,978 |
| BE after +30, stop to entry | 2228 | +15.8 | +0.0 | -35,280 |
| BE after +30, stop to entry+2 | 2357 | +18.3 | +2.0 | -38,306 |
| BE after +40, stop to entry | 1252 | +15.1 | +0.0 | -18,960 |
| BE after +40, stop to entry+2 | 1312 | +17.2 | +2.0 | -19,936 |
| TRAIL 20 after +30 | 4173 | +36.4 | +21.6 | -61,660 |
| TRAIL 30 after +30 | 3163 | +28.9 | +12.7 | -51,184 |
| TRAIL 20 after +40 | 3141 | +42.1 | +28.6 | -42,554 |
| TRAIL 30 after +40 | 2223 | +34.7 | +19.1 | -34,778 |
| SCALE half at +30, rest to 60/stop | 5682 | +42.7 | +36.3 | -36,030 |
| SCALE half at +40, rest to 60/stop | 5330 | +49.5 | +44.7 | -25,220 |
| TIME stop 60 min | 2823 | +22.5 | +4.3 | -51,385 |
| TIME stop 120 min | 1592 | +24.3 | +5.0 | -30,791 |
| TIME stop 240 min | 853 | +24.5 | +6.7 | -15,217 |
| COMBO scale half +30, BE +30 on rest | 5682 | +42.7 | +33.2 | -53,670 |
| COMBO scale half +40, BE +30 on rest | 5682 | +42.7 | +34.1 | -48,940 |
| COMBO BE +30 + time 120 | 3131 | +18.4 | +1.9 | -51,646 |
| COMBO trail 30 after +40 + time 120 | 3149 | +28.5 | +12.4 | -50,891 |
| COMBO scale half +30, trail 30 after +40 on rest | 5682 | +42.7 | +33.3 | -53,419 |
| COMBO BE +20 + scale half +40 | 6151 | +34.9 | +24.0 | -66,720 |
| COMBO BE +40 off 2 + time 240 | 1918 | +19.0 | +3.6 | -29,517 |
| COMBO scale half +30 + time 120 | 5948 | +38.1 | +28.8 | -55,401 |

The pair is a trend follower with a symmetric 60/60 bracket. Trades that have gone +40 pts finish at +60 more often than at -60 (BE after +40 changes 1,252 rows: 784 of them live winners, 468 live losers; the live mean of those rows is +15.1 pts, the managed mean 0.0). Every early-exit rule converts that continuation into scratches while paying the same round-trip cost, so total points fall from 27,928 to 8,968 for BE40 and to 12,711 for the 240-minute time stop. The 240-minute time stop touches 853 rows whose live mean is +24.5 pts (long-held trades are the winners). In other words path information at +20..+40 pts does not say "give it back", it says "keep going".

## Gates (adapted for a change to the pair itself)
Not reached. The pre-registered selection rule (top 3 on clean weekly Sharpe subject to clean net >= 95% of live and a positive clean Sharpe change) selects nothing: the best cell by clean net is BE after +40, stop to entry+2 at 322k vs 1,330k live. H1 and H2 columns are shown for transparency only; they were not used for any choice. Plateau (+-25%), 2x slippage, path-destroyed and matched-random-exit nulls, bootstrap and rolling Sharpe were therefore not run (no candidate to test; every neighbour of a losing cell also loses).

## Implementability
Not applicable (nothing to implement). For reference, breakeven/trail/scale/time stops are all native NT8 order-management settings (parameters, not new logic), so a positive result would have been cheap to deploy; the result is negative.

## Idea logged for a later cycle (not run; needs its own pre-registration)
The opposite direction - let winners run - is what the D3 lever ranking points at (+10% average win = +106% net): e.g. widen the target once a trade is +40 in profit, or trail only the target. E6 tested static brackets (70+ lose money), E5 tested tighter/at-touch targets; the conditional extension (target moves out only after the trade proves itself) has not been tested.

Runtime: grid 7.6 s on 6 workers; build and baseline verification < 2 s per cell. Fill model: second-bar path, stop-type fills at the level, 1 tick/side slippage as live (no gaps modelled).

DONE C2_G1
