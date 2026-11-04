# DS3_SLOT_CHANNEL: is the TH cut's second channel "slot turnover"? (DIS-AK)

Author ZL-2, 2026-11-04. Scope note l2vast/ds3/prereg/DISAK_scope.md sha256 acb60d28c6d9d39639d9eb74e00c0f7a7bfab6531d9dad6237d2e7c4f1532230 (DECISIONS.md, before any outcome). Measurement; no PASS; nothing live. Code l2vast/ds3/code/dis_x/ak_*.py; table l2vast/ds3/out/dis_ak/ak_variants.csv. Engine V13T ts2 (all runs: full stack, live lots, live cost frame, carrying weeks dropped for the period statistics; trade comparisons use all label days). Cells below: mean $/week / weekly-cumulative maxDD $k / Calmar.

## Plain sentence
The "freed slot" story does not hold: only 6 of the 1,779 extra trades that the cut allows were blocked in the OFF run by a position that the cut had closed early (emulating "slot not reusable until the plain exit time" changes the stack by -$2k of $2,520k and removes 24 signals); the extra trades come instead from the per-book daily loss gate (a book stops entering after a realised day loss of 2R): the gate blocks entries 1,556 times in the OFF run and 432 times with the cut, and 1,201 of the 1,779 extra trades (68%) sit on days when the OFF run's loss gate had blocked that book (88 more on the profit gate, 484 not classified), so the second channel is a risk-gate interaction and is worth +$162k live over 2023-26 (+$113k in 2026), but with the daily loss gate removed the cut still adds +$244k (2026 +$382k, 2025 -$201k) so the cut itself, not the turnover, carries most of the benefit and all of its year-to-year sign; the extra trades are not especially good trades (2026: +1.3 points/lot vs +1.7 for common trades; 2025: -2.0 vs +2.0; only 2024 +8.2 vs +3.1), they are more trades taken after losing days, whose sign follows the period; time stops (20-60 minutes, conditional or not) do not capture any of it and cost $0.4-0.8M over the period, and a re-entry pause after the cut also lowers the mean (-$0.2M to -$0.8M) while lowering the 2026 drawdown.

## 1. Hooks (existing only; no engine edit)
| item | hook | status |
|---|---|---|
| (a) cut ON/OFF | ov th_loss | exists; ON reproduces $2,520,149 |
| (b) time stop instead of the cut | ov inject (T.inject kind 'time', market exit 0.80 at the path price), th_loss off; rows of KB/PE/SM/HM/MV only (PB rows have no library exit, so the inject hook cannot price them); applied only where the plain exit is later than N minutes | exists; forward-safe (conditional form uses the open P&L at N minutes) |
| (c) cut applied, freed slot not reusable until the plain exit | no hook; emulated with ov extra_skip (rows of the same book entering after the cut exit and at or before the plain exit of the cut trade, mask from the ON run's cut trades, plain exits from the OFF run) | emulation; validated below |
| (d) re-entry pause after a cut | no dedicated hook; emulated with extra_skip (same book, N = 15/30/60 minutes after each cut); the SM-only U7 blackout hook is a fixed rule (ov u7 and the u7 keyword are rejected by the V13T chain: no hook) | emulation |
| daily loss gate / profit gate / give-back | OC.CFG['spec'] pb_loss, pb_win, arm/keep (lock_noise hook) | exists |
Dead_lookup (cited): DS3_EXIT_N_LOSS.md F-C time-stops (no progress at <= 0 after 5/10/20/30 min) harmful on V13T_LIVE (-13.1k to -18.8k $/wk); U7 blackout zero effect; DS3_CUTWAIT.md 1,044 cells 0 PASS / 0 CANDIDATE / 1,044 DEAD (cut at -X plus a pause); DS3_EXIT_N_RETARGET_TIME.md. The new ts2 reruns below agree.

## 2. Variants
| variant | total $k | 2023 | 2024 | 2025 | 2026 | HOLD | PRE | L6M | ALL |
|---|---|---|---|---|---|---|---|---|---|
| (a) TH cut ON (reference) | 2520 | -0.2k / 49k / -0.00 | 13.8k / 75k / 0.18 | 17.0k / 71k / 0.24 | 35.3k / 63k / 0.56 | 27.9k / 122k / 0.23 | 15.2k / 75k / 0.20 | 43.5k / 63k / 0.70 | 17.7k / 75k / 0.24 |
| (a) TH cut OFF | 2243 | 0.4k / 81k / 0.01 | 11.3k / 175k / 0.06 | 21.8k / 94k / 0.23 | 21.7k / 91k / 0.24 | 19.9k / 91k / 0.22 | 14.8k / 175k / 0.08 | 23.5k / 90k / 0.26 | 15.7k / 175k / 0.09 |
| (b) time stop 20 min, no progress (<=0), cut off | 1400 | -5.4k / 125k / -0.04 | 11.1k / 115k / 0.10 | 11.6k / 76k / 0.15 | 19.1k / 71k / 0.27 | 14.4k / 124k / 0.12 | 12.5k / 115k / 0.11 | 23.7k / 71k / 0.33 | 11.1k / 125k / 0.09 |
| (b) time stop 30 min cond., cut off | 1489 | -3.1k / 83k / -0.04 | 10.5k / 113k / 0.09 | 13.0k / 83k / 0.16 | 22.3k / 74k / 0.30 | 16.5k / 161k / 0.10 | 13.4k / 113k / 0.12 | 28.9k / 60k / 0.48 | 12.2k / 113k / 0.11 |
| (b) time stop 45 min cond., cut off | 1777 | -3.7k / 126k / -0.03 | 11.8k / 125k / 0.09 | 15.0k / 98k / 0.15 | 25.2k / 101k / 0.25 | 20.7k / 101k / 0.20 | 13.2k / 125k / 0.11 | 29.9k / 101k / 0.30 | 13.8k / 126k / 0.11 |
| (b) time stop 60 min cond., cut off | 1886 | -2.1k / 88k / -0.02 | 13.6k / 132k / 0.10 | 17.2k / 115k / 0.15 | 18.2k / 96k / 0.19 | 16.6k / 96k / 0.17 | 14.1k / 132k / 0.11 | 20.5k / 96k / 0.21 | 14.0k / 132k / 0.11 |
| (b) time stop 30 min uncond., cut off | 346 | -2.4k / 46k / -0.05 | 2.7k / 189k / 0.01 | 2.0k / 116k / 0.02 | 20.3k / 51k / 0.40 | 12.4k / 132k / 0.09 | 3.4k / 189k / 0.02 | 27.2k / 46k / 0.59 | 5.4k / 189k / 0.03 |
| (b) time stop 60 min uncond., cut off | 1201 | -0.1k / 67k / -0.00 | 5.8k / 189k / 0.03 | 9.8k / 104k / 0.09 | 22.8k / 87k / 0.26 | 18.8k / 87k / 0.22 | 8.4k / 207k / 0.04 | 26.3k / 87k / 0.30 | 10.0k / 207k / 0.05 |
| cut ON + time stop 30 cond. | 1723 | -1.8k / 53k / -0.04 | 9.9k / 74k / 0.13 | 11.4k / 81k / 0.14 | 29.8k / 51k / 0.59 | 22.3k / 144k / 0.15 | 11.9k / 74k / 0.16 | 41.2k / 51k / 0.81 | 13.2k / 81k / 0.16 |
| cut ON + time stop 60 cond. | 2340 | -1.9k / 59k / -0.03 | 13.8k / 77k / 0.18 | 15.4k / 89k / 0.17 | 34.5k / 63k / 0.54 | 27.2k / 115k / 0.24 | 14.4k / 77k / 0.19 | 43.6k / 63k / 0.69 | 16.8k / 89k / 0.19 |
| (c) emulation, empty mask (= ON) | 2520 | -0.2k / 49k / -0.00 | 13.8k / 75k / 0.18 | 17.0k / 71k / 0.24 | 35.3k / 63k / 0.56 | 27.9k / 122k / 0.23 | 15.2k / 75k / 0.20 | 43.5k / 63k / 0.70 | 17.7k / 75k / 0.24 |
| (c) emulation, plain-exit window blocked | 2518 | -0.1k / 49k / -0.00 | 13.9k / 75k / 0.18 | 16.9k / 71k / 0.24 | 35.3k / 63k / 0.56 | 27.9k / 122k / 0.23 | 15.1k / 75k / 0.20 | 43.5k / 63k / 0.70 | 17.7k / 75k / 0.24 |
| (d) re-entry pause 15 min after a cut | 2309 | 0.0k / 50k / 0.00 | 13.0k / 80k / 0.16 | 15.0k / 84k / 0.18 | 33.3k / 57k / 0.58 | 26.0k / 121k / 0.21 | 14.0k / 80k / 0.17 | 41.5k / 57k / 0.73 | 16.4k / 84k / 0.19 |
| (d) pause 30 min | 2035 | 0.8k / 48k / 0.02 | 12.9k / 87k / 0.15 | 13.5k / 59k / 0.23 | 28.2k / 33k / 0.85 | 22.3k / 134k / 0.17 | 12.9k / 87k / 0.15 | 33.8k / 33k / 1.02 | 14.9k / 87k / 0.17 |
| (d) pause 60 min | 1701 | 1.6k / 47k / 0.03 | 13.5k / 81k / 0.17 | 13.8k / 48k / 0.29 | 19.2k / 30k / 0.64 | 15.0k / 118k / 0.13 | 14.7k / 81k / 0.18 | 18.5k / 30k / 0.62 | 13.5k / 81k / 0.17 |

Reading: (b) every time-stop variant is below both ON and OFF in total ($1.40M-$1.89M conditional, $0.0M-$1.20M unconditional vs OFF $2.24M); in 2026 the conditional 30 and 45 minute stops are slightly above OFF (22.3k and 25.2k vs 21.7k) but 2023 and 2025 lose $2.5-10k/week; adding a time stop to the cut (ON+TC30, ON+TC60) lowers the total to $1.72M and $2.34M; no time stop reproduces the cut's 2026 maxDD/Calmar except the unconditional 30-minute stop on the short windows (L6M Calmar 0.59, 2026 Calmar 0.40) which pays for it with a $189k PRE maxDD. (d) a 15-60 minute pause after each cut lowers the total ($2.31M, $2.04M, $1.70M) and the 2026 gain (33.3k, 28.2k, 19.2k vs 35.3k) while shortening the 2026 drawdown (57k, 33k, 30k vs 63k): re-entry after a cut is where the profit is, not the cost. (c) the emulation changes nothing (C1 = ON within $2k).

## 3. What the extra trades are
Extra = taken in ON and not in OFF (1,779 trades; 246 trades go the other way). Why the OFF run did not take them: slot still occupied by a trade the cut closed early 6; the book's daily loss gate had already blocked entries that day 1,201 (2023 37, 2024 165, 2025 367, 2026 632); daily profit gate 88; other 484 (give-back arm, lock-R scaling, chained gate effects; not separable with the hooks). Per-book daily loss-gate blocks (OFF vs ON): KB 909 vs 263, PE 334 vs 72, MV 228 vs 47, HM 48 vs 3, SM 9 vs 0.
Validation of the emulation (c): empty mask equals ON exactly; the plain-exit mask removes only 24 signals; the emulated trade set differs from ON by 5 trades; versus OFF the emulated set still contains 1,776 trades that OFF does not: the extras are not inside the plain-exit windows.

## 4. Gate-off decomposition (ON minus OFF, $k; label-day years)
| variant | total $k | 2023 | 2024 | 2025 | 2026 | HOLD | PRE | L6M | ALL |
|---|---|---|---|---|---|---|---|---|---|
| gates as live: cut ON | 2520 | -0.2k / 49k / -0.00 | 13.8k / 75k / 0.18 | 17.0k / 71k / 0.24 | 35.3k / 63k / 0.56 | 27.9k / 122k / 0.23 | 15.2k / 75k / 0.20 | 43.5k / 63k / 0.70 | 17.7k / 75k / 0.24 |
| gates as live: cut OFF | 2243 | 0.4k / 81k / 0.01 | 11.3k / 175k / 0.06 | 21.8k / 94k / 0.23 | 21.7k / 91k / 0.24 | 19.9k / 91k / 0.22 | 14.8k / 175k / 0.08 | 23.5k / 90k / 0.26 | 15.7k / 175k / 0.09 |
| daily loss gate off: cut ON | 2460 | -0.5k / 49k / -0.01 | 13.6k / 75k / 0.18 | 17.0k / 71k / 0.24 | 34.2k / 55k / 0.62 | 26.9k / 140k / 0.19 | 14.8k / 75k / 0.20 | 42.1k / 55k / 0.76 | 17.4k / 75k / 0.23 |
| daily loss gate off: cut OFF | 2216 | 0.5k / 81k / 0.01 | 11.9k / 158k / 0.08 | 21.2k / 125k / 0.17 | 21.4k / 121k / 0.18 | 18.6k / 138k / 0.14 | 14.9k / 158k / 0.09 | 25.4k / 93k / 0.27 | 15.7k / 158k / 0.10 |
| daily loss+profit gates off: cut ON | 2429 | -0.5k / 49k / -0.01 | 13.7k / 75k / 0.18 | 16.6k / 71k / 0.23 | 33.6k / 55k / 0.61 | 26.4k / 140k / 0.19 | 14.7k / 75k / 0.20 | 40.9k / 55k / 0.74 | 17.2k / 75k / 0.23 |
| daily loss+profit gates off: cut OFF | 2190 | 0.5k / 81k / 0.01 | 12.3k / 156k / 0.08 | 21.1k / 123k / 0.17 | 20.1k / 121k / 0.17 | 17.6k / 166k / 0.11 | 15.1k / 156k / 0.10 | 24.8k / 93k / 0.27 | 15.5k / 156k / 0.10 |
| all day gates + give-back off: cut ON | 2488 | -0.5k / 49k / -0.01 | 14.0k / 90k / 0.16 | 15.9k / 71k / 0.22 | 34.7k / 55k / 0.63 | 27.3k / 149k / 0.18 | 14.2k / 90k / 0.16 | 41.9k / 55k / 0.76 | 17.3k / 90k / 0.19 |
| all day gates + give-back off: cut OFF | 2305 | 0.5k / 81k / 0.01 | 12.7k / 185k / 0.07 | 20.6k / 178k / 0.12 | 22.3k / 119k / 0.19 | 20.2k / 170k / 0.12 | 14.0k / 185k / 0.08 | 28.4k / 93k / 0.30 | 15.9k / 185k / 0.09 |

Trade-by-trade split (same trade in both runs / only with the cut):
| configuration | year | stack gain | cut rows (same trades) | non-cut rows | extra trades n / $k | extra $/trade | extra pts per lot | common pts per lot |
|---|---|---|---|---|---|---|---|---|
| live gates | 2024 | +136 | +85 | -47 | 240 / +103 | +429 | 8.2 | 3.1 |
| live gates | 2025 | -257 | -262 | +27 | 500 / -48 | -96 | -2.0 | 2.0 |
| live gates | 2026 | +388 | +201 | +31 | 998 / +113 | +114 | 1.3 | 1.7 |
| live gates | all | +277 | +93 | -46 | 1,779 / +162 | +91 | 1.4 | 1.9 |
| daily loss gate off | 2024 | +88 | +106 | -58 | 82 / +48 | +584 | 11.0 | 3.0 |
| daily loss gate off | 2025 | -201 | -252 | +19 | 139 / -1 | -9 | -1.5 | 1.8 |
| daily loss gate off | 2026 | +382 | +319 | +28 | 438 / +35 | +81 | 3.3 | 1.4 |
| daily loss gate off | all | +244 | +208 | -68 | 663 / +78 | +118 | 3.1 | 1.8 |
| all day gates and give-back off | 2025 | -214 | -159 | -53 | 47 / -2 | -42 | 1.7 | 1.6 |
| all day gates and give-back off | 2026 | +341 | +316 | -1 | 67 / +26 | +385 | 12.4 | 1.4 |
| all day gates and give-back off | all | +183 | +342 | -187 | 117 / +28 | +243 | 8.5 | 1.8 |
Answer to "how much is the cut and how much is the turnover": in 2026 the cut rows are +201k with the live gates and +319k with the daily loss gate removed; the extra trades are +113k with the gates and +35k without; so about two thirds of the live extra-trade value in 2026 is the gate interaction (the cut keeps day losses under the 2R gate so the book keeps trading) and the rest is more trades. In 2025 the sign is negative in every configuration (-$201k to -$257k) and comes from the cut rows (-$252k to -$262k): the turnover channel does not create the 2025 cost. The cut rows themselves are the dominant term in every year but their per-cut mean is ~zero (DS3_TH_MECHANISM), so the remaining stack-level effect on the same trades includes the engine mechanics identified there (70/30 add cancel, shifted entries, stop-cost frame, lock R).
Extra-trade quality, ON vs OFF: pts per lot of extra trades vs common trades in the same year: 2024 +8.2 vs +3.1 (240 trades); 2025 -2.0 vs +2.0 (500); 2026 +1.3 vs +1.7 (998). By book 2026: PE +4.6 (224, +$401/trade) vs 2.95, HM +16.6 (40) vs 3.7, KB -0.8 (588) vs 1.0, MV 0.0 (143) vs -0.6; 2025: KB -1.4 (258), PE -1.3 (153, -$172/trade), MV -6.2 (72). So the extra trades are "more trades in a good regime" in 2026 (equal to the common trades, except PE and HM where they are better), worse than common trades in 2025, and better in 2024.

## 5. Does a time stop capture the turnover benefit without the -30 cliff?
No. The turnover benefit is a gate effect (section 3), not a slot effect, and a time stop does not shorten the loss path the way a -30 exit does: the conditional time stops lose against OFF in 2023 and 2025 (-$2.5k to -$10k/week) and are roughly flat in 2024 (-$0.8k to +$2.3k) and add +0.7k to +3.6k in 2026 (30 and 45 minutes) or lose (20 and 60 minutes: -2.5k and -3.4k); their maxDD is larger than the cut's in every long window. They are also not smooth in N (2026: 19.1k, 22.3k, 25.2k, 18.2k for 20/30/45/60). The cliff in the arm (DS3_TH_OOS) is a property of exits that cap the loss in points; a time exit has a different cliff (the choice of N).

## Limits and unknowns
* Extras classified by the engine's logged gate days: "other" (484) is not separable with existing hooks. The PB book is outside the inject hook. The emulations (c), (d) use the ON run's cut set and OFF plain exits; they are not engine features.
* Results are single-path engine runs; yearly differences (2025 vs 2026) rest on 18-53 weeks; no confidence intervals were computed for the variant table.
* The daily loss/profit gates and give-back are the user's live locks (DIRECTIVE_USER_ANSWERS_20261102); turning them off is a diagnostic, not a recommendation.

## AMENDMENT 2026-11-04 (ZL-2, appended): clock correction for the time stops and the re-entry pause
The time stops (kx = kin + 60 N) and the pause emulation (kx + 60 N) were built in path-index units; the 1-second path holds only seconds with prints (1,800 indices = 60 real minutes in Asia, 48 London, 30 NY). Rebuilt with real seconds (RECON_PAUSE.md). Time stops, total $k (old -> real clock): conditional (no progress, <= 0) 20 min 1,400 -> 1,240; 30 min 1,489 -> 1,631; 45 min 1,777 -> 1,261; 60 min 1,886 -> 1,610; unconditional 20/30/45/60: -13/346/883/1,201 -> -195/-94/72/445; cut ON + conditional 30 / 60: 1,723 / 2,340 -> 1,959 / 2,011 (cut alone 2,520, TH off 2,243). Conclusion unchanged: no time stop captures the cut's benefit. Re-entry pause (cut ON, 2R gate, V0 base): pause 15 / 30 / 60 totals 2,309 / 2,035 / 1,701 -> 2,469 / 2,327 / 2,075; 2026 maxDD 57 / 33 / 30 -> 60 / 47 / 47; HOLD maxDD 121 / 134 / 118 -> 117 / 131 / 128. The claim that a 30-60 minute pause "shortens the 2026 drawdown to 30-33k" is withdrawn (real clock 47k); the main conclusion (the gate interaction, not slot occupancy, drives the extra trades; only 6 of 1,779 extra trades sat behind a cut-closed position) is unaffected (it used trade sets, not the pause window). Also: all "mean hold" minutes quoted from path-index differences (24 vs 39 min in 2026) are index units; the ratio (about 0.6) stands.

## AMENDMENT 2 2026-11-04 (ZL-2, appended; CLOCK_AUDIT_ZL2.md): hold durations
The quoted "mean hold 24 vs 39 minutes" (2026, cut ON vs OFF) was in path-index units; real minutes are 47.7 vs 76.7 (2026), 94.5 vs 145.2 (2025), 158.0 vs 214.0 (2024), 251.3 vs 309.9 (2023); the ratio (0.62 in 2026) is unchanged and the slot-channel analysis (trade sets, gate days) does not use durations.
