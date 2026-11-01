# DS3_DD_REREAD_A7 - A1's 101 old-frame as-is stored-stack RISK-KEEP leads re-run on the one-convention engine at live lots (A7, 2026-11-01). POST-HOC, Shadow/NEEDS only, no PASS

Prereg `l2vast/ds3/prereg/A7_DDREREAD_prereg.md` sha256 7c15801c34c45a8886bcb5c06a9ebcdf6a35fb87615bbfd7ee735b09586697fe (DECISIONS.md, before any risk statistic). dead_lookup before the runs (all 101 leads are already in DEAD_CELLS: out/dd_reread/a7/dead_lookup_leads.csv), append_cells after. Masks capped 20260206, no post-cap file opened. Code `l2vast/ds3/code/ddre_a7/`, out `l2vast/ds3/out/dd_reread/a7/`, per-lead table `a7_leads.csv`, all 5,778 re-run cell-frames `a7_all.parquet`.

**Plain sentence.** I re-simulated the fired rows of A1's 101 leads (not scaled, on the lock engine at live lots, frames: as-is, as-is+70/30 for S73-base stack cells, Sunday composite) and also every other cell of their sweeps (L2SE 2,179, STACK2 202, SP1 364, EINT2 time-in-session 84, CUTW PE 60). Of the 101: **20 survive as RISK-KEEP in the as-is frame (carried on PRE and X', L6M cut >= 20% with mean inside MDE, placebo beaten), another 18 meet every criterion but have a volume share under 1% so the same-volume placebo is not applicable (not counted), 62 more lose the label outright and EINT1 (oracle, not a rule) is not re-run, and in the Sunday composite frame 0 are RISK-KEEP** (the composite already takes that drawdown, as A1 found for the rest). **Only 4 of the 20 survivors have a stable +-1-step neighbourhood: 16 are fragile.** 52 of 100 re-run leads change the sign of at least one of (L6M cut, PRE cut, X' cut, L6M mean) vs A1 (L6M cut 12, PRE cut 5, X' cut 2, L6M mean 37); the label changes for 81 of 101. Nothing is a PASS; the as-is stack's L6M maxDD (88k) is one week (2026-01-19) and PRE/X' are a few episodes, so a cut there says "the rule skipped or reshaped those trades", which the volume placebo cannot separate when the share is under 3%.

## Page 1 - survivors, top 30 recent-first (strict RISK-KEEP first, then placebo-n/a; sorted by L6M maxDD cut). Units $k. Family-wise p = Westfall-Young over ALL swept cells of the family in that frame (200 draws), swept count beside it
| rule | frame | maxDD $k before→after | worst-20 ALL $k | mean Δ $k/wk (MDE) | equal-risk mean Δ L6M | placebo rank | PRE/X' agree | neighbourhood | family-wise p / swept | D6/D7 mapping or gap |
|---|---|---|---|---|---|---|---|---|---|---|
| L2SE_main 1369 fam=F4/X=5/N=1/chase=px8/stop=orig/veto=v4 | A | L6M 88→32 · PRE 162→111 · X' 317→139 | ALL -1161→-1012 | L6M +2.6 (11.2) · ALL -0.2 (4.8) | +6.1 (c=1.15) | vol 0% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 32% X' 56%) | FRAGILE (nbrs carried 43%, meet 86%, n=7) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: N-of-8 L2 class gate (ABS/ICE/PRINT/SWEEP/MICRO classes are NOT in D6; imb5, pulled_sup10, delta60 are); imb5 veto (in D6); price chase (price only) |
| L2SE_main 1645 fam=F4/X=5/N=0/chase=px8/stop=orig/veto=v4 | A | L6M 88→33 · PRE 162→113 · X' 317→144 | ALL -1161→-1012 | L6M +2.6 (11.1) · ALL +0.3 (4.9) | +6.2 (c=1.15) | vol 0% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 30% X' 55%) | FRAGILE (nbrs carried 60%, meet 80%, n=5) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: imb5 veto (in D6); price chase (price only) |
| L2SE_main 1391 fam=F4/X=5/N=1/chase=dlt8/stop=orig/veto=v4 | A | L6M 88→35 · PRE 162→110 · X' 317→146 | ALL -1161→-1021 | L6M +1.2 (11.4) · ALL -0.6 (4.9) | +4.3 (c=1.14) | vol 0% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 32% X' 54%) | FRAGILE (nbrs carried 43%, meet 86%, n=7) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: N-of-8 L2 class gate (ABS/ICE/PRINT/SWEEP/MICRO classes are NOT in D6; imb5, pulled_sup10, delta60 are); imb5 veto (in D6); chase on delta 10s/30s (D6 has delta60 only: gap) |
| L2SE_main 1667 fam=F4/X=5/N=0/chase=dlt8/stop=orig/veto=v4 | A | L6M 88→35 · PRE 162→109 · X' 317→143 | ALL -1161→-1019 | L6M +1.2 (11.2) · ALL -0.1 (5.0) | +4.4 (c=1.14) | vol 0% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 33% X' 55%) | FRAGILE (nbrs carried 40%, meet 80%, n=5) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: imb5 veto (in D6); chase on delta 10s/30s (D6 has delta60 only: gap) |
| L2SE_main 1657 fam=F4/X=5/N=0/chase=imb5/stop=orig/veto=v4 | A | L6M 88→36 · PRE 162→102 · X' 317→169 | ALL -1161→-1059 | L6M +2.0 (12.0) · ALL -0.6 (5.1) | +4.3 (c=1.10) | vol 0% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 37% X' 47%) | FRAGILE (nbrs carried 60%, meet 100%, n=5) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: imb5 veto (in D6); chase on imb5>=.2 (in D6) |
| L2SE_main 1682 fam=F4/X=5/N=0/chase=2of85/stop=fill/veto=v4 | A | L6M 88→36 · PRE 162→123 · X' 317→135 | ALL -1161→-1122 | L6M -1.3 (15.6) · ALL -1.9 (5.7) | -0.6 (c=1.04) | vol 1% · L6M 0.5% PRE 2.0% X' 0.5% | yes (PRE 24% X' 57%) | FRAGILE (nbrs carried 60%, meet 60%, n=5) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: imb5 veto (in D6); chase on 2-of-8 L2 classes (gap) |
| L2SE_main 1463 fam=F4/X=5/N=3/chase=px10/stop=orig/veto=v4 | A | L6M 88→37 · PRE 162→102 · X' 317→180 | ALL -1161→-960 | L6M +4.8 (12.4) · ALL +0.1 (5.6) | +10.4 (c=1.21) | vol 2% · L6M 0.5% PRE 0.5% X' 0.5% | yes (PRE 37% X' 43%) | FRAGILE (nbrs carried 33%, meet 83%, n=6) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: N-of-8 L2 class gate (ABS/ICE/PRINT/SWEEP/MICRO classes are NOT in D6; imb5, pulled_sup10, delta60 are); imb5 veto (in D6); price chase (price only) |
| L2SE_main 1485 fam=F4/X=5/N=3/chase=dlt10/stop=orig/veto=v4 | A | L6M 88→39 · PRE 162→100 · X' 317→180 | ALL -1161→-975 | L6M +4.5 (12.2) · ALL +0.0 (5.6) | +9.5 (c=1.19) | vol 2% · L6M 0.5% PRE 0.5% X' 0.5% | yes (PRE 38% X' 43%) | FRAGILE (nbrs carried 20%, meet 80%, n=5) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: N-of-8 L2 class gate (ABS/ICE/PRINT/SWEEP/MICRO classes are NOT in D6; imb5, pulled_sup10, delta60 are); imb5 veto (in D6); chase on delta 10s/30s (D6 has delta60 only: gap) |
| L2SE_main 1475 fam=F4/X=5/N=3/chase=imb8/stop=orig/veto=v4 | A | L6M 88→40 · PRE 162→115 · X' 317→157 | ALL -1161→-987 | L6M +8.4 (13.8) · ALL +2.2 (5.7) | +13.7 (c=1.18) | vol 2% · L6M 0.5% PRE 1.0% X' 0.5% | yes (PRE 29% X' 50%) | FRAGILE (nbrs carried 33%, meet 83%, n=6) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: N-of-8 L2 class gate (ABS/ICE/PRINT/SWEEP/MICRO classes are NOT in D6; imb5, pulled_sup10, delta60 are); imb5 veto (in D6); chase on imb5>=.2 (in D6) |
| L2SE_main 1501 fam=F4/X=5/N=3/chase=2of810/stop=orig/veto=v4 | A | L6M 88→44 · PRE 162→116 · X' 317→172 | ALL -1161→-993 | L6M +4.2 (15.2) · ALL +1.0 (5.8) | +8.5 (c=1.17) | vol 1% · L6M 0.5% PRE 1.0% X' 0.5% | yes (PRE 28% X' 46%) | FRAGILE (nbrs carried 40%, meet 80%, n=5) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: N-of-8 L2 class gate (ABS/ICE/PRINT/SWEEP/MICRO classes are NOT in D6; imb5, pulled_sup10, delta60 are); imb5 veto (in D6); chase on 2-of-8 L2 classes (gap) |
| L2SE_main 1644 fam=F4/X=5/N=0/chase=px5/stop=fill/veto=v4 | A | L6M 88→44 · PRE 162→121 · X' 317→114 | ALL -1161→-1113 | L6M -0.7 (15.8) · ALL -1.9 (5.5) | +0.2 (c=1.04) | vol 2% · L6M 0.5% PRE 1.5% X' 0.5% | yes (PRE 25% X' 64%) | STABLE (nbrs carried 80%, meet 60%, n=5) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: imb5 veto (in D6); price chase (price only) |
| L2SE_main 314 fam=F1/X=3/b=iii/prof=dflt/N=3/veto=v6 | A | L6M 88→45 · PRE 162→126 · X' 317→172 | ALL -1161→-1029 | L6M +2.8 (14.9) · ALL +0.4 (5.8) | +6.0 (c=1.13) | vol 0% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 22% X' 46%) | FRAGILE (nbrs carried 56%, meet 44%, n=9) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: N-of-8 L2 class gate (ABS/ICE/PRINT/SWEEP/MICRO classes are NOT in D6; imb5, pulled_sup10, delta60 are); imb5 veto (in D6) |
| L2SE_main 315 fam=F1/X=3/b=iii/prof=dflt/N=3/veto=none | A | L6M 88→45 · PRE 162→126 · X' 317→172 | ALL -1161→-1029 | L6M +2.8 (14.9) · ALL +0.4 (5.8) | +6.0 (c=1.13) | vol 0% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 22% X' 46%) | FRAGILE (nbrs carried 62%, meet 38%, n=8) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: N-of-8 L2 class gate (ABS/ICE/PRINT/SWEEP/MICRO classes are NOT in D6; imb5, pulled_sup10, delta60 are) |
| L2SE_main 1499 fam=F4/X=5/N=3/chase=2of88/stop=orig/veto=v4 | A | L6M 88→45 · PRE 162→121 · X' 317→166 | ALL -1161→-963 | L6M +4.8 (15.2) · ALL +0.4 (5.8) | +10.3 (c=1.21) | vol 3% · L6M 0.5% PRE 3.0% X' 0.5% | yes (PRE 25% X' 48%) | FRAGILE (nbrs carried 33%, meet 83%, n=6) | WY p 0.020 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: N-of-8 L2 class gate (ABS/ICE/PRINT/SWEEP/MICRO classes are NOT in D6; imb5, pulled_sup10, delta60 are); imb5 veto (in D6); chase on 2-of-8 L2 classes (gap) |
| STACK2 5 | A | L6M 88→48 · PRE 162→121 · X' 317→122 | ALL -1161→-1071 | L6M -1.6 (8.7) · ALL -0.3 (4.0) | +0.1 (c=1.08) | vol 0% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 25% X' 62%) | FRAGILE (nbrs carried 50%, meet 100%, n=4) | WY p 0.005 / swept 85 | D6 cut piece (Asia-stopped 50%) generalised; NEEDS cross-book state (stop event + open same-side books shared across the K6/P6/U6/H6/M6/A6 charts) |
| STACK2 4 | A | L6M 88→48 · PRE 162→121 · X' 317→122 | ALL -1161→-1071 | L6M -1.6 (8.7) · ALL -0.3 (4.0) | +0.1 (c=1.08) | vol 0% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 25% X' 62%) | FRAGILE (nbrs carried 50%, meet 100%, n=4) | WY p 0.005 / swept 85 | D6 cut piece (Asia-stopped 50%) generalised; NEEDS cross-book state (stop event + open same-side books shared across the K6/P6/U6/H6/M6/A6 charts) |
| STACK2 74 | A73 | L6M 77→42 · PRE 133→97 · X' 248→117 | ALL -1110→-1052 | L6M -3.6 (8.0) · ALL -1.4 (3.8) | -2.6 (c=1.06) | vol 1% · L6M 0.5% PRE 0.5% X' 0.5% | yes (PRE 27% X' 53%) | FRAGILE (nbrs carried 50%, meet 100%, n=4) | WY p 0.005 / swept 117 | D6 cut piece (Asia-stopped 50%) generalised; NEEDS cross-book state (stop event + open same-side books shared across the K6/P6/U6/H6/M6/A6 charts) |
| STACK2 75 | A73 | L6M 77→42 · PRE 133→97 · X' 248→117 | ALL -1110→-1052 | L6M -3.6 (8.0) · ALL -1.4 (3.8) | -2.6 (c=1.06) | vol 1% · L6M 0.5% PRE 0.5% X' 0.5% | yes (PRE 27% X' 53%) | FRAGILE (nbrs carried 50%, meet 100%, n=4) | WY p 0.005 / swept 117 | D6 cut piece (Asia-stopped 50%) generalised; NEEDS cross-book state (stop event + open same-side books shared across the K6/P6/U6/H6/M6/A6 charts) |
| L2SE_main 1453 fam=F4/X=5/N=2/chase=2of88/stop=orig/veto=v4 | A | L6M 88→52 · PRE 162→105 · X' 317→149 | ALL -1161→-983 | L6M +0.8 (14.5) · ALL -0.0 (5.6) | +4.8 (c=1.18) | vol 2% · L6M 0.5% PRE 0.5% X' 0.5% | yes (PRE 35% X' 53%) | STABLE (nbrs carried 71%, meet 71%, n=7) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: N-of-8 L2 class gate (ABS/ICE/PRINT/SWEEP/MICRO classes are NOT in D6; imb5, pulled_sup10, delta60 are); imb5 veto (in D6); chase on 2-of-8 L2 classes (gap) |
| SP1B S73_178 | A73 | L6M 77→46 · PRE 133→92 · X' 248→122 | ALL -1110→-983 | L6M -1.6 (10.5) · ALL +0.0 (4.6) | +0.9 (c=1.13) | vol 2% · L6M 0.5% PRE 0.5% X' 0.5% | yes (PRE 31% X' 51%) | FRAGILE (nbrs carried 0%, meet 100%, n=1) | WY p 0.005 / swept 182 | stack-level rule: cut rest of same-side books on first stop (as STACK2); NEEDS cross-book state |
| STACK2 76 | A73 | L6M 77→46 · PRE 133→92 · X' 248→122 | ALL -1110→-983 | L6M -1.6 (10.5) · ALL +0.0 (4.6) | +0.9 (c=1.13) | vol 2% · L6M 0.5% PRE 0.5% X' 0.5% | yes (PRE 31% X' 51%) | FRAGILE (nbrs carried 60%, meet 80%, n=5) | WY p 0.005 / swept 117 | D6 cut piece (Asia-stopped 50%) generalised; NEEDS cross-book state (stop event + open same-side books shared across the K6/P6/U6/H6/M6/A6 charts) |
| STACK2 77 | A73 | L6M 77→46 · PRE 133→92 · X' 248→122 | ALL -1110→-983 | L6M -1.6 (10.5) · ALL +0.0 (4.6) | +0.9 (c=1.13) | vol 2% · L6M 0.5% PRE 0.5% X' 0.5% | yes (PRE 31% X' 51%) | FRAGILE (nbrs carried 60%, meet 80%, n=5) | WY p 0.005 / swept 117 | D6 cut piece (Asia-stopped 50%) generalised; NEEDS cross-book state (stop event + open same-side books shared across the K6/P6/U6/H6/M6/A6 charts) |
| L2SE_main 1429 fam=F4/X=5/N=2/chase=imb8/stop=orig/veto=v4 | A | L6M 88→54 · PRE 162→106 · X' 317→139 | ALL -1161→-1032 | L6M +4.2 (12.5) · ALL +1.5 (5.3) | +7.5 (c=1.13) | vol 1% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 35% X' 56%) | FRAGILE (nbrs carried 43%, meet 86%, n=7) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: N-of-8 L2 class gate (ABS/ICE/PRINT/SWEEP/MICRO classes are NOT in D6; imb5, pulled_sup10, delta60 are); imb5 veto (in D6); chase on imb5>=.2 (in D6) |
| STACK2 180 | A | L6M 88→55 · PRE 162→127 · X' 317→143 | ALL -1161→-996 | L6M +0.8 (10.3) · ALL +1.9 (4.0) | +4.5 (c=1.17) | vol 0% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 22% X' 55%) | FRAGILE (nbrs carried 0%, meet 100%, n=3) | WY p 0.005 / swept 85 | D6 cut piece (Asia-stopped 50%) generalised; NEEDS cross-book state (stop event + open same-side books shared across the K6/P6/U6/H6/M6/A6 charts) |
| STACK2 23 | A | L6M 88→59 · PRE 162→113 · X' 317→123 | ALL -1161→-1038 | L6M +2.3 (9.5) · ALL +0.7 (4.3) | +5.2 (c=1.12) | vol 2% · L6M 1.0% PRE 0.5% X' 0.5% | yes (PRE 30% X' 61%) | FRAGILE (nbrs carried 33%, meet 100%, n=3) | WY p 0.005 / swept 85 | D6 cut piece (Asia-stopped 50%) generalised; NEEDS cross-book state (stop event + open same-side books shared across the K6/P6/U6/H6/M6/A6 charts) |
| STACK2 20 | A | L6M 88→59 · PRE 162→129 · X' 317→119 | ALL -1161→-1018 | L6M +0.2 (7.3) · ALL +1.6 (3.2) | +3.3 (c=1.14) | vol 0% · L6M 0.5% PRE 1.0% X' 0.5% (placebo n/a) | yes (PRE 21% X' 62%) | STABLE (nbrs carried 100%, meet 100%, n=2) | WY p 0.005 / swept 85 | D6 cut piece (Asia-stopped 50%) generalised; NEEDS cross-book state (stop event + open same-side books shared across the K6/P6/U6/H6/M6/A6 charts) |
| L2SE_main 1455 fam=F4/X=5/N=2/chase=2of810/stop=orig/veto=v4 | A | L6M 88→59 · PRE 162→112 · X' 317→146 | ALL -1161→-1020 | L6M +2.0 (14.1) · ALL +0.7 (5.3) | +5.3 (c=1.14) | vol 0% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 31% X' 54%) | FRAGILE (nbrs carried 50%, meet 67%, n=6) | WY p 0.005 / swept 2167 | D6 entry section (dip / split / chase parameters, X dip pts, stop at original level); needs: N-of-8 L2 class gate (ABS/ICE/PRINT/SWEEP/MICRO classes are NOT in D6; imb5, pulled_sup10, delta60 are); imb5 veto (in D6); chase on 2-of-8 L2 classes (gap) |
| STACK2 195 | A73 | L6M 77→57 · PRE 133→86 · X' 248→97 | ALL -1110→-969 | L6M +0.8 (10.6) · ALL +2.0 (3.7) | +4.0 (c=1.15) | vol 1% · L6M 0.5% PRE 0.5% X' 0.5% (placebo n/a) | yes (PRE 36% X' 61%) | STABLE (nbrs carried 67%, meet 100%, n=3) | WY p 0.005 / swept 117 | D6 cut piece (Asia-stopped 50%) generalised; NEEDS cross-book state (stop event + open same-side books shared across the K6/P6/U6/H6/M6/A6 charts) |
| STACK2 9 | A | L6M 88→65 · PRE 162→129 · X' 317→178 | ALL -1161→-1014 | L6M -0.9 (7.7) · ALL -0.0 (3.3) | +2.1 (c=1.15) | vol 1% · L6M 0.5% PRE 0.5% X' 0.5% | yes (PRE 20% X' 44%) | STABLE (nbrs carried 100%, meet 100%, n=2) | WY p 0.005 / swept 85 | D6 cut piece (Asia-stopped 50%) generalised; NEEDS cross-book state (stop event + open same-side books shared across the K6/P6/U6/H6/M6/A6 charts) |
| STACK2 19 | A | L6M 88→65 · PRE 162→103 · X' 317→128 | ALL -1161→-1077 | L6M -2.5 (7.5) · ALL +0.2 (3.7) | -1.0 (c=1.08) | vol 2% · L6M 1.5% PRE 0.5% X' 0.5% | yes (PRE 37% X' 60%) | STABLE (nbrs carried 100%, meet 67%, n=3) | WY p 0.005 / swept 85 | D6 cut piece (Asia-stopped 50%) generalised; NEEDS cross-book state (stop event + open same-side books shared across the K6/P6/U6/H6/M6/A6 charts) |

`*` after c = equal-risk lot scale not converged to 3% (engine integer rounding). Equal-risk = engine lot table re-run at the scale that matches the ALL worst-20 of the baseline; the number is the L6M mean change vs the baseline at that risk.

## Counts by family (101 leads)
| a1_family | leads | rerun | strict | placebo_na | carry | meets | sign_any | stable |
|---|---|---|---|---|---|---|---|---|
| CUTW | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 |
| EINT1 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| EINT2 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |
| L2SE_main | 59 | 59 | 11 | 13 | 38 | 39 | 24 | 4 |
| SP1B | 8 | 8 | 1 | 0 | 1 | 8 | 5 | 2 |
| STACK2 | 31 | 31 | 8 | 5 | 15 | 26 | 22 | 8 |

## Whole sweeps re-run (honest denominators; every cell in both frames)
| fam | frame | swept | carried | meets | carry_meets | rk | rk_na | wy_le05 |
|---|---|---|---|---|---|---|---|---|
| CUTW_PE | A | 60 | 45 | 21 | 19 | 0 | 0 | 0 |
| CUTW_PE | C | 60 | 32 | 0 | 0 | 0 | 0 | 6 |
| EINT2f | A | 84 | 2 | 2 | 0 | 0 | 0 | 0 |
| EINT2f | C | 84 | 3 | 1 | 0 | 0 | 0 | 0 |
| L2SE_f7 | A | 12 | 3 | 7 | 0 | 0 | 0 | 0 |
| L2SE_f7 | C | 12 | 0 | 3 | 0 | 0 | 0 | 0 |
| L2SE_main | A | 2167 | 280 | 813 | 132 | 45 | 65 | 300 |
| L2SE_main | C | 2167 | 131 | 229 | 3 | 0 | 0 | 120 |
| SP1 | A | 182 | 17 | 94 | 15 | 8 | 1 | 11 |
| SP1 | A73 | 182 | 3 | 82 | 1 | 1 | 0 | 2 |
| SP1 | C | 364 | 12 | 2 | 0 | 0 | 0 | 2 |
| STACK2 | A | 85 | 23 | 38 | 17 | 4 | 12 | 28 |
| STACK2 | A73 | 117 | 8 | 46 | 7 | 6 | 1 | 13 |
| STACK2 | C | 202 | 0 | 10 | 0 | 0 | 0 | 10 |

Reading: 'carried' = PRE and X' maxDD cut >= 20% with mean inside MDE (selection stat, PRE+X' only); 'meets' = the user's L6M definition (one recent look); rk = strict RISK-KEEP, rk_na = placebo n/a (volume share < 1%); wy_le05 = cells with family-wise p <= 0.05. The control cell (market-equivalent dip X=0, no gate) shows the noise floor: L6M cut +10%, PRE +11%, X' -4% with no real rule.

## Tie-outs (done before trusting any re-run)
T0 no-change: A, A73, C and every hook identity (entry layer = frame's own; empty skip mask; frame's own stack rule; S73 cell as entry layer in C) give delta EXACTLY 0.0 on the 745-day series; A and C equal oc_res ASIS|off and COMP|s0.25|k670|off exactly (0.0).
T1 L2SE (59 leads, program pipeline = old engine, research lots, measured basis): max per-trade NET diff vs stored grid 3.8e-06 pts; max daily diff vs stored engine_main CELL 0.0039 $; per-contract gain (pts/planned lot, 4 books) max rel diff L6M/HOLD/PRE/X' = 5.5e-04/2.6e-05/1.3e-05/4.9e-05; stack mean delta max rel diff 2.6e-05 (tolerance 1%: PASS).
T2 STACK2 (31): max daily diff 0.0038 $, mean delta max rel diff 6.4e-06; SP1B (8): 0.0038 $, 1.5e-04 (tolerance 1%: PASS). EINT2/CUTW: row masks and cut outputs are taken from the programs' own stored/kernel outputs (CUTW kernel+chain re-run from the program code; 5361/5361 PE signals map 1:1 to engine rows); the 'stored per-contract gain' for these two was not independently re-derived (stated).

## Method (short)
Entry cells: the program's own kernel replaces the entry layer of HM KB SM PE rows (MV, PB as the frame has them), engine rows, basis N, stop 2.45 (A) / parity (C), integer lots; stack cells: the program's own stack simulator inside the engine's stack-rule slot (cross-book same-side state); EINT2: skip rows from the programs' own time-in-session features; CUTW: the program's cut/blackout chain mapped 1:1 to PE engine rows (C frame: PE NY-session rows excluded, approximate). Metrics, windows, MDE as in DD-1. Labels/CARRY/MEETS exactly as A1. Placebo: first-order random skip of the same daily-volume share, 200 draws, per-draw interpolation on the realised share; plus the uniform size-cut test (cut > share). Neighbours: swept cells one ordinal step away on one parameter (STACK2: registered adjacency, condition on/off counted as the loosest step; stopdef is a no-op and not stepped; duplicates such as P50 stopdef0/1 are the same rule and appear twice in the counts). STABLE = >= 2/3 of neighbours carried and >= 1/2 meet.

## Caveats (read these)
1. Volume share is measured on daily gross P&L; the leads change which dollars occur, not how many (share 0-3%), so a random skip of that size is a very weak null (ranks 0.0%). RISK-KEEP here means the cut is not a volume cut; it does not mean the cut is out-of-sample safe. Whole-sweep carried counts are large (L2SE as-is 280 of 2,167 carried) and the as-is baseline's drawdown is dominated by few episodes.
2. The placebo is first-order (no engine re-run per draw); equal-risk uses engine lots.
3. R-trigger SP1 cells are evaluated at the program's research-lot R scale (feature gap); EINT1 netOneORACLE_5m is a non-causal oracle: not a rule.
4. Composite frame for L2SE F5 cells with F=0.7 uses the integer live split fractions; other F raw.
5. Shadow/NEEDS only: the survivors' D6/D7 mapping or gap is in the last column; STACK2/SP1 first-stop cuts need cross-book state; L2SE class gates need L2 classes D6 lacks (price-only variants map to the D6 entry section).

## All 101 leads: A1 (stored frame) vs A7 (engine re-run), as-is frame. Cuts L6M / PRE / X', L6M mean Δ $k
| lead | A1 cuts | A1 mean | A7 cuts | A7 mean (MDE) | A7 label | composite label | stable |
|---|---|---|---|---|---|---|---|
| EINT1 netOneORACLE_5m | 26/28/60 | +3.6 | not re-run (oracle) | - | NOT-A-RULE | - | - |
| EINT2 f.firstN30only.asia | 28/40/23 | -3.6 | 10/7/4 | -14.1 (19.1) | no | no | no |
| L2SE_main 152 fam=F1/X=2/b=iii/prof=loose/N=3/veto=v3 | 26/24/58 | -2.6 | -13/16/58 | -5.4 (12.0) | no | no | no |
| L2SE_main 153 fam=F1/X=2/b=iii/prof=loose/N=3/veto=v4 | 26/24/58 | -2.6 | -13/16/58 | -5.4 (12.0) | no | no | no |
| L2SE_main 154 fam=F1/X=2/b=iii/prof=loose/N=3/veto=v6 | 26/24/58 | -2.6 | -13/16/58 | -5.4 (12.0) | no | no | no |
| L2SE_main 155 fam=F1/X=2/b=iii/prof=loose/N=3/veto=none | 26/24/58 | -2.6 | -13/16/58 | -5.4 (12.0) | no | no | no |
| L2SE_main 168 fam=F1/X=2/b=iii/prof=dflt/N=3/veto=v3 | 21/30/47 | -0.0 | -20/29/55 | -1.5 (14.3) | no | no | no |
| L2SE_main 169 fam=F1/X=2/b=iii/prof=dflt/N=3/veto=v4 | 21/30/47 | -0.0 | -20/29/55 | -1.5 (14.3) | no | no | no |
| L2SE_main 170 fam=F1/X=2/b=iii/prof=dflt/N=3/veto=v6 | 21/30/47 | -0.0 | -20/38/55 | -1.5 (14.3) | no | no | no |
| L2SE_main 171 fam=F1/X=2/b=iii/prof=dflt/N=3/veto=none | 21/30/47 | -0.0 | -20/38/55 | -1.5 (14.3) | no | no | no |
| L2SE_main 312 fam=F1/X=3/b=iii/prof=dflt/N=3/veto=v3 | 53/30/46 | +2.9 | 49/15/46 | +2.8 (14.9) | RISK-KEEP (L6M only) | no | no |
| L2SE_main 313 fam=F1/X=3/b=iii/prof=dflt/N=3/veto=v4 | 53/30/46 | +2.9 | 49/15/46 | +2.8 (14.9) | RISK-KEEP (L6M only) | no | no |
| L2SE_main 314 fam=F1/X=3/b=iii/prof=dflt/N=3/veto=v6 | 53/32/46 | +2.9 | 49/22/46 | +2.8 (14.9) | RISK-KEEP (placebo n/a) | no | no |
| L2SE_main 315 fam=F1/X=3/b=iii/prof=dflt/N=3/veto=none | 53/32/46 | +2.9 | 49/22/46 | +2.8 (14.9) | RISK-KEEP (placebo n/a) | no | no |
| L2SE_main 932 fam=F1/X=2/b=iii/M=10/prof=dflt/N=3/veto=v4 | 27/33/38 | -1.9 | -5/29/62 | -5.5 (11.7) | no | no | no |
| L2SE_main 934 fam=F1/X=3/b=iii/M=10/prof=dflt/N=3/veto=v4 | 25/24/35 | +0.9 | 13/29/54 | -0.5 (12.4) | no | no | no |
| L2SE_main 1121 fam=F2/gate=DLT_10_30/X=5/b=iii/veto=v4 | 21/24/34 | +6.6 | 18/26/38 | +6.0 (17.0) | no | no | no |
| L2SE_main 1369 fam=F4/X=5/N=1/chase=px8/stop=orig/veto=v4 | 60/25/25 | -1.2 | 63/32/56 | +2.6 (11.2) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | no |
| L2SE_main 1371 fam=F4/X=5/N=1/chase=px10/stop=orig/veto=v4 | 41/32/24 | -1.3 | 23/33/49 | +2.8 (13.2) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | no |
| L2SE_main 1390 fam=F4/X=5/N=1/chase=dlt5/stop=fill/veto=v4 | 36/21/29 | -2.0 | 24/21/57 | -1.0 (16.6) | RISK-KEEP | no | no |
| L2SE_main 1391 fam=F4/X=5/N=1/chase=dlt8/stop=orig/veto=v4 | 58/23/24 | -2.2 | 61/32/54 | +1.2 (11.4) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | no |
| L2SE_main 1393 fam=F4/X=5/N=1/chase=dlt10/stop=orig/veto=v4 | 41/24/25 | -0.8 | 23/36/49 | +2.4 (13.0) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | no |
| L2SE_main 1414 fam=F4/X=5/N=2/chase=px5/stop=fill/veto=v4 | 50/28/25 | -1.8 | 55/20/59 | -1.8 (16.3) | RISK-KEEP (L6M only) | RISK-KEEP (L6M only) | no |
| L2SE_main 1429 fam=F4/X=5/N=2/chase=imb8/stop=orig/veto=v4 | 29/22/28 | +2.5 | 39/35/56 | +4.2 (12.5) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | no |
| L2SE_main 1436 fam=F4/X=5/N=2/chase=dlt5/stop=fill/veto=v4 | 48/28/24 | -2.3 | 23/28/57 | -2.1 (17.3) | RISK-KEEP | RISK-KEEP (L6M only) | no |
| L2SE_main 1449 fam=F4/X=5/N=2/chase=2of83/stop=orig/veto=v4 | 38/26/26 | -0.3 | 28/3/41 | -0.9 (11.8) | RISK-KEEP (L6M only) | no | no |
| L2SE_main 1453 fam=F4/X=5/N=2/chase=2of88/stop=orig/veto=v4 | 40/31/30 | -0.7 | 41/35/53 | +0.8 (14.5) | RISK-KEEP | RISK-KEEP (L6M only) | yes |
| L2SE_main 1455 fam=F4/X=5/N=2/chase=2of810/stop=orig/veto=v4 | 31/27/20 | +0.8 | 32/31/54 | +2.0 (14.1) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | no |
| L2SE_main 1463 fam=F4/X=5/N=3/chase=px10/stop=orig/veto=v4 | 45/49/26 | +3.3 | 57/37/43 | +4.8 (12.4) | RISK-KEEP | RISK-KEEP (L6M only) | no |
| L2SE_main 1475 fam=F4/X=5/N=3/chase=imb8/stop=orig/veto=v4 | 44/23/33 | +6.5 | 54/29/50 | +8.4 (13.8) | RISK-KEEP | RISK-KEEP (L6M only) | no |
| L2SE_main 1485 fam=F4/X=5/N=3/chase=dlt10/stop=orig/veto=v4 | 43/49/27 | +3.1 | 56/38/43 | +4.5 (12.2) | RISK-KEEP | RISK-KEEP (L6M only) | no |
| L2SE_main 1487 fam=F4/X=5/N=3/chase=prt3/stop=orig/veto=v4 | 50/26/38 | +1.8 | 40/11/34 | +0.1 (18.5) | RISK-KEEP (L6M only) | no | no |
| L2SE_main 1489 fam=F4/X=5/N=3/chase=prt5/stop=orig/veto=v4 | 50/26/35 | +1.6 | 40/11/31 | -0.1 (18.9) | RISK-KEEP (L6M only) | no | no |
| L2SE_main 1491 fam=F4/X=5/N=3/chase=prt8/stop=orig/veto=v4 | 47/27/37 | +1.9 | 39/16/26 | +1.8 (18.3) | RISK-KEEP (L6M only) | no | no |
| L2SE_main 1493 fam=F4/X=5/N=3/chase=prt10/stop=orig/veto=v4 | 42/27/37 | +2.9 | 39/17/27 | +1.5 (18.0) | RISK-KEEP (L6M only) | no | no |
| L2SE_main 1499 fam=F4/X=5/N=3/chase=2of88/stop=orig/veto=v4 | 46/24/30 | +3.3 | 49/25/48 | +4.8 (15.2) | RISK-KEEP | RISK-KEEP (L6M only) | no |
| L2SE_main 1501 fam=F4/X=5/N=3/chase=2of810/stop=orig/veto=v4 | 38/25/28 | +4.2 | 50/28/46 | +4.2 (15.2) | RISK-KEEP | RISK-KEEP (L6M only) | no |
| L2SE_main 1533 fam=F4/X=10/N=1/chase=prt3/stop=orig/veto=v4 | 40/21/21 | +0.2 | -5/23/19 | +0.4 (21.4) | no | no | no |
| L2SE_main 1537 fam=F4/X=10/N=1/chase=prt8/stop=orig/veto=v4 | 40/22/21 | +0.5 | 14/16/19 | +2.6 (21.3) | no | no | no |
| L2SE_main 1644 fam=F4/X=5/N=0/chase=px5/stop=fill/veto=v4 | 44/36/34 | -0.5 | 50/25/64 | -0.7 (15.8) | RISK-KEEP | RISK-KEEP (L6M only) | yes |
| L2SE_main 1645 fam=F4/X=5/N=0/chase=px8/stop=orig/veto=v4 | 59/36/30 | -1.7 | 63/30/55 | +2.6 (11.1) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | no |
| L2SE_main 1647 fam=F4/X=5/N=0/chase=px10/stop=orig/veto=v4 | 41/45/27 | -0.4 | 22/32/50 | +3.7 (12.4) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | yes |
| L2SE_main 1648 fam=F4/X=5/N=0/chase=px10/stop=fill/veto=v4 | 55/22/47 | -3.5 | 12/21/53 | -0.1 (15.6) | no | no | no |
| L2SE_main 1657 fam=F4/X=5/N=0/chase=imb5/stop=orig/veto=v4 | 27/30/22 | -1.2 | 59/37/47 | +2.0 (12.0) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | no |
| L2SE_main 1664 fam=F4/X=5/N=0/chase=dlt3/stop=fill/veto=v4 | 25/24/20 | -4.4 | -8/17/29 | -7.0 (15.2) | no | no | no |
| L2SE_main 1666 fam=F4/X=5/N=0/chase=dlt5/stop=fill/veto=v4 | 44/21/34 | -0.7 | 23/15/61 | -0.5 (16.2) | RISK-KEEP (L6M only) | RISK-KEEP (L6M only) | no |
| L2SE_main 1667 fam=F4/X=5/N=0/chase=dlt8/stop=orig/veto=v4 | 57/37/30 | -3.0 | 61/33/55 | +1.2 (11.2) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | no |
| L2SE_main 1669 fam=F4/X=5/N=0/chase=dlt10/stop=orig/veto=v4 | 41/45/28 | -0.0 | 22/35/50 | +3.3 (12.1) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | yes |
| L2SE_main 1670 fam=F4/X=5/N=0/chase=dlt10/stop=fill/veto=v4 | 55/22/48 | -3.6 | 12/21/54 | -0.1 (15.1) | no | no | no |
| L2SE_main 1679 fam=F4/X=5/N=0/chase=2of83/stop=orig/veto=v4 | 22/22/23 | -2.0 | 25/10/39 | -3.8 (10.5) | RISK-KEEP (L6M only) | no | no |
| L2SE_main 1682 fam=F4/X=5/N=0/chase=2of85/stop=fill/veto=v4 | 39/28/33 | -5.3 | 59/24/57 | -1.3 (15.6) | RISK-KEEP | no | no |
| L2SE_main 1974 fam=F5/F=0.5/X=10/N=0/chase=px20/veto=v4 | 50/23/33 | +3.7 | 39/21/23 | -1.5 (11.7) | RISK-KEEP (volume effect) | no | no |
| L2SE_main 2046 fam=F5/F=0.7/X=5/N=0/chase=px20/veto=v4 | 23/28/24 | +1.8 | 24/37/18 | +1.7 (6.3) | RISK-KEEP (L6M only) | no | no |
| L2SE_main 2052 fam=F5/F=0.7/X=5/N=1/chase=px20/veto=v4 | 23/29/22 | +1.9 | 24/32/20 | +2.1 (6.7) | RISK-KEEP (L6M only) | no | no |
| L2SE_main 2085 fam=F5/F=0.7/X=8/N=3/chase=none/veto=v4 | 26/30/39 | +5.9 | 6/32/31 | +3.4 (10.7) | no | no | no |
| L2SE_main 2091 fam=F5/F=0.7/X=10/N=0/chase=none/veto=v4 | 26/39/46 | +5.2 | 11/35/35 | +2.4 (10.5) | no | no | no |
| L2SE_main 2097 fam=F5/F=0.7/X=10/N=1/chase=none/veto=v4 | 26/38/43 | +5.5 | 11/34/33 | +2.6 (11.0) | no | no | no |
| L2SE_main 2103 fam=F5/F=0.7/X=10/N=2/chase=none/veto=v4 | 28/36/40 | +6.7 | 14/29/31 | +4.1 (10.5) | no | no | no |
| L2SE_main 2109 fam=F5/F=0.7/X=10/N=3/chase=none/veto=v4 | 33/39/45 | +7.3 | 25/26/33 | +4.4 (10.6) | RISK-KEEP | no | no |
| L2SE_main 2115 fam=F5/F=0.7/X=15/N=0/chase=none/veto=v4 | 61/24/41 | +4.8 | 35/4/24 | +0.4 (11.0) | RISK-KEEP (L6M only) | no | no |
| L2SE_main 2121 fam=F5/F=0.7/X=15/N=1/chase=none/veto=v4 | 60/22/43 | +6.2 | 34/16/25 | +1.2 (11.6) | RISK-KEEP (L6M only) | no | no |
| STACK2 4 | 54/26/42 | +3.4 | 46/25/62 | -1.6 (8.7) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | no |
| STACK2 5 | 54/26/42 | +3.4 | 46/25/62 | -1.6 (8.7) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | no |
| STACK2 6 | 56/40/49 | +2.6 | 51/20/61 | -1.2 (10.7) | RISK-KEEP (L6M only) | RISK-KEEP (L6M only) | yes |
| STACK2 7 | 56/40/49 | +2.6 | 51/20/61 | -1.2 (10.7) | RISK-KEEP (L6M only) | RISK-KEEP (L6M only) | yes |
| STACK2 9 | 56/21/42 | +2.1 | 26/20/44 | -0.9 (7.7) | RISK-KEEP | no | yes |
| STACK2 18 | 61/25/49 | +6.4 | 2/28/59 | -5.4 (7.6) | no | no | yes |
| STACK2 19 | 67/22/56 | +12.1 | 26/37/60 | -2.5 (7.5) | RISK-KEEP | no | yes |
| STACK2 20 | 52/35/53 | +5.3 | 33/21/62 | +0.2 (7.3) | RISK-KEEP (placebo n/a) | RISK-KEEP (L6M only) | yes |
| STACK2 23 | 67/39/56 | +2.1 | 33/30/61 | +2.3 (9.5) | RISK-KEEP | no | no |
| STACK2 44 | 22/26/35 | +3.3 | 3/15/53 | +0.8 (5.9) | no | no | yes |
| STACK2 46 | 21/23/27 | +0.4 | 2/-1/28 | -1.3 (4.7) | no | no | no |
| STACK2 52 | 52/24/26 | +6.5 | 34/-3/25 | +3.3 (6.0) | RISK-KEEP (L6M only) | no | no |
| STACK2 72 | 35/27/36 | +2.1 | 32/10/57 | -0.7 (6.9) | RISK-KEEP (L6M only) | no | no |
| STACK2 73 | 35/27/36 | +2.1 | 32/10/57 | -0.7 (6.9) | RISK-KEEP (L6M only) | no | no |
| STACK2 74 | 59/31/32 | +5.2 | 45/27/53 | -3.6 (8.0) | RISK-KEEP | RISK-KEEP (L6M only) | no |
| STACK2 75 | 59/31/32 | +5.2 | 45/27/53 | -3.6 (8.0) | RISK-KEEP | RISK-KEEP (L6M only) | no |
| STACK2 76 | 55/31/51 | +1.0 | 40/31/51 | -1.6 (10.5) | RISK-KEEP | RISK-KEEP (L6M only) | no |
| STACK2 77 | 55/31/51 | +1.0 | 40/31/51 | -1.6 (10.5) | RISK-KEEP | RISK-KEEP (L6M only) | no |
| STACK2 78 | 27/22/38 | -0.1 | 25/23/46 | +1.6 (6.6) | RISK-KEEP | no | no |
| STACK2 88 | 56/34/47 | +5.8 | 7/16/57 | -4.5 (7.8) | no | no | no |
| STACK2 89 | 38/39/56 | +6.9 | 35/16/57 | -1.0 (6.9) | RISK-KEEP (L6M only) | no | no |
| STACK2 90 | 37/39/50 | +1.9 | 36/5/55 | +0.2 (6.5) | RISK-KEEP (L6M only) | RISK-KEEP (L6M only) | no |
| STACK2 105 | 54/24/22 | +5.8 | 29/2/46 | +0.7 (5.8) | RISK-KEEP (L6M only) | no | no |
| STACK2 107 | 34/23/34 | +1.9 | 32/10/57 | -0.7 (6.9) | RISK-KEEP (L6M only) | no | no |
| STACK2 113 | 35/27/36 | +2.1 | 32/10/57 | -0.7 (6.9) | RISK-KEEP (L6M only) | no | no |
| STACK2 176 | 59/20/27 | +5.2 | 27/-6/18 | +3.6 (6.0) | RISK-KEEP (L6M only) | no | no |
| STACK2 180 | 64/22/52 | +3.4 | 38/22/55 | +0.8 (10.3) | RISK-KEEP (placebo n/a) | no | no |
| STACK2 186 | 34/23/50 | -2.2 | 14/36/54 | -7.0 (16.8) | no | no | no |
| STACK2 188 | 29/22/21 | +1.4 | 23/7/56 | +0.2 (6.3) | RISK-KEEP (L6M only) | no | no |
| STACK2 191 | 56/28/21 | +5.3 | 25/-7/18 | +2.9 (5.6) | RISK-KEEP (L6M only) | no | no |
| STACK2 195 | 60/32/43 | +4.3 | 26/36/61 | +0.8 (10.6) | RISK-KEEP (placebo n/a) | no | yes |
| SP1B MKT_4 | 64/21/25 | +1.5 | 57/12/31 | -1.1 (9.6) | RISK-KEEP (L6M only) | no | no |
| SP1B MKT_5 | 60/32/34 | -3.3 | 59/16/37 | -3.3 (11.8) | RISK-KEEP (L6M only) | no | no |
| SP1B MKT_81 | 62/23/29 | -2.5 | 57/5/29 | -2.0 (9.8) | RISK-KEEP (L6M only) | no | no |
| SP1B MKT_160 | 41/35/48 | +0.6 | 24/15/4 | +5.3 (5.4) | RISK-KEEP (L6M only) | no | yes |
| SP1B S73_160 | 52/36/28 | +1.8 | 34/19/-1 | +5.7 (5.5) | RISK-KEEP (L6M only) | no | no |
| SP1B S73_177 | 35/27/36 | +2.1 | 32/10/57 | -0.7 (6.9) | RISK-KEEP (L6M only) | no | no |
| SP1B MKT_178 | 56/40/49 | +2.6 | 51/20/61 | -1.2 (10.7) | RISK-KEEP (L6M only) | RISK-KEEP (L6M only) | yes |
| SP1B S73_178 | 55/31/51 | +1.0 | 40/31/51 | -1.6 (10.5) | RISK-KEEP | RISK-KEEP (L6M only) | no |
| CUTW CUTW/PE/x25/N60/any | 38/48/27 | -5.9 | 15/43/22 | -6.9 (15.2) | no | no | no |

## Questions (non-blocking)
1. Should the volume measure be changed to row-gross (lots x seconds) so the placebo bites on entry cells? 2. EINT1 oracle row: drop from future lead lists.
