# PREREG FV14 - GAPMAP untested cells, NQ/ES/RTY/YM (written before any run)

Date 2026-10-17. Worker ICT/FV. Code prefix ap_fv14*.py. Up to 8 processes. Selection clean 2023-08..2025-07 only; H1/H2 read once for selected cells; UNTESTED span never.

## 1. Inventory (GAPMAP.csv as of this morning, read-only)
UNTESTED cells on NQ/ES/RTY/YM: 329 (YM: none in the on-disk class). 57 are claimed by a running worker; 74 are unclaimed and on disk; the remainder need data we do not hold (cheap_buy 80 basket/COT/calendars, mbp10 74, options trades 26, other 18). Modes: M1 standalone, M2 additive sleeve, M3 constant-risk sleeve (the same sleeve in different framings), M4 pair switch/tilt, M5 pair exit, M6 execution, M7 risk rule, M8 sizing.
The 74 unclaimed on-disk cells split as follows. The coordinator's brief (ten families of 10-30 cells in my driver classes) cannot be met honestly from the map: only the groups below are in my tooling, and I will not invent cells.
- G-A (sleeve, flow persistence, D02 H4 M1-M3 NQ/ES/RTY = 9 cells; plus D02 H4 M4,M5,M7,M8 NQ = 4 pair-side cells, not run): signed-volume persistence/fade at fixed slots, 120-min time exit. Family FLOWP, 18 setups.
- G-B (sleeve, pair-internal state, D00 H1,H2 M2,M3 and H3,H4,H5 M1-M3 NQ = 13 cells): sleeves entered after pair events (loss exit, win exit, flip fade) with/against, holds 5/15/60/180/360 min (H1 5, H2 15, H3 60/180, H4 360; H5 mapped to the same 360 intraday maximum, flat 16:55, stated as a limitation). Family PAIRSTATE, 25 setups.
- G-C (M6 execution, D06/D07/D08/D10/D11 at H0-H2, 12 cells): execution-mode cells for drivers with no standalone edge in any tested M1-M3 cell, or already tested as limit mechanics: logged SKIPPED-DUPLICATE with reasons (FV12 time-of-day filters, FV7 pair limit re-entry, IMP3/FVG limit mechanic family). Not re-run.
- G-D (not run, out of tooling; stay UNTESTED, no claim): D01 H1-H5 M4-M8 NQ (15), D02 H1/H2 M5/M6 (3), D03 H6 M4/M7/M8 (3), D07 H0/H6 M4,M5,M7,M8 (5), D08 M5 (2), D12 ML cells (12), D00 pair-side M4. Reason: these are pair-side conditioners/exits/sizing/ML on flow or vol features that need a per-flip feature harness, owned by the claimed PZ/DRIVERS/L2 lineages; building a second harness here would duplicate claimed work.
So two families are run (43 setups x exit), not ten.

## 2. Family FLOWP (signed-volume persistence), definition
Signal at slots 10:30, 12:00, 13:30 ET (decision on the close of the previous minute; entry next open). S = sum of 1-min signed volume (series delta) over the previous W minutes; z = S / (sigma1 * sqrt(W)) with sigma1 = trailing 20-session std of 1-min delta (shifted one session). Enter side = sign(S) (persist) or -sign(S) (fade) iff |z| >= th. W in {30,60,120}, th in {1.0,1.5,2.0}, mode in {persist, fade}: 18 setups. Stop 1.5 ATR(15m), time exit 120 min (exit XT = stop plus time exit only; flat 16:55). 
## 3. Family PAIRSTATE definition
Pair trade list from the clean harness (B.EI/XI/SIDE/PTS0). Event at the pair exit row (known at its close; entry next open): LOSS (pair trade pts<0), WIN (pts>0); WITH or AGAINST the pair side; plus FADE = against at the pair entry row. Stop 1.5 ATR(15m); time exit h in {5,15,60,180,360} min. (LOSS,WIN) x (WITH,AGAINST) x 5 + FADE x 5 = 25 setups. Exit XT.

## 4. Gates (identical to the ICT study, ap_ict_stage2/ap_ict_verify, both framings)
Screen: clean weekly Sharpe >= 0.5 and n_clean >= 40; own timing-destroyed null 200 replicates (random entry rows with permuted sides, same stop distances and time-of-day, p95); family-level selection-corrected null = per replicate best-of over the family's cells; clean additive uplift @20% >= +0.10. Selected cells go to the full verify (H1/H2 once; shares 10-50%; vol-matched and R-sized framings; bootstrap; shift null; plateau +-25% exact; 2x slippage; strict fills; odd/even months; worst-decile corr <= +0.30). ES/RTY replication for FLOWP via ICT_SYM. ERA flag: not testable for either family (delta and pair trades exist only from 2023); the flag is recorded as UNKNOWN, not positive. Library: save every cell with >=100 trades via lib_save.save_family (R-sized). GAPMAP_UPDATES.md: UPD lines for closed cells, SKIPPED-DUPLICATE for G-C, no line for G-D.
## 5. Chance expectation
43 setups x 1 exit; with the screen rate seen in the ICT study (about 6-10% of cells pass Sharpe>=0.5 and n>=40 under the null) expect 2-4 screened by chance and <=1 to pass all three clean tests; the gates are not softened. Verdicts: FOUND needs all gates; LEAD needs clean+H1+H2 uplift >= +0.10 at 20% and the nulls; else NO.

## AMENDMENT A1 (before any result was read)
D00 H5 cells are NOT closed: the intraday simulator cannot hold past 16:55 so a 360-min hold is not the daily horizon; those three cells stay UNTESTED. G-B therefore closes 10 cells (H1-H4), not 13.
