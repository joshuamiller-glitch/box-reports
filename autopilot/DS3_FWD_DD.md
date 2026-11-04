# DS3_FWD_DD: forward drawdown distribution of the live stack (DIS-V)

Author ZL-2. Frame of every number: Q1-A ts2 live-stack weekly P&L at live lots, net of fees/slippage, with the corrected carrying weeks; 187 weeks (2023 W14 to 2026 W44), total $2,520,149, mean $13,477/wk, sd $34,205/wk, worst week -$62,576. Weekly resolution (intra-week drawdown is understated). Observed references: HOLD maxDD $122,025; HOLD_dropH and L6M $104,809; PRE $88,180; X' $80,802. "x" = multiple of the $122,025 HOLD maxDD.

## Scope (prereg, logged before any output was read)
Risk measurement, not a hypothesis test. No PASS claim; nothing live. Scope note l2vast/ds3/prereg/DISV_scope.md, sha256 a8b1bfc4b43f471203815ee8f2e4853ada53b59bd89b3904db26eb0fb023ce84 (in DECISIONS.md). Method: Politis-Romano stationary block bootstrap of weekly P&L, 20,000 paths, seed 2026, horizons 13/26/52 weeks, joint resampling of the stack with the bundles (same calendar weeks).

## Block length and why
Mean block length L=4 weeks (main tables). Weekly stack P&L autocorrelation lags 1-8: .108 .195 .008 .050 -.012 .030 -.040 -.060 (2/sqrt(n)=.146), so only lag 2 is marginally significant. |P&L| (volatility clustering, which drives drawdown depth) lags 1-8: .219 .205 .108 .191 .011 -.024 -.085 -.092, above 2/sqrt(n) at lags 1-4. The Politis-White automatic selector returned 0 (degenerate, sample too short), so it gave no guidance. Disclosure: I first set L=2 (clip floor) and moved to L=4 after seeing the |P&L| lag-1-4 clustering, i.e. after seeing the first table; the L-sensitivity below is therefore reported in full. Longer blocks lower the tail: all-history stack, 52 weeks, maxDD median/p90/p99 ($k): L=1 93.3/156.8/237.6; L=2 93.1/155.6/236.9; L=4 92.2/147.8/214.8; L=8 92.2/136.0/196.8 (P>150k .121/.119/.094/.061). Medians are insensitive; the p99 range across L is $197k-$238k. Treat the p99 as having about +-$20k method uncertainty. 187 weeks is also short for L=8 blocks (few distinct blocks), so L=8 is not obviously more right.

## Main table, stack alone, all-history pool, by horizon
| horizon | maxDD median / p90 / p99 ($k) | x HOLD (med/p90/p99) | P>100k / >150k / >200k | share of weeks under water | longest underwater run, median (wks) | worst week median / p10 ($k) | P(any week < -40k) |
|---|---|---|---|---|---|---|---|
| 13 w | 49.4 / 101.2 / 154.5 | .40/.83/1.27 | .102 / .012 / .001 | .52 | 4 | -42.8 / -62.3 | .51 |
| 26 w | 75.1 / 122.2 / 187.7 | .62/1.00/1.54 | .232 / .042 / .006 | .55 | 7 | -44.9 / -62.6 | .76 |
| 52 w | 92.5 / 148.7 / 217.9 | .76/1.22/1.79 | .442 / .095 / .019 | .56 | 10 | -61.7 / -62.6 | .95 |

Read: over a year, a drawdown as deep as the observed HOLD one ($122k) is roughly a 1-in-3 to 1-in-4 event on the all-history pool (P(>100k)=.44, P(>150k)=.095), and the stack spends more than half of all weeks below its running peak even though its mean is positive.

## Scenarios, 52 weeks, stack alone (maxDD $k median / p90 / p99; P>100k / 150k / 200k)
| scenario | median / p90 / p99 | x HOLD | P>100k / 150k / 200k |
|---|---|---|---|
| (a) all history | 92.5 / 148.7 / 217.9 | .76/1.22/1.79 | .442 / .095 / .019 |
| (b) 2023-25 only (143 w) | 80.5 / 124.1 / 183.8 | .66/1.02/1.51 | .241 / .039 / .005 |
| (c) 2026 only (44 w) | 122.0 / 181.7 / 263.3 | 1.00/1.49/2.16 | .764 / .209 / .058 |
| (d) mix p=0.25 | 88.2 / 143.5 / 219.6 | .72/1.18/1.80 | .371 / .083 / .018 |
| (d) mix p=0.50 | 99.2 / 155.1 / 242.1 | .81/1.27/1.98 | .495 / .117 / .032 |
| (d) mix p=0.75 | 122.0 / 170.1 / 251.5 | 1.00/1.39/2.06 | .634 / .165 / .046 |
| (d) p=1 = never leaves 2026 regime | 122.0 / 182.5 / 264.6 | 1.00/1.50/2.17 | .763 / .213 / .061 |
| (d) p=0 = 2023-25 only | = (b) | | |
| DIS-U duration, point hazard 1/27 per wk | 100.6 / 155.8 / 244.0 | .82/1.28/2.00 | .504 / .117 / .031 |
| DIS-U duration, 95% upper hazard 0.13 per wk | 87.7 / 136.9 / 209.3 | .72/1.12/1.72 | .334 / .063 / .013 |

Mixture mechanics: each path starts in the 2026 regime pool and each week persists with probability p (mixture) or leaves at the stated hazard (duration variants), after which it draws from the 2023-25 pool. DIS-U duration prior: ZL-1's DIS-U interim says one regime in 3.6 years, no earlier episode, duration unbounded above; I therefore used a stated range (hazard 0 = never leaves, 1/27 = one exit per about 27 weeks as point, 0.13 = upper) rather than a fitted prior, and will re-run if ZL-1 delivers a prior. The 2026 regime is the worse one for the stack alone, because its weekly sd is higher and early-2026 produced the HOLD drawdown; the 2026 median 122.0 equals the HOLD maxDD only by coincidence of the 44-week pool being the HOLD window's main contributor.

Horizons 13 and 26 weeks, same scenarios, are in the full log (scratchpad fwd_dd2.log; columns identical). Headline 26 w, stack: all 75.1/122.2/187.7; 2023-25 71.4/104.2/159.0; 2026 94.2/148.6/227.1 (P>150k .096); mix p=.5 76.1/130.5/208.2. 13 w: all 49.4/101.2/154.5; 2026 62.6/122.0/188.6.

## Bundle (DIS-T watch bundle, equal-risk 1x) and NY-AM fade bundle on/off, 52 weeks
| scenario | stack | +watch bundle | +fade bundle | +both |
|---|---|---|---|---|
| all history, med/p90/p99 | 92.5/148.7/217.9 | 80.8/121.9/177.0 | 102.1/157.9/231.4 | 85.7/138.9/202.1 |
| all history P>100k/150k/200k | .442/.095/.019 | .218/.032/.004 | .531/.123/.030 | .341/.069/.011 |
| 2023-25 | 80.5/124.1/183.8 | 78.4/119.0/172.8 | 93.0/150.3/222.8 | 90.7/143.6/211.7 |
| 2026 | 122.0/181.7/263.3 | 80.8/111.8/158.8 | 108.1/159.1/231.7 | 84.1/108.9/162.0 |
| mix p=.5 | 99.2/155.1/242.1 | 80.8/113.9/163.8 | 103.1/153.5/226.5 | 84.1/131.0/194.7 |
| duration point 1/27 | 100.6/155.8/244.0 | 80.8/115.4/167.2 | 102.7/156.6/233.9 | 84.1/134.5/197.3 |

Also at 0.5x bundle risk: see log. Read, and caveats: (1) the watch bundle shrinks the 2026-regime tail by about a third (p99 $263k to $159k), but 92% of the bundle's P&L is 2026 (DIS-T) and the bundle was selected in-sample on the same weeks, so this is an upper bound on the benefit; in 2023-25 the bundle barely helps (p99 183.8 to 172.8). It also is a regime-contingent offset: in the 2026 pool its sample covers the exact weeks the HOLD drawdown occurred. (2) Adding the NY-AM fade bundle on top of the stack raises the drawdown tail in every scenario (all history 52 w p99 217.9 to 231.4; P>150k .095 to .123), i.e. it does not diversify the stack on this evidence; with the watch bundle also present the tail sits between stack alone and stack+fade. (3) Bundles are trade-list based, so their numbers do not depend on the pending AUDIT-PLC relabelling; that audit changes labels (placebo p-values), not P&L.

## Dependence on the carrying-weeks correction
Sensitivity by removing weeks from the all-history pool (stack; 26 w / 52 w, median/p90/p99 $k, P>150k):
| pool | 26 w | 52 w | weekly mean / sd of pool |
|---|---|---|---|
| full history | 75.1/122.0/188.7, .037 | 92.2/148.2/215.8, .095 | 13,477 / 34,205 |
| corrected episode weeks removed (2025 W06-09, 2026 W06-08 and W29-39, 2023 W21-41: 39 weeks) | 62.6/91.0/145.0, .008 | 74.0/111.1/160.8, .018 | 17,716 / 34,127 |
| OLD wrong PRE constant weeks (2024 W34-51) removed, real PRE kept (53 weeks) | 65.1/96.1/153.5, .011 | 80.5/115.9/169.4, .025 | 17,463 / 35,061 |

The distribution is strongly dependent on which weeks are in the pool: dropping the 39 episode weeks cuts the 52-week p99 from $216k to $161k and P>150k from .095 to .018. That tests how much of the tail comes from those weeks (most of it), not how wrong the correction is. Weekly sd barely changes, the mean rises, so it is the loss clusters within the episodes (serial correlation) that drive the tail. If the corrected weeks are removed because they are carrying-week artefacts, the stack's forward tail is about 25% thinner; if they are real, the main tables stand. I use the corrected series as the main series because the correction was an audited fix, not a choice.

## Comparison to observed worst episodes
Observed HOLD maxDD $122,025 sits at about the bootstrap p90 for 26 w (all-history 122.2), about the 78th percentile at 52 w (P>100k .44 and P>150k .095 bracket it), and at the median of the 2026-pool and never-leaves scenarios at 52 w. HOLD_dropH/L6M $104,809 and PRE $88,180 are around the bootstrap medians (52 w all-history 92.5). X' $80,802 is below the median. So observed history is not unusually unlucky; a drawdown of 1.5x HOLD ($183k) at one-year horizon has probability about .10 all-history, .21 if the 2026 regime persists.

## Limitations
- 187 weeks, a single regime change; mixtures are scenario devices, not estimates. p is not identified (DIS-U: duration unbounded above).
- The worst-week distribution is floored by the pool minimum (-62.6k stack, -85.4k with fade); bootstrap cannot produce a week worse than seen. True tail weeks are worse. P(week<-X) for X>60k is therefore a lower bound; P(week < -40k) is meaningful.
- Weekly resolution understates intra-week drawdown; day-level maxDD would be larger.
- Sizing: live lots as given by the ts2 record; no scaling or drawdown rule is changed. Block bootstrap preserves only short-memory dependence (L=4).
- Bundle benefit is in-sample selected (DIS-T winner's-curse note: forward mean between -$3k and +$5k/wk).
- Method uncertainty on p99: about +-$20k (block-length range).

## Plain sentence
On the live stack's own history, a one-year drawdown deeper than $150k has a probability of roughly 10% (about 21% if the 2026 regime lasts the whole year), the median year's worst drawdown is about $90k, and the watch bundle would cut those tails by about a third only if its 2026-only performance repeats; nothing here is a PASS and nothing goes live.
