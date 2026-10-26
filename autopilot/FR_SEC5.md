## 5. THE PAIR ITSELF

Paths relative to `outputs/`; `AP/` = `autopilot/`. Live configuration: ST (ATR 120, mult 2.0, close, EMA200) + HM (HMA 20/55 of close minus session VWAP, reset 00:00 fixed UTC-4, slow-slope confirm, EMA200), 8/8 NQ, $20/pt, 60-pt stop = target, entries 18:00-15:00 ET except 09:00-09:58, flat at the 16:55 bar open, per-book 5R/-2R daily rule, combined day lock (cap 8R, arm 2R, give back 67%, from 00:00), combined week floor -8R, per-book week rule off, TH off; R = $9,600 per book; 1 tick/side + $34.88 per 8-lot trade; $700k. Engine = corrected NT8-faithful account model (netting, orphan protective orders, ET clock). Items marked **[unverified]** could not be traced to a primary report.

### 5.1 Baseline and the numbers that changed

| span | weeks | net | weekly Sharpe | max DD | worst week | source |
|---|---|---|---|---|---|---|
| clean 2023-08-01..2025-07-31 | 105 | $1,329,959 | **1.460** | $280,110 (40%) | -$81,874 | `AP/REPORT_EXTENSION_20261017.md` s3 |
| H1 2025-08-01..2026-02-06 | 28 | $593,797 | **2.828** | $151,713 (22%) | -$78,287 | same |
| H2 2026-02-07..2026-10-16 (extended) | 36 | $819,748 | **2.484** | $217,425 (31%) | -$82,524 | same |
| all-in 2023-08-01..2026-10-16 | 168 | $2,743,504 | **1.897** | $280,110 (40%) | -$82,524 | same |

All-in CVaR5 -$79,220, Sortino 3.71, MAR 9.79, 42.3% negative weeks (extension report; clean-process rebuild with `B.Cfg(wk_floor=8, wk_loss_pb=None)`).
- **The 2.30 / 1.86 figures are the 10-13 cut.** Through 2026-10-13: H2 2.30 ($761,254), all-in 1.86 ($2,685,011). The old H2 included a 2-hour 10-13 label day; the same span on the rebuilt rows reads 2.39, and the complete 10-13 day is +$10,211. The extension to 10-16 adds +$58,494 and gives H2 2.484 (36 weeks) and all-in 1.897 (168 weeks). Clean and H1 are unchanged (1.46 / 2.83). Some downstream reports still quote 2.30 / 1.86 / H2 to 10-13 (D3, B11, C6-N1, E9) and ~60 older scripts still hard-code 20261013 as the H2 end (extension report s6).
- **Two configurations, easy to confuse.** The described live config (combined -8R floor, per-book -6R week rule off) = 1.46 / 2.83 / 2.30 (all-in 1.86). `B.Cfg()` default (per-book -6R week rule on, no combined floor) = 1.35 / 1.65 / 2.26 (all-in 1.61; 1.350 / 1.653 / 2.458 / 1.655 on the extended span). Floor and per-book rule both on = 1.30 / 2.55 / 2.10; day lock only = 1.50 / 1.86 / 2.63 (`AP/DECISIONS.md` 2026-10-15 baseline entry; `b11/REPORT_WEEKFLOOR.md`, `REPORT_LIVE_CELL.md`). D1, B11-CAPS, B11-SIZING, D3 S3 (HM harness) and the engine-recon tables use the `Cfg()` baseline; D2, D3 S1/S2/S4/S5/S6 and the autopilot use the live one. E9 re-ran every D1 candidate on the live config.
- The 1-s series from 2023-02-10 is $2.81M (the extra Feb-Jul 2023 adds about +$127k by subtraction); SE2's control net of $2.95M is on a longer 1-s axis ending 10-16 (not reconciled to $2.74M here; **[unverified]** start date).
- Per-trade economics (D3 S6 baseline, to 10-13): 7,320 trades; win rate 50.8%; $160 per point at 8 contracts; net per accepted trade about $391 (SE1, 7,346 trades to 10-16).

### 5.2 Era dependence (2013-22): gross edge, cost, and scaled brackets

**Frozen live rules on NQ 2013-2022 (1-minute engine, C3-H2): net -$2,227,220, weekly Sharpe -0.78, max DD $2.52M, 7 of 10 years lose** (`AP/REPORT_C3_H2.md`; `AP/REPORT_P1.md`). By year (net $ / weekly Sharpe): 2013 -48k / -0.49; 2014 -163k / -1.09; 2015 +122k / 0.62; 2016 +22k / 0.13; 2017 +20k / 0.13; 2018 -330k / -1.18; 2019 -27k / -0.09; 2020 -614k / -1.43; 2021 -288k / -0.75; 2022 -921k / -2.09; 2023 +68k / 0.20; 2024 +1,005k / 2.18; 2025 +1,094k / 2.25; 2026 (to 10-13) +684k / 1.68. The loss is concentrated in 2018 and 2020-22 (2,800-3,700 trades a year, trend efficiency ~0.1). Parameters were chosen on 2023-26, so 2013-22 is a true out-of-sample test. Per book, HM lost in 2013-14, 2016, 2018-23 and ST lost in 2013-14, 2017-18, 2020, 2022; the 2023 split was HM -$198k, ST +$266k.
- Fidelity caveat: the 1-minute engine matches 11,779 of 13,089 live 1-s entries (90.0%), weekly correlation 0.88 (0.83-0.91 by span), net within about +-15% by span and optimistic for 2023 (Feb-Dec 2023: 1-min +$158k vs live engine -$10k); no netting or orphan orders. Read pre-2023 dollars loosely; the sign is not in doubt. Under Gate Amendment 2 (ERA) 2013-22 is reported, not gating.

**Gross versus cost (P1-DECOMP): the failure is a loss of gross edge, not cost eating an old edge** (`AP/REPORT_P1_DECOMP.md`):
- Price-scaled bracket (60 x price/20,000), 16,127 trades: gross move per trade +0.0003 R in 2013-22 (se 0.008, t 0.04) vs +0.036 R in 2023-26 (t 3.0). Live fixed 60-pt bracket: -0.016 R (t -1.9) vs +0.057 R (t 4.9). Gross yearly values swing +-0.06 R with no stable sign (2018 +0.053, 2022 -0.064).
- Fixed-dollar costs deepen the early loss: 0.05-0.08 R per trade in 2013-16 (the tick was 0.83 bp of price and the scaled bracket only 36-54 ticks) vs ~0.00-0.01 R in 2024-26; price-scaled costs alone would leave 2013-22 at about -0.01 R/trade. Net R summed over 2013-22: real cost -605 R, price-scaled cost -170 R; 2023-26 +227 R / +234 R.
- Four structural series (RTH share, MNQ share, NQ volume, NQ options share) do not track the pair's rolling 26-week gross Sharpe (|r| <= 0.20 in levels, 13-week changes and yearly values; MNQ share vs 13-week changes -0.40 flips sign vs levels +0.10). Not a test of cause: one regime change in the sample.

**Scaled brackets (P1, 3 scalings x 3 cost modes)** (`AP/REPORT_P1.md`; weekly Sharpe, 2013-22 / 2023-26):

| run | 2013-22 | clean | H1 | H2 | 2023-26 |
|---|---|---|---|---|---|
| a gross (bracket = 60 x price/20,000) | +0.06 | 2.05 | 2.68 | 1.31 | 1.62 |
| a real cost | -1.38 | 1.67 | 2.15 | 1.05 | 1.25 |
| a cost scaled to bracket | -0.38 | 1.71 | 2.21 | 0.99 | 1.28 |
| b gross (k x ADR20, k = 0.211) | +0.05 | 1.80 | 1.57 | 1.34 | 1.36 |
| b real / scaled | -1.57 / -0.31 | 1.51 / 1.57 | 1.44 / 1.32 | 1.23 / 1.03 | 1.13 / 1.12 |
| c gross (m x ATR120, m = 10.57) | -0.28 | 0.58 | 4.40 | 2.05 | 1.18 |
| c real / scaled | -2.04 / -0.79 | 0.31 / 0.31 | 4.04 / 3.98 | 2.01 / 1.89 | 0.90 / 0.89 |
| fixed 60 gross / real | -0.41 / -0.78 | 2.07 / 1.65 | 3.55 / 2.60 | 2.56 / 2.04 | 2.31 / 1.78 |

Scaling does not rescue 2013-22 and lowers the 2023-26 result (a 1.25, b 1.13, c 0.90 vs fixed 60 at 1.78): the live 60 pts is a 2023-26 parameter, not a price ratio that travels. Faithful scaling is (a); under it the pair also trades ~6 times a day vs 3.8 under fixed 60, and the extra trades are cost with no edge. A range-scaled bracket on the C3-H2 engine gave 2013-22 net -$6.26M, Sharpe -1.57. Fixed-60 numbers here are on the 1-min engine (1.78 for 2023-02..2026-10; the 1-s engine reads 1.72 on that span and 1.86-1.90 from 2023-08). P1 limits: 1-minute bars, stop-first, 1 tick/side with up to ~50 contracts at NQ 3,000 (liquidity not modelled, favours the scaled runs).

**What does not explain it:** none of 21 market-structure statistics tracks the pair's yearly Sharpe (max |rho| 0.45, p 0.11; 2023-26 within the 2013-22 range on 19 of 21; `AP/REPORT_C8_Q1.md`); regime switches on observables fitted 2014-22 fail (C6-N1: uplift -0.36 / -1.22 / -1.09); GEX sign tracks yearly gross Sharpe (rho +0.90, n = 8) only through the 2022 year and not weeks (rho 0.04) (`AP/REPORT_OPTIONS.md`); the cluster of index-futures fades found since shows the same era signature (net Sharpe -1.74 to +0.28, gross -0.48 to +1.23; `AP/REPORT_REGIME.md`). Most economical reading: the parameters are period-specific.
**Stand-down on trailing Sharpe (P2)** gains over 2013-26 only by being in cash through the no-edge era; in 2023-26 the effect is +0.32 (CI [-0.08, +0.78]) and -0.04 and false stand-downs cost ~$260k (`AP/REPORT_P2.md`).

### 5.3 Book attribution: HM carries about 90% of H1 and H2; ST is the weak book now

Live pair, per-book net after all locks (D3 S5; trades closed by exit trading day; totals clean $1,329,959 / 3,656 trades, H1 $593,797 / 1,187, H2 $778,359 / 1,742 to 10-13) (`d3/REPORT_D3_S5.md`):

| book | span | net | trades | $ per trade | share of span net |
|---|---|---|---|---|---|
| ST | clean | $739,597 | 2,062 | $359 | 56% |
| ST | H1 | $63,891 | 635 | $101 | 11% |
| ST | H2 | $74,592 | 889 | $84 | 10% |
| HM | clean | $590,361 | 1,594 | $370 | 44% |
| HM | H1 | $529,906 | 552 | $960 | 89% |
| HM | H2 | $703,767 | 853 | $825 | 90% |

- Rolling 26-week Sharpe under live rules (D3 S3): ST mean 1.20 clean, 1.84 H1, **0.11 in H2** (min -0.75, negative in 46% of H2 weeks); HM 1.18 / 2.67 / 3.17 (H2 minimum 2.56). The HM drawdown of Aug-Sep 2026 (section 5.9) did not show at the 26-week scale.
- Stability of the attribution across spans is low for every dimension available at entry: hour mean rank correlation -0.10 (35% of buckets same sign in all three spans), weekday -0.33, side -0.33. The only stable pattern is not usable at entry: trend-day class (rank correlation +1.00; trend days earn 232% / 86% / 113% of span net, chop days lose in clean and H2); side flips (long = 100% of clean net, short = 82% of H2 net). Hour 22 ET, trade-duration decile 1 and trend days are the stable under-exploited buckets (hour 22 is 2-5% of trades and 8-17% of net) (`d3/REPORT_D3_S5.md`).
- Era reading for the book split: HM was the research favourite (2.30 Sharpe on the retired harness) but the corrected HM has Sharpe 0.89 per book on clean vs ST 1.63 (zero slippage); H1/H2 are where HM earns (ENGINE_RECON, 5.10). The old h2 per-book table (HM H2 -$27k, ST +$142k) is from the retired harness and is superseded (`h2/REPORT_H2_BOOKS.md`).
- **EMA200 filters carry the pair.** EXEC_SUMMARY quotes "ST off = -93% net, HM off = -22%" **[unverified: stated only in `d3/EXEC_SUMMARY.md` and `AP/EXEC_SUMMARY.md`, no primary report found]**. What is verifiable: moving the EMA length one step is not free (D3 S1, net as a fraction of live): EMA 150 = 1.40 clean / 1.14 H1 / **0.38 H2**; EMA 250 = 1.08 / 1.20 / **0.68**; both fail H2. Marginal means over the 405-cell grid (net as a fraction of live) are EMA 150 = 0.84 / 0.96 / 0.69, EMA 200 = 0.54 / 0.88 / 0.94, EMA 250 = 0.68 / 1.05 / 1.00 (clean / H1 / H2), i.e. no length wins on every span; the HM-only surface prefers EMA 100-150 on all three spans (HM alone H2 Sharpe 2.73-2.74 at EMA 100/150 vs 2.17 at 200; `d3/REPORT_D3_S3.md` s2, `Cfg()` harness). Decision recorded: leave at 200 (the pair-level case for moving it rests on in-sample surfaces).

### 5.4 The day lock: regime-dependent (+clean, -H1, +H2)

Effect of the live combined day lock versus plain per-book rules, by span (`d3/REPORT_D3_S2.md` s1, day-level before the weekly stage; live-cell comparison in `b11/REPORT_LIVE_CELL.md`):

| span | days locked | cost days / save days | net effect of the lock | plain net | cap / give-back effect |
|---|---|---|---|---|---|
| clean | 210 (41%) | 101 / 109 | **+$149,437** | $1,266,413 | -$248,302 / +$397,739 |
| H1 | 51 (38%) | 30 / 20 | **-$422,339** (47% of plain H1 net) | $896,248 | -$36,193 / -$386,147 |
| H2 | 99 (56%) | 45 / 53 | **+$176,241** | $672,219 | +$852 / +$175,389 |

- Live cell vs plain (to 10-13): clean net +12%, Sharpe 1.13 -> 1.50, max DD -14%; H1 net **-47%**, Sharpe 2.66 -> 1.86, DD -10%; H2 net +26%, Sharpe 1.52 -> 2.63, max DD $214k vs $459k (-53%); all-in cost 3.4% of plain net, CVaR5 +17%, DD better by 27%. INSURANCE-flagged. With the per-book -6R week rule on and the lock on, H1 net is -52% vs plain and all-in -14.1% (`b11/REPORT_LIVE_CELL.md`). Lock off with per-book week rule on is worse than plain on clean (-19% net, Sharpe 0.91).
- Why H1 cost money: the lock's sign follows day character, not span. In all spans it costs money on high-range days (clean -$583k, H1 -$422k, H2 -$90k) and on trend days (top-third ER: clean -$789k, H1 -$174k, H2 -$265k) and saves money on low-range days (+$394k, +$210k, +$421k). H1 had more costly days (51% of H1 lock days were high-range vs 39% clean and 32% H2). Five H1 days account for 68% of the cost (-$289k): 2025-12-16, 2026-01-19, 2026-01-15, 2026-01-29, 2025-08-07; plain finished each of them +$55k..+$94k after the lock flattened a +2R..+7R day.
- Predictability: of 15 observables known at the lock minute, the best is equity at the lock in R (AUC 0.58, p 0.009, family-wise p 0.09; AUC 0.51 in H1 and 0.52 in H2); nothing separates H1 lock days from clean/H2 lock days (best trade count, family-wise p 0.22). The day character is only known after the day. The sign-flip by period matches the HM, netting and anchor results (same regime dependence).
- Re-tuning the lock fails (Section 3.4): 1,728-cell lock grid has no cell robust in every span; fixed cap-12R / arm-1.5R fitted on clean loses 32% of H1 and 21% of H2 net (`insurance/REPORT_INSURANCE_CORRECTED.md`, `d2/REPORT_D2_E8.md`).
- What the locks buy: with locks off (day lock and week floor removed, per-book rules kept) the bootstrap 8/8 median 12-month net is +5% ($901,862 vs $860,992) but P(DD > 30%) rises from 70% to 97%, P(DD > 40%) from 29% to 79%, P(losing year) from 1.1% to 3.7%, median longest recovery from 60 to 69 days (`d3/REPORT_D3_S1.md` 1c). The locks matter far more for drawdown than for net.

### 5.5 The combined week floor (-8R, $76,800)

- Fired 23 times (4 before the clean window, 13 clean, 2 H1, 4 H2); net effect by span: clean **-$85,891**, H1 **+$119,889**, H2 **-$87,205** (`d3/REPORT_D3_S2.md` s4). The H1 gain is one week: 2026-W04 (+$119,677; the week otherwise lost $196,610). The largest costs are weeks that would have recovered: 2024-W15 (-$128,754), 2026-W15 (-$90,580), 2023-W44 (-$85,238). It is insurance on single bad weeks, paid for by recoveries it cuts off.
- Versus the `Cfg()` baseline (`b11/REPORT_WEEKFLOOR.md`): floor -8R with the per-book week rule off is INSURANCE (all-in net +10.2%, CVaR5 +33%, worst week +58%, DD +11%; clean net +6%, H1 +39%, H2 +0%); -9R and -10R also INSURANCE; -7R is NO (clean DD $449k); the -8R floor with the per-book rule on is NO. The floor fires in 11.9% of traded weeks.
- It does **not** beat matched random weekly stops on net (200 draws, same firing rate): real dnet vs null p95 = clean +$77k vs +$275k, H1 +$168k vs +$195k, H2 +$3.6k vs +$198k; Sharpe uplift +0.11 / +1.17 / +0.03 vs p95 +0.32 / +1.45 / +0.89. Bootstrap of the weekly uplift excludes zero only in H1 (CI lo +$535 per week; Sharpe CI [0.11, 2.02]); clean and H2 straddle zero. Verdict across the reports: modest INSURANCE, effect mostly one H1 week. It is in the live config and the numbers above are with it.

### 5.6 Plateau (3% of 404 neighbours) and the re-fit result

**Plateau (D3 S1a, full joint neighbourhood: ST ATR {100,110,120,130,140} x mult {1.75,2,2.25} x HM {18/50, 20/55, 22/60} x bracket {55,60,65} x EMA {150,200,250} = 405 cells, 404 neighbours)** (`d3/REPORT_D3_S1.md`):
- Only **12 of 404 (3%) keep >= 90% of live net on clean, H1 and H2 simultaneously**; 94 (23%) do on clean, 230 (57%) on H1, 196 (49%) on H2; 55 keep >= 90% of live all-in Sharpe; 1 of 404 also keeps max DD within 1.10x. Median neighbour keeps 69% of live clean net (94% H1, 89% H2). Live's all-in Sharpe ranks **27th of 405**. The live cell is special only on clean (the span it was chosen on); on H1/H2 it is an ordinary neighbour.
- One-at-a-time failures (12 cells): HM 18/50 (0.76 / 0.47 / 0.42) and HM 22/60 (0.89 / 0.76 / 0.59) fail all three spans; bracket 65 fails all three (0.61 / 0.89 / 0.25, all-in Sharpe 0.96, DD $420k); bracket 55 and ST mult 1.75 / 2.25 fail clean; ST ATR 130 fails H1; EMA 150 / 250 fail H2. ATR 100, 110 and 140 are safe one-at-a-time. HM is the narrow-peak book.
- HM alone (fast x slow grid, `d3/REPORT_D3_S3.md`, `Cfg()` harness): live 20/55 ranks 42 of 53 on clean (0.90), 17 on H1 (3.01), 23 on H2 (2.17); the span surfaces are uncorrelated (Spearman -0.13 clean/H1, +0.06 clean/H2, -0.08 H1/H2), each span's best cell differs (22/70, 25/45, 15/80), so there is no optimum that drifted. In the pair, the 27-cell neighbourhood (fast 18-22, slow 50-60, EMA 150-250) keeps >= 75% of live Sharpe in 100% / 100% / 63% of cells (clean/H1/H2) and >= 90% of net in 74% / 93% / 56%.
- VWAP anchor and EMA length matter more than fast/slow: the 19:00 anchor beats the live 00:00 anchor in all 15 EMA x span comparisons for HM alone; live (EMA 200, 00:00) is among the weakest cells of the map. Descriptive; the anchor test failed 5 of 6 pre-set gates (`b11/REPORT_HM_ANCHOR.md`), research-HM variants reverse in H2 (`b11/REPORT_HM_VARIANTS.md`). Not adopted.

**Re-fit (D3 S4, walk-forward over the 405-cell grid, every 13 or 26 weeks on trailing 52 or 78 weeks, plateau-centred or argmax, 2,000-draw random-cell null)** (`d3/REPORT_D3_S4.md`):
- Plateau-centred re-fit earns 0.56-0.75x the live cell's OOS net (all-OOS), Sharpe 1.15-1.41 vs 2.05-2.10, max DD $345-364k vs $245k, worst week about equal; argmax is worse (0.24-0.64x, DD $552-636k). The live cell was chosen 0 of 62 times. The re-fit sits at the 24th-41st percentile of the random-pick null (argmax 1st-18th); the live cell sits at the 87th-95th (it is the in-sample winner).
- Fair read on untouched data (H1/H2): the re-fit keeps 71-89% of live net with Sharpe lower by 0.2-1.1; indistinguishable from picking a random neighbour each quarter. **Do not adopt re-fitting.** Limits: +-25% box around live, zero switching cost (flatters the re-fit).

### 5.7 Sizing table and drawdown probabilities

Sizing is linear (contracts per book; rules defined in R, so thresholds scale with size; D3 S1 and EXEC_SUMMARY, all-in to 2026-10-13; max DD % of $700k):

| size | all-in net | max DD | worst week | bootstrap median 12-month net | P(DD>30%) | P(DD>40%) | P(DD>50%) |
|---|---|---|---|---|---|---|---|
| 4/4 | $1.34M | $140k (20%) | -$41k | $430k | 3.8% | 0.4% | 0% |
| **6/6** | $2.01M | $210k (30%) | -$62k | $646k | 29.0% | **7.3%** | 1.9% |
| **8/8 (live)** | $2.69M | $280k (40%) | -$83k | $861k | **69.7%** | **29.0%** | 10.6% |
| 10/10 | $3.36M | $350k (50%) | -$103k | $1,076k | 91.7% | 59.0% | 29.0% |
| 12/12 | $4.03M | $420k (60%) | -$124k | $1,291k | 98.3% | 82.3% | 53.4% |

Post-extension (to 10-16) at 8/8: all-in net $2,743,504, max DD $280,110, worst week -$82,524 (extension report); 6/6 is 0.75x of that by linearity (about $2.06M, DD about $210k, worst week about -$62k; **derived, contract rounding and R-based locks ignored**). The bootstrap and sizing tables were not re-run after the extension **[unverified for the 10-16 span]**.
- 12-month block bootstrap (10,000 draws of 4-week blocks from 828 trading days, 2023-08..2026-10-13): at 8/8 median net **$860,992** (p5 $246,339, p95 $1,539,753), **1.1% chance of a losing year**, 44% chance of at least one losing quarter, P(DD>20%) 98.3%, **P(DD>30%) 69.7%, P(DD>40%) 29.0%**, P(DD>50%) 10.6%; median longest recovery 60 trading days (p90 121); 83.6% of paths end the year below their prior peak. Locks off: P(DD>40%) 79.1%, P(loss year) 3.7%.
- Largest size with P(max DD > limit) <= 10%: **6/6 for the 40% limit** (continuous 6.32, P = 7%, median net $645,744) and **4/4 for 30%** (continuous 4.74, P = 4%); locks off 3/3 and 2/2. Live 8/8 exceeds both. n* is +-1 contract per book (3-year, one-path sample; the 3-year window is the pair's best).
- Forward bootstrap with sleeves (SI1, 20,000 draws of 4-week blocks, 168 weeks 2023-08..2026-10 = the pair's best window; only the ordering between books is robust): P(DD > $200k) at 13 / 26 / 52 weeks = pair 8/8 **0.104 / 0.244 / 0.462**; pair 6/6 (0.75x) **0.025 / 0.079 / 0.190**. P(DD > $280k) at 52 weeks 0.156 (8/8) vs 0.036 (6/6). P(>= 8 of 13 weeks positive) 0.50. 52-week median net $844k (8/8) vs $633k (6/6). Share of weeks below -$25k: 25.6% vs 22.0% (`AP/REPORT_SI1.md`).
- Slippage ladder (all-in to 10-13; net / Sharpe): 0 ticks $3.21M / 2.16; 0.5 $2.96M / 2.01; **1 (live) $2.69M / 1.86**; 1.5 $2.40M / 1.64; 2 $2.16M / 1.49; 3 $1.48M / 1.02. Each extra tick/side costs about $280k (10%) and 0.2 Sharpe; clean is the most sensitive span (1.70 -> 0.65 from 0 to 3 ticks). Live fills file still not received; everything is 1 tick/side.
- Not comparable: `b11/REPORT_SIZING.md` (8/8 clean DD $316k = 45%, all-in 1.61) is the `Cfg()` baseline. Margin is unverified: intraday $1.5k per NQ puts the 16-contract pair at 3-7% of the account; exchange-style $20k per NQ puts it at 46% (SI1 **[unverified, assumed margins]**).
- Reading: 6/6 is the robust, low-assumption risk cut (no new edge assumption; at 25% of the sleeve's backtest edge only the constant-risk 70/30 pair/VC-arm blend (0.16) beats 6/6 (0.19) on P(DD>$200k), SI1; additive sleeve books are worse than the pair there).

### 5.8 Lever ranking (what would move the result)

D3 S6 (all-in to 10-13; exact re-run for fills, Globex size and trade removal, post-rule transform for win/loss levers; random items mean of 40 draws) (`d3/REPORT_D3_S6.md`):

| lever | all-in dSharpe | net | worst week | max DD | consistent across spans |
|---|---|---|---|---|---|
| +5 points win rate (50.8% -> 55.8%) | +3.46 | +190.8% | +$13.7k | -$158k | yes |
| -10% average loss | +1.74 | +93.4% | +$8.7k | -$96k | yes |
| +10% average win | +1.62 | +106.2% | +$0.7k | -$72k | yes |
| 1 tick better fills (1 -> 0 ticks/side) | +0.30 | +19.4% | +$1.4k | -$15k | yes |
| 10% fewer trades, worst-expectancy (book, hour, side) groups ranked on clean | +0.04 (H1 -1.26) | +4.2% | +$3.5k | -$28k | no |
| 10% fewer trades, random (control) | -0.07 | -12.7% | +$3.2k | -$11k | no |
| Half-size Globex | -0.66 | -39.9% | +$3.1k | +$138k (worse) | no |

- Win rate is by far the strongest lever and the system is extremely sensitive to it: with a symmetric 60/60 bracket each flipped stop is worth 120 points; one win-rate point is about 0.9 pt per trade (about $1.0M, roughly 38% of all-in net). The same sensitivity runs the other way: a one-point fall in hit rate costs roughly a third of net. Entry filters or exits that move the hit rate by 1-2 points matter more than any sizing or lock tweak, but every filter and exit tested failed out of sample (Section 3.1-3.2).
- The only lever execution can reach is fills (1 tick = +0.30 Sharpe, +19% net, consistent in all spans: clean +0.24, H1 +0.75, H2 +0.21); E5 found no limit-entry scheme that works, so it is lower real slippage, which the live fills will measure. Fewer trades and Globex trimming are not levers. Where to put effort: (1) anything that raises win rate or trims losers OOS (largest, nothing has passed), (2) fills, (3) leave Globex sizing and trade trimming alone. Win-rate flips are random among losers (not skill-based); levers are applied to the locked trade list and do not re-trigger locks.

### 5.9 HM early-warning threshold (late-summer 2026 drawdown)

(`d3/REPORT_D3_S3.md` s6-7; n = 1 event, not an estimated detection rate; thresholds are quantiles over 2023-08..2025-12.)
- Event: HM book without rules (NT8-list view) peaked on the week ending 2026-08-09 and bottomed 2026-09-13: **-$238,516**, nearly all in the five weeks after the peak (-$4k, -$51k, -$80k, -$37k, -$67k). NT8 list cumulative HM from 2026-02-07: peak 2026-05-17 to trough 2026-09-13, -$369,266. Inside the live-ruled pair the same episode is -$88,308 (peak 2026-07-19, trough 2026-09-13): the per-book and day rules absorb roughly two thirds.
- **8-week Sharpe red line (10th percentile, raw HM: -2.65; ruled HM: -1.76; yellow, 20th percentile: -1.40 raw): fired 2026-09-06, 28 days after the peak, one week before the trough, with 72% of the loss already booked; yellow fired 2026-08-30.** About 1.25 false-alarm episodes a year in the reference (red, raw), 2.09 for yellow; one alarm falls in H1 (a false one) for red/raw. The ruled-HM version fires 2026-09-13 (100% booked) at red and 2026-09-06 (89%) at yellow.
- Fast statistics fire earlier at higher false-alarm cost: last-50-trades win rate (red <= 0.44) and last-50 average points (red <= -7.16 pt) fired 2026-08-30 / 2026-08-23 (14-21 days after the peak, 23-57% booked) but with 2.5-3.3 false episodes a year. Slow statistics (26-week Sharpe, 13/26-week win rate, 26-week average points) never crossed their 10% lines; trades per day did not change: the drawdown is a payoff problem, not an activity problem.
- Use: the 8-week Sharpe red line is a confirmation display (about 4 weeks into a drawdown); last-50-trade stats a yellow watch. **None of this is evidence for a stop rule**: the rules already live cut the episode to about one third, and the walk-forward HM-health switch fails (C11-HM: +0.20 / -0.32 / -0.23). Threshold table for the monitoring dashboard is in `d3/REPORT_D3_S3.md` s7.

### 5.10 Latency fragility (SE1, SE2): the pair is sensitive to the exact fill second

Delay of every market entry by d seconds, 1-second order-level engine (`AP/REPORT_SE1.md`, `AP/REPORT_SE2.md`; control reproduces 1.46 / 2.83, H2 2.48, all-in 1.90):

| delay | clean | H1 | H2 | all-in Sharpe | P(worse) vs control (week-block bootstrap) | all-in net change (SE1 account re-run) |
|---|---|---|---|---|---|---|
| 0 (control) | 1.46 | 2.83 | 2.48 | **1.90** | | |
| 1 s | 1.48 | 3.17 | 2.02 | 1.86 | 0.60 | -$54k |
| 2 s | | | | 1.58 | | |
| 5 s | 1.33 | 3.07 | 0.80 | 1.47 | 0.93 (CI [-0.96, +0.05]) | -$459k (SE2: -$464k, -16%) |
| 15 s | 1.19 | 2.01 | 1.62 | 1.43 | 0.95 (CI [-0.98, 0.00]) | -$656k (SE2: -$662k, -22%) |
| 30 s | 1.12 | 1.61 | 1.07 | 1.20 | 0.98 | -$1.18M (SE2: -$1.26M, -43%) |
| 60 s | 1.37 | 1.13 | 1.03 | 1.25 | | -$963k |
| 120 s | 1.17 | 2.50 | 2.80 | 1.79 | | +$114k |
| 300 s | 1.13 | 1.97 | 2.46 | 1.59 | | -$519k |

- **Not price drift.** Signal-level fill drift is +$8.2 per signal at 1 s (+0.05 pt) and has no consistent slope to 300 s (+$17.9 at 300 s, sign alternates; 3 of 10 delays differ from zero at 1.96 se; 50,199 signals; pair nets about $391 per accepted trade); the 60-pt bracket re-centres on the fill, and stop/target ordering inside a second never matters (0 events). The non-monotone curve (120 s better than 60 s) is itself the signature of fragility.
- **Mechanism (SE2, diffuse):** at 5 s timing/path -$201k and drift incl. re-centred brackets -$263k; at 15 s -$179k / -$483k; at 30 s -$60k / -$1.20M. FIFO lot-closing reassignment between the two books, acceptance / netting changes (-$0.21M at 5 s), and sizing/lock rules changing on 667 events at 5 s (a different trade moves a day or week lock) carry the loss; the top 20 events carry only 2-3% of the gross change; top 3 hours 28-40%.
- Fill-second noise: a random 0 / 1 / 2 s delay per signal gives mean Sharpe 1.71, sd 0.15, so about 0.2 of the 1.90 is probably fill-second luck; the true cost of 15 s is about 0.3-0.5 Sharpe.
- **No fix:** SE1 11 cells and SE2 tolerance family are all NO; tol4 is a LEAD at 15 s only and is below the undelayed Sharpe everywhere. **Proposed latency gate (SE2):** median bar-open-first-print to NT8 fill <= 1 s, p95 <= 2 s; alarm at median > 2 s; stop and fix at > 5 s; about 200 live fills (about 4 weeks) settle it; log bar-close time, first print, SubmitOrder, Rithmic ack, OnExecutionUpdate. The existing `emission_latency` file measures model emission, not NT8 fills. MBO_VS_PAIR notes the real gate admits 97-100% overall but slow setups admit only ~13% in their worst ET hour (`h2/REPORT_MBO_VS_PAIR.md`).

### 5.11 Engine reconciliation (what the harness got wrong, and what the live account does)

(`h2/REPORT_ENGINE_RECON.md`, `h2/REPORT_FILLRECON.md`)
- FILLRECON first rejected the hypothesis that NT8 fills targets at touch while the harness needs trade-through: on 1,998 matched same-book bracket trades, 98.8% have the same exit type, targets +60.0 vs +60.0, stops -60.3 (NT8) vs -60.0 (stops fill through gaps in NT8, min -107 pts in one row). The 3x gap in total points (NT8 5,074 vs harness 1,571) came from WHICH trades were taken: only 72% of NT8 entries had a harness trade within 2 minutes (ST 85%, HM 54%).
- ENGINE_RECON found the harness differed from NT8 in four places, three in HM/entry logic: (1) HM VWAP reset at the session label vs NT8's 00:00 fixed UTC-4; (2) a second "slope" confirmation applied through `_post/_conf` that removes about a third of NT8's HM flips; (3) entry windows 18:05 start, 09:00-10:00 guard, 16:40 close on a fixed UTC-4 clock (an hour off every winter) vs NT8's 18:00-15:00 except 09:00-09:58 and flatten at the 16:55 bar open; plus (4) the account behaviour: an entry opposite to an open lot closes the oldest opposite lot at the entry price (309 rows) and the swallowed entry's protective orders stay working and can open unintended positions ("orphans": 309 of 3,941 NT8 H2 rows, 7.8%, -811 pts = -$141k at zero slippage; 299 stop-origin rows win 66% but average -2.6 pts; excluding them NT8's H2 would be +$815k vs $674k).
- Match after all fixes: **97.2% of ST and 97.7% of HM trades** (98.2% / 98.5% with NT8's own signal flags); exit-name agreement 96.7%, same-name rows reproduce exit prices to 0.006 pt per row; rows 3,947 simulated vs 3,939 NT8. ST math (ATR120 Wilder, mult 2.0, EMA200) matches NT8 with max difference 0.0000; HM (HMA, VWAP) matches to 0.0001 on 100% of bars after the reset fix; bars match: close exact on 96.7%, volume on 95.2% (3.3% of bars differ by a tick or a few contracts: Databento prints vs NT8 feed, not removable without NT8 tick data; 99% target not met).
- **Consequence for the baseline:** the research clean-period weekly Sharpe 2.74 (B10; 2.79 B8) is retired. Corrected plain pair: 1.12 raw / 1.35 with the live-style rules at 1 tick/side (1.55 / 1.83 at zero); raw all-in 1.46, per-book rules only 1.43, LIVE baseline (per-book + give-back + cap) all-in 1.61 under the `Cfg()` config. Per book, clean raw zero slippage: ST 2.80 -> 2.37 pt/trade (Sharpe 1.98 -> 1.63), HM 3.96 -> 1.53 pt/trade (Sharpe 2.30 -> 0.89): "more trades, much less edge". H1 and H2 do not decay in the corrected engine (raw 3.9 and 1.5 at zero slippage): the 2026 "weakness" was partly a harness-HM artefact, and the long-run edge is smaller than the research said. Everything built on the retired HM (B3 books, B8-B10 overlays, insurance work on the HM book) is void or was re-run (Section 3.0).
- Open: the orphan-order model reproduces NT8 rows, but whether the **live** account shows orphans must be checked against `LIVE_<acct>_trades_Sep1_Oct15.csv` (not received); if it does, they cost about $141k per 36 weeks at zero slippage before rules and are a DualStrat bug (cancel working protective orders of a swallowed entry). Under the live rules the orphan fills themselves are small (+$5k clean, -$10k H1, +$35k H2, `b11/REPORT_NETTING.md`), and removing the defect is not separable from changing exit behaviour (V4: clean -39%) (`b11/REPORT_NETTING_V4.md`).

### 5.12 What moves NQ minute to minute (DRIVERS)

(`AP/REPORT_DRIVERS.md`; 1-minute NQ/ES signed volume 2013-2026; R2 of the 1-minute NQ return, period means 2014-22 / 2023 / 2024-26.)
- **Same-minute ES return: 75.0% / 81.8% / 85.0%** (by year 66.7% in 2014 to 89.7% in 2025): NQ is priced off ES inside the minute (an arbitrage identity, not a forecast); it tightens after 2022.
- **NQ's own signed aggressor volume alone: 43.1% / 49.8% / 42.3%**; adds only 2-5 points once ES is known (ES return + NQ flow 79.7% / 84.4% / 87.1%). **ES signed volume alone: 31.1% / 30.3% / 23.8%**, adding about zero beyond NQ flow and ES return (everything: 73.6-91.1% by year).
- Lagged flow (1, 5, 15 minutes) and lagged return explain under 0.3% in every year (lag-1 return up to 0.21% in 2014): the minute ahead is not forecastable from flow.
- Signed-flow autocorrelation is short (mostly under 5 minutes, lag 1 about 0.10 falling to 0.06 in 2026); same-sign run lengths are 0.93x the independent expectation in 2013, 1.00x in 2018-19, 1.01-1.03x in 2021-26 (RTH 1.03-1.05x); a weak metaorder footprint exists only in the cash session and only since about 2019; nothing at 15-60 minutes.
- Price impact is permanent (no decay out to 60 minutes) and about 2-4 bp per 100 contracts in every year: $0.09 per contract of net flow in 2013 and $1.46 in 2026, purely because the index is 9x higher. The share of pair flips entered in top-third 30-minute imbalance fell from ~70% in 2013 to ~20% since 2020 (quoted from EXEC_SUMMARY; **[not re-checked in the DRIVERS tables]**).
- Gamma: short gamma doubles 1-minute volatility but autocorrelation differs by < 0.015; pair P&L by gamma sign is unstable (short gamma lost on clean and earned in H1/H2) (`AP/DECISIONS.md` DRIVERS entry; OPTIONS).
- **Usable conditioning variable for the pair: not yet.** NQ flow persistence at the flip (BLOCK PERS30, cut flips entered in the top two thirds of 30-min persistence, ET-block-relative) is a LEAD: +0.72 / +0.77 / +0.75, passes matched null and 2x slip, but BOOT lower bound -0.06, PLAT 1 of 4, H0 and alternating months fail, ERA negative pre-2023; two other top-3 cells reversed in H1/H2. A first stage-1 grid had a look-ahead (+1.28 spurious) and was discarded. Not FOUND; PERS30 cannot be confirmed by weekly P&L (Section 3.13).

### 5.13 W42 and the newest weeks (live result)

- **Week 2026-W42 (10-12..10-16): pair +$38,045** (daily: 10-12 -$3,344; 10-13 +$10,211; 10-14 +$7,860; 10-15 +$16,436; 10-16 +$6,881). The three post-freeze days (10-14..16) are +$31,177. Preceding weeks W40 -$15,630 and W41 -$54,750, so the last three weeks net -$32,335. VIX +21% on Fri 10-16 (16.46 -> 19.99); the pair made +$6.9k that day (`AP/REPORT_EXTENSION_20261017.md` s3, s6).
- Caveat: this is the engine replay of the live rules on Databento trades (rows regenerated through the unchanged `er_gen` / `nt8sim` account model), not reconciled to broker fills; the live-fills file has not been received. With 0.6 of a week post-freeze it carries no inference for any forward-tested lead (all 8 refreshed leads inside their weekly 90% intervals; BTC WT and Q20 RTY below band, kill-watch needs >= 6 weeks).
- Data cost of the weekly extension: $6.02 of the $120 family cap; Databento total $6,938.18 of $8,000.

### 5.14 Short list: what the pair is and is not

1. A good cell in a regime, not the centre of a plateau: 3% of neighbours keep 90% on all spans; HM carries ~90% of H1/H2; the optimum is not stable across spans; re-fitting does not help.
2. Edge window 2023-26 only (gross, before cost); 2013-22 gross is ~0 under every scaling; no observable explains it.
3. The two live protections are insurance with sign-flipping value: day lock +clean / -H1 / +H2 (cost ~3% of all-in net, DD better); week floor mostly one H1 week and not above a random-stop null.
4. Fragile to fill timing (1.90 -> 1.47 at 5 s -> 1.20 at 30 s) and to hit rate (one point of win rate is ~38% of net); resilient to slippage (still positive at 3 ticks/side).
5. At 8/8 a >30% drawdown in a year is 70% likely and >40% is 29%; 6/6 holds the 40% case at 7%, 4/4 the 30% case at 4%.

DONE FR_SEC5
