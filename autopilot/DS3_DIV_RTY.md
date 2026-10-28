# DS3_DIV_RTY - own-clock window rules and overnight-hold cells on RTY (D3DVE, 2026-10-28)

**Verdict: 0 CONFIRMED, 0 CANDIDATE, 11 DEAD of 11 registered cells.** RTY fee $4.84 RT = WEAK proxy (ES value; FEES.md has only M2K 1.78 micro): verdict ceiling CANDIDATE, 2x-cost column shown. Bars-only (class R2, D3CX conservative fills). Research only; no live/execution/chart change, no purchase, UNTOUCHED (after 2026-02-06) never read. Prereg `l2vast/ds3/prereg/DVE_RTY_prereg.md` sha256 `3c651d10ac29158e6a87d300e3437394bbe652f15b383e1fac5ce5587fa2b040` (logged in DECISIONS.md before scoring); pre-holdout text DVE_RTY_pre.md; one holdout look logged (track DS3_DVE_RTY, X span read at the same look). Code l2vast/ds3/code/dve/, outputs l2vast/ds3/out/dve/.

Windows (trade date): selection span used to pick the clocks = WFPRE 2024-02-01..2025-06-30; HOLD 2025-07-01..2026-02-06 (UNTOUCHED boundary); WF = WFPRE+HOLD; X = 2023-04-01..2024-01-31. All $ are weekly means at $1,000 risk per trade, 95% CI and MDE (2.8 SE) in brackets. The DS3_DIV_1_MAPS lists were not used for the window choice (they saw X and part of HOLD); only their rule types. The two drift windows were scanned over 56 clocks per market and judged against a best-of-168 null.

## 1. Verdict table (primary cells)

| cell | rule | tr/wk | WF $/wk [CI] (MDE) | HOLD $/wk [CI] (MDE) | X $/wk [CI] (MDE) | WF gross before cost | WF 2x cost | tier | failed gates | final label |
|---|---|---|---|---|---|---|---|---|---|---|
| DR_0165_m | DRIFT 02:45-03:00 ET SHORT | 4.82 | -33 [-351,+285] (454) | -58 [-635,+518] (824) | -570 [-1,066,-73] (709) | +697 | -764 | DEAD | mean_up, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | DEAD |
| DR_0885_m | DRIFT 14:45-15:00 ET SHORT | 4.72 | -154 [-622,+314] (669) | -946 [-1,811,-82] (1,235) | -690 [-1,422,+43] (1,046) | +221 | -529 | DEAD | cost2x_pre, year_share, hold, span2 | DEAD |
| RG_0510 | RANGE-BREAK 08:30-08:45 ET (pre-range 08:15-08:30) | 4.14 | +280 [+21,+539] (370) | +35 [-479,+550] (735) | -311 [-737,+116] (609) | +580 | -76 | DEAD | year_share, span2 | DEAD |
| RG_0570 | RANGE-BREAK 09:30-09:45 ET (pre-range 09:15-09:30) | 4.32 | +106 [-133,+345] (341) | +330 [-123,+782] (646) | +464 [+56,+873] (584) | +249 | -31 | DEAD | beats_a, cost2x_pre, year_share | DEAD |
| RG_0600 | RANGE-BREAK 10:00-10:15 ET (pre-range 09:45-10:00) | 4.26 | -195 [-429,+39] (335) | -326 [-817,+165] (701) | -299 [-625,+27] (466) | -15 | -389 | DEAD | mean_up, beats_a, cost2x_pre, year_share, hold, span2, best_of_N | DEAD |
| RG_0630 | RANGE-BREAK 10:30-10:45 ET (pre-range 10:15-10:30) | 4.28 | -240 [-488,+8] (354) | +24 [-405,+453] (613) | -309 [-684,+66] (536) | -3 | -475 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, span2, best_of_N | DEAD |
| RG_0660 | RANGE-BREAK 11:00-11:15 ET (pre-range 10:45-11:00) | 4.28 | -373 [-595,-151] (317) | -461 [-914,-7] (648) | -435 [-764,-106] (470) | -59 | -693 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | DEAD |
| PE_0570_m | POST-EVENT 09:30 first-5-min move, REVERSAL, flat 10:05 | 4.83 | +40 [-355,+435] (564) | -825 [-1,559,-92] (1,048) | -624 [-1,181,-67] (795) | +169 | -93 | DEAD | beats_a, hold, span2 | DEAD |
| PE_0600_p | POST-EVENT 10:00 first-5-min move, CONTINUATION, flat 10:35 | 4.88 | -0 [-339,+338] (483) | +23 [-510,+556] (761) | -86 [-609,+437] (747) | +171 | -182 | DEAD | mean_up, beats_a, cost2x_pre, year_share, span2 | DEAD |
| ON1 | OVERNIGHT premium: buy 15:59 close, flat next-day 09:30 open (Mon-Thu entries) | 3.73 | +235 [-512,+982] (1,067) | +202 [-898,+1,302] (1,571) | +181 [-971,+1,333] (1,646) | +351 | +120 | DEAD | beats_a, beats_b, year_share, best_of_N | DEAD |
| F19 | B3_F19 own-series: 15:55 daily series RSI2<20|3-lower|IBS<0.2 above SMA200, hold to next 15:55 | 1.13 | +149 [-215,+512] (520) | +275 [-505,+1,055] (1,114) | -139 [-519,+242] (544) | +168 | +129 | DEAD | beats_a, beats_b, year_share, span2, best_of_N | DEAD |

'WF gross before cost' re-runs the same trades with zero slippage and zero fee (post-hoc diagnostic added after the FINAL scoring, not a gate): the gap to the WF column is the whole cost of the D3CX conservative basis.

## 2. By year, halves (weekly $ mean [CI] (MDE)); strict = mean > 0

| cell | 2023 (from Apr) | 2024 | 2025 | 2026 (to 02-06, ~5 wk) | pre-2025 half | post-2025 half | years strictly + | years pass (+ or >= -MDE) | halves both + |
|---|---|---|---|---|---|---|---|---|---|
| DR_0165_m | -562 [-1,046,-79] (690) | -100 [-566,+365] (665) | -20 [-515,+474] (707) | -42 [-615,+531] (819) | -296 [-635,+43] (484) | -23 [-477,+432] (649) | 0/4 | 4/4 | no |
| DR_0885_m | -882 [-1,539,-224] (939) | -148 [-799,+502] (929) | -28 [-759,+704] (1,045) | -492 [-2,293,+1,308] (2,572) | -459 [-930,+11] (672) | -76 [-767,+614] (986) | 0/4 | 4/4 | no |
| RG_0510 | -274 [-693,+145] (599) | +317 [-83,+716] (571) | +278 [-63,+620] (488) | -809 [-1,978,+360] (1,670) | +66 [-229,+362] (422) | +171 [-172,+513] (489) | 2/4 | 4/4 | yes |
| RG_0570 | +560 [+142,+977] (597) | -110 [-486,+266] (537) | +244 [-64,+552] (440) | +453 [-193,+1,098] (922) | +174 [-112,+460] (409) | +270 [-19,+558] (412) | 3/4 | 4/4 | yes |
| RG_0600 | -359 [-694,-24] (479) | -117 [-452,+218] (478) | -195 [-491,+102] (423) | -554 [-2,152,+1,044] (2,283) | -220 [-459,+20] (342) | -235 [-545,+75] (443) | 0/4 | 4/4 | no |
| RG_0630 | -465 [-771,-159] (437) | -139 [-521,+243] (545) | -361 [-716,-5] (508) | +923 [+13,+1,833] (1,299) | -277 [-533,-21] (366) | -234 [-584,+116] (500) | 1/4 | 3/4 | no |
| RG_0660 | -429 [-783,-76] (505) | -444 [-736,-152] (417) | -394 [-702,-86] (440) | +419 [-938,+1,775] (1,938) | -438 [-662,-214] (320) | -317 [-637,+3] (457) | 1/4 | 3/4 | no |
| PE_0570_m | -551 [-1,166,+64] (878) | +128 [-411,+667] (770) | -76 [-624,+472] (783) | -747 [-2,877,+1,383] (3,042) | -160 [-569,+249] (584) | -146 [-690,+397] (777) | 1/4 | 4/4 | no |
| PE_0600_p | +39 [-514,+593] (791) | -25 [-505,+455] (686) | -55 [-554,+444] (713) | -190 [-1,182,+802] (1,417) | +2 [-359,+363] (515) | -70 [-534,+395] (664) | 1/4 | 4/4 | no |
| ON1 | +231 [-957,+1,418] (1,697) | +760 [-250,+1,769] (1,442) | -500 [-1,629,+628] (1,612) | +1,696 [-133,+3,525] (2,613) | +536 [-231,+1,302] (1,095) | -282 [-1,341,+778] (1,514) | 3/4 | 4/4 | no |
| F19 | -53 [-393,+287] (486) | +69 [-467,+605] (766) | +109 [-363,+581] (674) | +377 [-2,124,+2,877] (3,572) | +17 [-322,+357] (485) | +139 [-350,+627] (698) | 3/4 | 4/4 | yes |

## 3. Placebos (effect = real minus mean of 40 draws, weekly $; CI by week bootstrap; rank = share of draws below the real mean)

| cell | (a) random direction, WFPRE | (a) WF | (b) random clock, WFPRE | (b) WF | (b) HOLD | (b) WF rank |
|---|---|---|---|---|---|---|
| DR_0165_m | +665 [+236,+1,063] r1.00 | +664 [+338,+976] r1.00 | +353 [-53,+725] r0.93 | +389 [+68,+703] r1.00 | +462 [-130,+961] r0.93 | 1.00 |
| DR_0885_m | +536 [+53,+1,095] r1.00 | +223 [-237,+672] r0.88 | +625 [+119,+1,227] r1.00 | +288 [-167,+758] r0.88 | -510 [-1,269,+370] r0.12 | 0.88 |
| RG_0510 | +719 [+446,+1,021] r1.00 | +650 [+409,+898] r1.00 | +887 [+597,+1,212] r1.00 | +801 [+538,+1,091] r1.00 | +574 [+101,+1,058] r0.97 | 1.00 |
| RG_0570 | +158 [-170,+424] r0.90 | +251 [-3,+493] r1.00 | +527 [+221,+779] r1.00 | +647 [+400,+886] r1.00 | +910 [+446,+1,340] r1.00 | 1.00 |
| RG_0600 | +109 [-145,+358] r0.78 | +33 [-185,+256] r0.72 | +407 [+162,+651] r1.00 | +342 [+121,+583] r1.00 | +177 [-302,+627] r0.80 | 1.00 |
| RG_0630 | -94 [-371,+214] r0.15 | +14 [-233,+246] r0.53 | +209 [-83,+516] r0.88 | +315 [+89,+547] r1.00 | +554 [+166,+950] r1.00 | 1.00 |
| RG_0660 | -17 [-262,+212] r0.38 | -56 [-270,+143] r0.38 | +190 [-48,+444] r0.85 | +159 [-60,+380] r0.88 | +81 [-382,+529] r0.55 | 0.88 |
| PE_0570_m | +419 [-3,+853] r1.00 | +162 [-243,+517] r0.82 | +840 [+420,+1,267] r1.00 | +492 [+86,+876] r0.97 | -338 [-1,069,+407] r0.17 | 0.97 |
| PE_0600_p | +182 [-243,+580] r0.85 | +246 [-80,+574] r0.97 | +493 [+46,+887] r1.00 | +494 [+161,+833] r1.00 | +482 [-99,+966] r0.97 | 1.00 |
| ON1 | +430 [-491,+1,366] r0.85 | +428 [-285,+1,175] r0.80 | +243 [-255,+771] r0.85 | +243 [-229,+764] r0.90 | +237 [-746,+1,348] r0.72 | 0.90 |
| F19 | +136 [-256,+532] r0.70 | +168 [-199,+525] r0.88 | +131 [-198,+458] r0.85 | +134 [-193,+462] r0.85 | +138 [-550,+858] r0.70 | 0.85 |

Best-of-N p95 of the (b) WFPRE effect: N=33 (non-drift) $465; N=168 (drift, 56 clocks x 3 markets) $495.

## 4. Sibling replication and pooled index row (same cell definition run unchanged on the other two markets)

| cell | sibling A WF / HOLD / X | sibling B WF / HOLD / X | sibling(s) all three > 0 | pooled ES+RTY+YM WF $/wk [CI] (MDE) | pooled tier | pooled p (Bonferroni x11) |
|---|---|---|---|---|---|---|
| DR_0165_m | ES: -218 / -265 / -616 | YM: +352 / +35 / -317 | none | +101 [-885,+1,087] (1,408) | DEAD | 1.00 |
| DR_0885_m | ES: -282 / -1,119 / -719 | YM: -116 / -678 / -583 | none | -552 [-1,914,+810] (1,946) | DEAD | 1.00 |
| RG_0510 | ES: -104 / -156 / -281 | YM: +45 / -8 / -203 | none | +221 [-437,+879] (940) | DEAD | 1.00 |
| RG_0570 | ES: -225 / +171 / -121 | YM: +148 / +625 / +37 | YM | +28 [-554,+611] (833) | DEAD | 1.00 |
| RG_0600 | ES: -98 / -409 / -387 | YM: -85 / -159 / -359 | none | -379 [-920,+163] (774) | DEAD | 1.00 |
| RG_0630 | ES: -412 / -240 / -601 | YM: -248 / -38 / -363 | none | -900 [-1,555,-246] (935) | DEAD | 1.00 |
| RG_0660 | ES: -583 / -820 / -745 | YM: -98 / -127 / -270 | none | -1,054 [-1,596,-511] (775) | DEAD | 1.00 |
| PE_0570_m | ES: -437 / -457 / -435 | YM: +104 / +169 / -126 | none | -293 [-1,107,+521] (1,163) | DEAD | 1.00 |
| PE_0600_p | ES: -233 / -232 / -273 | YM: -146 / +112 / +60 | none | -379 [-1,148,+390] (1,098) | DEAD | 1.00 |
| ON1 | ES: +731 / +804 / +127 | YM: +62 / +166 / +47 | ES, YM | +1,028 [-1,279,+3,335] (3,296) | DEAD | 1.00 |
| F19 | ES: +247 / +660 / +369 | YM: -36 / +484 / +59 | ES | +359 [-504,+1,222] (1,233) | DEAD | 1.00 |

## 5. Link to the live stack (span 2023-04-01..2026-02-06, 149 weeks; stack mean $42,397/wk, SD $135,594, Sharpe 2.25; its 20 worst weeks sum $-3,589,562)

| cell | weekly corr to stack | cell $ in stack's 20 worst weeks (at $1k risk) | same scaled so cell weekly SD = 20 percent of stack SD | scaled weekly mean | marginal stack Sharpe at that scale |
|---|---|---|---|---|---|
| DR_0165_m | +0.00 | -3,978 | -63,278 (k=16) | -3,050 | -0.204 |
| DR_0885_m | -0.04 | +396 | +4,366 (k=11) | -3,457 | -0.208 |
| RG_0510 | +0.02 | +9,777 | +189,071 (k=19) | +2,077 | +0.055 |
| RG_0570 | +0.03 | -179 | -3,728 (k=21) | +4,417 | +0.172 |
| RG_0600 | +0.01 | -2,819 | -64,137 (k=23) | -5,169 | -0.319 |
| RG_0630 | +0.09 | -8,111 | -169,694 (k=21) | -5,485 | -0.362 |
| RG_0660 | +0.05 | -11,992 | -282,172 (k=24) | -9,265 | -0.542 |
| PE_0570_m | +0.03 | -6,934 | -92,070 (k=13) | -2,067 | -0.165 |
| PE_0600_p | +0.01 | -6,580 | -100,335 (k=15) | -392 | -0.068 |
| ON1 | +0.14 | -4,999 | -34,590 (k=7) | +1,529 | -0.024 |
| F19 | -0.12 | +5,843 | +90,149 (k=15) | +999 | +0.062 |

The stack link is shown for every cell for completeness; with no cell reaching CONFIRMED there is no portfolio add. Positive 'worst-20' P&L from a negative-edge cell is noise, not diversification.

## 6. Top cells regardless of verdict (ranked by WF t = mean / SE)

- **RG_0510** (RANGE-BREAK 08:30-08:45 ET (pre-range 08:15-08:30)): WF +280 [+21,+539] (370), t +2.12; HOLD +35 [-479,+550] (735); X -311 [-737,+116] (609); tier DEAD; failed gates year_share, span2; years strictly positive 2/4; pooled WF +221 (p 1.00). Weekly MDE 370: the cell is inside its MDE.
- **RG_0570** (RANGE-BREAK 09:30-09:45 ET (pre-range 09:15-09:30)): WF +106 [-133,+345] (341), t +0.87; HOLD +330 [-123,+782] (646); X +464 [+56,+873] (584); tier DEAD; failed gates beats_a, cost2x_pre, year_share; years strictly positive 3/4; pooled WF +28 (p 1.00). Weekly MDE 341: the cell is inside its MDE.
- **F19** (B3_F19 own-series: 15:55 daily series RSI2<20|3-lower|IBS<0.2 above SMA200, hold to next 15:55): WF +149 [-215,+512] (520), t +0.80; HOLD +275 [-505,+1,055] (1,114); X -139 [-519,+242] (544); tier DEAD; failed gates beats_a, beats_b, year_share, span2, best_of_N; years strictly positive 3/4; pooled WF +359 (p 1.00). Weekly MDE 520: the cell is inside its MDE.

## 7. Notes and disclosures
- Print-level stop/limit fill checks (ES/RTY trades files on disk) were NOT run: no cell is CONFIRMED or reaches the CANDIDATE tier; YM has no trades file.
- Range cells that trigger on both sides of the pre-range inside one minute are skipped (counted in orders but not trades). ON1 excludes Friday entries (no weekend hold); F19 holds Friday to Monday exactly as its spec.
- Placebo (b) for ON1 (random entry minute, same exit) is a weak placebo by construction (the premium accrues overnight whatever the entry minute); for F19 it is random days above the SMA200 with the real count (regime control).
- The prereg predictions for the range cells state both a cost arithmetic (about -$400 to -$650/wk at zero edge) and a wider range (-$200 to +$100); the realised numbers are reported against the arithmetic in the WF-gross column. Prereg smoke-test sums and the F19 NaN-rolling fix are disclosed in the prereg.
- UNTOUCHED never read; HOLD includes the part of 2025-07..2026-02 that the maps also saw, but the clocks here were chosen on WFPRE alone.
