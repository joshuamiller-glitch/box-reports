# EINT1_RULES_DD - drawdown-first line for the four shipped D7 v1.0b rules on the one-convention engine at live lots (EF-2, 2026-11-01). POST-HOC CONSISTENCY TEST, NO PASS CLAIM

**Selection history (label).** EINT1 groups A (signal quality) and C (HTF) were ranked and chosen on windows that INCLUDE the recent ones (L6M/HOLD/2026 looked; EINT1 prereg: "selection is on looked data"). So this is a consistency test of already-selected rules on the one-convention engine, not a discovery and not a PASS. Live/shadow status is D7's owner's call; this page only reports. Capped 20260206, no post-cap file opened. Prereg `l2vast/ds3/prereg/EF2_EINT1_RULES_DD_prereg.md` sha256 119ad39b4058d302a0747675e9915da4d7257bb64a45d21edcb861eae153219d (in DECISIONS.md before scoring; dead_lookup NOT FOUND x4; cells appended after). Code `l2vast/ds3/code/eint1dd/`, results `l2vast/ds3/out/eint1dd/` (results.csv = every number below, bucket_diff.csv, masks.pkl).

**What was run.** EINT1 cells: HM `skipBot3_sig_slope`, KB `skipTop3_sig_st1_dist_atr`, PE `sizeHi_sig_st1_dist_atr` (EINT1 multipliers: x1.5 in the top tercile, x0.5 in the bottom, x1 middle; the policy file lists both lines; variant "top x1.5 only" shown), HM `skipBot3_sig_st1_dist_atr` (shadow). Tercile = EINT1's own causal rank: expanding rank over the book's own prior signals (all signals of the book, taken and not-taken, since 2023-04), minimum 100 prior (first 100 signals of a book are unruled), bottom r<1/3, top r>=2/3. Engine = DS3_ONE_CONVENTION (oc_lib unchanged) at live lots, both frames (as-is stack; Sunday composite), skip = signals removed before the lock engine, size = multiplier on the ER multiplier row that feeds the running-max locks (lots integer half-up min 1 in the composite); never pts scaling. Combined week lock: OFF (page 1) and 12R (second table). Windows L3M 14 wk / L6M 28 / HOLD 32 / PRE 75 / X' 44 / ALL 149. maxDD = weekly-cumulative peak-to-trough. Change % in brackets (negative = smaller drawdown). `*` = mean change beyond MDE (2.8 x SE of paired weekly delta). L3M, L6M and HOLD have fewer than 20 losing weeks, so worst-20 is shown for PRE, X' and ALL only. The L6M/L3M maxDD of each frame is essentially ONE week (as-is 2026-01-19; composite 2025-10-20 or 2026-01-19 per source), so a L6M "cut" is a one-week statement.
**Placebo.** 200 completed draws per cell (target 200) of random skips of the same number of kept trades (skip rules) or permutation of the rule's multiplier vector over the same book's live rows (size rule). Rank = share of draws whose maxDD cut >= the rule's (0.00 = rule beats every draw). **RISK-KEEP** = L6M maxDD cut >=20% AND mean inside MDE AND beats the placebo (rule cut > placebo 95th pct) AND HOLD, PRE and X' each cut >=20%.

## Page 1 - lock OFF (headline), recent windows first
| rule | frame | maxDD $k before->after (change) by window | worst-20 $k (tail windows PRE / X' / ALL) | mean change $k/wk (MDE) | EQUAL-RISK mean change | placebo rank | HOLD/PRE/X' agree | RISK-KEEP | research (frozen 12m) vs expanding tercile |
|---|---|---|---|---|---|---|---|---|---|
| HM(H6) skipBot3 sig_slope [live] | as-is stack | L3M 88->73 (-17%) / L6M 88->73 (-17%) / HOLD 144->142 (-1%) / PRE 162->193 (+19%) / X' 317->345 (+9%) / ALL 317->345 (+9%) | PRE -811->-850 / X' -572->-591 / ALL -1161->-1164 | L3M +0.3 (7.1) / L6M +1.5 (5.8) / HOLD +0.6 (5.1) / PRE -2.4 (2.9) / X' +0.1 (2.9) | c=1.00: L3M +0.3 / L6M +1.4 / HOLD +0.5 / PRE -2.5 / X' +0.1 | L6M 0.26 (p95 cut 26%, rule 17%); PRE 0.99; X' 0.81; n=200 | HOLD -1% PRE +19% X' +9%: NO | no (L6M maxDD cut 17%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 229/4056, L6M 32/909, PRE 138/2285, X' 54/763 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +2% PRE +16% X' +9% vs expanding L6M -17% PRE +19% X' +9% |
| HM(H6) skipBot3 sig_slope [live] | Sunday composite | L3M 21->33 (+54%) / L6M 23->33 (+44%) / HOLD 97->113 (+17%) / PRE 241->270 (+12%) / X' 121->121 (-0%) / ALL 241->270 (+12%) | PRE -875->-894 / X' -420->-397 / ALL -1098->-1088 | L3M -1.8 (10.0) / L6M -1.0 (5.3) / HOLD -1.8 (4.7) / PRE -1.4 (2.1) / X' -0.3 (2.2) | c=1.00: L3M -1.8 / L6M -1.0 / HOLD -1.8 / PRE -1.4 / X' -0.3 | L6M 0.76 (p95 cut 11%, rule -44%); PRE 0.99; X' 0.71; n=200 | HOLD +17% PRE +12% X' -0%: NO | no (L6M maxDD cut -44%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 229/4056, L6M 32/909, PRE 138/2285, X' 54/763 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +44% PRE +8% X' -11% vs expanding L6M +44% PRE +12% X' -0% |
| KB(K6) skipTop3 sig_st1_dist_atr [live] | as-is stack | L3M 88->90 (+2%) / L6M 88->90 (+2%) / HOLD 144->137 (-5%) / PRE 162->153 (-5%) / X' 317->345 (+9%) / ALL 317->345 (+9%) | PRE -811->-768 / X' -572->-593 / ALL -1161->-1141 | L3M +4.4 (4.3)* / L6M +1.1 (3.8) / HOLD +0.6 (3.7) / PRE +0.6 (3.0) / X' -0.9 (2.5) | c=1.02: L3M +4.7 / L6M +1.5 / HOLD +1.0 / PRE +1.0 / X' -0.9 | L6M 0.57 (p95 cut 14%, rule -2%); PRE 0.18; X' 0.72; n=200 | HOLD -5% PRE -5% X' +9%: NO | no (L6M maxDD cut -2%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 87/5400, L6M 1/1257, PRE 32/3093, X' 54/933 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +2% PRE -5% X' -0% vs expanding L6M +2% PRE -5% X' +9% |
| KB(K6) skipTop3 sig_st1_dist_atr [live] | Sunday composite | L3M 21->24 (+12%) / L6M 23->30 (+32%) / HOLD 97->81 (-17%) / PRE 241->256 (+6%) / X' 121->121 (+0%) / ALL 241->256 (+6%) | PRE -875->-888 / X' -420->-426 / ALL -1098->-1086 | L3M +0.9 (4.0) / L6M +0.1 (3.8) / HOLD +0.3 (3.5) / PRE -0.7 (2.8) / X' -0.9 (1.9) | c=1.01: L3M +0.9 / L6M +0.1 / HOLD +0.3 / PRE -0.5 / X' -0.9 | L6M 0.78 (p95 cut 16%, rule -32%); PRE 0.85; X' 0.67; n=200 | HOLD -17% PRE +6% X' +0%: NO | no (L6M maxDD cut -32%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 87/5400, L6M 1/1257, PRE 32/3093, X' 54/933 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +32% PRE +6% X' -3% vs expanding L6M +32% PRE +6% X' +0% |
| PE(P6) sizeHi sig_st1_dist_atr x1.5 top / x0.5 bottom [live] | as-is stack | L3M 88->76 (-14%) / L6M 88->76 (-14%) / HOLD 144->157 (+9%) / PRE 162->191 (+18%) / X' 317->334 (+6%) / ALL 317->334 (+6%) | PRE -811->-980 / X' -572->-626 / ALL -1161->-1240 | L3M +4.9 (16.3) / L6M +2.3 (11.4) / HOLD +2.1 (10.4) / PRE -2.6 (8.4) / X' -0.4 (8.4) | c=0.94: L3M +3.8 / L6M +0.8 / HOLD +0.6 / PRE -3.7 / X' -0.2 | L6M 0.25 (p95 cut 35%, rule 14%); PRE 0.75; X' 0.77; n=200 | HOLD +9% PRE +18% X' +6%: NO | no (L6M maxDD cut 14%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 100/5261, L6M 11/1194, PRE 42/3049, X' 46/901 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD -14% PRE +30% X' -14% vs expanding L6M -14% PRE +18% X' +6% |
| PE(P6) sizeHi sig_st1_dist_atr x1.5 top / x0.5 bottom [live] | Sunday composite | L3M 21->36 (+68%) / L6M 23->23 (+2%) / HOLD 97->77 (-21%) / PRE 241->200 (-17%) / X' 121->156 (+29%) / ALL 241->200 (-17%) | PRE -875->-1008 / X' -420->-551 / ALL -1098->-1185 | L3M -3.0 (23.0) / L6M +2.2 (12.4) / HOLD +2.9 (11.3) / PRE -1.1 (8.6) / X' -2.3 (5.2) | c=0.90: L3M -6.1 / L6M -2.5 / HOLD -1.6 / PRE -3.6 / X' -3.2 | L6M 0.07 (p95 cut 1%, rule -2%); PRE 0.29; X' 0.57; n=200 | HOLD -21% PRE -17% X' +29%: NO | no (L6M maxDD cut -2%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 100/5261, L6M 11/1194, PRE 42/3049, X' 46/901 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +2% PRE -16% X' +10% vs expanding L6M +2% PRE -17% X' +29% |
| PE(P6) sizeHi sig_st1_dist_atr x1.5 top / x0.5 bottom [live] ; VARIANT top-tercile x1.5 only | as-is stack | L3M 88->86 (-2%) / L6M 88->86 (-2%) / HOLD 144->155 (+7%) / PRE 162->199 (+23%) / X' 317->344 (+9%) / ALL 317->344 (+9%) | PRE -811->-916 / X' -572->-664 / ALL -1161->-1270 | L3M +2.6 (10.7) / L6M +1.9 (6.8) / HOLD +1.4 (6.0) / PRE -0.6 (5.8) / X' -0.7 (5.5) | c=0.91: L3M +1.3 / L6M -0.1 / HOLD -0.6 / PRE -2.2 / X' -0.4 | L6M 0.47 (p95 cut 16%, rule 2%); PRE 0.74; X' 0.57; n=200 | HOLD +7% PRE +23% X' +9%: NO | no (L6M maxDD cut 2%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 100/5261, L6M 11/1194, PRE 42/3049, X' 46/901 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +2% PRE +25% X' +17% vs expanding L6M -2% PRE +23% X' +9% |
| PE(P6) sizeHi sig_st1_dist_atr x1.5 top / x0.5 bottom [live] ; VARIANT top-tercile x1.5 only | Sunday composite | L3M 21->27 (+26%) / L6M 23->29 (+26%) / HOLD 97->86 (-12%) / PRE 241->225 (-7%) / X' 121->135 (+12%) / ALL 241->225 (-7%) | PRE -875->-1081 / X' -420->-526 / ALL -1098->-1299 | L3M -3.6 (18.1) / L6M +1.5 (10.0) / HOLD +2.2 (8.9) / PRE +1.8 (5.9) / X' -0.6 (4.2) | c=0.85: L3M -7.0 / L6M -5.5 / HOLD -4.4 / PRE -2.3 / X' -1.5 | L6M 0.19 (p95 cut 10%, rule -26%); PRE 0.25; X' 0.35; n=200 | HOLD -12% PRE -7% X' +12%: NO | no (L6M maxDD cut -26%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 100/5261, L6M 11/1194, PRE 42/3049, X' 46/901 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +26% PRE -5% X' +8% vs expanding L6M +26% PRE -7% X' +12% |
| HM(H6) skipBot3 sig_st1_dist_atr [shadow] | as-is stack | L3M 88->88 (-0%) / L6M 88->88 (-0%) / HOLD 144->131 (-9%) / PRE 162->140 (-14%) / X' 317->331 (+5%) / ALL 317->331 (+5%) | PRE -811->-747 / X' -572->-569 / ALL -1161->-1081 | L3M -0.6 (8.0) / L6M +0.9 (6.4) / HOLD +0.6 (5.6) / PRE -0.4 (2.9) / X' -0.2 (2.3) | c=1.07: L3M +0.2 / L6M +2.6 / HOLD +2.2 / PRE +1.0 / X' -0.4 | L6M 0.81 (p95 cut 25%, rule 0%); PRE 0.43; X' 0.70; n=200 | HOLD -9% PRE -14% X' +5%: NO | no (L6M maxDD cut 0%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 114/4056, L6M 10/909, PRE 72/2285, X' 32/763 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD -0% PRE -14% X' +5% vs expanding L6M -0% PRE -14% X' +5% |
| HM(H6) skipBot3 sig_st1_dist_atr [shadow] | Sunday composite | L3M 21->25 (+16%) / L6M 23->25 (+8%) / HOLD 97->102 (+6%) / PRE 241->221 (-8%) / X' 121->122 (+1%) / ALL 241->221 (-8%) | PRE -875->-827 / X' -420->-432 / ALL -1098->-1043 | L3M -2.9 (6.8) / L6M -0.9 (4.5) / HOLD -1.4 (3.9) / PRE -0.8 (2.5) / X' -0.3 (2.2) | c=1.11: L3M -1.2 / L6M +1.6 / HOLD +1.4 / PRE -0.6 / X' +0.5 | L6M 0.29 (p95 cut 12%, rule -8%); PRE 0.28; X' 0.77; n=200 | HOLD +6% PRE -8% X' +1%: NO | no (L6M maxDD cut -8%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 114/4056, L6M 10/909, PRE 72/2285, X' 32/763 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +8% PRE -8% X' -17% vs expanding L6M +8% PRE -8% X' +1% |

**Plain reading (lock off).** None of the four shipped rules is a RISK-KEEP in either frame; no L6M maxDD cut beats the same-volume placebo (lowest placebo rank 0.075, PE sizeHi on the composite; the L6M "cut" there is -2%). Same-lot L6M maxDD change, expanding tercile, as-is / composite: HM slope -17% / +44%; KB +2% / +32%; PE sizeHi -14% / +2%; HM dist (shadow) 0% / +8% (negative = smaller). The as-is cuts (HM slope -17%, PE -14%) are inside the placebo (rank 0.26 and 0.25: random skips of the same size cut as much) and reverse in PRE (HM slope +19%, PE +18% deeper) and X' (all four +5% to +9% deeper). On the Sunday composite the frame's own maxDD is already 23k (one week), and every rule leaves it equal or deeper in L6M. Mean changes are inside MDE everywhere (so the mean test gives no information either way); same-lot L6M mean change $k/wk as-is +1.5 / +0.9 / +1.1 / +2.3 (HM slope / HM dist / KB / PE), composite -1.0 / -0.9 / +0.1 / +2.2. Equal-risk (L6M, ALL worst-20 matched): as-is +1.4 / +2.6 / +1.5 / +0.8; composite -1.0 / +1.6 / +0.1 / -2.5. Reading: a consistency test of rules chosen on the recent windows: the trade-level lean is not turned into a drawdown reduction beyond chance by the lock engine. The L6M maxDD of each frame is one week, so a short-history/frozen variant moves it by tens of points (HM slope as-is L6M cut +17% expanding vs -2% frozen/short-history), which is itself the finding on tercile sensitivity: the risk line is not robust to how the tercile is cut. The per-contract table shows the rule books' net pts per contract rising in L3M/L6M/HOLD and falling or flat in PRE for HM slope (PRE 3.05 -> 0.57 as-is), the same recent-regime pattern EINT1 already reported.

## Combined week lock 12R (on base and rule)
| rule | frame | maxDD $k before->after (change) by window | worst-20 $k (tail windows PRE / X' / ALL) | mean change $k/wk (MDE) | EQUAL-RISK mean change | placebo rank | HOLD/PRE/X' agree | RISK-KEEP | research (frozen 12m) vs expanding tercile |
|---|---|---|---|---|---|---|---|---|---|
| HM(H6) skipBot3 sig_slope [live] | as-is stack | L3M 105->94 (-11%) / L6M 116->94 (-19%) / HOLD 116->94 (-19%) / PRE 276->219 (-21%) / X' 436->395 (-9%) / ALL 436->395 (-9%) | PRE -585->-583 / X' -584->-582 / ALL -590->-588 | L3M +0.9 (4.8) / L6M +3.8 (8.6) / HOLD +2.5 (7.6) / PRE +1.0 (5.5) / X' +1.9 (5.6) | c=1.00: L3M +0.9 / L6M +3.9 / HOLD +2.6 / PRE +1.0 / X' +1.9 | L6M 0.30 (p95 cut 26%, rule 19%); PRE 0.30; X' 0.10; n=10 | HOLD -19% PRE -21% X' -9%: sign only | no (L6M maxDD cut 19%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 229/4056, L6M 32/909, PRE 138/2285, X' 54/763 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD -19% PRE -18% X' -10% vs expanding L6M -19% PRE -21% X' -9% |
| HM(H6) skipBot3 sig_slope [live] | Sunday composite | L3M 27->25 (-7%) / L6M 27->25 (-7%) / HOLD 35->33 (-6%) / PRE 233->205 (-12%) / X' 120->132 (+10%) / ALL 233->205 (-12%) | PRE -608->-617 / X' -468->-484 / ALL -688->-696 | L3M -0.2 (5.6) / L6M -1.6 (6.0) / HOLD -2.0 (5.3) / PRE -2.5 (4.8) / X' -1.0 (1.7) | c=0.99: L3M -8.4 / L6M -5.3 / HOLD -5.3 / PRE -4.2 / X' -1.0 | L6M 0.00 (p95 cut -5%, rule 7%); PRE 0.00; X' 0.60; n=10 | HOLD -6% PRE -12% X' +10%: NO | no (L6M maxDD cut 7%<20%; HOLD/PRE/X' do not all cut >=20%) | ALL 229/4056, L6M 32/909, PRE 138/2285, X' 54/763 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD -7% PRE -12% X' +18% vs expanding L6M -7% PRE -12% X' +10% |
| KB(K6) skipTop3 sig_st1_dist_atr [live] | as-is stack | L3M 105->58 (-45%) / L6M 116->87 (-24%) / HOLD 116->89 (-23%) / PRE 276->279 (+1%) / X' 436->468 (+7%) / ALL 436->468 (+7%) | PRE -585->-588 / X' -584->-584 / ALL -590->-594 | L3M +10.1 (16.2) / L6M +4.4 (10.3) / HOLD +3.2 (9.2) / PRE +1.1 (5.2) / X' -0.9 (3.0) | c=0.99: L3M +10.0 / L6M +4.3 / HOLD +3.1 / PRE +1.0 / X' -0.9 | L6M 0.00 (p95 cut 10%, rule 24%); PRE 0.60; X' 0.70; n=10 | HOLD -23% PRE +1% X' +7%: NO | no (HOLD/PRE/X' do not all cut >=20%) | ALL 87/5400, L6M 1/1257, PRE 32/3093, X' 54/933 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD -24% PRE +2% X' +2% vs expanding L6M -24% PRE +1% X' +7% |
| KB(K6) skipTop3 sig_st1_dist_atr [live] | Sunday composite | L3M 27->44 (+64%) / L6M 27->44 (+64%) / HOLD 35->44 (+24%) / PRE 233->249 (+7%) / X' 120->141 (+18%) / ALL 233->249 (+7%) | PRE -608->-671 / X' -468->-500 / ALL -688->-742 | L3M -1.8 (7.3) / L6M +3.9 (12.7) / HOLD +2.5 (11.5) / PRE -2.5 (5.5) / X' -0.3 (4.1) | c=0.93: L3M -7.6 / L6M -0.8 / HOLD -1.2 / PRE -4.0 / X' -0.1 | L6M 0.80 (p95 cut 13%, rule -64%); PRE 0.70; X' 0.70; n=10 | HOLD +24% PRE +7% X' +18%: NO | no (L6M maxDD cut -64%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 87/5400, L6M 1/1257, PRE 32/3093, X' 54/933 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +64% PRE +7% X' +11% vs expanding L6M +64% PRE +7% X' +18% |
| PE(P6) sizeHi sig_st1_dist_atr x1.5 top / x0.5 bottom [live] | as-is stack | L3M 105->133 (+27%) / L6M 116->133 (+15%) / HOLD 116->133 (+15%) / PRE 276->313 (+13%) / X' 436->430 (-2%) / ALL 436->531 (+22%) | PRE -585->-599 / X' -584->-583 / ALL -590->-601 | L3M -0.0 (23.7) / L6M +2.0 (15.3) / HOLD +2.2 (13.7) / PRE -2.8 (8.7) / X' -1.4 (5.0) | c=0.98: L3M -0.1 / L6M +1.8 / HOLD +1.9 / PRE -2.9 / X' -1.2 | L6M 1.00 (p95 cut 25%, rule -15%); PRE 0.30; X' 0.30; n=10 | HOLD +15% PRE +13% X' -2%: NO | no (L6M maxDD cut -15%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 100/5261, L6M 11/1194, PRE 42/3049, X' 46/901 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +15% PRE +29% X' +2% vs expanding L6M +15% PRE +13% X' -2% |
| PE(P6) sizeHi sig_st1_dist_atr x1.5 top / x0.5 bottom [live] | Sunday composite | L3M 27->144 (+440%) / L6M 27->111 (+318%) / HOLD 35->111 (+215%) / PRE 233->198 (-15%) / X' 120->111 (-7%) / ALL 233->198 (-15%) | PRE -608->-701 / X' -468->-475 / ALL -688->-787 | L3M -16.7 (24.8) / L6M -0.4 (17.5) / HOLD +2.6 (16.9) / PRE +0.9 (7.8) / X' +1.4 (5.5) | c=0.83: L3M -19.8 / L6M -8.4 / HOLD -5.6 / PRE -1.7 / X' -0.4 | L6M 0.70 (p95 cut -55%, rule -318%); PRE 0.50; X' 0.20; n=10 | HOLD +215% PRE -15% X' -7%: NO | no (L6M maxDD cut -318%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 100/5261, L6M 11/1194, PRE 42/3049, X' 46/901 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +318% PRE -15% X' +22% vs expanding L6M +318% PRE -15% X' -7% |
| PE(P6) sizeHi sig_st1_dist_atr x1.5 top / x0.5 bottom [live] ; VARIANT top-tercile x1.5 only | as-is stack | L3M 105->117 (+12%) / L6M 116->117 (+1%) / HOLD 116->117 (+1%) / PRE 276->440 (+59%) / X' 436->433 (-1%) / ALL 436->600 (+38%) | PRE -585->-591 / X' -584->-584 / ALL -590->-593 | L3M +0.9 (9.2) / L6M +3.9 (7.2) / HOLD +3.5 (6.4) / PRE -3.4 (7.5) / X' -0.8 (5.4) | c=1.00: L3M +0.9 / L6M +3.9 / HOLD +3.4 / PRE -3.4 / X' -0.7 | L6M 0.90 (p95 cut 22%, rule -1%); PRE 0.70; X' 0.30; n=10 | HOLD +1% PRE +59% X' -1%: NO | no (L6M maxDD cut -1%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 100/5261, L6M 11/1194, PRE 42/3049, X' 46/901 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD -28% PRE +70% X' +7% vs expanding L6M +1% PRE +59% X' -1% |
| PE(P6) sizeHi sig_st1_dist_atr x1.5 top / x0.5 bottom [live] ; VARIANT top-tercile x1.5 only | Sunday composite | L3M 27->76 (+185%) / L6M 27->76 (+185%) / HOLD 35->76 (+115%) / PRE 233->210 (-10%) / X' 120->111 (-7%) / ALL 233->210 (-10%) | PRE -608->-691 / X' -468->-467 / ALL -688->-778 | L3M -13.0 (25.4) / L6M -2.9 (14.0) / HOLD -1.9 (12.3) / PRE +3.2 (6.6) / X' +1.9 (4.8) | c=0.88: L3M -17.4 / L6M -9.5 / HOLD -8.1 / PRE +0.4 / X' -0.2 | L6M 0.70 (p95 cut -41%, rule -185%); PRE 0.20; X' 0.10; n=10 | HOLD +115% PRE -10% X' -7%: NO | no (L6M maxDD cut -185%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 100/5261, L6M 11/1194, PRE 42/3049, X' 46/901 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +185% PRE -10% X' +3% vs expanding L6M +185% PRE -10% X' -7% |
| HM(H6) skipBot3 sig_st1_dist_atr [shadow] | as-is stack | L3M 105->81 (-23%) / L6M 116->81 (-30%) / HOLD 116->89 (-23%) / PRE 276->200 (-27%) / X' 436->508 (+16%) / ALL 436->508 (+16%) | PRE -585->-586 / X' -584->-583 / ALL -590->-591 | L3M +5.0 (19.5) / L6M +6.6 (12.4) / HOLD +5.0 (11.0) / PRE +2.3 (5.7) / X' -1.5 (2.5) | c=1.00: L3M +5.0 / L6M +6.6 / HOLD +5.0 / PRE +2.3 / X' -1.5 | L6M 0.00 (p95 cut 26%, rule 30%); PRE 0.10; X' 0.90; n=10 | HOLD -23% PRE -27% X' +16%: NO | no (HOLD/PRE/X' do not all cut >=20%) | ALL 114/4056, L6M 10/909, PRE 72/2285, X' 32/763 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD -30% PRE -29% X' +17% vs expanding L6M -30% PRE -27% X' +16% |
| HM(H6) skipBot3 sig_st1_dist_atr [shadow] | Sunday composite | L3M 27->46 (+72%) / L6M 27->46 (+72%) / HOLD 35->46 (+29%) / PRE 233->245 (+5%) / X' 120->133 (+11%) / ALL 233->245 (+5%) | PRE -608->-604 / X' -468->-491 / ALL -688->-711 | L3M -5.8 (7.8) / L6M +1.8 (15.4) / HOLD +1.3 (13.4) / PRE -1.8 (2.1) / X' +0.8 (5.3) | c=0.97: L3M -14.6 / L6M -3.5 / HOLD -3.3 / PRE -3.1 / X' +0.8 | L6M 1.00 (p95 cut 7%, rule -72%); PRE 0.90; X' 0.90; n=10 | HOLD +29% PRE +5% X' +11%: NO | no (L6M maxDD cut -72%<20%; HOLD/PRE/X' do not all cut >=20%; placebo not beaten) | ALL 114/4056, L6M 10/909, PRE 72/2285, X' 32/763 signals in a different bucket (A vs frozen); risk line frozen: L6M maxDD +72% PRE +5% X' +9% vs expanding L6M +72% PRE +5% X' +11% |


## Detail, lock OFF: maxDD, worst-20, SD, Calmar (mean/maxDD), mean/|worst-20|, mean, equal-risk, every window ($k)
| rule | frame | window | maxDD before->after | worst-20 before->after | SD before->after | Calmar before->after | mean/|worst-20| before->after | mean before->after (change, MDE) | equal-risk mean change |
|---|---|---|---|---|---|---|---|---|---|
| HM_skipBot3_sig_slope | as-is stack | L3M | 88->73 | n/a (<20 losing weeks) | 46->45 | 0.138->0.171 | -->- | 12->12 (+0.3, 7.1) | +0.3 |
| HM_skipBot3_sig_slope | as-is stack | L6M | 88->73 | n/a (<20 losing weeks) | 44->44 | 0.247->0.318 | -->- | 22->23 (+1.5, 5.8) | +1.4 |
| HM_skipBot3_sig_slope | as-is stack | HOLD | 144->142 | n/a (<20 losing weeks) | 54->53 | 0.152->0.158 | 0.117->0.139 | 22->22 (+0.6, 5.1) | +0.5 |
| HM_skipBot3_sig_slope | as-is stack | PRE | 162->193 | -811->-850 | 50->49 | 0.115->0.084 | 0.023->0.019 | 19->16 (-2.4, 2.9) | -2.5 |
| HM_skipBot3_sig_slope | as-is stack | X' | 317->345 | -572->-591 | 29->30 | -0.011->-0.010 | -0.006->-0.006 | -3->-3 (+0.1, 2.9) | +0.1 |
| HM_skipBot3_sig_slope | as-is stack | ALL | 317->345 | -1161->-1164 | 47->46 | 0.041->0.035 | 0.011->0.010 | 13->12 (-1.1, 2.0) | -1.1 |
| HM_skipBot3_sig_slope | Sunday composite | L3M | 21->33 | n/a (<20 losing weeks) | 45->45 | 1.611->0.992 | -->- | 34->33 (-1.8, 10.0) | -1.8 |
| HM_skipBot3_sig_slope | Sunday composite | L6M | 23->33 | n/a (<20 losing weeks) | 43->45 | 1.797->1.221 | -->- | 41->40 (-1.0, 5.3) | -1.0 |
| HM_skipBot3_sig_slope | Sunday composite | HOLD | 97->113 | n/a (<20 losing weeks) | 52->54 | 0.398->0.325 | -->- | 39->37 (-1.8, 4.7) | -1.8 |
| HM_skipBot3_sig_slope | Sunday composite | PRE | 241->270 | -875->-894 | 56->55 | 0.096->0.080 | 0.026->0.024 | 23->22 (-1.4, 2.1) | -1.4 |
| HM_skipBot3_sig_slope | Sunday composite | X' | 121->121 | -420->-397 | 33->31 | 0.066->0.063 | 0.019->0.019 | 8->8 (-0.3, 2.2) | -0.3 |
| HM_skipBot3_sig_slope | Sunday composite | ALL | 241->270 | -1098->-1088 | 50->50 | 0.092->0.078 | 0.020->0.019 | 22->21 (-1.2, 1.6) | -1.2 |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | L3M | 88->90 | n/a (<20 losing weeks) | 46->48 | 0.138->0.184 | -->- | 12->17 (+4.4, 4.3) | +4.7 |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | L6M | 88->90 | n/a (<20 losing weeks) | 44->44 | 0.247->0.254 | -->- | 22->23 (+1.1, 3.8) | +1.5 |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | HOLD | 144->137 | n/a (<20 losing weeks) | 54->53 | 0.152->0.164 | 0.117->0.125 | 22->22 (+0.6, 3.7) | +1.0 |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | PRE | 162->153 | -811->-768 | 50->50 | 0.115->0.125 | 0.023->0.025 | 19->19 (+0.6, 3.0) | +1.0 |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | X' | 317->345 | -572->-593 | 29->29 | -0.011->-0.012 | -0.006->-0.007 | -3->-4 (-0.9, 2.5) | -0.9 |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | ALL | 317->345 | -1161->-1141 | 47->47 | 0.041->0.038 | 0.011->0.012 | 13->13 (+0.2, 1.8) | +0.4 |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | L3M | 21->24 | n/a (<20 losing weeks) | 45->44 | 1.611->1.474 | -->- | 34->35 (+0.9, 4.0) | +0.9 |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | L6M | 23->30 | n/a (<20 losing weeks) | 43->41 | 1.797->1.365 | -->- | 41->41 (+0.1, 3.8) | +0.1 |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | HOLD | 97->81 | n/a (<20 losing weeks) | 52->49 | 0.398->0.481 | -->- | 39->39 (+0.3, 3.5) | +0.3 |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | PRE | 241->256 | -875->-888 | 56->56 | 0.096->0.087 | 0.026->0.025 | 23->22 (-0.7, 2.8) | -0.5 |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | X' | 121->121 | -420->-426 | 33->32 | 0.066->0.059 | 0.019->0.017 | 8->7 (-0.9, 1.9) | -0.9 |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | ALL | 241->256 | -1098->-1086 | 50->50 | 0.092->0.085 | 0.020->0.020 | 22->22 (-0.5, 1.7) | -0.4 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | L3M | 88->76 | n/a (<20 losing weeks) | 46->50 | 0.138->0.225 | -->- | 12->17 (+4.9, 16.3) | +3.8 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | L6M | 88->76 | n/a (<20 losing weeks) | 44->49 | 0.247->0.316 | -->1.389 | 22->24 (+2.3, 11.4) | +0.8 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | HOLD | 144->157 | n/a (<20 losing weeks) | 54->60 | 0.152->0.153 | 0.117->0.091 | 22->24 (+2.1, 10.4) | +0.6 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | PRE | 162->191 | -811->-980 | 50->51 | 0.115->0.084 | 0.023->0.016 | 19->16 (-2.6, 8.4) | -3.7 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | X' | 317->334 | -572->-626 | 29->32 | -0.011->-0.011 | -0.006->-0.006 | -3->-4 (-0.4, 8.4) | -0.2 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | ALL | 317->334 | -1161->-1240 | 47->50 | 0.041->0.036 | 0.011->0.010 | 13->12 (-1.0, 5.4) | -1.8 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | L3M | 21->36 | n/a (<20 losing weeks) | 45->53 | 1.611->0.873 | -->- | 34->31 (-3.0, 23.0) | -6.1 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | L6M | 23->23 | n/a (<20 losing weeks) | 43->43 | 1.797->1.852 | -->- | 41->43 (+2.2, 12.4) | -2.5 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | HOLD | 97->77 | n/a (<20 losing weeks) | 52->53 | 0.398->0.539 | -->- | 39->41 (+2.9, 11.3) | -1.6 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | PRE | 241->200 | -875->-1008 | 56->62 | 0.096->0.110 | 0.026->0.022 | 23->22 (-1.1, 8.6) | -3.6 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | X' | 121->156 | -420->-551 | 33->35 | 0.066->0.036 | 0.019->0.010 | 8->6 (-2.3, 5.2) | -3.2 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | ALL | 241->200 | -1098->-1185 | 50->55 | 0.092->0.108 | 0.020->0.018 | 22->22 (-0.6, 5.1) | -3.1 |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | L3M | 88->88 | n/a (<20 losing weeks) | 46->46 | 0.138->0.132 | -->- | 12->12 (-0.6, 8.0) | +0.2 |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | L6M | 88->88 | n/a (<20 losing weeks) | 44->44 | 0.247->0.258 | -->- | 22->23 (+0.9, 6.4) | +2.6 |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | HOLD | 144->131 | n/a (<20 losing weeks) | 54->53 | 0.152->0.172 | 0.117->0.131 | 22->22 (+0.6, 5.6) | +2.2 |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | PRE | 162->140 | -811->-747 | 50->48 | 0.115->0.130 | 0.023->0.024 | 19->18 (-0.4, 2.9) | +1.0 |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | X' | 317->331 | -572->-569 | 29->28 | -0.011->-0.011 | -0.006->-0.006 | -3->-4 (-0.2, 2.3) | -0.4 |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | ALL | 317->331 | -1161->-1081 | 47->45 | 0.041->0.039 | 0.011->0.012 | 13->13 (-0.1, 2.0) | +0.9 |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | L3M | 21->25 | n/a (<20 losing weeks) | 45->41 | 1.611->1.269 | -->- | 34->31 (-2.9, 6.8) | -1.2 |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | L6M | 23->25 | n/a (<20 losing weeks) | 43->42 | 1.797->1.623 | -->- | 41->40 (-0.9, 4.5) | +1.6 |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | HOLD | 97->102 | n/a (<20 losing weeks) | 52->51 | 0.398->0.363 | -->- | 39->37 (-1.4, 3.9) | +1.4 |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | PRE | 241->221 | -875->-827 | 56->52 | 0.096->0.101 | 0.026->0.027 | 23->22 (-0.8, 2.5) | -0.6 |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | X' | 121->122 | -420->-432 | 33->33 | 0.066->0.062 | 0.019->0.018 | 8->8 (-0.3, 2.2) | +0.5 |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | ALL | 241->221 | -1098->-1043 | 50->48 | 0.092->0.097 | 0.020->0.021 | 22->21 (-0.8, 1.6) | +0.1 |

## Detail, lock 12R
| rule | frame | window | maxDD before->after | worst-20 before->after | SD before->after | Calmar before->after | mean/|worst-20| before->after | mean before->after (change, MDE) | equal-risk mean change |
|---|---|---|---|---|---|---|---|---|---|
| HM_skipBot3_sig_slope | as-is stack | L3M | 105->94 | n/a (<20 losing weeks) | 41->41 | 0.037->0.051 | -->- | 4->5 (+0.9, 4.8) | +0.9 |
| HM_skipBot3_sig_slope | as-is stack | L6M | 116->94 | n/a (<20 losing weeks) | 46->46 | 0.089->0.152 | 0.040->0.091 | 10->14 (+3.8, 8.6) | +3.9 |
| HM_skipBot3_sig_slope | as-is stack | HOLD | 116->94 | n/a (<20 losing weeks) | 53->52 | 0.118->0.173 | 0.032->0.046 | 14->16 (+2.5, 7.6) | +2.6 |
| HM_skipBot3_sig_slope | as-is stack | PRE | 276->219 | -585->-583 | 47->46 | 0.035->0.049 | 0.017->0.018 | 10->11 (+1.0, 5.5) | +1.0 |
| HM_skipBot3_sig_slope | as-is stack | X' | 436->395 | -584->-582 | 26->28 | -0.017->-0.013 | -0.012->-0.009 | -7->-5 (+1.9, 5.6) | +1.9 |
| HM_skipBot3_sig_slope | as-is stack | ALL | 436->395 | -590->-588 | 44->44 | 0.013->0.018 | 0.010->0.012 | 6->7 (+1.6, 3.6) | +1.6 |
| HM_skipBot3_sig_slope | Sunday composite | L3M | 27->25 | n/a (<20 losing weeks) | 48->47 | 1.089->1.160 | -->- | 29->29 (-0.2, 5.6) | -8.4 |
| HM_skipBot3_sig_slope | Sunday composite | L6M | 27->25 | n/a (<20 losing weeks) | 45->46 | 1.212->1.235 | -->- | 32->31 (-1.6, 6.0) | -5.3 |
| HM_skipBot3_sig_slope | Sunday composite | HOLD | 35->33 | n/a (<20 losing weeks) | 49->49 | 0.889->0.889 | 5.047->0.631 | 31->29 (-2.0, 5.3) | -5.3 |
| HM_skipBot3_sig_slope | Sunday composite | PRE | 233->205 | -608->-617 | 50->48 | 0.065->0.062 | 0.025->0.020 | 15->13 (-2.5, 4.8) | -4.2 |
| HM_skipBot3_sig_slope | Sunday composite | X' | 120->132 | -468->-484 | 30->30 | 0.009->0.001 | 0.002->0.000 | 1->0 (-1.0, 1.7) | -1.0 |
| HM_skipBot3_sig_slope | Sunday composite | ALL | 233->205 | -688->-696 | 46->45 | 0.063->0.062 | 0.021->0.018 | 15->13 (-2.0, 2.7) | -3.5 |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | L3M | 105->58 | n/a (<20 losing weeks) | 41->42 | 0.037->0.242 | -->- | 4->14 (+10.1, 16.2) | +10.0 |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | L6M | 116->87 | n/a (<20 losing weeks) | 46->45 | 0.089->0.169 | 0.040->0.093 | 10->15 (+4.4, 10.3) | +4.3 |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | HOLD | 116->89 | n/a (<20 losing weeks) | 53->51 | 0.118->0.191 | 0.032->0.048 | 14->17 (+3.2, 9.2) | +3.1 |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | PRE | 276->279 | -585->-588 | 47->48 | 0.035->0.039 | 0.017->0.018 | 10->11 (+1.1, 5.2) | +1.0 |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | X' | 436->468 | -584->-584 | 26->24 | -0.017->-0.017 | -0.012->-0.014 | -7->-8 (-0.9, 3.0) | -0.9 |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | ALL | 436->468 | -590->-594 | 44->44 | 0.013->0.014 | 0.010->0.011 | 6->7 (+1.0, 3.4) | +0.9 |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | L3M | 27->44 | n/a (<20 losing weeks) | 48->50 | 1.089->0.623 | -->- | 29->27 (-1.8, 7.3) | -7.6 |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | L6M | 27->44 | n/a (<20 losing weeks) | 45->46 | 1.212->0.828 | -->- | 32->36 (+3.9, 12.7) | -0.8 |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | HOLD | 35->44 | n/a (<20 losing weeks) | 49->50 | 0.889->0.776 | 5.047->- | 31->34 (+2.5, 11.5) | -1.2 |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | PRE | 233->249 | -608->-671 | 50->51 | 0.065->0.051 | 0.025->0.019 | 15->13 (-2.5, 5.5) | -4.0 |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | X' | 120->141 | -468->-500 | 30->30 | 0.009->0.005 | 0.002->0.001 | 1->1 (-0.3, 4.1) | -0.1 |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | ALL | 233->249 | -688->-742 | 46->47 | 0.063->0.056 | 0.021->0.019 | 15->14 (-0.8, 3.9) | -2.3 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | L3M | 105->133 | n/a (<20 losing weeks) | 41->41 | 0.037->0.029 | -->- | 4->4 (-0.0, 23.7) | -0.1 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | L6M | 116->133 | n/a (<20 losing weeks) | 46->50 | 0.089->0.093 | 0.040->0.043 | 10->12 (+2.0, 15.3) | +1.8 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | HOLD | 116->133 | n/a (<20 losing weeks) | 53->58 | 0.118->0.120 | 0.032->0.037 | 14->16 (+2.2, 13.7) | +1.9 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | PRE | 276->313 | -585->-599 | 47->45 | 0.035->0.022 | 0.017->0.012 | 10->7 (-2.8, 8.7) | -2.9 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | X' | 436->430 | -584->-583 | 26->27 | -0.017->-0.020 | -0.012->-0.015 | -7->-9 (-1.4, 5.0) | -1.2 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | ALL | 436->531 | -590->-601 | 44->45 | 0.013->0.008 | 0.010->0.007 | 6->4 (-1.3, 5.4) | -1.4 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | L3M | 27->144 | n/a (<20 losing weeks) | 48->58 | 1.089->0.085 | -->- | 29->12 (-16.7, 24.8) | -19.8 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | L6M | 27->111 | n/a (<20 losing weeks) | 45->51 | 1.212->0.286 | -->- | 32->32 (-0.4, 17.5) | -8.4 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | HOLD | 35->111 | n/a (<20 losing weeks) | 49->55 | 0.889->0.305 | 5.047->10.271 | 31->34 (+2.6, 16.9) | -5.6 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | PRE | 233->198 | -608->-701 | 50->57 | 0.065->0.081 | 0.025->0.023 | 15->16 (+0.9, 7.8) | -1.7 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | X' | 120->111 | -468->-475 | 30->30 | 0.009->0.022 | 0.002->0.005 | 1->2 (+1.4, 5.5) | -0.4 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | ALL | 233->198 | -688->-787 | 46->52 | 0.063->0.081 | 0.021->0.020 | 15->16 (+1.4, 5.6) | -2.2 |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | L3M | 105->81 | n/a (<20 losing weeks) | 41->42 | 0.037->0.111 | -->- | 4->9 (+5.0, 19.5) | +5.0 |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | L6M | 116->81 | n/a (<20 losing weeks) | 46->46 | 0.089->0.210 | 0.040->0.204 | 10->17 (+6.6, 12.4) | +6.6 |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | HOLD | 116->89 | n/a (<20 losing weeks) | 53->52 | 0.118->0.210 | 0.032->0.065 | 14->19 (+5.0, 11.0) | +5.0 |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | PRE | 276->200 | -585->-586 | 47->46 | 0.035->0.060 | 0.017->0.021 | 10->12 (+2.3, 5.7) | +2.3 |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | X' | 436->508 | -584->-583 | 26->25 | -0.017->-0.017 | -0.012->-0.015 | -7->-9 (-1.5, 2.5) | -1.5 |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | ALL | 436->508 | -590->-591 | 44->44 | 0.013->0.015 | 0.010->0.013 | 6->8 (+1.8, 3.8) | +1.8 |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | L3M | 27->46 | n/a (<20 losing weeks) | 48->47 | 1.089->0.507 | -->- | 29->23 (-5.8, 7.8) | -14.6 |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | L6M | 27->46 | n/a (<20 losing weeks) | 45->47 | 1.212->0.745 | -->- | 32->34 (+1.8, 15.4) | -3.5 |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | HOLD | 35->46 | n/a (<20 losing weeks) | 49->50 | 0.889->0.716 | 5.047->- | 31->33 (+1.3, 13.4) | -3.3 |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | PRE | 233->245 | -608->-604 | 50->48 | 0.065->0.054 | 0.025->0.022 | 15->13 (-1.8, 2.1) | -3.1 |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | X' | 120->133 | -468->-491 | 30->31 | 0.009->0.014 | 0.002->0.004 | 1->2 (+0.8, 5.3) | +0.8 |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | ALL | 233->245 | -688->-711 | 46->45 | 0.063->0.058 | 0.021->0.020 | 15->14 (-0.4, 3.4) | -2.1 |

## PE sizeHi variant, top tercile x1.5 only (x1 elsewhere), lock off
| rule | frame | window | maxDD before->after | worst-20 before->after | SD before->after | Calmar before->after | mean/|worst-20| before->after | mean before->after (change, MDE) | equal-risk mean change |
|---|---|---|---|---|---|---|---|---|---|
| PE_sizeHi_sig_st1_dist_atr | as-is stack | L3M | 88->86 | n/a (<20 losing weeks) | 46->47 | 0.138->0.171 | -->- | 12->15 (+2.6, 10.7) | +1.3 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | L6M | 88->86 | n/a (<20 losing weeks) | 44->47 | 0.247->0.274 | -->- | 22->24 (+1.9, 6.8) | -0.1 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | HOLD | 144->155 | n/a (<20 losing weeks) | 54->57 | 0.152->0.151 | 0.117->0.122 | 22->23 (+1.4, 6.0) | -0.6 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | PRE | 162->199 | -811->-916 | 50->52 | 0.115->0.090 | 0.023->0.020 | 19->18 (-0.6, 5.8) | -2.2 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | X' | 317->344 | -572->-664 | 29->34 | -0.011->-0.012 | -0.006->-0.006 | -3->-4 (-0.7, 5.5) | -0.4 |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | ALL | 317->344 | -1161->-1270 | 47->50 | 0.041->0.037 | 0.011->0.010 | 13->13 (-0.2, 3.6) | -1.3 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | L3M | 21->27 | n/a (<20 losing weeks) | 45->49 | 1.611->1.147 | -->- | 34->31 (-3.6, 18.1) | -7.0 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | L6M | 23->29 | n/a (<20 losing weeks) | 43->45 | 1.797->1.481 | -->- | 41->43 (+1.5, 10.0) | -5.5 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | HOLD | 97->86 | n/a (<20 losing weeks) | 52->55 | 0.398->0.475 | -->- | 39->41 (+2.2, 8.9) | -4.4 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | PRE | 241->225 | -875->-1081 | 56->66 | 0.096->0.110 | 0.026->0.023 | 23->25 (+1.8, 5.9) | -2.3 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | X' | 121->135 | -420->-526 | 33->37 | 0.066->0.055 | 0.019->0.014 | 8->7 (-0.6, 4.2) | -1.5 |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | ALL | 241->225 | -1098->-1299 | 50->58 | 0.092->0.104 | 0.020->0.018 | 22->23 (+1.2, 3.7) | -2.5 |

## Per contract (lock off): contract-weighted net pts per contract of the rule's book (after fees and slip), lots = sum of final f (contract-proportional)
| rule (book) | frame | stat | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|
| HM_skipBot3_sig_slope | as-is stack | net pts per contract before->after (lots before->after) | 7.02->10.83 (50->34) | 5.92->11.78 (92->59) | 5.35->9.76 (104->64) | 3.05->0.57 (240->149) | -1.22->-1.62 (103->68) |
| HM_skipBot3_sig_slope | Sunday composite | net pts per contract before->after (lots before->after) | 11.89->15.50 (41->26) | 11.99->15.46 (70->45) | 11.14->12.57 (76->49) | 3.23->0.94 (166->113) | -0.69->-1.69 (60->43) |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | net pts per contract before->after (lots before->after) | -1.88->3.49 (45->39) | 3.50->5.55 (92->77) | 2.96->4.33 (102->85) | 4.56->6.30 (233->195) | -0.22->-1.88 (110->84) |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | net pts per contract before->after (lots before->after) | 3.02->5.48 (56->45) | 5.13->7.06 (103->81) | 4.33->6.33 (112->88) | 4.02->4.45 (243->191) | 1.04->-0.44 (92->72) |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | net pts per contract before->after (lots before->after) | 2.23->3.71 (142->152) | 3.73->4.37 (271->284) | 4.27->4.89 (308->318) | 2.47->1.45 (702->709) | -0.82->-1.01 (312->316) |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | net pts per contract before->after (lots before->after) | 6.56->5.43 (171->179) | 8.43->9.01 (301->306) | 8.49->9.46 (332->333) | 4.54->4.30 (702->673) | 3.32->2.06 (260->246) |
| PE_sizeHi_sig_st1_dist_atr (top only) | as-is stack | net pts per contract before->after (lots before->after) | 2.23->2.93 (142->152) | 3.73->4.13 (271->291) | 4.27->4.45 (308->333) | 2.47->2.03 (702->770) | -0.82->-1.04 (312->353) |
| PE_sizeHi_sig_st1_dist_atr (top only) | Sunday composite | net pts per contract before->after (lots before->after) | 6.56->4.65 (171->202) | 8.43->7.69 (301->349) | 8.49->8.00 (332->383) | 4.54->4.33 (702->842) | 3.32->2.64 (260->292) |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | net pts per contract before->after (lots before->after) | 7.02->9.04 (50->35) | 5.92->9.98 (92->64) | 5.35->8.78 (104->71) | 3.05->3.99 (240->159) | -1.22->-2.05 (103->74) |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | net pts per contract before->after (lots before->after) | 11.89->11.87 (41->28) | 11.99->16.36 (70->46) | 11.14->13.99 (76->50) | 3.23->2.01 (166->109) | -0.69->-2.91 (60->43) |

## Research (frozen trailing-12-month cut, one constant for all history) vs expanding tercile: effect on the risk line
The frozen cut is the numeric threshold in out/missed/eint1_policy_candidate.txt (HM slope<0.0942; KB dist>=3.299; PE dist>=2.649 / <1.522; HM dist<2.787) and uses future data for earlier history; the expanding rank is what a live chart computes. The short-history row (chart history starting 20250201, 100-signal warm-up) is a sensitivity only: the rule is inactive earlier, so PRE/X' are mostly unruled.
| rule | frame | lock | assignment | L6M maxDD cut | PRE | X' | L6M mean change (MDE) | equal-risk L6M | signals unruled |
|---|---|---|---|---|---|---|---|---|---|
| HM_skipBot3_sig_slope | as-is stack | off | expanding (EINT1 cell) | -17% | +19% | +9% | +1.5 (5.8) | +1.4 | - |
| HM_skipBot3_sig_slope | as-is stack | off | research = frozen trailing-12m cut | +2% | +16% | +9% | +0.5 (5.9) | - | - |
| HM_skipBot3_sig_slope | as-is stack | off | expanding, short chart history (from 20250201) | +2% | -0% | -0% | +0.8 (5.7) | - | - |
| HM_skipBot3_sig_slope | as-is stack | 12 | expanding (EINT1 cell) | -19% | -21% | -9% | +3.8 (8.6) | +3.9 | - |
| HM_skipBot3_sig_slope | as-is stack | 12 | research = frozen trailing-12m cut | -19% | -18% | -10% | +3.9 (9.1) | - | - |
| HM_skipBot3_sig_slope | as-is stack | 12 | expanding, short chart history (from 20250201) | -19% | -0% | -0% | +3.7 (8.7) | - | - |
| HM_skipBot3_sig_slope | Sunday composite | off | expanding (EINT1 cell) | +44% | +12% | -0% | -1.0 (5.3) | -1.0 | - |
| HM_skipBot3_sig_slope | Sunday composite | off | research = frozen trailing-12m cut | +44% | +8% | -11% | -1.5 (5.4) | - | - |
| HM_skipBot3_sig_slope | Sunday composite | off | expanding, short chart history (from 20250201) | +44% | -0% | -0% | -1.3 (5.4) | - | - |
| HM_skipBot3_sig_slope | Sunday composite | 12 | expanding (EINT1 cell) | -7% | -12% | +10% | -1.6 (6.0) | -5.3 | - |
| HM_skipBot3_sig_slope | Sunday composite | 12 | research = frozen trailing-12m cut | -7% | -12% | +18% | -1.9 (6.0) | - | - |
| HM_skipBot3_sig_slope | Sunday composite | 12 | expanding, short chart history (from 20250201) | -7% | -0% | -0% | -1.7 (6.1) | - | - |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | off | expanding (EINT1 cell) | +2% | -5% | +9% | +1.1 (3.8) | +1.5 | - |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | off | research = frozen trailing-12m cut | +2% | -5% | -0% | +1.1 (3.8) | - | - |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | off | expanding, short chart history (from 20250201) | +2% | -0% | -0% | +0.8 (3.8) | - | - |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | 12 | expanding (EINT1 cell) | -24% | +1% | +7% | +4.4 (10.3) | +4.3 | - |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | 12 | research = frozen trailing-12m cut | -24% | +2% | +2% | +4.4 (10.3) | - | - |
| KB_skipTop3_sig_st1_dist_atr | as-is stack | 12 | expanding, short chart history (from 20250201) | -24% | -0% | -0% | +4.0 (10.0) | - | - |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | off | expanding (EINT1 cell) | +32% | +6% | +0% | +0.1 (3.8) | +0.1 | - |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | off | research = frozen trailing-12m cut | +32% | +6% | -3% | +0.1 (3.8) | - | - |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | off | expanding, short chart history (from 20250201) | +32% | -0% | -0% | -0.1 (3.7) | - | - |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | 12 | expanding (EINT1 cell) | +64% | +7% | +18% | +3.9 (12.7) | -0.8 | - |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | 12 | research = frozen trailing-12m cut | +64% | +7% | +11% | +3.9 (12.7) | - | - |
| KB_skipTop3_sig_st1_dist_atr | Sunday composite | 12 | expanding, short chart history (from 20250201) | +64% | -0% | -0% | +3.9 (12.7) | - | - |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | off | expanding (EINT1 cell) | -14% | +18% | +6% | +2.3 (11.4) | +0.8 | - |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | off | research = frozen trailing-12m cut | -14% | +30% | -14% | +1.5 (11.7) | - | - |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | off | expanding, short chart history (from 20250201) | -14% | -0% | -0% | +1.5 (11.7) | - | - |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | 12 | expanding (EINT1 cell) | +15% | +13% | -2% | +2.0 (15.3) | +1.8 | - |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | 12 | research = frozen trailing-12m cut | +15% | +29% | +2% | +0.0 (16.1) | - | - |
| PE_sizeHi_sig_st1_dist_atr | as-is stack | 12 | expanding, short chart history (from 20250201) | +15% | -0% | -0% | +0.0 (16.1) | - | - |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | off | expanding (EINT1 cell) | +2% | -17% | +29% | +2.2 (12.4) | -2.5 | - |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | off | research = frozen trailing-12m cut | +2% | -16% | +10% | +1.6 (12.4) | - | - |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | off | expanding, short chart history (from 20250201) | +2% | -0% | -0% | +1.6 (12.4) | - | - |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | 12 | expanding (EINT1 cell) | +318% | -15% | -7% | -0.4 (17.5) | -8.4 | - |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | 12 | research = frozen trailing-12m cut | +318% | -15% | +22% | -0.9 (17.4) | - | - |
| PE_sizeHi_sig_st1_dist_atr | Sunday composite | 12 | expanding, short chart history (from 20250201) | +313% | -0% | -0% | -0.9 (17.4) | - | - |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | off | expanding (EINT1 cell) | -0% | -14% | +5% | +0.9 (6.4) | +2.6 | - |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | off | research = frozen trailing-12m cut | -0% | -14% | +5% | +0.7 (6.4) | - | - |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | off | expanding, short chart history (from 20250201) | -0% | -0% | -0% | +1.1 (6.7) | - | - |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | 12 | expanding (EINT1 cell) | -30% | -27% | +16% | +6.6 (12.4) | +6.6 | - |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | 12 | research = frozen trailing-12m cut | -30% | -29% | +17% | +6.4 (12.2) | - | - |
| HM_skipBot3_sig_st1_dist_atr | as-is stack | 12 | expanding, short chart history (from 20250201) | -30% | -0% | -0% | +6.7 (12.6) | - | - |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | off | expanding (EINT1 cell) | +8% | -8% | +1% | -0.9 (4.5) | +1.6 | - |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | off | research = frozen trailing-12m cut | +8% | -8% | -17% | -0.9 (4.5) | - | - |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | off | expanding, short chart history (from 20250201) | +8% | -0% | -0% | -0.8 (4.5) | - | - |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | 12 | expanding (EINT1 cell) | +72% | +5% | +11% | +1.8 (15.4) | -3.5 | - |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | 12 | research = frozen trailing-12m cut | +72% | +5% | +9% | +1.8 (15.4) | - | - |
| HM_skipBot3_sig_st1_dist_atr | Sunday composite | 12 | expanding, short chart history (from 20250201) | +72% | -0% | -0% | +1.9 (15.4) | - | - |

### Signals in a different bucket
| rule | comparison | window | ranked in both | different tercile bucket | different rule action | A unranked (first 100) |
|---|---|---|---|---|---|---|
| HM_skipBot3_sig_slope | A_vs_C | ALL | 4056 | 229 | 110 | 100 |
| HM_skipBot3_sig_slope | A_vs_C | L6M | 909 | 32 | 19 | 0 |
| HM_skipBot3_sig_slope | A_vs_C | PRE | 2285 | 138 | 67 | 0 |
| HM_skipBot3_sig_slope | A_vs_C | X | 763 | 54 | 21 | 100 |
| HM_skipBot3_sig_slope | A_vs_B | ALL | 1761 | 55 | 24 | 100 |
| HM_skipBot3_sig_slope | A_vs_B | L6M | 909 | 28 | 16 | 0 |
| HM_skipBot3_sig_slope | A_vs_B | PRE | 753 | 26 | 8 | 0 |
| HM_skipBot3_sig_slope | A_vs_B | X | 0 | 0 | 0 | 100 |
| KB_skipTop3_sig_st1_dist_atr | A_vs_C | ALL | 5400 | 87 | 58 | 100 |
| KB_skipTop3_sig_st1_dist_atr | A_vs_C | L6M | 1257 | 1 | 0 | 0 |
| KB_skipTop3_sig_st1_dist_atr | A_vs_C | PRE | 3093 | 32 | 21 | 0 |
| KB_skipTop3_sig_st1_dist_atr | A_vs_C | X | 933 | 54 | 37 | 100 |
| KB_skipTop3_sig_st1_dist_atr | A_vs_B | ALL | 2500 | 45 | 30 | 100 |
| KB_skipTop3_sig_st1_dist_atr | A_vs_B | L6M | 1257 | 12 | 11 | 0 |
| KB_skipTop3_sig_st1_dist_atr | A_vs_B | PRE | 1126 | 32 | 18 | 0 |
| KB_skipTop3_sig_st1_dist_atr | A_vs_B | X | 0 | 0 | 0 | 100 |
| PE_sizeHi_sig_st1_dist_atr | A_vs_C | ALL | 5261 | 100 | 100 | 100 |
| PE_sizeHi_sig_st1_dist_atr | A_vs_C | L6M | 1194 | 11 | 11 | 0 |
| PE_sizeHi_sig_st1_dist_atr | A_vs_C | PRE | 3049 | 42 | 42 | 0 |
| PE_sizeHi_sig_st1_dist_atr | A_vs_C | X | 901 | 46 | 46 | 100 |
| PE_sizeHi_sig_st1_dist_atr | A_vs_B | ALL | 2447 | 47 | 47 | 100 |
| PE_sizeHi_sig_st1_dist_atr | A_vs_B | L6M | 1194 | 14 | 14 | 0 |
| PE_sizeHi_sig_st1_dist_atr | A_vs_B | PRE | 1136 | 30 | 30 | 0 |
| PE_sizeHi_sig_st1_dist_atr | A_vs_B | X | 0 | 0 | 0 | 100 |
| HM_skipBot3_sig_st1_dist_atr | A_vs_C | ALL | 4056 | 114 | 29 | 100 |
| HM_skipBot3_sig_st1_dist_atr | A_vs_C | L6M | 909 | 10 | 1 | 0 |
| HM_skipBot3_sig_st1_dist_atr | A_vs_C | PRE | 2285 | 72 | 19 | 0 |
| HM_skipBot3_sig_st1_dist_atr | A_vs_C | X | 763 | 32 | 9 | 100 |
| HM_skipBot3_sig_st1_dist_atr | A_vs_B | ALL | 1761 | 48 | 13 | 100 |
| HM_skipBot3_sig_st1_dist_atr | A_vs_B | L6M | 909 | 13 | 2 | 0 |
| HM_skipBot3_sig_st1_dist_atr | A_vs_B | PRE | 753 | 34 | 10 | 0 |
| HM_skipBot3_sig_st1_dist_atr | A_vs_B | X | 0 | 0 | 0 | 100 |