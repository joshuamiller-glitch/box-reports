# DS3_P7_ASIA_REENTRY - P7 Asia same-side re-entry after a loser (W-PR, PRIORITY 3 of BACK TO D7)
**VERDICT: UPDATE 3 (full 43-month run of BLK_M30 and 12 expansion cells; first pass, base-lot dollars, x1.75 and $4.84 columns beside): NO RULE IS A LEAD. BLK_M30 (30-min same-side block after a P7 Asia loser) is +1,210 / +1,428 $/wk and cuts DD 16.9% in L3M / L6M, but weekly cluster t is 1.1 / 1.0 (95% CI spans zero), the DD gain is W44 only (ex-W44 DD cut 0.0), HOLD +642 (DD +6.1%), PRE -783, X' +61, GAP 0; best recent expansion is the same block on all six books in Asia (XB_ALLBK: L3M +2,531, L6M +2,812 with t 1.8, DD cut 19.9%, HOLD +1,234, but PRE -919); HALF (half size on same-side re-entry) passes the tolerant gate in L3M/L6M/HOLD/PRE but is worth +1,356 / +608 / +72 / -339 $/wk with t below 1; evidence blocks, session caps, loss caps and every other session fail. Recent-only, weak, no PASS.**

Page stamp 2026-11-16T15:04Z (epoch 1794841492). Label: PRE-PROOF, post-hoc, Shadow only, no PASS claims. Prereg autopilot/P7_ASIA_REENTRY_PREREG.md (sha in DECISIONS.md before any exact cell). Code code/th_p7re/ (pr_load, pr_meas2, pr_fo, pr_hooks, pr_cells, pr_driver, pr_score, pr_page). Base: JN05W2 exact engine, all layers ON (which already contains the c_gov governor: skip a P7 signal after >= 2 same-side losers in the session unless a new session extreme was made). Fills as measured (+0.23 entry / +0.44 stop / +1.36 at 08:30 pts, $4.84 RT). Recent max DD is ONE week (2026-W44, 10-26..11-01, stack -36.4k); read drawdown against the -W44 rows and the placebos.

BASIS (one line; P7 day cap in the engine set = 8,400 base lots = 14,700 live x1.75, so the live cap is already what these sets use, no cap rerun needed): every $ on this page is the sum of the JN05W2 exact-engine trade table at BASE (box) lots, NOT live x1.75, with net_fee = gross - $1.18 per contract RT (engine's own fills), not FEES.md $4.84; the column 'd$/wk at FEES.md $4.84' reprices each trade at net_fee - 3.66 x lots (same trades, no rerun) for cell minus JN05W2.

Hook identity proof: TL3_PR_ID 202610 (hook module loaded, empty par): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL

## 1. Measurement (JN05W2 exact trade table, 43 months, 19,798 trades; P7 Asia = 2,161 trades, +915.9k)
### M1. P7 Asia P&L by entry class (JN05W2 exact, $ per week; same_after_loser = previous P7 Asia trade in the session lost on the SAME side)
| win | cls | n | d_per_wk | mean | win_rate | lots |
|---|---|---|---|---|---|---|
| L3M | fresh | 65.0 | 3997.9 | 808.4 | 47.7 | 4.7 |
| L3M | same_after_loser | 53.0 | -967.4 | -239.9 | 34.0 | 4.1 |
| L3M | opp_after_loser | 57.0 | 4521.4 | 1042.5 | 49.1 | 4.2 |
| L3M | same_after_win | 56.0 | -282.6 | -66.3 | 35.7 | 5.3 |
| L3M | opp_after_win | 12.0 | 281.7 | 308.6 | 41.7 | 3.3 |
| L6M | fresh | 131.0 | 3695.2 | 741.5 | 49.6 | 4.5 |
| L6M | same_after_loser | 128.0 | 492.3 | 101.1 | 41.4 | 4.1 |
| L6M | opp_after_loser | 124.0 | 4306.5 | 912.9 | 46.8 | 4.3 |
| L6M | same_after_win | 163.0 | 3450.0 | 556.4 | 42.9 | 5.3 |
| L6M | opp_after_win | 29.0 | -30.7 | -27.8 | 37.9 | 3.9 |
| HOLD | fresh | 257.0 | 2140.8 | 434.3 | 45.1 | 4.6 |
| HOLD | same_after_loser | 203.0 | 992.4 | 254.9 | 42.4 | 4.3 |
| HOLD | opp_after_loser | 221.0 | 3551.2 | 837.9 | 47.1 | 4.4 |
| HOLD | same_after_win | 266.0 | 1794.1 | 351.7 | 39.5 | 5.4 |
| HOLD | opp_after_win | 39.0 | 491.9 | 657.7 | 43.6 | 4.1 |
| PRE | fresh | 191.0 | 3646.7 | 744.6 | 49.2 | 4.6 |
| PRE | same_after_loser | 71.0 | 1643.5 | 902.8 | 45.1 | 4.5 |
| PRE | opp_after_loser | 93.0 | -651.9 | -273.4 | 32.3 | 4.7 |
| PRE | same_after_win | 109.0 | 526.9 | 188.5 | 36.7 | 5.3 |
| PRE | opp_after_win | 10.0 | -11.3 | -43.9 | 40.0 | 4.5 |
| X' | fresh | 382.0 | 602.2 | 123.6 | 46.1 | 4.3 |
| X' | same_after_loser | 21.0 | 141.3 | 527.8 | 47.6 | 4.3 |
| X' | opp_after_loser | 66.0 | 1305.9 | 1551.8 | 51.5 | 5.1 |
| X' | same_after_win | 60.0 | -123.2 | -161.1 | 36.7 | 5.9 |
| X' | opp_after_win | 11.0 | 210.7 | 1502.5 | 54.5 | 3.7 |
| GAP | fresh | 66.0 | 4272.5 | 850.8 | 53.0 | 4.3 |
| GAP | same_after_loser | 5.0 | -1210.0 | -3180.7 | 0.0 | 4.2 |
| GAP | opp_after_loser | 18.0 | 169.9 | 124.0 | 38.9 | 4.4 |
| GAP | same_after_win | 16.0 | 1495.2 | 1228.2 | 43.8 | 5.4 |
| GAP | opp_after_win | 1.0 | -187.5 | -2463.7 | 0.0 | 4.0 |
| ALL | fresh | 919.0 | 2077.5 | 423.1 | 47.2 | 4.5 |
| ALL | same_after_loser | 304.0 | 617.3 | 380.0 | 42.8 | 4.3 |
| ALL | opp_after_loser | 414.0 | 1381.6 | 624.5 | 43.7 | 4.6 |
| ALL | same_after_win | 463.0 | 607.9 | 245.7 | 38.2 | 5.4 |
| ALL | opp_after_win | 61.0 | 209.9 | 643.8 | 44.3 | 4.1 |

### M2. P7 Asia P&L by entry number in the session ($/wk; loss_sum = sum of the losing trades only)
| win | entry | n | d_per_wk | mean | loss_sum_per_wk |
|---|---|---|---|---|---|
| L3M | n=1 | 65.0 | 3997.9 | 808.4 | -8954.2 |
| L3M | n=2 | 63.0 | 3591.0 | 749.1 | -6899.8 |
| L3M | n=3 | 48.0 | 1428.7 | 391.2 | -5958.6 |
| L3M | n>=4 | 67.0 | -1466.5 | -287.7 | -9675.8 |
| L3M | n>=2 | 178.0 | 3553.2 | 262.4 | -22534.2 |
| L6M | n=1 | 131.0 | 3695.2 | 741.5 | -8697.8 |
| L6M | n=2 | 129.0 | 3549.8 | 723.3 | -7490.2 |
| L6M | n=3 | 103.0 | 684.2 | 174.6 | -6888.9 |
| L6M | n>=4 | 212.0 | 3984.0 | 494.0 | -13450.6 |
| L6M | n>=2 | 444.0 | 8218.0 | 486.5 | -27829.6 |
| HOLD | n=1 | 257.0 | 2140.8 | 434.3 | -9344.6 |
| HOLD | n=2 | 240.0 | 2821.7 | 613.0 | -7249.3 |
| HOLD | n=3 | 180.0 | 1255.3 | 363.7 | -5964.5 |
| HOLD | n>=4 | 309.0 | 2752.6 | 464.5 | -10289.6 |
| HOLD | n>=2 | 729.0 | 6829.6 | 488.5 | -23503.4 |
| PRE | n=1 | 191.0 | 3646.7 | 744.6 | -8930.6 |
| PRE | n=2 | 134.0 | 2029.9 | 590.8 | -6123.5 |
| PRE | n=3 | 71.0 | -1154.5 | -634.2 | -4197.0 |
| PRE | n>=4 | 78.0 | 631.8 | 315.9 | -3396.0 |
| PRE | n>=2 | 283.0 | 1507.2 | 207.7 | -13716.6 |
| X' | n=1 | 382.0 | 602.2 | 123.6 | -10504.2 |
| X' | n=2 | 109.0 | 619.5 | 445.8 | -3017.7 |
| X' | n=3 | 29.0 | 749.6 | 2027.3 | -549.9 |
| X' | n>=4 | 20.0 | 165.6 | 649.3 | -384.8 |
| X' | n>=2 | 158.0 | 1534.7 | 761.8 | -3952.3 |
| GAP | n=1 | 66.0 | 4272.5 | 850.8 | -8141.0 |
| GAP | n=2 | 28.0 | 2656.3 | 1246.8 | -3634.1 |
| GAP | n=3 | 10.0 | -2003.6 | -2633.3 | -2094.8 |
| GAP | n>=4 | 2.0 | -385.2 | -2531.2 | -385.2 |
| GAP | n>=2 | 40.0 | 267.6 | 87.9 | -6114.0 |
| ALL | n=1 | 919.0 | 2077.5 | 423.1 | -9620.4 |
| ALL | n=2 | 526.0 | 1583.7 | 563.4 | -4983.6 |
| ALL | n=3 | 300.0 | 356.7 | 222.5 | -2984.6 |
| ALL | n>=4 | 416.0 | 876.3 | 394.2 | -3872.5 |
| ALL | n>=2 | 1242.0 | 2816.6 | 424.4 | -11840.7 |

### M3. How much of P7 Asia loss and of the stack's 5 worst weeks sits in the 2nd+ same-side entry after a loser
| win | asia_loss_total | loss_in_same | share_pct | same_gain_total | same_net | worst5_stack | worst5_same | worst5_n2plus | worst1_week | worst1 | worst1_same |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | -413848 | -93025 | 22 | 80311 | -12714 | -43128 | -27500 | -47732 | 2026-10-26/2026-11-01 | -36371 | -15660 |
| L6M | -960148 | -203182 | 21 | 216122 | 12940 | -93509 | -20308 | -54778 | 2026-10-26/2026-11-01 | -36371 | -15660 |
| HOLD | -1712789 | -314197 | 18 | 365944 | 51748 | -199855 | -25357 | -68914 | 2026-02-02/2026-02-08 | -55145 | -5734 |
| PRE | -883240 | -108544 | 12 | 172640 | 64096 | -148490 | 9248 | -21629 | 2025-02-17/2025-02-23 | -52547 | 0 |
| X' | -1133805 | -34442 | 3 | 45525 | 11083 | -165344 | 2247 | -8141 | 2024-09-02/2024-09-08 | -45918 | 2247 |
| GAP | -187352 | -15903 | 8 | 0 | -15903 | -90217 | -9081 | -17180 | 2025-07-07/2025-07-13 | -68947 | -4713 |
| ALL | -4016295 | -478194 | 12 | 593715 | 115522 | -274481 | -18708 | -90176 | 2025-07-07/2025-07-13 | -68947 | -4713 |

### M4. 15 worst stack weeks (43 months) and the P7 Asia same-side-after-loser P&L inside them
| week | stack | p7_asia | same_after_loser | n_same |
|---|---|---|---|---|
| 2025-07-07/2025-07-13 | -68947 | -13339 | -4713 | 2 |
| 2026-02-02/2026-02-08 | -55145 | -20169 | -5734 | 6 |
| 2025-02-17/2025-02-23 | -52547 | -9313 | 0 | 0 |
| 2026-03-23/2026-03-29 | -51923 | -32568 | -10508 | 4 |
| 2024-09-02/2024-09-08 | -45918 | -6515 | 2247 | 2 |
| 2024-02-05/2024-02-11 | -44943 | -3566 | 0 | 0 |
| 2026-10-26/2026-11-01 | -36371 | -31051 | -15660 | 10 |
| 2025-12-01/2025-12-07 | -29754 | 19501 | 7102 | 3 |
| 2025-04-14/2025-04-20 | -29255 | 4618 | 9553 | 4 |
| 2024-02-26/2024-03-03 | -28169 | -23445 | 0 | 0 |
| 2024-11-18/2024-11-24 | -26977 | -23228 | -2759 | 1 |
| 2026-01-19/2026-01-25 | -26662 | -15534 | -557 | 3 |
| 2026-08-31/2026-09-06 | -26026 | -8583 | 4503 | 4 |
| 2026-05-18/2026-05-24 | -25313 | -5634 | 2763 | 5 |
| 2024-09-30/2024-10-06 | -24489 | 25691 | 0 | 0 |

### M5. L3M P7 Asia session by session (sides L/S and results in entry order)
| session (Globex date) | trades | net | fresh | same_after_loser | n_same | sides | res |
|---|---|---|---|---|---|---|---|
| 20260803 | 3 | -7555 | -3459 | -4096 | 2 | LLL | --- |
| 20260804 | 5 | 5562 | 4790 | 2403 | 1 | SSLLL | +--++ |
| 20260805 | 4 | -8111 | -3764 | -2549 | 1 | SSLL | --+- |
| 20260806 | 4 | -11212 | -3164 | -6829 | 2 | LSSS | ---- |
| 20260807 | 4 | -1339 | 7198 | -4073 | 2 | LSSS | +--- |
| 20260810 | 5 | 631 | 2403 | 4805 | 1 | LLSLL | +---+ |
| 20260820 | 6 | -3142 | 8402 | -1932 | 1 | LLSLLS | +----- |
| 20260821 | 3 | 7087 | 4805 | 4800 | 1 | LLL | +-+ |
| 20260824 | 6 | 12439 | 2403 | 4785 | 1 | LLSSSS | +--+++ |
| 20260831 | 6 | -1816 | 3601 | -5087 | 2 | SLLSSL | +----+ |
| 20260901 | 2 | 402 | -4399 | 4800 | 1 | LL | -+ |
| 20260902 | 3 | -1207 | -4064 | 4790 | 1 | LSS | --+ |
| 20260908 | 6 | 12185 | 1199 | -1309 | 1 | SLLLLS | +++--+ |
| 20260910 | 3 | -4394 | -2924 | -2669 | 1 | SSL | --+ |
| 20260914 | 4 | 13116 | 8397 | 2398 | 1 | SSSS | +-++ |
| 20260915 | 4 | -5244 | -2574 | 2398 | 1 | SLSS | ---+ |
| 20260916 | 5 | -896 | -350 | 3981 | 3 | LLLLL | --+-+ |
| 20260924 | 4 | 6375 | -3669 | 4785 | 1 | LSSS | -+-+ |
| 20260928 | 6 | 8200 | -4485 | 11983 | 2 | SSSSSS | -+-++- |
| 20260929 | 5 | 9273 | -2544 | 4800 | 1 | LSSSS | -+-++ |
| 20260930 | 7 | -3988 | 4795 | -5427 | 2 | LSSSLSS | ++----- |
| 20261005 | 5 | -1152 | -3493 | 4790 | 1 | LLLSS | -+-+- |
| 20261009 | 3 | -10223 | -4244 | -2012 | 1 | LSS | --- |
| 20261012 | 7 | 7598 | 8392 | -2614 | 1 | LLSSSLS | +-+---+ |
| 20261013 | 5 | 3457 | 8377 | -4383 | 1 | SSSSL | ++--- |
| 20261014 | 3 | 5233 | -610 | -2534 | 1 | LLS | --+ |
| 20261015 | 6 | -1504 | 4790 | -6632 | 3 | SSSSSS | ++---- |
| 20261016 | 4 | -4599 | -4453 | -1929 | 1 | SLLL | -+-- |
| 20261020 | 6 | 2159 | 4795 | -2504 | 1 | SSLLSS | ++--+- |
| 20261022 | 5 | 17327 | 5984 | 4790 | 1 | SSSSS | +++-+ |
| 20261023 | 4 | -8611 | -1824 | -6787 | 3 | LLLL | ---- |
| 20261026 | 5 | 6611 | 8387 | 838 | 2 | LSSSS | +-+-- |
| 20261027 | 3 | -8713 | -2469 | -4330 | 1 | LLS | --- |
| 20261028 | 5 | -8806 | -4049 | -2689 | 1 | SLLSS | -+--- |
| 20261029 | 5 | -8606 | -4230 | 107 | 3 | SSSSS | --+-- |
| 20261030 | 4 | -11537 | -1952 | -9586 | 3 | SSSS | ---- |

### M6. 12 worst P7 Asia sessions (43 months) by same-side-after-loser P&L
| session | trades | net | same_after_loser | n_same |
|---|---|---|---|---|
| 20261030 | 4 | -11537 | -9586 | 3 |
| 20250408 | 6 | -9262 | -7147 | 2 |
| 20260312 | 5 | -2779 | -7066 | 2 |
| 20260806 | 4 | -11212 | -6829 | 2 |
| 20261023 | 4 | -8611 | -6787 | 3 |
| 20261015 | 6 | -1504 | -6632 | 3 |
| 20260714 | 9 | 9625 | -6582 | 3 |
| 20260306 | 4 | -9036 | -6512 | 3 |
| 20240712 | 2 | -9663 | -5865 | 1 |
| 20240924 | 2 | -10841 | -5615 | 1 |
| 20260327 | 6 | -8039 | -5470 | 2 |
| 20260930 | 7 | -3988 | -5427 | 2 |

### M7. 12 best P7 Asia sessions (43 months) by same-side-after-loser P&L (what a block costs on trend nights)
| session | trades | net | same_after_loser | n_same |
|---|---|---|---|---|
| 20260213 | 7 | 3900 | 16798 | 3 |
| 20260713 | 6 | 4420 | 15580 | 3 |
| 20250411 | 10 | 21716 | 14386 | 3 |
| 20251117 | 4 | 8377 | 13172 | 2 |
| 20260928 | 6 | 8200 | 11983 | 2 |
| 20250417 | 5 | 8930 | 9596 | 2 |
| 20260710 | 6 | 5536 | 9596 | 2 |
| 20251107 | 6 | -4527 | 9581 | 2 |
| 20241111 | 2 | 3886 | 8407 | 1 |
| 20260717 | 5 | 8272 | 8402 | 1 |
| 20251124 | 5 | -5639 | 8402 | 1 |
| 20250401 | 2 | 4403 | 8397 | 1 |

### M8. Same-side-after-loser Asia re-entries, every book (side table)
| book | win | asia_trades | asia_d_wk | n_same | same_d_wk | same_mean | same_loss_d_wk |
|---|---|---|---|---|---|---|---|
| K7 | L3M | 333.0 | 2170.7 | 40.0 | 100.0 | 32.9 | -1541.9 |
| K7 | L6M | 787.0 | 2636.3 | 110.0 | 270.6 | 64.7 | -1951.9 |
| K7 | HOLD | 1281.0 | 2715.6 | 156.0 | 428.9 | 143.4 | -1303.9 |
| K7 | PRE | 544.0 | 886.6 | 56.0 | 111.1 | 77.4 | -811.2 |
| K7 | X' | 595.0 | 511.7 | 37.0 | -75.6 | -160.2 | -320.2 |
| K7 | ALL | 2596.0 | 1233.7 | 262.0 | 136.7 | 97.6 | -702.6 |
| U7 | L3M | 72.0 | 3297.4 | 1.0 | 182.0 | 2392.6 | 0.0 |
| U7 | L6M | 157.0 | 2501.6 | 1.0 | 91.0 | 2392.6 | 0.0 |
| U7 | HOLD | 267.0 | 1514.9 | 1.0 | 45.9 | 2392.6 | 0.0 |
| U7 | PRE | 138.0 | 1049.5 | 2.0 | 153.4 | 2992.1 | 0.0 |
| U7 | X' | 221.0 | 1232.4 | 0.0 | 0.0 | nan | 0.0 |
| U7 | ALL | 686.0 | 1412.1 | 3.0 | 44.8 | 2792.2 | 0.0 |
| M7 | L3M | 0.0 | 0.0 | 0.0 | 0.0 | nan | 0.0 |
| M7 | L6M | 0.0 | 0.0 | 0.0 | 0.0 | nan | 0.0 |
| M7 | HOLD | 0.0 | 0.0 | 0.0 | 0.0 | nan | 0.0 |
| M7 | PRE | 0.0 | 0.0 | 0.0 | 0.0 | nan | 0.0 |
| M7 | X' | 0.0 | 0.0 | 0.0 | 0.0 | nan | 0.0 |
| M7 | ALL | 0.0 | 0.0 | 0.0 | 0.0 | nan | 0.0 |
| A7 | L3M | 160.0 | -88.3 | 21.0 | -392.3 | -245.5 | -1030.8 |
| A7 | L6M | 353.0 | 772.2 | 48.0 | 34.7 | 19.0 | -968.7 |
| A7 | HOLD | 564.0 | 797.2 | 61.0 | -12.4 | -10.6 | -633.2 |
| A7 | PRE | 208.0 | 1245.6 | 10.0 | 163.6 | 638.0 | -51.6 |
| A7 | X' | 285.0 | 522.2 | 3.0 | 45.9 | 1198.8 | 0.0 |
| A7 | ALL | 1156.0 | 710.3 | 76.0 | 50.9 | 125.4 | -192.5 |
| H7 | L3M | 67.0 | 914.3 | 13.0 | 338.0 | 341.7 | -612.9 |
| H7 | L6M | 140.0 | 1831.8 | 19.0 | 278.3 | 385.1 | -425.0 |
| H7 | HOLD | 234.0 | 671.5 | 22.0 | 202.8 | 480.6 | -243.6 |
| H7 | PRE | 142.0 | 1006.0 | 9.0 | -237.5 | -1029.2 | -391.1 |
| H7 | X' | 254.0 | 981.0 | 2.0 | -22.7 | -888.5 | -22.7 |
| H7 | ALL | 700.0 | 807.1 | 34.0 | -7.9 | -43.4 | -164.3 |
| P7 | L3M | 243.0 | 7551.0 | 53.0 | -967.4 | -239.9 | -7078.0 |
| P7 | L6M | 575.0 | 11913.2 | 128.0 | 492.3 | 101.1 | -7729.7 |
| P7 | HOLD | 986.0 | 8970.4 | 203.0 | 992.4 | 254.9 | -6025.7 |
| P7 | PRE | 474.0 | 5153.9 | 71.0 | 1643.5 | 902.8 | -2783.2 |
| P7 | X' | 540.0 | 2136.9 | 21.0 | 141.3 | 527.8 | -439.2 |
| P7 | ALL | 2161.0 | 4894.1 | 304.0 | 617.3 | 380.0 | -2555.2 |

## 2. First-order screen of the rules (JN05W2 table, blocked trades removed, knock-on ignored; dDD% = max-DD cut vs REF, positive = shallower)
| rule | L3M dDD% / d$  | L6M dDD% / d$  | HOLD dDD% / d$  | PRE dDD% / d$  | X' dDD% / d$  | GAP dDD% / d$  |
|---|---|---|---|---|---|---|
| BLK_EXT | +5.7% / -11 | +5.7% / -1864 | -14.9% / -2106 | +7.2% / -1296 | -11.2% / -225 | +8.8% / +858 |
| BLK_ENT | +12.1% / +1217 | +12.1% / -949 | -5.1% / -1438 | +3.5% / -1609 | +0.0% / -1 | +6.5% / +740 |
| BLK_M30 | +16.9% / +1628 | +16.9% / +1312 | -3.5% / +543 | +7.2% / -697 | -5.2% / -80 | +0.0% / +0 |
| BLK_M60 | +8.2% / -136 | +8.2% / -155 | -11.0% / -828 | +7.2% / -850 | -11.2% / -129 | +3.4% / +521 |
| BLK_M120 | +10.1% / +1831 | +10.1% / -1104 | -6.3% / -1688 | +7.2% / -1064 | -11.2% / -149 | +8.8% / +1403 |
| BLK_OPP | +10.1% / +349 | +10.1% / -2297 | -9.8% / -1723 | +10.0% / -1794 | -11.2% / -187 | +5.7% / +1210 |
| BLK_HL | +16.5% / +631 | +16.5% / -1304 | -18.7% / -1478 | +2.9% / -1706 | +0.0% / -136 | +6.5% / +745 |
| HALF | +11.5% / +648 | +11.5% / -783 | -9.8% / -1276 | +5.0% / -861 | -3.0% / -100 | +4.4% / +870 |
| CAP2 | -15.6% / +38 | -15.6% / -4668 | +2.6% / -4008 | +13.3% / +523 | -4.7% / -915 | +9.7% / +2389 |
| CAP3 | +21.1% / +1466 | +21.1% / -3984 | +5.3% / -2753 | +1.7% / -632 | +0.0% / -166 | +3.2% / +385 |
| CAP4 | +12.5% / -193 | +12.5% / -2886 | -2.0% / -1765 | -2.6% / -87 | +0.0% / -35 | +0.0% / +0 |
| RCAP10 | -0.7% / -243 | -0.7% / -2657 | -17.8% / -2845 | +6.2% / -32 | -5.0% / -527 | +6.4% / -109 |
| RCAP15 | -3.8% / +557 | -3.8% / -1047 | -15.9% / -2146 | +6.2% / +452 | +0.0% / -206 | +3.1% / +530 |
| RCAP20 | +16.9% / +1238 | +16.9% / +328 | -0.9% / +326 | +0.0% / +88 | +0.0% / +73 | +0.0% / +0 |
| SN | +0.0% / +211 | +0.0% / +106 | +0.0% / +179 | -4.8% / -422 | -30.8% / -664 | +0.0% / +370 |

## 3. Exact engine (JN05W2 + pr_hooks, all layers ON); rows appear when every month of a window is run
| cell | win | d$/wk base | d$/wk x1.75 | d$/wk at $4.84 | DD cut % | d worst wk | best5 kept | win->lose | d full stops/wk | weekly t (cluster=week) | 95% CI d$/wk | nonzero wks | DD cut ex-W44 % | d$ ex-W44 | t ex-W44 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BLK_EXT | L3M | -4339 | -7594 | -4297 | -13.7 | -7874 | 0.98 | 2 | +0.38 | -1.89 | -8792..-206 | 13 | -36.8 | -4698 | -1.91 |
| BLK_ENT | L3M | +727 | +1272 | +729 | +6.4 | +5163 | 1.02 | 0 | +0.00 | 0.43 | -2214..+4116 | 12 | -12.7 | +0 | 0.00 |
| BLK_ENT | L6M | -2023 | -3540 | -1965 | +6.4 | +2302 | 0.88 | 0 | +0.00 | -1.28 | -4960..+1028 | 25 | -12.7 | -2481 | -1.57 |
| BLK_ENT | HOLD | -2289 | -4005 | -2236 | +4.9 | +6205 | 0.95 | 2 | +0.02 | -1.92 | -4719..-47 | 46 | +4.9 | -2520 | -2.12 |
| BLK_ENT | PRE | -1004 | -1757 | -985 | +0.8 | +0 | 0.89 | 0 | -0.10 | -1.30 | -2460..+409 | 25 |  |  |  |
| BLK_ENT | X' | -18 | -32 | -16 | +0.0 | -7302 | 0.99 | 0 | +0.00 | -0.08 | -464..+428 | 7 |  |  |  |
| BLK_ENT | GAP | +962 | +1683 | +962 | +13.2 | +850 | 1.00 | 0 | +0.00 | 1.27 | +0..+2399 | 3 |  |  |  |
| BLK_OPP | L3M | -2503 | -4379 | -2447 | -9.4 | -4360 | 0.83 | 0 | +0.23 | -0.82 | -8167..+3430 | 13 | -31.7 | -4312 | -1.60 |
| BLK_HL | L3M | +925 | +1619 | +930 | -4.2 | -1229 | 0.96 | 0 | +0.00 | 0.63 | -1477..+4116 | 13 | -0.0 | +1102 | 0.69 |
| BLK_M30 | L3M | +1210 | +2118 | +1202 | +16.9 | +10195 | 1.00 | 0 | -0.08 | 1.13 | -617..+3476 | 9 | +0.0 | +385 | 0.52 |
| BLK_M30 | L6M | +1428 | +2499 | +1427 | +16.9 | +10195 | 1.03 | 0 | +0.15 | 1.03 | -1304..+3991 | 21 | -0.0 | +1040 | 0.75 |
| BLK_M30 | HOLD | +642 | +1123 | +643 | +6.1 | -14091 | 0.99 | 0 | +0.12 | 0.75 | -1037..+2322 | 37 | +6.1 | +435 | 0.51 |
| BLK_M30 | PRE | -783 | -1370 | -777 | +2.0 | +0 | 0.95 | 1 | +0.00 | -1.05 | -2194..+615 | 19 |  |  |  |
| BLK_M30 | X' | +61 | +107 | +62 | +0.0 | -65 | 1.03 | 0 | +0.00 | 0.59 | -111..+279 | 7 |  |  |  |
| BLK_M30 | GAP | +0 | +0 | +0 | +0.0 | +0 | 1.00 | 0 | +0.00 | nan | +0..+0 | 0 |  |  |  |
| BLK_M60 | L3M | +1366 | +2390 | +1365 | -0.4 | +587 | 1.00 | 0 | -0.08 | 0.59 | -2622..+5953 | 12 | -20.8 | +100 | 0.05 |
| BLK_M120 | L3M | -2069 | -3620 | -2036 | -14.3 | -5887 | 0.99 | 1 | +0.38 | -0.78 | -7300..+2474 | 13 | -37.5 | -2804 | -1.01 |
| HALF | L3M | +1356 | +2372 | +1375 | +0.9 | +491 | 1.06 | 0 | +0.00 | 0.69 | -2055..+5303 | 13 | -15.5 | +1178 | 0.55 |
| HALF | L6M | +608 | +1064 | +639 | +0.9 | +491 | 0.96 | 0 | +0.00 | 0.51 | -1696..+2795 | 26 | -15.5 | +493 | 0.40 |
| HALF | HOLD | +72 | +126 | +99 | +5.2 | +10464 | 0.98 | 1 | +0.04 | 0.08 | -1823..+1824 | 48 | +5.2 | +5 | 0.01 |
| HALF | PRE | -339 | -594 | -326 | +2.5 | +0 | 0.97 | 0 | +0.03 | -0.77 | -1237..+495 | 32 |  |  |  |
| HALF | X' | -231 | -404 | -229 | -2.2 | -6236 | 1.01 | 0 | -0.01 | -1.61 | -533..+15 | 14 |  |  |  |
| HALF | GAP | +1141 | +1996 | +1143 | +9.9 | +1854 | 1.03 | 0 | +0.00 | 2.19 | +265..+2101 | 5 |  |  |  |
| CAP2 | L3M | -2454 | -4295 | -2341 | -13.3 | +8330 | 0.91 | 1 | +0.38 | -0.97 | -6784..+2615 | 13 | -36.4 | -4327 | -2.37 |
| CAP3 | L3M | -3500 | -6126 | -3428 | +21.1 | +10651 | 0.77 | 1 | +0.46 | -0.88 | -11002..+3508 | 13 | +5.1 | -5630 | -1.55 |
| CAP4 | L3M | -1545 | -2704 | -1515 | +12.5 | +9367 | 0.97 | 1 | +0.08 | -0.67 | -6244..+2136 | 12 | -5.3 | -2671 | -1.22 |
| RCAP10 | L3M | +601 | +1052 | +608 | -1.5 | +4577 | 1.00 | 0 | +0.00 | 0.49 | -1555..+3077 | 7 | -22.1 | -87 | -0.08 |
| RCAP15 | L3M | -149 | -260 | -137 | +16.2 | +5685 | 0.94 | 0 | -0.08 | -0.09 | -3151..+2744 | 5 | +0.0 | -904 | -0.59 |
| RCAP15 | L6M | -756 | -1323 | -741 | +16.2 | +5685 | 0.87 | 0 | -0.04 | -0.56 | -3641..+1549 | 10 | +0.0 | -1143 | -0.85 |
| RCAP15 | HOLD | -365 | -638 | -355 | -3.6 | +0 | 0.96 | 1 | -0.02 | -0.50 | -1951..+951 | 14 | -3.6 | -548 | -0.76 |
| RCAP15 | PRE | +30 | +52 | +32 | +0.0 | +0 | 1.00 | 0 | +0.00 | 0.10 | -581..+571 | 6 |  |  |  |
| RCAP15 | X' | -2 | -4 | -1 | +0.0 | +0 | 1.00 | 0 | +0.00 | -0.14 | -34..+28 | 2 |  |  |  |
| RCAP15 | GAP | +0 | +0 | +0 | +0.0 | +0 | 1.00 | 0 | +0.00 | nan | +0..+0 | 0 |  |  |  |
| RCAP20 | L3M | +185 | +324 | +186 | +0.0 | +0 | 1.00 | 0 | +0.00 | 1.00 | +0..+561 | 1 | +0.0 | +200 | 1.00 |
| SN | L3M | +211 | +370 | +215 | +0.0 | +0 | 1.00 | 0 | +0.00 | 1.00 | +0..+640 | 1 | +0.0 | +229 | 1.00 |
| XB_K7 | L3M | +843 | +1476 | +845 | +15.0 | +7945 | 1.01 | 0 | -0.08 | 1.33 | -96..+2308 | 11 | +3.6 | +259 | 0.99 |
| XB_K7 | L6M | +1181 | +2066 | +1182 | +15.0 | +7945 | 1.01 | 0 | +0.00 | 2.00 | +22..+2240 | 21 | +3.6 | +913 | 1.67 |
| XB_K7 | HOLD | +620 | +1085 | +621 | +3.8 | -9368 | 1.00 | 0 | +0.00 | 1.52 | -166..+1423 | 36 | +3.8 | +477 | 1.23 |
| XB_K7 | PRE | -9 | -16 | -9 | +1.1 | +0 | 0.98 | 0 | -0.03 | -0.03 | -576..+532 | 15 |  |  |  |
| XB_K7 | X' | +114 | +200 | +114 | +1.2 | -795 | 0.99 | 0 | -0.01 | 0.57 | -235..+572 | 12 |  |  |  |
| XB_K7 | GAP | -16 | -28 | -17 | +2.2 | +0 | 1.00 | 0 | +0.00 | -0.08 | -366..+368 | 3 |  |  |  |
| XB_U7 | L3M | +0 | +0 | +0 | +0.0 | +0 | 1.00 | 0 | +0.00 | nan | +0..+0 | 0 | +0.0 | +0 |  |
| XB_M7 | L3M | +0 | +0 | +0 | +0.0 | +0 | 1.00 | 0 | +0.00 | nan | +0..+0 | 0 | +0.0 | +0 |  |
| XB_A7 | L3M | -16 | -27 | -16 | -0.3 | -847 | 1.00 | 0 | +0.00 | -0.18 | -197..+152 | 3 | +0.0 | +53 | 0.96 |
| XB_H7 | L3M | +0 | +0 | +0 | +0.0 | +0 | 1.00 | 0 | +0.00 | nan | +0..+0 | 0 | +0.0 | +0 |  |
| XB_ALLBK | L3M | +2531 | +4430 | +2524 | +19.9 | +10424 | 1.03 | 0 | -0.15 | 1.40 | -223..+6545 | 11 | +3.6 | +902 | 1.07 |
| XB_ALLBK | L6M | +2812 | +4921 | +2810 | +19.9 | +10424 | 1.02 | 0 | +0.19 | 1.75 | -215..+5752 | 24 | +3.6 | +2041 | 1.39 |
| XB_ALLBK | HOLD | +1234 | +2160 | +1236 | +8.6 | -25453 | 0.97 | 0 | +0.15 | 1.19 | -810..+3307 | 42 | +8.6 | +822 | 0.85 |
| XB_ALLBK | PRE | -919 | -1608 | -914 | +4.3 | +0 | 0.92 | 1 | +0.03 | -1.15 | -2545..+474 | 24 |  |  |  |
| XB_ALLBK | X' | +175 | +306 | +176 | +0.8 | -860 | 1.03 | 0 | -0.01 | 0.80 | -215..+670 | 16 |  |  |  |
| XB_ALLBK | GAP | -16 | -28 | -17 | +2.2 | +0 | 1.00 | 0 | +0.00 | -0.08 | -366..+368 | 3 |  |  |  |
| XS_P7_LON | L3M | -236 | -414 | -234 | +0.0 | +0 | 0.99 | 0 | +0.00 | -0.93 | -712..+207 | 10 | -5.1 | -256 | -0.93 |
| XS_ALL_LON | L3M | -1364 | -2388 | -1352 | +0.4 | +1430 | 0.96 | 0 | -0.08 | -2.16 | -2631..-248 | 13 | -10.0 | -1594 | -2.50 |
| XS_P7_NYAM | L3M | +275 | +481 | +277 | +0.0 | +0 | 1.01 | 0 | +0.00 | 1.04 | -253..+710 | 8 | +0.0 | +297 | 1.04 |
| XS_ALL_NYAM | L3M | +148 | +259 | +153 | +0.0 | +0 | 1.01 | 0 | +0.00 | 0.48 | -468..+697 | 11 | +0.0 | +160 | 0.48 |
| XS_P7_NYPM | L3M | +0 | +0 | +0 | +0.0 | +0 | 1.00 | 0 | +0.00 | nan | +0..+0 | 0 | +0.0 | +0 |  |
| XS_ALL_NYPM | L3M | -97 | -170 | -96 | +0.0 | +0 | 0.99 | 0 | +0.00 | -0.48 | -525..+189 | 3 | +0.0 | -105 | -0.48 |
| XG_N15 | L3M | +1069 | +1870 | +1056 | +10.5 | +5471 | 1.04 | 0 | +0.15 | 1.18 | -273..+3070 | 5 | +0.0 | +706 | 0.79 |
| XG_N15 | L6M | +619 | +1082 | +616 | +10.5 | +5471 | 1.01 | 0 | +0.19 | 0.75 | -886..+2246 | 16 | +0.0 | +427 | 0.51 |
| XG_N15 | HOLD | +150 | +263 | +147 | -0.0 | -3776 | 1.00 | 0 | +0.12 | 0.29 | -873..+1146 | 26 | -0.0 | +46 | 0.09 |
| XG_N15 | PRE | -459 | -803 | -457 | +3.1 | +0 | 0.98 | 1 | -0.03 | -1.04 | -1393..+307 | 14 |  |  |  |
| XG_N15 | X' | +124 | +217 | +125 | +0.0 | +0 | 1.03 | 0 | +0.00 | 1.39 | -2..+322 | 3 |  |  |  |
| XG_N15 | GAP | +0 | +0 | +0 | +0.0 | +0 | 1.00 | 0 | +0.00 | nan | +0..+0 | 0 |  |  |  |
| XG_N45 | L3M | +73 | +128 | +73 | +2.0 | +2406 | 0.99 | 0 | +0.00 | 0.05 | -2293..+2779 | 10 | -18.0 | -945 | -0.98 |
| XG_N45 | L6M | +484 | +847 | +510 | +2.0 | +2406 | 1.06 | 0 | +0.04 | 0.29 | -3008..+3516 | 23 | -18.0 | +11 | 0.01 |
| XG_N45 | HOLD | -263 | -461 | -243 | +3.2 | -5938 | 1.01 | 0 | +0.08 | -0.28 | -2172..+1554 | 42 | +3.2 | -512 | -0.54 |
| XG_N45 | PRE | -284 | -498 | -279 | +5.2 | +0 | 0.93 | 1 | +0.00 | -0.30 | -2170..+1481 | 21 |  |  |  |
| XG_N45 | X' | -163 | -285 | -161 | +0.0 | -2724 | 0.99 | 0 | -0.01 | -1.05 | -486..+120 | 8 |  |  |  |
| XG_N45 | GAP | -119 | -208 | -120 | +0.0 | +0 | 0.99 | 0 | +0.00 | -1.00 | -335..+0 | 1 |  |  |  |
| XG_N60 | L3M | +1366 | +2390 | +1365 | -0.4 | +587 | 1.00 | 0 | -0.08 | 0.59 | -2622..+5953 | 12 | -20.8 | +100 | 0.05 |
| XG_N90 | L3M | -1480 | -2590 | -1467 | -5.4 | -4341 | 0.97 | 1 | +0.23 | -0.68 | -5384..+2595 | 12 | -26.8 | -1686 | -0.72 |
| XM_W15 | L3M | +1398 | +2447 | +1373 | +17.0 | +6560 | 1.03 | 0 | -0.08 | 1.40 | -436..+3300 | 13 | +5.3 | +973 | 0.99 |
| XM_W15 | L6M | +1888 | +3305 | +1870 | +17.0 | +6560 | 1.05 | 0 | +0.19 | 1.51 | -514..+4307 | 26 | +5.3 | +1704 | 1.33 |
| XM_W15 | HOLD | +630 | +1103 | +618 | +5.3 | -14998 | 1.01 | 0 | +0.13 | 0.76 | -971..+2193 | 44 | +5.3 | +514 | 0.62 |
| XM_W15 | PRE | -655 | -1147 | -654 | -0.1 | +0 | 0.96 | 1 | +0.03 | -0.79 | -2249..+836 | 25 |  |  |  |
| XM_W15 | X' | +86 | +151 | +86 | -2.5 | -65 | 1.07 | 1 | -0.01 | 0.42 | -235..+528 | 13 |  |  |  |
| XM_W15 | GAP | +365 | +638 | +363 | +0.0 | +0 | 1.03 | 0 | +0.00 | 1.06 | -178..+1036 | 3 |  |  |  |
| XM_ONLY15 | L3M | +708 | +1239 | +693 | +0.0 | +0 | 1.04 | 0 | +0.00 | 0.81 | -753..+2554 | 11 | +5.3 | +766 | 0.81 |
| XM_ONLY30 | L3M | +1653 | +2893 | +1625 | -12.0 | -6252 | 1.14 | 0 | +0.00 | 0.63 | -1878..+7369 | 12 | +0.9 | +2304 | 0.83 |
| XG_WINBLK | L3M | -2337 | -4089 | -2311 | -2.7 | -1388 | 0.94 | 1 | +0.15 | -0.91 | -7277..+1934 | 12 | -19.3 | -2415 | -0.87 |
| XG_ANYBLK | L3M | -96 | -168 | -85 | +0.9 | +10195 | 0.88 | 0 | +0.08 | -0.04 | -5215..+4901 | 13 | -19.3 | -1603 | -0.68 |
| XG_ANYBLK | L6M | +180 | +315 | +214 | +0.9 | +10195 | 0.84 | 0 | +0.30 | 0.08 | -4173..+4215 | 27 | -19.3 | -533 | -0.25 |
| XG_ANYBLK | HOLD | +352 | +617 | +371 | +7.5 | +10954 | 0.82 | 0 | +0.13 | 0.27 | -2255..+2895 | 50 | +7.5 | +3 | 0.00 |
| XG_ANYBLK | PRE | -641 | -1122 | -631 | +5.3 | +0 | 0.86 | 0 | +0.05 | -0.76 | -2246..+951 | 30 |  |  |  |
| XG_ANYBLK | X' | -77 | -135 | -75 | -11.6 | -65 | 1.02 | 0 | +0.03 | -0.26 | -712..+430 | 20 |  |  |  |
| XG_ANYBLK | GAP | -320 | -560 | -320 | +0.2 | +200 | 1.02 | 0 | +0.08 | -0.38 | -2049..+901 | 7 |  |  |  |
| XF_CARRY | L3M | +1210 | +2118 | +1202 | +16.9 | +10195 | 1.00 | 0 | -0.08 | 1.13 | -617..+3476 | 9 | +0.0 | +385 | 0.52 |
| XF_CARRY | L6M | +1428 | +2499 | +1427 | +16.9 | +10195 | 1.03 | 0 | +0.15 | 1.03 | -1304..+3991 | 21 | -0.0 | +1040 | 0.75 |
| XF_CARRY | HOLD | +642 | +1123 | +643 | +6.1 | -14091 | 0.99 | 0 | +0.12 | 0.75 | -1037..+2322 | 37 | +6.1 | +435 | 0.51 |
| XF_CARRY | PRE | -783 | -1370 | -777 | +2.0 | +0 | 0.95 | 1 | +0.00 | -1.05 | -2194..+615 | 19 |  |  |  |
| XF_CARRY | X' | +61 | +107 | +62 | +0.0 | -65 | 1.03 | 0 | +0.00 | 0.59 | -111..+279 | 7 |  |  |  |
| XF_CARRY | GAP | +0 | +0 | +0 | +0.0 | +0 | 1.00 | 0 | +0.00 | nan | +0..+0 | 0 |  |  |  |
| XF_CARRY_ALL | L3M | +1614 | +2824 | +1611 | +12.7 | +8592 | 1.00 | 0 | +0.00 | 1.26 | -608..+4217 | 13 | -5.1 | +857 | 0.77 |
| XF_CARRY_ALL | L6M | +1237 | +2165 | +1244 | +12.7 | +8592 | 1.01 | 0 | +0.15 | 0.71 | -2123..+4553 | 26 | -5.1 | +859 | 0.48 |
| XF_CARRY_ALL | HOLD | +827 | +1447 | +831 | +7.7 | -17107 | 0.99 | 0 | +0.10 | 0.73 | -1388..+3090 | 51 | +7.7 | +632 | 0.56 |
| XF_CARRY_ALL | PRE | -637 | -1115 | -625 | +9.3 | +0 | 0.98 | 1 | +0.00 | -0.72 | -2378..+967 | 35 |  |  |  |
| XF_CARRY_ALL | X' | +508 | +890 | +512 | +2.8 | -3165 | 1.05 | 0 | +0.03 | 2.16 | +68..+984 | 53 |  |  |  |
| XF_CARRY_ALL | GAP | -93 | -163 | -90 | +8.6 | +4410 | 0.96 | 0 | +0.15 | -0.16 | -1115..+935 | 6 |  |  |  |
| XF_P7_ALLSESS | L3M | +1615 | +2826 | +1612 | +12.7 | +8592 | 1.00 | 0 | -0.08 | 1.26 | -608..+4219 | 13 | -5.1 | +858 | 0.77 |
| XF_P7_ALLSESS | L6M | +1238 | +2166 | +1244 | +12.7 | +8592 | 1.01 | 0 | +0.11 | 0.71 | -2123..+4554 | 26 | -5.1 | +860 | 0.48 |
| XF_P7_ALLSESS | HOLD | +662 | +1158 | +668 | +7.7 | -17107 | 0.99 | 0 | +0.08 | 0.61 | -1491..+2831 | 51 | +7.7 | +464 | 0.43 |
| XF_P7_ALLSESS | PRE | -609 | -1065 | -597 | +9.3 | +0 | 0.97 | 1 | -0.03 | -0.69 | -2309..+1018 | 34 |  |  |  |
| XF_P7_ALLSESS | X' | +480 | +840 | +484 | +2.8 | -3165 | 1.04 | 0 | +0.04 | 2.05 | +43..+958 | 52 |  |  |  |
| XF_P7_ALLSESS | GAP | -91 | -158 | -87 | +8.7 | +4445 | 0.96 | 0 | +0.15 | -0.16 | -1115..+942 | 6 |  |  |  |

## 2b. First-order placebos for the block rules (20 random-same-count blocks with the same eligibility, and the evidence test run on the price path 11/23/37 days earlier)
real = the rule; pl = random same-count blocks (median / 90th pct of the DD cut %, share of placebos at least as good as real); sh = DD cut % when the evidence is read off the path 11 / 23 / 37 days earlier. Time-only rules (M30/M60/M120) and OPP have no path, so sh = real.

| rule | win | blocked/eligible | real DD cut % | pl med / p90 | share pl >= real | real d$ | pl d$ med | real d worst wk | pl d worst wk med | sh11 / sh23 / sh37 DD cut % |
|---|---|---|---|---|---|---|---|---|---|---|
| BLK_EXT | L3M | 50/80 | +5.7 | +10.1 / +12.1 | 0.55 | -11 | -162 | +2245 | +5842 | +16.9 / +12.1 / +7.7 |
| BLK_EXT | L6M | 143/229 | +5.7 | +10.1 / +12.1 | 0.55 | -1864 | -2203 | +2245 | +4611 | +4.5 / +12.1 / +7.7 |
| BLK_EXT | HOLD | 226/362 | -14.9 | -5.0 / +2.8 | 0.80 | -2106 | -2319 | -4005 | +1923 | -13.1 / +2.7 / -2.5 |
| BLK_EXT | PRE | 93/120 | +7.2 | +7.9 / +12.6 | 0.60 | -1296 | -1435 | +0 | +0 | +8.3 / +1.7 / +1.7 |
| BLK_EXT | X' | 26/32 | -11.2 | -11.2 / -0.7 | 1.00 | -225 | -169 | -2247 | -2247 | -0.7 / -11.2 / -0.7 |
| BLK_ENT | L3M | 33/80 | +12.1 | +5.7 / +12.1 | 0.15 | +1217 | -749 | +8173 | +5554 | +14.9 / +12.1 / +7.7 |
| BLK_ENT | L6M | 112/229 | +12.1 | +6.2 / +12.1 | 0.25 | -949 | -1935 | +1894 | +2696 | +11.9 / +12.1 / +7.7 |
| BLK_ENT | HOLD | 192/362 | -5.1 | -4.8 / +2.8 | 0.50 | -1438 | -2110 | +2408 | +4713 | -11.1 / +5.6 / -7.3 |
| BLK_ENT | PRE | 64/120 | +3.5 | +3.2 / +10.5 | 0.50 | -1609 | -1270 | +0 | +0 | +8.3 / -2.2 / +1.7 |
| BLK_ENT | X' | 15/32 | +0.0 | -0.7 / +0.0 | 0.20 | -1 | -84 | -2247 | +0 | -0.7 / -11.2 / -11.2 |
| BLK_M30 | L3M | 25/80 | +16.9 | +6.7 / +10.2 | 0.05 | +1628 | +535 | +12813 | +5554 | +16.9 / +16.9 / +16.9 |
| BLK_M30 | L6M | 68/229 | +16.9 | +6.7 / +10.2 | 0.00 | +1312 | -647 | +11896 | +5554 | +16.9 / +16.9 / +16.9 |
| BLK_M30 | HOLD | 104/362 | -3.5 | -10.3 / +6.9 | 0.40 | +543 | -947 | +3065 | +3270 | -3.5 / -3.5 / -3.5 |
| BLK_M30 | PRE | 43/120 | +7.2 | +2.0 / +10.5 | 0.35 | -697 | -860 | +0 | +0 | +7.2 / +7.2 / +7.2 |
| BLK_M30 | X' | 8/32 | -5.2 | -0.7 / +0.0 | 1.00 | -80 | -55 | +976 | +0 | -5.2 / -5.2 / -5.2 |
| BLK_M60 | L3M | 41/80 | +8.2 | +6.7 / +12.1 | 0.45 | -136 | -987 | +5842 | +5554 | +8.2 / +8.2 / +8.2 |
| BLK_M60 | L6M | 107/229 | +8.2 | +6.2 / +12.1 | 0.35 | -155 | -1940 | -891 | +2792 | +8.2 / +8.2 / +8.2 |
| BLK_M60 | HOLD | 171/362 | -11.0 | -6.7 / +3.3 | 0.55 | -828 | -1789 | +5734 | +4853 | -11.0 / -11.0 / -11.0 |
| BLK_M60 | PRE | 60/120 | +7.2 | +2.0 / +10.5 | 0.35 | -850 | -1112 | +0 | +0 | +7.2 / +7.2 / +7.2 |
| BLK_M60 | X' | 16/32 | -11.2 | -0.7 / +0.0 | 1.00 | -129 | -91 | -2247 | +0 | -11.2 / -11.2 / -11.2 |
| BLK_M120 | L3M | 52/80 | +10.1 | +10.0 / +12.1 | 0.35 | +1831 | +165 | +5842 | +5842 | +10.1 / +10.1 / +10.1 |
| BLK_M120 | L6M | 142/229 | +10.1 | +10.1 / +12.1 | 0.40 | -1104 | -2203 | +130 | +5175 | +10.1 / +10.1 / +10.1 |
| BLK_M120 | HOLD | 228/362 | -6.3 | -5.0 / +2.8 | 0.55 | -1688 | -2346 | -2043 | +1923 | -6.3 / -6.3 / -6.3 |
| BLK_M120 | PRE | 74/120 | +7.2 | +6.2 / +12.6 | 0.50 | -1064 | -1369 | +0 | +0 | +7.2 / +7.2 / +7.2 |
| BLK_M120 | X' | 20/32 | -11.2 | -5.2 / -0.7 | 1.00 | -149 | -144 | -2247 | -2247 | -11.2 / -11.2 / -11.2 |
| BLK_OPP | L3M | 65/80 | +10.1 | +0.9 / +12.1 | 0.15 | +349 | +1140 | +5842 | +2245 | +10.1 / +10.1 / +10.1 |
| BLK_OPP | L6M | 176/229 | +10.1 | +0.9 / +12.1 | 0.20 | -2297 | -3370 | +2774 | +2245 | +10.1 / +10.1 / +10.1 |
| BLK_OPP | HOLD | 273/362 | -9.8 | -8.7 / -2.4 | 0.75 | -1723 | -2828 | +8343 | +2825 | -9.8 / -9.8 / -9.8 |
| BLK_OPP | PRE | 93/120 | +10.0 | +7.9 / +12.6 | 0.30 | -1794 | -1435 | +0 | +0 | +10.0 / +10.0 / +10.0 |
| BLK_OPP | X' | 25/32 | -11.2 | -11.2 / -0.7 | 1.00 | -187 | -176 | -2247 | -2247 | -11.2 / -11.2 / -11.2 |
| BLK_HL | L3M | 36/80 | +16.5 | +6.2 / +12.1 | 0.00 | +631 | -932 | +4680 | +5554 | +8.0 / +16.9 / +16.9 |
| BLK_HL | L6M | 123/229 | +16.5 | +6.7 / +12.1 | 0.00 | -1304 | -2252 | +4680 | +4173 | +8.0 / +16.9 / +16.9 |
| BLK_HL | HOLD | 185/362 | -18.7 | -4.8 / +2.8 | 0.80 | -1478 | -1855 | -7157 | +4853 | -8.3 / -2.3 / -2.3 |
| BLK_HL | PRE | 66/120 | +2.9 | +3.2 / +10.5 | 0.50 | -1706 | -1214 | +0 | +0 | +4.8 / +1.7 / +1.7 |
| BLK_HL | X' | 16/32 | +0.0 | -0.7 / +0.0 | 0.15 | -136 | -91 | -4800 | +0 | -0.7 / -11.2 / -11.2 |

## 2c. Biweekly walk-forward (first order): every 2 weeks pick the rule with the shallowest trailing-26-week maxDD whose trailing mean is within 3% of REF, apply to the next 2 weeks

| start | WF maxDD | REF maxDD | WF $/day | REF $/day | picks |
|---|---|---|---|---|---|
| 2024-01-01 | -92243 | -92243 | 2661 | 2741 | {'REF': 27, 'CAP2': 19, 'BLK_M30': 12, 'BLK_M60': 8, 'CAP3': 7, 'BLK_HL': 1} |
| 2025-07-01 | -89683 | -92044 | 3373 | 3396 | {'CAP2': 12, 'REF': 8, 'CAP3': 7, 'BLK_M60': 7, 'BLK_HL': 1} |
| 2026-05-01 | -52233 | -52233 | 4987 | 5044 | {'BLK_M60': 7, 'REF': 5, 'BLK_HL': 2} |
| 2026-08-01 | -41109 | -52233 | 4162 | 3869 | {'BLK_HL': 3, 'REF': 2, 'BLK_M60': 1, 'BLK_M30': 1} |


## 3c. Tolerant vs strict gate, side by side
| cell | tolerant gate L3M+L6M | tolerant gate L3M..PRE | strict gate L3M..PRE (every window: DD cut >= 0, d$ >= 0, d worst wk >= 0) | verdict |
|---|---|---|---|---|
| BLK_ENT | False | False | False |  |
| BLK_M30 | True | False | False | recent-only (older window fails) |
| HALF | True | True | False | holds recent+older, tolerant |
| RCAP15 | False | False | False |  |
| XB_K7 | True | False | False | recent-only (older window fails) |
| XB_ALLBK | True | False | False | recent-only (older window fails) |
| XG_N15 | True | False | False | recent-only (older window fails) |
| XG_N45 | True | False | False | recent-only (older window fails) |
| XM_W15 | True | False | False | recent-only (older window fails) |
| XG_ANYBLK | True | False | False | recent-only (older window fails) |
| XF_CARRY | True | False | False | recent-only (older window fails) |
| XF_CARRY_ALL | True | False | False | recent-only (older window fails) |
| XF_P7_ALLSESS | True | False | False | recent-only (older window fails) |

## 4. Commentary (trader view, costs on trend nights, hand-off)
Measurement reading (first page, before the exact cells):
- The premise "P7 Asia keeps re-entering the failed side and loses" is true only in the most recent window. Over 43 months the same-side-after-loser class has mean +380 per trade (median -1,888, i.e. a few big winners carry it), is positive in PRE (+1,643 $/wk), HOLD (+992), L6M (+492), X' (+141) and negative in L3M (-967) and GAP (-1,210, 5 trades). The class that makes the most money after a loser is the OPPOSITE side (+4,521 $/wk L3M, 4,306 L6M, 3,551 HOLD) - D7 reversing is fine; D7 repeating is mixed.
- 295 of the 304 priors were StateCut exits (small controlled losses), not full stops. A StateCut loser is not a "failed idea" in the discretionary sense (the cut is a risk rule, price often resumes), which is why re-entry has paid historically. After a full stop the same-side count is only 6 (net +9.3k) - too few to judge.
- The existing governor (skip after 2 same-side losers with no new extreme) already removes the 3rd+ same-side attempts; same-side losers-before=3 gives only +2k and =4 one trade -2.8k.
- Where it hurts: W44 (-15.7k), 2026-03-23 week (-10.5k), 2026-02-02 week (-5.7k), 2025-07-07 (-4.7k); in 5 stack-worst weeks it carries -18.7k of -274k over 43 months (7%), -27.5k of -43.1k in L3M (64%), -20.3k of -93.5k in L6M (22%), +9.2k in PRE (it HELPS) and +2.2k in X'. So the recent worst weeks are different from the older ones: that is the "must hold in both windows" test the rule has to pass.
- What a block costs on trend nights: the 12 best same-side sessions are in section M7; a block would remove them (Asia trend nights re-entered after a cut are where the class earns).

Exact L3M reading (update 1):
- Rules that block the same side until a new session extreme (EXT), an opposite signal (OPP), or 120 minutes (M120) are WORSE than the base in L3M in the exact engine (d$ -4.3k / -2.5k / -2.1k per week, DD cut -13.7 / -9.4 / -14.3%). That is the trader-view problem: on a trend night the first cut-out is followed by the same side again (e.g. the 20260928 night, SSSSSS, where the 2 same-side-after-loser entries made +12.0k), and a "wait for a new extreme" rule waits until the move has already happened.
- BLK_M30 (30 min) and HALF (re-enter at half size) are the only ones with nothing lost in L3M (d$ +1.2k / +1.4k, best-5 weeks kept 1.00 / 1.06, no winning week turned losing); BLK_M30 cuts the worst week by 10.2k (W44), HALF changes DD +0.9% only. With W44 removed from both, BLK_M30 is neutral (DD cut 0.0, +385 $/wk) and HALF is -15.5% DD / +1.2k, i.e. the L3M drawdown benefit is the single week.
- Session caps: CAP3 cuts L3M DD 21.1% (worst week +10.7k) but loses 3.5k $/wk and keeps only 0.77 of the five best weeks (trend nights); CAP4 +12.5% DD / -1.5k, CAP2 -13.3% DD / -2.5k. A cap is the opposite of what a discretionary trader does on a trend night.
- Stop for the night after a full stop (SN): changes 4 trades in 13 weeks, +211 $/wk, no DD effect.

Update 2 (placebos and older windows so far):
- BLK_M30 vs 3 random same-count block placebos (PLA_M30_s1..3, p=0.31): placebos d$ -1,183 / -527 / -19 (L3M) and -410 / -1,001 / -1,367 (L6M), DD cut -0.4 / -0.4 / -0.5 %; real +1,210 / +1,428 and +16.9 %. The timing (30 min after the loser) matters, a random block does not do it.
- Shifted-evidence placebo of BLK_ENT (price path 11 / 23 days earlier): d$ -3,969 / +1,780 (L3M), DD cut +1.1 / +7.7 %: the real BLK_ENT (+727, 6.4%, L6M -2,023) is inside the placebo spread - no evidence value.
- RCAP15 (stop P7 Asia for the night once the session is -1.5R): L3M DD cut 16.2% but d$ -149, L6M -756, HOLD -365 with DD cut -3.6% and a winning week turned losing: fails HOLD.
- M30HALF (30 min block plus half size): no better than M30 alone.
- A 30-minute same-side cooldown is what a discretionary trader does after a stop-out (wait for the next setup, do not re-fire at once); it is not "never re-enter the failed idea", and 295 of 304 priors are small StateCut losses, so it is a pacing rule. Whether it holds in HOLD/PRE/X'/GAP is still open; the remaining cells TL3_PR_BLK_M30 (202603, then PRE, GAP, X') are queued.
- Hand-off to W-JV: candidate rule = pr_hooks par {"blk":{"ev":"min","N":30}} (set TL3_PR_BLK_M30), P7 Asia only; flag it as recent-only/unproven until HOLD+PRE land.

Update 3 (full windows, cluster-robust):
- Regression: RG30 (v2 hook) equals BLK_M30 to the cent on L3M (+1,210.0, DD +16.9%); XG_N60 equals BLK_M60; XF_CARRY equals BLK_M30 (carry across sessions changes nothing for Asia-only arming).
- BLK_M30: weekly paired t 1.1 (L3M), 1.0 (L6M), 0.7 (HOLD), -1.1 (PRE), 0.6 (X'); only 9 / 21 / 37 / 19 weeks differ from the base. Nothing here is distinguishable from zero at the week-cluster level, and the older windows do not confirm it (PRE -783 $/wk). The M30 placebos (random same-count blocks) are negative everywhere (-19 to -1,367 $/wk in L3M/L6M), so the timing is not random noise, but with W44 removed the DD gain disappears.
- Other books: only K7 reacts (XB_K7 L3M +843, L6M +1,181, t 2.0 in L6M, HOLD +620, PRE -9, X' +114); U7, M7, H7 have no trades changed (U7 already has the live post-cut blackout), A7 -16. All six books together: L6M +2,812 (t 1.8, ex-W44 +2,041), HOLD +1,234 (DD cut 8.6%), PRE -919, X' +175: the closest thing to a recent lead, fails PRE on mean (-7.7%).
- Grid: 15 min L6M +619, 45 min +484, 60 min +1,366 (L3M only), 90 min -1,480: 30 min is the peak, the neighbours are weaker (sharp, not a plateau) - a sign of fitting.
- Mirror (more size after a same-side winner): M30 + 1.5x within 15 min of a winner: L3M +1,398, L6M +1,888 (t 1.5), HOLD +630, PRE -655; 1.5x alone within 30 min L3M +1,653 but DD -12%. Block after a winner (reverse) -2,337; block after any trade ~0.
- Other sessions (P7 alone or all books): London -236 / -1,364, NY AM +275 / +148, NY PM 0 / -97 in L3M: no session other than Asia gives anything; none promoted.
- Trader reading: a 30-minute pause after being stopped on a side is ordinary; it does nothing measurable that survives the older windows. The price of "never re-enter the same failed idea" is therefore not paid back: the 2nd+ same-side entry after a loser is +115k over 43 months.
- Auto-expansion: BLK_M30 battery fully run (26 cells); next cells running: XB_ALL_N15, XB_ALL_N45, PLA_ALL_s1-3 (random all-book blocks) on L3M..PRE.

PLACEBO VALIDITY (asked by W-JV/lead 2026-11-16): the random draw of the old TL3_PR_PLA_* placebos (PLA_M30_s1-3, and PLA_ALL_s1-3 as queued before the fix) was taken from the signal SECOND (hash of epoch second), i.e. REDRAWN EVERY SECOND while a signal is live: INVALID, a blocked signal re-enters one second later. Measured block rate from finished runs (P7 Asia trades removed vs the base): target p=0.31 of eligible entries (about 40 of 128 in L6M, 63 of 203 in HOLD, 16 of 53 in L3M); actual removed 11-12 in L6M (~9%), 18-22 in HOLD (~10%), 0-1 in L3M (~2%), versus BLK_M30 itself 21 / 34 / -1. So these placebos blocked about a third of what they were meant to: they are WEAK controls and the earlier statement "BLK_M30 beats its random placebos" is withdrawn. Fixed in pr_hooks.py (one draw per loser event, seeded by the loser's exit time and side; block then lasts 30 min); fixed cells TL3_PR_PLB_M30_s1-3 and the queued PLA_ALL_* (they start with the fixed code) will replace them; the shifted-evidence placebos (ENT_SH*) are unaffected (no random draw).


## 5. Status
driver: 1794787469 epoch chains 25 ident TL3_PR_ID 202610 (hook module loaded, empty par): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL outstanding 73; cells with complete windows: {"BLK_EXT": 1, "BLK_ENT": 1, "BLK_OPP": 1, "BLK_HL": 1, "BLK_M30": 1, "BLK_M60": 1, "BLK_M120": 1, "HALF": 1, "CAP2": 1, "CAP3": 1, "CAP4": 1, "RCAP10": 1, "RCAP15": 1, "RCAP20": 1, "SN": 1, "XB_K7": 1, "XB_U7": 1, "XB_M7": 1, "XB_A7": 1, "XB_H7": 1, "XB_ALLBK": 1, "XS_P7_LON": 1, "XS_ALL_LON": 1, "XS_P7_NYAM": 1, "XS_ALL_NYAM": 1, "XS_P7_NYPM": 1, "XS_ALL_NYPM": 1, "XG_N15": 1, "XG_N45": 1, "XG_N60": 1, "XG_N90": 1, "XM_W15": 1, "XM_ONLY15": 1, "XM_ONLY30": 1, "XG_WINBLK": 1, "XG_ANYBLK": 1, "XF_CARRY": 1, "XF_CARRY_ALL": 1, "XF_P7_ALLSESS": 1}
