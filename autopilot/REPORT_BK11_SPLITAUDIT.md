# REPORT BK11_SPLITAUDIT - split-data audit of the basket/single-name work, and the ES/RTY cross-instrument harness
**Verdict: NO verdict changes. Part 1: the raw basket panel was used by exactly one earlier family (REPORT_BASKET: BK1 lead-lag, BK2 breadth divergence, BK3 breadth tilt, BK4 flow persistence), and every price comparison in that code is WITHIN a session, so the six stock splits in the panel (AMZN 2022-06-06, GOOGL 2022-07-18, TSLA 2022-08-25, NVDA 2024-06-10, AVGO 2024-07-15, NFLX 2025-11-17, all |cross-day return| 66-95%) never enter a return, an extreme count or a flow sign. No cell was re-run. Part 2: an ES/RTY pair-row cross-instrument harness is built and validated on six BK selected cells (report-only; none passed the NQ gates, so no replication credit is claimed). No skipped item qualified for item 2 of the follow-up.** Pre-registered in PREREG_AUTOPILOT.md ('BK11') before the first scored run.

## Part 1 - audit
| source | uses raw basket prices? | cross-session comparison? | verdict risk |
|---|---|---|---|
| REPORT_BASKET (ap_basket_core.py) | yes, dense_itch.npz, no explicit guard | NO: minute returns x[:,1:]/x[:,:-1] within a day with the first bar set to 0; 30-min extreme windows (sliding windows along the minute axis only); breadth counts, signed flow (sign of the in-day return x dollar volume) and the 20-session spread-sd are built from those; NQ aligned on the same in-day grid | none: immune by construction (unguarded but not exposed) |
| REPORT_DRIVERS | no (NQ/ES futures trades only) | n/a | none |
| E6 concentration / breadth items | E6 was never run before BK4 (no REPORT_E6); breadth tilt = BASKET BK3 above | n/a | none |
| earnings items (J6, J7, J4X) | EDGAR timestamps and NQ only, no equity prices | n/a | none |
| QQQ-NQ basis item | none before BK2 | n/a | none |
| ap_quotes2 / ap_gapmap / opt phase0 | ticker lists or price quotes, no panel returns | n/a | none |
Empirical check on the panel: maximum absolute in-session 1-minute return over all 17 symbols and 1,199 days = 3.8%, zero minutes above 5%; cross-day returns above 40% in absolute value occur exactly six times (the splits listed above). BK2, BK4 and BK5 of this batch DO use cross-session prices (daily closes, breadth versus prior close); they were guarded (|daily return| > 40% dropped; split days compared against the first bar) before any scored run and are the only places the guard mattered. Verdict changes: none.

## Part 2 - ES/RTY harness (ap_bk_xi.py)
ES and RTY ST+HM books from d1_f4_core (ADR20 k=0.75, equal R = $9,600, live account rules, 1 tick/side, same as J7V); weight-type BK overlays are mapped by entry minute, ET date and side; tercile edges frozen from the NQ pair's clean rows; null = 200 replicates (feature permuted within book x month x session blocks, exact account re-runs); replication criterion: both instruments positive on all-in and mean >= 50% of the NQ clean uplift. Supported: BK1, BK2, BK3, BK4, BK9, BK10 and any future tilt/skip overlay; NOT supported: bracket overlays (BK5, BK6, BK7), which need an ES/RTY 1-second replay (not on disk in the harness).
| NQ-selected cell | instrument | clean | H1 | H2 | all-in | touched | null p95 / rank (all-in) | note |
|---|---|---|---|---|---|---|---|---|
| BK1 thr6_W30_HALF | ES | -0.03 | -0.23 | +0.07 | -0.03 | 4% | +0.08 / 0.22 | NQ clean +0.11 / all +0.06; hold=False |
| BK1 thr6_W30_HALF | RTY | -0.07 | -0.05 | -0.06 | -0.06 | 4% | +0.06 / 0.07 | NQ clean +0.11 / all +0.06; hold=False |
| BK2 L5_HIGH_DOWN | ES | +0.08 | -0.23 | -0.99 | -0.16 | 35% | +0.16 / 0.21 | NQ clean +0.09 / all +0.11; hold=False |
| BK2 L5_HIGH_DOWN | RTY | +0.08 | +0.22 | -0.49 | +0.00 | 36% | +0.08 / 0.86 | NQ clean +0.09 / all +0.11; hold=False |
| BK3 VOL_HIGH_DOWN | ES | -0.04 | +0.18 | -0.04 | -0.02 | 8% | +0.11 / 0.18 | NQ clean +0.21 / all +0.11; hold=False |
| BK3 VOL_HIGH_DOWN | RTY | -0.09 | +0.20 | +0.02 | -0.02 | 9% | +0.03 / 0.67 | NQ clean +0.21 / all +0.11; hold=False |
| BK4 DISP_HIGH_DOWN | ES | -0.07 | -0.23 | +0.36 | +0.01 | 25% | +0.14 / 0.42 | NQ clean +0.05 / all -0.16; hold=False |
| BK4 DISP_HIGH_DOWN | RTY | -0.11 | -0.16 | +0.52 | +0.01 | 24% | +0.06 / 0.82 | NQ clean +0.05 / all -0.16; hold=False |
| BK9 L30_TWO | ES | -0.02 | -0.24 | -0.00 | -0.04 | 17% | +0.06 / 0.27 | NQ clean +0.04 / all -0.02; hold=False |
| BK9 L30_TWO | RTY | +0.06 | +0.05 | +0.03 | +0.05 | 17% | +0.07 / 0.91 | NQ clean +0.04 / all -0.02; hold=False |
| BK10 scopeA_HALF_six | ES | +0.16 | +0.05 | -0.14 | +0.08 | 4% | +0.11 / 0.84 | NQ clean -0.09 / all +0.01; hold=False |
| BK10 scopeA_HALF_six | RTY | +0.10 | -0.18 | +0.04 | +0.04 | 4% | +0.07 / 0.81 | NQ clean -0.09 / all +0.01; hold=False |
Reading: no BK cell replicates on ES or RTY; the NQ clean uplifts do not carry over (most all-in uplifts are within the null band). Nothing changes any BK verdict. Follow-up item 2 as asked: of the 26 skipped items, none was skipped for 'harness lacked X' (reasons were covered, duplicate, data not on disk, calendar not on disk, or an L2 queue model), so no further family was run; the ES/RTY harness for tilt/skip overlays is now available for the cross-instrument leg of future batches.

Files: code/census/night_ins/ap_bk_xi.py; outputs/autopilot/bk/bk*/xi.json.

DONE BK11
