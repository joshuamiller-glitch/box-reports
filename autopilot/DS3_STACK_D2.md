# DS3_STACK_D2 - opposite-direction overlap between books: frequency, as-traded P&L, and three treatments (D3SKD2, T-STACK addendum D2), 2026-10-28

Research only; no live / execution / chart change. Prereg `l2vast/ds3/prereg/D3SKD2_prereg.md` sha256 `0a3d7abd7eeb8367dec537bd4b27222ce670e1e6743bf623274cea08a08a5a40` (DECISIONS.md 2026-10-28T17:56Z, before any treatment cell was scored), 16 cells, F handoff = 60 (this section adds 16). Pre-holdout text `autopilot/DS3_STACK_D2_PREHOLD.md` (PRE only; HOLD and X read once, looks logged D3SKD2_GD, D3SKD2_GD_SPAN2). Code `l2vast/ds3/code/stk_d2/`, outputs `l2vast/ds3/out/stk_d2/` (step1.json, pre_results.json, final_results.json, final_series.pkl, pre_weekly_series.parquet). Data cut: label days after 2026-02-06 are masked before the engine (UNTOUCHED never scored); the 2026-10-28 example date is outside the window and was not read. Windows: PRE 2024-02..2025-06 (75 wk), HOLD 2025-07-01..2026-02-06 (32 wk), X 2023-04..2024-01 (44 wk), WF 2024-02..2026-02-06 (106 wk). MDE = 2.8 SD_diff/sqrt(n) of the paired delta.

## Verdict
**Overlap is common and, taken as a whole, roughly neutral; the only reliable dollars are execution costs, and they are small. No treatment that changes the trades helps.** Of 16 cells: the eight B/C cells are all DEAD; the eight A cells (net-only execution) pass the V2 gates (U5m capped at LEAD) because they are deterministic cost savings (G4 n/a), not because a signal was found.

**1. Frequency (as traded, WF 2024-02..2026-02-06, 106 weeks).** U6 (live DS3 stack): opposite positions are open together 2,158 min/wk (36 h/wk, 38% of the time anything is open), time-weighted offset 10.1 lots (max 23.8) inside 36.0 gross lots; 26.3% of all entries are made into an opposite open position (PRE 27.0%, HOLD 24.8%, 2023 span 34.7%; by year 2024 30%, 2025 24%, 2026 22%). U3 (KB10 SM10 PE8): 1,498 min/wk, offset 8.8 (max 10), 18.0% of entries; U5 (KB5 SM7 PE5): same timing, offset 5.4 (max 7). Heaviest pairs on U6: KB-PE 1,093 min/wk, ST-KB 1,036, WT-KB 902, HM-KB 858. Peak gross = peak net = 50.0 (U6), 28 (U3), 17 (U5): the contract cap binds at same-direction pile-ups, not in overlaps, so netting does not relieve it. The user's example (K5 short 8 while P5 long 14): K5/P5 map to KB5/PE5, which hold 5 lots each here, so an 8-vs-14 offset is not reproducible with KB5/PE5 as defined (8 and 14 match the DN8 and the 14-lot scale); that date is after 2026-02-06 and was not read.

**2. As traded.** U6 WF: entries that create an overlap earn +$6,365/wk [-3,214,+15,983] (MDE 13,694) = +$176 per entry vs +$402 for all other entries (+$24 vs +$55 per lot); hit rate identical (54%). The mark-to-market of the net exposure during overlap is +$439/wk [-7,722,+8,278] (MDE 11,721): the hedged lots earn zero gross by construction. Cost of the offset lots (commission $4.84 + slippage $10.00 per contract round trip): $1,131/wk commission, $3,467/wk with slippage (7.4% of the $47,055 base), versus $4,882/wk for all commission. U3: $439 / $1,345 per wk; U5: $268 / $823.

**3. Treatments (paired by week and by day vs the unchanged stack, exact lock engine).** Dollars per week of the overlap state, WF, U6 (MDE beside the mean): A1 net-only execution, exact 1-s order netting: **+$221/wk [+203,+240] (MDE 27)** - a futures account already nets by itself, so the only saving is orders that land in the same second (11 same-second opposite entries in 19,069 rows; 60-s window adds nothing: $225/wk PRE); with slippage counted +$682/wk PRE. A2 literal net-only bound (commission only on carried lots): +$1,131/wk [+1,080,+1,180] (MDE 71), +$3,467 with slippage; it is an upper bound, not achievable, because the real position must follow the signals (carrying only the larger bracket changes the exposure) - the virtual P&L would not be earned. B skip later: raw -$9,343/wk [-23,311,+4,639] (MDE 20,177), lot-matched +$890 [-16,778,+18,798]; C dead flip: raw -$9,212/wk [-25,175,+6,374] (MDE 22,458), LM +$5,890 [-14,941,+26,242]. On U3: A1 +68 (MDE 14), A2 +439, B raw -8,730 [-16,847,-455] (MDE 11,703) (CI excludes 0), C raw -6,124 [-15,386,+2,485]; U5: A1 +41, A2 +268, B -4,964 [-9,855,+54], C -3,273. U5m (MAPPED DN8; cap LEAD): A1 +101, A2 +418, B -4,345, C -1,502 raw; C LM +9,684 [+825,+18,422] (MDE 12,703) is the single LM interval above zero, but PRE LM +5,236 / X LM -231, lot-matched maxDD worse in PRE (+165k) and X (+135k) and HOLD worst week worse (-23.6k), placebo ranks 0.91/0.61 in PRE: fails G3, G4, G6.
**Best treatment.** Pre-registered rule (highest PRE raw mean delta) picks A2 in every set (the bound). The best ACHIEVABLE treatment is A1 (net the orders): +$221/wk on the 6-book stack, +$68 on KB10/SM10/PE8, +$41 on KB5/SM7/PE5 (+$101 on the mapped DS5), i.e. 0.5% of the weekly mean. The two treatments that change trades (skip-later B, dead flip C) cost about 20% of weekly income raw on U6 (-$9.3k/wk, inside its MDE of 20-22k: inconclusive, not proven harmful) and do nothing lot-matched (LM CIs span 0 in every cell except U5m_C); both increase lot-matched maxDD and worst week (U6_B LM WF worst-20-weeks -$886k, U6_C -$488k vs base -$3.53M: they remove more in good weeks than they save in bad ones; raw trade-off U6_B +$57k saved in the 20 worst weeks vs -$1.85M given up elsewhere, U6_C +$660k vs -$2.64M). Placebos: U6_B LM rank pair/dir PRE 0.17/0.36, HOLD 0.97/0.88; U6_C 0.86/0.99 PRE and 0.63/0.52 HOLD: not distinguishable from random pairing of co-open entries.
**2023 span (X):** A1/A2 positive; B/C raw -$18k..-$23k/wk U6 (U6_C X LM -23,630 [-50,416,+2,571]); every B/C cell is negative on X. By year: A positive every year; B/C change sign across years (U6_C LM 2024 +609k, 2025 -246k, 2026 +261k).
**DS5.** U5 (KB5 SM7 PE5, exact) is run; U5m adds DN8 on the MAPPED basis (stop-entry booked at the stop price, DN rows through the lock engine: 2.0% below the te_core.run_rows total, 39 of ~950 days differ) and is capped at LEAD; MV4 is a hybrid with no 1-s legs and is not run, so no number here is the live DS5. K5/P5 = KB5/PE5.
**Cells counted for F: 16** (4 sets x 4 treatments; 200+200 placebo draws per B/C cell, 200 per A1; F handoff total 60 assumed, this section would add 16). HOLD p <= 0.05/60 = 0.000833 is met only by the deterministic A cells (accounting, not a signal). PRE-selected rule to carry into F: **A1 order netting as a pure cost line (about +$220/wk on the stack, nothing else); do not stack B or C.**

## Disclosures (read these)
- Before the prereg was written: base reproduction (U6 PRE mean 44,127.1/wk = D3SKD; U3 PRE 41,697 and WF 42,928 = D3SKC2), the step-1 overlap counts (frequency, share, pairs; no treatment P&L), and one identity test of the DN mapped rows (WF total 2.0% below te_core.run_rows; 39 of ~950 days differ, the two engines group days differently on DN rows). No treatment cell was scored.
- The first PRE launch crashed in step 2 (a numpy-array indexing bug) after the engine passes had finished; only 'act' timing lines were logged, no numbers were printed or read; the fix touched the reporting line only and the PRE run was repeated with identical definitions. The pre-holdout text was written from the repeated run and logged before HOLD and X were computed.
- Data cut 2026-02-06 (the standing UNTOUCHED rule): D3SKD read to 2026-10-16, so HOLD here is 32 weeks (not 68) and WF is 106 weeks; absolute numbers are not comparable with DS3_STACK_D.
- Implementation simplifications (all in the prereg): a skipped (B) or closed (C) book stays flat until its next base signal (shadowed signals are not recovered); C closes at the later entry second + 1 (engine flatten convention); B/C converge exactly by pass 2 (pass 3 minus pass 2 = 0); fixed-lot sets have no sweep cost; 2x cost reuses the 1x multipliers/forced exits; A1 nets only orders in the same 1-s bucket and counts commission $2.42/contract/side (+ slippage $5.00 as a sensitivity); A2 is a bound (see verdict); PRE-edge tie order KB, SM, PE, DN, ST, HM, WT; the U5m MV4 hybrid is absent.
- The F handoff weekly series for the combine step: out/stk_d2/pre_weekly_series.parquet (PRE-only, raw and LM per cell, plus the base per set).


## Universes and what was run
| id | set | status |
|---|---|---|
| U6 | DS3 stack of DS3_DIV2_A_AUDIT: ST10 HM10 WT7 + KB/SM/PE at 10 x frozen monthly weights | exact (1-s path, per-book lock engine; base PRE mean 44,127/wk = D3SKD base) |
| U3 | DS3 set KB10 SM10 PE8 fixed lots | exact (base PRE 41,697/wk = D3SKC2 base) |
| U5 | DS5 books that have 1-s legs, KB5 SM7 PE5. The user's K5 and P5 map to KB5 and PE5 (N5 = DN, U5 = SM); DN and MV have no 1-s legs | exact, but NOT the live DS5 (DN8 and MV4 absent) |
| U5m | U5 + DN8 on the MAPPED basis (stop-entry booked at the stop price, no direct replay) | MAPPED approximation of 25 of 29 lots; MV4 (hybrid, no entry/exit legs) not run; every U5m verdict capped at LEAD |

## 1. How often opposite-direction positions overlap (as traded, base stack, 1-s path)
Overlap state = seconds with long and short lots open at once (any two books). Offset lots = min(long lots, short lots). Share of entries = entries made while another book holds an opposite open position, over all entries.

| set | window | weeks | overlap min/wk | share of open time with both sides | offset lots (time-wtd mean / max) | gross lots in overlap | entries | share into an opposite position | into same-direction position | opposite lots open at entry / offset lots |
|---|---|---|---|---|---|---|---|---|---|---|
| U6 | WFPRE | 75 | 2,234 | 40% | 10.3 / 23.8 | 36.7 | 10,205 | 27.0% | 70% | 14.1 / 6.6 |
| U6 | HOLD | 32 | 1,913 | 34% | 9.6 / 21.9 | 34.1 | 4,343 | 24.8% | 70% | 13.9 / 6.2 |
| U6 | X | 44 | 3,246 | 52% | 11.7 / 23.6 | 39.6 | 4,521 | 34.7% | 75% | 15.7 / 7.1 |
| U6 | WF | 106 | 2,158 | 38% | 10.1 / 23.8 | 36.0 | 14,548 | 26.3% | 70% | 14.1 / 6.5 |
| U3 | WFPRE | 75 | 1,628 | 31% | 8.8 / 10.0 | 23.0 | 4,360 | 18.7% | 42% | 11.1 / 8.7 |
| U3 | HOLD | 32 | 1,145 | 22% | 8.8 / 10.0 | 23.1 | 1,781 | 16.3% | 42% | 11.2 / 8.7 |
| U3 | X | 44 | 2,422 | 40% | 8.7 / 10.0 | 23.6 | 2,008 | 24.6% | 46% | 11.1 / 8.7 |
| U3 | WF | 106 | 1,498 | 29% | 8.8 / 10.0 | 23.0 | 6,141 | 18.0% | 42% | 11.1 / 8.7 |
| U5 | WFPRE | 75 | 1,628 | 31% | 5.4 / 7.0 | 13.6 | 4,360 | 18.7% | 42% | 6.4 / 5.3 |
| U5 | HOLD | 32 | 1,145 | 22% | 5.5 / 7.0 | 13.6 | 1,781 | 16.3% | 42% | 6.6 / 5.3 |
| U5 | X | 44 | 2,422 | 40% | 5.4 / 7.0 | 14.0 | 2,008 | 24.6% | 46% | 6.4 / 5.3 |
| U5 | WF | 106 | 1,498 | 29% | 5.4 / 7.0 | 13.6 | 6,141 | 18.0% | 42% | 6.5 / 5.3 |

By year (WF + 2023 span X is the X row above):

| set | year | weeks | overlap min/wk | share of entries into an opposite position | offset lots (tw mean) |
|---|---|---|---|---|---|
| U6 | 2024 | 49 | 2,566 | 29.8% | 10.9 |
| U6 | 2025 | 53 | 1,803 | 24.1% | 9.2 |
| U6 | 2026 | 6 | 1,248 | 21.9% | 8.4 |
| U3 | 2024 | 49 | 1,927 | 21.6% | 8.8 |
| U3 | 2025 | 53 | 1,124 | 15.3% | 8.8 |
| U3 | 2026 | 6 | 799 | 16.5% | 8.8 |
| U5 | 2024 | 49 | 1,927 | 21.6% | 5.4 |
| U5 | 2025 | 53 | 1,124 | 15.3% | 5.4 |
| U5 | 2026 | 6 | 799 | 16.5% | 5.5 |

Peak concurrent contracts as traded: U6 gross 50.0 / net 50.0; U3 28.0 / 28.0; U5 17.0 / 17.0 (gross counts every bracket, net is the account position; long and short are both open at the same time only because each book holds its own bracket). Entries in exactly the same second as an opposite position of another book (coincident): U6 11 of 19,069, U3 0, U5 0.

### By book pair, U6 (overlap min/wk and time-weighted offset lots; share of each side's entries that enter into the other's opposite open position, WF)
| pair | PRE min/wk | HOLD min/wk | X min/wk | WF min/wk | WF offset lots (mean / max) | WF share: first into second | WF share: second into first |
|---|---|---|---|---|---|---|---|
| KB-PB | 1,213 | 777 | 1,744 | 1,093 | 4.8 / 6.7 | KB_into_PB 14.2% (n 2,610) | PB_into_KB 10.8% (n 2,463) |
| ST-KB | 1,049 | 973 | 1,631 | 1,036 | 5.1 / 6.8 | ST_into_KB 14.2% (n 2,482) | KB_into_ST 12.6% (n 2,610) |
| WT-KB | 936 | 795 | 1,400 | 902 | 5.2 / 6.8 | WT_into_KB 15.5% (n 3,666) | KB_into_WT 8.0% (n 2,610) |
| HM-KB | 897 | 741 | 1,488 | 858 | 5.2 / 6.8 | HM_into_KB 13.4% (n 2,259) | KB_into_HM 8.7% (n 2,610) |
| ST-WT | 701 | 590 | 1,085 | 674 | 7.0 / 7.0 | ST_into_WT 3.2% (n 2,482) | WT_into_ST 14.3% (n 3,666) |
| HM-WT | 669 | 608 | 970 | 657 | 7.0 / 7.0 | HM_into_WT 8.7% (n 2,259) | WT_into_HM 11.1% (n 3,666) |
| HM-PB | 678 | 578 | 1,081 | 654 | 5.4 / 7.7 | HM_into_PB 10.8% (n 2,259) | PB_into_HM 6.1% (n 2,463) |
| WT-PB | 699 | 499 | 1,076 | 645 | 5.4 / 7.0 | WT_into_PB 13.2% (n 3,666) | PB_into_WT 3.3% (n 2,463) |
| ST-SM | 675 | 514 | 1,226 | 633 | 7.7 / 10.0 | ST_into_SM 1.8% (n 2,482) | SM_into_ST 30.8% (n 1,068) |
| ST-HM | 580 | 647 | 932 | 606 | 10.0 / 10.0 | ST_into_HM 5.4% (n 2,482) | HM_into_ST 11.9% (n 2,259) |
| KB-SM | 636 | 456 | 877 | 588 | 5.2 / 6.8 | KB_into_SM 4.7% (n 2,610) | SM_into_KB 23.6% (n 1,068) |
| HM-SM | 581 | 516 | 1,013 | 567 | 7.6 / 10.0 | HM_into_SM 4.0% (n 2,259) | SM_into_HM 24.5% (n 1,068) |
| SM-PB | 584 | 480 | 1,131 | 558 | 5.3 / 6.8 | SM_into_PB 27.4% (n 1,068) | PB_into_SM 2.3% (n 2,463) |
| ST-PB | 516 | 378 | 787 | 479 | 5.3 / 7.7 | ST_into_PB 6.0% (n 2,482) | PB_into_ST 7.5% (n 2,463) |
| WT-SM | 381 | 288 | 677 | 357 | 6.8 / 7.0 | WT_into_SM 4.3% (n 3,666) | SM_into_WT 16.4% (n 1,068) |

### By book pair, U3 (overlap min/wk and time-weighted offset lots; share of each side's entries that enter into the other's opposite open position, WF)
| pair | PRE min/wk | HOLD min/wk | X min/wk | WF min/wk | WF offset lots (mean / max) | WF share: first into second | WF share: second into first |
|---|---|---|---|---|---|---|---|
| KB-PB | 1,213 | 777 | 1,744 | 1,093 | 8.0 / 8.0 | KB_into_PB 14.2% (n 2,610) | PB_into_KB 10.8% (n 2,463) |
| KB-SM | 636 | 456 | 877 | 588 | 10.0 / 10.0 | KB_into_SM 4.7% (n 2,610) | SM_into_KB 23.6% (n 1,068) |
| SM-PB | 584 | 480 | 1,131 | 558 | 8.0 / 8.0 | SM_into_PB 27.4% (n 1,068) | PB_into_SM 2.3% (n 2,463) |

U5 (KB5 SM7 PE5) has the same timing as the U3 pairs (KB-SM, KB-PE, SM-PE) with offset lots scaled by 5/7/5 instead of 10/10/8; DS5 pairs with DN are in the U5m step-2 table below.

## 2. Overlap P&L and commissions AS TRADED (both brackets live)
'Creating' entries = entries made into an opposite open position; their own net P&L (engine net, after slippage and commission, lock engine exits). Overlap MTM = (long lots - short lots) x $20 x price change over the overlap seconds: the hedged lots earn exactly 0 gross, the net exposure is what moves; it is part of the books' P&L, not additional. Offset-lot cost = commission $4.84 + slippage $10.00 per contract round trip on min(entry lots, opposite lots open) of every creating entry (the lots that the other bracket already offsets).

| set | window | weeks | entries into opposite | creating net $/wk [CI] (MDE) | other entries net $/wk | net $ per creating entry vs other | hit rate creating / other | net $ per lot creating / other | overlap MTM $/wk [CI] (MDE) | offset contracts RT/wk | offset commission $/wk | offset commission+slippage $/wk | all commission $/wk | base stack $/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| U6 | WFPRE | 75 | 2,753 | +8,970 [-2,497,+20,383] (16,415) | +35,157 | +244 vs +354 | 54% / 54% | +33 / +48 | -2,288 [-11,581,+7,019] (13,491) | 242 | 1,169 | 3,585 | 4,870 | 44,127 |
| U6 | HOLD | 32 | 1,078 | +60 [-17,041,+16,432] (24,009) | +52,388 | +2 vs +513 | 53% / 54% | +0 / +71 | +6,816 [-9,720,+22,122] (22,789) | 208 | 1,005 | 3,082 | 4,756 | 52,448 |
| U6 | X | 44 | 1,570 | +3,823 [-10,010,+16,805] (19,574) | +16,793 | +107 vs +250 | 53% / 53% | +14 / +32 | +6,398 [-6,913,+19,962] (19,458) | 254 | 1,227 | 3,763 | 3,856 | 20,616 |
| U6 | WF | 106 | 3,831 | +6,365 [-3,214,+15,983] (13,694) | +40,690 | +176 vs +402 | 54% / 54% | +24 / +55 | +439 [-7,722,+8,278] (11,721) | 234 | 1,131 | 3,467 | 4,882 | 47,055 |
| U3 | WFPRE | 75 | 817 | +10,014 [+2,047,+17,811] (11,494) | +31,683 | +919 vs +671 | 54% / 53% | +97 / +73 | +31 [-2,899,+2,970] (4,260) | 95 | 457 | 1,402 | 2,590 | 41,697 |
| U3 | HOLD | 32 | 290 | +6,276 [-5,637,+17,700] (17,001) | +38,195 | +693 vs +820 | 53% / 53% | +73 / +90 | +3,317 [-1,064,+7,623] (6,312) | 79 | 381 | 1,168 | 2,473 | 44,471 |
| U3 | X | 44 | 493 | +2,600 [-6,881,+12,200] (14,050) | +6,319 | +232 vs +184 | 51% / 51% | +24 / +20 | -1,082 [-5,911,+3,891] (6,997) | 98 | 472 | 1,448 | 2,036 | 8,919 |
| U3 | WF | 106 | 1,107 | +8,980 [+2,238,+15,575] (9,644) | +33,948 | +860 vs +715 | 54% / 53% | +91 / +78 | +1,023 [-1,430,+3,429] (3,559) | 91 | 439 | 1,345 | 2,579 | 42,928 |
| U5 | WFPRE | 75 | 817 | +6,018 [+1,049,+10,872] (7,141) | +17,840 | +552 vs +378 | 54% / 53% | +97 / +72 | +171 [-1,666,+1,999] (2,661) | 58 | 279 | 857 | 1,507 | 23,857 |
| U5 | HOLD | 32 | 290 | +3,122 [-4,228,+10,173] (10,429) | +22,495 | +345 vs +483 | 53% / 53% | +61 / +92 | +1,566 [-808,+3,909] (3,442) | 48 | 234 | 719 | 1,436 | 25,617 |
| U5 | X | 44 | 493 | +2,042 [-3,938,+8,107] (8,842) | +3,463 | +182 vs +101 | 51% / 51% | +31 / +19 | +60 [-2,679,+2,863] (3,951) | 60 | 289 | 886 | 1,190 | 5,505 |
| U5 | WF | 106 | 1,107 | +5,200 [+1,031,+9,272] (5,978) | +19,413 | +498 vs +409 | 54% / 53% | +88 / +77 | +594 [-894,+2,060] (2,146) | 55 | 268 | 823 | 1,500 | 24,614 |
| U5m | WFPRE | 75 | 1,203 | +7,575 [+953,+14,190] (9,551) | +29,654 | +472 vs +482 | 54% / 53% | +76 / +81 | +2,934 [-510,+6,491] (5,107) | 89 | 431 | 1,321 | 2,259 | 37,229 |
| U5m | HOLD | 32 | 443 | +8,204 [-1,882,+18,258] (14,594) | +37,296 | +593 vs +611 | 55% / 53% | +96 / +102 | +4,777 [+918,+9,047] (5,842) | 77 | 374 | 1,146 | 2,180 | 45,500 |
| U5m | X | 44 | 744 | +3,716 [-5,542,+13,050] (13,669) | +4,985 | +220 vs +115 | 51% / 51% | +34 / +20 | +2,756 [-3,267,+9,077] (8,783) | 95 | 462 | 1,416 | 1,751 | 8,700 |
| U5m | WF | 106 | 1,646 | +7,837 [+2,325,+13,405] (8,068) | +32,241 | +505 vs +520 | 54% / 53% | +81 / +87 | +3,518 [+737,+6,279] (4,008) | 86 | 418 | 1,281 | 2,256 | 40,077 |

By year, U6 and U3 (WF windows):

| set | year | weeks | creating entries | creating net $/wk | net $ per creating entry | net $ per other entry |
|---|---|---|---|---|---|---|
| U6 | 2024 | 49 | 1,798 | +11,284 | +308 | +318 |
| U6 | 2025 | 53 | 1,843 | +3,420 | +98 | +453 |
| U6 | 2026 | 6 | 190 | -9,918 | -313 | +496 |
| U3 | 2024 | 49 | 560 | +7,233 | +633 | +711 |
| U3 | 2025 | 53 | 488 | +10,485 | +1,139 | +709 |
| U3 | 2026 | 6 | 59 | +6,959 | +708 | +797 |
| U5m | 2024 | 49 | 837 | +6,875 | +402 | +513 |
| U5m | 2025 | 53 | 733 | +6,716 | +486 | +501 |
| U5m | 2026 | 6 | 76 | +22,977 | +1,814 | +742 |

By book pair (later book into the earlier opposite book; WF; net $ per entry, hit rate, creating-entry $/wk):

**U6**

| later into earlier | n (WF) | per wk | net $ per entry | hit | net $/wk | mean lots | mean offset lots |
|---|---|---|---|---|---|---|---|
| WT_into_KB | 569 | 5.4 | -364 | 53% | -1,955 | 7.0 | 5.0 |
| WT_into_ST | 524 | 4.9 | -38 | 56% | -190 | 7.0 | 7.0 |
| WT_into_PB | 485 | 4.6 | -85 | 56% | -387 | 7.0 | 5.3 |
| WT_into_HM | 408 | 3.8 | +50 | 57% | +194 | 7.0 | 7.0 |
| KB_into_PB | 370 | 3.5 | +641 | 56% | +2,236 | 4.9 | 4.6 |
| ST_into_KB | 352 | 3.3 | +50 | 51% | +166 | 10.0 | 5.0 |
| KB_into_ST | 329 | 3.1 | +807 | 57% | +2,504 | 4.9 | 4.9 |
| SM_into_ST | 329 | 3.1 | +570 | 55% | +1,768 | 7.5 | 7.5 |
| HM_into_KB | 302 | 2.8 | -1,712 | 43% | -4,878 | 10.0 | 5.0 |
| SM_into_PB | 293 | 2.8 | +1,218 | 59% | +3,366 | 7.6 | 5.3 |
| HM_into_ST | 268 | 2.5 | +23 | 50% | +59 | 10.0 | 10.0 |
| PB_into_KB | 267 | 2.5 | +68 | 51% | +171 | 5.4 | 4.7 |
| SM_into_HM | 262 | 2.5 | +779 | 57% | +1,927 | 7.5 | 7.5 |
| SM_into_KB | 252 | 2.4 | +126 | 53% | +301 | 7.6 | 5.1 |
| HM_into_PB | 243 | 2.3 | -686 | 48% | -1,572 | 10.0 | 5.4 |
| KB_into_HM | 228 | 2.2 | +76 | 50% | +164 | 4.9 | 4.9 |
| KB_into_WT | 208 | 2.0 | +337 | 52% | +662 | 4.9 | 4.9 |
| HM_into_WT | 196 | 1.8 | -1,149 | 45% | -2,125 | 10.0 | 7.0 |
| PB_into_ST | 188 | 1.8 | -36 | 49% | -63 | 5.4 | 5.4 |
| SM_into_WT | 175 | 1.7 | +1,037 | 58% | +1,711 | 7.6 | 6.8 |
| WT_into_SM | 156 | 1.5 | +76 | 58% | +112 | 7.0 | 6.8 |
| PB_into_HM | 152 | 1.4 | +137 | 51% | +196 | 5.4 | 5.4 |
| ST_into_PB | 150 | 1.4 | +1,220 | 55% | +1,727 | 10.0 | 5.2 |
| ST_into_HM | 135 | 1.3 | +523 | 52% | +666 | 10.0 | 10.0 |
| KB_into_SM | 123 | 1.2 | +603 | 54% | +699 | 5.0 | 5.0 |
| HM_into_SM | 90 | 0.8 | +889 | 53% | +755 | 10.0 | 7.3 |
| PB_into_WT | 82 | 0.8 | +366 | 54% | +283 | 5.5 | 5.5 |
| ST_into_WT | 80 | 0.8 | +1,298 | 56% | +980 | 10.0 | 7.0 |
| PB_into_SM | 56 | 0.5 | -110 | 50% | -58 | 5.4 | 5.3 |
| ST_into_SM | 44 | 0.4 | +636 | 52% | +264 | 10.0 | 7.5 |

**U3**

| later into earlier | n (WF) | per wk | net $ per entry | hit | net $/wk | mean lots | mean offset lots |
|---|---|---|---|---|---|---|---|
| KB_into_PB | 370 | 3.5 | +1,298 | 56% | +4,532 | 10.0 | 8.0 |
| SM_into_PB | 293 | 2.8 | +1,689 | 59% | +4,669 | 10.0 | 8.0 |
| PB_into_KB | 267 | 2.5 | +153 | 51% | +386 | 8.0 | 8.0 |
| SM_into_KB | 252 | 2.4 | +392 | 53% | +932 | 10.0 | 10.0 |
| KB_into_SM | 123 | 1.2 | +1,223 | 54% | +1,419 | 10.0 | 10.0 |
| PB_into_SM | 56 | 0.5 | -24 | 50% | -13 | 8.0 | 8.0 |

**U5m**

| later into earlier | n (WF) | per wk | net $ per entry | hit | net $/wk | mean lots | mean offset lots |
|---|---|---|---|---|---|---|---|
| KB_into_PB | 370 | 3.5 | +649 | 56% | +2,266 | 5.0 | 5.0 |
| SM_into_PB | 293 | 2.8 | +1,182 | 59% | +3,268 | 7.0 | 5.0 |
| PB_into_KB | 267 | 2.5 | +96 | 51% | +242 | 5.0 | 5.0 |
| SM_into_KB | 252 | 2.4 | +275 | 53% | +653 | 7.0 | 5.0 |
| DN_into_KB | 246 | 2.3 | -216 | 49% | -502 | 8.0 | 5.0 |
| SM_into_DN | 219 | 2.1 | +560 | 55% | +1,157 | 7.0 | 7.0 |
| DN_into_PB | 211 | 2.0 | +348 | 52% | +692 | 8.0 | 5.0 |
| KB_into_DN | 207 | 2.0 | +773 | 56% | +1,509 | 5.0 | 5.0 |
| KB_into_SM | 123 | 1.2 | +611 | 54% | +709 | 5.0 | 5.0 |
| PB_into_DN | 106 | 1.0 | +66 | 51% | +66 | 5.0 | 5.0 |
| DN_into_SM | 56 | 0.5 | -1,303 | 43% | -688 | 8.0 | 7.0 |
| PB_into_SM | 56 | 0.5 | -15 | 50% | -8 | 5.0 | 5.0 |

## 3. Treatments on identical signals: verdict table (16 cells)
A1/A2 do not change a single trade (cost accounting); B and C change trades, so LM (lot-matched on PRE lot-seconds) is the fair comparison next to raw. Dollars per week of the overlap state = the paired weekly delta vs the unchanged stack.

| cell | set | treatment | acted on | tier | failed gates | WF raw d_mean/wk [CI] (MDE) | WF LM d_mean | PRE raw | HOLD raw [CI] (MDE) | HOLD LM | X raw |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U6_A1 | U6 | net-only execution (exact 1-s order netting, commission) | - | PASS (best-of-F cleared) | - | +221 [+203,+240] (27) | +221 | +222 | +213 [+178,+250] (53) | +213 | +216 |
| U6_A2 | U6 | net-only literal bound (commission on offset lots) | - | PASS (best-of-F cleared) | - | +1,131 [+1,080,+1,180] (71) | +1,131 | +1,169 | +1,005 [+941,+1,069] (92) | +1,005 | +1,227 |
| U6_B | U6 | later signal skipped while an opposite position is open | 20% | DEAD | G1,G2,G3,G4,G5,G6,G7 | -9,343 [-23,311,+4,639] (20,177) | +890 | -16,921 | +8,708 [-10,555,+27,335] (27,474) | +25,303 | -18,289 |
| U6_C | U6 | later signal closes the earlier (dead flip) | 15% | DEAD | G2,G3,G4,G5,G6,G7 | -9,212 [-25,175,+6,374] (22,458) | +5,890 | -9,733 | -7,704 [-35,458,+17,448] (38,238) | +10,156 | -22,770 |
| U3_A1 | U3 | net-only execution (exact 1-s order netting, commission) | - | PASS (best-of-F cleared) | - | +68 [+58,+78] (14) | +68 | +74 | +53 [+39,+67] (20) | +53 | +80 |
| U3_A2 | U3 | net-only literal bound (commission on offset lots) | - | PASS (best-of-F cleared) | - | +439 [+411,+466] (39) | +439 | +457 | +381 [+338,+428] (66) | +381 | +472 |
| U3_B | U3 | later signal skipped while an opposite position is open | 17% | DEAD | G1,G2,G3,G4,G5,G6,G7 | -8,730 [-16,847,-455] (11,703) | +163 | -7,636 | -11,020 [-21,636,+305] (15,509) | -2,322 | -9,202 |
| U3_C | U3 | later signal closes the earlier (dead flip) | 16% | DEAD | G1,G2,G3,G4,G5,G6,G7 | -6,124 [-15,386,+2,485] (12,827) | +2,871 | -9,413 | +1,776 [-10,299,+13,451] (17,360) | +13,079 | -8,388 |
| U5_A1 | U5 | net-only execution (exact 1-s order netting, commission) | - | PASS (best-of-F cleared) | - | +41 [+35,+47] (8) | +41 | +44 | +32 [+24,+41] (12) | +32 | +48 |
| U5_A2 | U5 | net-only literal bound (commission on offset lots) | - | PASS (best-of-F cleared) | - | +268 [+252,+285] (24) | +268 | +279 | +234 [+208,+263] (41) | +234 | +289 |
| U5_B | U5 | later signal skipped while an opposite position is open | 17% | DEAD | G2,G3,G4,G5,G6,G7 | -4,964 [-9,855,+54] (7,093) | +475 | -4,691 | -5,447 [-12,172,+1,853] (9,964) | +135 | -5,685 |
| U5_C | U5 | later signal closes the earlier (dead flip) | 16% | DEAD | G1,G2,G3,G4,G5,G6,G7 | -3,273 [-8,499,+1,613] (7,232) | +1,807 | -4,995 | +864 [-6,186,+7,643] (10,054) | +7,168 | -5,240 |
| U5m_A1 | U5m | net-only execution (exact 1-s order netting, commission) | - | LEAD (cap; was PASS (best-of-F cleared)) | - | +101 [+92,+111] (14) | +101 | +110 | +78 [+63,+94] (23) | +78 | +76 |
| U5m_A2 | U5m | net-only literal bound (commission on offset lots) | - | LEAD (cap; was PASS (best-of-F cleared)) | - | +418 [+393,+442] (35) | +418 | +431 | +374 [+329,+419] (66) | +374 | +462 |
| U5m_B | U5m | later signal skipped while an opposite position is open | 17% | DEAD | G2,G3,G4,G5,G6 | -4,345 [-11,359,+2,713] (10,086) | +5,621 | -2,634 | -8,219 [-19,401,+2,924] (15,983) | +2,179 | -8,202 |
| U5m_C | U5m | later signal closes the earlier (dead flip) | 15% | DEAD | G3,G4,G6 | -1,502 [-8,664,+5,349] (10,117) | +9,684 | -4,310 | +5,126 [-7,683,+17,919] (18,524) | +19,807 | -2,135 |

Gates (V2, never softened; prereg): G1 LM mean>0 PRE&HOLD; G2 HOLD CI low>0; G3 LM maxDD<=0 & worst>=0 PRE&HOLD; G4 pair AND direction placebo ranks>=0.95 PRE&HOLD (A cells: accounting, n/a); G5 >=2 of 3 years positive none >60%; G6 X LM mean>=0, maxDD<=0, worst>=0; G7 2x-cost WF LM>0. Best-of-F bar HOLD p<=0.05/60=0.000833. U5m capped at LEAD.

### Best treatment per universe (pre-registered rule: highest PRE raw weekly mean delta; shown with its HOLD/X/WF behaviour)
| set | best on PRE | PRE raw d/wk | HOLD raw d/wk [CI] (MDE) | X raw | WF raw [CI] (MDE) | day-paired WF d/day [CI] (MDE) | tier |
|---|---|---|---|---|---|---|---|
| U6 | A2 | +1,169 | +1,005 [+941,+1,069] (92) | +1,227 | +1,131 [+1,080,+1,180] (71) | +230 [+219,+241] (15) | PASS (best-of-F cleared) |
| U3 | A2 | +457 | +381 [+338,+428] (66) | +472 | +439 [+411,+466] (39) | +89 [+84,+94] (8) | PASS (best-of-F cleared) |
| U5 | A2 | +279 | +234 [+208,+263] (41) | +289 | +268 [+252,+285] (24) | +55 [+51,+58] (4) | PASS (best-of-F cleared) |
| U5m | A2 | +431 | +374 [+329,+419] (66) | +462 | +418 [+393,+442] (35) | +85 [+80,+89] (6) | LEAD (cap; was PASS (best-of-F cleared)) |

### Dollars per week of the overlap state, per treatment (paired weekly delta vs unchanged stack, raw and LM; MDE beside every mean)
| cell | PRE raw [CI] (MDE) | PRE LM | HOLD raw [CI] (MDE) | HOLD LM [CI] (MDE) | X raw | X LM | WF raw [CI] (MDE) | WF LM [CI] (MDE) | day-paired WF raw d/day [CI] (MDE) |
|---|---|---|---|---|---|---|---|---|---|
| U6_A1 | +222 [+201,+244] (31) | +222 | +213 [+178,+250] (53) | +213 [+178,+250] (53) | +216 | +216 | +221 [+203,+240] (27) | +221 [+203,+240] (27) | +45 [+42,+49] (5) |
| U6_A2 | +1,169 [+1,103,+1,234] (96) | +1,169 | +1,005 [+941,+1,069] (92) | +1,005 [+941,+1,069] (92) | +1,227 | +1,227 | +1,131 [+1,080,+1,180] (71) | +1,131 [+1,080,+1,180] (71) | +230 [+219,+241] (15) |
| U6_B | -16,921 [-34,485,+688] (25,655) | -9,538 | +8,708 [-10,555,+27,335] (27,474) | +25,303 [-1,791,+51,925] (39,411) | -18,289 | -17,658 | -9,343 [-23,311,+4,639] (20,177) | +890 [-16,778,+18,798] (25,881) | -1,901 [-4,556,+716] (3,784) |
| U6_C | -9,733 [-28,662,+9,166] (27,390) | +3,991 | -7,704 [-35,458,+17,448] (38,238) | +10,156 [-24,486,+42,632] (48,877) | -22,770 | -23,630 | -9,212 [-25,175,+6,374] (22,458) | +5,890 [-14,941,+26,242] (29,453) | -1,874 [-4,869,+1,051] (4,210) |
| U3_A1 | +74 [+62,+87] (18) | +74 | +53 [+39,+67] (20) | +53 [+39,+67] (20) | +80 | +80 | +68 [+58,+78] (14) | +68 [+58,+78] (14) | +14 [+12,+16] (3) |
| U3_A2 | +457 [+424,+491] (48) | +457 | +381 [+338,+428] (66) | +381 [+338,+428] (66) | +472 | +472 | +439 [+411,+466] (39) | +439 [+411,+466] (39) | +89 [+84,+94] (8) |
| U3_B | -7,636 [-18,084,+2,786] (15,164) | +1,221 | -11,020 [-21,636,+305] (15,509) | -2,322 [-18,270,+13,508] (22,811) | -9,202 | -9,276 | -8,730 [-16,847,-455] (11,703) | +163 [-9,968,+10,366] (14,731) | -1,776 [-3,478,-64] (2,453) |
| U3_C | -9,413 [-21,143,+1,580] (16,414) | -1,522 | +1,776 [-10,299,+13,451] (17,360) | +13,079 [-1,981,+27,679] (21,704) | -8,388 | -8,258 | -6,124 [-15,386,+2,485] (12,827) | +2,871 [-9,070,+14,029] (16,664) | -1,246 [-2,909,+410] (2,394) |
| U5_A1 | +44 [+37,+51] (11) | +44 | +32 [+24,+41] (12) | +32 [+24,+41] (12) | +48 | +48 | +41 [+35,+47] (8) | +41 [+35,+47] (8) | +8 [+7,+10] (2) |
| U5_A2 | +279 [+260,+299] (29) | +279 | +234 [+208,+263] (41) | +234 [+208,+263] (41) | +289 | +289 | +268 [+252,+285] (24) | +268 [+252,+285] (24) | +55 [+51,+58] (4) |
| U5_B | -4,691 [-10,967,+1,528] (9,088) | +614 | -5,447 [-12,172,+1,853] (9,964) | +135 [-10,003,+10,256] (14,601) | -5,685 | -5,735 | -4,964 [-9,855,+54] (7,093) | +475 [-5,916,+6,791] (9,127) | -1,010 [-2,023,+12] (1,459) |
| U5_C | -4,995 [-11,511,+1,117] (9,205) | -504 | +864 [-6,186,+7,643] (10,054) | +7,168 [-1,277,+15,330] (12,180) | -5,240 | -5,177 | -3,273 [-8,499,+1,613] (7,232) | +1,807 [-4,898,+8,144] (9,385) | -666 [-1,614,+273] (1,364) |
| U5m_A1 | +110 [+98,+122] (17) | +110 | +78 [+63,+94] (23) | +78 [+63,+94] (23) | +76 | +76 | +101 [+92,+111] (14) | +101 [+92,+111] (14) | +21 [+19,+23] (3) |
| U5m_A2 | +431 [+401,+459] (41) | +431 | +374 [+329,+419] (66) | +374 [+329,+419] (66) | +462 | +462 | +418 [+393,+442] (35) | +418 [+393,+442] (35) | +85 [+80,+89] (6) |
| U5m_B | -2,634 [-11,315,+5,842] (12,463) | +7,014 | -8,219 [-19,401,+2,924] (15,983) | +2,179 [-13,830,+18,103] (22,681) | -8,202 | -8,064 | -4,345 [-11,359,+2,713] (10,086) | +5,621 [-3,689,+14,830] (13,243) | -884 [-2,280,+523] (2,023) |
| U5m_C | -4,310 [-12,429,+3,703] (11,743) | +5,236 | +5,126 [-7,683,+17,919] (18,524) | +19,807 [+5,101,+34,579] (21,279) | -2,135 | -231 | -1,502 [-8,664,+5,349] (10,117) | +9,684 [+825,+18,422] (12,703) | -306 [-1,687,+1,065] (1,963) |

### Per overlap hour (WF raw delta per week divided by overlap hours per week)
| cell | overlap h/wk (WF) | WF raw d/wk | $ per overlap hour |
|---|---|---|---|
| U6_A1 | 36.0 | +221 | +6.2 |
| U6_A2 | 36.0 | +1,131 | +31.4 |
| U6_B | 36.0 | -9,343 | -259.7 |
| U6_C | 36.0 | -9,212 | -256.1 |
| U3_A1 | 25.0 | +68 | +2.7 |
| U3_A2 | 25.0 | +439 | +17.6 |
| U3_B | 25.0 | -8,730 | -349.7 |
| U3_C | 25.0 | -6,124 | -245.3 |
| U5_A1 | 25.0 | +41 | +1.6 |
| U5_A2 | 25.0 | +268 | +10.8 |
| U5_B | 25.0 | -4,964 | -198.8 |
| U5_C | 25.0 | -3,273 | -131.1 |
| U5m_A1 | 25.0 | +101 | +4.1 |
| U5m_A2 | 25.0 | +418 | +16.7 |
| U5m_B | 25.0 | -4,345 | -174.1 |
| U5m_C | 25.0 | -1,502 | -60.2 |

(U5m overlap hours use the U5 timing; DN adds overlap, so its per-hour figure is approximate.)

## 4. Per window detail (base mean/SD/maxDD/worst, cell deltas; raw and lot-matched)

### PRE
| cell | base mean/SD/maxDD/worst | basis | d_mean [CI iid] (MDE) | CI blk4 | p(d<=0) | d_SD | d_maxDD | d_worst | d_Sharpe | placebo rank pair/dir (mean) | rank worst pair/dir |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U6_A1 | 44,127/131,184/477,701/-306,664 | raw | +222 [+201,+244] (31) | [+209,+244] | 0.000 | -5 | -2,191 | +348 | +0.01 | -/0.00 | - |
| U6_A2 | 44,127/131,184/477,701/-306,664 | raw | +1,169 [+1,103,+1,234] (96) | [+1,133,+1,241] | 0.000 | -47 | -11,488 | +1,411 | +0.07 | - | - |
| U6_B | 44,127/131,184/477,701/-306,664 | raw | -16,921 [-34,485,+688] (25,655) | [-37,473,+1,524] | 0.970 | +5,994 | +397,387 | -79,534 | -1.00 | - | - |
| U6_B | 44,127/131,184/477,701/-306,664 | LM | -9,538 [-31,589,+12,658] (32,051) | [-36,148,+14,113] | 0.796 | +43,217 | +634,843 | -184,329 | -1.00 | 0.17/0.36 | 0.00/0.01 |
| U6_C | 44,127/131,184/477,701/-306,664 | raw | -9,733 [-28,662,+9,166] (27,390) | [-29,050,+11,449] | 0.841 | -1,815 | -22,527 | -8,590 | -0.51 | - | - |
| U6_C | 44,127/131,184/477,701/-306,664 | LM | +3,991 [-21,165,+28,734] (36,176) | [-19,676,+30,080] | 0.370 | +49,824 | +159,160 | -134,427 | -0.51 | 0.86/0.99 | 0.00/0.54 |
| U3_A1 | 41,697/89,226/323,714/-187,669 | raw | +74 [+62,+87] (18) | [+63,+85] | 0.000 | +2 | -368 | +48 | +0.01 | -/0.00 | - |
| U3_A2 | 41,697/89,226/323,714/-187,669 | raw | +457 [+424,+491] (48) | [+433,+495] | 0.000 | -22 | -1,975 | +445 | +0.04 | - | - |
| U3_B | 41,697/89,226/323,714/-187,669 | raw | -7,636 [-18,084,+2,786] (15,164) | [-20,789,+3,449] | 0.921 | -982 | +8,644 | -15,085 | -0.59 | - | - |
| U3_B | 41,697/89,226/323,714/-187,669 | LM | +1,221 [-11,511,+13,889] (18,441) | [-14,075,+14,521] | 0.424 | +21,965 | +95,069 | -67,809 | -0.59 | 0.78/0.88 | 0.01/0.03 |
| U3_C | 41,697/89,226/323,714/-187,669 | raw | -9,413 [-21,143,+1,580] (16,414) | [-20,375,+1,483] | 0.954 | +12,467 | +84,235 | +1,425 | -1.08 | - | - |
| U3_C | 41,697/89,226/323,714/-187,669 | LM | -1,522 [-16,723,+12,980] (21,463) | [-15,408,+12,549] | 0.578 | +37,321 | +183,935 | -44,092 | -1.08 | 0.82/0.88 | 0.03/0.47 |
| U5_A1 | 23,857/52,673/187,147/-107,639 | raw | +44 [+37,+51] (11) | [+38,+50] | 0.000 | +1 | -227 | +34 | +0.01 | -/0.00 | - |
| U5_A2 | 23,857/52,673/187,147/-107,639 | raw | +279 [+260,+299] (29) | [+264,+302] | 0.000 | -15 | -1,210 | +281 | +0.04 | - | - |
| U5_B | 23,857/52,673/187,147/-107,639 | raw | -4,691 [-10,967,+1,528] (9,088) | [-12,491,+2,141] | 0.925 | +160 | +1,341 | -11,228 | -0.65 | - | - |
| U5_B | 23,857/52,673/187,147/-107,639 | LM | +614 [-7,145,+8,379] (11,326) | [-8,755,+8,931] | 0.434 | +14,783 | +53,512 | -44,128 | -0.65 | 0.81/0.84 | 0.04/0.07 |
| U5_C | 23,857/52,673/187,147/-107,639 | raw | -4,995 [-11,511,+1,117] (9,205) | [-10,934,+1,186] | 0.944 | +7,200 | +40,396 | -1,397 | -0.99 | - | - |
| U5_C | 23,857/52,673/187,147/-107,639 | LM | -504 [-9,055,+7,652] (12,096) | [-8,100,+7,437] | 0.542 | +21,453 | +94,565 | -27,354 | -0.99 | 0.86/0.91 | 0.06/0.47 |
| U5m_A1 | 37,229/77,404/237,429/-172,264 | raw | +110 [+98,+122] (17) | [+101,+120] | 0.000 | +9 | -465 | +82 | +0.01 | -/0.00 | - |
| U5m_A2 | 37,229/77,404/237,429/-172,264 | raw | +431 [+401,+459] (41) | [+403,+467] | 0.000 | -25 | -2,134 | +450 | +0.04 | - | - |
| U5m_B | 37,229/77,404/237,429/-172,264 | raw | -2,634 [-11,315,+5,842] (12,463) | [-10,749,+4,929] | 0.714 | +1,683 | +28,413 | -29,398 | -0.31 | - | - |
| U5m_B | 37,229/77,404/237,429/-172,264 | LM | +7,014 [-4,191,+17,862] (16,037) | [-3,089,+16,917] | 0.110 | +23,741 | +102,559 | -85,643 | -0.31 | 0.96/0.80 | 0.01/0.06 |
| U5m_C | 37,229/77,404/237,429/-172,264 | raw | -4,310 [-12,429,+3,703] (11,743) | [-12,964,+3,634] | 0.852 | -412 | +74,238 | +33,397 | -0.39 | - | - |
| U5m_C | 37,229/77,404/237,429/-172,264 | LM | +5,236 [-5,192,+15,648] (15,101) | [-5,502,+15,528] | 0.157 | +21,914 | +164,616 | -6,872 | -0.39 | 0.91/0.61 | 0.40/0.59 |

### HOLD
| cell | base mean/SD/maxDD/worst | basis | d_mean [CI iid] (MDE) | CI blk4 | p(d<=0) | d_SD | d_maxDD | d_worst | d_Sharpe | placebo rank pair/dir (mean) | rank worst pair/dir |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U6_A1 | 52,448/151,891/601,016/-318,557 | raw | +213 [+178,+250] (53) | [+185,+242] | 0.000 | +17 | -438 | +69 | +0.01 | -/0.00 | - |
| U6_A2 | 52,448/151,891/601,016/-318,557 | raw | +1,005 [+941,+1,069] (92) | [+925,+1,082] | 0.000 | +20 | -2,928 | +1,166 | +0.05 | - | - |
| U6_B | 52,448/151,891/601,016/-318,557 | raw | +8,708 [-10,555,+27,335] (27,474) | [-7,627,+29,435] | 0.192 | +6,758 | +99,817 | -21,305 | +0.29 | - | - |
| U6_B | 52,448/151,891/601,016/-318,557 | LM | +25,303 [-1,791,+51,925] (39,411) | [-3,226,+59,547] | 0.034 | +49,808 | +289,989 | -113,527 | +0.29 | 0.97/0.88 | 0.04/0.14 |
| U6_C | 52,448/151,891/601,016/-318,557 | raw | -7,704 [-35,458,+17,448] (38,238) | [-32,740,+7,531] | 0.708 | -14,060 | +17,285 | -25,750 | -0.15 | - | - |
| U6_C | 52,448/151,891/601,016/-318,557 | LM | +10,156 [-24,486,+42,632] (48,877) | [-20,435,+34,654] | 0.263 | +40,956 | +264,085 | -163,183 | -0.15 | 0.63/0.52 | 0.00/0.78 |
| U3_A1 | 44,471/94,698/368,385/-133,876 | raw | +53 [+39,+67] (20) | [+40,+64] | 0.000 | -9 | -87 | +39 | +0.00 | -/0.00 | - |
| U3_A2 | 44,471/94,698/368,385/-133,876 | raw | +381 [+338,+428] (66) | [+343,+417] | 0.000 | -22 | -1,384 | +416 | +0.03 | - | - |
| U3_B | 44,471/94,698/368,385/-133,876 | raw | -11,020 [-21,636,+305] (15,509) | [-17,365,-2,325] | 0.972 | +4,415 | +74,023 | -35,334 | -0.95 | - | - |
| U3_B | 44,471/94,698/368,385/-133,876 | LM | -2,322 [-18,270,+13,508] (22,811) | [-14,872,+12,556] | 0.614 | +30,188 | +189,066 | -79,335 | -0.95 | 0.53/0.86 | 0.07/0.23 |
| U3_C | 44,471/94,698/368,385/-133,876 | raw | +1,776 [-10,299,+13,451] (17,360) | [-10,649,+9,616] | 0.379 | -2,526 | +23,136 | +4,463 | +0.23 | - | - |
| U3_C | 44,471/94,698/368,385/-133,876 | LM | +13,079 [-1,981,+27,679] (21,704) | [-2,999,+25,641] | 0.045 | +20,000 | +118,822 | -27,164 | +0.23 | 0.99/0.93 | 0.27/0.72 |
| U5_A1 | 25,617/52,852/191,840/-64,909 | raw | +32 [+24,+41] (12) | [+25,+39] | 0.000 | -6 | -58 | +24 | +0.00 | -/0.00 | - |
| U5_A2 | 25,617/52,852/191,840/-64,909 | raw | +234 [+208,+263] (41) | [+211,+257] | 0.000 | -16 | -847 | +252 | +0.03 | - | - |
| U5_B | 25,617/52,852/191,840/-64,909 | raw | -5,447 [-12,172,+1,853] (9,964) | [-9,459,-374] | 0.936 | +3,593 | +47,332 | -23,322 | -0.92 | - | - |
| U5_B | 25,617/52,852/191,840/-64,909 | LM | +135 [-10,003,+10,256] (14,601) | [-7,977,+9,258] | 0.489 | +19,216 | +113,530 | -47,743 | -0.92 | 0.66/0.94 | 0.13/0.30 |
| U5_C | 25,617/52,852/191,840/-64,909 | raw | +864 [-6,186,+7,643] (10,054) | [-6,494,+5,412] | 0.393 | -2,082 | +20,574 | -4,942 | +0.27 | - | - |
| U5_C | 25,617/52,852/191,840/-64,909 | LM | +7,168 [-1,277,+15,330] (12,180) | [-2,017,+14,049] | 0.048 | +10,004 | +71,141 | -21,571 | +0.27 | 0.97/0.95 | 0.24/0.81 |
| U5m_A1 | 45,500/84,477/309,765/-131,284 | raw | +78 [+63,+94] (23) | [+68,+89] | 0.000 | -6 | -227 | +145 | +0.01 | -/0.00 | - |
| U5m_A2 | 45,500/84,477/309,765/-131,284 | raw | +374 [+329,+419] (66) | [+338,+418] | 0.000 | -7 | -1,016 | +455 | +0.03 | - | - |
| U5m_B | 45,500/84,477/309,765/-131,284 | raw | -8,219 [-19,401,+2,924] (15,983) | [-15,168,+1,397] | 0.924 | +3,434 | +48,590 | -36,422 | -0.83 | - | - |
| U5m_B | 45,500/84,477/309,765/-131,284 | LM | +2,179 [-13,830,+18,103] (22,681) | [-9,978,+17,375] | 0.396 | +27,953 | +148,537 | -83,196 | -0.83 | 0.77/0.84 | 0.03/0.30 |
| U5m_C | 45,500/84,477/309,765/-131,284 | raw | +5,126 [-7,683,+17,919] (18,524) | [-12,783,+17,881] | 0.211 | -9,356 | -72,174 | +11,251 | +0.98 | - | - |
| U5m_C | 45,500/84,477/309,765/-131,284 | LM | +19,807 [+5,101,+34,579] (21,279) | [+756,+35,507] | 0.003 | +12,428 | -3,277 | -23,556 | +0.98 | 1.00/0.92 | 0.17/0.79 |

### X 2023-04..2024-01
| cell | base mean/SD/maxDD/worst | basis | d_mean [CI iid] (MDE) | CI blk4 | p(d<=0) | d_SD | d_maxDD | d_worst | d_Sharpe | placebo rank pair/dir (mean) | rank worst pair/dir |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U6_A1 | 20,616/112,784/553,090/-157,300 | raw | +216 [+191,+243] (38) | [+196,+241] | 0.000 | +4 | -1,814 | +228 | +0.01 | -/0.00 | - |
| U6_A2 | 20,616/112,784/553,090/-157,300 | raw | +1,227 [+1,157,+1,297] (103) | [+1,177,+1,303] | 0.000 | +41 | -8,873 | +915 | +0.08 | - | - |
| U6_B | 20,616/112,784/553,090/-157,300 | raw | -18,289 [-35,794,-573] (25,705) | [-30,558,-1,465] | 0.979 | +2,825 | +301,065 | -67,625 | -1.17 | - | - |
| U6_B | 20,616/112,784/553,090/-157,300 | LM | -17,658 [-39,659,+4,645] (32,351) | [-32,720,+5,304] | 0.937 | +34,196 | +532,840 | -128,658 | -1.17 | 0.03/0.28 | 0.02/0.14 |
| U6_C | 20,616/112,784/553,090/-157,300 | raw | -22,770 [-41,960,-3,753] (27,735) | [-38,316,-6,887] | 0.991 | +2,204 | +306,267 | -94,636 | -1.45 | - | - |
| U6_C | 20,616/112,784/553,090/-157,300 | LM | -23,630 [-50,416,+2,571] (38,566) | [-44,799,-864] | 0.960 | +48,103 | +649,287 | -195,199 | -1.45 | 0.03/1.00 | 0.00/0.67 |
| U3_A1 | 8,919/70,954/433,358/-128,369 | raw | +80 [+65,+96] (23) | [+62,+100] | 0.000 | -23 | -997 | +174 | +0.01 | -/0.00 | - |
| U3_A2 | 8,919/70,954/433,358/-128,369 | raw | +472 [+432,+514] (60) | [+430,+519] | 0.000 | +19 | -4,259 | +484 | +0.05 | - | - |
| U3_B | 8,919/70,954/433,358/-128,369 | raw | -9,202 [-21,140,+2,875] (17,300) | [-18,007,+2,763] | 0.937 | +9,350 | +231,318 | +5,221 | -0.93 | - | - |
| U3_B | 8,919/70,954/433,358/-128,369 | LM | -9,276 [-25,227,+6,439] (22,811) | [-22,471,+7,910] | 0.879 | +30,231 | +404,159 | -26,802 | -0.93 | 0.18/0.51 | 0.35/0.53 |
| U3_C | 8,919/70,954/433,358/-128,369 | raw | -8,388 [-17,028,+458] (12,626) | [-18,616,+1,185] | 0.969 | +3,716 | +132,736 | -27,760 | -0.86 | - | - |
| U3_C | 8,919/70,954/433,358/-128,369 | LM | -8,258 [-19,688,+3,348] (16,771) | [-20,470,+2,256] | 0.919 | +21,964 | +271,086 | -65,917 | -0.86 | 0.14/0.53 | 0.04/0.17 |
| U5_A1 | 5,505/40,975/226,113/-63,772 | raw | +48 [+39,+58] (14) | [+37,+60] | 0.000 | -12 | -566 | +97 | +0.01 | -/0.00 | - |
| U5_A2 | 5,505/40,975/226,113/-63,772 | raw | +289 [+265,+313] (35) | [+265,+315] | 0.000 | +14 | -2,570 | +290 | +0.05 | - | - |
| U5_B | 5,505/40,975/226,113/-63,772 | raw | -5,685 [-13,017,+1,659] (10,687) | [-11,174,+1,592] | 0.937 | +5,432 | +159,684 | -6,830 | -1.00 | - | - |
| U5_B | 5,505/40,975/226,113/-63,772 | LM | -5,735 [-15,518,+3,894] (14,094) | [-14,118,+4,779] | 0.880 | +18,277 | +266,466 | -26,371 | -1.00 | 0.14/0.50 | 0.21/0.57 |
| U5_C | 5,505/40,975/226,113/-63,772 | raw | -5,240 [-10,003,-313] (7,011) | [-10,787,-215] | 0.982 | +2,816 | +91,750 | -24,309 | -0.93 | - | - |
| U5_C | 5,505/40,975/226,113/-63,772 | LM | -5,177 [-11,641,+1,421] (9,505) | [-11,992,+567] | 0.940 | +13,240 | +167,421 | -45,277 | -0.93 | 0.07/0.47 | 0.04/0.28 |
| U5m_A1 | 8,700/60,450/274,013/-143,318 | raw | +76 [+64,+88] (18) | [+65,+86] | 0.000 | -4 | -291 | +97 | +0.01 | -/0.00 | - |
| U5m_A2 | 8,700/60,450/274,013/-143,318 | raw | +462 [+430,+494] (46) | [+433,+496] | 0.000 | +15 | -1,768 | +440 | +0.05 | - | - |
| U5m_B | 8,700/60,450/274,013/-143,318 | raw | -8,202 [-19,893,+3,561] (17,022) | [-18,620,+4,797] | 0.917 | +5,956 | +211,239 | +10,942 | -0.98 | - | - |
| U5m_B | 8,700/60,450/274,013/-143,318 | LM | -8,064 [-22,656,+6,972] (21,662) | [-22,291,+9,233] | 0.861 | +24,477 | +346,579 | -25,978 | -0.98 | 0.12/0.55 | 0.17/0.29 |
| U5m_C | 8,700/60,450/274,013/-143,318 | raw | -2,135 [-10,007,+5,851] (11,462) | [-9,936,+4,557] | 0.701 | +4,161 | +42,835 | +3,148 | -0.31 | - | - |
| U5m_C | 8,700/60,450/274,013/-143,318 | LM | -231 [-11,553,+10,761] (16,091) | [-9,816,+8,684] | 0.513 | +22,897 | +134,716 | -37,499 | -0.31 | 0.57/0.89 | 0.04/0.23 |

### WF
| cell | base mean/SD/maxDD/worst | basis | d_mean [CI iid] (MDE) | CI blk4 | p(d<=0) | d_SD | d_maxDD | d_worst | d_Sharpe | placebo rank pair/dir (mean) | rank worst pair/dir |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U6_A1 | 47,055/138,124/601,016/-318,557 | raw | +221 [+203,+240] (27) | [+208,+238] | 0.000 | +3 | -438 | +69 | +0.01 | -/0.00 | - |
| U6_A2 | 47,055/138,124/601,016/-318,557 | raw | +1,131 [+1,080,+1,180] (71) | [+1,085,+1,189] | 0.000 | -26 | -2,928 | +1,166 | +0.06 | - | - |
| U6_B | 47,055/138,124/601,016/-318,557 | raw | -9,343 [-23,311,+4,639] (20,177) | [-26,570,+5,038] | 0.902 | +6,698 | +274,073 | -67,640 | -0.58 | - | - |
| U6_B | 47,055/138,124/601,016/-318,557 | LM | +890 [-16,778,+18,798] (25,881) | [-21,977,+21,046] | 0.454 | +45,996 | +511,528 | -172,435 | -0.58 | 0.57/0.60 | 0.00/0.04 |
| U6_C | 47,055/138,124/601,016/-318,557 | raw | -9,212 [-25,175,+6,374] (22,458) | [-25,463,+5,441] | 0.873 | -5,644 | +17,285 | -25,750 | -0.40 | - | - |
| U6_C | 47,055/138,124/601,016/-318,557 | LM | +5,890 [-14,941,+26,242] (29,453) | [-13,949,+24,806] | 0.286 | +47,237 | +264,085 | -163,183 | -0.40 | 0.89/0.98 | 0.00/0.82 |
| U3_A1 | 42,928/90,799/368,385/-187,669 | raw | +68 [+58,+78] (14) | [+59,+78] | 0.000 | -2 | -87 | +48 | +0.01 | -/0.00 | - |
| U3_A2 | 42,928/90,799/368,385/-187,669 | raw | +439 [+411,+466] (39) | [+411,+468] | 0.000 | -24 | -1,384 | +445 | +0.04 | - | - |
| U3_B | 42,928/90,799/368,385/-187,669 | raw | -8,730 [-16,847,-455] (11,703) | [-18,036,-418] | 0.981 | +723 | +74,023 | -15,085 | -0.71 | - | - |
| U3_B | 42,928/90,799/368,385/-187,669 | LM | +163 [-9,968,+10,366] (14,731) | [-11,548,+10,578] | 0.490 | +24,522 | +189,066 | -67,809 | -0.71 | 0.78/0.94 | 0.01/0.04 |
| U3_C | 42,928/90,799/368,385/-187,669 | raw | -6,124 [-15,386,+2,485] (12,827) | [-15,055,+1,801] | 0.914 | +8,538 | +39,563 | +1,425 | -0.74 | - | - |
| U3_C | 42,928/90,799/368,385/-187,669 | LM | +2,871 [-9,070,+14,029] (16,664) | [-8,623,+13,178] | 0.312 | +32,816 | +139,263 | -44,092 | -0.74 | 0.96/0.97 | 0.03/0.49 |
| U5_A1 | 24,614/52,689/191,840/-107,639 | raw | +41 [+35,+47] (8) | [+36,+46] | 0.000 | -1 | -58 | +34 | +0.01 | -/0.00 | - |
| U5_A2 | 24,614/52,689/191,840/-107,639 | raw | +268 [+252,+285] (24) | [+252,+286] | 0.000 | -16 | -847 | +281 | +0.04 | - | - |
| U5_B | 24,614/52,689/191,840/-107,639 | raw | -4,964 [-9,855,+54] (7,093) | [-10,684,+40] | 0.974 | +1,199 | +47,332 | -11,228 | -0.74 | - | - |
| U5_B | 24,614/52,689/191,840/-107,639 | LM | +475 [-5,916,+6,791] (9,127) | [-6,793,+6,871] | 0.443 | +16,114 | +113,530 | -44,128 | -0.74 | 0.83/0.94 | 0.04/0.07 |
| U5_C | 24,614/52,689/191,840/-107,639 | raw | -3,273 [-8,499,+1,613] (7,232) | [-8,165,+1,204] | 0.901 | +4,859 | +35,703 | -1,397 | -0.69 | - | - |
| U5_C | 24,614/52,689/191,840/-107,639 | LM | +1,807 [-4,898,+8,144] (9,385) | [-4,504,+7,584] | 0.292 | +18,559 | +89,872 | -27,354 | -0.69 | 0.99/0.97 | 0.06/0.47 |
| U5m_A1 | 40,077/79,573/309,765/-172,264 | raw | +101 [+92,+111] (14) | [+92,+111] | 0.000 | +4 | -227 | +82 | +0.01 | -/0.00 | - |
| U5m_A2 | 40,077/79,573/309,765/-172,264 | raw | +418 [+393,+442] (35) | [+393,+447] | 0.000 | -21 | -1,016 | +450 | +0.04 | - | - |
| U5m_B | 40,077/79,573/309,765/-172,264 | raw | -4,345 [-11,359,+2,713] (10,086) | [-10,718,+1,672] | 0.888 | +2,085 | +48,590 | -29,398 | -0.48 | - | - |
| U5m_B | 40,077/79,573/309,765/-172,264 | LM | +5,621 [-3,689,+14,830] (13,243) | [-3,100,+13,658] | 0.113 | +24,860 | +148,537 | -85,643 | -0.48 | 0.97/0.90 | 0.01/0.10 |
| U5m_C | 40,077/79,573/309,765/-172,264 | raw | -1,502 [-8,664,+5,349] (10,117) | [-9,618,+5,585] | 0.664 | -2,315 | +1,902 | +33,397 | -0.03 | - | - |
| U5m_C | 40,077/79,573/309,765/-172,264 | LM | +9,684 [+825,+18,422] (12,703) | [-175,+18,348] | 0.017 | +20,088 | +92,280 | -6,872 | -0.03 | 0.99/0.88 | 0.40/0.81 |

## 5. By year (WF summed weekly delta, raw / LM), the 2023 span, and 2x cost
| cell | 2024 raw/LM | 2025 raw/LM | 2026 (to 02-06) raw/LM | X 2023-04..2024-01 sum raw/LM | X LM maxDD / worst d | 2x-cost WF raw / LM d_mean |
|---|---|---|---|---|---|---|
| U6_A1 | +10,897/+10,897 | +11,362/+11,362 | +1,218/+1,218 | +9,524/+9,524 | -1,814 / +228 | +443 / +443 |
| U6_A2 | +59,364/+59,364 | +55,544/+55,544 | +4,943/+4,943 | +54,002/+54,002 | -8,873 / +915 | +2,261 / +2,261 |
| U6_B | -556,329/-178,461 | -514,823/+108,179 | +80,754/+164,596 | -804,724/-776,941 | +532,840 / -128,658 | -7,207 / -369 |
| U6_C | -120,526/+608,948 | -977,542/-245,797 | +121,548/+261,163 | -1,001,898/-1,039,732 | +649,287 / -195,199 | -12,399 / -4,417 |
| U3_A1 | +3,766/+3,766 | +3,117/+3,117 | +348/+348 | +3,524/+3,524 | -997 / +174 | +136 / +136 |
| U3_A2 | +23,706/+23,706 | +20,386/+20,386 | +2,401/+2,401 | +20,783/+20,783 | -4,259 / +484 | +877 / +877 |
| U3_B | -19,304/+447,042 | -836,150/-404,357 | -69,879/-25,379 | -404,904/-408,143 | +404,159 / -26,802 | -8,779 / -1,717 |
| U3_C | -450,088/-117,077 | -314,731/+218,519 | +115,709/+202,888 | -369,058/-363,342 | +271,086 / -65,917 | -8,133 / -1,337 |
| U5_A1 | +2,241/+2,241 | +1,859/+1,859 | +218/+218 | +2,110/+2,110 | -566 / +97 | +81 / +81 |
| U5_A2 | +14,486/+14,486 | +12,507/+12,507 | +1,462/+1,462 | +12,715/+12,715 | -2,570 / +290 | +537 / +537 |
| U5_B | -11,431/+271,623 | -483,492/-219,994 | -31,235/-1,278 | -250,144/-252,336 | +266,466 / -26,371 | -5,055 / -748 |
| U5_C | -238,249/-48,790 | -178,220/+121,087 | +69,513/+119,264 | -230,560/-227,783 | +167,421 / -45,277 | -4,452 / -605 |
| U5m_A1 | +5,169/+5,169 | +5,106/+5,106 | +460/+460 | +3,330/+3,330 | -291 / +97 | +203 / +203 |
| U5m_A2 | +22,772/+22,772 | +19,520/+19,520 | +1,989/+1,989 | +20,323/+20,323 | -1,768 / +440 | +835 / +835 |
| U5m_B | -79,765/+370,852 | -250,880/+281,339 | -129,954/-56,405 | -360,909/-354,797 | +346,579 / -25,978 | -5,431 / +2,809 |
| U5m_C | -220,673/+206,980 | -46,721/+565,838 | +108,154/+253,671 | -93,932/-10,159 | +134,716 / -37,499 | -3,162 / +6,064 |

## 6. Worst 20 weeks and the trade-off line
Worst-20 (a) = the 20 worst base weeks over the whole 149-week span 2023-04-03..2026-02-06 (fixed on the base), (b) re-derived on PRE only (75 wk). Delta = cell minus base; positive = saved. 'Other weeks' = the remaining 129 weeks (PRE-only: remaining 55).

| cell | basis | worst-20 (a) delta | base worst-20 (a) | other 129 weeks delta | net (full span) | worst-20 (b) PRE-only delta | other PRE weeks delta |
|---|---|---|---|---|---|---|---|
| U6_A1 | raw | +4,343 | -3,534,170 | +28,657 | +33,000 | +4,637 | +12,034 |
| U6_A2 | raw | +24,877 | -3,534,170 | +148,977 | +173,854 | +25,059 | +62,622 |
| U6_B | raw | +57,491 | -3,534,170 | -1,852,613 | -1,795,122 | +417,971 | -1,687,038 |
| U6_B | LM | -885,907 | -3,534,170 | +203,280 | -682,627 | -94,020 | -621,366 |
| U6_C | raw | +659,567 | -3,534,170 | -2,637,985 | -1,978,417 | +507,155 | -1,237,141 |
| U6_C | LM | -487,924 | -3,534,170 | +72,506 | -415,418 | -210,496 | +509,831 |
| U3_A1 | raw | +1,423 | -2,095,941 | +9,332 | +10,754 | +1,258 | +4,288 |
| U3_A2 | raw | +8,954 | -2,095,941 | +58,322 | +67,276 | +9,361 | +24,945 |
| U3_B | raw | -16,296 | -2,095,941 | -1,313,941 | -1,330,237 | +211,133 | -783,815 |
| U3_B | LM | -565,556 | -2,095,941 | +174,719 | -390,837 | -73,804 | +165,410 |
| U3_C | raw | -69,027 | -2,095,941 | -949,141 | -1,018,168 | -134,017 | -571,927 |
| U3_C | LM | -598,133 | -2,095,941 | +539,121 | -59,012 | -486,166 | +371,980 |
| U5_A1 | raw | +823 | -1,217,278 | +5,605 | +6,428 | +770 | +2,517 |
| U5_A2 | raw | +5,435 | -1,217,278 | +35,734 | +41,169 | +5,682 | +15,270 |
| U5_B | raw | +33,345 | -1,217,278 | -809,648 | -776,303 | +9,129 | -360,973 |
| U5_B | LM | -294,346 | -1,217,278 | +92,361 | -201,985 | -199,593 | +245,613 |
| U5_C | raw | -89,285 | -1,217,278 | -488,231 | -577,516 | -117,602 | -256,995 |
| U5_C | LM | -400,326 | -1,217,278 | +364,103 | -36,223 | -327,294 | +289,482 |
| U5m_A1 | raw | +1,655 | -1,892,870 | +12,410 | +14,065 | +2,110 | +6,118 |
| U5m_A2 | raw | +8,262 | -1,892,870 | +56,342 | +64,604 | +9,699 | +22,617 |
| U5m_B | raw | +99,984 | -1,892,870 | -921,492 | -821,508 | +238,449 | -436,034 |
| U5m_B | LM | -400,063 | -1,892,870 | +641,052 | +240,989 | +15,741 | +510,325 |
| U5m_C | raw | +157,649 | -1,892,870 | -410,821 | -253,172 | +81,596 | -404,864 |
| U5m_C | LM | -345,535 | -1,892,870 | +1,361,865 | +1,016,330 | -195,442 | +588,118 |

## 7. Details: share acted on, lot-match scale, convergence, concurrency, sensitivities
| cell | entries acted on (of base entries) | c_LM | exposure ratio | pass3-vs-pass2 max daily diff | pass3-vs-pass2 PRE mean | notes |
|---|---|---|---|---|---|---|
| U6_A1 | - | 1 | 1 | - | - | PRE saving $/wk 222; with slippage 682; 60-s netting window commission 225, comm+slip 689; peak gross/net contracts 50.0/50.0 |
| U6_A2 | - | 1 | 1 | - | - | PRE saving $/wk 1,169; with slippage 3,585; peak gross/net contracts 50.0/50.0 |
| U6_B | 3,804 of 19,069 (19.9%) | 1.271 | 0.787 | 0 | +0 | by acting book {'ST': 468, 'HM': 566, 'WT': 1042, 'KB': 736, 'SM': 547, 'PB': 445} |
| U6_C | 2,884 of 19,069 (15.1%) | 1.399 | 0.715 | 0 | +0 | closed per flip mean 1.97; by acting book {'ST': 398, 'HM': 408, 'WT': 726, 'KB': 624, 'SM': 404, 'PB': 324} |
| U3_A1 | - | 1 | 1 | - | - | PRE saving $/wk 74; with slippage 227; 60-s netting window commission 74, comm+slip 227; peak gross/net contracts 28.0/28.0 |
| U3_A2 | - | 1 | 1 | - | - | PRE saving $/wk 457; with slippage 1,402; peak gross/net contracts 28.0/28.0 |
| U3_B | 1,352 of 8,149 (16.6%) | 1.260 | 0.794 | 0 | +0 | by acting book {'KB': 530, 'SM': 467, 'PB': 355} |
| U3_C | 1,295 of 8,149 (15.9%) | 1.244 | 0.804 | 0 | +0 | closed per flip mean 1.26; by acting book {'KB': 522, 'SM': 410, 'PB': 363} |
| U5_A1 | - | 1 | 1 | - | - | PRE saving $/wk 44; with slippage 134; 60-s netting window commission 44, comm+slip 134; peak gross/net contracts 17.0/17.0 |
| U5_A2 | - | 1 | 1 | - | - | PRE saving $/wk 279; with slippage 857; peak gross/net contracts 17.0/17.0 |
| U5_B | 1,352 of 8,149 (16.6%) | 1.277 | 0.783 | 0 | +0 | by acting book {'KB': 530, 'SM': 467, 'PB': 355} |
| U5_C | 1,295 of 8,149 (15.9%) | 1.238 | 0.808 | 0 | +0 | closed per flip mean 1.26; by acting book {'KB': 522, 'SM': 410, 'PB': 363} |
| U5m_A1 | - | 1 | 1 | - | - | PRE saving $/wk 110; with slippage 336; 60-s netting window commission 110, comm+slip 336; peak gross/net contracts 25.0/25.0 |
| U5m_A2 | - | 1 | 1 | - | - | PRE saving $/wk 431; with slippage 1,321; peak gross/net contracts 25.0/25.0 |
| U5m_B | 1,864 of 10,858 (17.2%) | 1.279 | 0.782 | 0 | +0 | by acting book {'KB': 609, 'DN': 386, 'SM': 491, 'PB': 378} |
| U5m_C | 1,653 of 10,858 (15.2%) | 1.290 | 0.775 | 0 | +0 | closed per flip mean 1.49; by acting book {'KB': 596, 'DN': 301, 'SM': 391, 'PB': 365} |

B and C by acting book, WF raw delta by book ($/wk, weighted):

| cell | KB | DN | SM | PB | ST | HM | WT |
|---|---|---|---|---|---|---|---|
| U6_B | -3,194 | - | -2,671 | -854 | -4,517 | +2,419 | -526 |
| U6_C | -3,768 | - | -2,205 | -3,838 | -1,395 | +4,378 | -2,384 |
| U3_B | -5,427 | - | -2,483 | -819 | - | - | - |
| U3_C | -5,212 | - | -1,298 | +387 | - | - | - |
| U5_B | -2,714 | - | -1,738 | -512 | - | - | - |
| U5_C | -2,606 | - | -909 | +242 | - | - | - |
| U5m_B | -2,778 | +1,481 | -2,080 | -968 | - | - | - |
| U5m_C | -2,616 | +579 | -481 | +1,016 | - | - | - |
