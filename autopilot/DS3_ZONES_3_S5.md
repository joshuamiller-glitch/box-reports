# DS3_ZONES_3_S5 - zone density as a regime (ZONES-3 section 5), updated 2026-11-02 on D7 V13Z (= V13Y + nfix, basis-N take deltas)
**BASES.** V13X = DEFECT BASE (section 7), V13Y = add-fill fix (section 8), V13Z = V13Y + nfix (section 9, current). Sections 0-6 are assumed bases (history).
**HEADLINE (V13Z, lock=None, section 9).** Still a volume effect, no lead. 100 draws per kind (same-volume B, shuffled-day C, random rows A), L6M rank: sA40>=1 skip (+34% L6M, PRE +18%, X' +14%, MID +31%; passes the band; MID/PRE/X' cuts ONE-WEEK) 0.31 / 0.40 / 0.36; openA40 half 0.58 / 0.38 / 0.45; open20 half 0.29 / 0.33 / 0.34; nA60>=1 skip 0.40 / 0.44 / 0.39; rho60>=2 skip 0.37 / 0.43 / 0.39 (its X' ranks 0.04-0.06 but L6M does not beat chance); sopen40 half 0.19 / 0.16 / 0.27 (PRE -2%). Half variants of the congestion cells give no cut (sA40>=1 half 0%, nA60>=1 half -1%). pass_all = 0 on V13Z; the previously closest cells (sopen40 half on V13Y: +41/+11/+21, ranks 0.24/0.16/0.30; on V13X ranks 0.09/0.07/0.11) moved with the base each time.
**STRUCTURAL.** A fixed-point density rule is a different rule in each window: share of signals with >= 2 set lines within 40 pts fell from 35% (2023-04) to 9% (2026-10) as NQ doubled; price-scaled distance (x*E/20000) is the only form carried forward. Causality audit 800/800 brute-force checks ok.
**Base dependence of the best cells (lock none, cut L6M/PRE/X').** sA40>=1 skip: V13X +36/+14/+27 -> V13Y +36/0/-5 (ONE-WEEK) -> V13Z +34/+18/+14; sopen40 half: +51/+22/+11 -> +41/+11/+21 -> +39/-2/+22; nA60>=1 skip: +38/-6/+31 -> +36/-36/+7 -> +32/-8/+19; rho60>=2 skip: +34/+9/+32 -> +41/+1/+36 -> +23/+12/+40. The sign of PRE/X' flips with the base, which is what a volume effect looks like.
Post-hoc, Shadow only, no PASS claim. Prereg sha256 1a8d58e0...53e (+addendum 1 600dc569...968d). DEAD_CELLS: ZONES3S5 +248, ZONES3S5X +34 (V13X, defect base).

**Reading order.** Section 7 = V13X (headline); 7g = master table finalist x frame; 7h-7i = lock=None placebos, sweep, episode, book x session, vol tercile, best-of-N null. Sections 0-6 are on the ASSUMED bases (v1.2 interim, v1.3-assumed) and are kept as history; where V13X differs (e.g. sA40>=1 skip is positive on V13X but PRE -21% on assumed v1.3) the difference is base-dependence.
Post-hoc, Shadow only, no PASS claim. Prereg sha256 1a8d58e0...53e (+addendum 1 600dc569...968d). DEAD_CELLS: ZONES3S5 +248 (assumed bases), ZONES3S5X +34 (V13X). Per-month chain files: out/zones3_s5/chain/chain_s5_V13X_*.csv (34).

**HEADLINE 1 (structural).** A fixed-point density rule is a different rule in each window: the share of signals with >= 2 set lines within 40 pts fell from 35% (2023-04) to 9% (2026-10) as NQ doubled (median entry 16.5k -> 29.9k). Price-scaled distance (x*E/20000) is the only form carried forward; the fixed-point cells below are kept for the record.
**HEADLINE 2 (assumed v1.3 base, section 6).** The one lead-shaped v1.2 cell, price-scaled sA40>=1 skip, is FRAGILE on v1.3-assumed: L6M +32% only at the exact cut-off (x0.5 -29%, x0.75 -25%, x1.25 -4%, x1.5 -31%, x2 -8%), PRE -21%, X' -3%; v1.3 placebo ranks L6M B 0.10 / C 0.30 / A 0.10 (40 draws). PRE flips because the PRE base episode moves (v1.2 2024-W13..29, v1.3 2025-W06..19) and the skip removes big winning weeks in the 2025 drawdown. The half variants (sA40>=1/2, sA60>=1 half) are consistent on L6M/F9 (+25..31%) at every scale x0.75-x2 but are negative on PRE (-2% .. -49%) and are not placebo-clean (see 6g). Re-target: delaying the decision by 1 s or 3 s does not remove the (small) effect; the control rtc shows most of it is the market-entry convention. Three profile streams in the count (qA cells) do not improve on the 8-line count (qA40>=1 skip F9 -17% vs +32%; qA60>=1 half is the only q-cell with STRICT/TOL/NOW all Y, F9 +31% = same as sA60>=1 half). Not a lead anywhere.
**HEADLINE 3 (Z3 noise band, assumed v1.3, section 6h).** 0 of 34 finalists pass the rule 'cut exceeds the band in L6M AND in PRE or X'' (bands from DS3_ZONES_3_NOISE.md interim). So the density family is NOISE under the program's own standard.\n**Pending:** rows on the EXACT D7 v1.3 (V13X) when announced; Z3 noise band; remaining placebo draws (section 6g shows n).

# DS3_ZONES_3_S5 - zone density as a regime (ZONES-3 section 5). ALL ROWS ARE ON THE ASSUMED BASES (v1.2 interim, v1.3-assumed); V13X (exact D7 v1.3) rows are added when BASE-4 announces
**Plain sentence.** Zone density does not give a drawdown cut that survives the robustness standard. Of 230 density / open-space / ratio / no-man's-land cells on D7 v1.2 (interim base), none is RISK-KEEP. The fixed-point cut-offs that look best on L6M are ONE-WEEK (the whole L6M/HOLD/F9 cut is the week 2026-W31; e.g. nA40>=1 skip -23% of maxDD becomes +0.1% without that week) or volume effects (placebo rank B > 0.10: open-space "half" cells cut 28-43% only because they halve 55-80% of the signals). The one lead-shaped cell is the PRICE-SCALED congestion-ahead rule sA40>=1 skip (skip when any of the 8 fresh set lines is within 40*E/20000 pts ahead; at E=29,000 that is 58 pts): v1.2 L6M/F9 maxDD -39%, PRE +15%, X' +22%, STRICT and TOLERANT, mean delta -3.5k/wk inside the 13.3k MDE, not ONE-WEEK (+17% after dropping the carrying week... see section 3), placebo ranks B 0.05 / C 0.25 / A 0.20 (20 draws): beats the same-volume placebo, not the shuffled-day or random-row ones; ROBUST to +-25/50% on x (F9 cut +8% at 0.5x, +37..40% at 0.75-1.5x); and it does NOT carry to D7 v1.3 (L6M +32% but PRE -21%, X' -3%, S/T/N n/n/Y). Label: LEAD-unconfirmed (v1.2), not a lead on v1.3. The no-man's land (middle third of PDR/ON/SESS) alone is not a drawdown rule: mid_PDR half cuts L6M 19% / PRE 11% / X' 48% but is ONE-WEEK; the "up" (x1.5) variants add risk. Re-target (rt): sA40>=1 rt L6M +14%, PRE -63% (worse); against its control (same market entry, original target) the re-target part is small, so most of any change is the entry convention.
**Key structural finding.** Line density per fixed-point distance collapsed as NQ doubled (2023-04 -> 2026-10): signals with >= 2 set lines within 40 pts fell from 35% to 9%; a fixed-pt density rule is therefore a different rule in PRE/X' than in L3M/L6M. This is why the honest selection on PRE+X' (e.g. nB40>=1 skip: PRE +51%, X' +64%) fails on the recent windows (L6M -24%) and why the price-scaled version exists.
**Caveats.** Base is D7 v1.2 (interim); finalists re-run on v1.3 (section 4); placebo draws 20 per kind for 12+4 cells (ranks resolution 0.05; fewer for 3 cells), none for the other finalists (labelled UNTESTED); per-scope reruns were not run (per book x session is read from the cube of the all-scope run, section 3d); 1-s/3-s delay on rt not run; vol-tercile and line-parameter variants (swing strength, profile bin) not run (density uses the 8 stored lines only; the three profile streams were not added to the count). Equal-risk used lscale on the ALL-window worst-20. All post-hoc, Shadow only, no PASS claim.

# DS3_ZONES_3_S5 - zone density as a regime (ZONES-3 section 5), base D7 v1.2 interim = ASSUMED base
Post-hoc, Shadow only, no PASS claim. Prereg sha256 1a8d58e0d5b48e4e51e26c7587754daa443e5ed578584238c3d833a2fe6ec53e (+ addendum 1, price-scaled distances, sha256 600dc569ee663858891149e948b0e6f8e9e6a420501d62d3282cc614b2bd968d), both in DECISIONS.md before scoring. dead_lookup: 0 of 146 + 0 of 84 cell specs found (out/zones3_s5/dead_lookup.txt, dead_lookup_A1.txt). Code l2vast/ds3/code/zones3_s5/, results out/zones3_s5/ and /mnt/l2/l2vast/ds3_zones3_new/S5/.

## 0. What this section does
Zone density as a regime on the 8 SET8 lines (kijun1h, PDmid, CRT4h, KCup4h, camH3, OTE62, OTE705, OTE79; the 'shipped 8 + OTE-62' of the order is these 8, OTE-62 being one of them): how many fresh lines sit within 20/40/60 pts ahead and behind at the signal (congestion nA, nB, nT), distance to the nearest line in any direction (open space), ahead/behind ratio, and the NTE-1 no-man's land (middle third of the prior-day / overnight / session range), as skip / half (x0.5) / up (x1.5) / re-target rules ADDED to the base through the extra_skip / extra_mult hooks. Placebos: A random rows same count, B same count stratified by book x session, C shuffled-day (the real mask circularly shifted within each book x session stream). Per book x session is read from the cube of the same run.

## 1. The density regime itself (descriptive; no outcome)

| win   |   n_sig |   nT40=0 % |   =1 % |   =2 % |   >=3 % |   open>40 % |   median dmin |   nA40>=1 % |   nB40>=1 % |
|:------|--------:|-----------:|-------:|-------:|--------:|------------:|--------------:|------------:|------------:|
| L3M   |    8671 |       68.7 |   19.5 |    7.9 |     4   |        68.7 |          66.2 |        22.2 |        13.1 |
| L6M   |   19396 |       73.6 |   17.3 |    6.3 |     2.8 |        73.6 |          76.8 |        18.7 |        10.4 |
| HOLD  |   34726 |       71.7 |   17.6 |    6.9 |     3.8 |        71.7 |          72.9 |        19.3 |        12.1 |
| MID   |    7693 |       70.6 |   18.1 |    7   |     4.3 |        70.6 |          70.2 |        20.3 |        12.5 |
| PRE   |   32723 |       60.2 |   18.5 |    9.9 |    11.5 |        60.2 |          52.2 |        25.3 |        22.3 |
| X'    |   13852 |       44.4 |   19.7 |   12.5 |    23.4 |        44.4 |          34.6 |        35.7 |        35.1 |
| session   |   n_sig |   nT40=0 % |   nT40>=2 % |   open>40 % |   mid-third PDR % |
|:----------|--------:|-----------:|------------:|------------:|------------------:|
| asia      |   23654 |       48.4 |        32   |        48.4 |              27   |
| london    |   22236 |       52.6 |        27.4 |        52.6 |              23   |
| pre       |    5057 |       64.9 |        16.9 |        64.9 |              20.7 |
| nyam      |   21095 |       75.7 |         7.7 |        75.7 |              19.5 |
| nypm      |   15959 |       72.6 |        10   |        72.6 |              17.3 |
| close     |     489 |       71   |        12.9 |        71   |              12.3 |
| book   |   n_sig |   nT40=0 % |   nT40>=2 % |   open>40 % |
|:-------|--------:|-----------:|------------:|------------:|
| KB     |    8480 |       62.5 |        18.1 |        62.5 |
| PE     |    8203 |       65.9 |        16.1 |        65.9 |
| SM     |    2332 |       48.2 |        30.1 |        48.2 |
| HM     |    6198 |       59.6 |        21.8 |        59.6 |
| MV     |    7736 |       67.2 |        16.1 |        67.2 |
| PB     |   22357 |       58.7 |        22.7 |        58.7 |

Reading: the number of set lines within 40 pts fell by a factor of ~3 from X' to L3M (share of signals with nT40 >= 2: 35% in 2023-04, 9% in 2026-10) while NQ doubled (median entry 16.5k to 29.9k). A fixed-point density cut-off therefore flags many signals in PRE/X' and few in the recent windows: the same rule is a different rule in each window. Hence the price-scaled A1 cells (x_s = x * E/20000).

## 2. Stage 1: 230 cells scored (146 fixed-pt + A1 price-scaled), all windows, v1.2 interim = ASSUMED base

Counts (gain = maxDD cut): STRICT 11, TOLERANT (literal) 14, TOL-B 18, TOL-nc 23, NOW-ONLY 57 of 230. L6M maxDD cut >= 20%: 20 cells; of these with mean delta inside the MDE: 20. L6M, HOLD and F9 share ONE maxDD episode (week 2026-W31): their cuts are the same number in most rows.

### 2a. top 15 by the post-hoc score (mean maxDD cut over L6M, HOLD, MID)

| cell | flag% | maxDD $k base>cell (cut) L6M | F9 | HOLD | MID | PRE | X' | L3M cut | mean d $k/wk L6M (MDE) / PRE (MDE) / X' (MDE) | worst-20 PRE base>cell $k | S/T/N | TOL-B / TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| open20 half | 81 | 128>73 (+43%) | 128>73 (+43%) | +43% | +66% | -0% | +30% | +25% | -13.1 (+15.6) / -8.6 (+8.2) / +1.8 (+5.2) | -480>-285 | n/n/Y | n / n |
| rho40>=2 skip | 18 | 128>80 (+37%) | 128>80 (+37%) | +30% | +81% | -13% | +19% | +38% | -2.4 (+8.9) / -3.3 (+8.5) / +1.2 (+5.4) | -480>-430 | n/n/Y | Y / Y |
| nA60>=1 half | 32 | 128>73 (+43%) | 128>73 (+43%) | +43% | +59% | -48% | +46% | +47% | -3.0 (+12.9) / -9.1 (+8.7) / +2.1 (+5.4) | -480>-416 | n/n/Y | n / n |
| sA40>=1 half | 28 | 128>73 (+43%) | 128>73 (+43%) | +43% | +59% | -9% | +28% | +47% | -2.9 (+12.9) / -8.7 (+7.9) / +0.9 (+5.8) | -480>-442 | n/n/Y | n / n |
| sA60>=1 half | 36 | 128>73 (+43%) | 128>73 (+43%) | +43% | +57% | -44% | +41% | +31% | -4.9 (+14.1) / -8.2 (+8.6) / +1.8 (+5.3) | -480>-399 | n/n/Y | n / n |
| rho60>=2 half | 20 | 128>90 (+30%) | 128>90 (+30%) | +30% | +65% | +11% | +42% | +43% | -2.2 (+11.8) / -2.8 (+5.8) / +2.0 (+4.7) | -480>-439 | Y/Y/Y | Y / Y |
| nA40>=1 half | 25 | 128>92 (+28%) | 128>92 (+28%) | +28% | +66% | -10% | +26% | -1% | -0.9 (+6.1) / -8.0 (+7.8) / +0.8 (+5.9) | -480>-426 | n/n/n | n / n |
| rho60>=2 skip | 20 | 128>84 (+34%) | 128>84 (+34%) | +34% | +53% | -16% | -10% | +23% | +1.4 (+11.2) / -1.8 (+9.5) / +0.6 (+5.4) | -480>-464 | n/n/Y | Y / Y |
| nTany40>=2 half | 47 | 128>101 (+21%) | 128>101 (+21%) | +21% | +70% | +5% | +43% | -49% | -1.7 (+10.2) / -5.7 (+7.9) / +2.5 (+5.0) | -480>-384 | n/n/n | n / n |
| nA40>=1 skip | 25 | 128>99 (+23%) | 128>99 (+23%) | +23% | +64% | +10% | +23% | +0% | -5.9 (+9.3) / -1.6 (+8.5) / +1.5 (+6.9) | -480>-461 | Y/Y/Y | Y / Y |
| sA40>=1 skip | 28 | 128>78 (+39%) | 128>78 (+39%) | +32% | +31% | +15% | +22% | +35% | -3.5 (+13.3) / -2.5 (+9.2) / +1.6 (+6.4) | -480>-468 | Y/Y/Y | Y / Y |
| sA40>=2 half | 11 | 128>95 (+25%) | 128>95 (+25%) | +25% | +51% | +8% | +37% | -11% | +0.5 (+5.0) / -2.9 (+6.8) / +2.0 (+4.2) | -480>-429 | n/n/n | n / n |
| openA40 half | 75 | 128>93 (+28%) | 128>93 (+28%) | +28% | +45% | +20% | +59% | -24% | -13.2 (+16.9) / -8.1 (+8.3) / +4.3 (+5.1) | -480>-310 | n/n/n | n / n |
| rho60<=0.5 half | 24 | 128>115 (+10%) | 128>115 (+10%) | +10% | +79% | -44% | +27% | -28% | -1.1 (+4.7) / -4.5 (+5.0) / +1.4 (+4.6) | -480>-443 | n/n/n | n / n |
| nA60>=1 skip | 32 | 128>84 (+34%) | 128>84 (+34%) | +34% | +31% | -1% | +7% | +35% | -3.5 (+13.0) / -4.4 (+11.0) / +2.5 (+8.3) | -480>-478 | n/n/Y | Y / Y |

### 2b. top 15 by the honest score (mean maxDD cut over PRE and X', judged on the recent windows)

| cell | flag% | maxDD $k base>cell (cut) L6M | F9 | HOLD | MID | PRE | X' | L3M cut | mean d $k/wk L6M (MDE) / PRE (MDE) / X' (MDE) | worst-20 PRE base>cell $k | S/T/N | TOL-B / TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| nB40>=1 skip | 21 | 128>159 (-24%) | 128>159 (-24%) | -24% | +8% | +51% | +64% | -79% | -2.7 (+6.9) / -4.3 (+9.6) / +5.6 (+10.4) | -480>-459 | n/n/n | n / n |
| sB40>=1 skip | 26 | 128>135 (-6%) | 128>135 (-6%) | -6% | +50% | +35% | +64% | -62% | -6.9 (+18.0) / -5.6 (+10.3) / +7.0 (+10.8) | -480>-426 | n/n/n | n / n |
| sT40>=3 skip | 14 | 128>178 (-40%) | 128>178 (-40%) | -40% | +53% | +36% | +51% | -128% | -5.7 (+10.4) / -0.0 (+7.6) / +6.0 (+9.1) | -480>-413 | n/n/n | n / n |
| rho40<=0.5 skip | 15 | 128>164 (-28%) | 128>164 (-28%) | -28% | -2% | +18% | +68% | -91% | -1.3 (+5.8) / -3.4 (+8.3) / +6.6 (+8.9) | -480>-470 | n/n/n | n / n |
| openA40 half | 75 | 128>93 (+28%) | 128>93 (+28%) | +28% | +45% | +20% | +59% | -24% | -13.2 (+16.9) / -8.1 (+8.3) / +4.3 (+5.1) | -480>-310 | n/n/n | n / n |
| nT40>=2 half | 20 | 128>132 (-3%) | 128>132 (-3%) | -3% | +46% | +13% | +60% | -9% | -1.4 (+2.9) / -3.9 (+7.5) / +4.7 (+5.3) | -480>-402 | n/n/n | n / n |
| nB40>=2 skip | 10 | 128>128 (-0%) | 128>128 (-0%) | -0% | +8% | +27% | +45% | -1% | +0.9 (+3.1) / +1.0 (+5.0) / +5.4 (+10.1) | -480>-432 | n/n/n | n / n |
| sB40>=3 skip | 7 | 128>165 (-29%) | 128>165 (-29%) | -29% | +16% | +31% | +40% | -93% | -1.0 (+4.5) / -0.5 (+5.7) / +4.6 (+7.6) | -480>-447 | n/n/n | n / n |
| sB40>=3 half | 7 | 128>127 (+1%) | 128>127 (+1%) | +1% | -7% | +29% | +41% | +2% | +0.1 (+1.9) / +0.4 (+2.4) / +3.5 (+4.7) | -480>-461 | n/Y/Y | Y / Y |
| mid_any3 half | 41 | 128>129 (-1%) | 128>129 (-1%) | -1% | +24% | +14% | +54% | -110% | -5.3 (+8.2) / -2.7 (+6.8) / +3.5 (+3.9) | -480>-413 | n/n/n | n / n |
| nB40>=3 half | 6 | 128>124 (+3%) | 128>124 (+3%) | +3% | -6% | +27% | +40% | +9% | +0.2 (+0.8) / +0.2 (+1.3) / +3.5 (+4.5) | -480>-465 | n/Y/Y | Y / Y |
| sB40>=2 half | 14 | 128>121 (+5%) | 128>121 (+5%) | +5% | -11% | +30% | +37% | -57% | -5.2 (+11.4) / -0.4 (+4.8) / +2.8 (+5.0) | -480>-428 | n/n/n | n / n |
| nB40>=2 half | 10 | 128>119 (+7%) | 128>119 (+7%) | +7% | -9% | +23% | +44% | +22% | +0.6 (+1.5) / -0.2 (+4.4) / +3.1 (+5.2) | -480>-432 | n/Y/Y | Y / Y |
| sT40>=3 half | 14 | 128>133 (-4%) | 128>133 (-4%) | -4% | +45% | +11% | +53% | -12% | -1.9 (+3.5) / -4.7 (+6.8) / +4.2 (+5.4) | -480>-428 | n/n/n | n / n |
| nB40>=1 half | 21 | 128>134 (-5%) | 128>134 (-5%) | -5% | +46% | +29% | +36% | -15% | -1.5 (+3.7) / -3.8 (+6.3) / +2.9 (+5.8) | -480>-452 | n/n/n | n / n |

### 2c. TOLERANT (literal) cells, top 15 by post-hoc score

| cell | flag% | maxDD $k base>cell (cut) L6M | F9 | HOLD | MID | PRE | X' | L3M cut | mean d $k/wk L6M (MDE) / PRE (MDE) / X' (MDE) | worst-20 PRE base>cell $k | S/T/N | TOL-B / TOL-nc |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| rho60>=2 half | 20 | 128>90 (+30%) | 128>90 (+30%) | +30% | +65% | +11% | +42% | +43% | -2.2 (+11.8) / -2.8 (+5.8) / +2.0 (+4.7) | -480>-439 | Y/Y/Y | Y / Y |
| nA40>=1 skip | 25 | 128>99 (+23%) | 128>99 (+23%) | +23% | +64% | +10% | +23% | +0% | -5.9 (+9.3) / -1.6 (+8.5) / +1.5 (+6.9) | -480>-461 | Y/Y/Y | Y / Y |
| sA40>=1 skip | 28 | 128>78 (+39%) | 128>78 (+39%) | +32% | +31% | +15% | +22% | +35% | -3.5 (+13.3) / -2.5 (+9.2) / +1.6 (+6.4) | -480>-468 | Y/Y/Y | Y / Y |
| rho40<=0.5 half | 15 | 128>117 (+9%) | 128>117 (+9%) | +9% | +45% | +23% | +35% | +29% | -0.3 (+3.4) / -0.2 (+3.1) / +2.9 (+5.6) | -480>-462 | Y/Y/Y | Y / Y |
| sA40>=3 half | 4 | 128>124 (+3%) | 128>124 (+3%) | +3% | +51% | +1% | +28% | +9% | +0.2 (+2.1) / -0.6 (+1.9) / +1.1 (+4.1) | -480>-468 | Y/Y/Y | Y / Y |
| nB40>=2 half | 10 | 128>119 (+7%) | 128>119 (+7%) | +7% | -9% | +23% | +44% | +22% | +0.6 (+1.5) / -0.2 (+4.4) / +3.1 (+5.2) | -480>-432 | n/Y/Y | Y / Y |
| sA20>=3 half | 1 | 128>128 (+0%) | 128>128 (+0%) | +0% | +3% | +4% | +8% | +0% | +0.0 (+0.1) / -0.1 (+0.4) / -0.3 (+2.7) | -480>-479 | Y/Y/Y | Y / Y |
| nA20>=3 half | 1 | 128>127 (+1%) | 128>127 (+1%) | +1% | +2% | +5% | +27% | +2% | +0.0 (+0.1) / -0.1 (+0.4) / +0.9 (+3.8) | -480>-477 | Y/Y/Y | Y / Y |
| nB20>=2 skip | 2 | 128>127 (+0%) | 128>127 (+0%) | +0% | +1% | +25% | -13% | +1% | +0.1 (+0.4) / +0.6 (+1.7) / -0.0 (+3.8) | -480>-479 | n/Y/Y | Y / Y |
| nB20>=2 half | 2 | 128>127 (+1%) | 128>127 (+1%) | +1% | -1% | +13% | -3% | +2% | +0.0 (+0.2) / +0.2 (+0.9) / +0.8 (+3.3) | -480>-477 | n/Y/Y | Y / Y |
| nB40>=3 half | 6 | 128>124 (+3%) | 128>124 (+3%) | +3% | -6% | +27% | +40% | +9% | +0.2 (+0.8) / +0.2 (+1.3) / +3.5 (+4.5) | -480>-465 | n/Y/Y | Y / Y |
| sB20>=2 half | 3 | 128>126 (+2%) | 128>126 (+2%) | +2% | -4% | +20% | +4% | +5% | -0.2 (+1.2) / +0.6 (+0.9) / +1.1 (+3.1) | -480>-477 | n/Y/Y | Y / Y |
| nB60>=3 half | 13 | 128>126 (+1%) | 128>126 (+1%) | +1% | -6% | +29% | +26% | +4% | -0.1 (+1.9) / -1.7 (+5.1) / +2.0 (+4.6) | -480>-429 | n/Y/Y | Y / Y |
| sB40>=3 half | 7 | 128>127 (+1%) | 128>127 (+1%) | +1% | -7% | +29% | +41% | +2% | +0.1 (+1.9) / +0.4 (+2.4) / +3.5 (+4.7) | -480>-461 | n/Y/Y | Y / Y |

Re-target: rt is judged against its control rtc (same market entry, original target): 
| mask | rt L6M cut / F9 cut / PRE cut | rtc L6M / F9 / PRE | rt mean d L6M (MDE) | rtc mean d L6M |
|---|---|---|---|---|
| nA20>=2 | -4% / -4% / +2% | -0% / -0% / +1% | -0.5 (+0.8) | +0.0 |
| nA20>=3 | -2% / -2% / +0% | +0% / +0% / -0% | -0.0 (+0.3) | +0.0 |
| nA40>=1 | +14% / +14% / -61% | +7% / +7% / +1% | -3.1 (+7.7) | +1.3 |
| nA40>=2 | -13% / -13% / -21% | +2% / +2% / -4% | -1.4 (+3.2) | +0.7 |
| nA40>=3 | -10% / -10% / +7% | -0% / -0% / -0% | -0.5 (+1.0) | -0.0 |
| nA60>=1 | +13% / +13% / -33% | +5% / +5% / +3% | -2.9 (+8.9) | +1.5 |
| nA60>=2 | -18% / -18% / -37% | +5% / +5% / -1% | -1.3 (+4.1) | +0.9 |
| nA60>=3 | -10% / -10% / +13% | +0% / +0% / +1% | -0.1 (+1.2) | +0.3 |
| rho40>=2 | +14% / +14% / +1% | +7% / +7% / -0% | -2.1 (+6.5) | +1.3 |
| rho60>=2 | +14% / +14% / +19% | +3% / +3% / +1% | -1.7 (+6.8) | +1.0 |
| sA20>=2 | -7% / -7% / +6% | -0% / -0% / +1% | -1.2 (+1.5) | +0.1 |
| sA20>=3 | -4% / -4% / -0% | +0% / +0% / -0% | +0.1 (+0.8) | -0.0 |
| sA40>=1 | +14% / +14% / -63% | +6% / +6% / +1% | -2.9 (+8.8) | +1.5 |
| sA40>=2 | -18% / -18% / -24% | +6% / +6% / -4% | -1.7 (+4.0) | +0.9 |
| sA40>=3 | -9% / -9% / +10% | +0% / +0% / -0% | -0.0 (+1.2) | +0.3 |
| sA60>=1 | -48% / -48% / -33% | +1% / +1% / +3% | -7.4 (+8.3) | +1.7 |
| sA60>=2 | -34% / -34% / -35% | +9% / +9% / -1% | -2.4 (+8.5) | +1.9 |
| sA60>=3 | -20% / -20% / +12% | +0% / +0% / +1% | -0.2 (+3.9) | +0.4 |

## 3. Finalists: 34 cells (prereg rule), robustness standard

Episode proofing = leave-one-week-out (LOWO) and leave-one-month-out (LOMO) range of the maxDD cut, month-block bootstrap 90% CI (400 draws) and P(cut>0), the week carrying the base maxDD (ISO key), and drop-that-week cut. ONE-WEEK = full cut >= 10% and the cut after dropping the carrying week < half of it (or < 5%).

| cell | window | cut | week carrying base maxDD | cut without that week | LOWO range | LOMO range | bootstrap 90% CI / P(cut>0) | ONE-WEEK |
|---|---|---|---|---|---|---|---|---|
| nA40>=1 skip | L6M | +23% | 202631 | +0% | +0% .. +36% | +0% .. +38% | [-47%, +38%] / 0.74 | ONE-WEEK |
| nA40>=1 skip | HOLD | +23% | 202631 | +4% | -3% .. +43% | -7% .. +24% | [-68%, +61%] / 0.74 | ONE-WEEK |
| nA40>=1 skip | PRE | +10% | 202417 | -21% | -21% .. +37% | -53% .. +23% | [-88%, +40%] / 0.45 | - |
| nA40>=1 skip | X' | +23% | 202333 | +12% | +8% .. +33% | -1% .. +39% | [-57%, +55%] / 0.67 | - |
| nA40>=1 skip | F9 | +23% | 202631 | +9% | +7% .. +36% | +15% .. +38% | [-12%, +71%] / 0.90 | ONE-WEEK |
| nA40>=1 half | L6M | +28% | 202631 | -0% | -0% .. +36% | +0% .. +43% | [-11%, +45%] / 0.92 | ONE-WEEK |
| nA40>=1 half | HOLD | +28% | 202631 | +8% | +7% .. +47% | +21% .. +38% | [-2%, +70%] / 0.94 | ONE-WEEK |
| nA40>=1 half | PRE | -10% | 202417 | -45% | -61% .. -3% | -83% .. +7% | [-162%, +25%] / 0.25 | - |
| nA40>=1 half | X' | +26% | 202333 | +14% | +12% .. +37% | +12% .. +36% | [-28%, +44%] / 0.76 | - |
| nA40>=1 half | F9 | +28% | 202631 | +8% | +8% .. +36% | +28% .. +43% | [+1%, +73%] / 0.97 | ONE-WEEK |
| nB40>=1 skip | L6M | -24% | 202631 | -37% | -37% .. -11% | -29% .. +5% | [-69%, +5%] / 0.47 | - |
| nB40>=1 skip | HOLD | -24% | 202631 | -25% | -33% .. +1% | -29% .. +5% | [-61%, +18%] / 0.46 | - |
| nB40>=1 skip | PRE | +51% | 202417 | +34% | +6% .. +65% | +16% .. +57% | [-27%, +60%] / 0.81 | - |
| nB40>=1 skip | X' | +64% | 202333 | +58% | +54% .. +69% | +48% .. +66% | [-35%, +75%] / 0.90 | - |
| nB40>=1 skip | F9 | -24% | 202631 | -25% | -33% .. -11% | -29% .. +8% | [-43%, +18%] / 0.60 | - |
| nB40>=1 half | L6M | -5% | 202631 | -7% | -11% .. +4% | -9% .. +5% | [-15%, +10%] / 0.54 | - |
| nB40>=1 half | HOLD | -5% | 202631 | +2% | -11% .. +23% | -9% .. +13% | [-5%, +44%] / 0.84 | - |
| nB40>=1 half | PRE | +29% | 202417 | +30% | +10% .. +38% | +19% .. +38% | [-5%, +38%] / 0.92 | - |
| nB40>=1 half | X' | +36% | 202333 | +41% | +19% .. +43% | +23% .. +42% | [+6%, +55%] / 0.97 | - |
| nB40>=1 half | F9 | -5% | 202631 | +2% | -11% .. +4% | -9% .. +37% | [-4%, +43%] / 0.83 | - |
| nB40>=2 skip | L6M | -0% | 202631 | -0% | -9% .. +4% | -3% .. +3% | [-6%, +4%] / 0.49 | - |
| nB40>=2 skip | HOLD | -0% | 202631 | +8% | -9% .. +26% | -3% .. +8% | [-5%, +25%] / 0.83 | - |
| nB40>=2 skip | PRE | +27% | 202417 | +7% | -9% .. +38% | -18% .. +36% | [-22%, +38%] / 0.69 | ONE-WEEK |
| nB40>=2 skip | X' | +45% | 202333 | +35% | +35% .. +53% | +33% .. +58% | [-2%, +67%] / 0.94 | - |
| nB40>=2 skip | F9 | -0% | 202631 | +8% | -9% .. +8% | -3% .. +8% | [-4%, +13%] / 0.81 | - |
| nB40>=2 half | L6M | +7% | 202631 | +10% | +2% .. +10% | +0% .. +7% | [-0%, +9%] / 0.69 | - |
| nB40>=2 half | HOLD | +7% | 202631 | -9% | -9% .. +17% | -9% .. +7% | [-9%, +20%] / 0.44 | - |
| nB40>=2 half | PRE | +23% | 202417 | +17% | -2% .. +32% | -6% .. +31% | [-16%, +34%] / 0.81 | - |
| nB40>=2 half | X' | +44% | 202333 | +52% | +28% .. +52% | +28% .. +50% | [+7%, +58%] / 0.97 | - |
| nB40>=2 half | F9 | +7% | 202631 | -9% | -9% .. +9% | -9% .. +7% | [-9%, +3%] / 0.27 | - |
| nB40>=3 skip | L6M | -1% | 202631 | -2% | -7% .. +3% | -7% .. +5% | [-13%, +5%] / 0.20 | - |
| nB40>=3 skip | HOLD | -1% | 202631 | -4% | -7% .. +3% | -7% .. +5% | [-8%, +7%] / 0.24 | - |
| nB40>=3 skip | PRE | +31% | 202417 | +19% | -9% .. +51% | -2% .. +40% | [-16%, +30%] / 0.73 | - |
| nB40>=3 skip | X' | +31% | 202333 | +36% | +14% .. +37% | +10% .. +41% | [-23%, +56%] / 0.83 | - |
| nB40>=3 skip | F9 | -1% | 202631 | -4% | -7% .. +3% | -7% .. +5% | [-9%, +5%] / 0.14 | - |
| nB40>=3 half | L6M | +3% | 202631 | +4% | -0% .. +4% | +0% .. +3% | [+0%, +4%] / 0.47 | - |
| nB40>=3 half | HOLD | +3% | 202631 | -6% | -6% .. +4% | -6% .. +3% | [-6%, +3%] / 0.18 | - |
| nB40>=3 half | PRE | +27% | 202417 | +18% | +6% .. +31% | -3% .. +30% | [-9%, +22%] / 0.81 | - |
| nB40>=3 half | X' | +40% | 202333 | +48% | +25% .. +48% | +23% .. +46% | [+9%, +58%] / 0.99 | - |
| nB40>=3 half | F9 | +3% | 202631 | -6% | -6% .. +4% | -6% .. +3% | [-6%, +2%] / 0.13 | - |
| nT40>=2 half | L6M | -3% | 202631 | -4% | -6% .. -1% | -4% .. +2% | [-12%, +5%] / 0.53 | - |
| nT40>=2 half | HOLD | -3% | 202631 | +5% | -6% .. +24% | -4% .. +15% | [-4%, +55%] / 0.80 | - |
| nT40>=2 half | PRE | +13% | 202417 | -17% | -17% .. +45% | -48% .. +40% | [-22%, +45%] / 0.82 | ONE-WEEK |
| nT40>=2 half | X' | +60% | 202333 | +53% | +53% .. +68% | +51% .. +69% | [+22%, +74%] / 0.99 | - |
| nT40>=2 half | F9 | -3% | 202631 | +5% | -6% .. +5% | -4% .. +37% | [-5%, +53%] / 0.77 | - |
| nT40>=4 half | L6M | -2% | 202631 | -3% | -3% .. +0% | -2% .. +0% | [-3%, +2%] / 0.25 | - |
| nT40>=4 half | HOLD | -2% | 202631 | -4% | -4% .. +0% | -4% .. +0% | [-6%, +3%] / 0.21 | - |
| nT40>=4 half | PRE | -2% | 202417 | -3% | -10% .. +13% | -7% .. +10% | [-14%, +13%] / 0.61 | - |
| nT40>=4 half | X' | +61% | 202333 | +54% | +44% .. +62% | +46% .. +61% | [+25%, +64%] / 1.00 | - |
| nT40>=4 half | F9 | -2% | 202631 | -4% | -4% .. +0% | -4% .. +0% | [-5%, +1%] / 0.12 | - |
| nA60>=1 skip | L6M | +34% | 202631 | +25% | +25% .. +39% | +1% .. +34% | [+1%, +34%] / 1.00 | - |
| nA60>=1 skip | HOLD | +34% | 202631 | +14% | -6% .. +52% | +13% .. +34% | [-26%, +66%] / 0.84 | ONE-WEEK |
| nA60>=1 skip | PRE | -1% | 202417 | -35% | -49% .. +29% | -71% .. +16% | [-110%, +47%] / 0.51 | - |
| nA60>=1 skip | X' | +7% | 202333 | -11% | -11% .. +20% | -26% .. +33% | [-94%, +59%] / 0.59 | - |
| nA60>=1 skip | F9 | +34% | 202631 | +21% | +5% .. +38% | +21% .. +34% | [-19%, +69%] / 0.91 | - |
| nA60>=1 half | L6M | +43% | 202631 | +22% | +22% .. +49% | -0% .. +45% | [-0%, +45%] / 0.83 | - |
| nA60>=1 half | HOLD | +43% | 202631 | +29% | +25% .. +58% | +37% .. +45% | [+11%, +72%] / 0.98 | - |
| nA60>=1 half | PRE | -48% | 202417 | -76% | -112% .. -16% | -114% .. -23% | [-187%, +28%] / 0.22 | - |
| nA60>=1 half | X' | +46% | 202333 | +38% | +34% .. +52% | +31% .. +57% | [-18%, +66%] / 0.90 | - |
| nA60>=1 half | F9 | +43% | 202631 | +29% | +25% .. +49% | +37% .. +45% | [+4%, +74%] / 0.95 | - |
| nA60>=2 half | L6M | +25% | 202631 | -5% | -5% .. +33% | -0% .. +35% | [-5%, +40%] / 0.79 | ONE-WEEK |
| nA60>=2 half | HOLD | +25% | 202631 | +4% | +4% .. +45% | +15% .. +33% | [-6%, +62%] / 0.92 | ONE-WEEK |
| nA60>=2 half | PRE | +5% | 202417 | -15% | -22% .. +18% | -46% .. +25% | [-67%, +28%] / 0.36 | - |
| nA60>=2 half | X' | +24% | 202333 | +12% | +12% .. +34% | +2% .. +38% | [-40%, +56%] / 0.74 | ONE-WEEK |
| nA60>=2 half | F9 | +25% | 202631 | +4% | +4% .. +33% | +25% .. +37% | [-0%, +68%] / 0.93 | ONE-WEEK |
| nT60>=3 skip | L6M | -39% | 202631 | -60% | -60% .. -26% | -55% .. -15% | [-160%, +1%] / 0.10 | - |
| nT60>=3 skip | HOLD | -39% | 202631 | -46% | -46% .. -2% | -39% .. -4% | [-75%, +47%] / 0.53 | - |
| nT60>=3 skip | PRE | -3% | 202417 | -18% | -26% .. +26% | -49% .. +24% | [-59%, +35%] / 0.44 | - |
| nT60>=3 skip | X' | +64% | 202333 | +57% | +48% .. +69% | +34% .. +72% | [+6%, +71%] / 0.96 | - |
| nT60>=3 skip | F9 | -39% | 202631 | -46% | -46% .. -26% | -39% .. -1% | [-87%, +47%] / 0.49 | - |
| nTany40>=2 half | L6M | +21% | 202631 | -11% | -11% .. +30% | -38% .. +32% | [-104%, +53%] / 0.47 | ONE-WEEK |
| nTany40>=2 half | HOLD | +21% | 202631 | -1% | -1% .. +42% | +21% .. +39% | [-16%, +69%] / 0.88 | ONE-WEEK |
| nTany40>=2 half | PRE | +5% | 202417 | -27% | -31% .. +29% | -61% .. +29% | [-64%, +48%] / 0.63 | - |
| nTany40>=2 half | X' | +43% | 202333 | +34% | +32% .. +49% | +29% .. +48% | [+16%, +64%] / 0.99 | - |
| nTany40>=2 half | F9 | +21% | 202631 | -1% | -1% .. +30% | +21% .. +39% | [-23%, +68%] / 0.82 | ONE-WEEK |
| open20 half | L6M | +43% | 202631 | +39% | +39% .. +49% | +40% .. +50% | [+19%, +52%] / 0.99 | - |
| open20 half | HOLD | +43% | 202631 | +44% | +39% .. +58% | +40% .. +60% | [+31%, +74%] / 1.00 | - |
| open20 half | PRE | -0% | 202417 | -17% | -17% .. +23% | -15% .. +20% | [-56%, +41%] / 0.67 | - |
| open20 half | X' | +30% | 202333 | +26% | +24% .. +40% | +18% .. +43% | [-2%, +59%] / 0.94 | - |
| open20 half | F9 | +43% | 202631 | +44% | +39% .. +49% | +40% .. +66% | [+36%, +76%] / 1.00 | - |
| open60 half | L6M | +24% | 202631 | -40% | -40% .. +43% | -64% .. +49% | [-103%, +71%] / 0.69 | ONE-WEEK |
| open60 half | HOLD | +24% | 202631 | -28% | -28% .. +44% | -4% .. +49% | [-25%, +59%] / 0.87 | ONE-WEEK |
| open60 half | PRE | -13% | 202417 | -21% | -25% .. +11% | -30% .. +6% | [-86%, +30%] / 0.43 | - |
| open60 half | X' | +5% | 202333 | +5% | -4% .. +23% | -8% .. +29% | [-44%, +38%] / 0.52 | - |
| open60 half | F9 | +24% | 202631 | -28% | -28% .. +43% | -4% .. +49% | [-47%, +63%] / 0.81 | ONE-WEEK |
| openA40 half | L6M | +28% | 202631 | +16% | +16% .. +36% | +15% .. +43% | [-9%, +52%] / 0.91 | - |
| openA40 half | HOLD | +28% | 202631 | +23% | +17% .. +47% | +24% .. +45% | [+20%, +57%] / 0.99 | - |
| openA40 half | PRE | +20% | 202417 | -6% | -7% .. +29% | -34% .. +20% | [-68%, +39%] / 0.58 | ONE-WEEK |
| openA40 half | X' | +59% | 202333 | +61% | +50% .. +65% | +52% .. +67% | [+36%, +76%] / 1.00 | - |
| openA40 half | F9 | +28% | 202631 | +23% | +17% .. +36% | +24% .. +45% | [-2%, +53%] / 0.94 | - |
| rho40>=2 skip | L6M | +37% | 202631 | +22% | +22% .. +44% | +1% .. +48% | [-5%, +48%] / 0.95 | - |
| rho40>=2 skip | HOLD | +30% | 202631 | +3% | -7% .. +48% | +3% .. +37% | [-38%, +69%] / 0.86 | ONE-WEEK |
| rho40>=2 skip | PRE | -13% | 202417 | -34% | -54% .. +4% | -50% .. +15% | [-81%, +30%] / 0.37 | - |
| rho40>=2 skip | X' | +19% | 202333 | +17% | +3% .. +30% | +3% .. +31% | [-27%, +39%] / 0.71 | - |
| rho40>=2 skip | F9 | +37% | 202631 | +29% | +27% .. +44% | +35% .. +48% | [+5%, +75%] / 1.00 | - |
| rho40<=0.5 skip | L6M | -28% | 202631 | -43% | -43% .. -15% | -30% .. -4% | [-48%, +1%] / 0.25 | - |
| rho40<=0.5 skip | HOLD | -28% | 202631 | -30% | -32% .. +1% | -28% .. -2% | [-38%, +10%] / 0.29 | - |
| rho40<=0.5 skip | PRE | +18% | 202417 | +16% | +0% .. +39% | -7% .. +28% | [-47%, +37%] / 0.60 | - |
| rho40<=0.5 skip | X' | +68% | 202333 | +62% | +57% .. +75% | +60% .. +73% | [+7%, +79%] / 0.96 | - |
| rho40<=0.5 skip | F9 | -28% | 202631 | -30% | -32% .. -15% | -28% .. -2% | [-33%, +9%] / 0.33 | - |
| rho60>=2 skip | L6M | +34% | 202631 | +25% | +25% .. +39% | -0% .. +34% | [-6%, +33%] / 0.77 | - |
| rho60>=2 skip | HOLD | +34% | 202631 | +22% | +18% .. +52% | +22% .. +35% | [-5%, +65%] / 0.92 | - |
| rho60>=2 skip | PRE | -16% | 202417 | -46% | -48% .. -4% | -85% .. +5% | [-115%, +27%] / 0.34 | - |
| rho60>=2 skip | X' | -10% | 202333 | -18% | -21% .. +1% | -18% .. +7% | [-50%, +35%] / 0.55 | - |
| rho60>=2 skip | F9 | +34% | 202631 | +32% | +18% .. +39% | +31% .. +37% | [-2%, +69%] / 0.94 | - |
| rho60>=2 half | L6M | +30% | 202631 | +20% | +20% .. +35% | +0% .. +31% | [+0%, +43%] / 1.00 | - |
| rho60>=2 half | HOLD | +30% | 202631 | +27% | +21% .. +48% | +29% .. +35% | [+7%, +68%] / 0.98 | - |
| rho60>=2 half | PRE | +11% | 202417 | +11% | -10% .. +25% | +4% .. +22% | [-28%, +27%] / 0.62 | - |
| rho60>=2 half | X' | +42% | 202333 | +33% | +33% .. +46% | +25% .. +52% | [-7%, +64%] / 0.92 | - |
| rho60>=2 half | F9 | +30% | 202631 | +27% | +21% .. +35% | +29% .. +37% | [+5%, +72%] / 0.97 | - |
| rho60<=0.5 half | L6M | +10% | 202631 | -13% | -13% .. +18% | +0% .. +29% | [-22%, +29%] / 0.70 | ONE-WEEK |
| rho60<=0.5 half | HOLD | +10% | 202631 | -3% | -3% .. +34% | +3% .. +29% | [-2%, +69%] / 0.93 | ONE-WEEK |
| rho60<=0.5 half | PRE | -44% | 202417 | -92% | -92% .. -1% | -144% .. +17% | [-85%, +17%] / 0.28 | - |
| rho60<=0.5 half | X' | +27% | 202333 | +32% | +20% .. +35% | +14% .. +39% | [-21%, +46%] / 0.83 | - |
| rho60<=0.5 half | F9 | +10% | 202631 | -3% | -3% .. +18% | +3% .. +37% | [-0%, +70%] / 0.91 | ONE-WEEK |
| mid_PDR half | L6M | +19% | 202631 | -13% | -13% .. +31% | +0% .. +42% | [-57%, +42%] / 0.65 | ONE-WEEK |
| mid_PDR half | HOLD | +19% | 202631 | -3% | -3% .. +40% | +17% .. +41% | [-13%, +61%] / 0.90 | ONE-WEEK |
| mid_PDR half | PRE | +11% | 202417 | +7% | -21% .. +15% | -9% .. +22% | [-35%, +23%] / 0.56 | - |
| mid_PDR half | X' | +48% | 202333 | +40% | +34% .. +54% | +36% .. +59% | [+17%, +64%] / 1.00 | - |
| mid_PDR half | F9 | +19% | 202631 | -3% | -3% .. +31% | +17% .. +42% | [-5%, +62%] / 0.91 | ONE-WEEK |
| mid_any3 half | L6M | -1% | 202631 | -43% | -43% .. +13% | -43% .. +26% | [-65%, +41%] / 0.66 | - |
| mid_any3 half | HOLD | -1% | 202631 | -31% | -31% .. +26% | -1% .. +26% | [-26%, +43%] / 0.86 | - |
| mid_any3 half | PRE | +14% | 202417 | +10% | -21% .. +21% | -14% .. +14% | [-28%, +30%] / 0.62 | - |
| mid_any3 half | X' | +54% | 202333 | +48% | +42% .. +58% | +42% .. +61% | [+27%, +69%] / 1.00 | - |
| mid_any3 half | F9 | -1% | 202631 | -31% | -31% .. +13% | -1% .. +26% | [-21%, +43%] / 0.86 | - |
| mid_PDR&open40 up | L6M | +24% | 202631 | +3% | +3% .. +34% | +0% .. +24% | [+0%, +23%] / 0.83 | ONE-WEEK |
| mid_PDR&open40 up | HOLD | +24% | 202631 | +11% | +11% .. +32% | +6% .. +24% | [+6%, +33%] / 0.97 | ONE-WEEK |
| mid_PDR&open40 up | PRE | -20% | 202417 | -61% | -61% .. -3% | -104% .. -4% | [-88%, +8%] / 0.17 | - |
| mid_PDR&open40 up | X' | -3% | 202333 | -3% | -6% .. +3% | -9% .. +4% | [-22%, +6%] / 0.21 | - |
| mid_PDR&open40 up | F9 | +24% | 202631 | +11% | +11% .. +32% | +6% .. +24% | [+2%, +32%] / 0.95 | ONE-WEEK |
| mid_ON&nT40<=1 up | L6M | +6% | 202631 | +9% | -14% .. +12% | +0% .. +6% | [-2%, +17%] / 0.61 | - |
| mid_ON&nT40<=1 up | HOLD | +6% | 202631 | +17% | -14% .. +31% | +0% .. +18% | [-0%, +57%] / 0.86 | - |
| mid_ON&nT40<=1 up | PRE | +8% | 202417 | +12% | -20% .. +12% | -7% .. +8% | [-24%, +5%] / 0.31 | - |
| mid_ON&nT40<=1 up | X' | -2% | 202333 | -4% | -4% .. -1% | -4% .. -1% | [-9%, +2%] / 0.19 | - |
| mid_ON&nT40<=1 up | F9 | +6% | 202631 | +17% | -14% .. +17% | +0% .. +37% | [-0%, +69%] / 0.86 | - |
| sA40>=1 skip | L6M | +39% | 202631 | +25% | +25% .. +45% | +1% .. +39% | [+1%, +38%] / 1.00 | - |
| sA40>=1 skip | HOLD | +32% | 202631 | +5% | -9% .. +50% | -4% .. +35% | [-40%, +66%] / 0.80 | ONE-WEEK |
| sA40>=1 skip | PRE | +15% | 202417 | -14% | -20% .. +40% | -44% .. +26% | [-82%, +41%] / 0.49 | ONE-WEEK |
| sA40>=1 skip | X' | +22% | 202333 | +9% | +9% .. +28% | +1% .. +37% | [-47%, +54%] / 0.67 | ONE-WEEK |
| sA40>=1 skip | F9 | +39% | 202631 | +21% | +5% .. +43% | +21% .. +39% | [-18%, +71%] / 0.88 | - |
| sA40>=1 half | L6M | +43% | 202631 | +22% | +22% .. +49% | -0% .. +45% | [-0%, +45%] / 0.83 | - |
| sA40>=1 half | HOLD | +43% | 202631 | +29% | +25% .. +58% | +37% .. +45% | [+11%, +72%] / 0.98 | - |
| sA40>=1 half | PRE | -9% | 202417 | -45% | -60% .. -3% | -84% .. +6% | [-169%, +26%] / 0.24 | - |
| sA40>=1 half | X' | +28% | 202333 | +16% | +14% .. +39% | +14% .. +38% | [-21%, +44%] / 0.79 | - |
| sA40>=1 half | F9 | +43% | 202631 | +29% | +25% .. +49% | +37% .. +45% | [+4%, +73%] / 0.95 | - |
| sA40>=1 rt | L6M | +14% | 202631 | +17% | +2% .. +17% | -21% .. +25% | [-60%, +25%] / 0.53 | - |
| sA40>=1 rt | HOLD | +14% | 202631 | +10% | +2% .. +36% | +8% .. +25% | [-51%, +55%] / 0.73 | - |
| sA40>=1 rt | PRE | -63% | 202417 | -119% | -119% .. -15% | -177% .. -4% | [-172%, +11%] / 0.10 | - |
| sA40>=1 rt | X' | -5% | 202333 | -6% | -14% .. +11% | -25% .. +15% | [-64%, +50%] / 0.57 | - |
| sA40>=1 rt | F9 | +14% | 202631 | +24% | +2% .. +24% | +10% .. +25% | [-59%, +59%] / 0.79 | - |
| sA40>=2 half | L6M | +25% | 202631 | -5% | -5% .. +33% | -0% .. +35% | [-5%, +40%] / 0.78 | ONE-WEEK |
| sA40>=2 half | HOLD | +25% | 202631 | +4% | +4% .. +45% | +15% .. +33% | [-8%, +64%] / 0.92 | ONE-WEEK |
| sA40>=2 half | PRE | +8% | 202417 | -3% | -12% .. +22% | -31% .. +30% | [-47%, +32%] / 0.53 | - |
| sA40>=2 half | X' | +37% | 202333 | +27% | +27% .. +41% | +19% .. +42% | [+2%, +59%] / 0.96 | - |
| sA40>=2 half | F9 | +25% | 202631 | +4% | +4% .. +33% | +25% .. +37% | [-0%, +68%] / 0.93 | ONE-WEEK |
| sB40>=3 half | L6M | +1% | 202631 | +1% | -3% .. +4% | +0% .. +1% | [-5%, +1%] / 0.43 | - |
| sB40>=3 half | HOLD | +1% | 202631 | -7% | -7% .. +4% | -7% .. +1% | [-7%, +3%] / 0.20 | - |
| sB40>=3 half | PRE | +29% | 202417 | +25% | +5% .. +34% | +6% .. +30% | [-4%, +29%] / 0.88 | - |
| sB40>=3 half | X' | +41% | 202333 | +48% | +23% .. +48% | +22% .. +45% | [+8%, +57%] / 0.98 | - |
| sB40>=3 half | F9 | +1% | 202631 | -7% | -7% .. +4% | -7% .. +1% | [-7%, +1%] / 0.15 | - |
| sA60>=1 half | L6M | +43% | 202631 | +22% | +22% .. +48% | +0% .. +48% | [-4%, +50%] / 0.92 | - |
| sA60>=1 half | HOLD | +43% | 202631 | +29% | +24% .. +58% | +37% .. +48% | [+9%, +73%] / 0.97 | - |
| sA60>=1 half | PRE | -44% | 202417 | -70% | -108% .. -11% | -91% .. -14% | [-178%, +38%] / 0.29 | - |
| sA60>=1 half | X' | +41% | 202333 | +31% | +28% .. +47% | +25% .. +52% | [-16%, +61%] / 0.90 | - |
| sA60>=1 half | F9 | +43% | 202631 | +29% | +24% .. +48% | +37% .. +48% | [+2%, +75%] / 0.97 | - |
| sopen40 half | L6M | +19% | 202631 | -45% | -45% .. +37% | -71% .. +46% | [-114%, +71%] / 0.67 | ONE-WEEK |
| sopen40 half | HOLD | +19% | 202631 | -32% | -32% .. +40% | -8% .. +46% | [-21%, +63%] / 0.88 | ONE-WEEK |
| sopen40 half | PRE | +20% | 202417 | -7% | -11% .. +33% | -36% .. +30% | [-62%, +42%] / 0.60 | ONE-WEEK |
| sopen40 half | X' | +39% | 202333 | +37% | +27% .. +45% | +30% .. +45% | [+16%, +64%] / 0.98 | - |
| sopen40 half | F9 | +19% | 202631 | -32% | -32% .. +37% | -8% .. +46% | [-44%, +64%] / 0.82 | ONE-WEEK |

### 3b. Placebo ranks (share of draws with a maxDD cut >= the real cut; small = real beats chance), equal-risk mean, definition sensitivity, other frames

| cell | draws B/C/A | rank B same-volume L6M / F9 / PRE | rank C shuffled-day L6M / F9 / PRE | rank A random L6M / F9 / PRE | equal-risk (lscale; mean d $k/wk L6M / HOLD / PRE / X') | sensitivity x0.5 / 0.75 / 1.25 / 1.5 : F9 cut (L6M cut) | D-label | lock-off L6M / F9 cut | v1.1 (no U7) L6M / F9 cut |
|---|---|---|---|---|---|---|---|---|---|
| nA40>=1 skip | 20/20/20 | 0.35 / 0.35 / 0.10 | 0.55 / 0.50 / 0.10 | 0.30 / 0.30 / 0.10 | 1.07; -4.1 / -2.7 / -1.4 / +1.2 | -12% (-12%) / +10% (+10%) / +16% (+16%) / +34% (+34%) | FRAGILE | -12% / -12% | +14% / +14% |
| nA40>=1 half | 20/20/20 | 0.55 / 0.45 / 0.35 | 0.45 / 0.40 / 0.60 | 0.25 / 0.25 / 0.50 | 1.27; +2.9 / +4.6 / -4.2 / -1.2 | -5% (-5%) / +23% (+23%) / +40% (+40%) / +43% (+43%) | ROBUST-D | -29% / -29% | +2% / +2% |
| nB40>=1 skip | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | -11% (-11%) / -1% (-1%) / -23% (-23%) / -8% (-8%) | FRAGILE | -55% / -55% | -17% / -17% |
| nB40>=1 half | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | -2% (-2%) / +2% (+2%) / +10% (+10%) / +5% (+5%) | FRAGILE | -21% / -21% | -7% / -7% |
| nB40>=2 skip | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | +0% (+0%) / +3% (+3%) / -33% (-33%) / -17% (-17%) | FRAGILE | -26% / -26% | -2% / -2% |
| nB40>=2 half | 20/20/20 | 0.65 / 0.65 / 0.05 | 0.75 / 0.75 / 0.05 | 0.45 / 0.45 / 0.00 | 1.05; +0.0 / +2.0 / -0.4 / +3.2 | +1% (+1%) / +2% (+2%) / +0% (+0%) / +11% (+11%) | FRAGILE | +2% / +2% | +2% / +2% |
| nB40>=3 skip | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | +0% (+0%) / -0% (-0%) / +4% (+4%) / -35% (-35%) | FRAGILE | -15% / -15% | -7% / -7% |
| nB40>=3 half | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | +0% (+0%) / +2% (+2%) / +5% (+5%) / +1% (+1%) | ROBUST-D | -5% / -5% | -6% / -6% |
| nT40>=2 half | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | -6% (-6%) / -4% (-4%) / +25% (+25%) / +17% (+17%) | FRAGILE | -38% / -38% | -4% / -4% |
| nT40>=4 half | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | +0% (+0%) / +0% (+0%) / -2% (-2%) / +3% (+3%) | FRAGILE | -5% / -5% | -3% / -3% |
| nA60>=1 skip | 20/20/20 | 0.45 / 0.45 / 0.05 | 0.40 / 0.40 / 0.15 | 0.10 / 0.00 / 0.35 | 1.00; -3.5 / -2.5 / -4.4 / +2.5 | +10% (+10%) / +37% (+37%) / +39% (+47%) / +36% (+47%) | ROBUST-D | +16% / +16% | +38% / +38% |
| nA60>=1 half | 20/20/20 | 0.15 / 0.10 / 0.70 | 0.35 / 0.30 / 0.95 | 0.15 / 0.15 / 0.95 | 1.30; +2.5 / +2.7 / -6.5 / +1.0 | +23% (+23%) / +11% (+11%) / +47% (+47%) / +43% (+43%) | FRAGILE | -3% / -3% | +13% / +13% |
| nA60>=2 half | 20/20/19 | 0.45 / 0.30 / 0.35 | 0.50 / 0.50 / 0.30 | 0.11 / 0.11 / 0.47 | 1.11; +2.8 / +2.0 / -2.9 / +0.7 | -3% (-3%) / +33% (+33%) / +29% (+29%) / -1% (-1%) | ROBUST-D | -35% / -35% | -6% / -6% |
| nT60>=3 skip | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | -6% (-6%) / -9% (-9%) / -7% (-7%) / -14% (-14%) | FRAGILE | -69% / -69% | -36% / -36% |
| nTany40>=2 half | 20/19/20 | 0.80 / 0.80 / 0.55 | 0.89 / 0.89 / 0.37 | 0.70 / 0.60 / 0.35 | 1.36; +5.8 / +6.2 / -1.8 / +1.9 | - / - / - / - | - | -67% / -67% | -1% / -1% |
| open20 half | 19/20/19 | 0.63 / 0.58 / 0.58 | 0.55 / 0.55 / 0.85 | 0.32 / 0.26 / 0.63 | 1.77; -4.7 / +0.6 / -5.0 / +1.7 | +57% (+57%) / +56% (+56%) / +14% (+14%) / +15% (+15%) | FRAGILE | +52% / +52% | +51% / +51% |
| open60 half | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | +15% (+15%) / +10% (+10%) / +24% (+50%) / +34% (+63%) | FRAGILE | +15% / +15% | +36% / +36% |
| openA40 half | 20/19/20 | 0.85 / 0.80 / 0.35 | 0.74 / 0.74 / 0.32 | 0.75 / 0.75 / 0.50 | 1.65; -6.2 / -0.6 / -4.2 / +3.9 | +50% (+50%) / +41% (+41%) / +6% (+6%) / -1% (-1%) | FRAGILE | +19% / +19% | +20% / +20% |
| rho40>=2 skip | 19/20/19 | 0.21 / 0.16 / 0.37 | 0.20 / 0.15 / 0.30 | 0.05 / 0.05 / 0.21 | 1.15; +0.1 / +1.4 / -1.9 / +0.3 | - / - / - / - | - | -1% / -1% | +21% / +21% |
| rho40<=0.5 skip | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | - / - / - / - | - | -22% / -22% | -10% / -10% |
| rho60>=2 skip | 20/19/20 | 0.05 / 0.05 / 0.30 | 0.32 / 0.16 / 0.16 | 0.15 / 0.15 / 0.40 | 1.00; +1.4 / +0.6 / -1.8 / +0.6 | - / - / - / - | - | +12% / +12% | +40% / +40% |
| rho60>=2 half | 19/20/19 | 0.21 / 0.21 / 0.11 | 0.35 / 0.35 / 0.10 | 0.00 / 0.00 / 0.16 | 1.17; -1.0 / +1.3 / -2.4 / +1.8 | - / - / - / - | - | -8% / -8% | +23% / +23% |
| rho60<=0.5 half | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | - / - / - / - | - | -22% / -22% | -6% / -6% |
| mid_PDR half | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | - / - / - / - | - | -91% / -91% | -0% / -0% |
| mid_any3 half | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | - / - / - / - | - | -81% / -81% | -14% / -14% |
| mid_PDR&open40 up | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | - / - / - / - | - | +14% / +14% | +27% / +27% |
| mid_ON&nT40<=1 up | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | - / - / - / - | - | +9% / +9% | +6% / +6% |
| sA40>=1 skip | 20/20/20 | 0.05 / 0.00 / 0.05 | 0.25 / 0.20 / 0.20 | 0.20 / 0.15 / 0.10 | 1.03; -4.1 / -3.1 / -2.5 / +1.5 | +8% (+8%) / +37% (+37%) / +39% (+44%) / +40% (+45%) | ROBUST-D | +16% / +16% | +60% / +53% |
| sA40>=1 half | 20/20/20 | 0.05 / 0.05 / 0.65 | 0.35 / 0.30 / 0.65 | 0.10 / 0.10 / 0.45 | 1.27; +0.2 / +2.6 / -3.9 / -1.2 | +22% (+22%) / +11% (+11%) / +47% (+47%) / +43% (+43%) | FRAGILE | -1% / -1% | +24% / +24% |
| sA40>=1 rt | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | - / - / - / - | - | - | - |
| sA40>=2 half | 20/20/20 | 0.30 / 0.25 / 0.30 | 0.50 / 0.50 / 0.50 | 0.10 / 0.10 / 0.40 | 1.22; +4.4 / +4.2 / -3.1 / +1.6 | -3% (-3%) / +33% (+33%) / +29% (+29%) / -0% (-0%) | ROBUST-D | -36% / -36% | -6% / -6% |
| sB40>=3 half | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | +2% (+2%) / +4% (+4%) / +9% (+9%) / +7% (+7%) | ROBUST-D | -1% / -1% | -7% / -7% |
| sA60>=1 half | 20/20/20 | 0.25 / 0.20 / 0.70 | 0.20 / 0.15 / 0.75 | 0.20 / 0.20 / 0.90 | 1.33; +1.2 / +1.2 / -5.3 / +0.0 | +11% (+11%) / +43% (+43%) / +40% (+40%) / +47% (+47%) | ROBUST-D | -8% / -8% | +36% / +36% |
| sopen40 half | 0/0/0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a / n/a / n/a | n/a | +15% (+15%) / +17% (+17%) / +31% (+50%) / +27% (+63%) | ROBUST-D | +12% / +12% | +31% / +31% |

### 3c. Labels (RISK-KEEP = L6M cut >= 20% with mean delta inside MDE, placebo ranks B, C, A <= 0.10 (L6M), HOLD/PRE/X' cuts > 0, not ONE-WEEK; (volume effect) = rank B > 0.10; (L6M only) = HOLD/PRE/X' disagree)

| cell | L6M cut | F9 cut | PRE / X' cut | mean d L6M (MDE) | S/T/N | TOL-B/nc | ONE-WEEK (L6M/F9) | rank B/C/A L6M | label |
|---|---|---|---|---|---|---|---|---|---|
| nA40>=1 skip | +23% | +23% | +10% / +23% | -5.9 (+9.3) | Y/Y/Y | Y/Y | Y/Y | 0.35/0.55/0.30 | ONE-WEEK (not a lead) |
| nA40>=1 half | +28% | +28% | -10% / +26% | -0.9 (+6.1) | n/n/n | n/n | Y/Y | 0.55/0.45/0.25 | ONE-WEEK (not a lead) |
| nB40>=1 skip | -24% | -24% | +51% / +64% | -2.7 (+6.9) | n/n/n | n/n | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| nB40>=1 half | -5% | -5% | +29% / +36% | -1.5 (+3.7) | n/n/n | n/n | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| nB40>=2 skip | -0% | -0% | +27% / +45% | +0.9 (+3.1) | n/n/n | n/n | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| nB40>=2 half | +7% | +7% | +23% / +44% | +0.6 (+1.5) | n/Y/Y | Y/Y | n/n | 0.65/0.75/0.45 | (volume effect) |
| nB40>=3 skip | -1% | -1% | +31% / +31% | +0.1 (+1.8) | n/n/n | n/n | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| nB40>=3 half | +3% | +3% | +27% / +40% | +0.2 (+0.8) | n/Y/Y | Y/Y | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| nT40>=2 half | -3% | -3% | +13% / +60% | -1.4 (+2.9) | n/n/n | n/n | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| nT40>=4 half | -2% | -2% | -2% / +61% | -0.2 (+0.6) | n/n/n | n/n | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| nA60>=1 skip | +34% | +34% | -1% / +7% | -3.5 (+13.0) | n/n/Y | Y/Y | n/n | 0.45/0.40/0.10 | (volume effect) |
| nA60>=1 half | +43% | +43% | -48% / +46% | -3.0 (+12.9) | n/n/Y | n/n | n/n | 0.15/0.35/0.15 | (volume effect) |
| nA60>=2 half | +25% | +25% | +5% / +24% | +0.3 (+5.0) | n/n/n | n/n | Y/Y | 0.45/0.50/0.11 | ONE-WEEK (not a lead) |
| nT60>=3 skip | -39% | -39% | -3% / +64% | -4.5 (+11.9) | n/n/n | n/n | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| nTany40>=2 half | +21% | +21% | +5% / +43% | -1.7 (+10.2) | n/n/n | n/n | Y/Y | 0.80/0.89/0.70 | ONE-WEEK (not a lead) |
| open20 half | +43% | +43% | -0% / +30% | -13.1 (+15.6) | n/n/Y | n/n | n/n | 0.63/0.55/0.32 | (volume effect) |
| open60 half | +24% | +24% | -13% / +5% | -11.7 (+18.0) | n/n/n | n/n | Y/Y | n/a/n/a/n/a | ONE-WEEK (not a lead) |
| openA40 half | +28% | +28% | +20% / +59% | -13.2 (+16.9) | n/n/n | n/n | n/n | 0.85/0.74/0.75 | (volume effect) |
| rho40>=2 skip | +37% | +37% | -13% / +19% | -2.4 (+8.9) | n/n/Y | Y/Y | n/n | 0.21/0.20/0.05 | (volume effect) |
| rho40<=0.5 skip | -28% | -28% | +18% / +68% | -1.3 (+5.8) | n/n/n | n/n | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| rho60>=2 skip | +34% | +34% | -16% / -10% | +1.4 (+11.2) | n/n/Y | Y/Y | n/n | 0.05/0.32/0.15 | (L6M only) |
| rho60>=2 half | +30% | +30% | +11% / +42% | -2.2 (+11.8) | Y/Y/Y | Y/Y | n/n | 0.21/0.35/0.00 | (volume effect) |
| rho60<=0.5 half | +10% | +10% | -44% / +27% | -1.1 (+4.7) | n/n/n | n/n | Y/Y | n/a/n/a/n/a | ONE-WEEK (not a lead) |
| mid_PDR half | +19% | +19% | +11% / +48% | -4.5 (+8.1) | n/n/n | n/n | Y/Y | n/a/n/a/n/a | ONE-WEEK (not a lead) |
| mid_any3 half | -1% | -1% | +14% / +54% | -5.3 (+8.2) | n/n/n | n/n | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| mid_PDR&open40 up | +24% | +24% | -20% / -3% | +5.1 (+5.2) | n/n/Y | n/n | Y/Y | n/a/n/a/n/a | ONE-WEEK (not a lead) |
| mid_ON&nT40<=1 up | +6% | +6% | +8% / -2% | -2.2 (+11.7) | n/n/Y | n/n | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| sA40>=1 skip | +39% | +39% | +15% / +22% | -3.5 (+13.3) | Y/Y/Y | Y/Y | n/n | 0.05/0.25/0.20 | LEAD-unconfirmed |
| sA40>=1 half | +43% | +43% | -9% / +28% | -2.9 (+12.9) | n/n/Y | n/n | n/n | 0.05/0.35/0.10 | (L6M only) |
| sA40>=1 rt | +14% | +14% | -63% / -5% | -2.9 (+8.8) | n/n/Y | n/n | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| sA40>=2 half | +25% | +25% | +8% / +37% | +0.5 (+5.0) | n/n/n | n/n | Y/Y | 0.30/0.50/0.10 | ONE-WEEK (not a lead) |
| sB40>=3 half | +1% | +1% | +29% / +41% | +0.1 (+1.9) | n/Y/Y | Y/Y | n/n | n/a/n/a/n/a | UNTESTED (placebo draws pending) |
| sA60>=1 half | +43% | +43% | -44% / +41% | -4.9 (+14.1) | n/n/Y | n/n | n/n | 0.25/0.20/0.20 | (volume effect) |
| sopen40 half | +19% | +19% | +20% / +39% | -11.7 (+17.6) | n/n/n | n/n | Y/Y | n/a/n/a/n/a | ONE-WEEK (not a lead) |

### 3d. Per book x session maxDD cut of the same run (rule applied everywhere; cut = 1 - cell/base within the book or session; windows L6M | HOLD | PRE | X')

| cell | K6 | P6 | U6 | H6 | M6 | A6 | asia | london | nyam | nypm |
|---|---|---|---|---|---|---|---|---|---|---|
| nA40>=1 skip | +31%/+16%/-66%/+54% | +44%/-91%/-13%/+40% | -24%/-24%/+15%/-67% | -79%/-45%/+39%/-65% | +5%/+22%/+9%/+37% | -69%/-47%/-10%/-66% | +8%/+17%/-13%/-1% | +23%/+16%/+7%/+53% | -19%/-144%/-85%/+10% | +54%/+40%/-83%/-38% |
| nA40>=1 half | +23%/+26%/-62%/+55% | +45%/-25%/-114%/+27% | -60%/-60%/+15%/+13% | +28%/+21%/-10%/+39% | +7%/+21%/+10%/+11% | +22%/+30%/+12%/-11% | +16%/+24%/-27%/+41% | +17%/+17%/-30%/+45% | +21%/-118%/-52%/-34% | +22%/+9%/-71%/+4% |
| nB40>=1 skip | -7%/-23%/-34%/+63% | -1%/-11%/+16%/+67% | +5%/+3%/+27%/-106% | -23%/+0%/-27%/+53% | -3%/-5%/+35%/-22% | -34%/-17%/+22%/-45% | +12%/+20%/-31%/+54% | -28%/-28%/+31%/+68% | -5%/-56%/-70%/+27% | -5%/-63%/-62%/+20% |
| nB40>=1 half | -27%/+3%/-4%/+6% | +2%/+2%/+11%/+36% | +11%/-3%/+15%/+28% | +23%/+11%/-16%/+55% | -17%/+7%/+27%/+10% | -11%/+4%/+25%/+16% | +7%/+16%/-6%/+28% | -27%/-27%/+39%/+71% | -9%/+4%/-62%/-13% | -21%/-51%/-7%/+28% |
| nB40>=2 skip | +6%/+11%/-18%/+26% | -1%/-1%/+3%/+45% | -14%/-14%/-6%/-28% | -0%/+19%/-12%/+50% | +3%/+7%/+11%/+30% | +0%/+10%/+17%/-34% | +8%/+16%/-89%/+43% | -11%/-11%/+35%/+55% | -10%/+14%/-6%/+13% | -21%/-20%/-16%/-20% |
| nB40>=2 half | +2%/+17%/-5%/+17% | +1%/+1%/+27%/+41% | +0%/+0%/-4%/-2% | +10%/+8%/+10%/+31% | +1%/+3%/+5%/+20% | +0%/+13%/+17%/-18% | +5%/+14%/-2%/+23% | -5%/-5%/+10%/+59% | -5%/+4%/-15%/+13% | +0%/-17%/-9%/-1% |
| nB40>=3 skip | +3%/+19%/-19%/-3% | +0%/+0%/+12%/+26% | +0%/+0%/-15%/-10% | -17%/+5%/+10%/+29% | +0%/+9%/-2%/+23% | +0%/+0%/-11%/-19% | +3%/+7%/-20%/+32% | -13%/-13%/+32%/+37% | -6%/-27%/-10%/+20% | +0%/+27%/-2%/-21% |
| nB40>=3 half | -1%/-2%/-3%/+7% | +0%/+0%/+19%/+37% | +0%/-21%/-1%/-14% | -2%/+5%/+10%/+22% | +0%/+5%/+3%/+24% | +0%/+0%/+1%/+2% | +1%/+6%/-10%/+17% | -1%/-1%/+22%/+34% | +0%/-20%/+4%/+20% | +0%/-21%/+0%/-2% |
| nT40>=2 half | -3%/+14%/-7%/+42% | +1%/+1%/-20%/+59% | -15%/-15%/+10%/+3% | -3%/+16%/+14%/+27% | -6%/+7%/+23%/+36% | -10%/+5%/+24%/-9% | +2%/+11%/-8%/+37% | -6%/-6%/+30%/+75% | -13%/+8%/-47%/+18% | +0%/-30%/-65%/-3% |
| nT40>=4 half | -2%/+0%/-3%/+29% | +0%/+0%/-19%/+56% | +0%/+0%/+22%/+2% | +0%/+2%/+3%/+27% | +1%/-6%/+2%/+20% | +0%/+0%/+0%/+5% | -1%/+2%/-9%/+28% | +2%/+2%/+31%/+52% | +0%/+5%/+3%/+10% | +0%/-16%/-25%/+35% |
| nA60>=1 skip | +43%/-6%/-30%/+48% | +33%/-66%/-12%/+29% | +23%/-51%/-23%/-95% | -9%/+12%/+21%/-111% | +24%/+45%/-10%/+30% | -72%/-49%/+16%/-43% | +6%/+15%/+1%/-9% | +29%/+18%/-134%/+60% | +28%/-121%/-81%/+1% | +9%/+34%/-187%/-27% |
| nA60>=1 half | +42%/+30%/-79%/+39% | +41%/+23%/-137%/+52% | -8%/-8%/-16%/-27% | +32%/+30%/-3%/+58% | +15%/+26%/+11%/+18% | +40%/+9%/-7%/-22% | +18%/+26%/-23%/+21% | +33%/+26%/-34%/+51% | +28%/-101%/-50%/+2% | +34%/-20%/-81%/+4% |
| nA60>=2 half | +39%/+21%/-8%/+29% | +40%/-10%/-88%/+28% | -25%/-25%/+17%/+14% | +10%/+18%/-9%/+28% | +11%/+34%/+22%/+32% | +22%/+15%/-17%/-32% | +17%/+25%/-21%/+5% | +38%/+16%/+42%/+29% | -22%/-172%/-54%/+14% | +12%/+25%/+8%/+17% |
| nT60>=3 skip | +26%/-2%/+7%/+30% | +3%/+3%/-41%/+51% | -18%/-18%/+11%/-19% | -72%/-40%/-0%/+40% | -3%/+1%/+10%/+4% | -24%/-8%/-19%/-24% | -8%/+2%/-39%/+64% | -9%/-9%/+8%/+45% | +6%/-30%/-73%/+20% | +14%/-66%/-188%/-36% |
| nTany40>=2 half | +53%/+27%/-6%/+54% | +28%/+28%/-56%/+46% | +2%/+2%/+28%/+29% | -9%/+2%/+16%/+23% | +21%/+24%/+23%/+49% | +13%/+6%/+41%/+27% | +20%/+27%/-1%/+27% | +18%/+18%/+32%/+67% | +44%/+34%/-54%/+12% | +0%/-55%/-110%/-22% |
| open20 half | +6%/+44%/+55%/+29% | +58%/+58%/-30%/+33% | +49%/+49%/+32%/-30% | +52%/+44%/+54%/+24% | +51%/+59%/+21%/+18% | +36%/+33%/+27%/+42% | +41%/+47%/+3%/+32% | +63%/+63%/-22%/+48% | +68%/+60%/+39%/+35% | +1%/+34%/-9%/-57% |
| open60 half | -1%/+12%/+30%/+2% | +50%/+39%/-17%/+15% | -59%/-59%/+5%/-50% | -85%/-50%/+0%/+1% | +45%/+56%/+8%/+14% | +44%/-17%/+4%/+10% | +11%/+13%/-1%/+16% | +13%/+13%/-50%/+17% | +55%/+68%/+55%/+29% | +13%/+3%/-35%/-36% |
| openA40 half | +1%/+27%/+38%/+29% | +59%/+52%/+5%/+47% | +27%/+27%/+30%/-19% | -13%/+8%/+9%/+27% | +40%/+49%/+39%/+26% | +47%/+19%/+32%/+49% | +33%/+39%/-14%/+41% | +25%/+25%/-10%/+27% | +58%/+45%/+27%/+55% | +45%/+63%/-15%/+14% |
| rho40>=2 skip | +17%/+35%/-41%/+5% | +45%/-73%/-55%/+19% | -14%/-14%/+10%/-50% | -36%/-10%/-11%/-48% | +15%/+38%/+10%/+51% | -24%/-8%/-6%/-20% | +19%/+27%/-54%/-15% | +47%/+33%/-2%/+42% | -15%/-182%/-78%/-6% | +53%/+68%/-98%/-26% |
| rho40<=0.5 skip | -51%/-3%/-52%/+31% | +0%/+0%/+19%/+69% | +5%/-0%/-12%/-16% | +4%/+20%/-32%/+60% | -5%/-1%/+35%/-32% | -36%/-18%/+22%/-18% | +12%/+20%/+6%/+50% | -17%/-17%/+29%/+65% | +8%/-48%/-117%/+25% | -11%/-61%/-36%/+8% |
| rho60>=2 skip | +12%/+11%/+30%/-27% | +33%/-9%/-54%/+2% | +23%/-14%/+14%/-49% | -25%/-2%/+27%/-39% | +20%/+44%/+4%/+12% | -70%/-48%/+8%/+23% | +20%/+27%/-26%/-16% | +49%/+22%/-18%/+10% | +22%/-189%/-35%/-15% | +40%/+38%/-81%/-4% |
| rho60>=2 half | +20%/+33%/-2%/-46% | +28%/+28%/-11%/+62% | +18%/+18%/+16%/-64% | +24%/+17%/-1%/+43% | +4%/+18%/+22%/+32% | +31%/+20%/-8%/+10% | +7%/+16%/+2%/+9% | +42%/+30%/+48%/+38% | +18%/-70%/-24%/+3% | +29%/-5%/-10%/-98% |
| rho60<=0.5 half | +23%/+17%/-27%/-9% | +36%/+36%/-68%/+26% | -28%/-28%/+23%/-8% | -12%/+9%/+12%/+17% | +11%/+30%/+2%/+24% | +12%/+24%/+27%/+41% | +19%/+27%/-9%/+5% | +29%/+29%/-33%/+40% | -43%/+16%/-95%/+29% | +14%/-26%/-44%/-57% |
| mid_PDR half | +7%/+32%/+7%/+55% | +36%/+23%/-12%/+40% | -30%/-30%/-12%/+2% | -63%/-32%/+5%/-27% | +23%/+25%/+8%/+31% | +18%/+25%/+18%/+17% | +2%/+11%/-31%/+6% | +52%/+45%/+36%/+50% | -38%/-36%/-68%/+6% | +12%/-7%/-32%/+18% |
| mid_any3 half | +6%/+44%/+10%/+56% | +33%/+32%/-1%/+51% | +20%/+20%/+13%/-50% | -62%/-31%/+2%/-9% | +26%/+9%/+11%/+43% | +26%/+14%/+10%/+30% | +2%/+12%/-14%/+32% | +37%/+36%/+7%/+40% | -10%/-16%/-2%/+22% | +48%/+19%/-41%/-47% |
| mid_PDR&open40 up | -21%/-22%/-31%/-9% | +17%/+17%/-34%/-8% | -15%/-15%/-10%/+0% | -6%/+13%/-74%/+0% | -5%/+7%/+22%/+1% | +28%/+2%/-13%/+2% | -12%/-2%/-89%/+2% | +10%/+7%/-5%/+2% | +4%/-36%/-48%/+1% | +38%/-92%/-50%/-1% |
| mid_ON&nT40<=1 up | +1%/-4%/-108%/-10% | +8%/+8%/+10%/-4% | -138%/-138%/+2%/+0% | -60%/-30%/-13%/-1% | +8%/+32%/-10%/+4% | +11%/+12%/+0%/-5% | -0%/+9%/-20%/-3% | +4%/+4%/-41%/+1% | +3%/+33%/-4%/-0% | -54%/-49%/-48%/+17% |
| sA40>=1 skip | +43%/-2%/-98%/+44% | +39%/-82%/-21%/+42% | +23%/-51%/+15%/-75% | -9%/+12%/+47%/-74% | +24%/+45%/+9%/+27% | -72%/-49%/+6%/-73% | +14%/+22%/-13%/-4% | +24%/+14%/-11%/+49% | +8%/-98%/-97%/+10% | +9%/+39%/-143%/-47% |
| sA40>=1 half | +42%/+37%/-56%/+51% | +41%/+21%/-106%/+29% | -8%/-8%/+17%/+14% | +32%/+28%/+8%/+39% | +15%/+26%/+10%/+10% | +40%/+17%/+20%/-11% | +18%/+26%/-25%/+41% | +30%/+27%/-33%/+42% | +28%/-100%/-52%/-34% | +34%/-20%/-66%/+4% |
| sA40>=1 rt | -1%/+40%/-24%/-16% | -2%/-2%/-73%/+7% | -15%/-48%/+9%/-76% | -21%/-12%/-14%/-57% | +4%/+23%/-7%/-8% | +22%/-19%/+5%/-18% | -14%/-3%/-50%/+9% | +2%/+2%/-8%/+0% | +21%/-82%/-42%/+18% | +66%/+16%/-170%/-50% |
| sA40>=2 half | +30%/+20%/+4%/+4% | +40%/+19%/-27%/+42% | -21%/-21%/+7%/-3% | +12%/+18%/-17%/+34% | +11%/+30%/+21%/+26% | +22%/+15%/+4%/-20% | +17%/+25%/-20%/+7% | +35%/+31%/+42%/+28% | -22%/-128%/-33%/+25% | +12%/+10%/+11%/+6% |
| sB40>=3 half | -4%/+9%/-2%/+7% | +2%/+2%/+21%/+39% | +0%/+0%/-6%/-14% | -10%/+5%/+11%/+24% | -6%/-1%/+2%/+20% | +0%/+13%/+1%/-4% | +3%/+5%/-2%/+21% | -3%/-3%/+23%/+33% | -9%/-11%/-10%/+21% | -3%/-25%/-23%/-2% |
| sA60>=1 half | +17%/+32%/-85%/+37% | +38%/+37%/-135%/+48% | +4%/-11%/+4%/-27% | +37%/+20%/-7%/+55% | +23%/+22%/+10%/+16% | +24%/+14%/-23%/-15% | +39%/+45%/-34%/+18% | -3%/-6%/-21%/+51% | -31%/-11%/-64%/+2% | +22%/-27%/-54%/+4% |
| sopen40 half | -1%/+22%/+52%/+29% | +50%/+46%/+28%/+44% | -59%/-59%/+5%/-14% | -86%/-51%/+35%/+48% | +46%/+61%/+14%/+26% | +45%/-36%/+12%/+6% | +10%/+1%/+1%/+32% | +10%/+10%/-41%/+27% | +55%/+59%/+51%/+46% | +13%/+16%/-43%/+4% |

## 4. Finalists re-run on D7 v1.3 (v1.2 + gated take lines U6/P6, best-effort; BASE-3)

Base lines moved (v1.2 > v1.3): L6M mean/maxDD 26.0/127.8 > 21.3/94.1; PRE 13.2/113.8 > 2.9/175.1; MID 11.3/92.1 > 19.7/43.1. Episode (v1.3 base maxDD week L6M / F9 / PRE): 202634 / 202634 / 202509.

| cell (v1.3) | maxDD cut L3M / L6M / HOLD / MID / PRE / X' / F9 | mean d $k/wk L6M (MDE) / PRE (MDE) | worst-20 PRE base>cell $k | S/T/N | TOL-B / nc | week carrying v1.3 base maxDD (L6M) | cut without it | ONE-WEEK (L6M/F9) | same sign as v1.2 L6M / PRE |
|---|---|---|---|---|---|---|---|---|---|
| nA40>=1 skip | +1% / -16% / -16% / +31% / -31% / +5% / -16% | -1.5 (+7.4) / +5.0 (+7.7) | -456>-499 | n/n/n | n / n | 202634 | -23% | n/n | n / n |
| nA40>=1 half | +32% / +14% / +14% / +39% / -34% / +20% / +14% | +1.4 (+8.1) / -0.8 (+4.3) | -456>-425 | n/n/Y | n / Y | 202634 | +8% | n/n | Y / Y |
| nB40>=1 skip | -12% / -9% / -37% / -94% / +46% / +60% / -9% | +3.5 (+13.8) / +2.5 (+6.8) | -456>-442 | n/n/n | n / n | 202634 | +1% | n/n | Y / Y |
| nB40>=1 half | +8% / +9% / +9% / -59% / +6% / +41% / +9% | +0.8 (+3.7) / +1.7 (+3.3) | -456>-433 | n/Y/Y | Y / Y | 202634 | +8% | n/n | n / Y |
| nB40>=2 skip | +20% / -1% / -1% / -91% / +4% / +33% / -1% | +4.3 (+8.9) / +5.5 (+6.0) | -456>-429 | n/n/n | n / n | 202634 | -4% | n/n | Y / Y |
| nB40>=2 half | +17% / +3% / +3% / -73% / -3% / +41% / +3% | +1.2 (+2.2) / +2.5 (+3.5) | -456>-439 | n/n/Y | Y / Y | 202634 | -2% | n/n | Y / n |
| nB40>=3 skip | -18% / -9% / -9% / -1% / +3% / +33% / -9% | -0.1 (+1.7) / +2.3 (+4.4) | -456>-442 | n/n/n | n / n | 202634 | -8% | n/n | Y / Y |
| nB40>=3 half | -10% / -5% / -5% / -15% / +6% / +37% / -5% | +0.5 (+2.0) / +1.4 (+2.9) | -456>-448 | n/n/n | n / n | 202634 | -3% | n/n | n / Y |
| nT40>=2 half | +13% / +8% / +8% / -16% / -5% / +37% / +8% | +1.7 (+3.7) / +0.1 (+4.7) | -456>-436 | n/n/Y | Y / Y | 202634 | +9% | n/n | n / n |
| nT40>=4 half | -6% / -2% / -2% / -5% / -7% / +35% / -2% | -0.2 (+0.5) / +0.5 (+2.4) | -456>-471 | n/n/n | n / n | 202634 | +0% | n/n | Y / Y |
| nA60>=1 skip | +15% / +31% / +3% / -19% / +7% / -27% / +31% | +1.8 (+9.8) / +4.1 (+8.8) | -456>-442 | n/Y/Y | Y / Y | 202634 | +26% | n/n | Y / n |
| nA60>=1 half | +38% / +25% / +25% / +39% / -23% / +17% / +25% | +0.2 (+11.1) / -1.3 (+4.2) | -456>-388 | n/n/Y | Y / Y | 202634 | +13% | n/n | Y / Y |
| nA60>=2 half | +61% / +26% / +26% / -1% / -55% / -7% / +26% | +4.4 (+9.2) / -1.1 (+2.9) | -456>-440 | n/n/Y | n / Y | 202634 | +10% | Y/Y | Y / n |
| nT60>=3 skip | -52% / -51% / -51% / -32% / -29% / +41% / -51% | +5.3 (+14.1) / +1.7 (+7.3) | -456>-492 | n/n/n | n / n | 202634 | -58% | n/n | Y / Y |
| nTany40>=2 half | -4% / +2% / +2% / -1% / +13% / +32% / +2% | +3.0 (+10.0) / +0.9 (+4.5) | -456>-392 | n/n/n | n / n | 202634 | +11% | n/n | Y / Y |
| open20 half | +59% / +37% / +37% / +28% / +22% / +11% / +37% | -7.1 (+16.6) / -1.8 (+6.9) | -456>-273 | Y/Y/Y | Y / Y | 202634 | +33% | n/n | Y / n |
| open60 half | -38% / +30% / +30% / +29% / +29% / +5% / +30% | -4.9 (+17.9) / -0.1 (+6.0) | -456>-370 | n/n/n | n / n | 202634 | +29% | n/n | Y / n |
| openA40 half | +14% / +30% / +30% / +11% / +35% / +60% / +30% | -5.0 (+16.6) / -0.3 (+7.7) | -456>-333 | Y/Y/Y | Y / Y | 202634 | +27% | n/n | Y / Y |
| rho40>=2 skip | +46% / +16% / +14% / +31% / -15% / -3% / +16% | +1.5 (+7.3) / +2.3 (+6.3) | -456>-451 | n/n/Y | Y / Y | 202634 | +1% | Y/Y | Y / Y |
| rho40<=0.5 skip | +9% / -8% / -8% / -114% / +46% / +63% / -8% | +5.2 (+13.7) / +2.7 (+6.6) | -456>-425 | n/n/n | n / n | 202634 | -11% | n/n | Y / Y |
| rho60>=2 skip | +33% / +53% / +26% / +16% / +22% / -17% / +53% | +8.7 (+11.9) / +3.8 (+6.8) | -456>-449 | n/Y/Y | Y / Y | 202634 | +43% | n/n | Y / n |
| rho60>=2 half | +45% / +21% / +21% / +38% / +15% / +6% / +21% | +1.2 (+11.9) / +1.5 (+3.3) | -456>-405 | Y/Y/Y | Y / Y | 202634 | +5% | Y/Y | Y / Y |
| rho60<=0.5 half | +30% / -6% / -6% / +16% / -13% / +18% / -6% | +2.6 (+9.6) / +3.3 (+6.4) | -456>-465 | n/n/n | n / n | 202634 | -17% | n/n | n / Y |
| mid_PDR half | +11% / +11% / +11% / -39% / +16% / +27% / +11% | -4.3 (+6.6) / +2.1 (+4.6) | -456>-398 | n/Y/Y | Y / Y | 202634 | +15% | n/n | Y / Y |
| mid_any3 half | -39% / -15% / -15% / -60% / +38% / +31% / -15% | -4.8 (+12.5) / +2.6 (+5.6) | -456>-401 | n/n/n | n / n | 202634 | +1% | n/n | Y / Y |
| mid_PDR&open40 up | +21% / +8% / +8% / +16% / -61% / -8% / +8% | +3.8 (+4.3) / -1.4 (+3.0) | -456>-526 | n/n/Y | n / n | 202634 | -8% | n/n | Y / Y |
| mid_ON&nT40<=1 up | +26% / -10% / -10% / -18% / -68% / +4% / -10% | -0.3 (+4.9) / -1.5 (+3.1) | -456>-502 | n/n/n | n / n | 202634 | -33% | n/n | n / n |
| sA40>=1 skip | +15% / +32% / +15% / -19% / -21% / -3% / +32% | +2.1 (+10.2) / +3.3 (+8.2) | -456>-464 | n/n/Y | n / n | 202634 | +28% | n/n | Y / n |
| sA40>=1 half | +38% / +25% / +25% / +39% / -29% / +21% / +25% | +0.4 (+11.1) / -1.0 (+4.6) | -456>-401 | n/n/Y | n / Y | 202634 | +13% | n/n | Y / Y |
| sA40>=1 rt | +13% / +12% / -0% / +45% / -37% / +4% / +12% | -5.3 (+11.7) / +0.4 (+7.2) | -456>-467 | n/n/Y | n / n | 202634 | +1% | Y/Y | Y / Y |
| sA40>=2 half | +61% / +26% / +26% / -0% / -11% / +5% / +26% | +4.5 (+9.2) / -0.0 (+3.3) | -456>-440 | n/n/Y | Y / Y | 202634 | +10% | Y/Y | Y / n |
| sB40>=3 half | +6% / -3% / -3% / -17% / -14% / +25% / -3% | +0.7 (+2.5) / +2.4 (+4.0) | -456>-454 | n/n/n | n / n | 202634 | -2% | n/n | n / n |
| sA60>=1 half | +58% / +31% / +31% / +33% / -2% / +15% / +31% | -1.7 (+11.6) / -0.5 (+4.7) | -456>-400 | n/n/Y | Y / Y | 202634 | +19% | n/n | Y / Y |
| sopen40 half | -53% / +25% / +25% / +6% / +32% / +4% / +25% | -5.0 (+18.1) / +1.3 (+7.7) | -456>-327 | n/n/n | n / n | 202634 | +16% | n/n | Y / Y |

## 5. Exact D7-computable definitions (all causal at the signal second; D7 needs nothing but its own 8 line values and the entry price E)

Inputs per signal: the 8 SET8 lines' current FRESH level (never touched since formed; the same value D7 already uses for the D20 zone test) for the stream's nearest POI on each side. Side s = +1 long / -1 short. For a line at price L: ahead distance a = s*(L - E) if >= 0, behind distance b = s*(E - L) if >= 0 (a line exactly at E counts as ahead, distance 0); one value per line (the nearest on each side; NaN = none). Not restricted by the trade's target or stop distance (the shipped D20 test restricts ahead to the target; the density counts do not).
* nA_x = number of the 8 lines with a <= x; nB_x = number with b <= x; nT_x = nA_x + nB_x; dA = min a, dmin = min over a and b (inf if none); rho_x = (nA_x+1)/(nB_x+1). Price-scaled form (A1): x_s = x * E / 20000 (x in pts at 20,000).
* Rules (act on the signal before the lock engine, like the zone half): SKIP = drop the signal; HALF = planned lots x0.5, integer half-up, min 1 lot (a 1-lot signal is unchanged); UP = x1.5 same rounding; RE-TARGET = target moved to the nearest fresh line ahead minus 2 ticks (0.5 pt, floor 0.25 pt), signal entered at market (control rtc = same market entry, original target).
* No-man's land (NTE-1): loc = (E - low)/(high - low); mid third = 1/3 <= loc <= 2/3; ranges: PDR = prior-day bar high/low (the 1d bar closed before the signal), ON = overnight range 18:00 ET to min(now, 09:30) (undefined 09:30-10:00), SESS = high/low of the current ET session block so far (defined from 15 min in); a range is used only if its width > 8 pts. All three are 1-minute-bar computable in NT8 (high/low of bars); the 8 lines are already in D7.

Which of these need the 1-s tape: none. The lines need the existing POI engines; the counts and distances are arithmetic on the 8 line values.

## 6. Follow-up on D7 v1.3 (lead order 02:00Z): placebos, scaled cut-off sweep, profile streams in the count, per-scope, vol tercile, re-target delay

### 6a. v1.3 placebos for sA40>=1 skip (rank = share of draws with a maxDD cut >= the real cut; B same-volume stratified, C shuffled-day, A random rows)

| window | real cut v1.3 | B rank (n) | C rank (n) | A rank (n) | B median draw cut |
|---|---|---|---|---|---|
| L6M | +32% | 0.10 (40) | 0.30 (40) | 0.10 (40) | -5% |
| HOLD | +15% | 0.15 (40) | 0.30 (40) | 0.17 (40) | -9% |
| MID | -19% | 0.60 (40) | 0.72 (40) | 0.72 (40) | -4% |
| PRE | -21% | 0.88 (40) | 0.65 (40) | 0.65 (40) | +10% |
| X' | -3% | 0.85 (40) | 0.82 (40) | 0.90 (40) | +33% |
| F9 | +32% | 0.07 (40) | 0.30 (40) | 0.05 (40) | -9% |

### 6b. Price-scaled cut-off sweep on v1.3 (x multiplied by 0.5 .. 2; 1.0 = the cell as defined): maxDD cut L6M / HOLD / MID / PRE / X' / F9, mean d $k/wk F9 (MDE)

| cell | factor | cuts L6M / HOLD / MID / PRE / X' / F9 | mean d F9 (MDE) | flagged % |
|---|---|---|---|---|
| sA40>=1 skip | x0.5 | -29% / -29% / -7% / -14% / -19% / -29% | -1.2 (+10.6) | |
| sA40>=1 skip | x0.75 | -25% / -25% / +18% / +26% / +14% / -25% | -3.4 (+8.6) | |
| sA40>=1 skip | x1.0 | +32% / +15% / -19% / -21% / -3% / +32% | +1.5 (+9.9) | |
| sA40>=1 skip | x1.25 | -4% / -4% / -20% / -14% / -15% / -4% | -0.1 (+10.5) | |
| sA40>=1 skip | x1.5 | -31% / -31% / -38% / +3% / -30% / -31% | -2.4 (+14.5) | |
| sA40>=1 skip | x2 | -8% / -8% / -128% / +12% / +8% / -8% | -4.2 (+17.6) | |
| sA40>=1 half | x0.5 | +10% / +10% / +12% / -56% / +32% / +10% | +1.3 (+7.2) | |
| sA40>=1 half | x0.75 | +14% / +14% / +39% / -35% / +8% / +14% | +1.0 (+6.9) | |
| sA40>=1 half | x1.0 | +25% / +25% / +39% / -29% / +21% / +25% | -1.9 (+9.5) | |
| sA40>=1 half | x1.25 | +31% / +31% / +32% / -19% / +18% / +31% | -2.2 (+9.7) | |
| sA40>=1 half | x1.5 | +31% / +31% / +33% / -2% / +15% / +31% | -2.9 (+9.2) | |
| sA40>=1 half | x2 | +34% / +34% / +40% / -42% / +36% / +34% | -3.3 (+10.1) | |
| sA40>=2 half | x0.5 | +8% / +8% / -0% / -2% / +12% / +8% | +0.9 (+7.7) | |
| sA40>=2 half | x0.75 | +20% / +20% / -2% / -12% / +9% / +20% | +1.1 (+8.0) | |
| sA40>=2 half | x1.0 | +26% / +26% / -0% / -11% / +5% / +26% | +1.2 (+8.5) | |
| sA40>=2 half | x1.25 | +25% / +25% / -1% / -49% / +7% / +25% | +0.5 (+7.8) | |
| sA40>=2 half | x1.5 | +27% / +27% / -7% / -77% / +13% / +27% | +1.5 (+8.2) | |
| sA40>=2 half | x2 | +23% / +23% / -2% / -34% / -9% / +23% | +1.2 (+7.4) | |
| sA60>=1 half | x0.5 | +14% / +14% / +39% / -35% / +8% / +14% | +1.0 (+6.9) | |
| sA60>=1 half | x0.75 | +27% / +27% / +39% / -37% / +15% / +27% | -2.0 (+9.6) | |
| sA60>=1 half | x1.0 | +31% / +31% / +33% / -2% / +15% / +31% | -2.9 (+9.2) | |
| sA60>=1 half | x1.25 | +34% / +32% / +40% / -31% / +38% / +34% | -3.2 (+9.9) | |
| sA60>=1 half | x1.5 | +36% / +35% / +46% / -35% / +35% / +36% | -5.1 (+10.9) | |
| sA60>=1 half | x2 | +28% / +28% / -15% / -65% / +35% / +28% | -7.2 (+13.2) | |

### 6c. Three profile streams (vah sw15, lvn1 sw1h, hvn0 sw1h) added to the 8 lines (11-line count, price-scaled): v1.3

| cell | cuts L3M / L6M / HOLD / MID / PRE / X' / F9 | mean d L6M (MDE) | S/T/N | vs the 8-line analogue (F9 / PRE) |
|---|---|---|---|---|
| qA40>=1 half | +25% / +12% / +12% / +40% / -60% / -4% / +12% | -2.3 (+11.6) | n/n/Y | +25% / -29% |
| qA40>=1 rt | -72% / -36% / -36% / +25% / -43% / +7% / -36% | -10.1 (+12.9) | n/n/n | +12% / -37% |
| qA40>=1 rtc | +47% / +11% / +11% / -1% / +7% / -11% / +11% | +1.0 (+4.5) | n/Y/Y | +18% / +21% |
| qA40>=1 skip | -67% / -17% / -17% / +9% / +24% / -0% / -17% | -4.0 (+12.7) | n/n/n | +32% / -21% |
| qA40>=1 up | -100% / -63% / -63% / -68% / -5% / -14% / -63% | -0.9 (+7.5) | n/n/n | - |
| qA40>=2 half | +16% / +7% / +7% / -6% / -13% / +2% / +7% | +3.6 (+8.9) | n/n/Y | +26% / -11% |
| qA40>=2 rt | +2% / +1% / +1% / +33% / -14% / -14% / +1% | -3.4 (+9.0) | n/n/Y | - |
| qA40>=2 rtc | +6% / +5% / +5% / -0% / +0% / -8% / +5% | +0.4 (+1.6) | n/n/Y | - |
| qA40>=2 skip | -31% / -31% / -31% / +0% / +16% / -20% / -31% | +2.0 (+8.0) | n/n/n | - |
| qA40>=2 up | -14% / -32% / -32% / -69% / +5% / -2% / -32% | -1.4 (+4.5) | n/n/n | - |
| qA60>=1 half | +57% / +31% / +31% / +45% / +8% / +35% / +31% | -3.5 (+12.7) | Y/Y/Y | +31% / -2% |
| qA60>=1 rt | -245% / -140% / -140% / +38% / -31% / -2% / -140% | -15.7 (+14.8) | n/n/n | - |
| qA60>=1 rtc | +47% / +12% / +12% / -26% / +6% / -14% / +12% | +1.3 (+4.7) | n/Y/Y | - |
| qA60>=1 up | -100% / -62% / -62% / -125% / -11% / -5% / -62% | +0.3 (+8.8) | n/n/n | - |
| qA60>=2 half | +1% / +10% / +10% / -24% / -35% / +11% / +10% | +5.0 (+8.3) | n/n/Y | - |
| qA60>=2 rt | -71% / -51% / -51% / +10% / -58% / -10% / -51% | -5.8 (+9.8) | n/n/n | - |
| qA60>=2 rtc | +15% / +4% / +4% / +18% / -10% / -10% / +4% | +1.1 (+2.8) | n/n/Y | - |
| qA60>=2 skip | -63% / -40% / -40% / +19% / -13% / -9% / -40% | +4.3 (+10.6) | n/n/n | - |
| qA60>=2 up | -8% / -40% / -40% / -60% / +9% / -13% / -40% | -2.2 (+5.1) | n/n/n | - |
| qB40>=2 half | +21% / -1% / -1% / -80% / -2% / +37% / -1% | -0.2 (+3.2) | n/n/n | - |
| qB40>=2 skip | -20% / -22% / -22% / -97% / -2% / +20% / -22% | +2.6 (+16.4) | n/n/n | - |
| qB40>=2 up | +46% / -8% / -8% / -17% / -37% / -8% / -8% | +4.6 (+11.4) | n/n/n | - |
| qB60>=2 half | +17% / -6% / -6% / -19% / -21% / +30% / -6% | +0.5 (+12.8) | n/n/n | - |
| qB60>=2 skip | -40% / -42% / -42% / -116% / -31% / +36% / -42% | -2.4 (+18.2) | n/n/n | - |
| qB60>=2 up | -36% / -18% / -18% / -1% / -21% / -6% / -18% | +6.8 (+16.3) | n/n/n | - |
| qT40>=3 half | +8% / +2% / +2% / -17% / +3% / +31% / +2% | +0.2 (+4.5) | n/Y/Y | - |
| qT40>=3 skip | -45% / -67% / -67% / -20% / -7% / +21% / -67% | +0.9 (+16.9) | n/n/n | - |
| qT40>=3 up | -2% / -34% / -34% / -1% / -14% / -40% / -34% | -0.5 (+5.5) | n/n/n | - |
| qT60>=3 half | -7% / -19% / -19% / -18% / -22% / -1% / -19% | +2.5 (+11.9) | n/n/n | - |
| qT60>=3 up | -44% / -44% / -44% / -60% / +0% / -7% / -44% | -1.0 (+6.2) | n/n/n | - |

### 6d. Per-scope reruns on v1.3 (rule applied ONLY to the book / session; cut on the TOTAL composite maxDD, F9 and L6M)

| cell | scope | cut L6M | cut F9 | cut PRE | cut X' | mean d F9 (MDE) |
|---|---|---|---|---|---|---|
| sA40>=1 skip | book=KB | -22% | -22% | -11% | -1% | +1.6 (+9.7) |
| sA40>=1 skip | book=PE | +22% | +22% | +45% | +5% | -0.1 (+7.9) |
| sA40>=1 skip | book=SM | -7% | -7% | -5% | -32% | +2.7 (+7.0) |
| sA40>=1 skip | book=HM | +13% | +13% | -13% | +2% | +1.3 (+6.5) |
| sA40>=1 skip | book=MV | +13% | +13% | +2% | -3% | +3.3 (+7.0) |
| sA40>=1 skip | book=PB | -1% | -1% | -13% | +1% | -0.5 (+1.4) |
| sA40>=1 skip | sess=asia | +12% | +12% | +52% | +44% | +0.1 (+12.4) |
| sA40>=1 skip | sess=london | +21% | +21% | -29% | -26% | +4.2 (+7.9) |
| sA40>=1 skip | sess=pre | +0% | +0% | +0% | +0% | +0.0 (+0.0) |
| sA40>=1 skip | sess=nyam | +8% | +8% | -35% | -18% | -0.2 (+1.2) |
| sA40>=1 skip | sess=nypm | +17% | +17% | +0% | -1% | +1.5 (+3.3) |
| sA40>=1 half | book=KB | -18% | -18% | -69% | +29% | -2.7 (+7.2) |
| sA40>=1 half | book=PE | +21% | +21% | -21% | -8% | +1.8 (+8.1) |
| sA40>=1 half | book=SM | +19% | +19% | -5% | -24% | +3.3 (+7.1) |
| sA40>=1 half | book=HM | +2% | +2% | -9% | +9% | -1.2 (+4.1) |
| sA40>=1 half | book=MV | +10% | +10% | +0% | +1% | +2.4 (+7.1) |
| sA40>=1 half | book=PB | +1% | +1% | -1% | +2% | -0.0 (+0.9) |
| sA40>=1 half | sess=asia | +11% | +11% | +13% | +35% | -3.0 (+8.2) |
| sA40>=1 half | sess=london | +20% | +20% | -17% | -16% | +3.1 (+7.0) |
| sA40>=1 half | sess=pre | +0% | +0% | +0% | +0% | +0.0 (+0.0) |
| sA40>=1 half | sess=nyam | +2% | +2% | -31% | -5% | -0.1 (+0.9) |
| sA40>=1 half | sess=nypm | +1% | +1% | -0% | -0% | +0.1 (+0.1) |

### 6e. Re-target decision delay (sA40>=1 rt on v1.3; delay = entry at the signal second +1 / +3 at that second's close, same stop and target LEVELS; rows whose target is already passed keep the base treatment); rtc = control with the original target

| action | delay | cuts L6M / F9 / PRE / X' | mean d F9 (MDE) |
|---|---|---|---|
| rt | 0 s | +12% / +12% / -37% / +4% | -2.4 (+11.1) |
| rt | 1 s | +18% / +18% / -40% / +2% | -0.1 (+12.1) |
| rt | 3 s | +18% / +18% / -24% / +10% | +0.0 (+11.9) |
| rtc | 0 s | +18% / +18% / +21% / -10% | +2.0 (+3.8) |
| rtc | 1 s | +17% / +17% / -30% / -11% | +0.4 (+6.4) |
| rtc | 3 s | +19% / +19% / -6% / -11% | +0.2 (+6.4) |

### 6g. v1.3 (assumed base) placebo ranks for the cells with L6M cut >= 20% on v1.3 (share of draws with cut >= real; n draws per kind in brackets; resolution 1/n)

| cell | real cut L6M / F9 / PRE | B rank L6M (n) | C rank L6M (n) | A rank L6M (n) | B rank PRE | label |
|---|---|---|---|---|---|---|
| sA40>=1 skip | +32% / +32% / -21% | 0.10 (40) | 0.30 (40) | 0.10 (40) | 0.88 (40) | LEAD-unconfirmed (C/A rank > 0.10) |
| rho60>=2 skip | +53% / +53% / +22% | n/a | n/a | n/a | n/a | UNTESTED (n<5) |
| sA60>=1 half | +31% / +31% / -2% | n/a | n/a | n/a | n/a | UNTESTED (n<5) |
| nA60>=1 skip | +31% / +31% / +7% | n/a | n/a | n/a | n/a | UNTESTED (n<5) |
| openA40 half | +30% / +30% / +35% | n/a | n/a | n/a | n/a | UNTESTED (n<5) |
| open20 half | +37% / +37% / +22% | 0.40 (5) | 0.40 (5) | 0.20 (5) | 0.20 (5) | (volume effect) |
| open60 half | +30% / +30% / +29% | n/a | 0.00 (5) | n/a | n/a | UNTESTED (n<5) |
| sA40>=2 half | +26% / +26% / -11% | n/a | n/a | n/a | n/a | UNTESTED (n<5) |
| sopen40 half | +25% / +25% / +32% | n/a | n/a | n/a | n/a | UNTESTED (n<5) |
| nA60>=2 half | +26% / +26% / -55% | n/a | n/a | n/a | n/a | UNTESTED (n<5) |
| sA40>=1 half | +25% / +25% / -29% | n/a | n/a | n/a | n/a | UNTESTED (n<5) |
| nA60>=1 half | +25% / +25% / -23% | n/a | n/a | n/a | n/a | UNTESTED (n<5) |
| rho60>=2 half | +21% / +21% / +15% | n/a | n/a | n/a | n/a | UNTESTED (n<5) |

### 6h. Z3 maxDD NOISE BAND (DS3_ZONES_3_NOISE.md, interim, assumed base): a cut counts only if it exceeds the band in L6M AND in PRE or X' (same sign). Band row chosen by the cell's flagged share of rows (<1%: flip 0.5, 1-1.5%: flip 1, 1.5-3.5%: flip 2, else flip 5; lenient for big masks)

| cell (v1.3 assumed) | flag % | band row | L6M cut / band | PRE cut / band | X' cut / band | passes the rule |
|---|---|---|---|---|---|---|
| nA40>=1 skip | 25.0 | flip 5 | -16% / 31% | -31% / 53% | +5% / 31% | NOISE |
| nA40>=1 half | 25.0 | flip 5 | +14% / 31% | -34% / 53% | +20% / 31% | NOISE |
| nB40>=1 skip | 21.0 | flip 5 | -9% / 31% | +46% / 53% | +60% / 31% | NOISE |
| nB40>=1 half | 21.0 | flip 5 | +9% / 31% | +6% / 53% | +41% / 31% | NOISE |
| nB40>=2 skip | 10.4 | flip 5 | -1% / 31% | +4% / 53% | +33% / 31% | NOISE |
| nB40>=2 half | 10.4 | flip 5 | +3% / 31% | -3% / 53% | +41% / 31% | NOISE |
| nB40>=3 skip | 5.5 | flip 5 | -9% / 31% | +3% / 53% | +33% / 31% | NOISE |
| nB40>=3 half | 5.5 | flip 5 | -5% / 31% | +6% / 53% | +37% / 31% | NOISE |
| nT40>=2 half | 20.1 | flip 5 | +8% / 31% | -5% / 53% | +37% / 31% | NOISE |
| nT40>=4 half | 4.8 | flip 5 | -2% / 31% | -7% / 53% | +35% / 31% | NOISE |
| nA60>=1 skip | 32.5 | flip 5 | +31% / 31% | +7% / 53% | -27% / 31% | NOISE |
| nA60>=1 half | 32.5 | flip 5 | +25% / 31% | -23% / 53% | +17% / 31% | NOISE |
| nA60>=2 half | 13.6 | flip 5 | +26% / 31% | -55% / 53% | -7% / 31% | NOISE |
| nT60>=3 skip | 22.0 | flip 5 | -51% / 31% | -29% / 53% | +41% / 31% | NOISE |
| nTany40>=2 half | 46.7 | flip 5 | +2% / 31% | +13% / 53% | +32% / 31% | NOISE |
| open20 half | 81.4 | flip 5 | +37% / 31% | +22% / 53% | +11% / 31% | NOISE |
| open60 half | 46.7 | flip 5 | +30% / 31% | +29% / 53% | +5% / 31% | NOISE |
| openA40 half | 75.0 | flip 5 | +30% / 31% | +35% / 53% | +60% / 31% | NOISE |
| rho40>=2 skip | 18.2 | flip 5 | +16% / 31% | -15% / 53% | -3% / 31% | NOISE |
| rho40<=0.5 skip | 15.1 | flip 5 | -8% / 31% | +46% / 53% | +63% / 31% | NOISE |
| rho60>=2 skip | 19.6 | flip 5 | +53% / 31% | +22% / 53% | -17% / 31% | NOISE |
| rho60>=2 half | 19.6 | flip 5 | +21% / 31% | +15% / 53% | +6% / 31% | NOISE |
| rho60<=0.5 half | 24.5 | flip 5 | -6% / 31% | -13% / 53% | +18% / 31% | NOISE |
| mid_PDR half | 22.0 | flip 5 | +11% / 31% | +16% / 53% | +27% / 31% | NOISE |
| mid_any3 half | 40.6 | flip 5 | -15% / 31% | +38% / 53% | +31% / 31% | NOISE |
| mid_PDR&open40 up | 10.3 | flip 5 | +8% / 31% | -61% / 53% | -8% / 31% | NOISE |
| mid_ON&nT40<=1 up | 10.1 | flip 5 | -10% / 31% | -68% / 53% | +4% / 31% | NOISE |
| sA40>=1 skip | 28.0 | flip 5 | +32% / 31% | -21% / 53% | -3% / 31% | NOISE |
| sA40>=1 half | 28.0 | flip 5 | +25% / 31% | -29% / 53% | +21% / 31% | NOISE |
| sA40>=1 rt | 28.0 | flip 5 | +12% / 31% | -37% / 53% | +4% / 31% | NOISE |
| sA40>=2 half | 10.5 | flip 5 | +26% / 31% | -11% / 53% | +5% / 31% | NOISE |
| sB40>=3 half | 7.5 | flip 5 | -3% / 31% | -14% / 53% | +25% / 31% | NOISE |
| sA60>=1 half | 35.9 | flip 5 | +31% / 31% | -2% / 53% | +15% / 31% | NOISE |
| sopen40 half | 55.2 | flip 5 | +25% / 31% | +32% / 53% | +4% / 31% | NOISE |

Passing the band: 0 of 34 finalists (necessary, not sufficient).

### 6f. Vol-tercile cuts (finalists, v1.2 and v1.3)

Vol tercile = tercile of the day's signal-price range / mean price over all 935 label days; cut = maxDD cut of the day-cumulative P&L of the days in the tercile over ALL windows (mean delta $k/day in brackets). Day-cumulative, not weekly.

| cell              | v1.2 low-vol   | v1.2 mid    | v1.2 high   | v1.3 low-vol   | v1.3 mid     | v1.3 high    |
|:------------------|:---------------|:------------|:------------|:---------------|:-------------|:-------------|
| nA40>=1 skip      | -17% (-0.7)    | +32% (-0.4) | -7% (+0.3)  | -26% (-0.6)    | +30% (-0.1)  | -43% (+0.8)  |
| nA40>=1 half      | +8% (+0.1)     | +21% (-0.6) | +3% (-1.8)  | +4% (+0.1)     | +14% (-0.2)  | -20% (-0.6)  |
| nB40>=1 skip      | +7% (+0.1)     | +44% (-0.7) | -2% (-0.5)  | -4% (-0.2)     | +49% (-0.7)  | -19% (+0.5)  |
| nB40>=1 half      | +31% (+0.7)    | +17% (-0.6) | -2% (-1.0)  | +17% (+0.3)    | +26% (-0.4)  | -15% (-0.8)  |
| nB40>=2 skip      | +20% (+0.5)    | +18% (+0.1) | -1% (+0.6)  | +9% (+0.1)     | +32% (-0.1)  | -4% (+0.9)   |
| nB40>=2 half      | +26% (+0.7)    | +4% (+0.1)  | +0% (-0.1)  | +9% (+0.2)     | +23% (+0.2)  | -1% (-0.5)   |
| nB40>=3 skip      | +18% (+0.5)    | +13% (+0.0) | -8% (+0.1)  | +8% (+0.3)     | +28% (+0.0)  | -9% (+0.4)   |
| nB40>=3 half      | +18% (+0.5)    | +3% (+0.1)  | +0% (+0.0)  | +7% (+0.2)     | +22% (+0.2)  | +1% (-0.4)   |
| nT40>=2 half      | +23% (+0.5)    | +29% (-0.4) | -2% (-0.8)  | +17% (+0.1)    | +23% (+0.0)  | -21% (-0.4)  |
| nT40>=4 half      | +10% (+0.3)    | -1% (-0.1)  | +0% (-0.1)  | +5% (+0.2)     | +7% (-0.1)   | +0% (+0.0)   |
| nA60>=1 skip      | -13% (-0.6)    | +16% (-0.8) | -17% (+0.0) | -36% (-0.8)    | +28% (-0.2)  | -30% (+0.8)  |
| nA60>=1 half      | +19% (+0.4)    | +9% (-1.3)  | +11% (-1.6) | +11% (+0.3)    | +22% (-0.6)  | -9% (-0.9)   |
| nA60>=2 half      | +15% (+0.3)    | +10% (-0.6) | +19% (-0.7) | +10% (+0.3)    | -3% (-0.3)   | -17% (-0.5)  |
| nT60>=3 skip      | -7% (-0.2)     | +29% (-0.9) | -16% (-0.1) | -12% (-0.2)    | -5% (-0.7)   | -38% (+0.9)  |
| nTany40>=2 half   | +31% (+0.6)    | +21% (-0.8) | +5% (-1.1)  | +27% (+0.4)    | +9% (-0.0)   | -10% (-0.4)  |
| open20 half       | +42% (+0.9)    | +40% (-0.9) | +42% (-3.6) | +35% (+0.7)    | +46% (-0.4)  | +41% (-2.5)  |
| open60 half       | +25% (+0.3)    | +17% (-0.5) | +36% (-2.5) | +10% (+0.1)    | +37% (-0.2)  | +18% (-1.4)  |
| openA40 half      | +39% (+0.7)    | +33% (-0.8) | +33% (-3.4) | +40% (+0.7)    | +36% (-0.6)  | +26% (-1.8)  |
| rho40>=2 skip     | -13% (-0.5)    | +20% (-0.3) | -0% (-0.1)  | -23% (-0.4)    | +21% (+0.3)  | -25% (+0.3)  |
| rho40<=0.5 skip   | +13% (+0.2)    | +42% (-0.2) | -4% (-0.4)  | -6% (-0.2)     | +45% (-0.4)  | -10% (+0.7)  |
| rho60>=2 skip     | -7% (-0.3)     | +33% (-0.1) | +2% (+0.0)  | -35% (-0.6)    | +49% (+0.2)  | -23% (+0.8)  |
| rho60>=2 half     | +17% (+0.5)    | +15% (-0.5) | +22% (-0.5) | -5% (+0.1)     | +38% (-0.2)  | -5% (-0.4)   |
| rho60<=0.5 half   | +38% (+0.9)    | +14% (-0.6) | +21% (-1.2) | +23% (+0.5)    | +12% (-0.2)  | -11% (-0.2)  |
| mid_PDR half      | +16% (+0.3)    | +4% (-0.4)  | +24% (-0.8) | +2% (+0.3)     | +27% (+0.3)  | +9% (-0.3)   |
| mid_any3 half     | +19% (+0.4)    | +14% (-0.5) | +15% (-0.5) | -0% (+0.2)     | +30% (-0.0)  | +26% (-0.1)  |
| mid_PDR&open40 up | -7% (-0.1)     | -7% (-0.2)  | +10% (-0.1) | -8% (-0.3)     | -22% (-0.3)  | -21% (-0.5)  |
| mid_ON&nT40<=1 up | +1% (-0.1)     | +5% (+0.2)  | -6% (-0.3)  | -1% (+0.1)     | -2% (+0.0)   | -2% (-0.3)   |
| sA40>=1 skip      | -16% (-0.7)    | +19% (-0.5) | -21% (+0.1) | -40% (-0.8)    | +27% (-0.2)  | -44% (+0.9)  |
| sA40>=1 half      | +14% (+0.3)    | +20% (-0.9) | +5% (-1.9)  | +3% (+0.1)     | +16% (-0.5)  | -17% (-0.7)  |
| sA40>=1 rt        | +19% (+0.4)    | -17% (-0.6) | -10% (-1.2) | +nan% (+nan)   | +nan% (+nan) | +nan% (+nan) |
| sA40>=2 half      | -1% (-0.1)     | +18% (-0.5) | +13% (-0.3) | +5% (+0.1)     | +1% (-0.3)   | -7% (-0.1)   |
| sB40>=3 half      | +20% (+0.5)    | +5% (+0.2)  | -13% (-0.1) | +4% (-0.0)     | +27% (+0.3)  | -10% (-0.4)  |
| sA60>=1 half      | +24% (+0.6)    | +6% (-1.5)  | +15% (-1.7) | +13% (+0.4)    | +13% (-0.7)  | +13% (-0.7)  |
| sopen40 half      | +38% (+0.7)    | +16% (-0.5) | +33% (-2.7) | +33% (+0.6)    | +35% (-0.1)  | +46% (-1.5)  |## 7. HEADLINE BASE: D7 v1.3 EXACT (V13X: exact U7 same-side, exact 5 THP take/tighten lines, exact lots, 12R per-book + give-back, ER running-max)

V13X base: L6M mean 22.4k/wk, maxDD 74k; HOLD mean 19.9k/wk, maxDD 119k; MID mean 5.3k/wk, maxDD 79k; PRE mean 4.0k/wk, maxDD 252k; X' mean -3.9k/wk, maxDD 174k; F9 mean 17.6k/wk, maxDD 79k. Base maxDD-carrying week (L6M / F9 / PRE / X'): 202634 / 202613 / 202508 / 202349.

### 7a. All 34 finalists on V13X (screen; placebo status in 7c)

| cell (V13X) | flag % | maxDD cut L3M / L6M / HOLD / MID / PRE / X' / F9 | mean d $k/wk L6M (MDE) / PRE (MDE) | S/T/N | TOL-B / nc | ONE-WEEK L6M/F9 | week carrying (L6M) | band (flip row) L6M / PRE / X' | band rule |
|---|---|---|---|---|---|---|---|---|---|
| nA40>=1 skip | 25 | -2% / -48% / +8% / +59% / -2% / +23% / -39% | -5.6 (+8.3) / +1.4 (+6.8) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nA40>=1 half | 25 | -41% / -31% / +19% / +39% / +8% / +31% / -24% | -1.6 (+5.6) / +0.1 (+4.8) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nB40>=1 skip | 21 | -63% / -54% / +5% / +8% / +21% / -2% / -45% | +1.2 (+8.4) / -3.1 (+6.6) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nB40>=1 half | 21 | -65% / -51% / +7% / +21% / +30% / +62% / -42% | -4.4 (+7.7) / -1.0 (+5.3) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nB40>=2 skip | 10 | -17% / -14% / +22% / -18% / +34% / +2% / -18% | +2.6 (+6.2) / +2.5 (+5.9) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nB40>=2 half | 10 | +2% / -15% / +29% / -6% / +28% / +54% / -8% | -2.4 (+7.7) / +1.4 (+5.0) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nB40>=3 skip | 6 | -23% / -13% / -1% / -8% / +25% / -8% / -8% | -0.4 (+1.9) / +1.9 (+5.3) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nB40>=3 half | 6 | -13% / -7% / +3% / +4% / +19% / +41% / -1% | -0.3 (+1.0) / +1.5 (+2.5) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nT40>=2 half | 20 | -55% / -54% / +5% / -8% / +25% / +45% / -45% | -5.1 (+8.5) / -0.3 (+6.2) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nT40>=4 half | 5 | -7% / -3% / +12% / +1% / +10% / +15% / +1% | -0.3 (+0.8) / +0.1 (+4.2) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nA60>=1 skip | 32 | +16% / +34% / +24% / +32% / +37% / -8% / +32% | -3.3 (+11.4) / +2.0 (+8.2) | n/Y/Y | Y / Y | Y/n | 202634 | flip 5: 36/28/29% | NOISE |
| nA60>=1 half | 32 | +25% / +10% / +44% / +45% / +6% / +35% / +15% | -3.3 (+8.9) / -1.1 (+5.1) | Y/Y/Y | Y / Y | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nA60>=2 half | 14 | +20% / +6% / +15% / +8% / -7% / +48% / +8% | +0.0 (+3.0) / -2.4 (+4.6) | n/n/Y | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nT60>=3 skip | 22 | -135% / -109% / -30% / -7% / +19% / -9% / -97% | -0.2 (+15.3) / +0.1 (+7.5) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| nTany40>=2 half | 47 | -87% / -37% / +15% / +39% / +22% / +44% / -29% | -2.7 (+6.5) / -0.0 (+5.8) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| open20 half | 81 | +46% / +28% / +55% / +52% / +37% / +17% / +32% | -10.0 (+14.4) / -4.0 (+7.0) | Y/n/Y | n / n | Y/n | 202634 | flip 5: 36/28/29% | NOISE |
| open60 half | 47 | -7% / +33% / +41% / +10% / +32% / +21% / +10% | -8.0 (+14.9) / -2.7 (+6.7) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| openA40 half | 75 | -15% / -1% / +38% / +58% / +32% / +47% / +5% | -11.3 (+16.0) / -2.7 (+6.6) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| rho40>=2 skip | 18 | +17% / -30% / +20% / +51% / +5% / +43% / -22% | -5.1 (+7.7) / +1.9 (+5.8) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| rho40<=0.5 skip | 15 | -56% / -55% / +0% / -5% / +26% / +20% / -46% | +0.6 (+7.2) / -1.2 (+5.9) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| rho60>=2 skip | 20 | +41% / +26% / +44% / +47% / +27% / +7% / +30% | +1.8 (+10.8) / +2.6 (+5.7) | Y/Y/Y | Y / Y | Y/n | 202634 | flip 5: 36/28/29% | NOISE |
| rho60>=2 half | 20 | +30% / +19% / +48% / +37% / +23% / +20% / +24% | +0.4 (+4.8) / -0.0 (+4.3) | Y/Y/Y | Y / Y | Y/n | 202634 | flip 5: 36/28/29% | NOISE |
| rho60<=0.5 half | 24 | -13% / -41% / +13% / +8% / +15% / +25% / -32% | -3.0 (+3.1) / +0.7 (+6.3) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| mid_PDR half | 22 | -8% / -29% / +20% / +6% / +35% / +42% / -22% | -5.4 (+7.8) / +2.9 (+6.1) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| mid_any3 half | 41 | -66% / -52% / +6% / +5% / +43% / +32% / -43% | -8.5 (+10.6) / +2.7 (+6.4) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| mid_PDR&open40 up | 10 | +19% / +15% / +8% / +29% / +1% / -38% / +20% | +3.9 (+5.6) / -1.5 (+5.0) | n/n/Y | n / n | Y/n | 202634 | flip 5: 36/28/29% | NOISE |
| mid_ON&nT40<=1 up | 10 | -3% / -25% / +6% / +3% / -36% / -22% / -17% | -0.1 (+3.6) / -1.5 (+2.6) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| sA40>=1 skip | 28 | +22% / +37% / +25% / +32% / +5% / +19% / +32% | -2.9 (+11.8) / +1.2 (+7.9) | Y/Y/Y | Y / Y | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| sA40>=1 half | 28 | +25% / +14% / +47% / +54% / +3% / +31% / +19% | -3.0 (+9.0) / -0.4 (+4.9) | Y/Y/Y | Y / Y | Y/n | 202634 | flip 5: 36/28/29% | NOISE |
| sA40>=1 rt | 28 | +4% / -8% / +24% / +34% / -15% / -29% / -2% | -6.4 (+12.2) / -0.6 (+7.2) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| sA40>=2 half | 11 | +18% / +6% / +21% / +17% / +1% / +46% / +11% | +0.1 (+3.0) / -1.7 (+4.8) | Y/Y/Y | Y / Y | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| sB40>=3 half | 7 | -11% / -9% / +4% / -2% / +23% / +37% / -2% | +0.2 (+2.0) / +2.0 (+2.8) | n/n/n | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |
| sA60>=1 half | 36 | +38% / +27% / +51% / +45% / +3% / +33% / +31% | -1.6 (+6.3) / -0.3 (+4.9) | Y/Y/Y | Y / Y | Y/n | 202634 | flip 5: 36/28/29% | NOISE |
| sopen40 half | 55 | +3% / +48% / +62% / +44% / -16% / +14% / +44% | -7.3 (+15.6) / -3.4 (+6.6) | n/n/Y | n / n | n/n | 202634 | flip 5: 36/28/29% | NOISE |

Band rule (Z3 V13X band, lock 12R, DS3_ZONES_3_NOISE.md; the earlier assumed-base band is superseded): 0 of 34 pass; TOLERANT 8, STRICT 8.

### 7b. Scaled cut-off sweep on V13X (sA40>=1 skip)

| factor | cuts L6M / HOLD / MID / PRE / X' / F9 | mean d F9 (MDE) |
|---|---|---|
| x0.5 | -56% / +3% / +23% / +11% / +25% / -47% | -3.9 (+7.3) |
| x0.75 | -31% / +19% / +56% / +12% / +30% / -23% | -4.0 (+8.9) |
| x1.0 | +37% / +25% / +32% / +5% / +19% / +32% | -0.2 (+10.5) |
| x1.25 | -12% / +15% / +31% / +23% / +4% / -6% | -2.1 (+11.9) |
| x1.5 | -22% / +15% / +11% / +37% / +3% / -15% | -2.7 (+14.3) |
| x2 | -12% / -5% / -60% / +10% / +18% / -60% | -6.4 (+18.6) |

### 7c. V13X placebo ranks (share of draws with cut >= real; n draws), L6M and PRE

| cell | real L6M / PRE | B L6M (n) | C L6M | A L6M | B PRE | C PRE | A PRE | label |
|---|---|---|---|---|---|---|---|---|
| nA60>=1 half | +10% / +6% | 0.20 (100) | 0.33 | 0.26 | 0.51 | 0.62 | 0.57 | (volume effect) |
| nA60>=1 skip | +34% / +37% | 0.05 (100) | 0.10 | 0.07 | 0.29 | 0.19 | 0.31 | placebos beaten |
| open20 half | +28% / +37% | 0.22 (100) | 0.21 | 0.27 | 0.32 | 0.33 | 0.43 | (volume effect) |
| rho60>=2 half | +19% / +23% | 0.20 (100) | 0.18 | 0.12 | 0.17 | 0.23 | 0.27 | (volume effect) |
| rho60>=2 skip | +26% / +27% | 0.17 (100) | 0.13 | 0.08 | 0.33 | 0.30 | 0.34 | (volume effect) |
| sA40>=1 half | +14% / +3% | 0.22 (100) | 0.23 | 0.27 | 0.62 | 0.62 | 0.51 | (volume effect) |
| sA40>=1 skip | +37% / +5% | 0.03 (100) | 0.07 | 0.05 | 0.78 | 0.70 | 0.72 | placebos beaten |
| sA40>=2 half | +6% / +1% | 0.24 (100) | 0.44 | 0.38 | 0.63 | 0.61 | 0.67 | (volume effect) |
| sA60>=1 half | +27% / +3% | 0.15 (100) | 0.16 | 0.11 | 0.60 | 0.71 | 0.61 | (volume effect) |

### 7d. Per-scope reruns on V13X (rule applied only to the book / session; cut on the TOTAL composite)

| cell | scope | cut L6M | cut F9 | cut PRE | cut X' | mean d F9 (MDE) |
|---|---|---|---|---|---|---|
| sA40>=1 skip | book=KB | +5% | +11% | +22% | +41% | -1.8 (+4.7) |
| sA40>=1 skip | book=PE | -20% | -13% | -19% | +3% | -2.4 (+6.8) |
| sA40>=1 skip | book=SM | +2% | +8% | +19% | -13% | +0.7 (+2.0) |
| sA40>=1 skip | book=HM | +2% | -4% | +15% | +9% | +0.3 (+2.5) |
| sA40>=1 skip | book=MV | -3% | +4% | +8% | -1% | +1.0 (+2.2) |
| sA40>=1 skip | book=PB | -11% | -4% | -3% | +3% | -0.3 (+1.5) |
| sA40>=1 skip | sess=asia | -15% | -8% | +27% | +55% | -0.9 (+9.8) |
| sA40>=1 skip | sess=london | -31% | -23% | -18% | -13% | +2.1 (+5.6) |
| sA40>=1 skip | sess=nyam | +16% | +4% | +8% | +15% | +0.5 (+2.2) |
| sA40>=1 skip | sess=nypm | +6% | +5% | +8% | +2% | +0.3 (+0.4) |
| sA40>=1 half | book=KB | -28% | -20% | -3% | +24% | +0.8 (+4.6) |
| sA40>=1 half | book=PE | -2% | +4% | -5% | +5% | -2.6 (+7.5) |
| sA40>=1 half | book=SM | +6% | +6% | +18% | -8% | +0.5 (+1.1) |
| sA40>=1 half | book=HM | -1% | +4% | +15% | +10% | -1.1 (+4.3) |
| sA40>=1 half | book=MV | +2% | +6% | -1% | -3% | +0.2 (+0.5) |
| sA40>=1 half | book=PB | -8% | -2% | +3% | +2% | -0.3 (+1.0) |
| sA40>=1 half | sess=asia | -2% | +4% | +13% | +3% | -0.7 (+8.1) |
| sA40>=1 half | sess=london | +3% | +8% | +14% | -14% | +0.4 (+2.2) |
| sA40>=1 half | sess=nyam | +7% | +1% | +1% | -7% | -1.3 (+4.0) |
| sA40>=1 half | sess=nypm | +2% | +1% | +0% | +0% | +0.1 (+0.1) |
| rho60>=2 skip | book=KB | +6% | +11% | +21% | +2% | -1.0 (+4.4) |
| rho60>=2 skip | book=PE | -0% | +6% | +6% | -10% | -1.6 (+6.6) |
| rho60>=2 skip | book=SM | +9% | +11% | +9% | -26% | +0.9 (+1.7) |
| rho60>=2 skip | book=HM | -3% | -2% | +2% | +4% | +0.6 (+2.4) |
| rho60>=2 skip | book=MV | +0% | +6% | +23% | +0% | +1.0 (+2.2) |
| rho60>=2 skip | book=PB | -11% | -4% | +7% | +1% | -0.2 (+1.3) |
| rho60>=2 skip | sess=asia | -7% | -0% | +40% | +18% | -0.7 (+8.0) |
| rho60>=2 skip | sess=london | -27% | -20% | +9% | -8% | +1.7 (+4.9) |
| rho60>=2 skip | sess=nyam | +15% | +4% | +13% | +35% | +0.4 (+2.2) |
| rho60>=2 skip | sess=nypm | +3% | +5% | +10% | +4% | +0.3 (+0.4) |

### 7e. Re-target decision delay on V13X (sA40>=1; rtc = same market entry with the original target)

| action | delay | cuts L6M / F9 / PRE / X' | mean d F9 (MDE) |
|---|---|---|---|
| rt | 0 s | -8% / -2% / -15% / -29% | -3.3 (+11.1) |
| rt | 1 s | -18% / -11% / -23% / -31% | -2.9 (+10.8) |
| rt | 3 s | -19% / -12% / -20% / -20% | -3.1 (+10.8) |
| rtc | 0 s | +25% / +3% / +21% / +5% | +2.9 (+3.4) |
| rtc | 1 s | +27% / +9% / +13% / -11% | +3.5 (+3.5) |
| rtc | 3 s | +23% / +4% / +12% / +4% | +3.3 (+3.7) |

### 7f. Vol-tercile cuts on V13X (day-range tercile over all days; day-cumulative maxDD cut, mean d $k/day)

| cell | low vol | mid | high |
|---|---|---|---|
| sA40>=1 skip | +1% (-0.1) | +10% (-0.1) | -28% (-0.1) |
| sA40>=1 half | +28% (+0.6) | +34% (-0.2) | +8% (-0.9) |
| sA60>=1 half | +38% (+0.8) | +32% (-0.0) | -2% (-1.0) |
| rho60>=2 skip | -2% (+0.0) | +49% (+0.3) | +3% (-0.0) |
| rho60>=2 half | +17% (+0.4) | +37% (-0.0) | +4% (-0.6) |
| nA60>=1 half | +34% (+0.8) | +25% (-0.4) | +10% (-1.0) |
| open20 half | +38% (+0.8) | +28% (-0.4) | +60% (-3.1) |

### 7g. MASTER TABLE finalist x frame: V13X lock=12 (shipped combined lock) vs lock=None (engine per-book locks only); HEADLINE frame = lock=None until the user confirms; LOCK-ONLY = lock=12 L6M cut >= 10% but lock=None L6M cut < 5%

lock=None base: L6M mean 26.9k, maxDD 133k; F9 mean 22.5k, maxDD 133k; PRE mean 10.0k, maxDD 178k; X' mean -1.2k, maxDD 135k

| cell | lock=12 cuts L6M / F9 / PRE / X' | lock=None cuts L6M / F9 / PRE / X' | mean d F9 lock=None (MDE) | ONE-WEEK (lock=None L6M/F9) | V13X band pass lock=12 / lock=None | label |
|---|---|---|---|---|---|---|
| nA40>=1 skip | -48% / -39% / -2% / +23% | -9% / -9% / +10% / +22% | -3.5 (+9.8) | n/n | noise / noise | - |
| nA40>=1 half | -31% / -24% / +8% / +31% | -4% / -4% / -0% / -34% | -1.9 (+5.9) | n/n | noise / noise | - |
| nB40>=1 skip | -54% / -45% / +21% / -2% | -45% / -45% / +26% / +19% | -4.4 (+7.4) | n/n | noise / noise | - |
| nB40>=1 half | -51% / -42% / +30% / +62% | -19% / -19% / +12% / -4% | -5.0 (+6.6) | n/n | noise / noise | - |
| nB40>=2 skip | -14% / -18% / +34% / +2% | -16% / -16% / +20% / +12% | +0.0 (+4.1) | n/n | noise / noise | - |
| nB40>=2 half | -15% / -8% / +28% / +54% | -12% / -12% / -6% / +11% | -2.7 (+5.9) | n/n | noise / noise | - |
| nB40>=3 skip | -13% / -8% / +25% / -8% | +1% / +1% / +10% / +22% | -0.4 (+2.1) | n/n | noise / noise | both frames + |
| nB40>=3 half | -7% / -1% / +19% / +41% | -0% / -0% / +8% / +4% | -0.9 (+1.6) | n/n | noise / noise | - |
| nT40>=2 half | -54% / -45% / +25% / +45% | -30% / -30% / +14% / -38% | -4.3 (+6.7) | n/n | noise / noise | - |
| nT40>=4 half | -3% / +1% / +10% / +15% | -1% / -1% / +8% / +3% | -0.6 (+0.9) | n/n | noise / noise | - |
| nA60>=1 skip | +34% / +32% / +37% / -8% | +38% / +38% / -6% / +31% | -3.5 (+11.9) | n/n | noise / PASS | - |
| nA60>=1 half | +10% / +15% / +6% / +35% | -6% / -6% / +3% / -16% | -5.2 (+7.9) | n/n | noise / noise | - |
| nA60>=2 half | +6% / +8% / -7% / +48% | -16% / -16% / +4% / -41% | -1.8 (+3.8) | n/n | noise / noise | - |
| nT60>=3 skip | -109% / -97% / +19% / -9% | -33% / -33% / +10% / -50% | -0.1 (+9.4) | n/n | noise / noise | - |
| nTany40>=2 half | -37% / -29% / +22% / +44% | -7% / -7% / -12% / -6% | -3.5 (+8.3) | n/n | noise / noise | - |
| open20 half | +28% / +32% / +37% / +17% | +47% / +47% / +26% / +1% | -9.8 (+12.0) | n/n | noise / PASS | both frames + |
| open60 half | +33% / +10% / +32% / +21% | +48% / +48% / +15% / +21% | -5.4 (+11.0) | n/n | noise / noise | both frames + |
| openA40 half | -1% / +5% / +32% / +47% | +37% / +37% / +36% / +30% | -7.6 (+11.0) | n/n | noise / PASS | both frames + |
| rho40>=2 skip | -30% / -22% / +5% / +43% | +7% / +7% / +17% / +11% | -1.9 (+9.1) | n/n | noise / noise | both frames + |
| rho40<=0.5 skip | -55% / -46% / +26% / +20% | -28% / -28% / +21% / +18% | -2.1 (+6.6) | n/n | noise / noise | - |
| rho60>=2 skip | +26% / +30% / +27% / +7% | +34% / +34% / +9% / +32% | -0.2 (+10.5) | n/n | noise / PASS | both frames + |
| rho60>=2 half | +19% / +24% / +23% / +20% | -2% / -2% / +8% / -12% | -2.7 (+5.7) | n/n | noise / noise | LOCK-ONLY |
| rho60<=0.5 half | -41% / -32% / +15% / +25% | -35% / -35% / -10% / -9% | -2.6 (+5.1) | n/n | noise / noise | - |
| mid_PDR half | -29% / -22% / +35% / +42% | -11% / -11% / -1% / +39% | -4.7 (+7.6) | n/n | noise / noise | - |
| mid_any3 half | -52% / -43% / +43% / +32% | -38% / -38% / +12% / +41% | -7.0 (+9.2) | n/n | noise / noise | - |
| mid_PDR&open40 up | +15% / +20% / +1% / -38% | -11% / -11% / +6% / -13% | +2.8 (+6.1) | n/n | noise / noise | LOCK-ONLY |
| mid_ON&nT40<=1 up | -25% / -17% / -36% / -22% | +2% / +2% / -10% / -5% | +2.0 (+3.4) | n/n | noise / noise | - |
| sA40>=1 skip | +37% / +32% / +5% / +19% | +36% / +36% / +14% / +27% | -2.5 (+12.6) | n/n | noise / noise | both frames + |
| sA40>=1 half | +14% / +19% / +3% / +31% | -5% / -5% / +6% / -29% | -4.2 (+8.4) | n/n | noise / noise | LOCK-ONLY |
| sA40>=1 rt | -8% / -2% / -15% / -29% | -12% / -12% / -6% / -15% | +3.3 (+10.7) | n/n | noise / noise | - |
| sA40>=2 half | +6% / +11% / +1% / +46% | -16% / -16% / +10% / -33% | -1.6 (+3.6) | n/n | noise / noise | - |
| sB40>=3 half | -9% / -2% / +23% / +37% | -6% / -6% / +12% / +13% | -0.2 (+2.6) | n/n | noise / noise | - |
| sA60>=1 half | +27% / +31% / +3% / +33% | -2% / -2% / +2% / -20% | -3.6 (+6.3) | n/n | noise / noise | LOCK-ONLY |
| sopen40 half | +48% / +44% / -16% / +14% | +51% / +51% / +22% / +11% | -5.4 (+10.9) | n/n | noise / PASS | both frames + |


V13X noise-band rule (band row by flagged share; flip 5.0 for masks >= 3.5% of rows): lock=12 passes: none; lock=None passes: ['nA60>=1 skip', 'open20 half', 'openA40 half', 'rho60>=2 skip', 'sopen40 half'] (necessary, not sufficient; the passing cells fail the placebo and carrying-week standards above).

### 7h. lock=None frame for the cells that hold in both frames: cut-off sweep (sA40>=1 skip) and placebo ranks (share of draws with cut >= real; n per kind)

| factor | cuts L6M / HOLD / MID / PRE / X' / F9 (lock=None) |
|---|---|
| x0.5 | -56% / -56% / +7% / +4% / -15% / -56% |
| x0.75 | +7% / +7% / +48% / +6% / +18% / +7% |
| x1.0 | +36% / +30% / +40% / +14% / +27% / +36% |
| x1.25 | +16% / +16% / +36% / +3% / +34% / +16% |
| x1.5 | -3% / -3% / +38% / -6% / +32% / -3% |
| x2 | +24% / +24% / +35% / -8% / +15% / +24% |

| cell | real L6M / PRE / X' | B L6M / PRE / X' (n) | C L6M / PRE / X' | A L6M / PRE / X' | label |
|---|---|---|---|---|---|
| sA40>=1 skip | +36% / +14% / +27% | 0.29 / 0.28 / 0.29 (100) | 0.37 / 0.21 / 0.41 | 0.37 / 0.22 / 0.33 | (volume effect) |
| rho60>=2 skip | +34% / +9% / +32% | 0.23 / 0.27 / 0.15 (100) | 0.35 / 0.21 / 0.21 | 0.23 / 0.26 / 0.19 | (volume effect) |
| nA60>=1 skip | +38% / -6% / +31% | 0.23 / 0.51 / 0.34 (100) | 0.30 / 0.57 / 0.31 | 0.35 / 0.58 / 0.27 | (volume effect) |
| sA40>=1 half | -5% / +6% / -29% | 0.71 / 0.37 / 0.88 (100) | 0.78 / 0.33 / 0.88 | 0.84 / 0.27 / 0.91 | (volume effect) |
| nA60>=1 half | -6% / +3% / -16% | 0.81 / 0.40 / 0.72 (100) | 0.84 / 0.40 / 0.79 | 0.82 / 0.49 / 0.75 | (volume effect) |
| open20 half | +47% / +26% / +1% | 0.29 / 0.46 / 0.91 (100) | 0.23 / 0.49 / 0.95 | 0.23 / 0.46 / 0.88 | (volume effect) |
| openA40 half | +37% / +36% / +30% | 0.52 / 0.14 / 0.41 (100) | 0.41 / 0.20 / 0.45 | 0.39 / 0.20 / 0.40 | (volume effect) |
| sopen40 half | +51% / +22% / +11% | 0.09 / 0.22 / 0.50 (100) | 0.07 / 0.24 / 0.52 | 0.11 / 0.30 / 0.60 | LEAD-unconfirmed (C/A>0.10) |

### 7i. Priority cells in the lock=None frame (headline): episode-proofing, book x session, vol tercile, best-of-N null, causality audit

| cell (lock=None) | window | cut | carrying week | cut w/o it | LOWO range | LOMO range | bootstrap 90% CI / P(cut>0) | ONE-WEEK |
|---|---|---|---|---|---|---|---|---|
| sA40>=1 skip | L6M | +36% | 202630 | +22% | +22% .. +49% | -35% .. +49% | [-103%, +53%] / 0.66 | - |
| sA40>=1 skip | HOLD | +30% | 202630 | +25% | +22% .. +39% | +10% .. +32% | [-19%, +55%] / 0.86 | - |
| sA40>=1 skip | MID | +40% | 202613 | +19% | +19% .. +66% | +19% .. +66% | [-18%, +79%] / 0.81 | ONE-WEEK |
| sA40>=1 skip | PRE | +14% | 202506 | +5% | -7% .. +36% | +5% .. +36% | [-32%, +56%] / 0.83 | ONE-WEEK |
| sA40>=1 skip | X' | +27% | 202314 | +34% | +1% .. +41% | -4% .. +33% | [-53%, +35%] / 0.56 | - |
| sA40>=1 skip | F9 | +36% | 202630 | +22% | +22% .. +49% | -7% .. +49% | [-45%, +59%] / 0.74 | - |
| nA60>=1 skip | L6M | +38% | 202630 | +22% | +22% .. +49% | -35% .. +49% | [-102%, +55%] / 0.72 | - |
| nA60>=1 skip | HOLD | +27% | 202630 | +21% | +21% .. +38% | +15% .. +38% | [-12%, +56%] / 0.89 | - |
| nA60>=1 skip | MID | +40% | 202613 | +19% | +19% .. +59% | +19% .. +59% | [-10%, +74%] / 0.81 | ONE-WEEK |
| nA60>=1 skip | PRE | -6% | 202506 | -18% | -18% .. +25% | -18% .. +34% | [-19%, +65%] / 0.89 | - |
| nA60>=1 skip | X' | +31% | 202314 | +48% | +2% .. +48% | -2% .. +50% | [-50%, +48%] / 0.68 | - |
| nA60>=1 skip | F9 | +38% | 202630 | +22% | +22% .. +49% | -7% .. +49% | [-45%, +58%] / 0.76 | - |
| sA40>=1 half | L6M | -5% | 202630 | -16% | -18% .. +10% | -41% .. -5% | [-115%, -4%] / 0.01 | - |
| sA40>=1 half | HOLD | -5% | 202630 | +19% | -18% .. +20% | -41% .. +20% | [-67%, +52%] / 0.59 | - |
| sA40>=1 half | MID | +28% | 202613 | +3% | +3% .. +51% | +3% .. +51% | [+3%, +69%] / 1.00 | ONE-WEEK |
| sA40>=1 half | PRE | +6% | 202506 | +0% | -3% .. +19% | +0% .. +24% | [-18%, +38%] / 0.85 | - |
| sA40>=1 half | X' | -29% | 202314 | -24% | -50% .. -11% | -53% .. -2% | [-142%, +14%] / 0.14 | - |
| sA40>=1 half | F9 | -5% | 202630 | -16% | -18% .. +10% | -41% .. +5% | [-72%, +31%] / 0.25 | - |
| nA60>=1 half | L6M | -6% | 202630 | -18% | -20% .. +9% | -42% .. -6% | [-113%, -2%] / 0.03 | - |
| nA60>=1 half | HOLD | -6% | 202630 | +18% | -20% .. +19% | -42% .. +22% | [-72%, +51%] / 0.57 | - |
| nA60>=1 half | MID | +19% | 202613 | +3% | +3% .. +35% | +3% .. +19% | [+3%, +60%] / 1.00 | ONE-WEEK |
| nA60>=1 half | PRE | +3% | 202506 | -8% | -8% .. +23% | -8% .. +25% | [-6%, +45%] / 0.92 | - |
| nA60>=1 half | X' | -16% | 202314 | -4% | -45% .. +1% | -49% .. +3% | [-120%, +30%] / 0.29 | - |
| nA60>=1 half | F9 | -6% | 202630 | -18% | -20% .. +9% | -42% .. +5% | [-74%, +21%] / 0.24 | - |
| sopen40 half | L6M | +51% | 202630 | +58% | +40% .. +58% | +39% .. +51% | [+30%, +62%] / 1.00 | - |
| sopen40 half | HOLD | +44% | 202630 | +39% | +30% .. +51% | +39% .. +51% | [+30%, +55%] / 1.00 | - |
| sopen40 half | MID | +36% | 202613 | +15% | +5% .. +50% | +15% .. +36% | [+15%, +36%] / 1.00 | ONE-WEEK |
| sopen40 half | PRE | +22% | 202506 | +26% | +15% .. +39% | +0% .. +26% | [-17%, +28%] / 0.84 | - |
| sopen40 half | X' | +11% | 202314 | +10% | -1% .. +31% | -6% .. +25% | [-10%, +44%] / 0.85 | - |
| sopen40 half | F9 | +51% | 202630 | +54% | +40% .. +54% | +36% .. +51% | [+24%, +51%] / 1.00 | - |
| open20 half | L6M | +47% | 202630 | +49% | +31% .. +55% | +21% .. +66% | [+17%, +73%] / 1.00 | - |
| open20 half | HOLD | +47% | 202630 | +46% | +40% .. +53% | +44% .. +47% | [+27%, +56%] / 1.00 | - |
| open20 half | MID | +32% | 202613 | +37% | +32% .. +46% | +32% .. +37% | [+32%, +40%] / 1.00 | - |
| open20 half | PRE | +26% | 202506 | +26% | +13% .. +35% | +11% .. +36% | [+4%, +40%] / 0.96 | - |
| open20 half | X' | +1% | 202314 | -0% | -16% .. +23% | -2% .. +23% | [+4%, +51%] / 0.98 | - |
| open20 half | F9 | +47% | 202630 | +49% | +31% .. +53% | +32% .. +53% | [+21%, +66%] / 1.00 | - |
| openA40 half | L6M | +37% | 202630 | +34% | +31% .. +42% | +24% .. +50% | [+24%, +57%] / 1.00 | - |
| openA40 half | HOLD | +37% | 202630 | +54% | +36% .. +54% | +37% .. +54% | [+23%, +68%] / 1.00 | - |
| openA40 half | MID | +22% | 202613 | +54% | +12% .. +54% | +22% .. +54% | [+11%, +54%] / 1.00 | - |
| openA40 half | PRE | +36% | 202506 | +29% | +22% .. +46% | +19% .. +36% | [-5%, +39%] / 0.92 | - |
| openA40 half | X' | +30% | 202314 | +29% | +23% .. +45% | +26% .. +45% | [+12%, +61%] / 0.97 | - |
| openA40 half | F9 | +37% | 202630 | +34% | +31% .. +42% | +22% .. +46% | [+19%, +55%] / 1.00 | - |

Per book x session maxDD cut (lock=None, rule applied everywhere; L6M | HOLD | PRE | X'):

| cell | K6 | P6 | U6 | H6 | M6 | A6 | asia | london | nyam | nypm |
|---|---|---|---|---|---|---|---|---|---|---|
| sA40>=1 skip | +63%/+19%/+1%/+56% | +26%/+15%/+9%/+16% | +10%/+10%/+7%/+6% | +60%/-8%/+16%/+16% | -6%/-8%/+27%/-13% | -111%/-95%/+29%/-14% | +45%/+51%/+34%/+17% | -34%/-15%/+7%/+9% | +12%/+16%/-6%/+21% | +58%/+38%/+4%/-14% |
| nA60>=1 skip | +74%/+16%/+18%/+52% | +26%/+17%/-6%/+39% | +10%/+10%/+1%/-33% | +60%/+9%/+30%/-6% | -6%/-10%/+46%/+6% | -111%/-95%/+8%/+22% | +45%/+44%/+3%/+32% | -20%/-10%/+20%/+16% | +11%/+12%/-5%/+38% | +61%/+43%/+4%/+3% |
| sA40>=1 half | +8%/+30%/-16%/-22% | -17%/+7%/+12%/-32% | +15%/+15%/+2%/+9% | +25%/+8%/+10%/+18% | -3%/+16%/+19%/-29% | -13%/-5%/+14%/+25% | +2%/+13%/+23%/+13% | -42%/-6%/+9%/-17% | +1%/+25%/-17%/-4% | +10%/+10%/-17%/+10% |
| nA60>=1 half | +8%/+25%/+1%/+4% | -18%/+7%/+5%/-7% | +15%/+15%/-0%/-16% | +25%/+8%/+17%/+15% | -3%/+16%/+19%/-30% | -13%/-5%/-4%/+29% | -2%/+10%/+21%/+20% | -41%/-5%/+16%/-7% | +1%/+22%/-19%/+11% | +10%/+10%/-2%/+17% |
| sopen40 half | -8%/+22%/+25%/+19% | +59%/+45%/+18%/+26% | +22%/+22%/+39%/-13% | +22%/+22%/+33%/+25% | +32%/+40%/+24%/+33% | +55%/-12%/+30%/+35% | +48%/+13%/+23%/+17% | +33%/+40%/+18%/+16% | +2%/+43%/+34%/+45% | +41%/+45%/-2%/-6% |
| open20 half | -26%/+19%/+31%/+10% | +56%/+43%/+25%/+22% | +47%/+47%/+43%/+4% | +49%/+49%/+26%/+44% | +38%/+52%/+30%/+12% | +35%/+40%/+51%/+51% | +48%/+44%/+32%/+22% | +34%/+49%/+35%/+33% | -15%/+54%/+49%/+47% | +78%/+80%/-20%/+36% |
| openA40 half | -25%/+19%/+26%/-6% | +48%/+59%/+27%/+49% | +34%/+34%/+36%/+32% | +21%/+21%/+27%/+30% | +10%/+36%/+27%/+40% | +58%/+27%/+42%/+43% | +41%/+48%/+20%/+30% | +38%/+45%/+39%/+40% | -15%/+46%/+50%/+47% | +67%/+68%/+11%/+19% |

Vol tercile (day-range tercile; day-cumulative maxDD cut, mean d $k/day), lock=None: low | mid | high

* sA40>=1 skip: +1% (-0.2) | +14% (-0.4) | +25% (-0.1)
* nA60>=1 skip: +9% (+0.0) | +10% (-0.7) | +23% (-0.2)
* sA40>=1 half: +6% (+0.1) | -14% (-0.9) | +34% (-0.5)
* nA60>=1 half: +11% (+0.2) | -17% (-1.1) | +34% (-0.6)
* sopen40 half: +40% (+1.2) | -5% (-0.1) | +20% (-3.4)
* open20 half: +42% (+1.1) | +35% (-0.4) | +45% (-4.4)
* openA40 half: +47% (+1.4) | +21% (-0.4) | +42% (-4.0)

Best-of-N null: pooled 2400 lock=None information-free masks (random rows / same-volume / shuffled-day of the 3-4 priority cells, same flag shares ~28-36%); best L6M cut among N=314 draws from that pool (2000 repeats): median +76%, 95th percentile +80%. Best real L6M cut among the 34 finalists in lock=None: +51%; sA40>=1 skip +36%, nA60>=1 skip +38%.

Causality audit (audit.py): 100 random signals x 8 lines (800 line-checks): the ahead and behind fresh distance recomputed by brute force from the stream rows with knowable-index ek <= signal second, alive (cap > kin) and never touched (end > kin) equals the stored feature in 800 of 800 checks (0 mismatches); the stream knowable index ek is the POI store's causal timestamp (poi_core), not re-derived here.
## 7. HEADLINE BASE: D7 V13Y (FIXED base = V13X + add-fill ordering fix; V13X was a DEFECT BASE; exact U7 same-side, exact 5 THP take/tighten lines, exact lots, 12R per-book + give-back, ER running-max)

V13Y base: L6M mean 21.2k/wk, maxDD 53k; HOLD mean 16.4k/wk, maxDD 90k; MID mean 6.7k/wk, maxDD 52k; PRE mean 5.9k/wk, maxDD 282k; X' mean -1.1k/wk, maxDD 132k; F9 mean 17.2k/wk, maxDD 53k. Base maxDD-carrying week (L6M / F9 / PRE / X'): 202632 / 202632 / 202447 / 202314.

### 7a. All 34 finalists on V13Y (screen; placebo status in 7c)

| cell (V13X) | flag % | maxDD cut L3M / L6M / HOLD / MID / PRE / X' / F9 | mean d $k/wk L6M (MDE) / PRE (MDE) | S/T/N | TOL-B / nc | ONE-WEEK L6M/F9 | week carrying (L6M) | band (flip row) L6M / PRE / X' | band rule |
|---|---|---|---|---|---|---|---|---|---|
| nA40>=1 skip | 25 | -47% / -50% / +3% / +41% / +19% / +32% / -50% | -3.5 (+12.5) / +0.7 (+8.5) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nA40>=1 half | 25 | -87% / -51% / +9% / +42% / +5% / +21% / -51% | -0.1 (+10.3) / -3.6 (+7.4) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nB40>=1 skip | 21 | -169% / -146% / -44% / +7% / +39% / +6% / -146% | +1.4 (+10.6) / -1.0 (+6.4) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nB40>=1 half | 21 | -110% / -79% / -5% / +3% / +42% / +50% / -79% | -1.2 (+10.9) / -0.6 (+6.1) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nB40>=2 skip | 10 | -37% / -22% / +6% / -38% / +37% / -18% / -36% | +2.1 (+4.7) / +2.5 (+6.3) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nB40>=2 half | 10 | -15% / -25% / +0% / -16% / +37% / +50% / -25% | -0.7 (+8.1) / +1.8 (+5.2) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nB40>=3 skip | 6 | -13% / -6% / -5% / -8% / +28% / +4% / -7% | -0.3 (+1.8) / +2.3 (+5.6) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nB40>=3 half | 6 | -2% / -1% / -3% / -13% / +22% / +44% / -12% | -0.2 (+0.9) / +2.0 (+3.2) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nT40>=2 half | 20 | -92% / -69% / +2% / -28% / +34% / +51% / -69% | -3.8 (+7.6) / -1.5 (+7.7) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nT40>=4 half | 5 | -4% / -2% / +15% / -5% / +23% / +29% / -4% | -0.3 (+0.8) / +0.5 (+4.6) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nA60>=1 skip | 32 | -32% / +30% / +1% / -2% / +46% / +34% / -1% | -2.3 (+14.6) / +0.9 (+10.2) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nA60>=1 half | 32 | +3% / -3% / +8% / +37% / +22% / +20% / -3% | -1.7 (+12.1) / -2.2 (+7.1) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nA60>=2 half | 14 | -63% / -17% / +11% / +14% / -6% / +34% / -17% | +0.8 (+9.0) / -3.3 (+6.7) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nT60>=3 skip | 22 | -154% / -118% / -28% / -13% / +10% / +3% / -118% | +0.7 (+14.6) / -2.7 (+8.6) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| nTany40>=2 half | 47 | -169% / -72% / -0% / +25% / +30% / +60% / -72% | -0.6 (+10.8) / -0.4 (+7.4) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| open20 half | 81 | +28% / +21% / +41% / +23% / +55% / +16% / +21% | -8.7 (+13.7) / -4.0 (+6.4) | Y/n/Y | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| open60 half | 47 | +36% / +47% / +29% / -4% / +30% / +2% / -3% | -4.1 (+13.4) / -4.2 (+5.8) | n/n/Y | n / n | n/n | 202632 | flip 5: 36/28/29% | PASS |
| openA40 half | 75 | -28% / -28% / +25% / +18% / +41% / +66% / -28% | -10.8 (+15.3) / -3.8 (+6.1) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| rho40>=2 skip | 18 | +3% / -24% / +3% / +44% / +9% / +38% / -24% | -3.4 (+11.6) / +0.3 (+7.9) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| rho40<=0.5 skip | 15 | -81% / -102% / -18% / -18% / +33% / -31% / -102% | +1.0 (+9.0) / -0.5 (+5.9) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| rho60>=2 skip | 20 | -63% / +17% / +26% / +42% / +44% / +13% / +17% | +2.5 (+13.8) / +2.0 (+8.3) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| rho60>=2 half | 20 | +11% / -1% / +29% / +34% / +29% / -6% / -1% | +1.2 (+9.8) / -2.0 (+7.3) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| rho60<=0.5 half | 24 | -32% / -84% / -7% / -17% / +24% / +33% / -84% | +0.1 (+8.7) / -0.8 (+6.2) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| mid_PDR half | 22 | -59% / -79% / -5% / -16% / +42% / +45% / -79% | -2.8 (+12.2) / +1.5 (+5.0) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| mid_any3 half | 41 | -188% / -124% / -31% / -11% / +44% / +47% / -124% | -5.8 (+13.4) / +0.5 (+5.8) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| mid_PDR&open40 up | 10 | -16% / -8% / -25% / +15% / +19% / -16% / -8% | +3.6 (+5.9) / -2.8 (+7.2) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| mid_ON&nT40<=1 up | 10 | +6% / -54% / -18% / +15% / -30% / +2% / -54% | +1.7 (+6.0) / -2.5 (+4.9) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| sA40>=1 skip | 28 | -32% / +34% / -1% / -2% / +27% / +34% / -1% | -2.0 (+15.0) / +0.0 (+9.4) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| sA40>=1 half | 28 | +3% / -3% / +5% / +50% / +6% / +23% / -3% | -1.5 (+12.2) / -3.7 (+7.5) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| sA40>=2 half | 11 | -63% / -18% / +13% / +27% / +17% / +9% / -18% | +1.3 (+9.4) / -2.6 (+6.9) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| sB40>=3 half | 7 | -31% / -15% / +0% / -13% / +25% / +36% / -15% | +0.2 (+1.7) / +2.3 (+3.5) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| sA60>=1 half | 36 | +0% / -4% / +15% / +34% / +15% / +16% / -4% | -1.0 (+11.3) / -2.2 (+7.1) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |
| sopen40 half | 55 | -38% / +31% / +38% / -8% / +7% / +3% / -7% | -4.8 (+13.2) / -4.2 (+5.5) | n/n/n | n / n | n/n | 202632 | flip 5: 36/28/29% | NOISE |

Band rule (Z3 V13X band, lock 12R, DS3_ZONES_3_NOISE.md; the earlier assumed-base band is superseded): 1 of 33 pass; TOLERANT 0, STRICT 1.

### 7b. Scaled cut-off sweep on V13Y (sA40>=1 skip)

| factor | cuts L6M / HOLD / MID / PRE / X' / F9 | mean d F9 (MDE) |
|---|---|---|
| x1.0 | +34% / -1% / -2% / +27% / +34% / -1% | +1.3 (+12.6) |

### 7c. V13X placebo ranks (share of draws with cut >= real; n draws), L6M and PRE

| cell | real L6M / PRE | B L6M (n) | C L6M | A L6M | B PRE | C PRE | A PRE | label |
|---|---|---|---|---|---|---|---|---|
| nA60>=1 skip | +30% / +46% | 0.03 (100) | 0.05 | 0.05 | 0.29 | 0.24 | 0.39 | placebos beaten |
| sA40>=1 skip | +34% / +27% | 0.01 (100) | 0.04 | 0.02 | 0.68 | 0.57 | 0.62 | placebos beaten |
| sopen40 half | +31% / +7% | 0.03 (100) | 0.04 | 0.05 | 0.83 | 0.83 | 0.88 | placebos beaten |

### 7d. Per-scope reruns on V13Y (rule applied only to the book / session; cut on the TOTAL composite)

| cell | scope | cut L6M | cut F9 | cut PRE | cut X' | mean d F9 (MDE) |
|---|---|---|---|---|---|---|

### 7e. Re-target decision delay on V13Y (sA40>=1; rtc = same market entry with the original target)

| action | delay | cuts L6M / F9 / PRE / X' | mean d F9 (MDE) |
|---|---|---|---|

### 7f. Vol-tercile cuts on V13Y (day-range tercile over all days; day-cumulative maxDD cut, mean d $k/day)

| cell | low vol | mid | high |
|---|---|---|---|
| sA40>=1 skip | +7% (+0.3) | +17% (+0.1) | -16% (-0.4) |
| sA40>=1 half | +27% (+0.7) | +16% (-0.3) | +3% (-1.8) |
| sA60>=1 half | +32% (+0.8) | +21% (-0.1) | -16% (-1.7) |
| rho60>=2 skip | +2% (+0.3) | +50% (+0.7) | -2% (-0.2) |
| rho60>=2 half | +21% (+0.6) | +42% (+0.2) | -19% (-1.4) |
| nA60>=1 half | +31% (+0.8) | +19% (-0.4) | +4% (-1.5) |
| open20 half | +41% (+0.9) | +47% (+0.1) | +50% (-3.4) |

### 7g. MASTER TABLE finalist x frame: V13Y lock=12 (shipped combined lock) vs lock=None (engine per-book locks only); HEADLINE frame = lock=None until the user confirms; LOCK-ONLY = lock=12 L6M cut >= 10% but lock=None L6M cut < 5%

lock=None base: L6M mean 28.8k, maxDD 96k; F9 mean 25.6k, maxDD 96k; PRE mean 12.1k, maxDD 130k; X' mean 1.6k, maxDD 70k

| cell | lock=12 cuts L6M / F9 / PRE / X' | lock=None cuts L6M / F9 / PRE / X' | mean d F9 lock=None (MDE) | ONE-WEEK (lock=None L6M/F9) | Z3 band pass (V13X-based) lock=12 / lock=None | label |
|---|---|---|---|---|---|---|
| nA40>=1 skip | -50% / -50% / +19% / +32% | +5% / +5% / -5% / -4% | -3.8 (+9.4) | n/n | noise / noise | - |
| nA40>=1 half | -51% / -51% / +5% / +21% | -9% / -9% / -15% / -19% | -1.8 (+5.4) | n/n | noise / noise | - |
| nB40>=1 skip | -146% / -146% / +39% / +6% | -73% / -73% / +0% / -12% | -5.4 (+6.3) | n/n | noise / noise | - |
| nB40>=1 half | -79% / -79% / +42% / +50% | -36% / -36% / -8% / +1% | -5.8 (+6.0) | n/n | noise / noise | - |
| nB40>=2 skip | -22% / -36% / +37% / -18% | -22% / -22% / -3% / -34% | -1.2 (+3.7) | n/n | noise / noise | - |
| nB40>=2 half | -25% / -25% / +37% / +50% | -18% / -18% / -10% / -3% | -3.3 (+5.4) | n/n | noise / noise | - |
| nB40>=3 skip | -6% / -7% / +28% / +4% | +1% / +1% / -9% / -29% | -0.7 (+2.2) | n/n | noise / noise | - |
| nB40>=3 half | -1% / -12% / +22% / +44% | +0% / +0% / -7% / -12% | -1.1 (+1.5) | n/n | noise / noise | - |
| nT40>=2 half | -69% / -69% / +34% / +51% | -29% / -29% / -2% / -24% | -4.5 (+5.6) | n/n | noise / noise | - |
| nT40>=4 half | -2% / -4% / +23% / +29% | +0% / +0% / +1% / +20% | -0.6 (+0.8) | n/n | noise / noise | - |
| nA60>=1 skip | +30% / -1% / +46% / +34% | +36% / +36% / -36% / +7% | -5.4 (+11.6) | Y/Y | noise / noise | ONE-WEEK |
| nA60>=1 half | -3% / -3% / +22% / +20% | -10% / -10% / -6% / +16% | -5.5 (+6.9) | n/n | noise / noise | - |
| nA60>=2 half | -17% / -17% / -6% / +34% | -19% / -19% / -3% / -19% | -1.9 (+3.3) | n/n | noise / noise | - |
| nT60>=3 skip | -118% / -118% / +10% / +3% | -16% / -16% / +2% / -35% | -1.9 (+8.4) | n/n | noise / noise | - |
| nTany40>=2 half | -72% / -72% / +30% / +60% | -2% / -2% / -36% / -18% | -4.0 (+7.8) | n/n | noise / noise | - |
| open20 half | +21% / +21% / +55% / +16% | +41% / +41% / +17% / +9% | -11.6 (+11.1) | n/n | noise / noise | both frames + |
| open60 half | +47% / -3% / +30% / +2% | +42% / +42% / +4% / +33% | -6.2 (+10.5) | n/n | PASS / PASS | both frames + |
| openA40 half | -28% / -28% / +41% / +66% | +35% / +35% / +20% / +41% | -9.8 (+10.0) | n/n | noise / PASS | both frames + |
| rho40>=2 skip | -24% / -24% / +9% / +38% | +21% / +21% / +8% / -7% | -2.0 (+8.6) | n/n | noise / noise | both frames + |
| rho40<=0.5 skip | -102% / -102% / +33% / -31% | -54% / -54% / -5% / -25% | -3.7 (+6.0) | n/n | noise / noise | - |
| rho60>=2 skip | +17% / +17% / +44% / +13% | +41% / +41% / +1% / +36% | +0.1 (+10.1) | Y/Y | noise / PASS | ONE-WEEK |
| rho60>=2 half | -1% / -1% / +29% / -6% | +8% / +8% / +4% / +13% | -2.6 (+5.0) | n/n | noise / noise | both frames + |
| rho60<=0.5 half | -84% / -84% / +24% / +33% | -51% / -51% / -36% / -31% | -4.1 (+4.8) | n/n | noise / noise | - |
| mid_PDR half | -79% / -79% / +42% / +45% | -30% / -30% / -18% / +21% | -6.4 (+6.8) | n/n | noise / noise | - |
| mid_any3 half | -124% / -124% / +44% / +47% | -61% / -61% / -9% / +23% | -8.8 (+8.1) | n/n | noise / noise | - |
| mid_PDR&open40 up | -8% / -8% / +19% / -16% | -15% / -15% / -13% / -1% | +3.5 (+5.6) | n/n | noise / noise | - |
| mid_ON&nT40<=1 up | -54% / -54% / -30% / +2% | +7% / +7% / -19% / -6% | +2.4 (+3.3) | n/n | noise / noise | - |
| sA40>=1 skip | +34% / -1% / +27% / +34% | +36% / +36% / +0% / -5% | -3.9 (+12.4) | Y/Y | noise / noise | ONE-WEEK |
| sA40>=1 half | -3% / -3% / +6% / +23% | -8% / -8% / -6% / -11% | -4.4 (+7.5) | n/n | noise / noise | - |
| sA40>=2 half | -18% / -18% / +17% / +9% | -19% / -19% / -0% / -9% | -1.6 (+3.2) | n/n | noise / noise | - |
| sB40>=3 half | -15% / -15% / +25% / +36% | -4% / -4% / -5% / +11% | -0.7 (+2.3) | n/n | noise / noise | - |
| sA60>=1 half | -4% / -4% / +15% / +16% | -14% / -14% / -6% / +7% | -4.3 (+5.8) | n/n | noise / noise | - |
| sopen40 half | +31% / -7% / +7% / +3% | +41% / +41% / +11% / +21% | -6.4 (+10.4) | n/n | noise / noise | both frames + |


Z3 noise-band rule (band computed on V13Y, recompute on V13Y pending) (band row by flagged share; flip 5.0 for masks >= 3.5% of rows): lock=12 passes: ['open60 half']; lock=None passes: ['open60 half', 'openA40 half', 'rho60>=2 skip'] (necessary, not sufficient; the passing cells fail the placebo and carrying-week standards above).

### 7h. lock=None frame for the cells that hold in both frames: cut-off sweep (sA40>=1 skip) and placebo ranks (share of draws with cut >= real; n per kind)

| factor | cuts L6M / HOLD / MID / PRE / X' / F9 (lock=None) |
|---|---|
| x1.0 | +36% / +16% / +12% / +0% / -5% / +36% |

| cell | real L6M / PRE / X' | B L6M / PRE / X' (n) | C L6M / PRE / X' | A L6M / PRE / X' | label |
|---|---|---|---|---|---|
| sA40>=1 skip | +36% / +0% / -5% | 0.24 / 0.16 / 0.40 (100) | 0.27 / 0.13 / 0.44 | 0.27 / 0.20 / 0.51 | (volume effect) |
| rho60>=2 skip | +41% / +1% / +36% | 0.15 / 0.22 / 0.05 (100) | 0.20 / 0.12 / 0.04 | 0.10 / 0.15 / 0.03 | (volume effect) |
| nA60>=1 skip | +36% / -36% / +7% | 0.27 / 0.65 / 0.31 (100) | 0.25 / 0.67 / 0.29 | 0.33 / 0.70 / 0.35 | (volume effect) |
| sA40>=1 half | -8% / -6% / -11% | 0.66 / 0.28 / 0.74 (100) | 0.66 / 0.25 / 0.67 | 0.76 / 0.25 / 0.76 | (volume effect) |
| nA60>=1 half | -10% / -6% / +16% | 0.69 / 0.34 / 0.28 (100) | 0.79 / 0.31 / 0.32 | 0.74 / 0.41 / 0.31 | (volume effect) |
| open20 half | +41% / +17% / +9% | 0.46 / 0.49 / 0.89 (100) | 0.38 / 0.58 / 0.88 | 0.34 / 0.54 / 0.79 | (volume effect) |
| openA40 half | +35% / +20% / +41% | 0.53 / 0.34 / 0.29 (100) | 0.38 / 0.33 / 0.25 | 0.47 / 0.35 / 0.22 | (volume effect) |
| sopen40 half | +41% / +11% / +21% | 0.24 / 0.26 / 0.37 (100) | 0.16 / 0.24 / 0.44 | 0.30 / 0.25 / 0.41 | (volume effect) |

### 7i. Priority cells in the lock=None frame (headline): episode-proofing, book x session, vol tercile, best-of-N null, causality audit

| cell (lock=None) | window | cut | carrying week | cut w/o it | LOWO range | LOMO range | bootstrap 90% CI / P(cut>0) | ONE-WEEK |
|---|---|---|---|---|---|---|---|---|
| sA40>=1 skip | L6M | +36% | 202630 | -7% | -7% .. +61% | -86% .. +61% | [-118%, +65%] / 0.64 | ONE-WEEK |
| sA40>=1 skip | HOLD | +16% | 202606 | +10% | +10% .. +29% | -2% .. +26% | [-57%, +50%] / 0.78 | - |
| sA40>=1 skip | MID | +12% | 202613 | +9% | -58% .. +45% | +9% .. +31% | [-41%, +65%] / 0.72 | - |
| sA40>=1 skip | PRE | +0% | 202436 | +15% | -19% .. +15% | +0% .. +15% | [-55%, +54%] / 0.79 | - |
| sA40>=1 skip | X' | -5% | 202329 | -29% | -29% .. +30% | -30% .. +30% | [-63%, +29%] / 0.34 | - |
| sA40>=1 skip | F9 | +36% | 202630 | -7% | -7% .. +61% | -86% .. +61% | [-104%, +63%] / 0.69 | ONE-WEEK |
| nA60>=1 skip | L6M | +36% | 202630 | -7% | -7% .. +56% | -86% .. +56% | [-118%, +65%] / 0.65 | ONE-WEEK |
| nA60>=1 skip | HOLD | +9% | 202606 | +3% | +3% .. +35% | +3% .. +35% | [-56%, +52%] / 0.80 | - |
| nA60>=1 skip | MID | +6% | 202613 | +3% | -52% .. +38% | +3% .. +31% | [-28%, +54%] / 0.72 | - |
| nA60>=1 skip | PRE | -36% | 202436 | +0% | -46% .. +0% | -36% .. +13% | [-47%, +58%] / 0.81 | - |
| nA60>=1 skip | X' | +7% | 202329 | -14% | -22% .. +36% | -14% .. +26% | [-47%, +41%] / 0.59 | - |
| nA60>=1 skip | F9 | +36% | 202630 | -7% | -7% .. +56% | -86% .. +56% | [-98%, +62%] / 0.71 | ONE-WEEK |
| sA40>=1 half | L6M | -8% | 202630 | -18% | -20% .. +4% | -45% .. -2% | [-107%, -2%] / 0.01 | - |
| sA40>=1 half | HOLD | -1% | 202606 | -8% | -8% .. +20% | -32% .. +22% | [-78%, +59%] / 0.51 | - |
| sA40>=1 half | MID | +18% | 202613 | +16% | +16% .. +64% | +16% .. +64% | [+16%, +76%] / 1.00 | - |
| sA40>=1 half | PRE | -6% | 202436 | -11% | -34% .. +11% | -15% .. +16% | [-25%, +33%] / 0.82 | - |
| sA40>=1 half | X' | -11% | 202329 | -31% | -45% .. +15% | -41% .. +15% | [-106%, +9%] / 0.14 | - |
| sA40>=1 half | F9 | -8% | 202630 | -18% | -20% .. +4% | -45% .. -2% | [-87%, +13%] / 0.12 | - |
| nA60>=1 half | L6M | -10% | 202630 | -21% | -23% .. +1% | -45% .. -2% | [-110%, -2%] / 0.01 | - |
| nA60>=1 half | HOLD | -2% | 202606 | -10% | -10% .. +22% | -34% .. +22% | [-73%, +51%] / 0.51 | - |
| nA60>=1 half | MID | +8% | 202613 | +16% | +6% .. +39% | +8% .. +16% | [+8%, +39%] / 1.00 | - |
| nA60>=1 half | PRE | -6% | 202436 | +11% | -11% .. +11% | -6% .. +11% | [-13%, +39%] / 0.86 | - |
| nA60>=1 half | X' | +16% | 202329 | -3% | -3% .. +31% | -3% .. +31% | [-50%, +22%] / 0.41 | ONE-WEEK |
| nA60>=1 half | F9 | -10% | 202630 | -21% | -23% .. +1% | -45% .. -2% | [-89%, +5%] / 0.09 | - |
| sopen40 half | L6M | +41% | 202630 | +63% | +32% .. +63% | +32% .. +54% | [+32%, +66%] / 1.00 | - |
| sopen40 half | HOLD | +34% | 202606 | +41% | +13% .. +44% | +34% .. +41% | [+21%, +51%] / 0.98 | - |
| sopen40 half | MID | -9% | 202613 | -12% | -48% .. +32% | -9% .. +3% | [-26%, +11%] / 0.45 | - |
| sopen40 half | PRE | +11% | 202436 | +7% | -3% .. +28% | -33% .. +25% | [-27%, +27%] / 0.78 | - |
| sopen40 half | X' | +21% | 202329 | +9% | +3% .. +40% | -9% .. +29% | [-14%, +43%] / 0.75 | ONE-WEEK |
| sopen40 half | F9 | +41% | 202630 | +43% | +32% .. +49% | +0% .. +41% | [-9%, +45%] / 0.93 | - |
| open20 half | L6M | +41% | 202630 | +44% | +25% .. +62% | +19% .. +62% | [+14%, +71%] / 0.97 | - |
| open20 half | HOLD | +35% | 202606 | +41% | +33% .. +41% | +35% .. +41% | [+21%, +62%] / 0.99 | - |
| open20 half | MID | +13% | 202613 | +11% | +11% .. +46% | +11% .. +16% | [+11%, +26%] / 1.00 | - |
| open20 half | PRE | +17% | 202436 | +14% | +7% .. +29% | -22% .. +23% | [-7%, +37%] / 0.90 | - |
| open20 half | X' | +9% | 202329 | +24% | -3% .. +42% | +9% .. +26% | [-3%, +54%] / 0.94 | - |
| open20 half | F9 | +41% | 202630 | +44% | +25% .. +62% | +19% .. +62% | [+3%, +62%] / 0.96 | - |
| openA40 half | L6M | +35% | 202630 | +39% | +24% .. +50% | +35% .. +50% | [+35%, +55%] / 1.00 | - |
| openA40 half | HOLD | +40% | 202606 | +35% | +33% .. +52% | +35% .. +53% | [+18%, +59%] / 0.99 | - |
| openA40 half | MID | -4% | 202613 | +21% | -13% .. +35% | -4% .. +21% | [-26%, +21%] / 0.45 | - |
| openA40 half | PRE | +20% | 202436 | +24% | +9% .. +35% | -14% .. +26% | [-19%, +35%] / 0.84 | - |
| openA40 half | X' | +41% | 202329 | +35% | +27% .. +52% | +34% .. +47% | [+19%, +63%] / 0.99 | - |
| openA40 half | F9 | +35% | 202630 | +39% | +24% .. +50% | +4% .. +50% | [-1%, +53%] / 0.95 | - |

Per book x session maxDD cut (lock=None, rule applied everywhere; L6M | HOLD | PRE | X'):

| cell | K6 | P6 | U6 | H6 | M6 | A6 | asia | london | nyam | nypm |
|---|---|---|---|---|---|---|---|---|---|---|
| sA40>=1 skip | +60%/+23%/-9%/+56% | +47%/+9%/+2%/+29% | +19%/+19%/+6%/-13% | +54%/-31%/-1%/+18% | +8%/+4%/+27%/-4% | -111%/-95%/+29%/-14% | +21%/+21%/+17%/+20% | -41%/-32%/+7%/+24% | +11%/+1%/-8%/+10% | +55%/+36%/+15%/-14% |
| nA60>=1 skip | +61%/+19%/+6%/+52% | +44%/+11%/-28%/+41% | +19%/+17%/+1%/-22% | +54%/-11%/+15%/+4% | +8%/+3%/+47%/-10% | -111%/-95%/+8%/+22% | +21%/+21%/-22%/+38% | -31%/-26%/+21%/+19% | +10%/-6%/-9%/+37% | +55%/+38%/+16%/+3% |
| sA40>=1 half | -22%/+20%/-52%/-23% | -6%/+9%/+16%/-10% | +17%/+17%/+1%/-2% | +35%/-2%/+2%/+16% | +16%/+21%/+20%/-13% | -13%/-5%/+14%/+25% | -4%/-4%/+14%/+14% | -61%/-17%/+10%/-9% | +34%/+4%/-11%/-0% | -3%/-7%/-22%/+10% |
| nA60>=1 half | -22%/+20%/-34%/+3% | -8%/+8%/-3%/+27% | +17%/+17%/-1%/-2% | +35%/+8%/+8%/+11% | +16%/+21%/+20%/-15% | -13%/-5%/-4%/+29% | -8%/-8%/+4%/+24% | -59%/-16%/+17%/+5% | +34%/+0%/-6%/+14% | -3%/-7%/-8%/+17% |
| sopen40 half | +6%/+22%/+23%/+16% | +48%/+44%/+11%/+28% | +11%/+11%/+34%/+8% | -20%/-4%/+43%/+13% | +47%/+40%/+27%/+45% | +55%/-12%/+30%/+35% | +51%/+8%/+12%/+14% | +44%/+50%/+15%/+3% | +18%/+36%/+40%/+49% | +50%/+52%/+13%/-6% |
| open20 half | -14%/+25%/+30%/+9% | +52%/+35%/+16%/+25% | +47%/+47%/+31%/+31% | +38%/+36%/+38%/+33% | +41%/+50%/+33%/+11% | +35%/+40%/+51%/+51% | +44%/+44%/+32%/+26% | +41%/+41%/+34%/+27% | +16%/+39%/+50%/+47% | +80%/+84%/-2%/+40% |
| openA40 half | -21%/+21%/+25%/-10% | +46%/+54%/+16%/+38% | +32%/+32%/+41%/+39% | +36%/+33%/+26%/+17% | +19%/+31%/+30%/+43% | +58%/+27%/+42%/+43% | +40%/+40%/+7%/+36% | +38%/+45%/+36%/+32% | +13%/+35%/+54%/+49% | +68%/+69%/+27%/+19% |

Vol tercile (day-range tercile; day-cumulative maxDD cut, mean d $k/day), lock=None: low | mid | high

* sA40>=1 skip: -5% (-0.4) | +18% (-0.4) | +16% (-0.2)
* nA60>=1 skip: +5% (-0.2) | +14% (-0.7) | +9% (-0.4)
* sA40>=1 half: +4% (-0.1) | -2% (-0.8) | +34% (-0.6)
* nA60>=1 half: +9% (+0.0) | -4% (-1.0) | +34% (-0.7)
* sopen40 half: +37% (+1.1) | +1% (+0.0) | +16% (-3.5)
* open20 half: +41% (+0.9) | +37% (-0.4) | +42% (-4.7)
* openA40 half: +47% (+1.1) | +26% (-0.4) | +34% (-4.4)

Best-of-N null: pooled 2700 lock=None information-free masks (random rows / same-volume / shuffled-day of the 3-4 priority cells, same flag shares ~28-36%); best L6M cut among N=314 draws from that pool (2000 repeats): median +75%, 95th percentile +80%. Best real L6M cut among the 34 finalists in lock=None: +42%; sA40>=1 skip +36%, nA60>=1 skip +36%.

Causality audit (audit.py): 100 random signals x 8 lines (800 line-checks): the ahead and behind fresh distance recomputed by brute force from the stream rows with knowable-index ek <= signal second, alive (cap > kin) and never touched (end > kin) equals the stored feature in 800 of 800 checks (0 mismatches); the stream knowable index ek is the POI store's causal timestamp (poi_core), not re-derived here.
## 9. BASE V13Z (= V13Y + nfix: basis-N take deltas; exact U7 same-side, exact 5 THP take/tighten lines, exact lots, 12R per-book + give-back, ER running-max)

V13Z base: L6M mean 12.7k/wk, maxDD 117k; HOLD mean 10.2k/wk, maxDD 122k; MID mean 0.8k/wk, maxDD 70k; PRE mean 3.0k/wk, maxDD 363k; X' mean -2.5k/wk, maxDD 139k; F9 mean 9.3k/wk, maxDD 117k. Base maxDD-carrying week (L6M / F9 / PRE / X'): 202631 / 202631 / 202447 / 202314.

### 9a. All 34 finalists on V13Z (screen; placebo status in 7c)

| cell (V13X) | flag % | maxDD cut L3M / L6M / HOLD / MID / PRE / X' / F9 | mean d $k/wk L6M (MDE) / PRE (MDE) | S/T/N | TOL-B / nc | ONE-WEEK L6M/F9 | week carrying (L6M) | band (flip row) L6M / PRE / X' | band rule |
|---|---|---|---|---|---|---|---|---|---|
| nA40>=1 skip | 25 | -17% / -11% / -7% / +51% / +26% / +34% / -11% | -1.9 (+11.6) / +1.4 (+8.6) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA40>=1 half | 25 | -23% / -5% / -0% / +44% / +8% / +26% / -5% | -0.7 (+10.8) / -2.5 (+7.0) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=1 skip | 21 | -26% / -16% / -11% / +9% / +35% / +0% / -16% | +3.5 (+7.5) / -0.3 (+5.8) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=1 half | 21 | -44% / -28% / -22% / +21% / +47% / +52% / -28% | -2.8 (+6.1) / +0.9 (+5.8) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=2 skip | 10 | -28% / -14% / -9% / -12% / +40% / -20% / -14% | +0.7 (+3.6) / +3.2 (+6.3) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=2 half | 10 | +9% / -9% / -5% / +0% / +35% / +47% / -9% | -1.5 (+6.6) / +2.1 (+5.7) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=3 skip | 6 | -10% / -4% / -0% / -6% / +25% / -8% / -4% | -0.2 (+1.8) / +2.5 (+6.0) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=3 half | 6 | -6% / -3% / +2% / +2% / +10% / +45% / -3% | +0.1 (+1.2) / +2.1 (+3.0) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nT40>=2 half | 20 | -30% / -36% / -30% / +1% / +41% / +53% / -36% | -3.3 (+8.4) / -1.0 (+7.5) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nT40>=4 half | 5 | -36% / -25% / -20% / -6% / +1% / +32% / -25% | -3.1 (+6.1) / +0.1 (+3.5) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA60>=1 skip | 32 | +20% / +14% / +18% / +23% / +51% / +27% / +14% | +0.2 (+13.5) / +1.9 (+10.1) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA60>=1 half | 32 | -12% / +0% / +4% / +35% / +19% / +24% / +0% | -0.7 (+10.9) / -2.2 (+7.2) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA60>=2 half | 14 | -28% / -14% / -9% / +15% / +4% / +17% / -14% | -2.7 (+6.1) / -2.2 (+6.4) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nT60>=3 skip | 22 | -54% / -34% / -28% / -3% / +20% / -15% / -34% | +2.0 (+13.1) / -1.2 (+8.5) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nTany40>=2 half | 47 | -50% / -17% / -12% / +37% / +42% / +52% / -17% | +0.5 (+9.9) / +0.4 (+7.9) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| open20 half | 81 | +39% / +47% / +44% / +35% / +50% / +14% / +47% | -4.5 (+11.5) / -2.5 (+5.8) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | PASS |
| open60 half | 47 | +38% / +60% / +43% / +33% / +19% / -1% / +60% | -2.2 (+11.5) / -3.6 (+5.3) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| openA40 half | 75 | +21% / +32% / +35% / +32% / +43% / +55% / +32% | -5.4 (+13.5) / -2.3 (+5.9) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho40>=2 skip | 18 | -4% / -6% / -1% / +57% / +21% / +29% / -6% | -2.0 (+11.1) / +1.0 (+8.0) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho40<=0.5 skip | 15 | -23% / -19% / -14% / -1% / +41% / -36% / -19% | +0.4 (+4.0) / +0.1 (+6.1) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho60>=2 skip | 20 | +14% / +15% / +18% / +48% / +48% / +15% / +15% | +3.6 (+11.8) / +2.6 (+8.4) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho60>=2 half | 20 | -25% / +1% / +5% / +36% / +29% / -7% / +1% | +2.0 (+9.1) / -1.2 (+7.0) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho60<=0.5 half | 24 | +7% / +8% / +12% / +13% / +31% / +23% / +8% | +2.0 (+7.3) / +0.4 (+6.2) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| mid_PDR half | 22 | -56% / -34% / -28% / -9% / +47% / +47% / -34% | -3.6 (+13.0) / +2.3 (+5.2) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| mid_any3 half | 41 | -80% / -33% / -28% / -1% / +49% / +50% / -33% | -4.3 (+11.6) / +1.7 (+5.3) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| mid_PDR&open40 up | 10 | +21% / +27% / +1% / +16% / +15% / -18% / +27% | +4.9 (+5.7) / -2.3 (+7.0) | n/n/Y | n / n | Y/Y | 202631 | flip 5: 36/28/29% | NOISE |
| mid_ON&nT40<=1 up | 10 | +24% / +12% / +15% / -2% / -21% / -2% / +12% | +1.4 (+3.3) / -2.4 (+4.8) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA40>=1 skip | 28 | +20% / +31% / +25% / +23% / +23% / +27% / +31% | +0.8 (+14.0) / +0.8 (+9.5) | Y/Y/Y | Y / Y | Y/Y | 202631 | flip 5: 36/28/29% | NOISE |
| sA40>=1 half | 28 | -12% / +0% / +4% / +51% / +4% / +33% / +0% | -0.7 (+10.9) / -2.9 (+7.1) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA40>=2 half | 11 | -30% / -14% / -9% / +20% / +21% / +10% / -14% | -0.1 (+9.8) / -2.1 (+6.6) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sB40>=3 half | 7 | +3% / +2% / +6% / +3% / +25% / +37% / +2% | +0.6 (+1.9) / +3.0 (+3.7) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA60>=1 half | 36 | +2% / +24% / +27% / +35% / +21% / +20% / +24% | -0.2 (+12.0) / -1.8 (+7.3) | Y/Y/Y | Y / Y | Y/Y | 202631 | flip 5: 36/28/29% | NOISE |
| sopen40 half | 55 | +24% / +60% / +45% / +7% / +14% / -4% / +44% | -2.4 (+11.2) / -3.3 (+5.3) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |

Band rule (Z3 V13X band, lock 12R, DS3_ZONES_3_NOISE.md; the earlier assumed-base band is superseded): 1 of 33 pass; TOLERANT 8, STRICT 8.

### 9b. Scaled cut-off sweep on V13Z (sA40>=1 skip)

| factor | cuts L6M / HOLD / MID / PRE / X' / F9 | mean d F9 (MDE) |
|---|---|---|
| x1.0 | +31% / +25% / +23% / +23% / +27% / +31% | +2.2 (+11.2) |

### 9c. V13X placebo ranks (share of draws with cut >= real; n draws), L6M and PRE

| cell | real L6M / PRE | B L6M (n) | C L6M | A L6M | B PRE | C PRE | A PRE | label |
|---|---|---|---|---|---|---|---|---|

### 9d. Per-scope reruns on V13Z (rule applied only to the book / session; cut on the TOTAL composite)

| cell | scope | cut L6M | cut F9 | cut PRE | cut X' | mean d F9 (MDE) |
|---|---|---|---|---|---|---|

### 9e. Re-target decision delay on V13Z (sA40>=1; rtc = same market entry with the original target)

| action | delay | cuts L6M / F9 / PRE / X' | mean d F9 (MDE) |
|---|---|---|---|

### 9f. Vol-tercile cuts on V13Z (day-range tercile over all days; day-cumulative maxDD cut, mean d $k/day)

| cell | low vol | mid | high |
|---|---|---|---|
| sA40>=1 skip | +6% (+0.3) | +14% (+0.2) | -13% (+0.0) |
| sA40>=1 half | +24% (+0.7) | +18% (-0.1) | -6% (-1.4) |
| sA60>=1 half | +29% (+0.8) | +19% (-0.0) | -3% (-1.2) |
| rho60>=2 skip | +3% (+0.3) | +50% (+0.8) | +6% (+0.1) |
| rho60>=2 half | +19% (+0.6) | +41% (+0.3) | -8% (-0.9) |
| nA60>=1 half | +27% (+0.7) | +20% (-0.2) | -6% (-1.2) |
| open20 half | +35% (+0.9) | +54% (+0.3) | +55% (-2.5) |

### 9g. MASTER TABLE finalist x frame: V13Z lock=12 (shipped combined lock) vs lock=None (engine per-book locks only); HEADLINE frame = lock=None until the user confirms; LOCK-ONLY = lock=12 L6M cut >= 10% but lock=None L6M cut < 5%

lock=None base: L6M mean 16.8k, maxDD 183k; F9 mean 14.6k, maxDD 183k; PRE mean 8.4k, maxDD 173k; X' mean 1.2k, maxDD 88k

| cell | lock=12 cuts L6M / F9 / PRE / X' | lock=None cuts L6M / F9 / PRE / X' | mean d F9 lock=None (MDE) | ONE-WEEK (lock=None L6M/F9) | Z3 band pass (V13X-based) lock=12 / lock=None | label |
|---|---|---|---|---|---|---|
| nA40>=1 skip | -11% / -11% / +26% / +34% | -5% / -5% / +14% / +14% | -1.6 (+9.2) | n/n | noise / noise | - |
| nA40>=1 half | -5% / -5% / +8% / +26% | -7% / -7% / -24% / -18% | -2.3 (+6.3) | n/n | noise / noise | - |
| nB40>=1 skip | -16% / -16% / +35% / +0% | -34% / -34% / +14% / +6% | -3.2 (+6.3) | n/n | noise / noise | - |
| nB40>=1 half | -28% / -28% / +47% / +52% | -17% / -17% / -12% / +2% | -4.9 (+5.6) | n/n | noise / noise | - |
| nB40>=2 skip | -14% / -14% / +40% / -20% | -20% / -20% / +15% / -16% | -0.7 (+4.2) | n/n | noise / noise | - |
| nB40>=2 half | -9% / -9% / +35% / +47% | -13% / -13% / -9% / +7% | -2.8 (+5.1) | n/n | noise / noise | - |
| nB40>=3 skip | -4% / -4% / +25% / -8% | -1% / -1% / +9% / -12% | -0.5 (+2.0) | n/n | noise / noise | - |
| nB40>=3 half | -3% / -3% / +10% / +45% | -1% / -1% / +9% / -9% | -0.9 (+1.4) | n/n | noise / noise | - |
| nT40>=2 half | -36% / -36% / +41% / +53% | -26% / -26% / -7% / -15% | -3.9 (+5.4) | n/n | noise / noise | - |
| nT40>=4 half | -25% / -25% / +1% / +32% | -8% / -8% / +7% / +30% | -2.1 (+4.2) | n/n | noise / noise | - |
| nA60>=1 skip | +14% / +14% / +51% / +27% | +32% / +32% / -8% / +19% | -2.4 (+11.5) | n/n | noise / noise | - |
| nA60>=1 half | +0% / +0% / +19% / +24% | -1% / -1% / -3% / +20% | -4.1 (+6.6) | n/n | noise / noise | - |
| nA60>=2 half | -14% / -14% / +4% / +17% | -5% / -5% / -16% / -22% | -2.2 (+5.0) | n/n | noise / noise | - |
| nT60>=3 skip | -34% / -34% / +20% / -15% | -18% / -18% / +13% / -18% | -0.9 (+8.5) | n/n | noise / noise | - |
| nTany40>=2 half | -17% / -17% / +42% / +52% | +3% / +3% / -30% / -18% | -2.2 (+7.7) | n/n | noise / noise | - |
| open20 half | +47% / +47% / +50% / +14% | +43% / +43% / +3% / +8% | -6.4 (+10.3) | n/n | PASS / noise | both frames + |
| open60 half | +60% / +60% / +19% / -1% | +39% / +39% / +11% / +45% | -3.5 (+9.5) | n/n | noise / PASS | both frames + |
| openA40 half | +32% / +32% / +43% / +55% | +36% / +36% / +3% / +37% | -5.3 (+9.1) | n/n | noise / PASS | both frames + |
| rho40>=2 skip | -6% / -6% / +21% / +29% | +4% / +4% / -2% / -2% | -1.2 (+8.7) | n/n | noise / noise | - |
| rho40<=0.5 skip | -19% / -19% / +41% / -36% | -26% / -26% / +11% / -8% | -2.3 (+5.8) | n/n | noise / noise | - |
| rho60>=2 skip | +15% / +15% / +48% / +15% | +23% / +23% / +12% / +40% | +0.5 (+9.9) | n/n | noise / PASS | both frames + |
| rho60>=2 half | +1% / +1% / +29% / -7% | -5% / -5% / -10% / +12% | -1.8 (+5.1) | n/n | noise / noise | - |
| rho60<=0.5 half | +8% / +8% / +31% / +23% | -18% / -18% / -37% / -28% | -2.3 (+4.7) | n/n | noise / noise | - |
| mid_PDR half | -34% / -34% / +47% / +47% | -29% / -29% / -26% / +18% | -7.2 (+8.0) | n/n | noise / noise | - |
| mid_any3 half | -33% / -33% / +49% / +50% | -27% / -27% / -14% / +38% | -7.3 (+7.9) | n/n | noise / noise | - |
| mid_PDR&open40 up | +27% / +27% / +15% / -18% | -0% / -0% / -17% / -7% | +3.1 (+5.6) | n/n | noise / noise | LOCK-ONLY |
| mid_ON&nT40<=1 up | +12% / +12% / -21% / -2% | +10% / +10% / -32% / -5% | +2.8 (+5.1) | n/n | noise / noise | - |
| sA40>=1 skip | +31% / +31% / +23% / +27% | +34% / +34% / +18% / +14% | -1.1 (+12.2) | n/n | noise / noise | both frames + |
| sA40>=1 half | +0% / +0% / +4% / +33% | -0% / -0% / -17% / -13% | -3.1 (+7.1) | n/n | noise / noise | - |
| sA40>=2 half | -14% / -14% / +21% / +10% | -6% / -6% / +1% / -15% | -1.9 (+4.9) | n/n | noise / noise | - |
| sB40>=3 half | +2% / +2% / +25% / +37% | -3% / -3% / +10% / +7% | -0.4 (+2.2) | n/n | noise / noise | - |
| sA60>=1 half | +24% / +24% / +21% / +20% | +0% / +0% / +5% / +18% | -3.3 (+6.9) | n/n | noise / noise | LOCK-ONLY |
| sopen40 half | +60% / +44% / +14% / -4% | +39% / +39% / -2% / +22% | -3.6 (+9.3) | n/n | noise / noise | - |


Z3 noise-band rule (band computed on V13Z, recompute on V13Z pending) (band row by flagged share; flip 5.0 for masks >= 3.5% of rows): lock=12 passes: ['open20 half']; lock=None passes: ['open60 half', 'openA40 half', 'rho60>=2 skip'] (necessary, not sufficient; the passing cells fail the placebo and carrying-week standards above).

### 9h. lock=None frame for the cells that hold in both frames: cut-off sweep (sA40>=1 skip) and placebo ranks (share of draws with cut >= real; n per kind)

| factor | cuts L6M / HOLD / MID / PRE / X' / F9 (lock=None) |
|---|---|
| x1.0 | +34% / +34% / +31% / +18% / +14% / +34% |

| cell | real L6M / PRE / X' | B L6M / PRE / X' (n) | C L6M / PRE / X' | A L6M / PRE / X' | label |
|---|---|---|---|---|---|
| sA40>=1 skip | +34% / +18% / +14% | 0.31 / 0.06 / 0.27 (100) | 0.40 / 0.14 / 0.41 | 0.36 / 0.12 / 0.45 | (volume effect) |
| rho60>=2 skip | +23% / +12% / +40% | 0.37 / 0.17 / 0.06 (100) | 0.43 / 0.15 / 0.04 | 0.39 / 0.10 / 0.05 | (volume effect) |
| nA60>=1 skip | +32% / -8% / +19% | 0.40 / 0.42 / 0.31 (100) | 0.44 / 0.50 / 0.25 | 0.39 / 0.45 / 0.32 | (volume effect) |
| sA40>=1 half | -0% / -17% / -13% | n/a / n/a / n/a (0) | n/a / n/a / n/a | n/a / n/a / n/a | UNTESTED |
| nA60>=1 half | -1% / -3% / +20% | n/a / n/a / n/a (0) | n/a / n/a / n/a | n/a / n/a / n/a | UNTESTED |
| open20 half | +43% / +3% / +8% | 0.29 / 0.64 / 0.88 (100) | 0.33 / 0.70 / 0.90 | 0.34 / 0.72 / 0.86 | (volume effect) |
| openA40 half | +36% / +3% / +37% | 0.58 / 0.47 / 0.43 (100) | 0.38 / 0.49 / 0.46 | 0.45 / 0.58 / 0.42 | (volume effect) |
| sopen40 half | +39% / -2% / +22% | 0.19 / 0.23 / 0.47 (100) | 0.16 / 0.33 / 0.54 | 0.27 / 0.33 / 0.45 | (volume effect) |

### 9i. Priority cells in the lock=None frame (headline): episode-proofing, book x session, vol tercile, best-of-N null, causality audit

| cell (lock=None) | window | cut | carrying week | cut w/o it | LOWO range | LOMO range | bootstrap 90% CI / P(cut>0) | ONE-WEEK |
|---|---|---|---|---|---|---|---|---|
| sA40>=1 skip | L6M | +34% | 202630 | +39% | +24% .. +47% | -39% .. +45% | [-84%, +62%] / 0.67 | - |
| sA40>=1 skip | HOLD | +34% | 202630 | +31% | +24% .. +47% | +12% .. +44% | [-24%, +61%] / 0.85 | - |
| sA40>=1 skip | MID | +31% | 202613 | -2% | -23% .. +52% | -2% .. +53% | [-71%, +80%] / 0.65 | ONE-WEEK |
| sA40>=1 skip | PRE | +18% | 202506 | +1% | -4% .. +31% | +1% .. +39% | [-57%, +52%] / 0.79 | ONE-WEEK |
| sA40>=1 skip | X' | +14% | 202329 | -31% | -31% .. +37% | -31% .. +29% | [-61%, +23%] / 0.33 | ONE-WEEK |
| sA40>=1 skip | F9 | +34% | 202630 | +39% | +24% .. +47% | -39% .. +45% | [-56%, +67%] / 0.77 | - |
| nA60>=1 skip | L6M | +32% | 202630 | +36% | +21% .. +45% | -39% .. +41% | [-84%, +59%] / 0.67 | - |
| nA60>=1 skip | HOLD | +32% | 202630 | +26% | +21% .. +45% | +11% .. +41% | [-21%, +59%] / 0.86 | - |
| nA60>=1 skip | MID | +27% | 202613 | -8% | -19% .. +49% | -8% .. +42% | [-77%, +66%] / 0.65 | ONE-WEEK |
| nA60>=1 skip | PRE | -8% | 202506 | -30% | -30% .. +23% | -30% .. +35% | [-44%, +59%] / 0.82 | - |
| nA60>=1 skip | X' | +19% | 202329 | -23% | -23% .. +39% | -23% .. +36% | [-53%, +41%] / 0.56 | ONE-WEEK |
| nA60>=1 skip | F9 | +32% | 202630 | +36% | +21% .. +45% | -39% .. +41% | [-56%, +63%] / 0.77 | - |
| sA40>=1 half | L6M | -0% | 202630 | -4% | -9% .. +9% | -35% .. +15% | [-49%, +14%] / 0.17 | - |
| sA40>=1 half | HOLD | -0% | 202630 | -4% | -9% .. +9% | -27% .. +15% | [-41%, +51%] / 0.60 | - |
| sA40>=1 half | MID | +42% | 202613 | +15% | +15% .. +63% | +15% .. +63% | [+7%, +78%] / 0.96 | ONE-WEEK |
| sA40>=1 half | PRE | -17% | 202506 | -4% | -28% .. +8% | -17% .. +14% | [-37%, +32%] / 0.69 | - |
| sA40>=1 half | X' | -13% | 202329 | -32% | -38% .. +7% | -60% .. +5% | [-172%, +9%] / 0.16 | - |
| sA40>=1 half | F9 | -0% | 202630 | -4% | -9% .. +9% | -35% .. +15% | [-44%, +31%] / 0.45 | - |
| nA60>=1 half | L6M | -1% | 202630 | -5% | -8% .. +8% | -32% .. +13% | [-48%, +12%] / 0.15 | - |
| nA60>=1 half | HOLD | -1% | 202630 | -5% | -8% .. +8% | -28% .. +18% | [-39%, +47%] / 0.58 | - |
| nA60>=1 half | MID | +14% | 202613 | +15% | +3% .. +39% | +14% .. +15% | [+0%, +49%] / 0.96 | - |
| nA60>=1 half | PRE | -3% | 202506 | -7% | -14% .. +11% | -7% .. +13% | [-26%, +36%] / 0.78 | - |
| nA60>=1 half | X' | +20% | 202329 | -12% | -13% .. +37% | -20% .. +37% | [-114%, +27%] / 0.39 | ONE-WEEK |
| nA60>=1 half | F9 | -1% | 202630 | -5% | -8% .. +8% | -32% .. +13% | [-48%, +20%] / 0.32 | - |
| sopen40 half | L6M | +39% | 202630 | +47% | +26% .. +47% | +29% .. +39% | [+21%, +53%] / 0.98 | - |
| sopen40 half | HOLD | +39% | 202630 | +43% | +26% .. +46% | +31% .. +39% | [+20%, +49%] / 0.99 | - |
| sopen40 half | MID | +25% | 202613 | -10% | -10% .. +42% | -7% .. +25% | [-7%, +25%] / 0.75 | ONE-WEEK |
| sopen40 half | PRE | -2% | 202506 | +9% | -21% .. +16% | -17% .. +19% | [-36%, +26%] / 0.64 | - |
| sopen40 half | X' | +22% | 202329 | +4% | +4% .. +45% | -5% .. +28% | [-31%, +39%] / 0.72 | ONE-WEEK |
| sopen40 half | F9 | +39% | 202630 | +47% | +26% .. +47% | +27% .. +39% | [+7%, +41%] / 0.96 | - |
| open20 half | L6M | +43% | 202630 | +46% | +38% .. +49% | +22% .. +53% | [+18%, +63%] / 1.00 | - |
| open20 half | HOLD | +43% | 202630 | +46% | +38% .. +49% | +35% .. +45% | [+25%, +55%] / 1.00 | - |
| open20 half | MID | +29% | 202613 | +11% | +11% .. +37% | +11% .. +29% | [-0%, +30%] / 0.89 | ONE-WEEK |
| open20 half | PRE | +3% | 202506 | +10% | -14% .. +16% | -7% .. +16% | [-13%, +35%] / 0.88 | - |
| open20 half | X' | +8% | 202329 | -3% | -3% .. +36% | -8% .. +23% | [-9%, +48%] / 0.88 | - |
| open20 half | F9 | +43% | 202630 | +46% | +38% .. +49% | +22% .. +53% | [+18%, +59%] / 1.00 | - |
| openA40 half | L6M | +36% | 202630 | +38% | +28% .. +40% | +30% .. +36% | [+30%, +53%] / 1.00 | - |
| openA40 half | HOLD | +36% | 202630 | +38% | +28% .. +40% | +36% .. +39% | [+22%, +55%] / 0.99 | - |
| openA40 half | MID | +16% | 202613 | +14% | -4% .. +32% | +14% .. +16% | [+0%, +16%] / 0.95 | - |
| openA40 half | PRE | +3% | 202506 | +13% | -15% .. +17% | -6% .. +21% | [-23%, +34%] / 0.77 | - |
| openA40 half | X' | +37% | 202329 | +28% | +26% .. +53% | +26% .. +51% | [+7%, +58%] / 0.97 | - |
| openA40 half | F9 | +36% | 202630 | +38% | +28% .. +40% | +18% .. +36% | [+13%, +45%] / 1.00 | - |

Per book x session maxDD cut (lock=None, rule applied everywhere; L6M | HOLD | PRE | X'):

| cell | K6 | P6 | U6 | H6 | M6 | A6 | asia | london | nyam | nypm |
|---|---|---|---|---|---|---|---|---|---|---|
| sA40>=1 skip | +59%/+13%/-14%/+57% | +38%/+17%/+6%/+22% | +23%/+19%/+10%/-14% | +46%/-28%/+1%/+17% | +4%/+29%/+26%/-2% | -111%/-95%/+29%/-14% | +46%/+46%/+25%/+21% | -6%/+19%/+8%/+26% | +23%/-45%/-8%/+8% | +55%/+34%/+15%/-14% |
| nA60>=1 skip | +61%/+10%/+2%/+53% | +37%/+18%/-19%/+43% | +23%/+19%/+6%/-21% | +46%/-10%/+16%/+5% | +4%/+28%/+44%/-8% | -111%/-95%/+8%/+22% | +46%/+40%/-9%/+39% | -0%/+22%/+20%/+20% | +22%/-65%/-7%/+37% | +55%/+36%/+15%/+3% |
| sA40>=1 half | -18%/+14%/-55%/-21% | +9%/+9%/+18%/-22% | +18%/+16%/+0%/-6% | +17%/-8%/+4%/+11% | +15%/+38%/+19%/-26% | -13%/-5%/+14%/+25% | +4%/+4%/+21%/+15% | -19%/+16%/+9%/-12% | +45%/-46%/-19%/+1% | +3%/-6%/-22%/+9% |
| nA60>=1 half | -18%/+14%/-46%/+4% | +8%/+8%/+2%/+16% | +18%/+16%/+3%/-7% | +17%/+1%/+14%/+11% | +15%/+38%/+19%/-27% | -13%/-5%/-4%/+29% | +1%/+1%/+12%/+24% | -18%/+5%/+15%/+2% | +45%/-53%/-12%/+15% | +3%/-6%/-14%/+17% |
| sopen40 half | -5%/+15%/+16%/+15% | +51%/+50%/+9%/+24% | +19%/+14%/+26%/+3% | -10%/-10%/+24%/+11% | +32%/+49%/+25%/+41% | +55%/-12%/+30%/+35% | +48%/+15%/-5%/+14% | +39%/+57%/+15%/+3% | +24%/-3%/+40%/+49% | +48%/+50%/+6%/-6% |
| open20 half | -10%/+20%/+25%/+11% | +52%/+44%/+9%/+20% | +46%/+46%/+29%/+28% | +40%/+34%/+29%/+28% | +41%/+54%/+33%/+5% | +35%/+40%/+51%/+51% | +37%/+37%/+12%/+26% | +52%/+57%/+35%/+28% | +35%/+9%/+49%/+47% | +80%/+85%/-3%/+40% |
| openA40 half | -18%/+14%/+25%/-29% | +42%/+42%/+4%/+38% | +38%/+34%/+36%/+38% | +35%/+31%/+13%/+18% | +24%/+40%/+28%/+42% | +58%/+27%/+42%/+43% | +36%/+36%/-20%/+35% | +43%/+44%/+35%/+32% | +25%/-4%/+54%/+49% | +67%/+71%/+19%/-6% |

Vol tercile (day-range tercile; day-cumulative maxDD cut, mean d $k/day), lock=None: low | mid | high

* sA40>=1 skip: -3% (-0.2) | +13% (-0.3) | +25% (+0.1)
* nA60>=1 skip: +6% (-0.0) | +9% (-0.5) | +21% (-0.1)
* sA40>=1 half: +2% (-0.0) | -9% (-0.8) | +17% (-0.4)
* nA60>=1 half: +7% (+0.1) | -9% (-0.9) | +16% (-0.5)
* sopen40 half: +38% (+1.1) | +5% (+0.0) | +17% (-3.0)
* open20 half: +38% (+1.0) | +37% (-0.2) | +41% (-3.9)
* openA40 half: +43% (+1.2) | +25% (-0.2) | +35% (-3.7)

Best-of-N null: pooled 2100 lock=None information-free masks (random rows / same-volume / shuffled-day of the 3-4 priority cells, same flag shares ~28-36%); best L6M cut among N=314 draws from that pool (2000 repeats): median +75%, 95th percentile +83%. Best real L6M cut among the 34 finalists in lock=None: +43%; sA40>=1 skip +34%, nA60>=1 skip +32%.

Causality audit (audit.py): 100 random signals x 8 lines (800 line-checks): the ahead and behind fresh distance recomputed by brute force from the stream rows with knowable-index ek <= signal second, alive (cap > kin) and never touched (end > kin) equals the stored feature in 800 of 800 checks (0 mismatches); the stream knowable index ek is the POI store's causal timestamp (poi_core), not re-derived here.
## 10. HEADLINE BASE V13T (= V13Z with the five take lines OFF, lock none = live per-book stack; lock-12 columns are REFERENCE (not live); exact U7 same-side, exact 5 THP take/tighten lines, exact lots, 12R per-book + give-back, ER running-max)

V13T base: L6M mean 29.2k/wk, maxDD 150k; HOLD mean 24.5k/wk, maxDD 150k; MID mean 19.0k/wk, maxDD 44k; PRE mean 8.9k/wk, maxDD 132k; X' mean -4.6k/wk, maxDD 234k; F9 mean 26.8k/wk, maxDD 150k. Base maxDD-carrying week (L6M / F9 / PRE / X'): 202631 / 202631 / 202440 / 202342.

### 10a. All 34 finalists on V13T (screen; placebo status in 7c)

| cell (V13X) | flag % | maxDD cut L3M / L6M / HOLD / MID / PRE / X' / F9 | mean d $k/wk L6M (MDE) / PRE (MDE) | S/T/N | TOL-B / nc | ONE-WEEK L6M/F9 | week carrying (L6M) | band (flip row) L6M / PRE / X' | band rule |
|---|---|---|---|---|---|---|---|---|---|
| nA40>=1 skip | 25 | +46% / +22% / +22% / +26% / +18% / +10% / +22% | -6.2 (+9.4) / +4.7 (+10.9) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA40>=1 half | 25 | +13% / +7% / +7% / +28% / -9% / +3% / +7% | -0.8 (+5.4) / -3.9 (+7.7) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=1 skip | 21 | -16% / -6% / -6% / -47% / +41% / +57% / -6% | -2.2 (+7.2) / +0.2 (+9.3) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=1 half | 21 | -13% / -5% / -5% / -7% / -16% / +31% / -5% | -1.3 (+3.1) / -0.6 (+5.8) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=2 skip | 10 | +12% / +2% / +2% / -20% / +20% / +33% / +2% | +1.9 (+3.6) / +1.7 (+6.0) | n/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=2 half | 10 | +9% / +1% / +1% / -60% / -16% / +47% / +1% | +0.5 (+1.6) / +1.5 (+4.1) | n/n/Y | n / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=3 skip | 6 | -15% / -7% / -7% / +0% / +18% / +25% / -7% | -0.2 (+1.9) / +2.2 (+4.5) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=3 half | 6 | -13% / -6% / -6% / -0% / +22% / +41% / -6% | -0.3 (+1.0) / +0.9 (+2.9) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nT40>=2 half | 20 | -1% / -3% / -3% / +1% / +1% / +48% / -3% | -1.0 (+2.7) / -1.7 (+6.8) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nT40>=4 half | 5 | -6% / -2% / -2% / +0% / +18% / +53% / -2% | -0.3 (+0.6) / +0.3 (+2.8) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA60>=1 skip | 32 | +63% / +44% / +13% / -45% / -16% / -16% / +44% | -3.7 (+13.4) / +0.9 (+11.0) | n/n/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA60>=1 half | 32 | +25% / +16% / +16% / +21% / +5% / +32% / +16% | -4.0 (+11.2) / -3.6 (+8.1) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA60>=2 half | 14 | -1% / -3% / -3% / +1% / -13% / +7% / -3% | -1.0 (+3.2) / -2.7 (+6.3) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nT60>=3 skip | 22 | -34% / -27% / -27% / -0% / +10% / +55% / -27% | -7.7 (+15.1) / -0.1 (+10.7) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nTany40>=2 half | 47 | -13% / +5% / +5% / +28% / -0% / +33% / +5% | -4.9 (+10.1) / -0.3 (+5.5) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| open20 half | 81 | +33% / +45% / +45% / +51% / +15% / +13% / +45% | -15.7 (+18.3) / -4.0 (+8.1) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| open60 half | 47 | -33% / +18% / +18% / -3% / -14% / -0% / +18% | -17.7 (+20.2) / -0.7 (+7.8) | n/n/n | n / n | Y/Y | 202631 | flip 5: 36/28/29% | NOISE |
| openA40 half | 75 | +2% / +23% / +23% / -16% / +7% / +56% / +23% | -17.4 (+19.4) / -4.3 (+7.5) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho40>=2 skip | 18 | +64% / +29% / +29% / +61% / +2% / +13% / +29% | -4.8 (+9.6) / +3.2 (+8.2) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho40<=0.5 skip | 15 | -6% / -5% / -5% / -72% / +32% / +64% / -5% | -0.7 (+5.1) / +1.5 (+6.5) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho60>=2 skip | 20 | +39% / +45% / +45% / +1% / +7% / -22% / +45% | -1.3 (+9.3) / +3.6 (+9.5) | n/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho60>=2 half | 20 | +25% / +16% / +16% / +3% / +30% / +16% / +16% | -3.9 (+10.5) / +1.4 (+4.2) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho60<=0.5 half | 24 | +2% / -2% / -2% / +55% / -72% / +16% / -2% | -2.7 (+3.2) / -1.4 (+4.4) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| mid_PDR half | 22 | -8% / +7% / +7% / -5% / +18% / +41% / +7% | -5.0 (+7.2) / -0.8 (+5.9) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| mid_any3 half | 41 | -37% / -6% / -6% / -63% / +28% / +54% / -6% | -8.6 (+10.7) / +0.5 (+5.9) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| mid_PDR&open40 up | 10 | +9% / +10% / +10% / -50% / -105% / -5% / +10% | +5.0 (+6.1) / -1.9 (+3.8) | n/n/Y | n / n | Y/Y | 202631 | flip 5: 36/28/29% | NOISE |
| mid_ON&nT40<=1 up | 10 | +15% / +4% / +4% / +2% / +3% / -4% / +4% | -5.8 (+12.7) / -1.1 (+3.9) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA40>=1 skip | 28 | +63% / +64% / +21% / -45% / +27% / +4% / +58% | -2.9 (+14.5) / +4.0 (+11.2) | n/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA40>=1 half | 28 | +25% / +28% / +28% / +21% / -4% / +6% / +28% | -3.1 (+11.6) / -4.5 (+7.8) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA40>=2 half | 11 | -3% / -4% / -4% / +1% / +6% / +17% / -4% | -0.7 (+3.2) / -0.2 (+4.3) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sB40>=3 half | 7 | -15% / -6% / -6% / +0% / +11% / +52% / -6% | -0.3 (+1.9) / +1.3 (+3.6) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA60>=1 half | 36 | -9% / +37% / +37% / +18% / +9% / +16% / +37% | -5.0 (+13.6) / -3.4 (+8.1) | n/n/n | n / n | Y/Y | 202631 | flip 5: 36/28/29% | NOISE |
| sopen40 half | 55 | -49% / +1% / +1% / +1% / -14% / +15% / +1% | -18.6 (+19.9) / -2.9 (+8.1) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |

Band rule (Z3 V13X band, lock 12R, DS3_ZONES_3_NOISE.md; the earlier assumed-base band is superseded): 0 of 33 pass; TOLERANT 8, STRICT 5.

### 10b. Scaled cut-off sweep on V13T (sA40>=1 skip)

| factor | cuts L6M / HOLD / MID / PRE / X' / F9 | mean d F9 (MDE) |
|---|---|---|
| x1.0 | +64% / +21% / -45% / +27% / +4% / +58% | -1.9 (+12.1) |

### 10c. V13X placebo ranks (share of draws with cut >= real; n draws), L6M and PRE

| cell | real L6M / PRE | B L6M (n) | C L6M | A L6M | B PRE | C PRE | A PRE | label |
|---|---|---|---|---|---|---|---|---|

### 10d. Per-scope reruns on V13T (rule applied only to the book / session; cut on the TOTAL composite)

| cell | scope | cut L6M | cut F9 | cut PRE | cut X' | mean d F9 (MDE) |
|---|---|---|---|---|---|---|

### 10e. Re-target decision delay on V13T (sA40>=1; rtc = same market entry with the original target)

| action | delay | cuts L6M / F9 / PRE / X' | mean d F9 (MDE) |
|---|---|---|---|

### 10f. Vol-tercile cuts on V13T (day-range tercile over all days; day-cumulative maxDD cut, mean d $k/day)

| cell | low vol | mid | high |
|---|---|---|---|
| sA40>=1 skip | -19% (-0.7) | +24% (-0.2) | -24% (+1.6) |
| sA40>=1 half | +17% (+0.4) | +25% (-1.0) | +2% (-1.2) |
| sA60>=1 half | +23% (+0.5) | +15% (-1.3) | +8% (-0.9) |
| rho60>=2 skip | -5% (-0.3) | +39% (+0.0) | +8% (+0.8) |
| rho60>=2 half | +14% (+0.2) | +29% (-0.4) | +9% (-0.1) |
| nA60>=1 half | +16% (+0.3) | +24% (-1.2) | +8% (-0.9) |
| open20 half | +36% (+0.7) | +39% (-0.9) | +49% (-3.0) |

### 10g. MASTER TABLE finalist x frame: V13T lock=12 (reference, not live) (shipped combined lock) vs lock=None (engine per-book locks only); HEADLINE frame = lock=None until the user confirms; LOCK-ONLY = lock=12 L6M cut >= 10% but lock=None L6M cut < 5%

lock=None base: L6M mean 37.1k, maxDD 132k; F9 mean 33.7k, maxDD 132k; PRE mean 17.1k, maxDD 166k; X' mean 4.7k, maxDD 91k

| cell | lock=12 cuts L6M / F9 / PRE / X' | lock=None cuts L6M / F9 / PRE / X' | mean d F9 lock=None (MDE) | ONE-WEEK (lock=None L6M/F9) | Z3 band pass (V13X-based) lock=12 / lock=None | label |
|---|---|---|---|---|---|---|
| nA40>=1 skip | +22% / +22% / +18% / +10% | -15% / -15% / +3% / -72% | -5.1 (+11.3) | n/n | noise / noise | LOCK-ONLY |
| nA40>=1 half | +7% / +7% / -9% / +3% | -40% / -40% / +2% / -32% | -3.2 (+6.0) | n/n | noise / noise | - |
| nB40>=1 skip | -6% / -6% / +41% / +57% | -67% / -67% / +30% / -27% | -9.1 (+8.3) | n/n | noise / noise | - |
| nB40>=1 half | -5% / -5% / -16% / +31% | -32% / -32% / +14% / +20% | -4.6 (+4.3) | n/n | noise / noise | - |
| nB40>=2 skip | +2% / +2% / +20% / +33% | -9% / -9% / +19% / -33% | -0.9 (+5.0) | n/n | noise / noise | - |
| nB40>=2 half | +1% / +1% / -16% / +47% | -1% / -1% / +10% / +10% | -1.2 (+2.8) | n/n | noise / noise | - |
| nB40>=3 skip | -7% / -7% / +18% / +25% | -15% / -15% / -2% / -32% | -0.7 (+2.1) | n/n | noise / noise | - |
| nB40>=3 half | -6% / -6% / +22% / +41% | -9% / -9% / +2% / +7% | -1.1 (+1.5) | n/n | noise / noise | - |
| nT40>=2 half | -3% / -3% / +1% / +48% | -45% / -45% / +15% / +0% | -3.3 (+4.5) | n/n | noise / noise | - |
| nT40>=4 half | -2% / -2% / +18% / +53% | -9% / -9% / +4% / -11% | -0.6 (+0.8) | n/n | noise / noise | - |
| nA60>=1 skip | +44% / +44% / -16% / -16% | +33% / +33% / +7% / -52% | -5.0 (+14.1) | Y/Y | noise / noise | ONE-WEEK |
| nA60>=1 half | +16% / +16% / +5% / +32% | -1% / -1% / +4% / -31% | -3.5 (+6.9) | n/n | noise / noise | LOCK-ONLY |
| nA60>=2 half | -3% / -3% / -13% / +7% | -40% / -40% / +9% / +3% | -2.8 (+4.2) | n/n | noise / noise | - |
| nT60>=3 skip | -27% / -27% / +10% / +55% | -50% / -50% / +23% / -26% | -5.4 (+8.0) | n/n | noise / noise | - |
| nTany40>=2 half | +5% / +5% / -0% / +33% | -42% / -42% / +22% / +24% | -6.8 (+9.1) | n/n | noise / noise | - |
| open20 half | +45% / +45% / +15% / +13% | +56% / +56% / +41% / +15% | -15.8 (+15.4) | n/n | noise / PASS | both frames + |
| open60 half | +18% / +18% / -14% / -0% | +18% / +18% / +16% / +6% | -12.8 (+13.8) | Y/Y | noise / noise | ONE-WEEK |
| openA40 half | +23% / +23% / +7% / +56% | +18% / +18% / +36% / +41% | -16.6 (+13.5) | n/n | noise / noise | both frames + |
| rho40>=2 skip | +29% / +29% / +2% / +13% | -0% / -0% / +1% / -35% | -3.0 (+10.7) | n/n | noise / noise | LOCK-ONLY |
| rho40<=0.5 skip | -5% / -5% / +32% / +64% | -27% / -27% / +17% / -6% | -5.4 (+7.3) | n/n | noise / noise | - |
| rho60>=2 skip | +45% / +45% / +7% / -22% | +31% / +31% / -11% / +8% | -3.7 (+10.9) | Y/Y | noise / noise | ONE-WEEK |
| rho60>=2 half | +16% / +16% / +30% / +16% | -6% / -6% / -0% / -3% | -3.0 (+5.7) | n/n | noise / noise | LOCK-ONLY |
| rho60<=0.5 half | -2% / -2% / -72% / +16% | -23% / -23% / +13% / +16% | -4.2 (+5.5) | n/n | noise / noise | - |
| mid_PDR half | +7% / +7% / +18% / +41% | -42% / -42% / +30% / +18% | -6.9 (+6.8) | n/n | noise / noise | - |
| mid_any3 half | -6% / -6% / +28% / +54% | -52% / -52% / +22% / +35% | -9.6 (+9.2) | n/n | noise / noise | - |
| mid_PDR&open40 up | +10% / +10% / -105% / -5% | +33% / +33% / -10% / -29% | +4.6 (+7.1) | Y/Y | noise / noise | ONE-WEEK |
| mid_ON&nT40<=1 up | +4% / +4% / +3% / -4% | +16% / +16% / -2% / -8% | +1.0 (+4.5) | Y/Y | noise / noise | ONE-WEEK |
| sA40>=1 skip | +64% / +58% / +27% / +4% | +33% / +33% / +12% / -52% | -4.8 (+14.5) | Y/Y | noise / noise | ONE-WEEK |
| sA40>=1 half | +28% / +28% / -4% / +6% | +18% / +18% / +10% / -19% | -2.5 (+7.5) | n/n | noise / noise | both frames + |
| sA40>=2 half | -4% / -4% / +6% / +17% | -40% / -40% / +5% / -0% | -2.3 (+4.0) | n/n | noise / noise | - |
| sB40>=3 half | -6% / -6% / +11% / +52% | +4% / +4% / +6% / +9% | -0.1 (+2.5) | n/n | noise / noise | both frames + |
| sA60>=1 half | +37% / +37% / +9% / +16% | +13% / +13% / -0% / -35% | -5.0 (+8.1) | n/n | noise / noise | - |
| sopen40 half | +1% / +1% / -14% / +15% | +16% / +16% / +47% / -1% | -13.2 (+13.3) | Y/Y | noise / noise | ONE-WEEK |


Z3 noise-band rule (band computed on V13T, recompute on V13T pending) (band row by flagged share; flip 5.0 for masks >= 3.5% of rows): lock=12 passes: none; lock=None passes: ['open20 half'] (necessary, not sufficient; the passing cells fail the placebo and carrying-week standards above).

### 10h. lock=None frame for the cells that hold in both frames: cut-off sweep (sA40>=1 skip) and placebo ranks (share of draws with cut >= real; n per kind)

| factor | cuts L6M / HOLD / MID / PRE / X' / F9 (lock=None) |
|---|---|
| x1.0 | +33% / +36% / +25% / +12% / -52% / +33% |

| cell | real L6M / PRE / X' | B L6M / PRE / X' (n) | C L6M / PRE / X' | A L6M / PRE / X' | label |
|---|---|---|---|---|---|
| sA40>=1 skip | +33% / +12% / -52% | 0.19 / 0.42 / 0.88 (100) | 0.26 / 0.36 / 0.95 | 0.20 / 0.46 / 0.98 | (volume effect) |
| rho60>=2 skip | +31% / -11% / +8% | 0.21 / 0.90 / 0.40 (100) | 0.17 / 0.85 / 0.45 | 0.14 / 0.87 / 0.36 | (volume effect) |
| nA60>=1 skip | +33% / +7% / -52% | 0.18 / 0.51 / 0.90 (100) | 0.29 / 0.46 / 0.94 | 0.29 / 0.59 / 0.88 | (volume effect) |
| sA40>=1 half | +18% / +10% / -19% | n/a / n/a / n/a (0) | n/a / n/a / n/a | n/a / n/a / n/a | UNTESTED |
| nA60>=1 half | -1% / +4% / -31% | n/a / n/a / n/a (0) | n/a / n/a / n/a | n/a / n/a / n/a | UNTESTED |
| open20 half | +56% / +41% / +15% | 0.06 / 0.49 / 0.75 (100) | 0.05 / 0.53 / 0.80 | 0.05 / 0.43 / 0.80 | placebos beaten on L6M |
| openA40 half | +18% / +36% / +41% | 0.67 / 0.52 / 0.21 (100) | 0.63 / 0.60 / 0.20 | 0.57 / 0.47 / 0.12 | (volume effect) |
| sopen40 half | +16% / +47% / -1% | 0.53 / 0.00 / 0.77 (100) | 0.46 / 0.01 / 0.73 | 0.49 / 0.02 / 0.87 | (volume effect) |

### 10i. Priority cells in the lock=None frame (headline): episode-proofing, book x session, vol tercile, best-of-N null, causality audit

| cell (lock=None) | window | cut | carrying week | cut w/o it | LOWO range | LOMO range | bootstrap 90% CI / P(cut>0) | ONE-WEEK |
|---|---|---|---|---|---|---|---|---|
| sA40>=1 skip | L6M | +33% | 202630 | +9% | +9% .. +40% | +9% .. +40% | [-33%, +47%] / 0.87 | ONE-WEEK |
| sA40>=1 skip | HOLD | +36% | 202606 | +33% | +33% .. +53% | +29% .. +43% | [-24%, +58%] / 0.83 | - |
| sA40>=1 skip | MID | +25% | 202607 | -64% | -64% .. +33% | -64% .. +39% | [-64%, +58%] / 0.51 | ONE-WEEK |
| sA40>=1 skip | PRE | +12% | 202436 | +29% | -14% .. +29% | +6% .. +29% | [-59%, +51%] / 0.67 | - |
| sA40>=1 skip | X' | -52% | 202346 | -61% | -78% .. -22% | -78% .. +7% | [-91%, +23%] / 0.15 | - |
| sA40>=1 skip | F9 | +33% | 202630 | +9% | +9% .. +40% | +9% .. +40% | [-54%, +46%] / 0.76 | ONE-WEEK |
| nA60>=1 skip | L6M | +33% | 202630 | +10% | +10% .. +40% | +10% .. +40% | [-31%, +47%] / 0.87 | ONE-WEEK |
| nA60>=1 skip | HOLD | +36% | 202606 | +33% | +33% .. +54% | +27% .. +43% | [-20%, +58%] / 0.83 | - |
| nA60>=1 skip | MID | +22% | 202607 | -71% | -71% .. +39% | -71% .. +39% | [-71%, +58%] / 0.51 | ONE-WEEK |
| nA60>=1 skip | PRE | +7% | 202436 | +41% | -22% .. +41% | +7% .. +26% | [-39%, +62%] / 0.78 | - |
| nA60>=1 skip | X' | -52% | 202346 | -80% | -80% .. -7% | -72% .. +10% | [-145%, +31%] / 0.32 | - |
| nA60>=1 skip | F9 | +33% | 202630 | +10% | +10% .. +40% | +10% .. +40% | [-54%, +45%] / 0.77 | ONE-WEEK |
| sA40>=1 half | L6M | +18% | 202630 | +26% | -6% .. +26% | +16% .. +26% | [-27%, +39%] / 0.86 | - |
| sA40>=1 half | HOLD | +22% | 202606 | +18% | +16% .. +48% | +18% .. +48% | [-4%, +61%] / 0.93 | - |
| sA40>=1 half | MID | +24% | 202607 | +22% | -3% .. +24% | +22% .. +24% | [+22%, +45%] / 0.96 | - |
| sA40>=1 half | PRE | +10% | 202436 | +30% | +1% .. +30% | +10% .. +30% | [-17%, +40%] / 0.81 | - |
| sA40>=1 half | X' | -19% | 202346 | -12% | -28% .. -4% | -47% .. +5% | [-64%, +12%] / 0.18 | - |
| sA40>=1 half | F9 | +18% | 202630 | +26% | -6% .. +26% | +16% .. +26% | [-19%, +34%] / 0.87 | - |
| nA60>=1 half | L6M | -1% | 202630 | +7% | -12% .. +13% | -6% .. +26% | [-27%, +27%] / 0.74 | - |
| nA60>=1 half | HOLD | +5% | 202606 | -1% | -2% .. +39% | -1% .. +48% | [-12%, +56%] / 0.88 | - |
| nA60>=1 half | MID | +24% | 202607 | +1% | -3% .. +24% | +1% .. +24% | [+1%, +24%] / 0.96 | ONE-WEEK |
| nA60>=1 half | PRE | +4% | 202436 | +43% | -9% .. +43% | +4% .. +43% | [-13%, +43%] / 0.84 | - |
| nA60>=1 half | X' | -31% | 202346 | -38% | -43% .. -4% | -48% .. +8% | [-86%, +14%] / 0.20 | - |
| nA60>=1 half | F9 | -1% | 202630 | +7% | -12% .. +13% | -6% .. +26% | [-20%, +27%] / 0.77 | - |
| sopen40 half | L6M | +16% | 202630 | +1% | -5% .. +36% | +1% .. +48% | [-65%, +60%] / 0.79 | ONE-WEEK |
| sopen40 half | HOLD | -2% | 202606 | +16% | -9% .. +16% | -4% .. +16% | [-43%, +48%] / 0.41 | - |
| sopen40 half | MID | -8% | 202607 | -48% | -48% .. +30% | -12% .. -8% | [-50%, -8%] / 0.04 | - |
| sopen40 half | PRE | +47% | 202436 | +33% | +33% .. +51% | +18% .. +51% | [-9%, +50%] / 0.89 | - |
| sopen40 half | X' | -1% | 202346 | -39% | -39% .. +40% | -39% .. +40% | [-39%, +47%] / 0.68 | - |
| sopen40 half | F9 | +16% | 202630 | +1% | -5% .. +36% | +1% .. +43% | [-62%, +48%] / 0.63 | ONE-WEEK |
| open20 half | L6M | +56% | 202630 | +54% | +50% .. +61% | +48% .. +57% | [+26%, +67%] / 1.00 | - |
| open20 half | HOLD | +38% | 202606 | +56% | +38% .. +56% | +25% .. +56% | [+16%, +57%] / 0.99 | - |
| open20 half | MID | +16% | 202607 | +0% | +0% .. +48% | +16% .. +40% | [-2%, +40%] / 0.84 | ONE-WEEK |
| open20 half | PRE | +41% | 202436 | +37% | +37% .. +43% | +37% .. +43% | [+24%, +46%] / 0.99 | - |
| open20 half | X' | +15% | 202346 | -17% | -17% .. +53% | -17% .. +53% | [-17%, +52%] / 0.82 | ONE-WEEK |
| open20 half | F9 | +56% | 202630 | +54% | +50% .. +61% | +48% .. +56% | [+16%, +63%] / 0.99 | - |
| openA40 half | L6M | +18% | 202630 | +16% | +10% .. +27% | +18% .. +45% | [+16%, +51%] / 1.00 | - |
| openA40 half | HOLD | +11% | 202606 | +18% | +5% .. +21% | +11% .. +18% | [-11%, +42%] / 0.89 | - |
| openA40 half | MID | -0% | 202607 | -61% | -61% .. -0% | -61% .. -0% | [-96%, -0%] / 0.04 | - |
| openA40 half | PRE | +36% | 202436 | +18% | +18% .. +56% | +11% .. +56% | [-4%, +56%] / 0.94 | - |
| openA40 half | X' | +41% | 202346 | +18% | +18% .. +60% | +18% .. +60% | [+5%, +67%] / 0.96 | ONE-WEEK |
| openA40 half | F9 | +18% | 202630 | +16% | +10% .. +27% | +18% .. +45% | [-19%, +44%] / 0.85 | - |

Per book x session maxDD cut (lock=None, rule applied everywhere; L6M | HOLD | PRE | X'):

| cell | K6 | P6 | U6 | H6 | M6 | A6 | asia | london | nyam | nypm |
|---|---|---|---|---|---|---|---|---|---|---|
| sA40>=1 skip | +76%/+29%/-38%/+62% | +42%/+11%/-1%/+1% | +48%/+35%/+4%/+12% | +4%/+4%/+41%/-34% | +16%/+14%/+25%/-2% | -111%/-95%/+29%/-14% | +1%/+3%/+13%/+16% | +39%/-30%/+6%/+9% | +8%/-23%/-17%/-32% | +42%/+38%/+8%/+39% |
| nA60>=1 skip | +76%/+17%/-18%/+59% | +42%/-4%/-32%/+4% | +48%/+34%/+10%/-30% | -2%/-2%/+38%/-59% | +16%/+12%/+42%/+13% | -111%/-95%/+8%/+22% | -6%/-4%/-1%/+23% | +39%/-25%/+13%/+17% | +4%/-89%/-19%/-12% | +42%/+32%/+17%/+42% |
| sA40>=1 half | +7%/+7%/-37%/-24% | +50%/+39%/-5%/-9% | +42%/+42%/+5%/+20% | -38%/-38%/+18%/-1% | +11%/+19%/+15%/-19% | -13%/-5%/+14%/+25% | +2%/+4%/-4%/+13% | +26%/+1%/+6%/+4% | -61%/-20%/-11%/-6% | +18%/+1%/-19%/+14% |
| nA60>=1 half | +7%/+7%/-7%/-9% | +26%/+25%/-20%/-10% | +42%/+42%/+7%/+2% | -41%/-41%/+28%/-6% | +11%/+22%/+14%/-22% | -13%/-5%/-4%/+29% | -2%/-0%/+26%/+16% | -1%/+3%/+9%/+6% | -61%/-38%/-13%/-2% | +18%/-2%/+3%/+16% |
| sopen40 half | +16%/+16%/+29%/+22% | +38%/+12%/+41%/+24% | +23%/+23%/+13%/-5% | -12%/-12%/+49%/+27% | +44%/+48%/+30%/+47% | +55%/-12%/+30%/+35% | +36%/-47%/+35%/+15% | +18%/+27%/+14%/+32% | -72%/+36%/+55%/+41% | +4%/+13%/+27%/+60% |
| open20 half | +23%/+23%/+39%/+8% | +72%/+40%/+43%/+29% | +55%/+55%/+30%/+14% | +60%/+60%/+45%/+42% | +26%/+33%/+35%/+29% | +35%/+40%/+51%/+51% | +50%/+51%/+33%/+31% | +41%/+46%/+40%/+32% | +31%/+29%/+46%/+56% | +68%/+70%/+51%/+56% |
| openA40 half | +4%/+4%/+26%/+8% | +37%/+22%/+36%/+59% | +48%/+45%/+44%/+12% | +11%/+11%/+26%/+37% | +15%/+21%/+36%/+60% | +58%/+27%/+42%/+43% | +29%/+30%/+28%/+43% | +27%/+17%/+41%/+39% | -63%/+20%/+50%/+46% | +31%/+34%/+37%/+50% |

Vol tercile (day-range tercile; day-cumulative maxDD cut, mean d $k/day), lock=None: low | mid | high

* sA40>=1 skip: -0% (-0.1) | +24% (-1.8) | +15% (+0.3)
* nA60>=1 skip: +8% (+0.2) | +24% (-2.3) | +16% (+0.1)
* sA40>=1 half: +6% (+0.2) | -2% (-1.5) | +38% (-0.3)
* nA60>=1 half: +9% (+0.4) | +6% (-1.8) | +32% (-0.4)
* sopen40 half: +33% (+1.4) | +18% (-0.9) | -5% (-4.2)
* open20 half: +43% (+1.7) | +44% (-1.7) | +38% (-5.5)
* openA40 half: +47% (+1.8) | +34% (-1.5) | +8% (-5.4)

Best-of-N null: pooled 2100 lock=None information-free masks (random rows / same-volume / shuffled-day of the 3-4 priority cells, same flag shares ~28-36%); best L6M cut among N=314 draws from that pool (2000 repeats): median +68%, 95th percentile +74%. Best real L6M cut among the 34 finalists in lock=None: +56%; sA40>=1 skip +33%, nA60>=1 skip +33%.

Causality audit (audit.py): 100 random signals x 8 lines (800 line-checks): the ahead and behind fresh distance recomputed by brute force from the stream rows with knowable-index ek <= signal second, alive (cap > kin) and never touched (end > kin) equals the stored feature in 800 of 800 checks (0 mismatches); the stream knowable index ek is the POI store's causal timestamp (poi_core), not re-derived here.
## 9. BASE V13Z (= V13Y + nfix: basis-N take deltas; exact U7 same-side, exact 5 THP take/tighten lines, exact lots, 12R per-book + give-back, ER running-max)

V13Z base: L6M mean 12.7k/wk, maxDD 117k; HOLD mean 10.2k/wk, maxDD 122k; MID mean 0.8k/wk, maxDD 70k; PRE mean 3.0k/wk, maxDD 363k; X' mean -2.5k/wk, maxDD 139k; F9 mean 9.3k/wk, maxDD 117k. Base maxDD-carrying week (L6M / F9 / PRE / X'): 202631 / 202631 / 202447 / 202314.

### 9a. All 34 finalists on V13Z (screen; placebo status in 7c)

| cell (V13X) | flag % | maxDD cut L3M / L6M / HOLD / MID / PRE / X' / F9 | mean d $k/wk L6M (MDE) / PRE (MDE) | S/T/N | TOL-B / nc | ONE-WEEK L6M/F9 | week carrying (L6M) | band (flip row) L6M / PRE / X' | band rule |
|---|---|---|---|---|---|---|---|---|---|
| nA40>=1 skip | 25 | -17% / -11% / -7% / +51% / +26% / +34% / -11% | -1.9 (+11.6) / +1.4 (+8.6) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA40>=1 half | 25 | -23% / -5% / -0% / +44% / +8% / +26% / -5% | -0.7 (+10.8) / -2.5 (+7.0) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=1 skip | 21 | -26% / -16% / -11% / +9% / +35% / +0% / -16% | +3.5 (+7.5) / -0.3 (+5.8) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=1 half | 21 | -44% / -28% / -22% / +21% / +47% / +52% / -28% | -2.8 (+6.1) / +0.9 (+5.8) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=2 skip | 10 | -28% / -14% / -9% / -12% / +40% / -20% / -14% | +0.7 (+3.6) / +3.2 (+6.3) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=2 half | 10 | +9% / -9% / -5% / +0% / +35% / +47% / -9% | -1.5 (+6.6) / +2.1 (+5.7) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=3 skip | 6 | -10% / -4% / -0% / -6% / +25% / -8% / -4% | -0.2 (+1.8) / +2.5 (+6.0) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=3 half | 6 | -6% / -3% / +2% / +2% / +10% / +45% / -3% | +0.1 (+1.2) / +2.1 (+3.0) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nT40>=2 half | 20 | -30% / -36% / -30% / +1% / +41% / +53% / -36% | -3.3 (+8.4) / -1.0 (+7.5) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nT40>=4 half | 5 | -36% / -25% / -20% / -6% / +1% / +32% / -25% | -3.1 (+6.1) / +0.1 (+3.5) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA60>=1 skip | 32 | +20% / +14% / +18% / +23% / +51% / +27% / +14% | +0.2 (+13.5) / +1.9 (+10.1) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA60>=1 half | 32 | -12% / +0% / +4% / +35% / +19% / +24% / +0% | -0.7 (+10.9) / -2.2 (+7.2) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA60>=2 half | 14 | -28% / -14% / -9% / +15% / +4% / +17% / -14% | -2.7 (+6.1) / -2.2 (+6.4) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nT60>=3 skip | 22 | -54% / -34% / -28% / -3% / +20% / -15% / -34% | +2.0 (+13.1) / -1.2 (+8.5) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nTany40>=2 half | 47 | -50% / -17% / -12% / +37% / +42% / +52% / -17% | +0.5 (+9.9) / +0.4 (+7.9) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| open20 half | 81 | +39% / +47% / +44% / +35% / +50% / +14% / +47% | -4.5 (+11.5) / -2.5 (+5.8) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | PASS |
| open60 half | 47 | +38% / +60% / +43% / +33% / +19% / -1% / +60% | -2.2 (+11.5) / -3.6 (+5.3) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| openA40 half | 75 | +21% / +32% / +35% / +32% / +43% / +55% / +32% | -5.4 (+13.5) / -2.3 (+5.9) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho40>=2 skip | 18 | -4% / -6% / -1% / +57% / +21% / +29% / -6% | -2.0 (+11.1) / +1.0 (+8.0) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho40<=0.5 skip | 15 | -23% / -19% / -14% / -1% / +41% / -36% / -19% | +0.4 (+4.0) / +0.1 (+6.1) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho60>=2 skip | 20 | +14% / +15% / +18% / +48% / +48% / +15% / +15% | +3.6 (+11.8) / +2.6 (+8.4) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho60>=2 half | 20 | -25% / +1% / +5% / +36% / +29% / -7% / +1% | +2.0 (+9.1) / -1.2 (+7.0) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho60<=0.5 half | 24 | +7% / +8% / +12% / +13% / +31% / +23% / +8% | +2.0 (+7.3) / +0.4 (+6.2) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| mid_PDR half | 22 | -56% / -34% / -28% / -9% / +47% / +47% / -34% | -3.6 (+13.0) / +2.3 (+5.2) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| mid_any3 half | 41 | -80% / -33% / -28% / -1% / +49% / +50% / -33% | -4.3 (+11.6) / +1.7 (+5.3) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| mid_PDR&open40 up | 10 | +21% / +27% / +1% / +16% / +15% / -18% / +27% | +4.9 (+5.7) / -2.3 (+7.0) | n/n/Y | n / n | Y/Y | 202631 | flip 5: 36/28/29% | NOISE |
| mid_ON&nT40<=1 up | 10 | +24% / +12% / +15% / -2% / -21% / -2% / +12% | +1.4 (+3.3) / -2.4 (+4.8) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA40>=1 skip | 28 | +20% / +31% / +25% / +23% / +23% / +27% / +31% | +0.8 (+14.0) / +0.8 (+9.5) | Y/Y/Y | Y / Y | Y/Y | 202631 | flip 5: 36/28/29% | NOISE |
| sA40>=1 half | 28 | -12% / +0% / +4% / +51% / +4% / +33% / +0% | -0.7 (+10.9) / -2.9 (+7.1) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA40>=2 half | 11 | -30% / -14% / -9% / +20% / +21% / +10% / -14% | -0.1 (+9.8) / -2.1 (+6.6) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sB40>=3 half | 7 | +3% / +2% / +6% / +3% / +25% / +37% / +2% | +0.6 (+1.9) / +3.0 (+3.7) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA60>=1 half | 36 | +2% / +24% / +27% / +35% / +21% / +20% / +24% | -0.2 (+12.0) / -1.8 (+7.3) | Y/Y/Y | Y / Y | Y/Y | 202631 | flip 5: 36/28/29% | NOISE |
| sopen40 half | 55 | +24% / +60% / +45% / +7% / +14% / -4% / +44% | -2.4 (+11.2) / -3.3 (+5.3) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |

Band rule (Z3 V13X band, lock 12R, DS3_ZONES_3_NOISE.md; the earlier assumed-base band is superseded): 1 of 33 pass; TOLERANT 8, STRICT 8.

### 9b. Scaled cut-off sweep on V13Z (sA40>=1 skip)

| factor | cuts L6M / HOLD / MID / PRE / X' / F9 | mean d F9 (MDE) |
|---|---|---|
| x1.0 | +31% / +25% / +23% / +23% / +27% / +31% | +2.2 (+11.2) |

### 9c. V13X placebo ranks (share of draws with cut >= real; n draws), L6M and PRE

| cell | real L6M / PRE | B L6M (n) | C L6M | A L6M | B PRE | C PRE | A PRE | label |
|---|---|---|---|---|---|---|---|---|

### 9d. Per-scope reruns on V13Z (rule applied only to the book / session; cut on the TOTAL composite)

| cell | scope | cut L6M | cut F9 | cut PRE | cut X' | mean d F9 (MDE) |
|---|---|---|---|---|---|---|

### 9e. Re-target decision delay on V13Z (sA40>=1; rtc = same market entry with the original target)

| action | delay | cuts L6M / F9 / PRE / X' | mean d F9 (MDE) |
|---|---|---|---|

### 9f. Vol-tercile cuts on V13Z (day-range tercile over all days; day-cumulative maxDD cut, mean d $k/day)

| cell | low vol | mid | high |
|---|---|---|---|
| sA40>=1 skip | +6% (+0.3) | +14% (+0.2) | -13% (+0.0) |
| sA40>=1 half | +24% (+0.7) | +18% (-0.1) | -6% (-1.4) |
| sA60>=1 half | +29% (+0.8) | +19% (-0.0) | -3% (-1.2) |
| rho60>=2 skip | +3% (+0.3) | +50% (+0.8) | +6% (+0.1) |
| rho60>=2 half | +19% (+0.6) | +41% (+0.3) | -8% (-0.9) |
| nA60>=1 half | +27% (+0.7) | +20% (-0.2) | -6% (-1.2) |
| open20 half | +35% (+0.9) | +54% (+0.3) | +55% (-2.5) |

### 9g. MASTER TABLE finalist x frame: V13Z lock=12 (shipped combined lock) vs lock=None (engine per-book locks only); HEADLINE frame = lock=None until the user confirms; LOCK-ONLY = lock=12 L6M cut >= 10% but lock=None L6M cut < 5%

lock=None base: L6M mean 16.8k, maxDD 183k; F9 mean 14.6k, maxDD 183k; PRE mean 8.4k, maxDD 173k; X' mean 1.2k, maxDD 88k

| cell | lock=12 cuts L6M / F9 / PRE / X' | lock=None cuts L6M / F9 / PRE / X' | mean d F9 lock=None (MDE) | ONE-WEEK (lock=None L6M/F9) | Z3 band pass (V13X-based) lock=12 / lock=None | label |
|---|---|---|---|---|---|---|
| nA40>=1 skip | -11% / -11% / +26% / +34% | -5% / -5% / +14% / +14% | -1.6 (+9.2) | n/n | noise / noise | - |
| nA40>=1 half | -5% / -5% / +8% / +26% | -7% / -7% / -24% / -18% | -2.3 (+6.3) | n/n | noise / noise | - |
| nB40>=1 skip | -16% / -16% / +35% / +0% | -34% / -34% / +14% / +6% | -3.2 (+6.3) | n/n | noise / noise | - |
| nB40>=1 half | -28% / -28% / +47% / +52% | -17% / -17% / -12% / +2% | -4.9 (+5.6) | n/n | noise / noise | - |
| nB40>=2 skip | -14% / -14% / +40% / -20% | -20% / -20% / +15% / -16% | -0.7 (+4.2) | n/n | noise / noise | - |
| nB40>=2 half | -9% / -9% / +35% / +47% | -13% / -13% / -9% / +7% | -2.8 (+5.1) | n/n | noise / noise | - |
| nB40>=3 skip | -4% / -4% / +25% / -8% | -1% / -1% / +9% / -12% | -0.5 (+2.0) | n/n | noise / noise | - |
| nB40>=3 half | -3% / -3% / +10% / +45% | -1% / -1% / +9% / -9% | -0.9 (+1.4) | n/n | noise / noise | - |
| nT40>=2 half | -36% / -36% / +41% / +53% | -26% / -26% / -7% / -15% | -3.9 (+5.4) | n/n | noise / noise | - |
| nT40>=4 half | -25% / -25% / +1% / +32% | -8% / -8% / +7% / +30% | -2.1 (+4.2) | n/n | noise / noise | - |
| nA60>=1 skip | +14% / +14% / +51% / +27% | +32% / +32% / -8% / +19% | -2.4 (+11.5) | n/n | noise / noise | - |
| nA60>=1 half | +0% / +0% / +19% / +24% | -1% / -1% / -3% / +20% | -4.1 (+6.6) | n/n | noise / noise | - |
| nA60>=2 half | -14% / -14% / +4% / +17% | -5% / -5% / -16% / -22% | -2.2 (+5.0) | n/n | noise / noise | - |
| nT60>=3 skip | -34% / -34% / +20% / -15% | -18% / -18% / +13% / -18% | -0.9 (+8.5) | n/n | noise / noise | - |
| nTany40>=2 half | -17% / -17% / +42% / +52% | +3% / +3% / -30% / -18% | -2.2 (+7.7) | n/n | noise / noise | - |
| open20 half | +47% / +47% / +50% / +14% | +43% / +43% / +3% / +8% | -6.4 (+10.3) | n/n | PASS / noise | both frames + |
| open60 half | +60% / +60% / +19% / -1% | +39% / +39% / +11% / +45% | -3.5 (+9.5) | n/n | noise / PASS | both frames + |
| openA40 half | +32% / +32% / +43% / +55% | +36% / +36% / +3% / +37% | -5.3 (+9.1) | n/n | noise / PASS | both frames + |
| rho40>=2 skip | -6% / -6% / +21% / +29% | +4% / +4% / -2% / -2% | -1.2 (+8.7) | n/n | noise / noise | - |
| rho40<=0.5 skip | -19% / -19% / +41% / -36% | -26% / -26% / +11% / -8% | -2.3 (+5.8) | n/n | noise / noise | - |
| rho60>=2 skip | +15% / +15% / +48% / +15% | +23% / +23% / +12% / +40% | +0.5 (+9.9) | n/n | noise / PASS | both frames + |
| rho60>=2 half | +1% / +1% / +29% / -7% | -5% / -5% / -10% / +12% | -1.8 (+5.1) | n/n | noise / noise | - |
| rho60<=0.5 half | +8% / +8% / +31% / +23% | -18% / -18% / -37% / -28% | -2.3 (+4.7) | n/n | noise / noise | - |
| mid_PDR half | -34% / -34% / +47% / +47% | -29% / -29% / -26% / +18% | -7.2 (+8.0) | n/n | noise / noise | - |
| mid_any3 half | -33% / -33% / +49% / +50% | -27% / -27% / -14% / +38% | -7.3 (+7.9) | n/n | noise / noise | - |
| mid_PDR&open40 up | +27% / +27% / +15% / -18% | -0% / -0% / -17% / -7% | +3.1 (+5.6) | n/n | noise / noise | LOCK-ONLY |
| mid_ON&nT40<=1 up | +12% / +12% / -21% / -2% | +10% / +10% / -32% / -5% | +2.8 (+5.1) | n/n | noise / noise | - |
| sA40>=1 skip | +31% / +31% / +23% / +27% | +34% / +34% / +18% / +14% | -1.1 (+12.2) | n/n | noise / noise | both frames + |
| sA40>=1 half | +0% / +0% / +4% / +33% | -0% / -0% / -17% / -13% | -3.1 (+7.1) | n/n | noise / noise | - |
| sA40>=2 half | -14% / -14% / +21% / +10% | -6% / -6% / +1% / -15% | -1.9 (+4.9) | n/n | noise / noise | - |
| sB40>=3 half | +2% / +2% / +25% / +37% | -3% / -3% / +10% / +7% | -0.4 (+2.2) | n/n | noise / noise | - |
| sA60>=1 half | +24% / +24% / +21% / +20% | +0% / +0% / +5% / +18% | -3.3 (+6.9) | n/n | noise / noise | LOCK-ONLY |
| sopen40 half | +60% / +44% / +14% / -4% | +39% / +39% / -2% / +22% | -3.6 (+9.3) | n/n | noise / noise | - |


Z3 noise-band rule (band computed on V13Z, recompute on V13Z pending) (band row by flagged share; flip 5.0 for masks >= 3.5% of rows): lock=12 passes: ['open20 half']; lock=None passes: ['open60 half', 'openA40 half', 'rho60>=2 skip'] (necessary, not sufficient; the passing cells fail the placebo and carrying-week standards above).

### 9h. lock=None frame for the cells that hold in both frames: cut-off sweep (sA40>=1 skip) and placebo ranks (share of draws with cut >= real; n per kind)

| factor | cuts L6M / HOLD / MID / PRE / X' / F9 (lock=None) |
|---|---|
| x1.0 | +34% / +34% / +31% / +18% / +14% / +34% |

| cell | real L6M / PRE / X' | B L6M / PRE / X' (n) | C L6M / PRE / X' | A L6M / PRE / X' | label |
|---|---|---|---|---|---|
| sA40>=1 skip | +34% / +18% / +14% | 0.31 / 0.06 / 0.27 (100) | 0.40 / 0.14 / 0.41 | 0.36 / 0.12 / 0.45 | (volume effect) |
| rho60>=2 skip | +23% / +12% / +40% | 0.37 / 0.17 / 0.06 (100) | 0.43 / 0.15 / 0.04 | 0.39 / 0.10 / 0.05 | (volume effect) |
| nA60>=1 skip | +32% / -8% / +19% | 0.40 / 0.42 / 0.31 (100) | 0.44 / 0.50 / 0.25 | 0.39 / 0.45 / 0.32 | (volume effect) |
| sA40>=1 half | -0% / -17% / -13% | n/a / n/a / n/a (0) | n/a / n/a / n/a | n/a / n/a / n/a | UNTESTED |
| nA60>=1 half | -1% / -3% / +20% | n/a / n/a / n/a (0) | n/a / n/a / n/a | n/a / n/a / n/a | UNTESTED |
| open20 half | +43% / +3% / +8% | 0.29 / 0.64 / 0.88 (100) | 0.33 / 0.70 / 0.90 | 0.34 / 0.72 / 0.86 | (volume effect) |
| openA40 half | +36% / +3% / +37% | 0.58 / 0.47 / 0.43 (100) | 0.38 / 0.49 / 0.46 | 0.45 / 0.58 / 0.42 | (volume effect) |
| sopen40 half | +39% / -2% / +22% | 0.19 / 0.23 / 0.47 (100) | 0.16 / 0.33 / 0.54 | 0.27 / 0.33 / 0.45 | (volume effect) |

### 9i. Priority cells in the lock=None frame (headline): episode-proofing, book x session, vol tercile, best-of-N null, causality audit

| cell (lock=None) | window | cut | carrying week | cut w/o it | LOWO range | LOMO range | bootstrap 90% CI / P(cut>0) | ONE-WEEK |
|---|---|---|---|---|---|---|---|---|
| sA40>=1 skip | L6M | +34% | 202630 | +39% | +24% .. +47% | -39% .. +45% | [-84%, +62%] / 0.67 | - |
| sA40>=1 skip | HOLD | +34% | 202630 | +31% | +24% .. +47% | +12% .. +44% | [-24%, +61%] / 0.85 | - |
| sA40>=1 skip | MID | +31% | 202613 | -2% | -23% .. +52% | -2% .. +53% | [-71%, +80%] / 0.65 | ONE-WEEK |
| sA40>=1 skip | PRE | +18% | 202506 | +1% | -4% .. +31% | +1% .. +39% | [-57%, +52%] / 0.79 | ONE-WEEK |
| sA40>=1 skip | X' | +14% | 202329 | -31% | -31% .. +37% | -31% .. +29% | [-61%, +23%] / 0.33 | ONE-WEEK |
| sA40>=1 skip | F9 | +34% | 202630 | +39% | +24% .. +47% | -39% .. +45% | [-56%, +67%] / 0.77 | - |
| nA60>=1 skip | L6M | +32% | 202630 | +36% | +21% .. +45% | -39% .. +41% | [-84%, +59%] / 0.67 | - |
| nA60>=1 skip | HOLD | +32% | 202630 | +26% | +21% .. +45% | +11% .. +41% | [-21%, +59%] / 0.86 | - |
| nA60>=1 skip | MID | +27% | 202613 | -8% | -19% .. +49% | -8% .. +42% | [-77%, +66%] / 0.65 | ONE-WEEK |
| nA60>=1 skip | PRE | -8% | 202506 | -30% | -30% .. +23% | -30% .. +35% | [-44%, +59%] / 0.82 | - |
| nA60>=1 skip | X' | +19% | 202329 | -23% | -23% .. +39% | -23% .. +36% | [-53%, +41%] / 0.56 | ONE-WEEK |
| nA60>=1 skip | F9 | +32% | 202630 | +36% | +21% .. +45% | -39% .. +41% | [-56%, +63%] / 0.77 | - |
| sA40>=1 half | L6M | -0% | 202630 | -4% | -9% .. +9% | -35% .. +15% | [-49%, +14%] / 0.17 | - |
| sA40>=1 half | HOLD | -0% | 202630 | -4% | -9% .. +9% | -27% .. +15% | [-41%, +51%] / 0.60 | - |
| sA40>=1 half | MID | +42% | 202613 | +15% | +15% .. +63% | +15% .. +63% | [+7%, +78%] / 0.96 | ONE-WEEK |
| sA40>=1 half | PRE | -17% | 202506 | -4% | -28% .. +8% | -17% .. +14% | [-37%, +32%] / 0.69 | - |
| sA40>=1 half | X' | -13% | 202329 | -32% | -38% .. +7% | -60% .. +5% | [-172%, +9%] / 0.16 | - |
| sA40>=1 half | F9 | -0% | 202630 | -4% | -9% .. +9% | -35% .. +15% | [-44%, +31%] / 0.45 | - |
| nA60>=1 half | L6M | -1% | 202630 | -5% | -8% .. +8% | -32% .. +13% | [-48%, +12%] / 0.15 | - |
| nA60>=1 half | HOLD | -1% | 202630 | -5% | -8% .. +8% | -28% .. +18% | [-39%, +47%] / 0.58 | - |
| nA60>=1 half | MID | +14% | 202613 | +15% | +3% .. +39% | +14% .. +15% | [+0%, +49%] / 0.96 | - |
| nA60>=1 half | PRE | -3% | 202506 | -7% | -14% .. +11% | -7% .. +13% | [-26%, +36%] / 0.78 | - |
| nA60>=1 half | X' | +20% | 202329 | -12% | -13% .. +37% | -20% .. +37% | [-114%, +27%] / 0.39 | ONE-WEEK |
| nA60>=1 half | F9 | -1% | 202630 | -5% | -8% .. +8% | -32% .. +13% | [-48%, +20%] / 0.32 | - |
| sopen40 half | L6M | +39% | 202630 | +47% | +26% .. +47% | +29% .. +39% | [+21%, +53%] / 0.98 | - |
| sopen40 half | HOLD | +39% | 202630 | +43% | +26% .. +46% | +31% .. +39% | [+20%, +49%] / 0.99 | - |
| sopen40 half | MID | +25% | 202613 | -10% | -10% .. +42% | -7% .. +25% | [-7%, +25%] / 0.75 | ONE-WEEK |
| sopen40 half | PRE | -2% | 202506 | +9% | -21% .. +16% | -17% .. +19% | [-36%, +26%] / 0.64 | - |
| sopen40 half | X' | +22% | 202329 | +4% | +4% .. +45% | -5% .. +28% | [-31%, +39%] / 0.72 | ONE-WEEK |
| sopen40 half | F9 | +39% | 202630 | +47% | +26% .. +47% | +27% .. +39% | [+7%, +41%] / 0.96 | - |
| open20 half | L6M | +43% | 202630 | +46% | +38% .. +49% | +22% .. +53% | [+18%, +63%] / 1.00 | - |
| open20 half | HOLD | +43% | 202630 | +46% | +38% .. +49% | +35% .. +45% | [+25%, +55%] / 1.00 | - |
| open20 half | MID | +29% | 202613 | +11% | +11% .. +37% | +11% .. +29% | [-0%, +30%] / 0.89 | ONE-WEEK |
| open20 half | PRE | +3% | 202506 | +10% | -14% .. +16% | -7% .. +16% | [-13%, +35%] / 0.88 | - |
| open20 half | X' | +8% | 202329 | -3% | -3% .. +36% | -8% .. +23% | [-9%, +48%] / 0.88 | - |
| open20 half | F9 | +43% | 202630 | +46% | +38% .. +49% | +22% .. +53% | [+18%, +59%] / 1.00 | - |
| openA40 half | L6M | +36% | 202630 | +38% | +28% .. +40% | +30% .. +36% | [+30%, +53%] / 1.00 | - |
| openA40 half | HOLD | +36% | 202630 | +38% | +28% .. +40% | +36% .. +39% | [+22%, +55%] / 0.99 | - |
| openA40 half | MID | +16% | 202613 | +14% | -4% .. +32% | +14% .. +16% | [+0%, +16%] / 0.95 | - |
| openA40 half | PRE | +3% | 202506 | +13% | -15% .. +17% | -6% .. +21% | [-23%, +34%] / 0.77 | - |
| openA40 half | X' | +37% | 202329 | +28% | +26% .. +53% | +26% .. +51% | [+7%, +58%] / 0.97 | - |
| openA40 half | F9 | +36% | 202630 | +38% | +28% .. +40% | +18% .. +36% | [+13%, +45%] / 1.00 | - |

Per book x session maxDD cut (lock=None, rule applied everywhere; L6M | HOLD | PRE | X'):

| cell | K6 | P6 | U6 | H6 | M6 | A6 | asia | london | nyam | nypm |
|---|---|---|---|---|---|---|---|---|---|---|
| sA40>=1 skip | +59%/+13%/-14%/+57% | +38%/+17%/+6%/+22% | +23%/+19%/+10%/-14% | +46%/-28%/+1%/+17% | +4%/+29%/+26%/-2% | -111%/-95%/+29%/-14% | +46%/+46%/+25%/+21% | -6%/+19%/+8%/+26% | +23%/-45%/-8%/+8% | +55%/+34%/+15%/-14% |
| nA60>=1 skip | +61%/+10%/+2%/+53% | +37%/+18%/-19%/+43% | +23%/+19%/+6%/-21% | +46%/-10%/+16%/+5% | +4%/+28%/+44%/-8% | -111%/-95%/+8%/+22% | +46%/+40%/-9%/+39% | -0%/+22%/+20%/+20% | +22%/-65%/-7%/+37% | +55%/+36%/+15%/+3% |
| sA40>=1 half | -18%/+14%/-55%/-21% | +9%/+9%/+18%/-22% | +18%/+16%/+0%/-6% | +17%/-8%/+4%/+11% | +15%/+38%/+19%/-26% | -13%/-5%/+14%/+25% | +4%/+4%/+21%/+15% | -19%/+16%/+9%/-12% | +45%/-46%/-19%/+1% | +3%/-6%/-22%/+9% |
| nA60>=1 half | -18%/+14%/-46%/+4% | +8%/+8%/+2%/+16% | +18%/+16%/+3%/-7% | +17%/+1%/+14%/+11% | +15%/+38%/+19%/-27% | -13%/-5%/-4%/+29% | +1%/+1%/+12%/+24% | -18%/+5%/+15%/+2% | +45%/-53%/-12%/+15% | +3%/-6%/-14%/+17% |
| sopen40 half | -5%/+15%/+16%/+15% | +51%/+50%/+9%/+24% | +19%/+14%/+26%/+3% | -10%/-10%/+24%/+11% | +32%/+49%/+25%/+41% | +55%/-12%/+30%/+35% | +48%/+15%/-5%/+14% | +39%/+57%/+15%/+3% | +24%/-3%/+40%/+49% | +48%/+50%/+6%/-6% |
| open20 half | -10%/+20%/+25%/+11% | +52%/+44%/+9%/+20% | +46%/+46%/+29%/+28% | +40%/+34%/+29%/+28% | +41%/+54%/+33%/+5% | +35%/+40%/+51%/+51% | +37%/+37%/+12%/+26% | +52%/+57%/+35%/+28% | +35%/+9%/+49%/+47% | +80%/+85%/-3%/+40% |
| openA40 half | -18%/+14%/+25%/-29% | +42%/+42%/+4%/+38% | +38%/+34%/+36%/+38% | +35%/+31%/+13%/+18% | +24%/+40%/+28%/+42% | +58%/+27%/+42%/+43% | +36%/+36%/-20%/+35% | +43%/+44%/+35%/+32% | +25%/-4%/+54%/+49% | +67%/+71%/+19%/-6% |

Vol tercile (day-range tercile; day-cumulative maxDD cut, mean d $k/day), lock=None: low | mid | high

* sA40>=1 skip: -3% (-0.2) | +13% (-0.3) | +25% (+0.1)
* nA60>=1 skip: +6% (-0.0) | +9% (-0.5) | +21% (-0.1)
* sA40>=1 half: +2% (-0.0) | -9% (-0.8) | +17% (-0.4)
* nA60>=1 half: +7% (+0.1) | -9% (-0.9) | +16% (-0.5)
* sopen40 half: +38% (+1.1) | +5% (+0.0) | +17% (-3.0)
* open20 half: +38% (+1.0) | +37% (-0.2) | +41% (-3.9)
* openA40 half: +43% (+1.2) | +25% (-0.2) | +35% (-3.7)

Best-of-N null: pooled 2100 lock=None information-free masks (random rows / same-volume / shuffled-day of the 3-4 priority cells, same flag shares ~28-36%); best L6M cut among N=314 draws from that pool (2000 repeats): median +75%, 95th percentile +83%. Best real L6M cut among the 34 finalists in lock=None: +43%; sA40>=1 skip +34%, nA60>=1 skip +32%.

Causality audit (audit.py): 100 random signals x 8 lines (800 line-checks): the ahead and behind fresh distance recomputed by brute force from the stream rows with knowable-index ek <= signal second, alive (cap > kin) and never touched (end > kin) equals the stored feature in 800 of 800 checks (0 mismatches); the stream knowable index ek is the POI store's causal timestamp (poi_core), not re-derived here.
## 10. HEADLINE BASE V13T (= V13Z with the five take lines OFF, lock none = live per-book stack; lock-12 columns are REFERENCE (not live); exact U7 same-side, exact 5 THP take/tighten lines, exact lots, 12R per-book + give-back, ER running-max)

V13T base: L6M mean 29.2k/wk, maxDD 150k; HOLD mean 24.5k/wk, maxDD 150k; MID mean 19.0k/wk, maxDD 44k; PRE mean 8.9k/wk, maxDD 132k; X' mean -4.6k/wk, maxDD 234k; F9 mean 26.8k/wk, maxDD 150k. Base maxDD-carrying week (L6M / F9 / PRE / X'): 202631 / 202631 / 202440 / 202342.

### 10a. All 34 finalists on V13T (screen; placebo status in 7c)

| cell (V13X) | flag % | maxDD cut L3M / L6M / HOLD / MID / PRE / X' / F9 | mean d $k/wk L6M (MDE) / PRE (MDE) | S/T/N | TOL-B / nc | ONE-WEEK L6M/F9 | week carrying (L6M) | band (flip row) L6M / PRE / X' | band rule |
|---|---|---|---|---|---|---|---|---|---|
| nA40>=1 skip | 25 | +46% / +22% / +22% / +26% / +18% / +10% / +22% | -6.2 (+9.4) / +4.7 (+10.9) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA40>=1 half | 25 | +13% / +7% / +7% / +28% / -9% / +3% / +7% | -0.8 (+5.4) / -3.9 (+7.7) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=1 skip | 21 | -16% / -6% / -6% / -47% / +41% / +57% / -6% | -2.2 (+7.2) / +0.2 (+9.3) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=1 half | 21 | -13% / -5% / -5% / -7% / -16% / +31% / -5% | -1.3 (+3.1) / -0.6 (+5.8) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=2 skip | 10 | +12% / +2% / +2% / -20% / +20% / +33% / +2% | +1.9 (+3.6) / +1.7 (+6.0) | n/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=2 half | 10 | +9% / +1% / +1% / -60% / -16% / +47% / +1% | +0.5 (+1.6) / +1.5 (+4.1) | n/n/Y | n / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=3 skip | 6 | -15% / -7% / -7% / +0% / +18% / +25% / -7% | -0.2 (+1.9) / +2.2 (+4.5) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nB40>=3 half | 6 | -13% / -6% / -6% / -0% / +22% / +41% / -6% | -0.3 (+1.0) / +0.9 (+2.9) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nT40>=2 half | 20 | -1% / -3% / -3% / +1% / +1% / +48% / -3% | -1.0 (+2.7) / -1.7 (+6.8) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nT40>=4 half | 5 | -6% / -2% / -2% / +0% / +18% / +53% / -2% | -0.3 (+0.6) / +0.3 (+2.8) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA60>=1 skip | 32 | +63% / +44% / +13% / -45% / -16% / -16% / +44% | -3.7 (+13.4) / +0.9 (+11.0) | n/n/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA60>=1 half | 32 | +25% / +16% / +16% / +21% / +5% / +32% / +16% | -4.0 (+11.2) / -3.6 (+8.1) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nA60>=2 half | 14 | -1% / -3% / -3% / +1% / -13% / +7% / -3% | -1.0 (+3.2) / -2.7 (+6.3) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nT60>=3 skip | 22 | -34% / -27% / -27% / -0% / +10% / +55% / -27% | -7.7 (+15.1) / -0.1 (+10.7) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| nTany40>=2 half | 47 | -13% / +5% / +5% / +28% / -0% / +33% / +5% | -4.9 (+10.1) / -0.3 (+5.5) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| open20 half | 81 | +33% / +45% / +45% / +51% / +15% / +13% / +45% | -15.7 (+18.3) / -4.0 (+8.1) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| open60 half | 47 | -33% / +18% / +18% / -3% / -14% / -0% / +18% | -17.7 (+20.2) / -0.7 (+7.8) | n/n/n | n / n | Y/Y | 202631 | flip 5: 36/28/29% | NOISE |
| openA40 half | 75 | +2% / +23% / +23% / -16% / +7% / +56% / +23% | -17.4 (+19.4) / -4.3 (+7.5) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho40>=2 skip | 18 | +64% / +29% / +29% / +61% / +2% / +13% / +29% | -4.8 (+9.6) / +3.2 (+8.2) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho40<=0.5 skip | 15 | -6% / -5% / -5% / -72% / +32% / +64% / -5% | -0.7 (+5.1) / +1.5 (+6.5) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho60>=2 skip | 20 | +39% / +45% / +45% / +1% / +7% / -22% / +45% | -1.3 (+9.3) / +3.6 (+9.5) | n/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho60>=2 half | 20 | +25% / +16% / +16% / +3% / +30% / +16% / +16% | -3.9 (+10.5) / +1.4 (+4.2) | Y/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| rho60<=0.5 half | 24 | +2% / -2% / -2% / +55% / -72% / +16% / -2% | -2.7 (+3.2) / -1.4 (+4.4) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| mid_PDR half | 22 | -8% / +7% / +7% / -5% / +18% / +41% / +7% | -5.0 (+7.2) / -0.8 (+5.9) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| mid_any3 half | 41 | -37% / -6% / -6% / -63% / +28% / +54% / -6% | -8.6 (+10.7) / +0.5 (+5.9) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| mid_PDR&open40 up | 10 | +9% / +10% / +10% / -50% / -105% / -5% / +10% | +5.0 (+6.1) / -1.9 (+3.8) | n/n/Y | n / n | Y/Y | 202631 | flip 5: 36/28/29% | NOISE |
| mid_ON&nT40<=1 up | 10 | +15% / +4% / +4% / +2% / +3% / -4% / +4% | -5.8 (+12.7) / -1.1 (+3.9) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA40>=1 skip | 28 | +63% / +64% / +21% / -45% / +27% / +4% / +58% | -2.9 (+14.5) / +4.0 (+11.2) | n/Y/Y | Y / Y | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA40>=1 half | 28 | +25% / +28% / +28% / +21% / -4% / +6% / +28% | -3.1 (+11.6) / -4.5 (+7.8) | n/n/Y | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA40>=2 half | 11 | -3% / -4% / -4% / +1% / +6% / +17% / -4% | -0.7 (+3.2) / -0.2 (+4.3) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sB40>=3 half | 7 | -15% / -6% / -6% / +0% / +11% / +52% / -6% | -0.3 (+1.9) / +1.3 (+3.6) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |
| sA60>=1 half | 36 | -9% / +37% / +37% / +18% / +9% / +16% / +37% | -5.0 (+13.6) / -3.4 (+8.1) | n/n/n | n / n | Y/Y | 202631 | flip 5: 36/28/29% | NOISE |
| sopen40 half | 55 | -49% / +1% / +1% / +1% / -14% / +15% / +1% | -18.6 (+19.9) / -2.9 (+8.1) | n/n/n | n / n | n/n | 202631 | flip 5: 36/28/29% | NOISE |

Band rule (Z3 V13X band, lock 12R, DS3_ZONES_3_NOISE.md; the earlier assumed-base band is superseded): 0 of 33 pass; TOLERANT 8, STRICT 5.

### 10b. Scaled cut-off sweep on V13T (sA40>=1 skip)

| factor | cuts L6M / HOLD / MID / PRE / X' / F9 | mean d F9 (MDE) |
|---|---|---|
| x1.0 | +64% / +21% / -45% / +27% / +4% / +58% | -1.9 (+12.1) |

### 10c. V13X placebo ranks (share of draws with cut >= real; n draws), L6M and PRE

| cell | real L6M / PRE | B L6M (n) | C L6M | A L6M | B PRE | C PRE | A PRE | label |
|---|---|---|---|---|---|---|---|---|

### 10d. Per-scope reruns on V13T (rule applied only to the book / session; cut on the TOTAL composite)

| cell | scope | cut L6M | cut F9 | cut PRE | cut X' | mean d F9 (MDE) |
|---|---|---|---|---|---|---|

### 10e. Re-target decision delay on V13T (sA40>=1; rtc = same market entry with the original target)

| action | delay | cuts L6M / F9 / PRE / X' | mean d F9 (MDE) |
|---|---|---|---|

### 10f. Vol-tercile cuts on V13T (day-range tercile over all days; day-cumulative maxDD cut, mean d $k/day)

| cell | low vol | mid | high |
|---|---|---|---|
| sA40>=1 skip | -19% (-0.7) | +24% (-0.2) | -24% (+1.6) |
| sA40>=1 half | +17% (+0.4) | +25% (-1.0) | +2% (-1.2) |
| sA60>=1 half | +23% (+0.5) | +15% (-1.3) | +8% (-0.9) |
| rho60>=2 skip | -5% (-0.3) | +39% (+0.0) | +8% (+0.8) |
| rho60>=2 half | +14% (+0.2) | +29% (-0.4) | +9% (-0.1) |
| nA60>=1 half | +16% (+0.3) | +24% (-1.2) | +8% (-0.9) |
| open20 half | +36% (+0.7) | +39% (-0.9) | +49% (-3.0) |

### 10g. MASTER TABLE finalist x frame: V13T lock=12 (reference, not live) (shipped combined lock) vs lock=None (engine per-book locks only); HEADLINE frame = lock=None until the user confirms; LOCK-ONLY = lock=12 L6M cut >= 10% but lock=None L6M cut < 5%

lock=None base: L6M mean 37.1k, maxDD 132k; F9 mean 33.7k, maxDD 132k; PRE mean 17.1k, maxDD 166k; X' mean 4.7k, maxDD 91k

| cell | lock=12 cuts L6M / F9 / PRE / X' | lock=None cuts L6M / F9 / PRE / X' | mean d F9 lock=None (MDE) | ONE-WEEK (lock=None L6M/F9) | Z3 band pass (V13X-based) lock=12 / lock=None | label |
|---|---|---|---|---|---|---|
| nA40>=1 skip | +22% / +22% / +18% / +10% | -15% / -15% / +3% / -72% | -5.1 (+11.3) | n/n | noise / noise | LOCK-ONLY |
| nA40>=1 half | +7% / +7% / -9% / +3% | -40% / -40% / +2% / -32% | -3.2 (+6.0) | n/n | noise / noise | - |
| nB40>=1 skip | -6% / -6% / +41% / +57% | -67% / -67% / +30% / -27% | -9.1 (+8.3) | n/n | noise / noise | - |
| nB40>=1 half | -5% / -5% / -16% / +31% | -32% / -32% / +14% / +20% | -4.6 (+4.3) | n/n | noise / noise | - |
| nB40>=2 skip | +2% / +2% / +20% / +33% | -9% / -9% / +19% / -33% | -0.9 (+5.0) | n/n | noise / noise | - |
| nB40>=2 half | +1% / +1% / -16% / +47% | -1% / -1% / +10% / +10% | -1.2 (+2.8) | n/n | noise / noise | - |
| nB40>=3 skip | -7% / -7% / +18% / +25% | -15% / -15% / -2% / -32% | -0.7 (+2.1) | n/n | noise / noise | - |
| nB40>=3 half | -6% / -6% / +22% / +41% | -9% / -9% / +2% / +7% | -1.1 (+1.5) | n/n | noise / noise | - |
| nT40>=2 half | -3% / -3% / +1% / +48% | -45% / -45% / +15% / +0% | -3.3 (+4.5) | n/n | noise / noise | - |
| nT40>=4 half | -2% / -2% / +18% / +53% | -9% / -9% / +4% / -11% | -0.6 (+0.8) | n/n | noise / noise | - |
| nA60>=1 skip | +44% / +44% / -16% / -16% | +33% / +33% / +7% / -52% | -5.0 (+14.1) | Y/Y | noise / noise | ONE-WEEK |
| nA60>=1 half | +16% / +16% / +5% / +32% | -1% / -1% / +4% / -31% | -3.5 (+6.9) | n/n | noise / noise | LOCK-ONLY |
| nA60>=2 half | -3% / -3% / -13% / +7% | -40% / -40% / +9% / +3% | -2.8 (+4.2) | n/n | noise / noise | - |
| nT60>=3 skip | -27% / -27% / +10% / +55% | -50% / -50% / +23% / -26% | -5.4 (+8.0) | n/n | noise / noise | - |
| nTany40>=2 half | +5% / +5% / -0% / +33% | -42% / -42% / +22% / +24% | -6.8 (+9.1) | n/n | noise / noise | - |
| open20 half | +45% / +45% / +15% / +13% | +56% / +56% / +41% / +15% | -15.8 (+15.4) | n/n | noise / PASS | both frames + |
| open60 half | +18% / +18% / -14% / -0% | +18% / +18% / +16% / +6% | -12.8 (+13.8) | Y/Y | noise / noise | ONE-WEEK |
| openA40 half | +23% / +23% / +7% / +56% | +18% / +18% / +36% / +41% | -16.6 (+13.5) | n/n | noise / noise | both frames + |
| rho40>=2 skip | +29% / +29% / +2% / +13% | -0% / -0% / +1% / -35% | -3.0 (+10.7) | n/n | noise / noise | LOCK-ONLY |
| rho40<=0.5 skip | -5% / -5% / +32% / +64% | -27% / -27% / +17% / -6% | -5.4 (+7.3) | n/n | noise / noise | - |
| rho60>=2 skip | +45% / +45% / +7% / -22% | +31% / +31% / -11% / +8% | -3.7 (+10.9) | Y/Y | noise / noise | ONE-WEEK |
| rho60>=2 half | +16% / +16% / +30% / +16% | -6% / -6% / -0% / -3% | -3.0 (+5.7) | n/n | noise / noise | LOCK-ONLY |
| rho60<=0.5 half | -2% / -2% / -72% / +16% | -23% / -23% / +13% / +16% | -4.2 (+5.5) | n/n | noise / noise | - |
| mid_PDR half | +7% / +7% / +18% / +41% | -42% / -42% / +30% / +18% | -6.9 (+6.8) | n/n | noise / noise | - |
| mid_any3 half | -6% / -6% / +28% / +54% | -52% / -52% / +22% / +35% | -9.6 (+9.2) | n/n | noise / noise | - |
| mid_PDR&open40 up | +10% / +10% / -105% / -5% | +33% / +33% / -10% / -29% | +4.6 (+7.1) | Y/Y | noise / noise | ONE-WEEK |
| mid_ON&nT40<=1 up | +4% / +4% / +3% / -4% | +16% / +16% / -2% / -8% | +1.0 (+4.5) | Y/Y | noise / noise | ONE-WEEK |
| sA40>=1 skip | +64% / +58% / +27% / +4% | +33% / +33% / +12% / -52% | -4.8 (+14.5) | Y/Y | noise / noise | ONE-WEEK |
| sA40>=1 half | +28% / +28% / -4% / +6% | +18% / +18% / +10% / -19% | -2.5 (+7.5) | n/n | noise / noise | both frames + |
| sA40>=2 half | -4% / -4% / +6% / +17% | -40% / -40% / +5% / -0% | -2.3 (+4.0) | n/n | noise / noise | - |
| sB40>=3 half | -6% / -6% / +11% / +52% | +4% / +4% / +6% / +9% | -0.1 (+2.5) | n/n | noise / noise | both frames + |
| sA60>=1 half | +37% / +37% / +9% / +16% | +13% / +13% / -0% / -35% | -5.0 (+8.1) | n/n | noise / noise | - |
| sopen40 half | +1% / +1% / -14% / +15% | +16% / +16% / +47% / -1% | -13.2 (+13.3) | Y/Y | noise / noise | ONE-WEEK |


Z3 noise-band rule (band computed on V13T, recompute on V13T pending) (band row by flagged share; flip 5.0 for masks >= 3.5% of rows): lock=12 passes: none; lock=None passes: ['open20 half'] (necessary, not sufficient; the passing cells fail the placebo and carrying-week standards above).

### 10h. lock=None frame for the cells that hold in both frames: cut-off sweep (sA40>=1 skip) and placebo ranks (share of draws with cut >= real; n per kind)

| factor | cuts L6M / HOLD / MID / PRE / X' / F9 (lock=None) |
|---|---|
| x1.0 | +33% / +36% / +25% / +12% / -52% / +33% |

| cell | real L6M / PRE / X' | B L6M / PRE / X' (n) | C L6M / PRE / X' | A L6M / PRE / X' | label |
|---|---|---|---|---|---|
| sA40>=1 skip | +33% / +12% / -52% | 0.19 / 0.42 / 0.88 (100) | 0.26 / 0.36 / 0.95 | 0.20 / 0.46 / 0.98 | (volume effect) |
| rho60>=2 skip | +31% / -11% / +8% | 0.21 / 0.90 / 0.40 (100) | 0.17 / 0.85 / 0.45 | 0.14 / 0.87 / 0.36 | (volume effect) |
| nA60>=1 skip | +33% / +7% / -52% | 0.18 / 0.51 / 0.90 (100) | 0.29 / 0.46 / 0.94 | 0.29 / 0.59 / 0.88 | (volume effect) |
| sA40>=1 half | +18% / +10% / -19% | n/a / n/a / n/a (0) | n/a / n/a / n/a | n/a / n/a / n/a | UNTESTED |
| nA60>=1 half | -1% / +4% / -31% | n/a / n/a / n/a (0) | n/a / n/a / n/a | n/a / n/a / n/a | UNTESTED |
| open20 half | +56% / +41% / +15% | 0.06 / 0.49 / 0.75 (100) | 0.05 / 0.53 / 0.80 | 0.05 / 0.43 / 0.80 | placebos beaten on L6M |
| openA40 half | +18% / +36% / +41% | 0.67 / 0.52 / 0.21 (100) | 0.63 / 0.60 / 0.20 | 0.57 / 0.47 / 0.12 | (volume effect) |
| sopen40 half | +16% / +47% / -1% | 0.53 / 0.00 / 0.77 (100) | 0.46 / 0.01 / 0.73 | 0.49 / 0.02 / 0.87 | (volume effect) |

### 10i. Priority cells in the lock=None frame (headline): episode-proofing, book x session, vol tercile, best-of-N null, causality audit

| cell (lock=None) | window | cut | carrying week | cut w/o it | LOWO range | LOMO range | bootstrap 90% CI / P(cut>0) | ONE-WEEK |
|---|---|---|---|---|---|---|---|---|
| sA40>=1 skip | L6M | +33% | 202630 | +9% | +9% .. +40% | +9% .. +40% | [-33%, +47%] / 0.87 | ONE-WEEK |
| sA40>=1 skip | HOLD | +36% | 202606 | +33% | +33% .. +53% | +29% .. +43% | [-24%, +58%] / 0.83 | - |
| sA40>=1 skip | MID | +25% | 202607 | -64% | -64% .. +33% | -64% .. +39% | [-64%, +58%] / 0.51 | ONE-WEEK |
| sA40>=1 skip | PRE | +12% | 202436 | +29% | -14% .. +29% | +6% .. +29% | [-59%, +51%] / 0.67 | - |
| sA40>=1 skip | X' | -52% | 202346 | -61% | -78% .. -22% | -78% .. +7% | [-91%, +23%] / 0.15 | - |
| sA40>=1 skip | F9 | +33% | 202630 | +9% | +9% .. +40% | +9% .. +40% | [-54%, +46%] / 0.76 | ONE-WEEK |
| nA60>=1 skip | L6M | +33% | 202630 | +10% | +10% .. +40% | +10% .. +40% | [-31%, +47%] / 0.87 | ONE-WEEK |
| nA60>=1 skip | HOLD | +36% | 202606 | +33% | +33% .. +54% | +27% .. +43% | [-20%, +58%] / 0.83 | - |
| nA60>=1 skip | MID | +22% | 202607 | -71% | -71% .. +39% | -71% .. +39% | [-71%, +58%] / 0.51 | ONE-WEEK |
| nA60>=1 skip | PRE | +7% | 202436 | +41% | -22% .. +41% | +7% .. +26% | [-39%, +62%] / 0.78 | - |
| nA60>=1 skip | X' | -52% | 202346 | -80% | -80% .. -7% | -72% .. +10% | [-145%, +31%] / 0.32 | - |
| nA60>=1 skip | F9 | +33% | 202630 | +10% | +10% .. +40% | +10% .. +40% | [-54%, +45%] / 0.77 | ONE-WEEK |
| sA40>=1 half | L6M | +18% | 202630 | +26% | -6% .. +26% | +16% .. +26% | [-27%, +39%] / 0.86 | - |
| sA40>=1 half | HOLD | +22% | 202606 | +18% | +16% .. +48% | +18% .. +48% | [-4%, +61%] / 0.93 | - |
| sA40>=1 half | MID | +24% | 202607 | +22% | -3% .. +24% | +22% .. +24% | [+22%, +45%] / 0.96 | - |
| sA40>=1 half | PRE | +10% | 202436 | +30% | +1% .. +30% | +10% .. +30% | [-17%, +40%] / 0.81 | - |
| sA40>=1 half | X' | -19% | 202346 | -12% | -28% .. -4% | -47% .. +5% | [-64%, +12%] / 0.18 | - |
| sA40>=1 half | F9 | +18% | 202630 | +26% | -6% .. +26% | +16% .. +26% | [-19%, +34%] / 0.87 | - |
| nA60>=1 half | L6M | -1% | 202630 | +7% | -12% .. +13% | -6% .. +26% | [-27%, +27%] / 0.74 | - |
| nA60>=1 half | HOLD | +5% | 202606 | -1% | -2% .. +39% | -1% .. +48% | [-12%, +56%] / 0.88 | - |
| nA60>=1 half | MID | +24% | 202607 | +1% | -3% .. +24% | +1% .. +24% | [+1%, +24%] / 0.96 | ONE-WEEK |
| nA60>=1 half | PRE | +4% | 202436 | +43% | -9% .. +43% | +4% .. +43% | [-13%, +43%] / 0.84 | - |
| nA60>=1 half | X' | -31% | 202346 | -38% | -43% .. -4% | -48% .. +8% | [-86%, +14%] / 0.20 | - |
| nA60>=1 half | F9 | -1% | 202630 | +7% | -12% .. +13% | -6% .. +26% | [-20%, +27%] / 0.77 | - |
| sopen40 half | L6M | +16% | 202630 | +1% | -5% .. +36% | +1% .. +48% | [-65%, +60%] / 0.79 | ONE-WEEK |
| sopen40 half | HOLD | -2% | 202606 | +16% | -9% .. +16% | -4% .. +16% | [-43%, +48%] / 0.41 | - |
| sopen40 half | MID | -8% | 202607 | -48% | -48% .. +30% | -12% .. -8% | [-50%, -8%] / 0.04 | - |
| sopen40 half | PRE | +47% | 202436 | +33% | +33% .. +51% | +18% .. +51% | [-9%, +50%] / 0.89 | - |
| sopen40 half | X' | -1% | 202346 | -39% | -39% .. +40% | -39% .. +40% | [-39%, +47%] / 0.68 | - |
| sopen40 half | F9 | +16% | 202630 | +1% | -5% .. +36% | +1% .. +43% | [-62%, +48%] / 0.63 | ONE-WEEK |
| open20 half | L6M | +56% | 202630 | +54% | +50% .. +61% | +48% .. +57% | [+26%, +67%] / 1.00 | - |
| open20 half | HOLD | +38% | 202606 | +56% | +38% .. +56% | +25% .. +56% | [+16%, +57%] / 0.99 | - |
| open20 half | MID | +16% | 202607 | +0% | +0% .. +48% | +16% .. +40% | [-2%, +40%] / 0.84 | ONE-WEEK |
| open20 half | PRE | +41% | 202436 | +37% | +37% .. +43% | +37% .. +43% | [+24%, +46%] / 0.99 | - |
| open20 half | X' | +15% | 202346 | -17% | -17% .. +53% | -17% .. +53% | [-17%, +52%] / 0.82 | ONE-WEEK |
| open20 half | F9 | +56% | 202630 | +54% | +50% .. +61% | +48% .. +56% | [+16%, +63%] / 0.99 | - |
| openA40 half | L6M | +18% | 202630 | +16% | +10% .. +27% | +18% .. +45% | [+16%, +51%] / 1.00 | - |
| openA40 half | HOLD | +11% | 202606 | +18% | +5% .. +21% | +11% .. +18% | [-11%, +42%] / 0.89 | - |
| openA40 half | MID | -0% | 202607 | -61% | -61% .. -0% | -61% .. -0% | [-96%, -0%] / 0.04 | - |
| openA40 half | PRE | +36% | 202436 | +18% | +18% .. +56% | +11% .. +56% | [-4%, +56%] / 0.94 | - |
| openA40 half | X' | +41% | 202346 | +18% | +18% .. +60% | +18% .. +60% | [+5%, +67%] / 0.96 | ONE-WEEK |
| openA40 half | F9 | +18% | 202630 | +16% | +10% .. +27% | +18% .. +45% | [-19%, +44%] / 0.85 | - |

Per book x session maxDD cut (lock=None, rule applied everywhere; L6M | HOLD | PRE | X'):

| cell | K6 | P6 | U6 | H6 | M6 | A6 | asia | london | nyam | nypm |
|---|---|---|---|---|---|---|---|---|---|---|
| sA40>=1 skip | +76%/+29%/-38%/+62% | +42%/+11%/-1%/+1% | +48%/+35%/+4%/+12% | +4%/+4%/+41%/-34% | +16%/+14%/+25%/-2% | -111%/-95%/+29%/-14% | +1%/+3%/+13%/+16% | +39%/-30%/+6%/+9% | +8%/-23%/-17%/-32% | +42%/+38%/+8%/+39% |
| nA60>=1 skip | +76%/+17%/-18%/+59% | +42%/-4%/-32%/+4% | +48%/+34%/+10%/-30% | -2%/-2%/+38%/-59% | +16%/+12%/+42%/+13% | -111%/-95%/+8%/+22% | -6%/-4%/-1%/+23% | +39%/-25%/+13%/+17% | +4%/-89%/-19%/-12% | +42%/+32%/+17%/+42% |
| sA40>=1 half | +7%/+7%/-37%/-24% | +50%/+39%/-5%/-9% | +42%/+42%/+5%/+20% | -38%/-38%/+18%/-1% | +11%/+19%/+15%/-19% | -13%/-5%/+14%/+25% | +2%/+4%/-4%/+13% | +26%/+1%/+6%/+4% | -61%/-20%/-11%/-6% | +18%/+1%/-19%/+14% |
| nA60>=1 half | +7%/+7%/-7%/-9% | +26%/+25%/-20%/-10% | +42%/+42%/+7%/+2% | -41%/-41%/+28%/-6% | +11%/+22%/+14%/-22% | -13%/-5%/-4%/+29% | -2%/-0%/+26%/+16% | -1%/+3%/+9%/+6% | -61%/-38%/-13%/-2% | +18%/-2%/+3%/+16% |
| sopen40 half | +16%/+16%/+29%/+22% | +38%/+12%/+41%/+24% | +23%/+23%/+13%/-5% | -12%/-12%/+49%/+27% | +44%/+48%/+30%/+47% | +55%/-12%/+30%/+35% | +36%/-47%/+35%/+15% | +18%/+27%/+14%/+32% | -72%/+36%/+55%/+41% | +4%/+13%/+27%/+60% |
| open20 half | +23%/+23%/+39%/+8% | +72%/+40%/+43%/+29% | +55%/+55%/+30%/+14% | +60%/+60%/+45%/+42% | +26%/+33%/+35%/+29% | +35%/+40%/+51%/+51% | +50%/+51%/+33%/+31% | +41%/+46%/+40%/+32% | +31%/+29%/+46%/+56% | +68%/+70%/+51%/+56% |
| openA40 half | +4%/+4%/+26%/+8% | +37%/+22%/+36%/+59% | +48%/+45%/+44%/+12% | +11%/+11%/+26%/+37% | +15%/+21%/+36%/+60% | +58%/+27%/+42%/+43% | +29%/+30%/+28%/+43% | +27%/+17%/+41%/+39% | -63%/+20%/+50%/+46% | +31%/+34%/+37%/+50% |

Vol tercile (day-range tercile; day-cumulative maxDD cut, mean d $k/day), lock=None: low | mid | high

* sA40>=1 skip: -0% (-0.1) | +24% (-1.8) | +15% (+0.3)
* nA60>=1 skip: +8% (+0.2) | +24% (-2.3) | +16% (+0.1)
* sA40>=1 half: +6% (+0.2) | -2% (-1.5) | +38% (-0.3)
* nA60>=1 half: +9% (+0.4) | +6% (-1.8) | +32% (-0.4)
* sopen40 half: +33% (+1.4) | +18% (-0.9) | -5% (-4.2)
* open20 half: +43% (+1.7) | +44% (-1.7) | +38% (-5.5)
* openA40 half: +47% (+1.8) | +34% (-1.5) | +8% (-5.4)

Best-of-N null: pooled 2100 lock=None information-free masks (random rows / same-volume / shuffled-day of the 3-4 priority cells, same flag shares ~28-36%); best L6M cut among N=314 draws from that pool (2000 repeats): median +68%, 95th percentile +74%. Best real L6M cut among the 34 finalists in lock=None: +56%; sA40>=1 skip +33%, nA60>=1 skip +33%.

Causality audit (audit.py): 100 random signals x 8 lines (800 line-checks): the ahead and behind fresh distance recomputed by brute force from the stream rows with knowable-index ek <= signal second, alive (cap > kin) and never touched (end > kin) equals the stored feature in 800 of 800 checks (0 mismatches); the stream knowable index ek is the POI store's causal timestamp (poi_core), not re-derived here.
