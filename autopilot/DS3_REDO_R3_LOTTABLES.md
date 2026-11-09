# DS3_REDO_R3_LOTTABLES - session lot tables per book x 6 sessions on the state base (S1b-COMB), first version 2026-11-09 18:11Z

> FIRST-ORDER SCREEN ONLY, ROLL-EXCL, PRE-PROOF, post-hoc, Shadow only; exact runs pending (FGH_P744, P644, P444, GREEDY in the SZ-CORE queue). STANDING RULE: every layer stays ON; the table is a setting; the live table is the reference row. Tables are the six-number strings D7 reads (asia,london,pre,nyam,nypm,close). A cell going to 0 shows the P&L it removes. Equal-$-risk parity row (2 lots every 60-pt cell, O7 3) is a REFERENCE ROW only.

## Summary block: setting | live value | best on the state base | holds OOS? | change recommended | panel field
| setting | live value | best on the state base (first-order) | holds OOS? | change? | panel field |
|--|--|--|--|--|--|
| K7 SessionLots | 2,2,0,1,2,0 | stack-greedy down: 1,0,0,1,0,0 ; UP: 1,0,0,6,4,0 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk | NO (live stays unless exact confirms) | SessionLots_K7 |
| P7 SessionLots | 7,7,0,7,0,0 | stack-greedy down: 6,3,0,0,0,0 ; UP: 6,5,0,0,0,0 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk; P7 table cells alone WF 38% raw / 35% eq / -840$/wk | P7 only: candidate 7,4,0,4,0,0 or 6,4,0,4,0,0 pending exact; others NO (live stays) | SessionLots_P7 |
| M7 SessionLots | 0,2,0,1,0,0 | stack-greedy down: 0,1,0,0,0,0 ; UP: 0,1,0,0,0,0 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk | NO (live stays unless exact confirms) | SessionLots_M7 |
| U7 SessionLots | 4,4,0,0,0,0 | stack-greedy down: 4,0,0,0,0,0 ; UP: 7,2,0,0,0,0 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk | NO (live stays unless exact confirms) | SessionLots_U7 |
| A7 SessionLots | 1,0,0,0,0,0 | stack-greedy down: 1,0,0,0,0,0 ; UP: 4,0,0,0,0,0 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk | NO (live stays unless exact confirms) | SessionLots_A7 |
| H7 SessionLots | 4,0,0,1,0,0 | stack-greedy down: 4,0,0,1,0,0 ; UP: 8,0,0,2,0,0 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk | NO (live stays unless exact confirms) | SessionLots_H7 |
| O7 SessionLots | 1,1,1,1,1,1 | stack-greedy down: 1,1,1,1,1,1 ; UP: 1,1,1,6,1,1 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk | NO (live stays unless exact confirms) | SessionLots_O7 |

## Stack-joint tables (coordinate descent over the 15 book x session cells, first-order additive; WF re-runs the procedure monthly)
| variant | strings | in-sample cut L6M/HOLD/PRE/X' | d mean L6M | WF raw / eq-mean % / d mean | P&L removed (all history) |
|--|--|--|--|--|--|
| down-only | K7 1,0,0,1,0,0; P7 6,3,0,0,0,0; M7 0,1,0,0,0,0; U7 4,0,0,0,0,0; A7 1,0,0,0,0,0; H7 4,0,0,1,0,0; O7 1,1,1,1,1,1 | 44/54/66/65 | -3132 | 52 / 22 / -6443 | +558716 |
| UP-allowed (labelled) | K7 1,0,0,6,4,0; P7 6,5,0,0,0,0; M7 0,1,0,0,0,0; U7 7,2,0,0,0,0; A7 4,0,0,0,0,0; H7 8,0,0,2,0,0; O7 1,1,1,6,1,1 | 16/33/52/47 | +5818 | 35 / 38 / +705 | -907814 |

## Reference rows (zero-change = live)
| setting | cut L6M/HOLD/PRE/X' % | d mean L6M/PRE $/wk | eq-mean cut L6M/PRE/X' % | w20 vs live | Ulcer vs live | $/wk per $1k | note |
|--|--|--|--|--|--|--|--|
| LIVE tables (reference) | 0/0/0/0 | +0/+0 | 0/0/0 | 1.00 | 1.00 | n/a | reference |
| equal-$-risk parity (2 lots per cell, O7 3) | 42/35/49/69 | -11546 | -13/2/40 | - | - | - | REFERENCE ROW only (mean lots x0.63) |

## P7 (live 7,7,0,7,0,0): asia x london x nyam lots 3-7, down-only, top 10 by SEL (sz_core numbers)
| setting | cut L6M/HOLD/PRE/X' % | d mean L6M/PRE $/wk | eq-mean cut L6M/PRE/X' % | w20 vs live | Ulcer vs live | $/wk per $1k | note |
|--|--|--|--|--|--|--|--|
| P7 7,4,0,4,0,0 | 29/19/32/27 | +372/-446 | 30/33/28 | 1.41 | 0.69 | -16 | chg share 0.13 |
| P7 6,4,0,4,0,0 | 34/29/33/37 | -1874/-1247 | 29/28/33 | 1.27 | 0.65 | +70 | chg share 0.22 |
| P7 7,3,0,4,0,0 | 29/19/36/26 | -269/-738 | 28/35/25 | 1.33 | 0.69 | +12 | chg share 0.13 |
| P7 6,3,0,4,0,0 | 32/29/36/37 | -2458/-1540 | 25/30/30 | 1.20 | 0.65 | +95 | chg share 0.22 |
| P7 7,4,0,3,0,0 | 29/19/32/25 | -478/-505 | 28/31/24 | 1.35 | 0.69 | +21 | chg share 0.13 |
| P7 7,3,0,3,0,0 | 28/19/36/24 | -1120/-717 | 24/33/21 | 1.27 | 0.70 | +51 | chg share 0.13 |
| P7 6,4,0,3,0,0 | 31/29/33/35 | -2738/-1240 | 23/25/28 | 1.21 | 0.65 | +111 | chg share 0.22 |
| P7 7,5,0,4,0,0 | 20/14/24/26 | +610/-457 | 22/26/28 | 1.35 | 0.78 | -38 | chg share 0.12 |
| P7 6,3,0,3,0,0 | 30/30/36/34 | -3323/-1452 | 20/27/25 | 1.14 | 0.64 | +140 | chg share 0.22 |
| P7 5,4,0,4,0,0 | 34/29/30/36 | -3518/-1307 | 24/19/26 | 1.18 | 0.66 | +130 | chg share 0.23 |

P7 single-cell grid (one session at a time, q = 0..8; q=0 removes the cell; P&L removed over all history and L6M):
| session | q | cut L6M/PRE/X' | d mean L6M | P&L removed all / L6M ($ at base lots) | trades changed |
|--|--|--|--|--|--|
| 0 | 0 | -38/-3/21 | -13514 | +1023252 / +384068 | 2288 |
| 0 | 1 | -19/-3/15 | -9900 | +806663 / +287627 | 2234 |
| 0 | 2 | -18/-6/20 | -9656 | +735401 / +274402 | 2234 |
| 0 | 3 | -8/-7/9 | -7677 | +600930 / +218396 | 2234 |
| 0 | 4 | -1/-2/15 | -5585 | +409645 / +159609 | 2234 |
| 0 | 5 | 2/-2/8 | -3289 | +278411 / +96006 | 2108 |
| 0 | 6 | 2/1/12 | -1979 | +134471 / +56006 | 1986 |
| 0 | 8 (UP) | -4/-1/3 | +1093 | -121813 / -33608 | 878 |
| 1 | 0 | 28/51/5 | -2348 | +234499 / +44580 | 1679 |
| 1 | 1 | 28/44/8 | -1217 | +153083 / +18506 | 1609 |
| 1 | 2 | 23/40/6 | -1457 | +174401 / +25975 | 1609 |
| 1 | 3 | 19/28/7 | -1274 | +140168 / +23854 | 1609 |
| 1 | 4 | 17/25/9 | -632 | +80446 / +10130 | 1609 |
| 1 | 5 | 8/17/9 | -561 | +53822 / +9496 | 1412 |
| 1 | 6 | 5/12/3 | -183 | +34233 / +2121 | 1323 |
| 1 | 8 (UP) | -5/-3/-2 | +67 | -20924 / +95 | 550 |
| 3 | 0 | 15/16/32 | +1971 | +12060 / -47946 | 1303 |
| 3 | 1 | 15/12/31 | +2301 | -32087 / -55994 | 1053 |
| 3 | 2 | 14/11/24 | +2031 | +12642 / -49518 | 1053 |
| 3 | 3 | 7/7/15 | +991 | +63610 / -23498 | 1053 |
| 3 | 4 | 9/8/19 | +1700 | -48933 / -41708 | 1053 |
| 3 | 5 | 5/4/9 | +698 | +7516 / -16618 | 972 |
| 3 | 6 | 5/4/10 | +1040 | -52238 / -26020 | 764 |
| 3 | 8 (UP) | -4/-1/-4 | +0 | -18866 / -4 | 321 |

## U7 (live 4,4,0,0,0,0): asia x london lots 0-6, down-only top 6 by SEL (first-order, rz via sz_core)
| setting | cut L6M/HOLD/PRE/X' % | d mean L6M/PRE $/wk | eq-mean cut L6M/PRE/X' % | w20 vs live | Ulcer vs live | $/wk per $1k | note |
|--|--|--|--|--|--|--|--|
| U7 4,0,0,0,0,0 | 14/0/13/-1 | +15/-232 | 14/13/-1 | 0.98 | 0.89 | -1 |  |
| U7 4,2,0,0,0,0 | 7/-1/7/4 | -432/-116 | 6/5/2 | 1.00 | 0.93 | +74 |  |
| U7 4,1,0,0,0,0 | 8/-1/9/5 | -159/-138 | 8/9/5 | 0.94 | 0.92 | +24 |  |
| U7 4,3,0,0,0,0 | 1/0/3/2 | -239/-23 | 0/2/1 | 0.94 | 0.99 | +274 |  |
| U7 4,4,0,0,0,0 | 0/0/0/0 | +0/+0 | 0/0/0 | 1.00 | 1.00 | n/a |  |
| U7 3,0,0,0,0,0 | 8/2/14/-7 | -845/-472 | 5/10/-11 | 0.89 | 0.93 | +132 |  |

## Cells going to 0: P&L removed (base lots, all history / L6M) and effect
| book | session | trades removed | P&L removed all / L6M | cut L6M/PRE/X' | d mean L6M |
|--|--|--|--|--|--|
| M7 | 1 | 2722 | -19642 / -28780 | 11/14/-26 | +1243 |
| P7 | 3 | 1303 | +12060 / -47946 | 15/16/32 | +1971 |
| H7 | 3 | 415 | +29275 / +12345 | -5/-3/-6 | -561 |
| M7 | 3 | 1803 | +31341 / +5464 | -1/1/3 | -26 |
| K7 | 3 | 1686 | +51308 / -10161 | -6/1/-7 | +359 |
| K7 | 4 | 1356 | +51927 / +30442 | 3/3/-1 | -1194 |
| K7 | 1 | 1760 | +62069 / +168 | 4/9/4 | -160 |
| O7 | 3 | 506 | +86882 / +8119 | -3/0/-4 | -188 |
| U7 | 1 | 686 | +90508 / +14007 | 14/13/-1 | -753 |
| A7 | 0 | 1160 | +124028 / +21788 | 0/-3/-7 | -744 |
| H7 | 0 | 701 | +145871 / +55744 | -10/-8/7 | -2416 |
| P7 | 1 | 1679 | +234499 / +44580 | 28/51/5 | -2348 |
| K7 | 0 | 2383 | +257139 / +67487 | -6/-3/6 | -2528 |
| U7 | 0 | 687 | +266004 / +77860 | -19/7/-16 | -3047 |
| P7 | 0 | 2288 | +1023252 / +384068 | -38/-3/21 | -13514 |

Plain sentences: P7 - lowering the Asia/London/NY-AM lots to 7,4,0,4 (or 6,4,0,4) is the one table change whose picking procedure walks forward on all three bases at first-order (see SZ_FGH.md section 1); it is a first-order lead and needs the exact runs before any panel change. Zeroing whole book-sessions (the stack greedy) removes real profit and its walk-forward at equal mean is weak; the live tables stay for K7, M7, U7, A7, H7, O7 until exact says otherwise. Old-vs-new base for these cells is on SZ_FGH.md section 10.

## Old base vs new (first-order, same grid; OLD-BASE not roll-excluded)
Stack greedy down WF at equal mean: new 22% / old 1%; strings new 6,3,0,0,0,0 / old 4,3,0,0,0,0.

| P7 table | cut L6M/PRE/X' NEW | OLD | delta L6M/PRE | SEL new/old | rank new/old (of 125) | identical to the dollar? |
|--|--|--|--|--|--|--|
| 7,4,0,4,0,0 | 29/32/27 | 21/37/0 | +8/-5 | 32.7/17.2 | 1/5 | no |
| 6,4,0,4,0,0 | 34/33/37 | 32/41/9 | +1/-9 | 31.9/20.6 | 2/1 | no |
| 7,3,0,4,0,0 | 29/36/26 | 22/41/1 | +7/-5 | 31.5/15.7 | 3/8 | no |
| 6,3,0,4,0,0 | 32/36/37 | 34/45/9 | -1/-8 | 30.5/19.0 | 4/2 | no |
| 7,4,0,3,0,0 | 29/32/25 | 18/37/-8 | +11/-5 | 29.8/9.6 | 5/38 | no |
| 7,3,0,3,0,0 | 28/36/24 | 19/41/-6 | +9/-5 | 28.3/8.1 | 6/44 | no |
| 6,4,0,3,0,0 | 31/33/35 | 29/41/2 | +2/-9 | 28.1/13.3 | 7/14 | no |
| 7,5,0,4,0,0 | 20/24/26 | 14/26/1 | +7/-2 | 27.2/12.1 | 8/20 | no |
