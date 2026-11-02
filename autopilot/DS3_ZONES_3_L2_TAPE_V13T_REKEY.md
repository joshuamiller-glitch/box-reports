# DS3_ZONES_3_L2_TAPE_V13T_REKEY - ZL-2 tape leads and E4 key cells re-keyed to the published V13T PA9 band, LP_AGAINST mask correction, KB BT re-target (2026-11-02; Shadow only, no PASS)
Prereg for the new statistics: ZL2_EXIT_N_E4B_prereg.md sha256 7b9ac1510226033ca0cc6c32757fbced28c68700c7b72035f166654260a33675 (DECISIONS.md, before any E4B statistic). Band source: DS3_ZONES_3_NOISE_V13T.md (PARTIAL, n about 45): PA9, flip 2%: L6M 17.9, HOLD 16.8, MID 19.2, PRE 7.9, X' 13.5; flip 5%: 25.7 / 20.2 / 31.5 / 10.0 / 19.1 (percent of base maxDD). Base for ALL cuts below: d7_v13t.run_v13t_live (xcost 0.80, stopcost 2.45, lines empty, lock none, lockfix legs), 9 lock-reset phases. NOTE: the earlier V13T table (DS3_ZONES_3_L2_TAPE_LP_AGAINST_V13T.md) used V13Y+nfix+lines empty without xcost 0.80 / stopcost 2.45 / lockfix; the tape cells are now re-run on V13T_LIVE proper.

## 1. LP_AGAINST mask correction (bug found while pinning ZL-1's 147-row residual)
My density kernel counted prints with side flag N (no aggressor, direction 0) as 'against' prints (direction 0 passes the any-side rule). 147 rows of the 2,081-row natural mask were triggered by one side-N print each (mostly session-open prints at 22:00/23:00 UTC; list in ZL-2/lp_pin_sideN_trigger_prints.csv). Corrected mask (aggressor A/B only): 1,934 rows; agreement with ZL-1's clean room: Jaccard 0.996 vs its range-contains + usable-next mask (1,934 shared, 8 only ZL-1), 0.928 vs its primary. Frame offsets and conventions were not the issue; ZL-1's reading is the reference. Row-level saved $k, lock none, base = V13Y+nfix, take lines off (n taken 457): L6M +22.3 / HOLD +14.5 / PRE +63.6 / X' -30.8 (V13Y: 47.4 / 69.8 / 80.8 / -0.4). 2,001-family null (side-N excluded in the families, thinned to 1,934): p(min L6M,HOLD,PRE) = 0.141 (offset 0.016, shuffled-day 0.261, side-flip 0.145), p(with X') = 0.483; 12R min -37.3.
V13T_LIVE phase-averaged cut (corrected mask): L6M +4.5 / HOLD +4.5 / MID -3.5 / PRE +3.4 / X' -28.0 (band 17.9 / 16.8 / 19.2 / 7.9 / 13.5): FAIL, X' harm beyond the no-harm limit. Legacy 2,614-row mask: +0.2 / +0.2 / -0.6 / +0.6 / -14.3. LP_AGAINST stays NOISE (stronger than before). The V13Y and nfix pages that quote 2,081 rows remain as history; the corrected mask is mask_LP_AGAINST_AB_only.npy.

## 2. Tape leads re-keyed (V13T_LIVE, PA9 cut %, carrying weeks dropped in brackets for L6M / PRE / X')
| cell | L6M | HOLD | MID | PRE | X' | drop L6M / PRE / X' | d total $k | vs V13T band 2% | no-harm |
|--|--|--|--|--|--|--|--|--|--|
| TCD ext A30 half | +39.7 | +33.0 | -28.2 | +13.0 | -15.5 | +16.5 / +14.1 / +33.3 | -319 | passes L6M and PRE | FAILS (MID -28.2, X' -15.5) |
| TLQ asia half | +17.4 | +10.4 | -40.8 | +6.1 | +8.2 | -8.0 / +6.2 / +9.5 | -103 | L6M just under 17.9 | fails (MID) |
| large prints any side (T25 4h) skip | +13.0 | +12.1 | -8.4 | +3.0 | -15.0 | -8.9 / +2.4 / -19.1 | +38 | no | fails (X') |
| TCP hvn1_60d half | +8.5 | +8.5 | 0.0 | +2.2 | +3.2 | 0.0 / +3.5 / +1.1 | -17 | no | ok |
| TCP hvn1_60d skip | +2.6 | +2.6 | 0.0 | +2.6 | +8.1 | 0.0 / +4.8 / +4.9 | -18 | no | ok |
| LP_AGAINST (corrected) skip | +4.5 | +4.5 | -3.5 | +3.4 | -28.0 | -3.9 / +4.7 / -25.2 | +39 | no | fails (X') |
What changes: under the V13Y band (PRE 11.5) TCD ext A30 half missed on PRE (11.4); under the V13T band (PRE 7.9) it now PASSES L6M and PRE, and L6M survives the carrying-week drop (+16.5). It is still not a lead: no-harm fails (MID -28.2, X' -15.5), it costs $319k over the period (HALF on 13.6k rows = 15% of rows), and the volume-matched placebo (100 draws each, random rows halved with the same count per day / per book x session) beats it only in L6M (rank 1.00 / 0.98) and not in PRE (0.51 / 0.68), HOLD 0.89 / 0.81, X' 0.25 / 0.30: random halving gives the same PRE protection. Label: NOW-ONLY (L6M), not a lead, Shadow only. Nothing else changes: the other tape cells stay below the band.

## 3. E4 key cells (PA9 cut, V13T_LIVE; unchanged numbers, V13T band instead of V13Y)
| cell | L6M | HOLD | PRE | X' | verdict under the V13T band |
|--|--|--|--|--|--|
| RT100 BT swing, all books | +21.5 (band 17.9) | +18.6 (16.8) | +0.3 (7.9) | +3.4 (13.5) | L6M/HOLD pass, PRE and X' fail: PARTIAL, unchanged |
| RT70 BT swing, all books | +19.6 | +18.8 | +0.7 | +9.0 | same |
| TM F10 KB (flatten 10 min before session end) | +8.7 | +8.4 | +3.0 | +16.3 | X' passes, L6M and PRE fail: unchanged (NOT a lead) |
| TM MH240 all books | +15.9 | +15.7 | -12.1 | -47.3 | fails |
The V13T band makes PRE easier (7.9 vs 11.5) and L6M/HOLD slightly harder (17.9 / 16.8 vs 15.5 / 13.3); RT100/RT70 L6M stay above it; no E4 verdict flips.

## 4. KB-only BT-flip re-target (order item 3; prereg 7b9ac151...)
PA9 (carrying week dropped in brackets): RT100 KB L6M +13.2 [+0.5], HOLD +12.3, PRE -0.1 [+0.5], X' +8.1 [+18.6]; RT70 KB L6M +12.0 [+0.6], HOLD +11.6, PRE +0.3 [+0.6], X' +8.4 [+17.0]. Against the V13T band KB does NOT pass L6M (13.2 < 17.9) and its L6M cut is carried by the single 2026 W27-38 episode (dropped: +0.5). Monthly delta $ (phase 0, $k): PRE (17 months, RT100) 10 positive, total +24.8, best month 2024-10 +10.7, total without it +14.0 (RT70: 11 positive, +13.3, without best +4.0); X' (10 months) 4 positive, total +10.2, best 2023-10 +8.4, without it +1.8 (RT70: 3 positive, +5.8, without best -3.0). Other books (RT100): PE L6M +0.3, HM +5.0, SM +2.6, MV +0.3, i.e. the all-books L6M +21.5 is spread (KB +13.2 is the largest part). Label: NOT a lead (fails the prereg rule: L6M below band, PRE flat, X' carried by one month). Zone-take ('take at a line') is covered by E3 on V13T_LIVE (DS3_EXIT_N_TAKE.md, R4|zone: ONE-WEEK, no placebo beaten) and was not re-run.
