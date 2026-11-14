# DS3_TOOLS_T2_P3 - refreshed 00:02Z (driver code/th_t2b/t2b_driver.sh; page 2 = DS3_TOOLS_T2_P2.md; no PASS claims)

## Narrative (W-TL2b, written 03:40Z; auto sections below are regenerated every 4 h by code/th_t2b/t2b_driver.sh)
New since page 2 (DS3_TOOLS_T2_P2.md):
1. LEVEL-RELATIVE HOOK BUILT from the existing zone hooks (code/th_zn_act/zone_hooks.py already has `retgt` = target placed at wall + off, `struct` = stop just behind the wall behind, keyed by a (book7, signal second) level table). I only supplied level tables: /mnt/l2/l2vast/_th_zn/ztable_TL2A.npz (native A hourly OI walls: call res, put sup, 0DTE call/put), ztable_TL2V (A hourly volume-source walls), ztable_TL2B (B: NDX OI call wall / put wall / magnet, prior-day), built by code/th_t2b/t2b_ztable.py (keys = S1B-COMB base trades + LPB_BASE + JN05W2 trade lists; ahead coverage 45-55%). Sets (state S1-COMB, zone_exact, TL2_ names = admission tag TOOLS): TL2_RETA/RETV/RETB (target -> wall - 3 pts when a wall is 0-60 pts ahead, min 4), TL2_STOPA/STOPB (structure stop = wall behind + 3 pts when the wall is 6-60 pts behind, lots rescaled to equal $ risk, cap 3x), TL2_RETA2 (wall within 45, off -8), TL2_STOPV, TL2_ZID (identity).
2. IDENTITY GATE PASSED: TL2_ZID (table loaded, flags never fire) vs the exact base RB_COMB, month 202610: 823 / 823 trades identical on (book, entry, exit, gross), gross 47,330.5 = 47,330.5. Only then are the numbers below counted.
3. EXACT RESULT, L6M (6 months) and HOLD (12 months, 2025-11..2026-10), state base TL2_ZID(=RB_COMB), net after fees: TL2_RETA (target at the A wall) L6M +4.5k (+174 $/wk), HOLD -20.5k (-393 $/wk), 5 of 12 months better, maxDD 134.8k -> 137.8k; TL2_STOPA (stop behind the A wall) L6M -46k, HOLD -100k (-1,921 $/wk), 2 of 12 months better; TL2_RETV (volume-source wall target) HOLD -117k (-2,245 $/wk); TL2_RETB (B wall target) HOLD -74k (-1,423 $/wk); TL2_STOPB (stop behind the B wall) L6M -13.1k (-504 $/wk), HOLD -19.6k (-377 $/wk), 7 of 12 months better, maxDD 134.8k -> 129.6k (-3.8%). The single-month Oct view (+13k STOPB) did not hold. VERDICT: walls as targets or stops do NOT help on the exact engine, A or B; only STOPB trims maxDD slightly at -377 $/wk (a cost, not a gain). The first-order W/S 'LEADs' were artefacts of the coarse minute-path, as flagged. PRE (2024-09..2025-06) rows below as months finish.
4. PER-MINUTE PLACEBO now exists (london sig-minute snapshots shifted 7-60 days, 8 offsets): JN05W2 London skip when price is >= 73 pts above the volume-source flip: recents $2.6k/wk vs placebo max $1.05k and family null q95 $1.8k (L3M +2.6k, L6M +3.7k, HOLD +1.6k, trend weeks +12.9k/+30.7k, PRE -1.1k); LPB_BASE does not replicate it (not LEAD there). Other London per-minute LEADs (net gamma sign, wall distances) exceed their placebo max too but are mostly E-press cells (leverage). Exact set TL2_LONFL73 (+ _RM) queued in the TOOLS runner (grid T2B_M_VFLU built: per-minute price minus vol-flip, London minutes).
5. BLOCKERS: (a) K-hold (loss-cut hold) leads have no exact hook (no 'cut gate'); they stay first-order. (b) The TOOLS exact runner (EMF03/EMF07/LONFL73 on LPB_BASE/JN04RM) is still waiting for tp_admit (cap 24 workers); the zone sets run through zone_exact's own gate and are running.

6. K-HOLD (loss-cut hold) EXACT HOOK BUILT (08:30Z): code/th_t2b/t2b_kexact.py = zone_exact + a mixin on the `statecut` event: the state cut is skipped (position held under its stop/target) when (NQ mid at the last completed minute - level) x side x mult passes dir/th, for the listed books and entry sessions; level grid /mnt/l2/l2vast/_th_screens/grid/T2B_KLV.npz (A hourly/daily OI call wall, put wall, 0DTE walls per minute). IDENTITY GATE PASSED: TL2_KID (gate never fires) = base on all 6 L6M months (same n, same net, delta 0). Sets (P7, London entry session): TL2_K1 (px - hourly call wall <= -129), TL2_K2 (px - daily put wall <= 1,476), TL2_K3 ((put wall - px) x side <= 526), TL2_KALL (CONTROL: always hold P7 London cuts).
   L6M exact, net after fees vs TL2_ZID (= base): K1 +704 $/wk (2 of 6 months better, maxDD 124.9k -> 132.6k), K2 +1,325 $/wk (5 of 6; maxDD 125.6k), K3 +1,214 $/wk (3 of 6; 131.9k), KALL +421 $/wk (2 of 6; 132.6k).
   READING: K1/K3 are mostly 'hold London P7 cuts', not level information (KALL does the same). K2 beats the unconditional hold by ~900 $/wk (August +1.9k vs KALL -7.8k; October +3.5k vs -5.2k) because its condition keeps the cut when price is > 1,476 pts above the daily put wall. LABEL: K2 is a 6-MONTH, ONE-MONTH-DRIVEN RESULT (September +32.7k of +34.5k; without September K2 is +1.9k over 5 months, about +90 $/wk). No claim is made; HOLD months (2025-11..2026-04) for K2 and KALL are running (queue t2b_kqueue2.py, ~6 min/month) and are required before any claim. Not a pass, not even a lead.
7. TOOLS exact runner for the finalist skips (TL2_EMF03 / EMF07 / LONFL73, LPB_BASE, L6M only): runner restarted with 5 workers at 08:30Z; tp_admit still answers WAIT (24-worker global cap, load 26), so it launches as slots free. 3 of 18 jobs done (EMF03 202610, 202609; EMF07 202610): no multi-month row yet.

## AUTO: level-relative exact sets TL2_* vs RB_COMB (t2b_zscore.py)
set | month | n base->set | net base -> set | delta $
TL2_RETA 202409  n 545->554  net 18546 -> -2173  delta -20719
TL2_RETA 202410  n 438->456  net 49830 -> 34515  delta -15315
TL2_RETA 202411  n 456->474  net 49039 -> 58649  delta +9610
TL2_RETA 202412  n 387->401  net 200513 -> 187571  delta -12943
TL2_RETA 202501  n 534->547  net 135269 -> 134663  delta -605
TL2_RETA 202502  n 443->458  net -82029 -> -79264  delta +2765
TL2_RETA 202503  n 603->616  net 103845 -> 110977  delta +7132
TL2_RETA 202504  n 869->879  net -72542 -> -74319  delta -1777
TL2_RETA 202505  n 533->560  net 142846 -> 153705  delta +10860
TL2_RETA 202506  n 435->449  net 23951 -> 33516  delta +9565
TL2_RETA 202511  n 647->642  net 132116 -> 91293  delta -40824
TL2_RETA 202512  n 488->505  net 1344 -> 32109  delta +30765
TL2_RETA 202601  n 510->513  net 100840 -> 94381  delta -6459
TL2_RETA 202602  n 613->622  net -32837 -> -30362  delta +2475
TL2_RETA 202603  n 854->878  net 20732 -> 11826  delta -8907
TL2_RETA 202604  n 608->606  net 105100 -> 103032  delta -2068
TL2_RETA 202605  n 672->730  net 35852 -> 16260  delta -19592
TL2_RETA 202606  n 954->999  net 259213 -> 281988  delta +22775
TL2_RETA 202607  n 1058->1070  net 109408 -> 135010  delta +25601
TL2_RETA 202608  n 673->681  net 15104 -> 6306  delta -8799
TL2_RETA 202609  n 681->700  net 179048 -> 200000  delta +20951
TL2_RETA 202610  n 823->830  net 45347 -> 8951  delta -36396
  L6M: months 6 of 6, delta +4540 $ (+174 $/wk), set better in 3 of 6 months
  HOLD: months 12 of 12, delta -20477 $ (-393 $/wk), set better in 5 of 12 months
  PRE: months 10 of 10, delta -11427 $ (-263 $/wk), set better in 5 of 10 months
  trade-sequence maxDD base 179221 -> set 178858 over the 22 months done
TL2_STOPA 202409  n 545->551  net 18546 -> 32670  delta +14124
TL2_STOPA 202410  n 438->445  net 49830 -> 52448  delta +2618
TL2_STOPA 202411  n 456->469  net 49039 -> 49203  delta +164
TL2_STOPA 202412  n 387->394  net 200513 -> 200227  delta -286
TL2_STOPA 202501  n 534->536  net 135269 -> 119145  delta -16124
TL2_STOPA 202502  n 443->447  net -82029 -> -98379  delta -16350
TL2_STOPA 202503  n 603->606  net 103845 -> 98416  delta -5429
TL2_STOPA 202504  n 869->861  net -72542 -> -55088  delta +17454
TL2_STOPA 202505  n 533->540  net 142846 -> 139162  delta -3683
TL2_STOPA 202506  n 435->445  net 23951 -> 24792  delta +841
TL2_STOPA 202511  n 647->646  net 132116 -> 118975  delta -13141
TL2_STOPA 202512  n 488->490  net 1344 -> 10210  delta +8866
TL2_STOPA 202601  n 510->520  net 100840 -> 80586  delta -20254
TL2_STOPA 202602  n 613->609  net -32837 -> -58395  delta -25558
TL2_STOPA 202603  n 854->856  net 20732 -> 22895  delta +2163
TL2_STOPA 202604  n 608->604  net 105100 -> 99037  delta -6062
TL2_STOPA 202605  n 672->707  net 35852 -> 25657  delta -10195
TL2_STOPA 202606  n 954->946  net 259213 -> 258595  delta -617
TL2_STOPA 202607  n 1058->1046  net 109408 -> 108917  delta -491
TL2_STOPA 202608  n 673->661  net 15104 -> -4286  delta -19390
TL2_STOPA 202609  n 681->690  net 179048 -> 165389  delta -13660
TL2_STOPA 202610  n 823->823  net 45347 -> 43510  delta -1837
  L6M: months 6 of 6, delta -46191 $ (-1772 $/wk), set better in 0 of 6 months
  HOLD: months 12 of 12, delta -100177 $ (-1921 $/wk), set better in 2 of 12 months
  PRE: months 10 of 10, delta -6672 $ (-154 $/wk), set better in 5 of 10 months
  trade-sequence maxDD base 179221 -> set 156545 over the 22 months done
TL2_RETV 202409  n 545->556  net 18546 -> 17038  delta -1508
TL2_RETV 202410  n 438->467  net 49830 -> 32026  delta -17804
TL2_RETV 202411  n 456->486  net 49039 -> 61765  delta +12727
TL2_RETV 202412  n 387->415  net 200513 -> 202387  delta +1873
TL2_RETV 202501  n 534->549  net 135269 -> 138128  delta +2859
TL2_RETV 202502  n 443->459  net -82029 -> -89961  delta -7932
TL2_RETV 202503  n 603->619  net 103845 -> 119669  delta +15824
TL2_RETV 202504  n 869->861  net -72542 -> -58778  delta +13764
TL2_RETV 202505  n 533->556  net 142846 -> 110342  delta -32503
TL2_RETV 202506  n 435->468  net 23951 -> 29799  delta +5848
TL2_RETV 202511  n 647->659  net 132116 -> 107035  delta -25081
TL2_RETV 202512  n 488->498  net 1344 -> -5477  delta -6820
TL2_RETV 202601  n 510->557  net 100840 -> 81887  delta -18952
TL2_RETV 202602  n 613->648  net -32837 -> -45134  delta -12297
TL2_RETV 202603  n 854->910  net 20732 -> 36022  delta +15290
TL2_RETV 202604  n 608->627  net 105100 -> 89995  delta -15104
TL2_RETV 202605  n 672->722  net 35852 -> 24127  delta -11725
TL2_RETV 202606  n 954->970  net 259213 -> 245613  delta -13599
TL2_RETV 202607  n 1058->1092  net 109408 -> 72502  delta -36907
TL2_RETV 202608  n 673->704  net 15104 -> 27814  delta +12709
TL2_RETV 202609  n 681->698  net 179048 -> 161854  delta -17194
TL2_RETV 202610  n 823->833  net 45347 -> 57994  delta +12647
  L6M: months 6 of 6, delta -54070 $ (-2074 $/wk), set better in 2 of 6 months
  HOLD: months 12 of 12, delta -117035 $ (-2245 $/wk), set better in 3 of 12 months
  PRE: months 10 of 10, delta -6852 $ (-158 $/wk), set better in 6 of 10 months
  trade-sequence maxDD base 179221 -> set 171977 over the 22 months done
TL2_RETB 202409  n 545->545  net 18546 -> 18546  delta +0
TL2_RETB 202410  n 438->442  net 49830 -> 50709  delta +878
TL2_RETB 202411  n 456->467  net 49039 -> 56506  delta +7467
TL2_RETB 202412  n 387->403  net 200513 -> 187459  delta -13055
TL2_RETB 202501  n 534->544  net 135269 -> 98170  delta -37099
TL2_RETB 202502  n 443->461  net -82029 -> -72179  delta +9850
TL2_RETB 202503  n 603->603  net 103845 -> 104694  delta +848
TL2_RETB 202504  n 869->874  net -72542 -> -74152  delta -1610
TL2_RETB 202505  n 533->550  net 142846 -> 76293  delta -66552
TL2_RETB 202506  n 435->442  net 23951 -> 13228  delta -10723
TL2_RETB 202511  n 647->651  net 132116 -> 112684  delta -19432
TL2_RETB 202512  n 488->490  net 1344 -> 1584  delta +241
TL2_RETB 202601  n 510->515  net 100840 -> 91164  delta -9676
TL2_RETB 202602  n 613->613  net -32837 -> -35928  delta -3091
TL2_RETB 202603  n 854->865  net 20732 -> 3897  delta -16835
TL2_RETB 202604  n 608->624  net 105100 -> 93085  delta -12015
TL2_RETB 202605  n 672->699  net 35852 -> 25248  delta -10604
TL2_RETB 202606  n 954->961  net 259213 -> 271245  delta +12033
TL2_RETB 202607  n 1058->1066  net 109408 -> 143242  delta +33834
TL2_RETB 202608  n 673->676  net 15104 -> 9191  delta -5913
TL2_RETB 202609  n 681->702  net 179048 -> 162324  delta -16725
TL2_RETB 202610  n 823->840  net 45347 -> 19316  delta -26031
  L6M: months 6 of 6, delta -13407 $ (-514 $/wk), set better in 2 of 6 months
  HOLD: months 12 of 12, delta -74216 $ (-1423 $/wk), set better in 3 of 12 months
  PRE: months 10 of 10, delta -109994 $ (-2532 $/wk), set better in 4 of 10 months
  trade-sequence maxDD base 179221 -> set 178174 over the 22 months done
TL2_STOPB 202409  n 545->545  net 18546 -> 18546  delta +0
TL2_STOPB 202410  n 438->449  net 49830 -> 48888  delta -942
TL2_STOPB 202411  n 456->470  net 49039 -> 80614  delta +31575
TL2_STOPB 202412  n 387->396  net 200513 -> 213904  delta +13391
TL2_STOPB 202501  n 534->542  net 135269 -> 140225  delta +4956
TL2_STOPB 202502  n 443->458  net -82029 -> -80353  delta +1676
TL2_STOPB 202503  n 603->612  net 103845 -> 88010  delta -15835
TL2_STOPB 202504  n 869->862  net -72542 -> -54666  delta +17877
TL2_STOPB 202505  n 533->559  net 142846 -> 135712  delta -7134
TL2_STOPB 202506  n 435->455  net 23951 -> 34445  delta +10494
TL2_STOPB 202511  n 647->633  net 132116 -> 121565  delta -10551
TL2_STOPB 202512  n 488->488  net 1344 -> 15853  delta +14509
TL2_STOPB 202601  n 510->516  net 100840 -> 128421  delta +27582
TL2_STOPB 202602  n 613->623  net -32837 -> -53158  delta -20321
TL2_STOPB 202603  n 854->834  net 20732 -> 24161  delta +3429
TL2_STOPB 202604  n 608->627  net 105100 -> 83954  delta -21145
TL2_STOPB 202605  n 672->688  net 35852 -> 34481  delta -1371
TL2_STOPB 202606  n 954->924  net 259213 -> 264572  delta +5359
TL2_STOPB 202607  n 1058->1044  net 109408 -> 59381  delta -50027
TL2_STOPB 202608  n 673->680  net 15104 -> 29468  delta +14364
TL2_STOPB 202609  n 681->691  net 179048 -> 184297  delta +5248
TL2_STOPB 202610  n 823->794  net 45347 -> 58638  delta +13291
  L6M: months 6 of 6, delta -13136 $ (-504 $/wk), set better in 4 of 6 months
  HOLD: months 12 of 12, delta -19633 $ (-377 $/wk), set better in 7 of 12 months
  PRE: months 10 of 10, delta +56058 $ (+1290 $/wk), set better in 6 of 10 months
  trade-sequence maxDD base 179221 -> set 157098 over the 22 months done

## AUTO: K-hold gate sets TL2_K* vs TL2_ZID (t2b_kexact.py; KID = identity)
set | month | n base->set | net base -> set | delta $
TL2_KID 202605  n 672->672  net 35852 -> 35852  delta +0
TL2_KID 202606  n 954->954  net 259213 -> 259213  delta +0
TL2_KID 202607  n 1058->1058  net 109408 -> 109408  delta +0
TL2_KID 202608  n 673->673  net 15104 -> 15104  delta +0
TL2_KID 202609  n 681->681  net 179048 -> 179048  delta +0
TL2_KID 202610  n 823->823  net 45347 -> 45347  delta +0
  L6M: months 6 of 6, delta +0 $ (+0 $/wk), set better in 0 of 6 months
  trade-sequence maxDD base 124920 -> set 124920 over the 6 months done
TL2_K1 202605  n 672->667  net 35852 -> 20497  delta -15355
TL2_K1 202606  n 954->950  net 259213 -> 256340  delta -2873
TL2_K1 202607  n 1058->1050  net 109408 -> 118824  delta +9416
TL2_K1 202608  n 673->665  net 15104 -> 7908  delta -7197
TL2_K1 202609  n 681->677  net 179048 -> 217479  delta +38431
TL2_K1 202610  n 823->818  net 45347 -> 41283  delta -4064
  L6M: months 6 of 6, delta +18358 $ (+704 $/wk), set better in 2 of 6 months
  trade-sequence maxDD base 124920 -> set 132557 over the 6 months done
TL2_K2 202511  n 647->643  net 132116 -> 142420  delta +10304
TL2_K2 202512  n 488->483  net 1344 -> 5599  delta +4255
TL2_K2 202601  n 510->507  net 100840 -> 88982  delta -11858
TL2_K2 202602  n 613->611  net -32837 -> -37520  delta -4684
TL2_K2 202603  n 854->848  net 20732 -> 11700  delta -9032
TL2_K2 202604  n 608->614  net 105100 -> 79242  delta -25858
TL2_K2 202605  n 672->667  net 35852 -> 22910  delta -12942
TL2_K2 202606  n 954->954  net 259213 -> 260927  delta +1714
TL2_K2 202607  n 1058->1050  net 109408 -> 117033  delta +7625
TL2_K2 202608  n 673->668  net 15104 -> 17027  delta +1923
TL2_K2 202609  n 681->678  net 179048 -> 211732  delta +32684
TL2_K2 202610  n 823->820  net 45347 -> 48891  delta +3544
  L6M: months 6 of 6, delta +34548 $ (+1325 $/wk), set better in 5 of 6 months
  HOLD: months 12 of 12, delta -2325 $ (-45 $/wk), set better in 7 of 12 months
  trade-sequence maxDD base 134781 -> set 140511 over the 12 months done
TL2_K3 202605  n 672->665  net 35852 -> 46781  delta +10929
TL2_K3 202606  n 954->949  net 259213 -> 248386  delta -10827
TL2_K3 202607  n 1058->1050  net 109408 -> 110260  delta +851
TL2_K3 202608  n 673->669  net 15104 -> 6857  delta -8248
TL2_K3 202609  n 681->678  net 179048 -> 220862  delta +41814
TL2_K3 202610  n 823->817  net 45347 -> 42475  delta -2872
  L6M: months 6 of 6, delta +31648 $ (+1214 $/wk), set better in 3 of 6 months
  trade-sequence maxDD base 124920 -> set 131852 over the 6 months done
TL2_KALL 202511  n 647->643  net 132116 -> 141684  delta +9568
TL2_KALL 202512  n 488->483  net 1344 -> 22417  delta +21073
TL2_KALL 202601  n 510->507  net 100840 -> 88181  delta -12659
TL2_KALL 202602  n 613->611  net -32837 -> -37520  delta -4684
TL2_KALL 202603  n 854->842  net 20732 -> 6914  delta -13819
TL2_KALL 202604  n 608->610  net 105100 -> 104128  delta -971
TL2_KALL 202605  n 672->667  net 35852 -> 20497  delta -15355
TL2_KALL 202606  n 954->950  net 259213 -> 254961  delta -4252
TL2_KALL 202607  n 1058->1050  net 109408 -> 117033  delta +7625
TL2_KALL 202608  n 673->665  net 15104 -> 7282  delta -7823
TL2_KALL 202609  n 681->677  net 179048 -> 215056  delta +36008
TL2_KALL 202610  n 823->818  net 45347 -> 40116  delta -5231
  L6M: months 6 of 6, delta +10972 $ (+421 $/wk), set better in 2 of 6 months
  HOLD: months 12 of 12, delta +9480 $ (+182 $/wk), set better in 4 of 12 months
  trade-sequence maxDD base 134781 -> set 145297 over the 12 months done

## AUTO: TOOLS exact runner (EMF03/EMF07/LONFL73)
09:12:40 end ('TL2_EMF07', 202605, 'LPB') rc=0 186s
09:13:15 launch ('TL2_LONFL73', 202605, 'LPB') pid 229689
09:15:20 end ('TL2_LONFL73', 202605, 'LPB') rc=0 125s
09:15:35 ALL DONE
#### Exact sets (one set per job, TP engine, engine = base + screen gate hook th_screens/scr_hooks.py; bases LPB_BASE and JN04RM)
- TL2_EMF03 vs LPB_BASE: 6 of 43 months done.
  months better/worse/equal vs the base (of 6 done): 5 / 1 / 0; sum +181919 $.
  window L6M: stack maxDD 51253 -> 49504 (cut 3.4%), mean per week +6179 $ (18898 -> 25077), trades 4651 -> 4566; weeks: set minus base in the base 20 worst weeks +nan $/wk, in its 20 best +nan $/wk.
  L6M contiguous 2-week blocks: set beat or equalled the base in 6 of 8.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
- TL2_EMF07 vs LPB_BASE: 6 of 43 months done.
  months better/worse/equal vs the base (of 6 done): 4 / 2 / 0; sum +60600 $.
  window L6M: stack maxDD 51253 -> 45900 (cut 10.4%), mean per week +2152 $ (18898 -> 21051), trades 4651 -> 4611; weeks: set minus base in the base 20 worst weeks +nan $/wk, in its 20 best +nan $/wk.
  L6M contiguous 2-week blocks: set beat or equalled the base in 6 of 8.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
- TL2_LONFL73 vs LPB_BASE: 6 of 43 months done.
  months better/worse/equal vs the base (of 6 done): 4 / 2 / 0; sum +118572 $.
  window L6M: stack maxDD 51253 -> 51510 (cut -0.5%), mean per week +3740 $ (18898 -> 22638), trades 4651 -> 4151; weeks: set minus base in the base 20 worst weeks +nan $/wk, in its 20 best +nan $/wk.
  L6M contiguous 2-week blocks: set beat or equalled the base in 5 of 8.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
- TL2_EMF03_RM vs JN04RM: 1 of 43 months done.
  months better/worse/equal vs the base (of 1 done): 1 / 0 / 0; sum +37198 $.
- TL2_EMF07_RM vs JN04RM: 1 of 43 months done.
  months better/worse/equal vs the base (of 1 done): 1 / 0 / 0; sum +29180 $.
- TL2_LONFL73_RM vs JN04RM: 0 of 43 months done.

## AUTO: first-order screens
## cells scored per group and LEAD count (LEAD = recents > within-month family-null q95, L3M>0, both L6M halves > 0)
              scopes  LEAD  best_margin  med_margin
set      grp                                       
JN05W2   Ad      328     8        271.0      -339.0
         Ah      328     4        102.0      -387.0
         Am      328    14        830.0      -379.0
         Am2     328    14        830.0      -379.0
         Blv     328     6        150.0      -291.0
         Buw     208     4        310.0      -186.0
LPB_BASE Ad      336    34        747.0      -349.0
         Ah      336    37        711.0      -321.0
         Am      336    28        602.0      -291.0
         Am2     336    28        602.0      -291.0
         Blv     336     7        325.0      -302.0
         Buw     232     0         -5.0      -266.0

## A vs B per scope (best margin = recents minus null q95, $/wk first-order), count of scopes where group best margin > 0 (cells that beat the family null)
Ah vs Blv: scopes 83, Ah>0 in 9, Blv>0 in 7, Ah better in 38
Am vs Blv: scopes 83, Am>0 in 13, Blv>0 in 7, Am better in 32
Ad vs Blv: scopes 83, Ad>0 in 14, Blv>0 in 7, Ad better in 38
Ah vs Buw: scopes 55, Ah>0 in 9, Buw>0 in 4, Ah better in 28
Ah vs Ad: scopes 83, Ah>0 in 9, Ad>0 in 14, Ah better in 38
Am vs Ah: scopes 83, Am>0 in 13, Ah>0 in 9, Am better in 44

## LEAD cells (all groups), sorted by recents
     set grp use   act book  scope           feat dir     th  n_L6M     L1M    L3M    L6M   HOLD     MID   PREUW  recents  null_q95  plc_rank  tw_best5  tw_worst5  win_turned_losing
LPB_BASE  Ad   E  skip   P7   asia     Nd_em_room  ge  522.3    102  5022.9 4763.3 4286.9 3010.6   334.4   879.7   3648.8    2981.0       1.0    -408.4    36686.5                0.0
LPB_BASE  Ad   E  skip  ALL   asia     Nd_em_frac  le   -0.3    285  4455.8 4816.2 3426.8 2915.1   294.8 -1597.6   3170.9    2663.5       1.0      19.6    23185.5                1.0
LPB_BASE  Ad   E press  ALL london  Nd_vol_wfront  ge   34.8    887  4890.3 3910.9 3697.6 2517.2  4340.9   636.6   3107.4    2491.8       1.0   19037.1     4592.1                0.0
LPB_BASE Am2   E press  ALL london    Nm_vol_netg  le    0.0    841  3153.6 3039.8 3303.7 2729.3  4011.5  -660.6   3016.5    2414.7       1.0   20876.5   -11105.0                1.0
LPB_BASE  Am   E press  ALL london    Nm_vol_netg  le    0.0    841  3153.6 3039.8 3303.7 2729.3  4011.5  -660.6   3016.5    2414.7       1.0   20876.5   -11105.0                1.0
LPB_BASE  Am   E press  ALL london    Nm_vol_netg  le    0.1    979  2766.3 3356.2 3108.3 2896.1  5119.4  -187.6   3002.2    2414.7       1.0   24763.8   -16052.6                1.0
LPB_BASE Am2   E press  ALL london    Nm_vol_netg  le    0.1    979  2766.3 3356.2 3108.3 2896.1  5119.4  -187.6   3002.2    2414.7       1.0   24763.8   -16052.6                1.0
LPB_BASE  Ah   K  hold  ALL london Nh_vol_wbehind  ge  198.6    252   136.7 3182.2 2541.8 3360.2  2537.0   261.9   2951.0    2630.7       1.0   28566.2    -7573.5                0.0
LPB_BASE Am2   E press  ALL london    Nm_vol_netg  le    0.2   1137  2815.9 3868.2 3217.3 2680.1  4391.7  -195.4   2948.7    2414.7       1.0   35617.2    -9206.8                2.0
LPB_BASE  Am   E press  ALL london    Nm_vol_netg  le    0.2   1137  2815.9 3868.2 3217.3 2680.1  4391.7  -195.4   2948.7    2414.7       1.0   35617.2    -9206.8                2.0
LPB_BASE  Ad   E press  ALL london  Nd_vol_wfront  ge   71.0    783  3291.3 3200.1 3077.6 2610.9  5205.3   899.5   2844.2    2491.8       1.0   23392.5    -2726.6                1.0
LPB_BASE  Ad   E press  ALL london    Nd_vol_netg  le    0.0    855  3800.1 3155.1 3283.7 2392.9  3301.8  -486.0   2838.3    2491.8       1.0   23405.1     -193.1                0.0
LPB_BASE  Ad   E press  ALL london    Nd_vol_netg  le    0.1   1168  1790.0 3865.4 3023.7 2624.1  4702.2   -87.3   2823.9    2491.8       1.0   30107.4    -6178.8                2.0
LPB_BASE  Ah   E press  ALL london    Nh_vol_netg  le    0.1   1142  2623.2 3777.1 2995.8 2572.2  4714.8  -112.2   2784.0    2434.3       1.0   34820.0    -9352.6                2.0
LPB_BASE  Ah   E press  ALL london    Nh_vol_netg  le    0.0    842  2917.8 2872.6 2993.9 2542.0  3640.6  -404.3   2767.9    2434.3       1.0   21463.1   -12000.4                1.0
LPB_BASE Blv   E press  ALL london   NB_NDX_oi_mg  ge -913.0   1381  -612.1 3237.9 2771.0 2738.1  5669.6   429.1   2754.6    2479.8       1.0   54220.2   -23318.4                3.0
LPB_BASE  Ad   E press  ALL london      Nd_iv_atm  le    0.2   1047  2783.6 3348.7 2853.1 2597.9  4651.1  -212.9   2725.5    2491.8       1.0   24627.4    -6617.9                2.0
LPB_BASE  Ah   E press  ALL london  Nh_vol_wfront  ge   57.9    942  5294.2 4049.5 3012.9 2418.9  3618.4    53.1   2715.9    2434.3       1.0   21346.2    -6500.2                1.0
LPB_BASE  Am   E press  ALL london  Nm_vol_wfront  ge   57.9   1071  5518.6 4687.7 2772.7 2652.2  4213.3  -565.2   2712.4    2414.7       1.0   25318.2   -13090.2                1.0
LPB_BASE Am2   E press  ALL london  Nm_vol_wfront  ge   57.9   1071  5518.6 4687.7 2772.7 2652.2  4213.3  -565.2   2712.4    2414.7       1.0   25318.2   -13090.2                1.0
LPB_BASE Am2   E press  ALL london  Nm_vol_wfront  ge   87.7    921  5311.0 4819.6 2901.3 2486.8  3652.4  -434.4   2694.1    2414.7       1.0   20204.0    -5724.3                1.0
LPB_BASE  Am   E press  ALL london  Nm_vol_wfront  ge   87.7    921  5311.0 4819.6 2901.3 2486.8  3652.4  -434.4   2694.1    2414.7       1.0   20204.0    -5724.3                1.0
LPB_BASE  Ah   E press  ALL london  Nh_vol_wfront  ge   27.5   1051  4592.1 3762.5 3008.8 2294.6  3778.3   323.4   2651.7    2434.3       1.0   21134.6      687.4                1.0
LPB_BASE Am2   E press  ALL london Nm_vol_abehind  le  130.2    675  1563.3 2664.6 2822.2 2455.5  3083.8   102.5   2638.8    2414.7       1.0   32032.4   -16251.4                0.0
LPB_BASE  Am   E press  ALL london Nm_vol_abehind  le  130.2    675  1563.3 2664.6 2822.2 2455.5  3083.8   102.5   2638.8    2414.7       1.0   32032.4   -16251.4                0.0
  JN05W2  Am   E  skip  ALL london    Nm_vol_fl_u  ge   72.9    576  -935.3 2578.4 3695.1 1565.1 -5592.8 -1067.0   2630.1    1799.9       1.0   12913.0    30733.0                1.0
  JN05W2 Am2   E  skip  ALL london    Nm_vol_fl_u  ge   72.9    576  -935.3 2578.4 3695.1 1565.1 -5592.8 -1067.0   2630.1    1799.9       1.0   12913.0    30733.0                1.0
LPB_BASE  Ad   E press  ALL london      Nd_iv_atm  le    0.2    934  2783.6 3348.7 2790.0 2433.2  4066.7  -243.3   2611.6    2491.8       1.0   21868.8    -6617.9                2.0
LPB_BASE  Ah   E press  ALL london    Nh_vol_netg  le    0.1    978  2360.6 3001.6 2530.0 2680.8  5142.9  -546.9   2605.4    2434.3       1.0   25123.7   -17300.8                2.0
LPB_BASE Blv   E press  ALL london   NB_SPX_oi_cw  ge -487.3   1026 -2280.5 3974.9 2853.0 2351.1  3585.5  -317.3   2602.1    2479.8       1.0   49646.3    -5382.9                2.0
LPB_BASE  Ad   E press  ALL london  Nd_vol_afront  ge   20.5    972  4435.2 3360.6 2893.0 2307.5  4771.4   253.6   2600.3    2491.8       1.0   17310.9    -2270.7                1.0
LPB_BASE  Am   E press  ALL london    Nm_vol_net0  le    0.1   1020  2498.3 3664.9 2728.1 2460.1  4043.7  -249.6   2594.1    2414.7       1.0   24778.4   -15065.3                2.0
LPB_BASE Am2   E press  ALL london    Nm_vol_net0  le    0.1   1020  2498.3 3664.9 2728.1 2460.1  4043.7  -249.6   2594.1    2414.7       1.0   24778.4   -15065.3                2.0
LPB_BASE  Am   E press  ALL london     Nm_oi_net0  le    0.1   1026  3476.7 3584.8 2758.8 2425.0  4045.5  -314.4   2591.9    2414.7       1.0   23383.0    -3210.8                2.0
