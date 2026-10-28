# DS3_DIV_ES - own-clock window rules and overnight-hold cells on ES (D3DVE, 2026-10-28)

**Verdict: 0 CONFIRMED, 0 CANDIDATE, 11 DEAD of 11 registered cells.** ES fee $4.84 RT NT-published (solid): verdicts can reach PASS/CONFIRMED. Bars-only (class R2, D3CX conservative fills). Research only; no live/execution/chart change, no purchase, UNTOUCHED (after 2026-02-06) never read. Prereg `l2vast/ds3/prereg/DVE_ES_prereg.md` sha256 `e80fb566b89ebbb81d161952940178dded723e707d58665970d6767e7f8f04a5` (logged in DECISIONS.md before scoring); pre-holdout text DVE_ES_pre.md; one holdout look logged (track DS3_DVE_ES, X span read at the same look). Code l2vast/ds3/code/dve/, outputs l2vast/ds3/out/dve/.

Windows (trade date): selection span used to pick the clocks = WFPRE 2024-02-01..2025-06-30; HOLD 2025-07-01..2026-02-06 (UNTOUCHED boundary); WF = WFPRE+HOLD; X = 2023-04-01..2024-01-31. All $ are weekly means at $1,000 risk per trade, 95% CI and MDE (2.8 SE) in brackets. The DS3_DIV_1_MAPS lists were not used for the window choice (they saw X and part of HOLD); only their rule types. The two drift windows were scanned over 56 clocks per market and judged against a best-of-168 null.

## 1. Verdict table (primary cells)

| cell | rule | tr/wk | WF $/wk [CI] (MDE) | HOLD $/wk [CI] (MDE) | X $/wk [CI] (MDE) | WF gross before cost | WF 2x cost | tier | failed gates | final label |
|---|---|---|---|---|---|---|---|---|---|---|
| DR_0165_m | DRIFT 02:45-03:00 ET SHORT | 4.91 | -218 [-583,+148] (522) | -265 [-1,051,+522] (1,124) | -616 [-1,123,-108] (725) | +718 | -1,154 | DEAD | mean_up, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | DEAD |
| DR_0930_m | DRIFT 15:30-15:45 ET SHORT | 4.72 | +133 [-319,+586] (647) | -331 [-911,+248] (827) | -71 [-576,+434] (721) | +492 | -225 | DEAD | cost2x_pre, year_share, hold, span2 | DEAD |
| RG_0510 | RANGE-BREAK 08:30-08:45 ET (pre-range 08:15-08:30) | 4.04 | -104 [-376,+168] (389) | -156 [-637,+325] (687) | -281 [-704,+142] (604) | +320 | -641 | DEAD | mean_up, cost2x_pre, year_share, hold, span2 | DEAD |
| RG_0570 | RANGE-BREAK 09:30-09:45 ET (pre-range 09:15-09:30) | 4.68 | -225 [-544,+93] (455) | +171 [-372,+714] (776) | -121 [-406,+163] (406) | +106 | -585 | DEAD | mean_up, beats_a, cost2x_pre, year_share, span2, best_of_N | DEAD |
| RG_0600 | RANGE-BREAK 10:00-10:15 ET (pre-range 09:45-10:00) | 4.32 | -98 [-347,+150] (355) | -409 [-846,+28] (625) | -387 [-733,-40] (495) | +212 | -406 | DEAD | cost2x_pre, year_share, hold, span2 | DEAD |
| RG_0630 | RANGE-BREAK 10:30-10:45 ET (pre-range 10:15-10:30) | 4.27 | -412 [-684,-140] (388) | -240 [-744,+264] (720) | -601 [-935,-267] (477) | -31 | -845 | DEAD | mean_up, beats_a, cost2x_pre, year_share, hold, span2, best_of_N | DEAD |
| RG_0660 | RANGE-BREAK 11:00-11:15 ET (pre-range 10:45-11:00) | 4.21 | -583 [-822,-343] (342) | -820 [-1,229,-412] (584) | -745 [-1,048,-441] (434) | -160 | -1,033 | DEAD | mean_up, beats_a, cost2x_pre, year_share, hold, span2, best_of_N | DEAD |
| PE_0570_p | POST-EVENT 09:30 first-5-min move, CONTINUATION, flat 10:05 | 4.86 | -110 [-498,+278] (554) | +165 [-470,+800] (907) | -108 [-703,+487] (850) | +208 | -364 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, span2, best_of_N | DEAD |
| PE_0600_p | POST-EVENT 10:00 first-5-min move, CONTINUATION, flat 10:35 | 4.79 | -233 [-566,+100] (476) | -232 [-839,+376] (867) | -273 [-748,+201] (678) | +75 | -515 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | DEAD |
| ON1 | OVERNIGHT premium: buy 15:59 close, flat next-day 09:30 open (Mon-Thu entries) | 3.73 | +731 [-81,+1,543] (1,160) | +804 [-220,+1,829] (1,464) | +127 [-815,+1,070] (1,347) | +887 | +575 | DEAD | beats_a, beats_b, year_share, hold, best_of_N | DEAD |
| F19 | B3_F19 own-series: 15:55 daily series RSI2<20|3-lower|IBS<0.2 above SMA200, hold to next 15:55 | 1.14 | +247 [-138,+632] (550) | +660 [-108,+1,429] (1,098) | +369 [-132,+871] (717) | +275 | +218 | DEAD | beats_a, beats_b, best_of_N | DEAD |

'WF gross before cost' re-runs the same trades with zero slippage and zero fee (post-hoc diagnostic added after the FINAL scoring, not a gate): the gap to the WF column is the whole cost of the D3CX conservative basis.

## 2. By year, halves (weekly $ mean [CI] (MDE)); strict = mean > 0

| cell | 2023 (from Apr) | 2024 | 2025 | 2026 (to 02-06, ~5 wk) | pre-2025 half | post-2025 half | years strictly + | years pass (+ or >= -MDE) | halves both + |
|---|---|---|---|---|---|---|---|---|---|
| DR_0165_m | -585 [-1,090,-80] (721) | -415 [-862,+32] (639) | -7 [-610,+595] (860) | -833 [-2,061,+394] (1,753) | -487 [-820,-153] (476) | -93 [-659,+473] (808) | 0/4 | 4/4 | no |
| DR_0930_m | -19 [-550,+512] (759) | +361 [-246,+968] (867) | -71 [-756,+613] (978) | -598 [-1,729,+534] (1,616) | +200 [-216,+615] (594) | -127 [-762,+508] (907) | 1/4 | 4/4 | no |
| RG_0510 | -320 [-766,+126] (637) | +163 [-252,+578] (593) | -284 [-610,+42] (466) | -749 [-2,224,+725] (2,106) | -42 [-349,+265] (439) | -337 [-668,-7] (472) | 1/4 | 4/4 | no |
| RG_0570 | -124 [-442,+194] (455) | -517 [-949,-84] (618) | +78 [-353,+509] (616) | -191 [-1,085,+703] (1,277) | -350 [-635,-65] (407) | +51 [-349,+451] (571) | 1/4 | 4/4 | no |
| RG_0600 | -417 [-778,-55] (516) | -87 [-439,+264] (502) | -153 [-500,+193] (495) | +260 [-983,+1,504] (1,777) | -227 [-482,+28] (364) | -113 [-453,+227] (486) | 1/4 | 4/4 | no |
| RG_0630 | -616 [-952,-280] (480) | -410 [-791,-29] (545) | -382 [-778,+13] (566) | -688 [-1,626,+250] (1,340) | -497 [-759,-236] (373) | -421 [-794,-48] (533) | 0/4 | 3/4 | no |
| RG_0660 | -756 [-1,058,-454] (432) | -506 [-881,-131] (536) | -679 [-1,003,-354] (464) | -375 [-890,+139] (735) | -612 [-863,-361] (359) | -659 [-960,-359] (429) | 0/4 | 2/4 | no |
| PE_0570_p | +18 [-627,+664] (922) | -399 [-946,+148] (781) | +125 [-411,+660] (765) | -433 [-2,370,+1,503] (2,766) | -222 [-639,+195] (596) | +69 [-456,+593] (749) | 2/4 | 4/4 | no |
| PE_0600_p | -108 [-593,+377] (693) | -510 [-1,011,-8] (716) | -103 [-535,+330] (618) | -4 [-1,740,+1,731] (2,479) | -339 [-694,+16] (507) | -94 [-522,+333] (610) | 0/4 | 4/4 | no |
| ON1 | +236 [-763,+1,235] (1,427) | +1,160 [+172,+2,147] (1,411) | +149 [-1,153,+1,451] (1,860) | +760 [-150,+1,669] (1,299) | +768 [+56,+1,480] (1,017) | +215 [-978,+1,407] (1,704) | 4/4 | 4/4 | yes |
| F19 | +400 [-145,+945] (779) | +67 [-517,+652] (835) | +300 [-196,+796] (708) | +1,222 [+106,+2,338] (1,594) | +208 [-199,+616] (582) | +400 [-70,+871] (672) | 4/4 | 4/4 | yes |

## 3. Placebos (effect = real minus mean of 40 draws, weekly $; CI by week bootstrap; rank = share of draws below the real mean)

| cell | (a) random direction, WFPRE | (a) WF | (b) random clock, WFPRE | (b) WF | (b) HOLD | (b) WF rank |
|---|---|---|---|---|---|---|
| DR_0165_m | +819 [+426,+1,211] r1.00 | +747 [+392,+1,116] r1.00 | +380 [-29,+782] r0.93 | +315 [-47,+661] r0.97 | +152 [-595,+893] r0.68 | 0.97 |
| DR_0930_m | +619 [+32,+1,229] r0.97 | +423 [-28,+855] r0.97 | +928 [+360,+1,535] r1.00 | +725 [+281,+1,160] r1.00 | +227 [-296,+803] r0.68 | 1.00 |
| RG_0510 | +360 [+81,+667] r1.00 | +333 [+82,+587] r1.00 | +819 [+513,+1,163] r1.00 | +777 [+517,+1,066] r1.00 | +654 [+206,+1,131] r1.00 | 1.00 |
| RG_0570 | -34 [-383,+326] r0.47 | +97 [-173,+387] r0.80 | +453 [+101,+855] r1.00 | +622 [+331,+931] r1.00 | +999 [+523,+1,488] r1.00 | 1.00 |
| RG_0600 | +402 [+91,+691] r0.97 | +276 [+11,+529] r0.97 | +905 [+609,+1,169] r1.00 | +759 [+510,+1,018] r1.00 | +392 [-74,+838] r1.00 | 1.00 |
| RG_0630 | +4 [-333,+318] r0.53 | +44 [-218,+316] r0.65 | +407 [+74,+743] r1.00 | +450 [+183,+736] r1.00 | +535 [-8,+1,102] r1.00 | 1.00 |
| RG_0660 | -92 [-368,+201] r0.25 | -138 [-397,+108] r0.20 | +359 [+98,+638] r0.95 | +266 [+31,+508] r0.95 | +38 [-331,+418] r0.60 | 0.95 |
| PE_0570_p | +114 [-315,+590] r0.65 | +193 [-197,+581] r0.80 | +443 [-14,+951] r0.97 | +528 [+144,+929] r1.00 | +711 [+50,+1,307] r0.97 | 1.00 |
| PE_0600_p | +102 [-296,+506] r0.78 | +104 [-227,+417] r0.78 | +384 [-21,+797] r1.00 | +352 [+17,+676] r1.00 | +268 [-368,+899] r0.72 | 1.00 |
| ON1 | +783 [-410,+1,906] r0.97 | +801 [-71,+1,601] r0.97 | -114 [-933,+701] r0.38 | -93 [-667,+528] r0.38 | -41 [-698,+696] r0.42 | 0.38 |
| F19 | +146 [-260,+531] r0.70 | +293 [-112,+640] r0.90 | -49 [-387,+301] r0.45 | +104 [-218,+407] r0.78 | +459 [-179,+1,113] r0.95 | 0.78 |

Best-of-N p95 of the (b) WFPRE effect: N=33 (non-drift) $465; N=168 (drift, 56 clocks x 3 markets) $495.

## 4. Sibling replication and pooled index row (same cell definition run unchanged on the other two markets)

| cell | sibling A WF / HOLD / X | sibling B WF / HOLD / X | sibling(s) all three > 0 | pooled ES+RTY+YM WF $/wk [CI] (MDE) | pooled tier | pooled p (Bonferroni x11) |
|---|---|---|---|---|---|---|
| DR_0165_m | RTY: -33 / -58 / -570 | YM: +352 / +35 / -317 | none | +101 [-885,+1,087] (1,408) | DEAD | 1.00 |
| DR_0930_m | RTY: +78 / -342 / +53 | YM: +51 / -360 / -1 | none | +262 [-989,+1,514] (1,787) | DEAD | 1.00 |
| RG_0510 | RTY: +280 / +35 / -311 | YM: +45 / -8 / -203 | none | +221 [-437,+879] (940) | DEAD | 1.00 |
| RG_0570 | RTY: +106 / +330 / +464 | YM: +148 / +625 / +37 | RTY, YM | +28 [-554,+611] (833) | DEAD | 1.00 |
| RG_0600 | RTY: -195 / -326 / -299 | YM: -85 / -159 / -359 | none | -379 [-920,+163] (774) | DEAD | 1.00 |
| RG_0630 | RTY: -240 / +24 / -309 | YM: -248 / -38 / -363 | none | -900 [-1,555,-246] (935) | DEAD | 1.00 |
| RG_0660 | RTY: -373 / -461 / -435 | YM: -98 / -127 / -270 | none | -1,054 [-1,596,-511] (775) | DEAD | 1.00 |
| PE_0570_p | RTY: -219 / +175 / +342 | YM: -295 / -529 / -107 | none | -624 [-1,384,+135] (1,085) | DEAD | 1.00 |
| PE_0600_p | RTY: -0 / +23 / -86 | YM: -146 / +112 / +60 | none | -379 [-1,148,+390] (1,098) | DEAD | 1.00 |
| ON1 | RTY: +235 / +202 / +181 | YM: +62 / +166 / +47 | RTY, YM | +1,028 [-1,279,+3,335] (3,296) | DEAD | 1.00 |
| F19 | RTY: +149 / +275 / -139 | YM: -36 / +484 / +59 | none | +359 [-504,+1,222] (1,233) | DEAD | 1.00 |

## 5. Link to the live stack (span 2023-04-01..2026-02-06, 149 weeks; stack mean $42,397/wk, SD $135,594, Sharpe 2.25; its 20 worst weeks sum $-3,589,562)

| cell | weekly corr to stack | cell $ in stack's 20 worst weeks (at $1k risk) | same scaled so cell weekly SD = 20 percent of stack SD | scaled weekly mean | marginal stack Sharpe at that scale |
|---|---|---|---|---|---|
| DR_0165_m | -0.04 | -4,215 | -60,793 (k=14) | -4,857 | -0.281 |
| DR_0930_m | -0.06 | -740 | -9,049 (k=12) | +904 | +0.031 |
| RG_0510 | -0.14 | +16,086 | +306,852 (k=19) | -2,998 | -0.142 |
| RG_0570 | +0.10 | +1,186 | +21,438 (k=18) | -3,547 | -0.268 |
| RG_0600 | -0.08 | -7,603 | -161,397 (k=21) | -3,909 | -0.216 |
| RG_0630 | +0.09 | -7,193 | -144,598 (k=20) | -9,464 | -0.565 |
| RG_0660 | +0.02 | -13,609 | -307,770 (k=23) | -14,347 | -0.797 |
| PE_0570_p | -0.02 | +2,200 | +29,160 (k=13) | -1,462 | -0.111 |
| PE_0600_p | +0.07 | -10,130 | -160,799 (k=16) | -3,909 | -0.274 |
| ON1 | +0.22 | +7,012 | +47,796 (k=7) | +3,802 | +0.058 |
| F19 | -0.06 | +10,223 | +143,305 (k=14) | +3,989 | +0.193 |

The stack link is shown for every cell for completeness; with no cell reaching CONFIRMED there is no portfolio add. Positive 'worst-20' P&L from a negative-edge cell is noise, not diversification.

## 6. Top cells regardless of verdict (ranked by WF t = mean / SE)

- **ON1** (OVERNIGHT premium: buy 15:59 close, flat next-day 09:30 open (Mon-Thu entries)): WF +731 [-81,+1,543] (1,160), t +1.76; HOLD +804 [-220,+1,829] (1,464); X +127 [-815,+1,070] (1,347); tier DEAD; failed gates beats_a, beats_b, year_share, hold, best_of_N; years strictly positive 4/4; pooled WF +1,028 (p 1.00). Weekly MDE 1,160: the cell is inside its MDE.
- **F19** (B3_F19 own-series: 15:55 daily series RSI2<20|3-lower|IBS<0.2 above SMA200, hold to next 15:55): WF +247 [-138,+632] (550), t +1.26; HOLD +660 [-108,+1,429] (1,098); X +369 [-132,+871] (717); tier DEAD; failed gates beats_a, beats_b, best_of_N; years strictly positive 4/4; pooled WF +359 (p 1.00). Weekly MDE 550: the cell is inside its MDE.
- **DR_0930_m** (DRIFT 15:30-15:45 ET SHORT): WF +133 [-319,+586] (647), t +0.58; HOLD -331 [-911,+248] (827); X -71 [-576,+434] (721); tier DEAD; failed gates cost2x_pre, year_share, hold, span2; years strictly positive 1/4; pooled WF +262 (p 1.00). Weekly MDE 647: the cell is inside its MDE.

## 7. Notes and disclosures
- Print-level stop/limit fill checks (ES/RTY trades files on disk) were NOT run: no cell is CONFIRMED or reaches the CANDIDATE tier; YM has no trades file.
- Range cells that trigger on both sides of the pre-range inside one minute are skipped (counted in orders but not trades). ON1 excludes Friday entries (no weekend hold); F19 holds Friday to Monday exactly as its spec.
- Placebo (b) for ON1 (random entry minute, same exit) is a weak placebo by construction (the premium accrues overnight whatever the entry minute); for F19 it is random days above the SMA200 with the real count (regime control).
- The prereg predictions for the range cells state both a cost arithmetic (about -$400 to -$650/wk at zero edge) and a wider range (-$200 to +$100); the realised numbers are reported against the arithmetic in the WF-gross column. Prereg smoke-test sums and the F19 NaN-rolling fix are disclosed in the prereg.
- UNTOUCHED never read; HOLD includes the part of 2025-07..2026-02 that the maps also saw, but the clocks here were chosen on WFPRE alone.
