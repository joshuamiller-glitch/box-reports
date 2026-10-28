# DS3_DIV_YM - own-clock window rules and overnight-hold cells on YM (D3DVE, 2026-10-28)

**Verdict: 0 CONFIRMED, 0 CANDIDATE, 11 DEAD of 11 registered cells.** YM fee $4.84 RT = WEAK proxy (ES value; FEES.md has only MYM 1.78 micro): verdict ceiling CANDIDATE, 2x-cost column shown. Bars-only (class R2, D3CX conservative fills). Research only; no live/execution/chart change, no purchase, UNTOUCHED (after 2026-02-06) never read. Prereg `l2vast/ds3/prereg/DVE_YM_prereg.md` sha256 `bfb242cbff6c5cd7fb18bec949f6c4cd80239b7536e6d8c63d92f985a8d6cd32` (logged in DECISIONS.md before scoring); pre-holdout text DVE_YM_pre.md; one holdout look logged (track DS3_DVE_YM, X span read at the same look). Code l2vast/ds3/code/dve/, outputs l2vast/ds3/out/dve/.

Windows (trade date): selection span used to pick the clocks = WFPRE 2024-02-01..2025-06-30; HOLD 2025-07-01..2026-02-06 (UNTOUCHED boundary); WF = WFPRE+HOLD; X = 2023-04-01..2024-01-31. All $ are weekly means at $1,000 risk per trade, 95% CI and MDE (2.8 SE) in brackets. The DS3_DIV_1_MAPS lists were not used for the window choice (they saw X and part of HOLD); only their rule types. The two drift windows were scanned over 56 clocks per market and judged against a best-of-168 null.

## 1. Verdict table (primary cells)

| cell | rule | tr/wk | WF $/wk [CI] (MDE) | HOLD $/wk [CI] (MDE) | X $/wk [CI] (MDE) | WF gross before cost | WF 2x cost | tier | failed gates | final label |
|---|---|---|---|---|---|---|---|---|---|---|
| DR_0165_m | DRIFT 02:45-03:00 ET SHORT | 4.85 | +352 [-32,+736] (549) | +35 [-575,+645] (872) | -317 [-853,+219] (766) | +981 | -277 | DEAD | cost2x_pre, year_share, span2 | DEAD |
| DR_0870_p | DRIFT 14:30-14:45 ET LONG | 4.72 | +17 [-415,+448] (617) | -620 [-1,595,+356] (1,393) | +193 [-298,+684] (701) | +295 | -262 | DEAD | year_share, hold | DEAD |
| RG_0510 | RANGE-BREAK 08:30-08:45 ET (pre-range 08:15-08:30) | 3.98 | +45 [-219,+309] (377) | -8 [-486,+469] (682) | -203 [-641,+235] (626) | +414 | -269 | DEAD | cost2x_pre, year_share, hold, span2 | DEAD |
| RG_0570 | RANGE-BREAK 09:30-09:45 ET (pre-range 09:15-09:30) | 4.37 | +148 [-139,+435] (410) | +625 [+134,+1,116] (702) | +37 [-324,+399] (517) | +276 | -1 | DEAD | mean_up, beats_a, cost2x_pre, year_share | DEAD |
| RG_0600 | RANGE-BREAK 10:00-10:15 ET (pre-range 09:45-10:00) | 4.22 | -85 [-304,+134] (313) | -159 [-523,+204] (519) | -359 [-727,+9] (526) | +108 | -266 | DEAD | mean_up, beats_a, cost2x_pre, year_share, hold, span2, best_of_N | DEAD |
| RG_0630 | RANGE-BREAK 10:30-10:45 ET (pre-range 10:15-10:30) | 4.41 | -248 [-509,+13] (373) | -38 [-518,+441] (685) | -363 [-753,+28] (557) | -16 | -482 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | DEAD |
| RG_0660 | RANGE-BREAK 11:00-11:15 ET (pre-range 10:45-11:00) | 4.37 | -98 [-331,+135] (333) | -127 [-558,+305] (617) | -270 [-558,+18] (412) | +156 | -356 | DEAD | mean_up, beats_a, cost2x_pre, year_share, hold, span2, best_of_N | DEAD |
| PE_0570_m | POST-EVENT 09:30 first-5-min move, REVERSAL, flat 10:05 | 4.85 | +104 [-255,+462] (512) | +169 [-487,+825] (937) | -126 [-726,+474] (857) | +239 | -34 | DEAD | beats_a, cost2x_pre, year_share, span2 | DEAD |
| PE_0600_m | POST-EVENT 10:00 first-5-min move, REVERSAL, flat 10:35 | 4.85 | -249 [-584,+86] (479) | -300 [-852,+253] (789) | -666 [-1,159,-173] (704) | -65 | -417 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | DEAD |
| ON1 | OVERNIGHT premium: buy 15:59 close, flat next-day 09:30 open (Mon-Thu entries) | 3.73 | +62 [-826,+949] (1,268) | +166 [-912,+1,244] (1,540) | +47 [-871,+965] (1,312) | +192 | -69 | DEAD | beats_a, beats_b, cost2x_pre, year_share, best_of_N | DEAD |
| F19 | B3_F19 own-series: 15:55 daily series RSI2<20|3-lower|IBS<0.2 above SMA200, hold to next 15:55 | 1.14 | -36 [-388,+316] (503) | +484 [-245,+1,212] (1,041) | +59 [-348,+466] (582) | -18 | -55 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, best_of_N | DEAD |

'WF gross before cost' re-runs the same trades with zero slippage and zero fee (post-hoc diagnostic added after the FINAL scoring, not a gate): the gap to the WF column is the whole cost of the D3CX conservative basis.

## 2. By year, halves (weekly $ mean [CI] (MDE)); strict = mean > 0

| cell | 2023 (from Apr) | 2024 | 2025 | 2026 (to 02-06, ~5 wk) | pre-2025 half | post-2025 half | years strictly + | years pass (+ or >= -MDE) | halves both + |
|---|---|---|---|---|---|---|---|---|---|
| DR_0165_m | -352 [-902,+199] (786) | +474 [-65,+1,012] (769) | +316 [-257,+890] (819) | -800 [-1,509,-91] (1,012) | +124 [-272,+519] (565) | +206 [-329,+742] (765) | 2/4 | 4/4 | yes |
| DR_0870_p | +191 [-321,+703] (731) | +48 [-485,+582] (762) | -27 [-733,+680] (1,009) | +275 [-650,+1,200] (1,321) | +109 [-265,+483] (535) | +4 [-647,+655] (931) | 3/4 | 4/4 | yes |
| RG_0510 | -176 [-614,+262] (626) | +106 [-279,+491] (550) | +29 [-345,+402] (534) | -744 [-2,070,+582] (1,894) | -13 [-302,+276] (413) | -51 [-420,+318] (527) | 2/4 | 4/4 | no |
| RG_0570 | +103 [-294,+500] (567) | -397 [-769,-24] (532) | +549 [+162,+936] (553) | +873 [-51,+1,797] (1,320) | -185 [-461,+91] (394) | +592 [+225,+959] (524) | 3/4 | 4/4 | no |
| RG_0600 | -525 [-887,-164] (517) | +178 [-139,+494] (452) | -239 [-549,+71] (443) | -186 [-834,+461] (925) | -120 [-368,+127] (353) | -237 [-527,+52] (413) | 1/4 | 3/4 | no |
| RG_0630 | -525 [-863,-187] (483) | -192 [-594,+210] (574) | -234 [-603,+135] (527) | +130 [-959,+1,219] (1,555) | -333 [-606,-60] (390) | -200 [-553,+153] (505) | 1/4 | 3/4 | no |
| RG_0660 | -366 [-676,-56] (443) | +70 [-246,+386] (452) | -237 [-575,+100] (482) | +146 [-399,+692] (779) | -115 [-343,+113] (325) | -202 [-516,+112] (448) | 2/4 | 4/4 | no |
| PE_0570_m | -34 [-650,+582] (880) | +231 [-266,+727] (709) | -97 [-630,+436] (762) | -47 [-1,840,+1,746] (2,561) | +119 [-267,+505] (552) | -94 [-607,+419] (733) | 1/4 | 4/4 | no |
| PE_0600_m | -564 [-1,056,-71] (704) | -345 [-844,+153] (712) | -172 [-653,+309] (687) | -1,051 [-2,239,+137] (1,697) | -438 [-792,-84] (506) | -266 [-722,+189] (651) | 0/4 | 4/4 | no |
| ON1 | +199 [-818,+1,216] (1,453) | +481 [-679,+1,642] (1,658) | -355 [-1,685,+975] (1,900) | -977 [-2,995,+1,042] (2,884) | +362 [-430,+1,153] (1,131) | -425 [-1,656,+805] (1,757) | 2/4 | 4/4 | no |
| F19 | +7 [-446,+460] (647) | -317 [-794,+160] (681) | +97 [-357,+552] (650) | +1,690 [-235,+3,616] (2,751) | -180 [-515,+155] (479) | +264 [-207,+735] (673) | 3/4 | 4/4 | no |

## 3. Placebos (effect = real minus mean of 40 draws, weekly $; CI by week bootstrap; rank = share of draws below the real mean)

| cell | (a) random direction, WFPRE | (a) WF | (b) random clock, WFPRE | (b) WF | (b) HOLD | (b) WF rank |
|---|---|---|---|---|---|---|
| DR_0165_m | +1,095 [+556,+1,592] r1.00 | +966 [+607,+1,332] r1.00 | +848 [+354,+1,305] r1.00 | +713 [+350,+1,073] r1.00 | +374 [-201,+955] r0.82 | 1.00 |
| DR_0870_p | +585 [+119,+1,049] r0.95 | +336 [-91,+747] r0.90 | +672 [+225,+1,101] r1.00 | +374 [-40,+776] r0.97 | -335 [-1,442,+547] r0.17 | 0.97 |
| RG_0510 | +438 [+160,+755] r1.00 | +413 [+157,+673] r1.00 | +568 [+295,+880] r1.00 | +524 [+252,+796] r1.00 | +405 [-64,+910] r0.97 | 1.00 |
| RG_0570 | +49 [-266,+355] r0.65 | +269 [-3,+533] r0.95 | +491 [+142,+836] r1.00 | +673 [+382,+963] r1.00 | +1,079 [+563,+1,557] r1.00 | 1.00 |
| RG_0600 | +163 [-80,+408] r0.85 | +134 [-60,+324] r0.80 | +455 [+185,+748] r1.00 | +426 [+218,+631] r1.00 | +347 [+0,+705] r0.95 | 1.00 |
| RG_0630 | -75 [-391,+228] r0.28 | -11 [-267,+254] r0.38 | +143 [-188,+460] r0.88 | +243 [-17,+525] r0.97 | +470 [-19,+969] r0.97 | 0.97 |
| RG_0660 | +132 [-158,+408] r0.80 | +132 [-90,+385] r0.85 | +422 [+154,+686] r1.00 | +406 [+196,+633] r1.00 | +356 [-93,+780] r0.95 | 1.00 |
| PE_0570_m | +159 [-284,+562] r0.78 | +187 [-169,+514] r0.90 | +545 [+71,+970] r0.97 | +570 [+189,+918] r1.00 | +609 [-25,+1,259] r0.97 | 1.00 |
| PE_0600_m | +57 [-317,+458] r0.68 | -41 [-363,+248] r0.42 | +259 [-164,+705] r0.93 | +240 [-104,+570] r1.00 | +188 [-343,+778] r0.78 | 1.00 |
| ON1 | +59 [-1,010,+1,190] r0.47 | +202 [-637,+988] r0.60 | -27 [-965,+971] r0.45 | +63 [-650,+875] r0.65 | +271 [-581,+1,195] r0.70 | 0.65 |
| F19 | -271 [-695,+131] r0.20 | -65 [-472,+284] r0.42 | -309 [-603,-20] r0.03 | -138 [-440,+132] r0.17 | +269 [-299,+837] r0.85 | 0.17 |

Best-of-N p95 of the (b) WFPRE effect: N=33 (non-drift) $465; N=168 (drift, 56 clocks x 3 markets) $495.

## 4. Sibling replication and pooled index row (same cell definition run unchanged on the other two markets)

| cell | sibling A WF / HOLD / X | sibling B WF / HOLD / X | sibling(s) all three > 0 | pooled ES+RTY+YM WF $/wk [CI] (MDE) | pooled tier | pooled p (Bonferroni x11) |
|---|---|---|---|---|---|---|
| DR_0165_m | ES: -218 / -265 / -616 | RTY: -33 / -58 / -570 | none | +101 [-885,+1,087] (1,408) | DEAD | 1.00 |
| DR_0870_p | ES: -198 / -730 / +68 | RTY: -134 / -783 / +32 | none | -316 [-1,596,+965] (1,829) | DEAD | 1.00 |
| RG_0510 | ES: -104 / -156 / -281 | RTY: +280 / +35 / -311 | none | +221 [-437,+879] (940) | DEAD | 1.00 |
| RG_0570 | ES: -225 / +171 / -121 | RTY: +106 / +330 / +464 | RTY | +28 [-554,+611] (833) | DEAD | 1.00 |
| RG_0600 | ES: -98 / -409 / -387 | RTY: -195 / -326 / -299 | none | -379 [-920,+163] (774) | DEAD | 1.00 |
| RG_0630 | ES: -412 / -240 / -601 | RTY: -240 / +24 / -309 | none | -900 [-1,555,-246] (935) | DEAD | 1.00 |
| RG_0660 | ES: -583 / -820 / -745 | RTY: -373 / -461 / -435 | none | -1,054 [-1,596,-511] (775) | DEAD | 1.00 |
| PE_0570_m | ES: -437 / -457 / -435 | RTY: +40 / -825 / -624 | none | -293 [-1,107,+521] (1,163) | DEAD | 1.00 |
| PE_0600_m | ES: -438 / -371 / -527 | RTY: -422 / -627 / -283 | none | -1,110 [-1,918,-301] (1,155) | DEAD | 1.00 |
| ON1 | ES: +731 / +804 / +127 | RTY: +235 / +202 / +181 | ES, RTY | +1,028 [-1,279,+3,335] (3,296) | DEAD | 1.00 |
| F19 | ES: +247 / +660 / +369 | RTY: +149 / +275 / -139 | ES | +359 [-504,+1,222] (1,233) | DEAD | 1.00 |

## 5. Link to the live stack (span 2023-04-01..2026-02-06, 149 weeks; stack mean $42,397/wk, SD $135,594, Sharpe 2.25; its 20 worst weeks sum $-3,589,562)

| cell | weekly corr to stack | cell $ in stack's 20 worst weeks (at $1k risk) | same scaled so cell weekly SD = 20 percent of stack SD | scaled weekly mean | marginal stack Sharpe at that scale |
|---|---|---|---|---|---|
| DR_0165_m | -0.05 | +7,497 | +102,058 (k=14) | +2,132 | +0.089 |
| DR_0870_p | -0.06 | +7,565 | +96,321 (k=13) | +877 | +0.028 |
| RG_0510 | -0.14 | +16,410 | +314,375 (k=19) | -537 | -0.010 |
| RG_0570 | -0.00 | -1,090 | -20,623 (k=19) | +2,203 | +0.072 |
| RG_0600 | -0.12 | -251 | -5,739 (k=23) | -3,815 | -0.197 |
| RG_0630 | +0.05 | +89 | +1,782 (k=20) | -5,682 | -0.358 |
| RG_0660 | +0.13 | -1,707 | -39,913 (k=23) | -3,493 | -0.276 |
| PE_0570_m | +0.03 | +3,643 | +51,152 (k=14) | +516 | -0.031 |
| PE_0600_m | -0.13 | -5,923 | -91,540 (k=15) | -5,779 | -0.295 |
| ON1 | +0.13 | +2,100 | +13,333 (k=6) | +366 | -0.078 |
| F19 | -0.11 | +645 | +10,133 (k=16) | -130 | -0.001 |

The stack link is shown for every cell for completeness; with no cell reaching CONFIRMED there is no portfolio add. Positive 'worst-20' P&L from a negative-edge cell is noise, not diversification.

## 6. Top cells regardless of verdict (ranked by WF t = mean / SE)

- **DR_0165_m** (DRIFT 02:45-03:00 ET SHORT): WF +352 [-32,+736] (549), t +1.80; HOLD +35 [-575,+645] (872); X -317 [-853,+219] (766); tier DEAD; failed gates cost2x_pre, year_share, span2; years strictly positive 2/4; pooled WF +101 (p 1.00). Weekly MDE 549: the cell is inside its MDE.
- **RG_0570** (RANGE-BREAK 09:30-09:45 ET (pre-range 09:15-09:30)): WF +148 [-139,+435] (410), t +1.01; HOLD +625 [+134,+1,116] (702); X +37 [-324,+399] (517); tier DEAD; failed gates mean_up, beats_a, cost2x_pre, year_share; years strictly positive 3/4; pooled WF +28 (p 1.00). Weekly MDE 410: the cell is inside its MDE.
- **PE_0570_m** (POST-EVENT 09:30 first-5-min move, REVERSAL, flat 10:05): WF +104 [-255,+462] (512), t +0.57; HOLD +169 [-487,+825] (937); X -126 [-726,+474] (857); tier DEAD; failed gates beats_a, cost2x_pre, year_share, span2; years strictly positive 1/4; pooled WF -293 (p 1.00). Weekly MDE 512: the cell is inside its MDE.

## 7. Notes and disclosures
- Print-level stop/limit fill checks (ES/RTY trades files on disk) were NOT run: no cell is CONFIRMED or reaches the CANDIDATE tier; YM has no trades file.
- Range cells that trigger on both sides of the pre-range inside one minute are skipped (counted in orders but not trades). ON1 excludes Friday entries (no weekend hold); F19 holds Friday to Monday exactly as its spec.
- Placebo (b) for ON1 (random entry minute, same exit) is a weak placebo by construction (the premium accrues overnight whatever the entry minute); for F19 it is random days above the SMA200 with the real count (regime control).
- The prereg predictions for the range cells state both a cost arithmetic (about -$400 to -$650/wk at zero edge) and a wider range (-$200 to +$100); the realised numbers are reported against the arithmetic in the WF-gross column. Prereg smoke-test sums and the F19 NaN-rolling fix are disclosed in the prereg.
- UNTOUCHED never read; HOLD includes the part of 2025-07..2026-02 that the maps also saw, but the clocks here were chosen on WFPRE alone.
