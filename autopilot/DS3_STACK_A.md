# DS3_STACK_A - slot rules on the live stack (D3SKA, T-STACK section A, 2026-10-28)
Research only. Prereg l2vast/ds3/prereg/D3SKA_prereg.md sha256 ffc0d180053e1428541fe4241b2b5edf49b03efd2fb2975f7eae9060945a53dd (10 cells; F for this section 10, program F_total 60). Pre-holdout text autopilot/DS3_STACK_A_PREHOLD.md (looks logged: STKA, STKA_SPAN2). Windows capped at label day 2026-02-06 (UNTOUCHED not read). Code l2vast/ds3/code/stk_a/, outputs l2vast/ds3/out/stk_a/.

## Plain line
**Blocking or halving the half-hour slots that were negative on PRE does not carry out of sample: 0 CONFIRMED, 0 LEAD, 9 DEAD rule cells (+ the reverse control A10, which loses as predicted). The PRE-negative slots do not stay negative: of the 14 pooled loose slots only 5 are negative in HOLD (binomial p 0.91 under a coin-flip null; 3 of 14 in the 2023 span, p 0.99), PRE-vs-HOLD Spearman of slot weekly means +0.06 (vs the 2023 span -0.34), and the $ those 14 slots would have removed flip from -$18.5k/wk (PRE) to +$11.7k/wk in HOLD and +$17.2k/wk in 2023, so blocking them costs money out of sample (A02 HOLD LM -6,042/wk, 2023 span -19,542/wk). The range-day gate makes it worse (A07-A09 negative on PRE already). The only cell with a clean HOLD CI above zero is A03 (block WT only at 05:00 and 22:00 ET, the only strict-significant slots): HOLD LM +4,231/wk [+746,+8,016], WF +2,682, FULL +1,687/wk, but it is 1% of entries, below the FULL MDE (2,140) on the WF scale, negative in the 2023 span (-748) and it fails G3/G4/G6 and best-of-F.**

## Verdicts (gates: D3DVG definitions, LM basis; FTOT=60 for best-of-F)
| cell | what | tier | failed gates | HOLD p(<=0) | best-of-F (<=0.05/60) |
|---|---|---|---|---|---|
| A01_blk_strict_pool | block  pooled strict (05:00) | DEAD | G1, G2, G3, G4, G5, G6, G7 | 0.282 | no |
| A02_blk_loose_pool | block  pooled loose (14 slots) | DEAD | G1, G2, G3, G4, G5, G6, G7 | 0.681 | no |
| A03_blk_strict_book | block  per-book strict (WT) | DEAD | G3, G4, G6 | 0.008 | no |
| A04_blk_loose_book | block  per-book loose | DEAD | G1, G2, G3, G4, G5, G6 | 0.636 | no |
| A05_half_loose_pool | halve  pooled loose (14 slots) | DEAD | G2, G3, G4, G5, G6 | 0.141 | no |
| A06_half_loose_book | halve  per-book loose | DEAD | G2, G3, G4, G5, G6 | 0.465 | no |
| A07_blk_loose_pool_rng | block range-gated pooled loose (14 slots) | DEAD | G1, G2, G3, G4, G5, G6, G7, G8 | 0.555 | no |
| A08_blk_loose_book_rng | block range-gated per-book loose | DEAD | G1, G2, G3, G4, G5, G6, G7 | 0.127 | no |
| A09_half_loose_pool_rng | halve range-gated pooled loose (14 slots) | DEAD | G1, G2, G3, G4, G5, G6, G7, G8 | 0.455 | no |
| A10_ctl_blk_top14_pool | block  top-14 best slots (control) | CONTROL | G1, G2, G3, G5, G6, G7, G8 | 0.946 | no |

G4 (random-slot placebo rank >= 0.95 on PRE and HOLD, and above both shifted draws) is None-safe; PRE G4 is in-sample by construction (slots were chosen on PRE), the HOLD / 2023-span ranks are the informative ones.

## Slot lists (PRE only, 2024-02..2025-06, 75 weeks; ET clock slot of the entry bar)
Strict = weekly mean < 0 with 95% t-upper bound < 0; loose = weekly mean < 0 and >= 30 PRE trades. 1 of 41 active pooled slots is strict-significant; expected false positives at 5% two-sided one-tail: about 1-2.

| set | strict | loose |
|---|---|---|
| ALL | 05:00 | 00:00, 00:30, 01:00, 03:30, 04:30, 05:00, 05:30, 12:30, 13:00, 14:30, 22:00, 22:30, 23:00, 23:30 |
| ST | - | 03:30, 04:30, 05:00, 11:30, 12:30, 14:00, 14:30, 19:00 |
| HM | - | 04:00, 05:30, 08:30, 10:30, 12:30, 13:00, 14:00, 18:30 |
| WT | 05:00, 22:00 | 01:00, 01:30, 03:30, 04:30, 05:00, 07:00, 08:00, 10:30, 12:30, 13:00, 13:30, 14:30, 19:30, 21:00, 22:00, 23:00, 23:30 |
| KB | - | 03:30, 04:00, 04:30, 05:00, 05:30, 14:30, 19:00, 19:30, 20:30, 21:00 |
| SM | - | 02:00, 08:30 |
| PE | - | 03:30, 05:00, 08:30 |

## Stability table: PRE-negative slots that stay negative in HOLD / in the 2023 span (X)
k = slots of the list with a negative weekly mean in the window; binomial null: P(>=k of n negative) with p0 = 0.5 and with p0 = share of PRE-eligible (n>=30) slots that are negative in that window. Spearman = PRE vs window weekly slot means over eligible slots.

| set (list) | n | HOLD k neg | p(0.5) | p(base) | PRE $/wk of list | HOLD $/wk of list | X k neg | p(0.5) | p(base) | X $/wk of list | Spearman HOLD / X |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL loose | 14 | 5 | 0.910 | 0.652 | -18,490 | +11,652 | 3 | 0.994 | 0.882 | +17,220 | 0.06 / -0.34 |
| ALL strict | 1 | 0 | 1.000 | 1.000 | -3,617 | +4,208 | 0 | 1.000 | 1.000 | +2,051 | 0.06 / -0.34 |
| ST loose | 8 | 1 | 0.996 | 0.967 | -6,296 | +9,469 | 3 | 0.855 | 0.799 | +4,669 | -0.29 / -0.23 |
| HM loose | 8 | 3 | 0.855 | 0.753 | -5,031 | +2,325 | 5 | 0.363 | 0.412 | -1,810 | 0.08 / -0.21 |
| WT loose | 17 | 10 | 0.315 | 0.483 | -7,810 | +3,639 | 6 | 0.928 | 0.848 | +4,578 | -0.06 / -0.23 |
| WT strict | 2 | 2 | 0.250 | 0.305 | -1,963 | -495 | 1 | 0.750 | 0.695 | +389 | -0.06 / -0.23 |
| KB loose | 10 | 3 | 0.945 | 0.930 | -2,416 | +4,262 | 5 | 0.623 | 0.470 | +1,744 | -0.35 / -0.03 |
| SM loose | 2 | 1 | 0.750 | 0.750 | -397 | -104 | 0 | 1.000 | 1.000 | +1,763 | NA / NA |
| PE loose | 3 | 2 | 0.500 | 0.191 | -1,801 | -1,145 | 0 | 1.000 | 1.000 | +1,339 | 0.32 / -0.09 |

Pooled loose slots one by one (weekly $; negative = loses):

| slot | PRE | HOLD | X (2023-04..2024-01) |
|---|---|---|---|
| 00:00 | -876 | +1,668 | +1,111 |
| 00:30 | -817 | +3,842 | +865 |
| 01:00 | -1,009 | +1,076 | +647 |
| 03:30 | -2,367 | -6,035 | +1,820 |
| 04:30 | -2,215 | +2,360 | +5,784 |
| 05:00 | -3,617 | +4,208 | +2,051 |
| 05:30 | -1,328 | -507 | -478 |
| 12:30 | -70 | +3,528 | +288 |
| 13:00 | -242 | -3,144 | +2,829 |
| 14:30 | -1,470 | -1,854 | +79 |
| 22:00 | -2,807 | +4,351 | +2,257 |
| 22:30 | -894 | +923 | +460 |
| 23:00 | -129 | +3,678 | -441 |
| 23:30 | -649 | -2,441 | -52 |

WT strict slots: 05:00 PRE -1,053 / HOLD -306 / X +442; 22:00 PRE -910 / HOLD -189 / X -53 (weekly $; the only two slots negative in HOLD, both small).

## Cell results (paired by week vs the unchanged stack; LM = lot-matched on PRE exposure, MM = mean-matched; delta = cell - base per week; CI = iid bootstrap 95%; MDE = 2.8 x SD(delta)/sqrt(n))
Base stack weekly mean / SD / maxDD / worst: WFPRE: 44,127 / 131,184 / 477,701 / -306,664 (75 wk) ; HOLD: 52,448 / 151,891 / 601,016 / -318,557 (32 wk) ; X: 20,616 / 112,784 / 553,090 / -157,300 (44 wk) ; WF: 47,055 / 138,124 / 601,016 / -318,557 (106 wk) ; FULL: 39,564 / 131,851 / 601,016 / -318,557 (149 wk)


### PRE 2024-02..2025-06 (selection window: in-sample)
| cell | entries affected | raw d_mean | LM d_mean [CI] | MDE | d_SD | d_maxDD | d_worst wk | MM d_mean | rand-slot rank | shifted +-30 min d_mean (2 draws) |
|---|---|---|---|---|---|---|---|---|---|---|
| A01_blk_strict_pool | 1.7% | -203 | -49 [-4,285,+4,127] | 5,962 | +1,229 | -59,036 | +27,242 | -0 | 0.50 | 2274.0, 2103.0 |
| A02_blk_loose_pool | 25.0% | +2,760 | +8,112 [-6,663,+22,837] | 21,509 | +4,061 | +52,563 | +76,173 | +0 | 0.98 | -10021.0, 444.0 |
| A03_blk_strict_book | 0.9% | +1,898 | +1,985 [-76,+4,217] | 3,135 | +912 | +5,389 | -580 | -0 | 0.91 | 78.0, -550.0 |
| A04_blk_loose_book | 24.1% | +12,473 | +16,351 [+2,898,+30,252] | 19,850 | -11,015 | -66,597 | +125,420 | +0 | 1.00 | -1346.0, -16377.0 |
| A05_half_loose_pool | 25.0% | +6,078 | +9,955 [-535,+20,551] | 15,366 | +1,852 | -38,476 | +39,628 | -0 | 0.99 | 4085.0, 9600.0 |
| A06_half_loose_book | 24.1% | +10,093 | +14,531 [+6,199,+23,073] | 12,059 | +337 | -24,956 | +51,756 | +0 | 1.00 | 4182.0, -4489.0 |
| A07_blk_loose_pool_rng | 3.2% | -3,385 | -2,670 [-8,636,+3,373] | 8,743 | +697 | +80,267 | -5,383 | -0 | 0.63 | 677.0, -2184.0 |
| A08_blk_loose_book_rng | 3.7% | -4,343 | -3,731 [-10,176,+2,051] | 8,815 | -2,054 | +22,632 | -4,715 | +0 | 0.37 | 1447.0, -360.0 |
| A09_half_loose_pool_rng | 3.2% | -3,037 | -2,530 [-7,473,+1,474] | 6,539 | -1,406 | -25,078 | -3,783 | -0 | 0.38 | -726.0, 64.0 |
| A10_ctl_blk_top14_pool | 47.2% | -51,960 | -53,649 [-78,401,-28,648] | 35,801 | +16,369 | +1,130,981 | -99,996 | NA | - | - |

### HOLD 2025-07..2026-02-06 (one logged look)
| cell | entries affected | raw d_mean | LM d_mean [CI] | MDE | d_SD | d_maxDD | d_worst wk | MM d_mean | rand-slot rank | shifted +-30 min d_mean (2 draws) |
|---|---|---|---|---|---|---|---|---|---|---|
| A01_blk_strict_pool | 1.9% | +1,232 | +1,420 [-3,973,+6,439] | 7,635 | +106 | -15,125 | -1,115 | +1,480 | 0.62 | 2788.0, 2758.0 |
| A02_blk_loose_pool | 25.8% | -10,796 | -6,042 [-31,178,+17,962] | 35,746 | -12,540 | -52,338 | -78,540 | -13,248 | 0.34 | -21863.0, -11188.0 |
| A03_blk_strict_book | 1.0% | +4,124 | +4,231 [+746,+8,016] | 5,414 | +57 | +1,138 | -603 | +1,792 | 0.98 | 50.0, 2207.0 |
| A04_blk_loose_book | 23.2% | -6,038 | -2,859 [-18,980,+13,627] | 24,007 | -5,178 | +42,917 | -47,280 | -16,266 | 0.28 | -3707.0, 454.0 |
| A05_half_loose_pool | 25.8% | +3,918 | +8,270 [-7,348,+22,527] | 21,785 | -1,694 | +20,831 | -37,379 | -2,906 | 0.70 | 2437.0, 3759.0 |
| A06_half_loose_book | 23.2% | -3,691 | +300 [-9,941,+10,136] | 14,845 | +1,391 | +37,358 | -30,916 | -12,767 | 0.19 | -1077.0, 14640.0 |
| A07_blk_loose_pool_rng | 4.4% | -1,775 | -886 [-12,686,+10,292] | 16,609 | -5,975 | +43,486 | -38,528 | +2,435 | 0.67 | -1531.0, -3189.0 |
| A08_blk_loose_book_rng | 4.1% | +3,908 | +4,774 [-2,953,+13,289] | 11,949 | +3,452 | +31,481 | -27,138 | +10,059 | 0.95 | 830.0, 1489.0 |
| A09_half_loose_pool_rng | 4.4% | -286 | +358 [-6,039,+6,446] | 9,069 | -6,549 | +18,619 | -15,135 | +3,569 | 0.86 | 695.0, -3693.0 |
| A10_ctl_blk_top14_pool | 47.8% | -36,084 | -32,556 [-71,304,+7,907] | 57,879 | -7,273 | -92,711 | +38,943 | NA | - | - |

### Second holdout / 2023 span 2023-04..2024-01
| cell | entries affected | raw d_mean | LM d_mean [CI] | MDE | d_SD | d_maxDD | d_worst wk | MM d_mean | rand-slot rank | shifted +-30 min d_mean (2 draws) |
|---|---|---|---|---|---|---|---|---|---|---|
| A01_blk_strict_pool | 1.7% | -739 | -670 [-3,785,+2,693] | 4,596 | -1,798 | -15,511 | -7,631 | -648 | 0.51 | 383.0, -1713.0 |
| A02_blk_loose_pool | 21.2% | -19,652 | -19,542 [-34,267,-4,776] | 21,174 | -7,747 | +154,478 | -47,814 | -19,709 | 0.19 | -4006.0, -5868.0 |
| A03_blk_strict_book | 0.9% | -786 | -748 [-2,650,+1,101] | 2,683 | -691 | -4,274 | -7,079 | -1,604 | 0.26 | -1470.0, -178.0 |
| A04_blk_loose_book | 24.1% | -6,164 | -5,174 [-19,242,+9,630] | 20,842 | -5,331 | +51,859 | -66,902 | -9,349 | 0.51 | -10850.0, -9123.0 |
| A05_half_loose_pool | 21.2% | -11,798 | -11,117 [-20,691,-1,815] | 13,606 | -5,928 | +46,908 | -2,490 | -12,865 | 0.12 | -2110.0, -8580.0 |
| A06_half_loose_book | 24.1% | -9,481 | -8,570 [-16,687,-382] | 11,801 | -2,692 | +75,410 | -57,555 | -11,554 | 0.08 | -7824.0, -2264.0 |
| A07_blk_loose_pool_rng | 3.2% | -1,287 | -947 [-6,906,+4,410] | 8,103 | +3,542 | -79,922 | -25,778 | +319 | 0.60 | 2516.0, 4297.0 |
| A08_blk_loose_book_rng | 4.2% | +43 | +361 [-5,025,+6,041] | 7,971 | +3,400 | +2,522 | -45,496 | +2,298 | 0.64 | 1526.0, 877.0 |
| A09_half_loose_pool_rng | 3.2% | -1,128 | -888 [-4,111,+2,336] | 4,598 | -210 | -54,435 | -5,532 | +312 | 0.76 | 1690.0, 659.0 |
| A10_ctl_blk_top14_pool | 53.8% | -10,485 | -8,300 [-37,786,+21,638] | 42,968 | +13,974 | +78,378 | -53,051 | NA | - | - |

### WF 2024-02..2026-02-06
| cell | entries affected | raw d_mean | LM d_mean [CI] | MDE | d_SD | d_maxDD | d_worst wk | MM d_mean | rand-slot rank | shifted +-30 min d_mean (2 draws) |
|---|---|---|---|---|---|---|---|---|---|---|
| A01_blk_strict_pool | 1.8% | +229 | +394 [-3,018,+3,618] | 4,791 | +895 | -15,125 | -1,115 | +447 | 0.63 | 2450.0, 2321.0 |
| A02_blk_loose_pool | 25.3% | -1,306 | +3,916 [-9,297,+16,730] | 18,643 | -1,163 | -52,338 | -78,540 | -3,999 | 0.92 | -13690.0, -3063.0 |
| A03_blk_strict_book | 0.9% | +2,588 | +2,682 [+780,+4,643] | 2,755 | +672 | +1,138 | -603 | +541 | 0.99 | 70.0, 277.0 |
| A04_blk_loose_book | 23.8% | +7,003 | +10,706 [-456,+22,011] | 15,925 | -9,065 | +42,917 | -47,280 | -4,910 | 1.00 | -2072.0, -11450.0 |
| A05_half_loose_pool | 25.3% | +5,483 | +9,540 [+555,+18,201] | 12,643 | +394 | +20,831 | -37,379 | -877 | 0.99 | 3626.0, 7927.0 |
| A06_half_loose_book | 23.8% | +6,027 | +10,372 [+3,695,+17,146] | 9,751 | +349 | +37,358 | -30,916 | -3,854 | 1.00 | 2634.0, 1243.0 |
| A07_blk_loose_pool_rng | 3.5% | -2,931 | -2,156 [-7,694,+3,362] | 7,925 | -1,498 | +43,486 | -38,528 | +735 | 0.67 | 17.0, -2508.0 |
| A08_blk_loose_book_rng | 3.8% | -1,893 | -1,199 [-6,465,+3,609] | 7,242 | -80 | +31,481 | -27,138 | +3,037 | 0.71 | 1275.0, 195.0 |
| A09_half_loose_pool_rng | 3.5% | -2,235 | -1,682 [-5,737,+1,817] | 5,366 | -3,039 | +18,619 | -15,135 | +1,077 | 0.61 | -304.0, -1069.0 |
| A10_ctl_blk_top14_pool | 47.4% | -47,657 | -47,787 [-69,132,-25,982] | 30,906 | +8,791 | +1,007,667 | -88,102 | NA | - | - |

### FULL 2023-04..2026-02-06
| cell | entries affected | raw d_mean | LM d_mean [CI] | MDE | d_SD | d_maxDD | d_worst wk | MM d_mean | rand-slot rank | shifted +-30 min d_mean (2 draws) |
|---|---|---|---|---|---|---|---|---|---|---|
| A01_blk_strict_pool | 1.8% | -56 | +83 [-2,534,+2,627] | 3,662 | +254 | -15,125 | -1,115 | +127 | 0.64 | 1856.0, 1145.0 |
| A02_blk_loose_pool | 24.5% | -6,733 | -2,985 [-13,326,+7,463] | 14,737 | -1,521 | +106,553 | -78,540 | -8,665 | 0.78 | -10922.0, -3912.0 |
| A03_blk_strict_book | 0.9% | +1,609 | +1,687 [+221,+3,180] | 2,140 | +479 | +1,138 | -603 | -89 | 0.99 | -384.0, 145.0 |
| A04_blk_loose_book | 23.9% | +3,161 | +6,089 [-2,733,+15,310] | 12,994 | -7,240 | +42,917 | -47,280 | -6,254 | 1.00 | -4678.0, -10840.0 |
| A05_half_loose_pool | 24.5% | +417 | +3,504 [-3,591,+10,656] | 10,034 | +55 | +20,831 | -37,379 | -4,423 | 0.98 | 1956.0, 3106.0 |
| A06_half_loose_book | 23.9% | +1,488 | +4,848 [-739,+10,523] | 7,994 | +657 | +37,358 | -30,916 | -6,154 | 0.99 | -437.0, 216.0 |
| A07_blk_loose_pool_rng | 3.5% | -2,465 | -1,814 [-6,082,+2,569] | 6,112 | -239 | +43,486 | -38,528 | +617 | 0.69 | 755.0, -515.0 |
| A08_blk_loose_book_rng | 3.9% | -1,334 | -746 [-4,818,+3,105] | 5,652 | +722 | +31,481 | -27,138 | +2,839 | 0.75 | 1357.0, 398.0 |
| A09_half_loose_pool_rng | 3.5% | -1,923 | -1,459 [-4,404,+1,243] | 4,044 | -2,312 | +18,619 | -15,135 | +859 | 0.71 | 283.0, -566.0 |
| A10_ctl_blk_top14_pool | 48.6% | -37,000 | -36,447 [-54,148,-18,242] | 25,841 | +9,964 | +1,007,667 | -88,102 | NA | - | - |

Placebo = 200 random slot sets of the same size (per book for per-book cells) + 2 shifted-by-one-slot copies; rank = share of random draws with a lower LM d_mean.

## Worst weeks and the trade-off line (delta = cell - base, summed)
W20-FULL = the 20 worst base weeks of 2023-04..2026-02-06 (fixed on all data, as in the audit but capped at 2026-02-06); 'in window' is how many of those weeks fall in the window. PRE-W20 = the 20 worst base weeks re-derived on PRE only. HOLD/X quartile = worst 25% of that window's own weeks. 'other wks' = per-week delta in the remaining weeks (negative = given up).

| cell | basis | FULL: base $ in W20 | saved in W20 (sum) | other 165 wks per wk | HOLD (4 W20 wks) saved | HOLD other wks per wk | PRE-W20 (PRE-derived) saved | PRE other wks per wk | HOLD worst-quartile saved | X worst-quartile saved |
|---|---|---|---|---|---|---|---|---|---|---|
| A01_blk_strict_pool | LM | -3,534,170 | -7,705 | +155 | -13,102 (4 wk) | +2,091 | +3,042 | -122 | -6,907 (8 wk) | +44,762 (11 wk) |
| A01_blk_strict_pool | raw | -3,534,170 | +4,652 | -100 | -9,865 (4 wk) | +1,760 | +11,072 | -478 | -2,763 (8 wk) | +49,366 (11 wk) |
| A02_blk_loose_pool | LM | -3,534,170 | +373,537 | -6,343 | +7,783 (4 wk) | -7,183 | +284,411 | +5,891 | +295,606 (8 wk) | +126,992 (11 wk) |
| A02_blk_loose_pool | raw | -3,534,170 | +697,365 | -13,182 | +100,729 (4 wk) | -15,936 | +491,413 | -5,171 | +386,308 (8 wk) | +253,776 (11 wk) |
| A03_blk_strict_book | LM | -3,534,170 | +68,722 | +1,416 | +3,106 (4 wk) | +4,725 | +93,689 | +1,003 | +24,821 (8 wk) | +4,761 (11 wk) |
| A03_blk_strict_book | raw | -3,534,170 | +75,269 | +1,275 | +4,828 (4 wk) | +4,541 | +97,866 | +808 | +27,005 (8 wk) | +7,330 (11 wk) |
| A04_blk_loose_book | LM | -3,534,170 | +763,035 | +1,118 | -12,994 (4 wk) | -2,803 | +1,138,222 | +1,602 | -41,153 (8 wk) | +157,332 (11 wk) |
| A04_blk_loose_book | raw | -3,534,170 | +940,721 | -3,641 | +46,506 (4 wk) | -8,562 | +1,213,023 | -5,046 | +37,205 (8 wk) | +234,732 (11 wk) |
| A05_half_loose_pool | LM | -3,534,170 | +327,157 | +1,512 | +15,904 (4 wk) | +8,884 | +251,831 | +8,996 | +123,744 (8 wk) | +36,173 (11 wk) |
| A05_half_loose_pool | raw | -3,534,170 | +557,042 | -3,836 | +80,349 (4 wk) | +1,608 | +398,991 | +1,034 | +199,522 (8 wk) | +131,385 (11 wk) |
| A06_half_loose_book | LM | -3,534,170 | +162,889 | +4,337 | -3,160 (4 wk) | +455 | +449,108 | +11,649 | -12,236 (8 wk) | -56,523 (11 wk) |
| A06_half_loose_book | raw | -3,534,170 | +417,938 | -1,521 | +66,299 (4 wk) | -6,586 | +589,497 | +3,045 | +78,027 (8 wk) | +50,977 (11 wk) |
| A07_blk_loose_pool_rng | LM | -3,534,170 | +39,902 | -2,404 | -978 (4 wk) | -977 | +36,584 | -4,306 | +111,133 (8 wk) | -22,237 (11 wk) |
| A07_blk_loose_pool_rng | raw | -3,534,170 | +100,185 | -3,624 | +14,823 (4 wk) | -2,558 | +75,714 | -5,993 | +129,588 (8 wk) | +1,685 (11 wk) |
| A08_blk_loose_book_rng | LM | -3,534,170 | +116,225 | -1,763 | -11,188 (4 wk) | +5,856 | +149,839 | -7,812 | +26,437 (8 wk) | +2,604 (11 wk) |
| A08_blk_loose_book_rng | raw | -3,534,170 | +167,976 | -2,843 | +2,834 (4 wk) | +4,365 | +182,467 | -9,240 | +43,916 (8 wk) | +23,223 (11 wk) |
| A09_half_loose_pool_rng | LM | -3,534,170 | +74,344 | -2,261 | +43,837 (4 wk) | -1,157 | +29,973 | -3,995 | +102,326 (8 wk) | -7,168 (11 wk) |
| A09_half_loose_pool_rng | raw | -3,534,170 | +116,500 | -3,124 | +54,451 (4 wk) | -2,271 | +57,690 | -5,190 | +115,467 (8 wk) | +9,544 (11 wk) |
| A10_ctl_blk_top14_pool | LM | -3,534,170 | +401,196 | -45,208 | +354,869 (4 wk) | -49,881 | +223,228 | -77,216 | +148,702 (8 wk) | +396,428 (11 wk) |
| A10_ctl_blk_top14_pool | raw | -3,534,170 | +956,894 | -50,154 | +454,211 (4 wk) | -57,461 | +592,438 | -81,626 | +331,780 (8 wk) | +568,124 (11 wk) |

## By year (LM, summed delta over the year's weeks; FULL window)
| cell | 2023 (Apr-Dec) | 2024 | 2025 | 2026 (to 02-06) | WF cost 2x d_mean/wk |
|---|---|---|---|---|---|
| A01_blk_strict_pool | -47,143 | +24,203 | +49,763 | -14,515 | +147 |
| A02_blk_loose_pool | -594,473 | +322,511 | -127,501 | -45,282 | +2,919 |
| A03_blk_strict_book | -53,003 | +108,069 | +169,637 | +26,621 | +1,849 |
| A04_blk_loose_book | -307,404 | +1,459,531 | -376,353 | +131,443 | +12,649 |
| A05_half_loose_pool | -253,466 | +469,575 | +212,781 | +93,255 | +5,394 |
| A06_half_loose_book | -334,296 | +759,493 | +287,618 | +9,493 | +9,862 |
| A07_blk_loose_pool_rng | -12,178 | -122,119 | -120,042 | -15,925 | -2,151 |
| A08_blk_loose_book_rng | -4,099 | -91,596 | -86,350 | +70,847 | +349 |
| A09_half_loose_pool_rng | +891 | -111,816 | -108,995 | +2,563 | -2,648 |
| A10_ctl_blk_top14_pool | -842,130 | -1,828,578 | -2,658,347 | -101,573 | -49,316 |

## Reading
- **No PRE-derived slot list persists.** The block cells A02/A04 and halves A05/A06 are big and significant in-sample (A04 PRE LM +16,351/wk, CI lower +2,898, rank 1.00, all PRE gates pass) and that is selection: HOLD -2,859, 2023 span -5,174, FULL +6,089 (MDE 12,994); random-slot rank on HOLD 0.28. The same holds for the worst weeks: the in-sample PRE saving in the PRE-W20 is +1,138,222 but on the FULL-W20 inside HOLD it is -12,994.
- **The range-day gate does not isolate the losses.** Gated cells touch 3-4% of entries and are negative already on PRE (A07 -2,670, A08 -3,731, A09 -2,530); the flag does not concentrate the slot losses (the audit's 64% range-day share is an ex-post label; the ex-ante 0.7x first-hour flag, 20% of days, does not recover it).
- **The control behaves.** Blocking the 14 best PRE slots (A10) costs -53,649/wk on PRE, -32,556 in HOLD and -36,447 over FULL, consistent with the best-slot list persisting while the worst-slot list does not (the HOLD CI of A10 alone includes 0, MDE 57,879; FULL is significant).
- **A03 (the one survivor candidate).** WT-only block at 05:00 and 22:00 ET: FULL LM +1,687/wk [+221,+3,180] (MDE 2,140); trade-off line: in the 20 worst FULL weeks the base lost -3,534,170 and the rule changes that by +68,722, and in the other 165 weeks it adds +1,416/wk (it gives nothing up on average), LM and raw about equal because it blocks 1% of entries. But its X-span delta is -748 (05:00 is positive in 2023: +442 vs PRE -1,053), HOLD maxDD +1,138 and worst week -603 fail G3 by a hair, PRE placebo rank 0.91 < 0.95, 2023 negative. It is one book (WT, 7 lots, the smallest book) and two slots chosen as the only strict-significant ones out of 41 (about 1-2 false positives expected). Verdict DEAD by the gates; flag LEAD-adjacent for transparency, not carried as confirmed.
- **Power.** The PRE MDEs are 3k-22k/wk and the HOLD ones 5k-36k/wk (MDE beside every mean above); every non-control mean except the in-sample PRE cells is below its MDE, so the HOLD nulls are inconclusive for effects under ~7-30k/wk but the point estimates (A02 -6,042, A04 -2,859) and the 2023 span (-19.5k A02, significant) are on the wrong side, and the slot-persistence test (binomial/Spearman) is independent of the dollar MDE.

## Carry into F (T-STACK combine)
- PRE-selected rule (rule: highest PRE LM d_mean with PRE CI lower > 0 and all PRE gates): **A06** (halve lots per book in the book's own PRE loose slots; PRE LM +14,531/wk [+6,199,+23,073]). Against F's admission test (HOLD worst-20 improves, HOLD mean not below -MDE): HOLD mean +300, FULL-W20-in-HOLD saved -3,160 -> fails the worst-20 condition; it should NOT be stacked.
- The only section-A rule that would pass F's admission test is A03 (HOLD mean +4,231, HOLD W20-in-window +3,106), but it was not PRE-selected as the best cell (A03 was picked by the strict-significance rule on PRE, a defined prereg list, yet is DEAD on G3/G4/G6). If F wants a section-A entry for completeness, carry A03 as the weakest-possible LEAD-adjacent rule with the caveat above; the honest default is no slot rule.
- PRE-only per-cell weekly series for stacking: out/stk_a/pre_series.parquet (index wk; columns base and <cell>__raw / __LM / __MM, 75 PRE weeks). Full daily series (all windows, daily $ per cell raw/LM/MM and per-book weighted nominal daily) in out/stk_a/daily_series.pkl (opened only after the logged look).

## Disclosures
1. Base-stack smoke test (PRE baseline 44,127/wk) and PRE-only slot derivation + descriptive PRE slot-dollar sums were printed before the prereg; no cell had been scored. 2. The audit's slot list (ALL data) was read for context, not used; lists are re-derived on PRE. 3. A tail print of day_labels.parquet showed rows dated 2026-10 (a market-feature table); not used. 4. Sealed-file procedure: the compute stage ran all engine tasks (1,828: 10 cells + 200 random + 2 shifted placebos per rule cell) and wrote a sealed result file; the PRE-only analysis read only the WFPRE windows; HOLD/X/FULL were opened after the PREHOLD text was logged (tracks STKA, STKA_SPAN2). 5. The `affected` column is the share of base entries in the window that fall in the rule's slot set. 6. HOLD here is capped at 2026-02-06 (the shared dvg windows run to 2026-10-16); the base weekly mean on PRE (44,127) is the cap-independent number, the audit's 45,947 is the WF to 2026-10-16. 7. Per-book loose lists are the most overfit rules (24% of entries blocked, in-sample ceiling +23.8k/wk): their PRE gate pass is a selection artifact, flagged by the HOLD / X ranks. 8. Gates unchanged from D3DVG; I did not soften any. Not tested here (no data): section-A variants on the 2026-02-06+ span.
