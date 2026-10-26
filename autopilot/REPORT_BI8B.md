# REPORT BI8B - drift-matched long-only null and short-side symmetry for BI8 (ES long after a range-shock day)
**Verdict: BI8 closed as NO (long beta). Against 200 random long-only entry sets with the same number of trades (483 over 2013-26), the same holding rule (RTH open to the 16:55 flatten, same day) and therefore the same ES bull drift, the real cell ranks 0.85 on clean standalone Sharpe (p95 +1.05) and 0.91 on clean additive uplift at 20% (p95 +0.15), all below the drift-matched p95 on every span; only the all-in aggregate (rank 0.96) edges above p95, which is the long-only drift of the whole 2023-26 window, not the shock selection. The short side of the same rule is the exact mirror (standalone Sharpe -0.84 clean, uplift -0.21), as expected for a no-stop time exit.**
Correction to REPORT_BI8: the cell 'hold=1d' is a SAME-DAY hold (enter the RTH open after the shock day, flatten at 16:55 ET), not a hold to the next day's 15:55; the text of REPORT_BI8's lead detail has been corrected. The numbers of REPORT_BI8 are unchanged (this script reproduces standalone 0.75 / 1.22 / 1.54 and uplift@30% +0.18 / +0.15 / +0.12).

## Method
- Drift-matched null: 200 replicates; each draws the same number of RTH-open entry days (483) at random from all eligible days 2013-26, goes LONG, holds the same open-to-16:55 flatten, on ES with the same fill model; each replicate is scaled to the pair's clean weekly sigma and added at 20% / 30% of pair risk exactly as BI8. Rank = share of replicates below the real cell; p95 as printed. This keeps long-only exposure and the 2023-26 bull drift in the null (the pipeline's alternating-side null does not).
- Short side: the same signal days, SHORT; with no stop and a time exit it is the negative of the long series, so it cannot separate 'volatility-shock reversal' from beta by itself; the random long-only null does that.

## Result
| statistic | real BI8 | null mean | null p95 | real rank | short side (same days) |
|---|---|---|---|---|---|
| standalone Sharpe clean | +0.75 | -0.00 | +1.05 | 0.85 | -0.84 |
| standalone H1 | +1.22 | +0.26 | +2.62 | 0.76 | -1.53 |
| standalone H2 | +1.54 | -0.06 | +1.74 | 0.92 | -1.73 |
| standalone all-in | +0.83 | -0.01 | +0.76 | 0.96 | -0.93 |
| uplift@20% clean | +0.14 | -0.03 | +0.15 | 0.91 | -0.21 |
| uplift@20% H1 | +0.10 | -0.02 | +0.54 | 0.69 | -0.15 |
| uplift@20% H2 | +0.08 | -0.10 | +0.27 | 0.81 | -0.12 |
| uplift@20% all-in | +0.12 | -0.05 | +0.11 | 0.96 | -0.19 |
| uplift@30% clean | +0.18 | -0.06 | +0.20 | 0.91 | -0.32 |
| uplift@30% H1 | +0.15 | -0.08 | +0.73 | 0.71 | -0.23 |
| uplift@30% H2 | +0.12 | -0.18 | +0.35 | 0.81 | -0.18 |
| uplift@30% all-in | +0.16 | -0.10 | +0.13 | 0.97 | -0.30 |

## Reading
Random long-only ES entries earn a clean-span standalone Sharpe of -0.00 on average (the bull drift) and the 95th percentile is +1.05; the shock-day selection adds +0.76 over the mean, inside the null spread (rank 0.85). On the uplift gate the real cell's clean +0.14 vs p95 +0.15 (rank 0.91), H1 +0.10 vs +0.54, H2 +0.08 vs +0.27. The gate needs the real cell above the null p95 on clean AND all-in; it is below on clean. Verdict per the coordinator rule: NO (long beta). CANDIDATES.md, GAPMAP_UPDATES.md and DECISIONS.md updated (BI8 lead withdrawn). Sized dollars of the withdrawn lead, for the record: sleeve scale 20.8 ES contracts = pair weekly sigma; 20% share = 4.2 contracts, worst single 1-contract trade in the pair window -$13,142 (same-day), about -$55k at 4.2 contracts.

Files: code/census/night_ins/ap_bi8b.py; outputs/autopilot/b/bi8_co/bi8b.json.

DONE BI8B
