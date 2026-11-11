# DS3_ZONES_EXHAUST_FINAL - the zone layer per book x session on the state base (T-ZONES-EXHAUST; 2026-11-11 11:44Z)

**Labels: ROLL-FIXED (ROLLFIX1 base S1BRF-COMB, 21,163 trades; first-order tables use M tables lifted with Z.lift_M, 59 new rows m = 1); PRE-PROOF (entries not live-matched); post-hoc; Shadow only; NO PASS CLAIMS; FIRST-ORDER SCREEN unless a row says EXACT.** Standing rules: (1) the zone layer stays ON, "no zones / skip all / off" are reference rows only; (2) recents first: L6M/L3M/L1M, then the bi-weekly re-pick walk-forward (trailing 26 weeks -> next 2 weeks, purged 7 d), PRE/X' only as a tolerant check; (2a) PRE deepening allowed = min(25, L6M cut + 10)% only when the bi-weekly WF beats live in >= 60% of refit periods, else 15%, PRE mean floor = 25% of the live PRE mean (user decision 2026-11-10 13:45Z; d mean PRE >= -0.25 x live PRE mean, i.e. -$3.5k/wk; the old fixed -$1k label is shown beside); worse = RECENT-ONLY (still reported). Engine caveats at the end.

## PLAIN VERDICT

Keep the live zone layer (HALF D20 on the PoiSet lines + OTE-62 B73 D30) in every book x session: no zone cell that adds or changes the layer is confirmed by the exact engine on L6M, PRE and X' together and clears the placebo, the family max-stat (p_fam is 1.00 for every cell over a hypothesis set of 10^5 - 10^7) and the bi-weekly re-pick walk-forward. First-order screens say otherwise (large cuts for skip/quarter cells on london / PE), but every exact re-run so far shrinks them (ZNC_A0: first-order L6M +30 -> exact -10; ZNC_B0: +34 -> -7), and most first-order cuts are SCOPE-EFFECT (the same action on the whole book x session does as well). Exact leads: ZS_C0 / ZS_D0 (ZN-STRUCT swing / band levels) are positive on L1M-L6M, PRE and X' but ZS_D0 is -12.6% on HOLD (the Nov-2025..Apr-2026 drawdown path is deeper with it) and ZS_C0 is not level-specific by the first-order test; they are listed as ADD CANDIDATES (recents-only evidence for ZS_D0, HOLD-negative), never as replacements; the ZN-BOOK exact cells are still queued.

## 1. Reference rows (ROLL-FIXED; stack; all weeks; windows as of 2026-11-09)

| row | mean $/wk L6M | maxDD L6M | maxDD L3M | maxDD L1M | maxDD HOLD | maxDD PRE | maxDD X' | worst-20 L6M | Ulcer L6M | note |
|---|---|---|---|---|---|---|---|---|---|---|
| REF_LIVE (live layer: HALF D20 + OTE-62 B73 D30) | 22949 | 79907 | 79907 | 79821 | 99496 | 140288 | 137520 | 165224 | 34734 | exact base by definition |
| REF_NOZONE_FO | 28122 | 91798 | 91798 | 83462 | 112018 | 144258 | 146301 | 167377 | 36566 | first-order, labelled UP |
| REF_S4A (first-order ZREPLAY) | 22439 | 90644 | 89078 | 81532 | 107041 | 139299 | 128424 | 140228 | 37824 | first-order cross-check; the exact row of the S4A published layer is REF_LIVE |
| REF_ZOFF EXACT (zone layer off, reference only) [39 months, engine ROLLFIX1,old] | 25405 | 90124 | 90124 | 90124 | 104074 | 113391 | 186140 | 173487 | | cut vs live L6M/PRE/X' = -13/19/-35 |

Reading: removing the layer (exact) deepens L6M and X' drawdown and shallows PRE; it is a reference only. The user's earlier old-engine number (L6M -12.8 / PRE +19.2 / X' -38.6, WF 16%) is the same sign pattern.

## 2. Exact-engine rows landed (reference = ROLLFIX1 base daily; windows reported only when every month of the window landed; cut + = shallower maxDD)

| set | months | engine | cut_L1M | eq_cut_L1M | dmean_L1M | cut_L3M | eq_cut_L3M | dmean_L3M | cut_L6M | eq_cut_L6M | dmean_L6M | cut_HOLD | eq_cut_HOLD | dmean_HOLD | cut_PRE | eq_cut_PRE | dmean_PRE | cut_X' | eq_cut_X' | dmean_X' |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| REF_ZOFF | 39.0 | ROLLFIX1,old | -12.9 | -7.8 | -626.2 | -12.8 | -7.7 | 454.5 | -12.8 | -7.7 | 1138.5 | -4.6 | 0.1 | 1030.8 | 19.2 | 22.8 | 239.9 | -35.4 | -29.3 | -408.4 |
| ZNC_A0 | 39.0 | ROLLEXCL,ROLLFIX1,old | 2.8 | 9.1 | 753.4 | -9.9 | -2.9 | -3435.7 | -9.9 | -2.9 | 1675.6 | 11.7 | 17.4 | 2168.9 | -5.4 | 1.4 | -730.0 | 40.6 | 44.5 | 2729.6 |
| ZNC_A1 | 6.0 | ROLLFIX1 | 2.8 | 10.0 | 753.4 | -8.0 | -0.0 | -3459.2 | -8.0 | -0.0 | 1787.7 |  |  |  |  |  |  |  |  |  |
| ZNC_B0 | 39.0 | ROLLEXCL,ROLLFIX1,old | -6.9 | 2.7 | -266.0 | -6.8 | 2.8 | -388.4 | -6.8 | 2.8 | 2414.1 | 14.2 | 22.0 | 2868.7 | 30.6 | 36.8 | -1344.9 | 23.7 | 30.6 | 1922.1 |
| ZNC_B1 | 6.0 | ROLLFIX1 | 0.6 | 6.1 | 162.1 | 0.7 | 6.2 | -1096.4 | -0.6 | 5.0 | 1423.7 |  |  |  |  |  |  |  |  |  |
| ZS_C0 | 39.0 | ROLLEXCL,ROLLFIX1 | 14.9 | 23.4 | 3962.3 | 15.0 | 23.4 | -1936.3 | 15.0 | 23.4 | 2344.4 | 16.7 | 25.0 | 725.4 | 17.1 | 25.4 | -948.7 | 44.5 | 50.1 | 1642.7 |
| ZS_C1 | 39.0 | ROLLFIX1 | -0.9 | 8.9 | -241.4 | -0.8 | 9.0 | 1746.3 | -0.8 | 9.0 | 2615.4 | 7.1 | 16.1 | 1885.1 | 22.6 | 30.1 | -103.3 | 16.4 | 24.5 | -436.7 |
| ZS_C2 | 6.0 | ROLLFIX1 | 31.6 | -13.3 | -9768.3 | -0.4 | -66.4 | -4799.5 | -59.3 | -163.9 | -9180.1 |  |  |  |  |  |  |  |  |  |
| ZS_C3 | 6.0 | ROLLFIX1 | -1.2 | 0.3 | 1312.5 | -1.1 | 0.4 | -91.6 | -1.1 | 0.4 | 366.7 |  |  |  |  |  |  |  |  |  |
| ZS_C4 | 6.0 | ROLLFIX1 | 52.9 | 53.2 | 6357.8 | -31.1 | -30.2 | -146.6 | -31.1 | -30.2 | 156.3 |  |  |  |  |  |  |  |  |  |
| ZS_D0 | 39.0 | ROLLEXCL,ROLLFIX1 | 29.2 | 26.7 | -5069.2 | 20.3 | 17.5 | 2954.9 | 20.3 | 17.5 | -837.9 | -12.6 | -16.6 | -504.9 | 38.7 | 36.5 | -898.5 | 33.4 | 31.0 | 2634.6 |
| ZS_D1 | 39.0 | ROLLFIX1 | 80.0 | 79.0 | 3991.1 | 32.6 | 29.3 | 5932.1 | 27.7 | 24.2 | -1130.6 | 3.6 | -1.1 | -3185.4 | 14.7 | 10.6 | -4371.7 | 58.3 | 56.3 | -93.4 |
| ZS_D2 | 6.0 | ROLLFIX1 | 33.1 | 32.7 | -5252.4 | 15.8 | 15.3 | 2706.1 | 15.8 | 15.3 | -130.4 |  |  |  |  |  |  |  |  |  |
| ZS_D3 | 6.0 | ROLLFIX1 | 31.1 | 29.2 | 8283.5 | 17.0 | 14.6 | 2128.1 | 17.0 | 14.6 | -682.5 |  |  |  |  |  |  |  |  |  |
| ZS_D4 | 6.0 | ROLLFIX1 | 85.9 | 83.0 | 24698.4 | 38.4 | 25.5 | 1833.1 | 17.9 | 0.7 | -3872.8 |  |  |  |  |  |  |  |  |  |
| ZS_E0 | 39.0 | ROLLFIX1 | 28.3 | 23.7 | -5858.8 | 23.2 | 18.2 | 2743.4 | 23.2 | 18.2 | -1476.6 | -23.4 | -31.4 | -2611.5 | 42.5 | 38.8 | -1288.1 | 30.8 | 26.3 | 1001.3 |
| ZS_E1 | 39.0 | ROLLFIX1 | 34.5 | 39.6 | 1059.9 | 21.4 | 27.4 | 3890.6 | 21.4 | 27.4 | 2029.3 | -0.1 | 7.6 | 444.4 | 42.8 | 47.2 | -1538.6 | 24.0 | 29.8 | 956.4 |
| ZS_E2 | 6.0 | ROLLFIX1 | 43.1 | 50.4 | 710.3 | 43.1 | 50.4 | 6337.2 | 36.4 | 44.5 | 3582.9 |  |  |  |  |  |  |  |  |  |
| ZS_E3 | 6.0 | ROLLFIX1 | 29.0 | 33.3 | -427.2 | 29.0 | 33.4 | 3311.3 | 29.0 | 33.4 | 1609.2 |  |  |  |  |  |  |  |  |  |
| ZS_E4 | 6.0 | ROLLFIX1 | 32.0 | 29.9 | -1610.1 | 32.1 | 30.0 | -40.6 | 32.1 | 30.0 | -789.3 |  |  |  |  |  |  |  |  |  |

First-order vs exact for the same cells: see the cell-details table right below.

### Exact sets: cell details (first-order vs exact) and ROLL-FIX status

| set | owner | level | geometry | action | scope | level-specific? | gain over whole-scope action (pts, first-order) | first-order cut L6M | first-order eq-mean L6M | EXACT cut L6M | EXACT cut PRE | EXACT cut X' | roll months not yet ROLLFIX1 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZNC_A0 | CORE | ldnl | ahead 1atr | skip | london | SCOPE-EFFECT/unproven | 9.1 | 31 | 35 | -9.9 | -5.4 | 40.6 | none |
| ZNC_A1 | CORE | ldnl | ahead 1atr hw5 | skip | london | SCOPE-EFFECT/unproven | 2.7 | 27 | 28 | -8.0 |  |  | none |
| ZNC_B0 | CORE | ALL | ahead 0.25atr hw5 fresh=t1 age<=1d | skip | london | SCOPE-EFFECT/unproven | 19.7 | 34 | 45 | -6.8 | 30.6 | 23.7 | none |
| ZNC_B1 | CORE | ALL | ahead 0.5atr fresh=t1 age<=1d | skip | london | SCOPE-EFFECT/unproven | 15.0 | 28 | 40 | -0.6 |  |  | none |
| ZS_C0 | STRUCT | sw5_5 v23 hw2 pt5 BA skip london: maxDD cut L6M/PRE/X' 45/55 | (see ZN_STRUCT.md) | skip/half per evidence | london | SCOPE-EFFECT/unproven |  | 45 | 50 | 15.0 | 17.1 | 44.5 | none |
| ZS_C1 | STRUCT | sw5_3 v23 hw2 pt20 APs skip london: maxDD cut L6M/PRE/X' 34/ | (see ZN_STRUCT.md) | skip/half per evidence | london | SCOPE-EFFECT/unproven |  | 34 | 44 | -0.8 | 22.6 | 16.4 | none |
| ZS_C2 | STRUCT | fvg5 | v18 hw10 pt90 BP | skip | PE | level-specific | 76.7 | 55 | 32 | -59.3 |  |  | none |
| ZS_C3 | STRUCT | pd1h_38 | v0 hw0 atr1 BP | skip | PE|london | level-specific | 6.0 | 26 | 31 | -1.1 |  |  | none |
| ZS_C4 | STRUCT | ote5_any | v0 hw5 pt60 BA | skip | PE | level-specific | 75.1 | 36 | 31 | -31.1 |  |  | none |
| ZS_D0 | STRUCT | bbup_5 | v0 hw0 pt15 AA | quarter | london | level-specific | 13.6 | 36 | 38 | 20.3 | 38.7 | 33.4 | none |
| ZS_D1 | STRUCT | kcany_15 | v0 hw0 pt40 BA | quarter | ALL | level-specific | 51.3 | 40 | 38 | 27.7 | 14.7 | 58.3 | none |
| ZS_D2 | STRUCT | kc2.5up_5 | v0 hw0 pt15 AA | quarter | london | level-specific | 11.6 | 35 | 36 | 15.8 |  |  | none |
| ZS_D3 | STRUCT | kc1.5up_5 | v0 hw2 pt20 BA | quarter | london | level-specific | 11.4 | 36 | 36 | 17.0 |  |  | none |
| ZS_D4 | STRUCT | u7st10 | v0 hw10 pt90 BA | quarter | ALL | level-specific | 50.4 | 45 | 37 | 17.9 |  |  | none |
| ZS_E0 | STRUCT | grid0.5 | v0 hw2 pt5 BA | quarter | london | level-specific | 6.0 | 36 | 31 | 23.2 | 42.5 | 30.8 | none |
| ZS_E1 | STRUCT | grid1 | v0 hw10 atr1 AA | quarter | london | level-specific | 10.9 | 32 | 36 | 21.4 | 42.8 | 24.0 | none |
| ZS_E2 | STRUCT | rn50 | v0 hw0 atr0.5 AA | quarter | london | level-specific | 15.8 | 35 | 41 | 36.4 |  |  | none |
| ZS_E3 | STRUCT | grid1 | v0 hw0 pt30 AA | half | london | level-specific | 1.8 | 29 | 28 | 29.0 |  |  | none |
| ZS_E4 | STRUCT | grid0.5 | v0 hw0 atr1 AA | half | london | level-specific | 4.9 | 31 | 31 | 32.1 |  |  | none |

**Rule 2a on the exact rows** (PRE maxDD deepening <= 15% [tolerance rises to min(25, L6M cut + 10) only with a >= 60% bi-weekly WF], PRE mean floor = -25% of live PRE mean = -3490 $/wk; old fixed floor -$1k beside):

| set | exact PRE cut % | exact d mean PRE $/wk | single-cell bi-weekly WF beat% (first-order series) | PRE deepening allowed % | PRE mean floor $/wk | rule 2a label (Z.prior_info) |
|---|---|---|---|---|---|---|
| REF_ZOFF | 19.2 | 240 |  | 15 | 3490 | OK-PRIOR-UNKNOWN-WF (old fixed -$1k: OK-PRIOR-UNKNOWN-WF) |
| ZNC_A0 | -5.4 | -730 | 44 | 15 | 3490 | OK-PRIOR (old fixed -$1k: OK-PRIOR) |
| ZNC_B0 | 30.6 | -1345 | 40 | 15 | 3490 | OK-PRIOR (old fixed -$1k: RECENT-ONLY) |
| ZS_C0 | 17.1 | -949 |  | 15 | 3490 | OK-PRIOR-UNKNOWN-WF (old fixed -$1k: OK-PRIOR-UNKNOWN-WF) |
| ZS_C1 | 22.6 | -103 |  | 15 | 3490 | OK-PRIOR-UNKNOWN-WF (old fixed -$1k: OK-PRIOR-UNKNOWN-WF) |
| ZS_D0 | 38.7 | -898 | 46 | 15 | 3490 | OK-PRIOR (old fixed -$1k: OK-PRIOR) |
| ZS_D1 | 14.7 | -4372 | 39 | 15 | 3490 | RECENT-ONLY (old fixed -$1k: RECENT-ONLY) |
| ZS_E0 | 42.5 | -1288 | 46 | 15 | 3490 | OK-PRIOR (old fixed -$1k: RECENT-ONLY) |
| ZS_E1 | 42.8 | -1539 | 42 | 15 | 3490 | OK-PRIOR (old fixed -$1k: RECENT-ONLY) |

**ZS_D0 lead (single-cell bi-weekly re-pick WF vs live, first-order daily series; pick = cell if its trailing-26-week maxDD is lower and trailing mean >= live - 25% of live PRE mean):** 48 of 72 refit periods pick the cell; of those the cell period beats live (maxDD <= live and pnl >= live - floor) in 46%; OOS maxDD cut vs live 23.7%, OOS d mean -277 $/wk. EXACT cut L1M/L3M/L6M/HOLD/PRE/X' = 29.2/20.3/20.3/-12.6/38.7/33.4 (section 2). Label: ADD CANDIDATE only where recents hold (L1M/L3M/L6M positive) - HOLD and X' decide whether it is more than a recents-only lead; never a replacement; PRE rule 2a label in the table above.

## 3. The zone layer per book x session (SETTING = live layer unless an exact-confirmed cell beats it)

For each scope the best first-order cell (ranked by min(equal-mean cut L6M, L3M)) among all owners' down-only cells with >= 20 changed trades, scored on the ROLL-FIXED base; WF = bi-weekly re-pick (pool = scope top 40 + live; pick lowest trailing-26-week maxDD with trailing mean >= live - $1k/wk); beat% = share of non-live picks whose 2-week period had maxDD <= live and pnl >= live - $1k/wk; PRE tolerance per rule 2a (mean floor -25% of live PRE mean); scope effect = gain over the same action applied to the whole scope (gain <= 0 -> SCOPE-EFFECT). SETTING column: LIVE RETAINED unless the exact table has the cell complete on L6M and PRE with cut > 0.

| scope | n cells | best cell (owner / level / geometry / action) | cut % L6M/L3M/L1M | equal-mean L6M | HOLD/PRE/X' cut | dMean L6M $/wk | touched % | gain over whole-scope action (pts) | level-specific? | placebo p L6M (B200) | WF: n picks non-live / beat% / OOS cut% / dMean | PRE tol (allowed) | label | SETTING |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | 1786 | STRUCT / sw5_2 / v7 hw5 atr1.5 AP / quarter | 58/58/58 | 60 | 2/34/37 | 1105 | 25.8 | 74.3 | SCOPE-EFFECT | 0.00 | 72 / 50 / 45 / -2127 | fails | LEAD / RECENT-ONLY (PRE deeper than 15% or PRE mean below -25% of live) [old fixed -$1k floor: RECENT-ONLY] / FIRST-ORDER ONLY | LIVE + ADD CANDIDATE ZS_D1 (exact L6M and PRE cut > 0; X-prime/HOLD pending or listed above) |
| KB | 297 | BOOK / maxsz_w300 / BH-absent:B5 / skip | 20/20/20 | 15 | -4/12/-2 | -1155 | 20.9 | 21.9 | SCOPE-EFFECT | 0.00 | 72 / 56 / 1 / -817 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: RECENT-ONLY] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| PE | 604 | STRUCT / sw1_5 / v4 hw0 atr1.5 AP / skip | 69/69/92 | 71 | 10/53/42 | 1528 | 19.1 | 115.6 | SCOPE-EFFECT | 0.01 | 72 / 44 / 42 / -4797 | fails | LEAD / RECENT-ONLY (PRE deeper than 15% or PRE mean below -25% of live) [old fixed -$1k floor: RECENT-ONLY] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| SM | 236 | STRUCT / rn100 / v0 hw10 atr1.5 BP / skip | 10/10/10 | 9 | -11/8/3 | -308 | 2.4 | 37.2 | SCOPE-EFFECT | 0.07 | 72 / 54 / 5 / -1496 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| HM | 19 | BOOK / wall_k3_p0 / AH:A0.5|s-1|tch0|any / skip | 0/0/0 | 0 | 0/0/-1 | 66 | 0.2 | 26.7 | SCOPE-EFFECT | 0.20 | 43 / 67 / -4 / -140 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| MV | 184 | BOOK / swp_w900_t6 / AH:A0.5|s-1|any|any / skip | 21/21/21 | 27 | 12/10/7 | 2237 | 13.1 | 12.4 | SCOPE-EFFECT | 0.00 | 72 / 74 / 13 / -11 | ok | LEAD / PRE ok (tol 25%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| PB | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| OD | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| asia | 1291 | STRUCT / sw5_3 / v5 hw10 pt90 BA / skip | 44/44/50 | 55 | 0/1/1 | 5427 | 7.7 | 1188.4 | SCOPE-EFFECT | 0.00 | 71 / 62 / 24 / -1500 | ok | LEAD / PRE ok (tol 25%) [old fixed -$1k floor: RECENT-ONLY] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| london | 1071 | CORE / ALL / ahead 60pts hw2 fresh=t0 age<=5d / skip | 56/72/78 | 59 | -56/54/-24 | 1877 | 23.1 | 33.7 | SCOPE-EFFECT | 0.00 | 63 / 44 / -10 / -2630 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE + ADD CANDIDATE ZS_C0,ZS_D0,ZS_E0,ZS_E1 (exact L6M and PRE cut > 0; X-prime/HOLD pending or listed above) |
| pre | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| nyam | 87 | CORE / vg_u2 / ahead 90pts hw5 / skip | 14/14/20 | 27 | -1/5/1 | 4253 | 9.6 | 21.6 | SCOPE-EFFECT | 0.07 | 72 / 53 / 4 / -676 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| nypm | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| KB|asia | 96 | BOOK / maxsz_w300 / BH-absent:B5 / skip | 11/11/11 | 11 | -11/3/1 | -200 | 6.1 | 25.6 | SCOPE-EFFECT | 0.00 | 70 / 77 / 2 / -148 | ok | LEAD / PRE ok (tol 21%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| KB|london | 203 | BOOK / maxsz_w300 / BH-absent:B5 / skip | 8/8/8 | 9 | 8/6/3 | 160 | 4.8 | 6.4 | SCOPE-EFFECT | 0.02 | 71 / 59 / 9 / -201 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| KB|pre | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| KB|nyam | 11 | BOOK / ice_w600_n4 / AH:A0.5|s-1|any|any / skip | 1/1/3 | 1 | -3/3/-4 | 134 | 3.4 | 3.9 | SCOPE-EFFECT | 0.11 | 54 / 70 / 1 / -85 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| KB|nypm | 244 | STRUCT / confB10 / v0 hw0 np16 NP / skip | 6/6/6 | 8 | 0/0/14 | 499 | 2.3 | 8.2 | SCOPE-EFFECT | 0.00 | 68 / 71 / 2 / -140 | ok | LEAD / PRE ok (tol 16%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| PE|asia | 597 | STRUCT / sw5_5 / v7 hw10 pt90 BA / skip | 35/35/60 | 47 | 12/12/12 | 5493 | 3.4 | 254.9 | SCOPE-EFFECT | 0.00 | 72 / 54 / -4 / -679 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: RECENT-ONLY] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| PE|london | 398 | STRUCT / ema50_5 / v0 hw0 pt30 BA / skip | 34/41/51 | 37 | -5/39/36 | 1058 | 5.4 | 11.8 | SCOPE-EFFECT | 0.02 | 66 / 55 / 4 / -1382 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| PE|pre | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| PE|nyam | 444 | CORE / vg_u2 / ahead 90pts hw5 / skip | 11/11/19 | 23 | 0/6/8 | 3757 | 2.1 | 5.7 | SCOPE-EFFECT | 0.17 | 72 / 57 / 16 / -11 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| PE|nypm | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| SM|asia | 13 | STRUCT / tenkan_60 / v0 hw10 pt40 AP / skip | 6/6/5 | 7 | 8/2/2 | 376 | 0.9 | 40.1 | SCOPE-EFFECT | 0.03 | 71 / 68 / 0 / -449 | ok | LEAD / PRE ok (tol 16%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| SM|london | 323 | BOOK / ice_w600_n1 / AH:D5|s-1|any|any / skip | 17/19/25 | 16 | 3/10/8 | -559 | 2.9 | 1.6 | SCOPE-EFFECT | 0.03 | 69 / 49 / 11 / -641 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| SM|pre | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| SM|nyam | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| SM|nypm | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| HM|asia | 14 | STRUCT / ote15_any / v0 hw0 atr0.25 BP / skip | 3/3/3 | 4 | 0/0/3 | 307 | 0.3 | 22.3 | SCOPE-EFFECT | 0.01 | 55 / 91 / 1 / -65 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| HM|london | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| HM|pre | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| HM|nyam | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| HM|nypm | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| MV|asia | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| MV|london | 608 | BOOK / swp_w900_t6 / AH:D5|s-1|any|any / skip | 13/13/13 | 18 | 7/8/3 | 1555 | 7.0 | 5.1 | SCOPE-EFFECT | 0.08 | 72 / 68 / 14 / 128 | ok | LEAD / PRE ok (tol 23%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| MV|pre | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| MV|nyam | 25 | BOOK / maxsz_w900 / AH:D90|s-1|any|any / skip | 2/2/2 | 3 | 4/1/1 | 273 | 2.9 | 3.0 | SCOPE-EFFECT | 0.07 | 72 / 72 / 2 / -107 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| MV|nypm | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| PB|asia | 12 | BOOK / dpiv_w900 / AH:A0.5|s-1|any|any / skip | 0/0/8 | 1 | 3/0/1 | 172 | 0.9 | 2.9 | SCOPE-EFFECT | 0.23 | 68 / 74 / 0 / -513 | ok | LEAD / PRE ok (tol 15%) [old fixed -$1k floor: ok] / FIRST-ORDER ONLY | LIVE RETAINED (exact pending) |
| PB|london | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| PB|pre | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| PB|nyam | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| PB|nypm | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| OD|asia | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| OD|london | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| OD|pre | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| OD|nyam | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |
| OD|nypm | 0 | no eligible cell | | | | | | | | | | | none | LIVE RETAINED |

## 4. ADD / CHANGE candidates and how each is expressed

Exact-confirmed so far means complete exact L6M and PRE rows with cut > 0 in section 2 (and X'/HOLD listed when landed). Panel expression: v1.5 fields (PoiSet families, NtzDistancePts, NtzAction, Ote*, Flip*) cover only the existing 8 lines with HALF/SKIP at a distance; every other cell needs named v1.6 fields (proposed names below; not in the panel today).

| cell | owner | level / geometry / action | scope | expression |
|---|---|---|---|---|
| LIVE_HALF_D20_OTE62_B73_D30 | | reference row; exact base by definition | | live panel values: PoiSet = PD_mid, RTH_camH3, Kijun_1h, CRT_mid_4h, KC_up_4h, OTE62/705/79_15m; NtzAction = HALF; NtzDistancePts = 20; OTE-62 B73 D30 unchanged |
| ZS_D0_b0c41cc34961 | | EXACT cut L1M/L3M/L6M/HOLD/PRE/X' = +29.2/+20.3/+20.3/-12.6/+38.7/+33.4 (d mean L6M -838, PRE -898 $/wk); bbup_5 v0 hw0 pt15 AA quarter london: maxDD cut L6M/PRE/X' 36/44/46%, equal-mean min cut 38%, gain over group-wide 23 pts, shifted-level gain 18 pts, placebo p 0.06, live-week d$ 3225, family p  | | v1.6 proposed: ZoneLevelSet / ZoneGeometry (side, reach pts|ATR, half-width, freshness, age) / ZoneAction (HALF|QUARTER|SKIP) / ZoneScope (book|session); exact status: set ZS_D0: 39 exact months landed (see DS3_ZONES_EXHAUST_FINAL.md section 2) |
| ZS_C0_6e93e2da912d | | EXACT cut L1M/L3M/L6M/HOLD/PRE/X' = +14.9/+15.0/+15.0/+16.7/+17.1/+44.5 (d mean L6M +2344, PRE -949 $/wk); sw5_5 v23 hw2 pt5 BA skip london: maxDD cut L6M/PRE/X' 45/55/38%, equal-mean min cut 44%, gain over group-wide 61 pts, shifted-level gain 42 pts, placebo p 0.08, live-week d$ 19865, family p 1. | | v1.6 proposed: ZoneLevelSet / ZoneGeometry (side, reach pts|ATR, half-width, freshness, age) / ZoneAction (HALF|QUARTER|SKIP) / ZoneScope (book|session); exact status: set ZS_C0: 39 exact months landed (see DS3_ZONES_EXHAUST_FINAL.md section 2) |
| ZS_E0_d87874dba5c6 | | ; grid0.5 v0 hw2 pt5 BA quarter london: maxDD cut L6M/PRE/X' 36/48/34%, equal-mean min cut 29%, gain over group-wide 14 pts, shifted-level gain 17 pts, placebo p 0.06, live-week d$ 3873, family p 1.00 (all hyp), FIRST-ORDER | | v1.6 proposed: ZoneLevelSet / ZoneGeometry (side, reach pts|ATR, half-width, freshness, age) / ZoneAction (HALF|QUARTER|SKIP) / ZoneScope (book|session); exact status: set ZS_E0: 0 exact months landed (see DS3_ZONES_EXHAUST_FINAL.md section 2) |
| ZNB_F00 | | ZN-BOOK ice_w600_n1 AH:D20|s-1|any|any quarter b:PE: equal-mean cut L6M/PRE/X 35/39/37, p_own 0.05, p_fam 1.00, FIRST-ORDER, ROLL-EXCL | | v1.6 proposed: ZoneLevelSet / ZoneGeometry (side, reach pts|ATR, half-width, freshness, age) / ZoneAction (HALF|QUARTER|SKIP) / ZoneScope (book|session); exact status: set ZNB_F00: 0 exact months landed (see DS3_ZONES_EXHAUST_FINAL.md section 2) |

## 5. Family results (all owners) and level-specificity

Pool scored on the ROLL-FIXED base: 11103 cells (CORE 400, STRUCT 2308, BOOK 8378, S4 17). Level-specific = beats the same action on the whole scope AND the +/-25 pt shifted-level placebo (owner columns); SCOPE-EFFECT otherwise.

| owner/family | cells | down-only >= 20 trades | cut L6M>0 & L3M>0 & eq-mean>0 | of those level-specific | of those with gain over whole-scope > 0 | best equal-mean L6M | best cell |
|---|---|---|---|---|---|---|---|
| BOOK F | 8378 | 6144 | 4237 | 0 | 2013 | 50 | maxsz_w300 BH-absent:B5 skip (PE) |
| CORE A | 172 | 172 | 172 | 0 | 125 | 59 | ALL ahead 60pts hw2 fresh=t0 age<=5d skip (london) |
| CORE B | 172 | 172 | 172 | 0 | 127 | 50 | ALL ahead 0.25atr hw10 age<=1h skip (london) |
| CORE G | 56 | 56 | 56 | 0 | 8 | 21 | ALL behind 90pts age<=4h skip (ALL) |
| S4 S4 | 17 | 12 | 2 | 0 | 0 | 17 | PoiSet8 openA40 half half (ALL) |
| STRUCT C | 853 | 767 | 767 | 230 | 755 | 71 | sw1_5 v4 hw0 atr1.5 AP skip (PE) |
| STRUCT D | 834 | 747 | 747 | 128 | 726 | 63 | k7st_1 v0 hw0 pt30 BA skip (PE) |
| STRUCT E | 621 | 493 | 493 | 23 | 394 | 52 | grid0.5 v0 hw0 pt40 AA skip (london) |

Family p: ZN-CORE A/B/G, ZN-STRUCT, ZN-BOOK all report p_fam ~ 1.00 for every cell (max-stat over 10^5-10^7 hypotheses, cells independent = conservative); candidates are own-p only. ZN-TRIG (entry-trigger books, section 5 of the directive): 1,334,592 trigger-book cells over 68 level families, smallest family p 0.95, no book registered, no zone-filter candidates (ZN_TRIG.md). ZN-BOOK learned layer: the monotone tree fails its permutation null (p .24); the GBDT policy (halve bottom 50% / skip bottom 5%) fails (p .33) and is seed-unstable: the learned layer FAILS; no learned entry is registered. Details: ZN_STRUCT.md, ZN_BOOK.md, ZN_TRIG.md.

## Old-vs-new: every published ZONES-3 / S4 zone cell, with the base-change proof

Columns: **published** = the V13Y/V13T-era ZONES-3 verdict (old per-print-cut engine) as quoted on DS3_TH_S4_ZONES_S1B.md; **S4 page** = the same cell on the S1b-COMB state base as published by S345 (windows as of 2026-10-31, carrying weeks DROPPED before maxDD, the S3 defect, first-order); **new** = the same cell re-scored here on S1b-COMB with ALL weeks and windows as of 2026-11-09 (zone features = the PoiSet replay at the signal second, s345_common.zone_features; Z scorer); **old base** = the same cells (same replay rule) on the old V0 trade list (V13T ts2, 21,397 trades) and on replica HOLD (S1b engine with the old live per-print cut). SAME-TO-DOLLAR: none of the cells is identical between pages (the page used 10-31 windows with the carrying week dropped; new uses 11-09, all weeks). Equal-mean = scale lots so the L6M mean equals the reference (S1b-COMB base layer).

| cell | published L6M/PRE/X' | S4 page L6M/PRE/X' | new L6M/HOLD/PRE/X' | new equal-mean cut L6M/PRE/X' | d mean $/wk L6M | placebo p L6M/PRE (own, B100) | old base V0 L6M/PRE/X' | replica HOLD base L6M/PRE/X' | change vs S4 page (L6M) | verdict |
|---|---|---|---|---|---|---|---|---|---|---|
| ZOFF |  | -9/-3/-18 | -15/-13/-3/-6 | -9/2/-1 | 1352 | 0.38/0.29 | -5/-11/-15 | -18/-7/-27 | -6 | base-ref row |
| ZREPLAY |  | -6/1/-5 | -13/-8/1/7 | -18/-3/3 | -907 | 0.68/0.32 | -9/-7/1 | -33/5/-4 | -7 | base-ref row |
| open20 half | +41 / +17 / +9 (VOLUME) | 45/41/31 | 32/39/41/35 | 4/16/8 | -6255 | 0.21/0.09 | 22/32/3 | 55/38/21 | -13 | L6M and PRE cut > 0 on all 3 bases (screen) |
| open40 half |  | 48/34/20 | 27/34/34/34 | 15/24/23 | -3124 | 0.16/0.19 | 20/24/-22 | 50/26/25 | -21 | L6M and PRE cut > 0 on all 3 bases (screen) |
| open60 half | +42 / +4 / +33 (VOLUME) | 41/34/28 | -4/17/34/30 | -11/29/25 | -1549 | 0.81/0.02 | 4/31/-9 | 30/15/24 | -45 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| openA40 half | +35 / +20 / +41 (VOLUME) | 48/37/31 | 35/34/37/40 | 16/18/23 | -6365 | 0.05/0.13 | 22/26/25 | 54/37/23 | -13 | L6M and PRE cut > 0 on all 3 bases (screen) |
| openA60 half |  | 46/35/18 | 13/27/35/42 | -17/13/21 | -7130 | 0.60/0.14 | -3/19/15 | 44/15/27 | -33 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| sopen40 half | +41 / +11 / +21 (NOISE) | 40/35/23 | 4/23/35/32 | -4/30/27 | -1644 | 0.71/0.04 | 6/26/-15 | 38/26/14 | -36 | L6M and PRE cut > 0 on all 3 bases (screen); negative at equal mean (cut is lot reduction) |
| nA20>=2 skip |  | -6/-1/14 | -10/0/-1/17 | -11/-2/16 | -273 | 0.76/0.67 | 1/6/8 | -16/4/-2 | -4 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA20>=3 skip |  | 1/0/-2 | -2/0/0/7 | -1/1/8 | 192 | 0.49/0.55 | 0/0/11 | -1/3/-8 | -2 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA40>=1 skip | +5 / -5 / -4 (NOISE (v1.2 assumed); sA40>=1 pub: 36/0/-5 NOISE ONE-WEEK) | -17/9/10 | -27/-2/9/2 | -104/-48/-59 | -8321 | 0.83/0.73 | -9/20/32 | -55/20/12 | -10 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA40>=2 skip |  | -1/-2/27 | -9/7/-2/10 | -21/-13/0 | -2541 | 0.57/0.76 | -25/19/33 | -23/5/8 | -8 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA40>=3 skip |  | 1/0/21 | -5/0/0/24 | -4/1/24 | 214 | 0.47/0.64 | 2/-2/16 | -8/-9/-1 | -5 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA60>=1 skip | +36 / -36 / +7 (NOISE ONE-WEEK) | -11/12/6 | -11/-0/12/6 | -58/-26/-34 | -6498 | 0.66/0.68 | 36/30/-4 | 9/12/-2 | +0 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA60>=2 skip |  | -3/4/34 | -12/10/4/26 | -37/-18/9 | -4458 | 0.58/0.68 | -44/2/24 | -43/13/18 | -8 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA60>=3 skip |  | 0/1/32 | -6/2/1/17 | -4/3/18 | 462 | 0.50/0.73 | -7/2/28 | -13/-2/1 | -6 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| rho60>=2 skip | +41 / +1 / +36 (VOLUME ONE-WEEK) | 3/15/4 | 3/-9/17/-18 | -6/10/-28 | -1858 | 0.54/0.49 | 38/7/23 | 21/21/-22 | +0 | L6M and PRE cut > 0 on all 3 bases (screen); negative at equal mean (cut is lot reduction) |

ZOFF = live zone half undone (a REFERENCE row: the layer stays ON; a negative cut means removing it deepens drawdown). ZREPLAY = replay of the published 8-line PoiSet HALF D20 on every trade = the REF_S4A first-order cross-check (M table /mnt/l2/l2vast/_th_zn/M_ZN_REF_S4A.npz); in the exact engine the S4A published layer IS the live layer, so its exact row is the live-layer reference row of SZ-CORE (replay vs live half agree on 88.5% of informative trades).

### Whole HALF layer vs zone off (maxDD cut of the layer, + = the layer makes drawdown shallower)

| source | L6M | HOLD | MID | PRE | X' | note |
|---|---|---|---|---|---|---|
| published V13T (old engine; take lines off, lock none) | +20 | +15 | +20 | -1 | -19 | DS3_ZONES_3_HALF_FINAL_V13T.md; ranks vs placebo 0.32 / 0.24 / 0.36 / 0.70 / 0.86 |
| published V13TLIVE | +7 | +7 | +25 | +7 | -16 | DS3_ZONES_3_HALF_FINAL_V13TLIVE.md |
| new S1b-COMB first-order (ZOFF rescored, all weeks, 11-09) | 13 | 11 | -4 | 3 | 6 | layer vs ZOFF; ZOFF is first-order (undo the replay-inferred live half at chain_nz lots) |

### Base-change proof (same reference row, three bases; Q1-A with the live zone layer; stack, all weeks)

| base | trades | zone-inferred share | maxDD L6M | maxDD PRE | maxDD X' | maxDD HOLD | mean $/wk L6M |
|---|---|---|---|---|---|---|---|
| old V0 (V13T ts2, per-print cuts) | 21397 | 8.2% | 104809 | 88180 | 80802 | 122025 | 23778 |
| replica HOLD (S1b engine, old live cut) | 23855 | 7.2% | 119980 | 155580 | 75870 | 119980 | 19166 |
| S1b-COMB (state cut, live D7 v1.5) | 21135 | 7.5% | 79907 | 140288 | 128944 | 99496 | 26769 |

Reading: the base changed (SZ_BASE_PROOF.md: state cuts 38% of exits vs 54-57% per-print cuts, stops 3% -> 14%), and the zone-cell cuts move 20-60 points between bases; the half-type cells keep a positive L6M/PRE cut on every base mainly because they halve 47-81% of trades, which is why the equal-mean column and the placebo decide, not the cut. Per-line published cells (kijun1h, PDmid, CRT4h, KCup4h, camH3, OTE705/79/62 HALF and SKIP marginals; V13T and V13TLIVE) need the exact engine with one line left out and are NOT re-scored here (first-order cannot isolate a line: the replay only stores the nearest line); the whole-layer row above stands in. The B73 / B8 / generic-B73 pages (DS3_B73_ORDERING_NOTE.md, DS3_B8_ZONE_TARGET_SHIPPED_V13Z.md, DS3_ZONES_3_B73_GENERIC.md) are delay/re-target actions: exact-engine only, not re-scored in this refresh.


### The same S4 / ZONES-3 cells on the ROLL-FIXED base (lifted M tables)

| cell | cut L6M/L3M/L1M | HOLD/PRE/X' | equal-mean L6M | dMean L6M |
|---|---|---|---|---|
| ZOFF | -15/-15/-5 | -13/-3/-6 | -9 | 1352 |
| ZREPLAY | -13/-11/-2 | -8/1/7 | -18 | -907 |
| open20 half | 32/32/47 | 39/41/33 | 6 | -5920 |
| open40 half | 27/27/51 | 34/34/31 | 16 | -2932 |
| open60 half | -4/-4/47 | 17/34/28 | -11 | -1405 |
| openA40 half | 35/35/52 | 34/37/38 | 17 | -6125 |
| openA60 half | 13/13/50 | 27/35/39 | -16 | -6938 |
| sopen40 half | 4/4/42 | 23/35/30 | -3 | -1500 |
| nA20>=2 skip | -10/-10/-6 | 0/-1/16 | -11 | -273 |
| nA20>=3 skip | -2/-2/1 | 0/0/6 | -1 | 192 |
| nA40>=1 skip | -27/-17/-17 | -2/9/3 | -104 | -8298 |
| nA40>=2 skip | -9/-9/-1 | 7/-2/9 | -21 | -2541 |
| nA40>=3 skip | -5/-5/1 | 0/0/22 | -4 | 214 |
| nA60>=1 skip | -11/-11/-11 | 11/12/7 | -58 | -6475 |
| nA60>=2 skip | -12/-12/-3 | 10/4/24 | -37 | -4458 |
| nA60>=3 skip | -6/-6/0 | 2/1/16 | -4 | 462 |
| rho60>=2 skip | 3/3/3 | 13/15/-17 | -4 | -1522 |

## 6. REFIT 2026-11-22 (settings the bi-weekly procedure would pick today)

Procedure: trailing 26 weeks of data to 2026-11-05, pool = scope top 40 cells + live, pick lowest weekly maxDD among cells whose trailing mean >= live - $1k/wk, else live.

| scope | pick | trailing maxDD pick/live | trailing mean pick/live |
|---|---|---|---|
| ALL | STRUCT k7st_1 v0 hw0 pt30 BA quarter (first-order only; exact required before adoption) | 36422 / 79907 | 23480 / 24125 |
| KB | BOOK ice_w120_n2 BH-absent:B20 skip (first-order only; exact required before adoption) | 74137 / 79907 | 24611 / 24125 |
| PE | STRUCT k7st_1 v0 hw0 pt30 BA skip (first-order only; exact required before adoption) | 32939 / 79907 | 23665 / 24125 |
| SM | STRUCT rn100 v0 hw10 atr1.5 BP skip (first-order only; exact required before adoption) | 72105 / 79907 | 23322 / 24125 |
| HM | BOOK wall_k3_p0 AH:A0.5|s-1|tch0|any skip (first-order only; exact required before adoption) | 79821 / 79907 | 24098 / 24125 |
| MV | BOOK swp_w900_t6 AH:A0.5|s-1|any|any skip (first-order only; exact required before adoption) | 63343 / 79907 | 26697 / 24125 |
| asia | STRUCT sw5_3 v5 hw10 pt90 BA skip (first-order only; exact required before adoption) | 44554 / 79907 | 27027 / 24125 |
| london | CORE ALL ahead 60pts hw2 fresh=t0 age<=5d skip (first-order only; exact required before adoption) | 35161 / 79907 | 27782 / 24125 |
| nyam | STRUCT rn25 v0 hw0 pt15 AP skip (first-order only; exact required before adoption) | 66384 / 79907 | 23720 / 24125 |
| KB|asia | BOOK maxsz_w300 BH-absent:B5 skip (first-order only; exact required before adoption) | 70782 / 79907 | 23190 / 24125 |
| KB|london | BOOK maxsz_w300 BH-absent:B5 skip (first-order only; exact required before adoption) | 73485 / 79907 | 23966 / 24125 |
| KB|nyam | BOOK ice_w600_n4 AH:D5|s-1|any|any skip (first-order only; exact required before adoption) | 78902 / 79907 | 24183 / 24125 |
| KB|nypm | STRUCT confB10 v0 hw0 np16 NP skip (first-order only; exact required before adoption) | 75076 / 79907 | 24320 / 24125 |
| PE|asia | STRUCT sw5_5 v7 hw10 pt90 BA skip (first-order only; exact required before adoption) | 52055 / 79907 | 27805 / 24125 |
| PE|london | BOOK ice_w600_n1 AH:D5|s-1|any|any skip (first-order only; exact required before adoption) | 52264 / 79907 | 23633 / 24125 |
| PE|nyam | BOOK ice_w120_n4 BH-absent:B5 skip (first-order only; exact required before adoption) | 63622 / 79907 | 24442 / 24125 |
| SM|asia | STRUCT tenkan_60 v0 hw10 pt40 AP skip (first-order only; exact required before adoption) | 75506 / 79907 | 24202 / 24125 |
| SM|london | BOOK ice_w600_n1 AH:D5|s-1|any|any skip (first-order only; exact required before adoption) | 65976 / 79907 | 24327 / 24125 |
| HM|asia | STRUCT ote15_any v0 hw0 atr0.25 BP skip (first-order only; exact required before adoption) | 77732 / 79907 | 24276 / 24125 |
| MV|london | BOOK ice_w120_n2 BH-absent:B5 skip (first-order only; exact required before adoption) | 68731 / 79907 | 25102 / 24125 |
| MV|nyam | BOOK maxsz_w900 AH:D90|s-1|any|any skip (first-order only; exact required before adoption) | 78470 / 79907 | 24575 / 24125 |
| PB|asia | BOOK wall_k2_p5 BH-absent:B5 skip (first-order only; exact required before adoption) | 79517 / 79907 | 23713 / 24125 |

## UPDATE (zone-STATE actions and per-line marginals; exact engine, ROLLFIX1; first rows as months land)

Hooks: code/th_zn_act/zone_hooks.py (mixin on the live engine with the live zone layer ON; level table = nearest family level ahead/behind at the signal second, ZN-CORE lv_A / lv_B; regression: the empty-config set ZNA_NULL reproduces the S1b-COMB base list for 202610 to the dollar, 823 trades). Signals created only by the new engine path (re-entries after a held/dropped signal) carry no level row and run live. Sets ZNA_*, queue code/th_zn_act/zone_queue.py (2 workers, gate MemAvailable >= 55 GB, load < 32), order L6M then PRE months; HOLD / X' for the top 3 by L6M + PRE after those land. Cut = maxDD cut vs the ROLLFIX1 base (+ = shallower); WF = bi-weekly re-pick (single cell vs live, exact daily series; months not run count as live); rule 2a by Z.prior_info.

### Zone-state actions

| set | action | months | cut L1M/L3M/L6M | HOLD/PRE/X' cut | equal-mean L6M/PRE | d mean $/wk L6M/PRE | trades vs base | WF beat% (non-live picks) / OOS cut% | rule 2a label (old) |
|---|---|---|---|---|---|---|---|---|---|
| ZNA_DELAY_A | delay-until-through: family-A level ahead within 20 pts; hold <= 20 min; stop unchanged | 3 | 2/-10/ | // | / | / | 2062 vs 21163 | n/a (< 12 months) | PRE pending |
| ZNA_RET_A | re-target to the family-A level ahead (within 60 pts) minus 0.5 pt | 3 | 77/-19/ | // | / | / | 2616 vs 21163 | n/a (< 12 months) | PRE pending |
| ZNA_RETB_A | re-target BEYOND the family-A level ahead (within 40 pts) by +5 pts (magnet) | 3 | 64/-25/ | // | / | / | 2686 vs 21163 | n/a (< 12 months) | PRE pending |
| ZNA_STOP_A | structure stop just beyond the family-A level behind (6-40 pts, buffer 2) with lots scaled for equal $ risk (cap 3x) | 3 | 13/-63/ | // | / | / | 2222 vs 21163 | n/a (< 12 months) | PRE pending |
| ZNA_B73_A | generalised B73 (70% now / 30% when price trades through) at the family-A level ahead within 30 pts | 3 | -5/-30/ | // | / | / | 2152 vs 21163 | n/a (< 12 months) | PRE pending |
| ZNA_COOL_A | cooldown 15 min after the family-A level behind (within 40 pts) is lost | 3 | -4/-4/ | // | / | / | 2158 vs 21163 | n/a (< 12 months) | PRE pending |
| ZNA_DELAY_B | delay-until-through, family-B level ahead within 20 pts | 3 | -5/-5/ | // | / | / | 2137 vs 21163 | n/a (< 12 months) | PRE pending |
| ZNA_RET_B | re-target to the family-B level ahead (within 60 pts) minus 0.5 pt | 3 | 82/-72/ | // | / | / | 2652 vs 21163 | n/a (< 12 months) | PRE pending |

### Per-line marginals of the eight published zone lines (the live layer with ONE line left out; cut vs the live layer: negative = the line HELPS)

| line left out | months | cut L1M/L3M/L6M | HOLD/PRE/X' | d mean $/wk L6M/PRE | trades vs base |
|---|---|---|---|---|---|
| PD_mid | 20 | 0/0/0 | // | 4/ | 11762 vs 21163 |
| RTH_camH3 | 20 | -3/-4/-4 | // | 283/ | 11773 vs 21163 |
| Kijun_1h | 20 | -3/-3/-3 | // | 136/ | 11758 vs 21163 |
| CRT_mid_4h | 20 | 0/0/0 | // | 296/ | 11752 vs 21163 |
| KC_up_4h | 20 | 0/0/0 | // | -53/ | 11755 vs 21163 |
| OTE62_15m | 20 | 0/0/0 | // | -948/ | 11768 vs 21163 |
| OTE705_15m | 20 | -5/-7/-7 | // | -69/ | 11754 vs 21163 |
| OTE79_15m | 20 | 0/0/0 | // | 679/ | 11723 vs 21163 |

### Leave-one-out proof (counters from the hook, all months run so far)

| line left out | runs (months) | NTZ checks | checks where the line was eligible (<= 20 ahead, untouched) | ... and it was the ONLY eligible line | zone-HALF decisions changed | OTE-62 B73 paths suppressed |
|---|---|---|---|---|---|---|
| PD_mid | 16 | 8903 | 86 | 36 | 36 | 0 |
| RTH_camH3 | 16 | 8913 | 106 | 87 | 87 | 0 |
| Kijun_1h | 16 | 8906 | 132 | 70 | 70 | 0 |
| CRT_mid_4h | 16 | 8892 | 145 | 123 | 123 | 0 |
| KC_up_4h | 16 | 8697 | 89 | 70 | 70 | 0 |
| OTE62_15m | 16 | 9326 | 291 | 195 | 195 | 417 |
| OTE705_15m | 16 | 8900 | 190 | 121 | 121 | 0 |
| OTE79_15m | 16 | 8885 | 299 | 219 | 219 | 0 |

A line only changes the zone action when it is the only eligible line; the counts show how often that happens (most eligible checks are sole-eligible, so the lines are NOT redundant by construction, but each changes only a handful of decisions per month). An earlier first-pass run showed exactly zero effect for the single lines because of an engine load-cache bug (every set in a batch inherited the first set's config); it was fixed and all ZNA runs were redone.

Placebo / family null for these exact cells: only 16 exact cells exist, so the family max-stat is not meaningful; the exact placebo is the shifted-level rerun of the top 3 (levels +25 pts; sets ZNA_*_SH25 queued after the L6M + PRE rows land). Zone-state actions NOT built: state-cut arm widening (cut layer owner), 70/30 add with a true resting limit at the level (needs the entry-limit hooks of R4 composed; B73-generalised above is the market-through variant).


## 7. Caveats

- First-order vs exact: first-order rescales pnl per lot and cannot see re-entries, caps, locks or exit-type changes; every exact re-run so far (section 2) is far smaller than the first-order cut for skip/quarter cells. The exact table is the evidence; the first-order tables are screens.
- Engine: ROLLFIX1 closes positions at the engine market-walk price on the pre-roll book at each of the 14 rolls and suppresses entries from roll-120 s to roll+300 s; exact months carry engine_ver in the table. Stop-fill bias of the replica engine (stops fill at the engine walk price, slippage on stops understated) is unchanged and inflates every drawdown comparison the same way. Entries are not live-matched (entry match < .85) so everything is PRE-PROOF.
- Data: levels come from the 1-s state arrays of NQ only (2023-04-03..2026-11-05), roll-continuous; volume profile = traded prints (not chart volume); no news series owned; ES/RTY depth levels are not used (the live NQ book carried ES/RTY levels so live cuts are not ground truth); other instruments are not covered by the zone study. Warm-up: week/month/composite levels start ~May-June 2023, so X' has fewer level-days. Held-out live week (frozen file) is first-order and mechanically penalises skips in a +$105k week.
- Hypothesis counts: CORE 347,553 cells; STRUCT 9,263,348 evaluated; BOOK 32,155; TRIG 1,334,592. Family p uses the conservative independent max-stat; with these counts nothing can reach p <= .10 without a very large effect.
- Not built: delay-until-through, re-target, structure-stop, 70/30 add and cooldown-after-lost-level actions (exact engine only); per-line marginals of the published eight lines (need the engine with one line left out).

Generated by code/th_zn/zn_final.py (2026-11-11 11:44Z).