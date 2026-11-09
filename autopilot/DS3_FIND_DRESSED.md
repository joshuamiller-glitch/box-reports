# DS3_FIND_DRESSED (FD-CORE, 2026-11-09 19:18Z). Post-hoc, Shadow only, no PASS claim, nothing live.
User order: judge every candidate book WITH the stack on it, not naked. Seat test on the S1b-COMB stack drawdown (API: FD_API.md). MV is the weakest live book on L6M stack-Calmar contribution (removing it alone cuts L6M maxDD 14%% at equal mean, so replace seats are credited only beyond that drop-only row).

## REFERENCE ROW (not a recommendation): drop-only MV
Weakest live book by L6M stack-Calmar contribution = MV (-3.21; the stack Calmar rises when it is removed). Removing it and adding nothing: maxDD cut vs live stack L6M +13.7% / HOLD +17.0% / PRE +15.3% / X' -22.6%; at equal stack mean (global lot scale) L6M +14.5% / PRE +16.1%; mean change L6M +257 $/wk. Every "replace weakest" row below is credited only for the increment over this row (inc_*).
Does any dressed candidate beat "replace MV" beyond the drop-only credit (inc eq-mean cut > 0 on L6M and PRE)? no dressed rows yet; naked lists: 786 of 6734 lists do on the screen (not a verdict)
ROLL-EXCL: naked NQ/ES/RTY (+ES/RTY pairs) lists were checked against the 14 contract-roll seconds of the replica engine; 116 trades in 43 of 1,916 lists were alive across a roll and carry rollx=1 (weight 0 in every daily series). instr2 lists run on back-adjusted bars so the artifact is small; ES/RTY use the NQ roll seconds (same quarterly cycle, exact ES/RTY roll days not separately checked). Other instruments: back-adjusted series, no stitched prints.

## 0. Status of the dressing
Inventory: 6734 exported naked lists (LIQ 2924, NOL2 3810) + 133 registry rows without an exported list (FD_INVENTORY.md). Scored ledger rows by stage: none yet (FD-LIQ / FD-NOL2 ledgers not written). The ranked table below shows DRESSED rows first; where an owner has not delivered a dressed row yet the NAKED screen rows are shown and labelled NAKED ONLY.

## 1. Ranked table (dressed rows)
| instrument | session | book | naked L6M / PRE mean | naked L6M / PRE maxDD | dressed L6M / PRE mean | dressed L6M / PRE maxDD | layers that carry it | stack eq-mean cut L6M/PRE: add | replace-weakest (MV, vs drop-only) | replace-correlated (vs drop-only) | corr | placebo p (add) | family p | WF | live weeks | L2? | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| (no dressed row has been delivered by FD-LIQ / FD-NOL2 yet) | | | | | | | | | | | | | | | | | |

## 2. NAKED screen (FD-CORE, all 6734 exported lists, first-order, no placebo/family null): top 40 by add-seat equal-mean maxDD cut on min(L6M, PRE)
LABEL NAKED ONLY: a number here is the bare list at equal $1,200 risk added to the stack; it is the baseline the dressed rows must beat. Row = seat add; replace columns are INCREMENTAL over the drop-only row.

| instrument | session | family | id | naked L6M / PRE mean | naked L6M / PRE maxDD | add: eq-mean cut L6M / PRE | replace-weakest inc L6M / PRE | corr to stack | random-entry placebo p L6M / PRE (finalists, 50 worlds, days+side re-simulated; conflates edge with timing) | status | owner |
|--|--|--|--|--|--|--|--|--|--|--|--|
| BTC | nyam | native_sympathy | BTC.native_sympathy.85317b4c | +1382 / -1044 | +19198 / +150965 | +10.2 / +16.2 | +9.2 / +7.0 | -0.08 | 0.02 / 0.06 | NOW-ONLY | NOL2 |
| BTC | nyam | native_sympathy | BTC.native_sympathy.94ec90c0 | +987 / -1140 | +21735 / +159222 | +7.8 / +22.6 | +20.5 / +20.5 | -0.14 | 0.02 / 0.02 | NOW-ONLY | NOL2 |
| GC | asia | T120 | GC.T120.8ce0c5d2 | +1213 / -70 | +18704 / +20742 | +7.3 / +9.8 | +7.2 / +9.6 | -0.05 | 0.02 / 0.04 | NOW-ONLY | NOL2 |
| GC | asia | T120 | GC.T120.ab8eecf0 | +1674 / -129 | +18468 / +20447 | +5.9 / +8.3 | +5.1 / +7.5 | -0.07 | 0.06 / 0.04 | NOW-ONLY | NOL2 |
| CL | london | flip | CL.flip.802d00dc | +1080 / -675 | +2764 / +73674 | +5.5 / +6.9 | +5.1 / +6.2 | +0.06 | - | NOW-ONLY | NOL2 |
| GC | nypm | vwap_reject | GC.vwap_reject.2b040a14 | +1671 / -391 | +4968 / +32845 | +5.4 / +5.7 | +5.2 / +4.9 | +0.20 | 0.02 / 0.06 | NOW-ONLY | NOL2 |
| GC | nyam | donchian | GC.donchian.b1e82932 | +1716 / -97 | +7909 / +46024 | +5.2 / +8.2 | +4.3 / +7.3 | -0.12 | 0.04 / 0.02 | NOW-ONLY | NOL2 |
| YM | nyam | 120 | YM.120.f8bdb952 | +1375 / +312 | +2570 / +33161 | +5.1 / +9.0 | +5.2 / +9.0 | +0.04 | - | NOW-ONLY | NOL2 |
| RTY | nypm | F_K_b1_ema21_atr20_m1.0 | RTY.F_K_b1_ema21_atr20_m1.0.4e2344ed | +1292 / -232 | +4165 / +26088 | +5.0 / +8.5 | +5.1 / +8.6 | +0.00 | - | killed | LIQ |
| BTC | nyam | native_sympathy | BTC.native_sympathy.1b60e8bf | +780 / -1310 | +11148 / +160668 | +4.4 / +9.3 | +4.3 / +6.2 | -0.07 | 0.04 / 0.08 | NOW-ONLY | NOL2 |
| GC | nypm | vwap_reject | GC.vwap_reject.e86771b9 | +1710 / -191 | +8723 / +29245 | +4.1 / +4.2 | +4.5 / +4.3 | +0.26 | 0.02 / 0.14 | NOW-ONLY | NOL2 |
| MBT | nyam | native_sympathy | MBT.native_sympathy.aefa1999 | +191 / -295 | +5370 / +36420 | +4.0 / +5.3 | +3.1 / +4.4 | -0.07 | 0.04 / 0.10 | NOW-ONLY | NOL2 |
| YM | nyam | 60 | YM.60.3f877350 | +448 / +1 | +4014 / +14242 | +3.9 / +4.0 | +4.2 / +4.4 | -0.06 | - | killed | NOL2 |
| RTY | nyam | F_K_b10_ema8_atr14_m2.0 | RTY.F_K_b10_ema8_atr14_m2.0.9c0d1e09 | +1187 / -186 | +4125 / +27327 | +6.1 / +3.8 | +9.2 / +4.1 | +0.05 | - | NOW-ONLY | LIQ |
| YM | london | LRS_YM_gp_h60_london_q0.7_atr_3.0_2R_s0 | YM.LRS_YM_gp_h60_london_q0.7_atr_3.0_2R_s0.78e37472 | +1939 / -1810 | +7819 / +144736 | +3.7 / +6.7 | +3.9 / +7.4 | -0.13 | 0.04 / 0.08 | NOW-ONLY | NOL2 |
| ES | close | daily_MR_k5_th1 | ES.daily_MR_k5_th1.0a1679d5 | +614 / +194 | +7142 / +14542 | +3.6 / +10.4 | +1.9 / +8.7 | +0.06 | - | NOW-ONLY | LIQ |
| BTC | nyam | F1_keltner | BTC.F1_keltner.4408fbbd | +233 / +309 | +5629 / +19218 | +5.7 / +3.6 | +6.9 / +4.5 | +0.04 | - | killed | NOL2 |
| NQ | pre | T2FNQ | NQ.T2FNQ.b204fb7b | +326 / -94 | +9791 / +13950 | +3.7 / +3.5 | +1.5 / +1.4 | -0.06 | 0.04 / 0.10 | killed | LIQ |
| ES | pre | F_S | ES.F_S.38c9d503 | +655 / -273 | +3079 / +27682 | +3.7 / +3.5 | +3.4 / +3.3 | -0.02 | 0.04 / 0.08 | killed | LIQ |
| ES | nyam | F_K | ES.F_K.ab400189 | +1024 / -157 | +2769 / +23209 | +3.4 / +4.0 | +3.1 / +3.8 | +0.08 | 0.10 / 0.10 | killed | LIQ |
| GC | london | vwap_reclaim | GC.vwap_reclaim.4018ab72 | +1348 / -76 | +4105 / +12041 | +3.3 / +4.4 | +3.0 / +4.0 | -0.02 | 0.02 / 0.04 | NOW-ONLY | NOL2 |
| GC | asia | T2FGC | GC.T2FGC.54497c15 | +117 / -493 | +5721 / +43304 | +3.3 / +4.8 | +1.7 / +3.8 | -0.11 | 0.02 / 0.02 | killed | NOL2 |
| ES | pre | F_K | ES.F_K.ecdeaacf | +1024 / +8 | +3818 / +19657 | +3.2 / +5.1 | +4.2 / +5.2 | +0.18 | 0.02 / 0.02 | killed | LIQ |
| NQ | nypm | LRS | NQ.LRS.234b08c5 | +2221 / -592 | +11546 / +57903 | +4.8 / +3.2 | +6.1 / +4.5 | +0.22 | 0.04 / 0.20 | NOW-ONLY | LIQ |
| ES | close | F_K | ES.F_K.0502b1d5 | +846 / -174 | +4682 / +20671 | +3.1 / +3.3 | +3.5 / +3.7 | +0.06 | 0.02 / 0.10 | killed | LIQ |
| GC | asia | T2FGC | GC.T2FGC.9ed38ac0 | +47 / -466 | +5721 / +41304 | +3.1 / +4.7 | +1.6 / +3.6 | -0.11 | 0.02 / 0.04 | killed | NOL2 |
| YM | nyam | 120 | YM.120.713a0432 | +637 / +98 | +1370 / +18270 | +3.1 / +5.0 | +2.4 / +4.4 | +0.04 | - | NOW-ONLY | NOL2 |
| GC | nyam | T60 | GC.T60.d167f416 | +552 / +281 | +3476 / +11002 | +3.1 / +4.1 | +2.1 / +3.2 | -0.05 | 0.02 / 0.02 | NOW-ONLY | NOL2 |
| ES | nypm | F_S | ES.F_S.549288af | +556 / -101 | +785 / +15730 | +3.0 / +3.4 | +2.5 / +2.9 | +0.12 | 0.02 / 0.04 | killed | LIQ |
| RTY | pre | F_K_b3_ema13_atr7_m2.0 | RTY.F_K_b3_ema13_atr7_m2.0.93835934 | +850 / -252 | +1335 / +26926 | +3.0 / +3.6 | +3.5 / +4.3 | -0.07 | - | NOW-ONLY | LIQ |
| GC | asia | T2FGC | GC.T2FGC.3f595fd7 | +1259 / -204 | +6463 / +38006 | +2.9 / +7.7 | +2.8 / +8.3 | -0.13 | 0.02 / 0.02 | killed | NOL2 |
| RTY | nypm | F_K_b1_ema21_atr20_m1.0 | RTY.F_K_b1_ema21_atr20_m1.0.3fce7ab2 | +744 / -39 | +2756 / +9221 | +2.9 / +4.7 | +2.8 / +4.7 | +0.04 | - | killed | LIQ |
| YM | nyam | 120 | YM.120.c3f0f0f8 | +720 / +144 | +1964 / +7371 | +2.8 / +3.1 | +2.7 / +3.0 | +0.06 | - | NOW-ONLY | NOL2 |
| ES | pre | F_K | ES.F_K.9f1a7a02 | +637 / -311 | +4434 / +31210 | +4.5 / +2.8 | +5.2 / +3.6 | +0.19 | 0.08 / 0.12 | killed | LIQ |
| GC | london | T2FGC | GC.T2FGC.7cbd7d38 | +1236 / +125 | +3699 / +12052 | +2.9 / +2.8 | +2.4 / +2.3 | +0.07 | 0.02 / 0.08 | NOW-ONLY | NOL2 |
| GC | nyam | T60 | GC.T60.0e39a54e | +1552 / -66 | +6579 / +13816 | +2.8 / +4.6 | +3.1 / +4.9 | +0.03 | 0.08 / 0.06 | NOW-ONLY | NOL2 |
| ES | pre | F_K | ES.F_K.23cbaa9c | +732 / -192 | +2529 / +21011 | +2.7 / +4.1 | +3.0 / +4.5 | -0.06 | 0.08 / 0.04 | killed | LIQ |
| YM | nyam | 120 | YM.120.b935bc01 | +662 / +158 | +1964 / +9914 | +2.7 / +4.6 | +3.0 / +5.0 | +0.03 | - | NOW-ONLY | NOL2 |
| RTY | nyam | F_K_b3_ema34_atr20_m0.5 | RTY.F_K_b3_ema34_atr20_m0.5.e1b8e86e | +828 / -267 | +1995 / +22704 | +2.6 / +2.7 | +2.9 / +2.6 | -0.10 | - | killed | LIQ |
| ES | pre | F_K | ES.F_K.2618be56 | +1672 / +55 | +4667 / +21170 | +3.6 / +2.5 | +3.2 / +2.2 | -0.03 | - | killed | LIQ |

Counts: add-seat cut > 0 on both L6M and PRE at equal mean: 511 of 6734 lists (NOT a verdict: no placebo, no family null, no WF; with 6734 lists the max-stat alone would produce about this many).

## 3. Plain sentences
Written per dressed candidate once the owners deliver (template: "<instr> <session> <family>: naked X/wk; dressed with <layers> Y/wk, maxDD -Z%; added to the stack it lowers stack maxDD A% (L6M) / B% (PRE) at equal mean; holds / fails OOS because ...; with depth it would also get a state cut: quote $...").

## 4. What is not done yet
- Owners FD-LIQ / FD-NOL2 own the layer screens and joint stages; this page only merges their ledgers.
- Registry rows (page rows without an exported list, live siblings, Monday/WATCH books, WHAT_IS_DEAD families) have no naked list yet; see FD_INVENTORY.md.
- Random-entry placebo (re-simulated), purged WF and held-out live weeks are computed for finalists only; the 11-02..05 week is absent from most lists (1-min lists end 10-16, NQ lists 10-30).
- Depth-purchase quote (YM/GC/CL MBP-10 history and forward $/wk): to be filled from the NO-L2 vs LIQ layer deltas once both ledgers exist; no purchase made.