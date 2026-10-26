# REPORT STRUCT48 HB - handoff book after an ST/HM stop-out (RESEARCH V2 addendum)
Agent HB, 2026-10-24. Research only: no execution-server / chart / live change, no credentials, no download, UNTOUCHED never read. Prereg l2vast/struct48/prereg/HB_prereg.md sha256 ac398dcc5472910477495467c39be06ba230bb49b58f38494e648c8e3bef177e (frozen in autopilot/DECISIONS.md before any scored cell; 28 cells in ledger/trials.jsonl, cumulative total 28,502). Pre-holdout text autopilot/REPORT_STRUCT48_HB_PREHOLD.md (sha256 599025ac82dd40f020e072c5bc9fdc2fe80e72543a7a5533675ad3b0379621a4, written and logged before the one holdout look, ledger/holdout_looks.jsonl track HB). Rows: l2vast/struct48/rows/HB_pre.json (WF-PRE stage) and HB_final.json (final). Code: l2vast/struct48/code/hb_*.py.

## Verdict
**0 PASS, 0 CANDIDATE, 28 DEAD.** Nothing is registered in PAPER-ALL (no paper_all/*.json written for HB). The mechanism 'a 67-pt stop-run exhausts the move' is not paid by any of the four handoff constructions on this data under live cost:
- (a) reverse at the stop fill: significantly NEGATIVE, -1.7 to -2.6 pts/event (-$138 to -$368 per stop-out event, -$1.9k to -$5.1k per week standalone) in WF with 1,956 events; placebo rank 0.00-0.15 (random times do better than stop-out times); holdout agrees (-1.3 to -2.4 pts/event); gross edge at ZERO cost is negative (see cost table): the stop-run does not continue, and it does not pay its fills.
- (b) VWAP reversion from the stop fill: -0.9 to -1.4 pts/event, CI includes zero, MDE 2.2-2.5 pts/event; the gross edge at zero cost is positive (+0.4 to +1.2 pts/event in WF-PRE) but is entirely consumed by the 1.01 pt joins and the 0.995 pt market entry. Holdout negative.
- (c) opening range re-entry: +0.4 pts/event WF (+0.9 in WF-PRE, -0.1 in the holdout), placebo 0.97-0.98, CI includes zero, MDE 0.97: below the detectable effect and not confirmed out of sample; prior-value re-entry: +0.02 pts/event (MDE 0.74), nothing.
- (d) re-break in the original direction: -0.7 / -1.0 pts/event (w15/w30), CI includes zero, MDE 2.3-2.4.
So the answer to the addendum is a clean no: a 67-pt stop-run is followed neither by continuation (a) nor by a tradable reversion (b, d); the opening-range re-entry (c) is the only positive sign and is neither significant nor confirmed.

## Power and counts (stated before scoring, confirmed here)
Stop-out events (Set A trades that exited at their natural stop, not flattened earlier by a lock): IS 512, WF-PRE 912, holdout 1,044, **WF 1,956** (about 13.8 per week; 1,919 of the WF events fall before the last entry bar and can trade; the rest count as 0 in the paired mean). Sessions with at least one WF event: 893.
MDE at 80% power for the paired test on the WF window is in the table next to every cell (2.80 x cluster-bootstrap SE, blocks = label-day x session): 0.50-2.49 pts/event, i.e. $71-$349 per event at 7 lots; the weekly (unpaired) test could only see 24,574 $/wk (Set A's own SD), so no cell was judged on weekly P&L. Design effect (block clustering) 0.93-1.30.

## Main table, WF 2024-02..2026-10 (paired = decision basis)
Score window WF. Paired effect = mean over ALL stop-out events (0 for no-trade events) of book pts net of fills and commission; $ at the cell's lots; $/wk = window sum / weeks. Full-seq = Set A + book through the locked sequence, week-block CI; d = vs Set A.

| cell | n events | trades (skipped by filter) | paired effect pts/event [95% CI] | $/event | $/wk | MDE pts (80%) | effect >= MDE | placebo | neighbours | full-seq d mean $/wk [CI] | d SD | d maxDD | 2x d $/wk | SENS2 paired pts | SENS2 d $/wk | year-share | DSR | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HB_REV_s20_r1.0_L4 | 1956 | 1552 (366) | -2.12 [-2.91, -1.35] | -169 | -2,333 | 1.13 | Y | 0.01 | Y | -1,078 [-3,538, +1,322] | +1,868 | +79,794 | -2,406 | -4.72 | -2,619 | - | 0.205 | DEAD |
| HB_REV_s20_r1.0_L7 | 1956 | 1552 (366) | -2.12 [-2.91, -1.35] | -296 | -4,083 | 1.13 | Y | 0.01 | Y | -1,734 [-4,649, +1,476] | +3,071 | +64,350 | -4,669 | -4.72 | -5,598 | - | 0.177 | DEAD |
| HB_REV_s20_r1.5_L4 | 1956 | 1552 (366) | -2.40 [-3.37, -1.50] | -192 | -2,642 | 1.33 | Y | 0.00 | Y | +66 [-2,931, +3,166] | +3,178 | +44,180 | -2,747 | -5.22 | -3,513 | 22.77 | 0.234 | DEAD |
| HB_REV_s20_r1.5_L7 | 1956 | 1552 (366) | -2.40 [-3.37, -1.50] | -336 | -4,624 | 1.33 | Y | 0.00 | Y | -523 [-4,449, +3,798] | +2,824 | +29,286 | -5,415 | -5.22 | -7,739 | - | 0.216 | DEAD |
| HB_REV_s30_r1.0_L4 | 1956 | 1552 (366) | -2.06 [-3.23, -0.97] | -165 | -2,274 | 1.67 | Y | 0.03 | Y | +132 [-3,081, +3,516] | +793 | +41,752 | -1,212 | -4.99 | -2,603 | 5.69 | 0.257 | DEAD |
| HB_REV_s30_r1.0_L7 | 1956 | 1552 (366) | -2.06 [-3.23, -0.97] | -289 | -3,979 | 1.67 | Y | 0.03 | Y | -246 [-5,140, +4,575] | +3,554 | +32,781 | -5,808 | -4.99 | -5,424 | - | 0.220 | DEAD |
| HB_REV_s30_r1.5_L4 | 1956 | 1552 (366) | -2.37 [-3.69, -1.05] | -189 | -2,608 | 1.94 | Y | 0.01 | Y | -44 [-4,015, +3,681] | +1,148 | +41,595 | -3,637 | -5.00 | -3,620 | - | 0.245 | DEAD |
| HB_REV_s30_r1.5_L7 | 1956 | 1552 (366) | -2.37 [-3.69, -1.05] | -331 | -4,564 | 1.94 | Y | 0.01 | Y | -1,122 [-6,043, +4,082] | +3,012 | -2,419 | -7,503 | -5.00 | -6,001 | - | 0.195 | DEAD |
| HB_REV_s40_r1.0_L4 | 1956 | 1552 (366) | -1.72 [-3.26, -0.18] | -138 | -1,897 | 2.18 | N | 0.15 | Y | -1,390 [-4,538, +1,636] | +1,903 | +29,020 | -682 | -4.04 | -3,628 | - | 0.196 | DEAD |
| HB_REV_s40_r1.0_L7 | 1956 | 1552 (366) | -1.72 [-3.26, -0.18] | -241 | -3,319 | 2.18 | N | 0.15 | Y | -398 [-6,140, +5,186] | +3,879 | -12,410 | -789 | -4.04 | -3,925 | - | 0.211 | DEAD |
| HB_REV_s40_r1.5_L4 | 1956 | 1552 (366) | -2.63 [-4.34, -1.01] | -210 | -2,896 | 2.47 | Y | 0.01 | Y | -3,511 [-7,905, +485] | +2,658 | +31,254 | -3,625 | -4.75 | -6,017 | - | 0.132 | DEAD |
| HB_REV_s40_r1.5_L7 | 1956 | 1552 (366) | -2.63 [-4.34, -1.01] | -368 | -5,068 | 2.47 | Y | 0.01 | Y | -2,358 [-8,365, +3,335] | +2,491 | +65,952 | -6,061 | -4.75 | -7,640 | - | 0.162 | DEAD |
| HB_VWAP_k1.5_L4 | 1956 | 1349 (370) | -0.91 [-2.54, +0.61] | -73 | -1,000 | 2.25 | N | 0.70 | Y | +2,919 [-2,240, +9,005] | +1,759 | +29,829 | -3,237 | -1.25 | +2,455 | 0.50 | 0.355 | DEAD |
| HB_VWAP_k1.5_L7 | 1956 | 1349 (370) | -0.91 [-2.54, +0.61] | -127 | -1,749 | 2.25 | N | 0.70 | Y | +2,443 [-4,136, +9,525] | -459 | +28,837 | -2,505 | -1.25 | +2,001 | 0.67 | 0.361 | DEAD |
| HB_VWAP_k1.25_L4_NB (NB) | 1956 | 1349 (370) | -1.00 [-2.61, +0.49] | -80 | -1,104 | 2.17 | N | 0.59 | - | +2,076 [-3,179, +8,117] | +1,779 | +45,105 | -2,972 | -1.41 | +1,809 | 0.81 | 0.321 | DEAD* |
| HB_VWAP_k2.0_L4_NB (NB) | 1956 | 1349 (370) | -1.37 [-3.13, +0.28] | -110 | -1,510 | 2.49 | N | 0.46 | - | +1,159 [-4,056, +7,059] | -10 | +19,396 | -3,320 | -1.63 | +959 | 0.98 | 0.303 | DEAD* |
| HB_OR_s30_L4 | 1956 | 288 (167) | +0.36 [-0.28, +1.04] | +29 | +395 | 0.97 | N | 0.98 | Y | +3,102 [+264, +6,760] | +1,650 | -31,600 | -73 | +0.23 | +2,261 | 0.58 | 0.364 | DEAD |
| HB_OR_s30_L7 | 1956 | 288 (167) | +0.36 [-0.28, +1.04] | +50 | +691 | 0.97 | N | 0.98 | Y | +1,388 [-2,282, +5,882] | +2,960 | +18,208 | 675 | +0.23 | +1,245 | 1.10 | 0.283 | DEAD |
| HB_OR_s20_L4_NB (NB) | 1956 | 288 (167) | +0.14 [-0.30, +0.56] | +11 | +150 | 0.62 | N | 0.97 | - | +904 [-1,093, +3,490] | +1,899 | -1,005 | -128 | -0.02 | +760 | 1.68 | 0.273 | DEAD* |
| HB_OR_s40_L4_NB (NB) | 1956 | 288 (167) | +0.52 [-0.26, +1.32] | +42 | +574 | 1.15 | N | 0.97 | - | +1,750 [-1,870, +6,004] | +3,255 | +24,429 | 1,029 | +0.41 | +1,627 | 1.02 | 0.294 | DEAD* |
| HB_PV_s30_L4 | 1956 | 178 (64) | +0.02 [-0.46, +0.58] | +2 | +26 | 0.74 | N | 0.70 | N | +287 [-311, +933] | +255 | -32,412 | -766 | -0.07 | +214 | 0.69 | 0.266 | DEAD |
| HB_PV_s30_L7 | 1956 | 178 (64) | +0.02 [-0.46, +0.58] | +3 | +46 | 0.74 | N | 0.70 | N | +131 [-1,911, +1,975] | -268 | -27,464 | -1,526 | -0.07 | +18 | 5.20 | 0.265 | DEAD |
| HB_PV_s20_L4_NB (NB) | 1956 | 178 (64) | +0.05 [-0.29, +0.40] | +4 | +55 | 0.50 | N | 0.86 | - | +121 [-408, +735] | +107 | -30,858 | -1,294 | -0.05 | +66 | 1.86 | 0.262 | DEAD* |
| HB_PV_s40_L4_NB (NB) | 1956 | 178 (64) | -0.24 [-0.83, +0.46] | -19 | -264 | 0.93 | N | 0.32 | - | -437 [-2,343, +897] | -157 | -32,267 | -595 | -0.33 | -512 | - | 0.243 | DEAD* |
| HB_REB_w15_L4 | 1956 | 911 (305) | -0.66 [-2.29, +0.96] | -53 | -725 | 2.33 | N | 0.55 | Y | -2,659 [-7,792, +2,165] | +1,893 | +263,499 | -7,342 | -1.96 | -3,878 | - | 0.159 | DEAD |
| HB_REB_w15_L7 | 1956 | 911 (305) | -0.66 [-2.29, +0.96] | -92 | -1,269 | 2.33 | N | 0.55 | Y | -2,967 [-9,327, +3,234] | +1,945 | +415,714 | -8,709 | -1.96 | -6,395 | - | 0.152 | DEAD |
| HB_REB_w30_L4 | 1956 | 977 (361) | -0.96 [-2.68, +0.73] | -77 | -1,060 | 2.43 | N | 0.44 | Y | -3,310 [-8,523, +1,570] | +1,628 | +256,705 | -5,312 | -2.32 | -4,683 | - | 0.143 | DEAD |
| HB_REB_w30_L7 | 1956 | 977 (361) | -0.96 [-2.68, +0.73] | -135 | -1,855 | 2.43 | N | 0.44 | Y | -3,685 [-10,600, +2,722] | +2,618 | +403,742 | -7,947 | -2.32 | -6,451 | - | 0.130 | DEAD |

Every number is for the cell's own lots (4 or 7); lots-4 and lots-7 cells have identical points. '(NB)' cells are the neighbour-only cells of the prereg (counted as trials, they only feed neighbours-agree).

## Holdout (2025-07+, looked once after the pre-holdout text), L8W and IS
| cell | holdout events | holdout paired pts/event | holdout $/event | holdout full-seq d $/wk | WF effect pts/event | WF-PRE effect pts/event (pre-holdout text) | L8W full-seq d $/wk | IS full-seq d $/wk | IS paired pts/event |
|---|---|---|---|---|---|---|---|---|---|
| HB_REV_s20_r1.0_L4 | 1044 | -2.26 | -181 | -1,599 | -2.12 | -1.96 | -4,187 | -4,684 | -2.80 |
| HB_REV_s20_r1.0_L7 | 1044 | -2.26 | -316 | -3,659 | -2.12 | -1.96 | -9,923 | -5,437 | -2.80 |
| HB_REV_s20_r1.5_L4 | 1044 | -2.24 | -179 | -1,932 | -2.40 | -2.58 | -5,064 | -4,839 | -2.50 |
| HB_REV_s20_r1.5_L7 | 1044 | -2.24 | -314 | -1,387 | -2.40 | -2.58 | -7,989 | -3,006 | -2.50 |
| HB_REV_s30_r1.0_L4 | 1044 | -1.67 | -134 | +1,322 | -2.06 | -2.51 | +9,935 | -3,181 | -2.61 |
| HB_REV_s30_r1.0_L7 | 1044 | -1.67 | -234 | -1,201 | -2.06 | -2.51 | +6,749 | -4,171 | -2.61 |
| HB_REV_s30_r1.5_L4 | 1044 | -1.83 | -146 | +2,923 | -2.37 | -2.98 | +9,837 | -2,030 | -2.33 |
| HB_REV_s30_r1.5_L7 | 1044 | -1.83 | -256 | +1,415 | -2.37 | -2.98 | +6,722 | -539 | -2.33 |
| HB_REV_s40_r1.0_L4 | 1044 | -1.32 | -106 | -64 | -1.72 | -2.18 | +9,086 | -4,116 | -1.11 |
| HB_REV_s40_r1.0_L7 | 1044 | -1.32 | -185 | +1,752 | -1.72 | -2.18 | +5,852 | -6,334 | -1.11 |
| HB_REV_s40_r1.5_L4 | 1044 | -2.37 | -190 | -1,627 | -2.63 | -2.92 | +9,820 | -1,910 | -1.08 |
| HB_REV_s40_r1.5_L7 | 1044 | -2.37 | -332 | -725 | -2.63 | -2.92 | +6,931 | +225 | -1.08 |
| HB_VWAP_k1.5_L4 | 1044 | -1.40 | -112 | +2,572 | -0.91 | -0.34 | +189 | -1,794 | -2.89 |
| HB_VWAP_k1.5_L7 | 1044 | -1.40 | -196 | +367 | -0.91 | -0.34 | -6,354 | -3,149 | -2.89 |
| HB_VWAP_k1.25_L4_NB | 1044 | -1.70 | -136 | +450 | -1.00 | -0.20 | -89 | -1,537 | -2.52 |
| HB_VWAP_k2.0_L4_NB | 1044 | -1.85 | -148 | +1,013 | -1.37 | -0.83 | -407 | -3,117 | -3.55 |
| HB_OR_s30_L4 | 1044 | -0.12 | -9 | +1,876 | +0.36 | +0.90 | -939 | +1,199 | -0.69 |
| HB_OR_s30_L7 | 1044 | -0.12 | -16 | -518 | +0.36 | +0.90 | -1,293 | +555 | -0.69 |
| HB_OR_s20_L4_NB | 1044 | -0.18 | -14 | +601 | +0.14 | +0.50 | -1,552 | -293 | -0.86 |
| HB_OR_s40_L4_NB | 1044 | +0.10 | +8 | +285 | +0.52 | +1.00 | -1,587 | -91 | -1.18 |
| HB_PV_s30_L4 | 1044 | +0.14 | +12 | +45 | +0.02 | -0.11 | +223 | +233 | +0.66 |
| HB_PV_s30_L7 | 1044 | +0.14 | +20 | +250 | +0.02 | -0.11 | +390 | +1,207 | +0.66 |
| HB_PV_s20_L4_NB | 1044 | +0.12 | +10 | -273 | +0.05 | -0.04 | -435 | +124 | +0.41 |
| HB_PV_s40_L4_NB | 1044 | -0.08 | -6 | -50 | -0.24 | -0.43 | -607 | +683 | +0.64 |
| HB_REB_w15_L4 | 1044 | -1.21 | -97 | -1,684 | -0.66 | -0.03 | +154 | +1,732 | +0.81 |
| HB_REB_w15_L7 | 1044 | -1.21 | -169 | -1,113 | -0.66 | -0.03 | -9,925 | +3,027 | +0.81 |
| HB_REB_w30_L4 | 1044 | -1.40 | -112 | -1,923 | -0.96 | -0.46 | +281 | +1,384 | +0.44 |
| HB_REB_w30_L7 | 1044 | -1.40 | -197 | -2,800 | -0.96 | -0.46 | -9,951 | +2,623 | +0.44 |

The holdout paired effect is negative for every (a), (b) and (d) cell, as in WF-PRE; the OR re-entry flips from +0.90 (WF-PRE) to -0.12 (holdout) and PV s30 from -0.11 to +0.14 (both about zero, MDE 0.7-1.3).

## Weekly WF / L8W / IS of Set A + book through the full locked sequence (locks, give-back, week floor, 50-contract and opposite-side rules; 1x cost)
| system | WF mean / SD / maxDD / worst week | L8W mean / SD / maxDD / worst | IS mean / SD / maxDD / worst | trades/wk WF |
|---|---|---|---|---|
| Set A (benchmark) | 24,975 / 104,523 / 401,293 / -137,081 | 34,191 / 109,399 / 267,133 / -98,918 | 13,671 / 95,946 / 407,253 / -136,337 | 35.8 |
| Set A + HB_REV_s20_r1.0_L4 | 23,897 / 106,392 / 481,087 / -140,259 | 30,004 / 112,505 / 287,991 / -112,399 | 8,987 / 97,485 / 525,769 / -135,332 | 46.1 |
| Set A + HB_REV_s20_r1.0_L7 | 23,241 / 107,594 / 465,643 / -136,836 | 24,269 / 113,495 / 301,709 / -122,475 | 8,234 / 97,090 / 534,047 / -136,700 | 45.9 |
| Set A + HB_REV_s20_r1.5_L4 | 25,042 / 107,702 / 445,473 / -137,884 | 29,128 / 110,971 / 286,813 / -109,899 | 8,832 / 96,933 / 502,314 / -135,100 | 46.0 |
| Set A + HB_REV_s20_r1.5_L7 | 24,453 / 107,348 / 430,579 / -136,977 | 26,202 / 113,633 / 299,648 / -117,435 | 10,665 / 94,580 / 484,025 / -136,488 | 45.8 |
| Set A + HB_REV_s30_r1.0_L4 | 25,107 / 105,317 / 443,045 / -142,657 | 44,126 / 116,289 / 271,010 / -113,257 | 10,490 / 95,235 / 491,074 / -135,031 | 45.6 |
| Set A + HB_REV_s30_r1.0_L7 | 24,730 / 108,077 / 434,074 / -136,835 | 40,941 / 120,430 / 285,475 / -124,956 | 9,500 / 96,965 / 467,607 / -135,263 | 44.8 |
| Set A + HB_REV_s30_r1.5_L4 | 24,932 / 105,671 / 442,889 / -141,457 | 44,028 / 113,253 / 265,951 / -109,017 | 11,641 / 95,219 / 465,888 / -135,491 | 45.8 |
| Set A + HB_REV_s30_r1.5_L7 | 23,854 / 107,535 / 398,874 / -136,663 | 40,914 / 115,968 / 283,310 / -114,806 | 13,132 / 95,782 / 407,026 / -134,983 | 45.2 |
| Set A + HB_REV_s40_r1.0_L4 | 23,585 / 106,426 / 430,313 / -137,256 | 43,277 / 115,382 / 262,770 / -112,517 | 9,555 / 97,186 / 455,918 / -136,736 | 45.5 |
| Set A + HB_REV_s40_r1.0_L7 | 24,577 / 108,402 / 388,883 / -138,330 | 40,043 / 118,952 / 279,458 / -119,078 | 7,337 / 97,919 / 555,870 / -137,036 | 44.6 |
| Set A + HB_REV_s40_r1.5_L4 | 21,464 / 107,182 / 432,547 / -139,581 | 44,011 / 115,593 / 270,545 / -112,879 | 11,761 / 96,047 / 405,896 / -135,617 | 44.7 |
| Set A + HB_REV_s40_r1.5_L7 | 22,617 / 107,014 / 467,246 / -135,672 | 41,122 / 118,224 / 278,868 / -123,315 | 13,896 / 94,449 / 467,404 / -135,955 | 44.4 |
| Set A + HB_VWAP_k1.5_L4 | 27,894 / 106,282 / 431,122 / -137,239 | 34,380 / 113,240 / 266,564 / -104,322 | 11,877 / 98,039 / 474,368 / -136,802 | 44.7 |
| Set A + HB_VWAP_k1.5_L7 | 27,418 / 104,065 / 430,131 / -138,725 | 27,837 / 105,436 / 265,892 / -103,755 | 10,522 / 97,469 / 441,107 / -137,151 | 44.5 |
| Set A + HB_VWAP_k1.25_L4_NB | 27,052 / 106,303 / 446,399 / -137,448 | 34,103 / 113,335 / 267,700 / -102,605 | 12,134 / 98,132 / 481,202 / -136,244 | 44.4 |
| Set A + HB_VWAP_k2.0_L4_NB | 26,134 / 104,513 / 420,690 / -140,269 | 33,784 / 111,784 / 259,934 / -99,316 | 10,554 / 98,336 / 487,092 / -135,081 | 44.7 |
| Set A + HB_OR_s30_L4 | 28,077 / 106,174 / 369,693 / -137,081 | 33,252 / 110,852 / 276,093 / -101,458 | 14,870 / 94,576 / 347,909 / -136,856 | 37.8 |
| Set A + HB_OR_s30_L7 | 26,363 / 107,483 / 419,502 / -137,081 | 32,898 / 111,997 / 282,813 / -103,363 | 14,226 / 95,522 / 373,540 / -137,245 | 37.2 |
| Set A + HB_OR_s20_L4_NB | 25,880 / 106,422 / 400,288 / -137,081 | 32,639 / 110,000 / 273,352 / -100,658 | 13,378 / 96,056 / 409,488 / -135,387 | 37.8 |
| Set A + HB_OR_s40_L4_NB | 26,725 / 107,778 / 425,722 / -138,296 | 32,604 / 111,344 / 278,873 / -102,218 | 13,580 / 96,103 / 417,114 / -136,856 | 37.1 |
| Set A + HB_PV_s30_L4 | 25,263 / 104,779 / 368,881 / -137,081 | 34,414 / 110,246 / 268,831 / -98,918 | 13,904 / 95,661 / 395,211 / -136,337 | 36.7 |
| Set A + HB_PV_s30_L7 | 25,106 / 104,255 / 373,829 / -137,592 | 34,581 / 110,889 / 270,104 / -98,918 | 14,878 / 94,815 / 386,915 / -136,337 | 36.6 |
| Set A + HB_PV_s20_L4_NB | 25,096 / 104,631 / 370,435 / -137,081 | 33,757 / 109,132 / 268,870 / -98,918 | 13,795 / 95,721 / 403,042 / -136,337 | 36.8 |
| Set A + HB_PV_s40_L4_NB | 24,539 / 104,367 / 369,026 / -138,533 | 33,584 / 110,554 / 275,470 / -98,918 | 14,354 / 95,218 / 392,501 / -136,337 | 36.6 |
| Set A + HB_REB_w15_L4 | 22,317 / 106,416 / 664,792 / -138,040 | 34,345 / 116,726 / 287,268 / -107,976 | 15,403 / 95,187 / 379,818 / -135,862 | 41.4 |
| Set A + HB_REB_w15_L7 | 22,008 / 106,468 / 817,007 / -139,147 | 24,266 / 106,432 / 302,474 / -114,070 | 16,698 / 94,009 / 383,440 / -135,231 | 41.3 |
| Set A + HB_REB_w30_L4 | 21,666 / 106,152 / 657,998 / -139,203 | 34,473 / 115,871 / 287,268 / -107,976 | 15,055 / 94,845 / 377,608 / -135,862 | 41.7 |
| Set A + HB_REB_w30_L7 | 21,290 / 107,142 / 805,035 / -137,507 | 24,240 / 105,491 / 302,474 / -114,070 | 16,294 / 93,757 / 378,644 / -135,231 | 41.6 |

READ THIS COLUMN WITH CARE: the book's P&L enters the combined day cap / give-back arm / week floor, which shifts which D2 trades survive. Even for a book that earns 0 the full-sequence weekly mean moves by -2,249 to +4,192 $/wk (WF, lock-feedback shift) and the maxDD by tens to hundreds of $k (REB cells: +256,705 to +415,714 $ maxDD vs Set A with a book whose own P&L is about -$0.7k to -$1.9k/wk). This lock chaos is larger than any effect the handoff book could carry, so the 'maxDD not worse in the full sequence' leg of the trade-modifier criterion cannot be evaluated cleanly; additive view (no feedback) below.

## The book on its own (additive, no lock feedback) and lock-feedback size
| cell | book alone WF mean $/wk (additive, no locks) | SD | maxDD | worst wk | holdout mean | L8W mean | IS mean | book DSR (WF, N trials) | lock-feedback shift of the full-seq weekly mean | additive maxDD diff vs Set A |
|---|---|---|---|---|---|---|---|---|---|---|
| HB_REV_s20_r1.0_L4 | -2,333 | 4,995 | 332,890 | -17,282 | -2,774 | -6,202 | -2,207 | 0.000 | +1,255 | +48,071 |
| HB_REV_s20_r1.0_L7 | -4,083 | 8,741 | 582,557 | -30,244 | -4,855 | -10,853 | -3,863 | 0.000 | +2,349 | +84,125 |
| HB_REV_s20_r1.5_L4 | -2,642 | 6,129 | 378,249 | -29,783 | -2,753 | -5,055 | -1,970 | 0.000 | +2,708 | +45,155 |
| HB_REV_s20_r1.5_L7 | -4,624 | 10,725 | 661,936 | -52,120 | -4,817 | -8,845 | -3,447 | 0.000 | +4,101 | +79,022 |
| HB_REV_s30_r1.0_L4 | -2,274 | 7,618 | 325,275 | -26,241 | -2,051 | -4,003 | -2,059 | 0.000 | +2,406 | +50,767 |
| HB_REV_s30_r1.0_L7 | -3,979 | 13,332 | 569,232 | -45,921 | -3,589 | -7,005 | -3,603 | 0.000 | +3,734 | +88,842 |
| HB_REV_s30_r1.5_L4 | -2,608 | 7,915 | 375,010 | -27,521 | -2,244 | -2,578 | -1,832 | 0.000 | +2,564 | +39,910 |
| HB_REV_s30_r1.5_L7 | -4,564 | 13,852 | 656,267 | -48,162 | -3,927 | -4,512 | -3,207 | 0.000 | +3,443 | +69,843 |
| HB_REV_s40_r1.0_L4 | -1,897 | 9,205 | 272,528 | -33,539 | -1,620 | -2,800 | -876 | 0.000 | +506 | +23,242 |
| HB_REV_s40_r1.0_L7 | -3,319 | 16,109 | 476,924 | -58,692 | -2,835 | -4,901 | -1,532 | 0.000 | +2,921 | +40,674 |
| HB_REV_s40_r1.5_L4 | -2,896 | 10,261 | 420,236 | -39,380 | -2,912 | -791 | -851 | 0.000 | -615 | +29,767 |
| HB_REV_s40_r1.5_L7 | -5,068 | 17,957 | 735,412 | -68,915 | -5,096 | -1,384 | -1,490 | 0.000 | +2,710 | +52,093 |
| HB_VWAP_k1.5_L4 | -1,000 | 11,092 | 209,201 | -26,842 | -1,723 | -3,718 | -2,278 | 0.000 | +3,918 | -12,848 |
| HB_VWAP_k1.5_L7 | -1,749 | 19,411 | 366,102 | -46,973 | -3,015 | -6,507 | -3,987 | 0.000 | +4,192 | +7,414 |
| HB_VWAP_k1.25_L4_NB | -1,104 | 10,596 | 222,845 | -28,662 | -2,094 | -2,430 | -1,983 | 0.000 | +3,180 | +962 |
| HB_VWAP_k2.0_L4_NB | -1,510 | 12,157 | 266,087 | -34,227 | -2,267 | -4,457 | -2,796 | 0.000 | +2,668 | -4,277 |
| HB_OR_s30_L4 | +395 | 4,506 | 40,462 | -15,001 | -145 | -939 | -543 | 0.007 | +2,707 | -15,531 |
| HB_OR_s30_L7 | +691 | 7,886 | 70,808 | -26,252 | -253 | -1,644 | -950 | 0.007 | +697 | -27,179 |
| HB_OR_s20_L4_NB | +150 | 2,919 | 26,549 | -9,859 | -222 | -1,552 | -680 | 0.002 | +755 | -8,987 |
| HB_OR_s40_L4_NB | +574 | 5,700 | 41,334 | -19,759 | +125 | -1,587 | -927 | 0.012 | +1,177 | -15,553 |
| HB_PV_s30_L4 | +26 | 3,002 | 29,604 | -7,500 | +177 | -90 | +518 | 0.000 | +261 | -15,086 |
| HB_PV_s30_L7 | +46 | 5,253 | 51,806 | -13,126 | +309 | -157 | +906 | 0.000 | +85 | -18,706 |
| HB_PV_s20_L4_NB | +55 | 2,263 | 30,098 | -6,801 | +153 | -137 | +323 | 0.001 | +66 | -2,125 |
| HB_PV_s40_L4_NB | -264 | 3,784 | 57,797 | -9,900 | -95 | -1,019 | +502 | 0.000 | -173 | -9,186 |
| HB_REB_w15_L4 | -725 | 9,937 | 204,936 | -28,820 | -1,482 | -593 | +640 | 0.000 | -1,934 | -2,468 |
| HB_REB_w15_L7 | -1,269 | 17,390 | 358,638 | -50,436 | -2,594 | -1,038 | +1,119 | 0.000 | -1,699 | +51,167 |
| HB_REB_w30_L4 | -1,060 | 10,025 | 237,648 | -30,620 | -1,725 | -308 | +343 | 0.000 | -2,249 | -5,369 |
| HB_REB_w30_L7 | -1,855 | 17,544 | 415,885 | -53,584 | -3,019 | -539 | +600 | 0.000 | -1,830 | +44,375 |


## Cost sensitivities and gross edge (paired, WF)
Zero-cost gross edge = thr, joins, market costs and commission all 0. 1.5x / 2x = all fill costs and commission scaled; SENS2 = every stop-order fill (reversal entry in (a), re-break entry in (d), every bracket stop) a further 2.0 pts worse, because live stop exits are ~2.01 pts worse than nominal (replay 0.52). Live reality is therefore closer to the SENS2 column than to the 1x column for stop-based entries, and every cell is worse there.
| cell | gross pts/event at ZERO cost, WF | gross, holdout | net 1x pts/event (WF) | net 1.5x | net 2x | net SENS2 (all stop fills +2 pts) | mean net pts per trade | trades | exit share stop / target / closed-next-stop / session end | share of book rows lock-blocked |
|---|---|---|---|---|---|---|---|---|---|---|
| HB_REV_s20_r1.0_L4 | -0.68 | -0.82 | -2.12 | -2.99 | -3.82 | -4.72 | -2.4 | 1552 | 0.52 / 0.42 / 0.04 / 0.02 | 0.036 |
| HB_REV_s20_r1.0_L7 | -0.68 | -0.82 | -2.12 | -2.99 | -3.82 | -4.72 | -2.4 | 1552 | 0.52 / 0.42 / 0.04 / 0.02 | 0.045 |
| HB_REV_s20_r1.5_L4 | -0.63 | -0.61 | -2.40 | -3.16 | -3.98 | -5.22 | -2.8 | 1552 | 0.60 / 0.32 / 0.04 / 0.04 | 0.039 |
| HB_REV_s20_r1.5_L7 | -0.63 | -0.61 | -2.40 | -3.16 | -3.98 | -5.22 | -2.8 | 1552 | 0.60 / 0.32 / 0.04 / 0.04 | 0.054 |
| HB_REV_s30_r1.0_L4 | -0.34 | -0.03 | -2.06 | -3.00 | -3.96 | -4.99 | -2.4 | 1552 | 0.48 / 0.41 / 0.04 / 0.07 | 0.051 |
| HB_REV_s30_r1.0_L7 | -0.34 | -0.03 | -2.06 | -3.00 | -3.96 | -4.99 | -2.4 | 1552 | 0.48 / 0.41 / 0.04 / 0.07 | 0.070 |
| HB_REV_s30_r1.5_L4 | -0.57 | +0.14 | -2.37 | -3.09 | -3.98 | -5.00 | -2.7 | 1552 | 0.55 / 0.30 / 0.05 / 0.10 | 0.048 |
| HB_REV_s30_r1.5_L7 | -0.57 | +0.14 | -2.37 | -3.09 | -3.98 | -5.00 | -2.7 | 1552 | 0.55 / 0.30 / 0.05 / 0.10 | 0.065 |
| HB_REV_s40_r1.0_L4 | +0.01 | +0.61 | -1.72 | -2.44 | -3.30 | -4.04 | -1.9 | 1552 | 0.43 / 0.39 / 0.06 / 0.12 | 0.050 |
| HB_REV_s40_r1.0_L7 | +0.01 | +0.61 | -1.72 | -2.44 | -3.30 | -4.04 | -1.9 | 1552 | 0.43 / 0.39 / 0.06 / 0.12 | 0.076 |
| HB_REV_s40_r1.5_L4 | -1.00 | -0.67 | -2.63 | -3.25 | -4.13 | -4.75 | -3.1 | 1552 | 0.49 / 0.27 / 0.08 / 0.16 | 0.061 |
| HB_REV_s40_r1.5_L7 | -1.00 | -0.67 | -2.63 | -3.25 | -4.13 | -4.75 | -3.1 | 1552 | 0.49 / 0.27 / 0.08 / 0.16 | 0.083 |
| HB_VWAP_k1.5_L4 | +0.32 | -0.11 | -0.91 | -1.64 | -2.22 | -1.25 | -1.1 | 1349 | 0.25 / 0.40 / 0.23 / 0.11 | 0.050 |
| HB_VWAP_k1.5_L7 | +0.32 | -0.11 | -0.91 | -1.64 | -2.22 | -1.25 | -1.1 | 1349 | 0.25 / 0.40 / 0.23 / 0.11 | 0.079 |
| HB_VWAP_k1.25_L4_NB | +0.45 | -0.17 | -1.00 | -1.55 | -2.36 | -1.41 | -1.2 | 1349 | 0.30 / 0.39 / 0.22 / 0.10 | 0.056 |
| HB_VWAP_k2.0_L4_NB | +0.01 | -0.30 | -1.37 | -1.99 | -2.59 | -1.63 | -1.7 | 1349 | 0.19 / 0.43 / 0.25 / 0.14 | 0.063 |
| HB_OR_s30_L4 | +0.61 | +0.15 | +0.36 | +0.24 | +0.12 | +0.23 | 2.7 | 288 | 0.44 / 0.35 / 0.07 / 0.14 | 0.063 |
| HB_OR_s30_L7 | +0.61 | +0.15 | +0.36 | +0.24 | +0.12 | +0.23 | 2.7 | 288 | 0.44 / 0.35 / 0.07 / 0.14 | 0.089 |
| HB_OR_s20_L4_NB | +0.49 | +0.19 | +0.14 | -0.04 | -0.15 | -0.02 | 1.2 | 288 | 0.52 / 0.40 / 0.03 / 0.05 | 0.063 |
| HB_OR_s40_L4_NB | +0.79 | +0.29 | +0.52 | +0.40 | +0.30 | +0.41 | 3.8 | 288 | 0.38 / 0.29 / 0.14 / 0.19 | 0.092 |
| HB_PV_s30_L4 | +0.13 | +0.26 | +0.02 | -0.06 | -0.19 | -0.07 | 0.5 | 178 | 0.52 / 0.37 / 0.04 / 0.07 | 0.134 |
| HB_PV_s30_L7 | +0.13 | +0.26 | +0.02 | -0.06 | -0.19 | -0.07 | 0.5 | 178 | 0.52 / 0.37 / 0.04 / 0.07 | 0.143 |
| HB_PV_s20_L4_NB | +0.17 | +0.26 | +0.05 | -0.06 | -0.13 | -0.05 | 0.8 | 178 | 0.53 / 0.40 / 0.03 / 0.03 | 0.129 |
| HB_PV_s40_L4_NB | -0.01 | +0.18 | -0.24 | -0.35 | -0.42 | -0.33 | -2.4 | 178 | 0.51 / 0.31 / 0.08 / 0.10 | 0.143 |
| HB_REB_w15_L4 | +0.26 | -0.33 | -0.66 | -1.23 | -1.74 | -1.96 | -1.2 | 911 | 0.29 / 0.18 / 0.32 / 0.22 | 0.062 |
| HB_REB_w15_L7 | +0.26 | -0.33 | -0.66 | -1.23 | -1.74 | -1.96 | -1.2 | 911 | 0.29 / 0.18 / 0.32 / 0.22 | 0.076 |
| HB_REB_w30_L4 | +0.03 | -0.44 | -0.96 | -1.56 | -2.09 | -2.32 | -1.7 | 977 | 0.29 / 0.18 / 0.32 / 0.21 | 0.067 |
| HB_REB_w30_L7 | +0.03 | -0.44 | -0.96 | -1.56 | -2.09 | -2.32 | -1.7 | 977 | 0.29 / 0.18 / 0.32 / 0.21 | 0.081 |


## Placebo (500 random event sets of the same size and session mix; same bracket on random stop-times)
| cell | placebo rank | candidate sum of net pts (WF) | placebo mean | placebo SD | placebo 5% / 95% |
|---|---|---|---|---|---|
| HB_REV_s20_r1.0_L4 | 0.01 | -4,141 | -2,445 | 733 | -3,586 / -1,218 |
| HB_REV_s20_r1.0_L7 | 0.01 | -4,141 | -2,445 | 733 | -3,586 / -1,218 |
| HB_REV_s20_r1.5_L4 | 0.00 | -4,690 | -2,465 | 847 | -3,778 / -1,000 |
| HB_REV_s20_r1.5_L7 | 0.00 | -4,690 | -2,465 | 847 | -3,778 / -1,000 |
| HB_REV_s30_r1.0_L4 | 0.03 | -4,036 | -2,290 | 1,004 | -3,900 / -732 |
| HB_REV_s30_r1.0_L7 | 0.03 | -4,036 | -2,290 | 1,004 | -3,900 / -732 |
| HB_REV_s30_r1.5_L4 | 0.01 | -4,629 | -2,265 | 1,141 | -4,066 / -415 |
| HB_REV_s30_r1.5_L7 | 0.01 | -4,629 | -2,265 | 1,141 | -4,066 / -415 |
| HB_REV_s40_r1.0_L4 | 0.15 | -3,367 | -2,065 | 1,239 | -4,220 / -123 |
| HB_REV_s40_r1.0_L7 | 0.15 | -3,367 | -2,065 | 1,239 | -4,220 / -123 |
| HB_REV_s40_r1.5_L4 | 0.01 | -5,141 | -2,054 | 1,479 | -4,573 / +239 |
| HB_REV_s40_r1.5_L7 | 0.01 | -5,141 | -2,054 | 1,479 | -4,573 / +239 |
| HB_VWAP_k1.5_L4 | 0.70 | -1,774 | -2,302 | 1,118 | -3,985 / -390 |
| HB_VWAP_k1.5_L7 | 0.70 | -1,774 | -2,302 | 1,118 | -3,985 / -390 |
| HB_VWAP_k1.25_L4_NB | 0.59 | -1,960 | -2,200 | 1,053 | -3,813 / -294 |
| HB_VWAP_k2.0_L4_NB | 0.46 | -2,680 | -2,504 | 1,219 | -4,312 / -471 |
| HB_OR_s30_L4 | 0.98 | +700 | -337 | 512 | -1,165 / +505 |
| HB_OR_s30_L7 | 0.98 | +700 | -337 | 512 | -1,165 / +505 |
| HB_OR_s20_L4_NB | 0.97 | +265 | -422 | 356 | -971 / +175 |
| HB_OR_s40_L4_NB | 0.97 | +1,018 | -283 | 665 | -1,345 / +877 |
| HB_PV_s30_L4 | 0.70 | +46 | -175 | 438 | -919 / +540 |
| HB_PV_s30_L7 | 0.70 | +46 | -175 | 438 | -919 / +540 |
| HB_PV_s20_L4_NB | 0.86 | +97 | -209 | 302 | -738 / +260 |
| HB_PV_s40_L4_NB | 0.32 | -468 | -264 | 562 | -1,198 / +614 |
| HB_REB_w15_L4 | 0.55 | -1,287 | -1,529 | 1,561 | -4,039 / +1,126 |
| HB_REB_w15_L7 | 0.55 | -1,287 | -1,529 | 1,561 | -4,039 / +1,126 |
| HB_REB_w30_L4 | 0.44 | -1,882 | -1,645 | 1,625 | -4,404 / +1,127 |
| HB_REB_w30_L7 | 0.44 | -1,882 | -1,645 | 1,625 | -4,404 / +1,127 |

Rank = share of placebo sums BELOW the cell. Near 0: stop-out timing is worse than random timing; near 1: better.

## Long / short, ST / HM, session decomposition (WF; contribution in pts per ALL events; lots-7 cells)
Long/short = the book's trade side; after_long_stop / after_short_stop = split by the side of the stopped D2 trade.
| cell | long: trades / contrib pts per event / mean pts per trade | short: trades / contrib pts per event / mean pts per trade | ST: trades / contrib pts per event / mean pts per trade | HM: trades / contrib pts per event / mean pts per trade | ASIA: trades / contrib pts per event / mean pts per trade | LONDON: trades / contrib pts per event / mean pts per trade | NY: trades / contrib pts per event / mean pts per trade | after_long_stop: trades / contrib pts per event / mean pts per trade | after_short_stop: trades / contrib pts per event / mean pts per trade |
|---|---|---|---|---|---|---|---|---|---|
| HB_REV_s20_r1.0_L7 | 792 / -0.93 / -2.3 | 760 / -1.18 / -3.0 | 869 / -1.06 / -2.4 | 683 / -1.06 / -3.0 | 505 / -0.41 / -1.6 | 535 / -0.81 / -3.0 | 512 / -0.90 / -3.4 | 760 / -1.18 / -3.0 | 792 / -0.93 / -2.3 |
| HB_REV_s20_r1.5_L7 | 792 / -1.00 / -2.5 | 760 / -1.40 / -3.6 | 869 / -1.29 / -2.9 | 683 / -1.10 / -3.2 | 505 / -0.31 / -1.2 | 535 / -1.03 / -3.8 | 512 / -1.05 / -4.0 | 760 / -1.40 / -3.6 | 792 / -1.00 / -2.5 |
| HB_REV_s30_r1.0_L7 | 792 / -0.85 / -2.1 | 760 / -1.22 / -3.1 | 869 / -1.42 / -3.2 | 683 / -0.64 / -1.8 | 505 / -0.05 / -0.2 | 535 / -0.99 / -3.6 | 512 / -1.02 / -3.9 | 760 / -1.22 / -3.1 | 792 / -0.85 / -2.1 |
| HB_REV_s30_r1.5_L7 | 792 / -0.61 / -1.5 | 760 / -1.76 / -4.5 | 869 / -1.46 / -3.3 | 683 / -0.91 / -2.6 | 505 / +0.06 / +0.2 | 535 / -1.08 / -4.0 | 512 / -1.34 / -5.1 | 760 / -1.76 / -4.5 | 792 / -0.61 / -1.5 |
| HB_REV_s40_r1.0_L7 | 792 / -0.19 / -0.5 | 760 / -1.53 / -3.9 | 869 / -0.67 / -1.5 | 683 / -1.05 / -3.0 | 505 / -0.07 / -0.3 | 535 / -0.90 / -3.3 | 512 / -0.75 / -2.9 | 760 / -1.53 / -3.9 | 792 / -0.19 / -0.5 |
| HB_REV_s40_r1.5_L7 | 792 / -0.87 / -2.1 | 760 / -1.76 / -4.5 | 869 / -1.24 / -2.8 | 683 / -1.39 / -4.0 | 505 / -0.35 / -1.3 | 535 / -1.06 / -3.9 | 512 / -1.22 / -4.7 | 760 / -1.76 / -4.5 | 792 / -0.87 / -2.1 |
| HB_VWAP_k1.5_L7 | 715 / -0.59 / -1.6 | 634 / -0.32 / -1.0 | 722 / -0.02 / -0.1 | 627 / -0.88 / -2.8 | 451 / -0.89 / -3.8 | 472 / -0.02 / -0.1 | 426 / -0.01 / -0.0 | 676 / -0.39 / -1.1 | 673 / -0.51 / -1.5 |
| HB_OR_s30_L7 | 137 / +0.22 / +3.1 | 151 / +0.14 / +1.9 | 156 / +0.23 / +2.9 | 132 / +0.13 / +1.9 | 106 / +0.21 / +3.8 | 107 / -0.07 / -1.4 | 75 / +0.22 / +5.9 | 142 / +0.33 / +4.5 | 146 / +0.03 / +0.4 |
| HB_PV_s30_L7 | 83 / -0.01 / -0.3 | 95 / +0.04 / +0.7 | 106 / -0.04 / -0.8 | 72 / +0.07 / +1.8 | 31 / +0.03 / +2.2 | 55 / +0.05 / +1.9 | 92 / -0.07 / -1.4 | 89 / -0.16 / -3.6 | 89 / +0.19 / +4.1 |
| HB_REB_w15_L7 | 432 / -0.77 / -3.5 | 479 / +0.11 / +0.5 | 499 / -0.59 / -2.3 | 412 / -0.07 / -0.3 | 291 / -0.18 / -1.2 | 297 / -0.79 / -5.2 | 323 / +0.31 / +1.9 | 432 / -0.77 / -3.5 | 479 / +0.11 / +0.5 |
| HB_REB_w30_L7 | 461 / -1.02 / -4.3 | 516 / +0.06 / +0.2 | 533 / -0.77 / -2.8 | 444 / -0.20 / -0.9 | 307 / -0.06 / -0.4 | 318 / -0.91 / -5.6 | 352 / +0.01 / +0.1 | 461 / -1.02 / -4.3 | 516 / +0.06 / +0.2 |

Reversal (a) by book and session (trades / pts per event):
| cell | ST ASIA | ST LONDON | ST NY | HM ASIA | HM LONDON | HM NY |
|---|---|---|---|---|---|---|
| HB_REV_s20_r1.0_L7 | 289 / -0.14 | 289 / -0.45 | 291 / -0.48 | 216 / -0.27 | 246 / -0.36 | 221 / -0.42 |
| HB_REV_s20_r1.5_L7 | 289 / -0.01 | 289 / -0.67 | 291 / -0.61 | 216 / -0.30 | 246 / -0.36 | 221 / -0.44 |
| HB_REV_s30_r1.0_L7 | 289 / +0.00 | 289 / -0.69 | 291 / -0.74 | 216 / -0.05 | 246 / -0.31 | 221 / -0.28 |
| HB_REV_s30_r1.5_L7 | 289 / +0.11 | 289 / -0.73 | 291 / -0.84 | 216 / -0.05 | 246 / -0.36 | 221 / -0.50 |
| HB_REV_s40_r1.0_L7 | 289 / -0.01 | 289 / -0.48 | 291 / -0.19 | 216 / -0.07 | 246 / -0.42 | 221 / -0.56 |
| HB_REV_s40_r1.5_L7 | 289 / -0.12 | 289 / -0.51 | 291 / -0.61 | 216 / -0.23 | 246 / -0.56 | 221 / -0.61 |


## Verdict per cell (all three tiers; MDE next to each null)
PASS: none. CANDIDATE: none. DEAD (28):
- HB_REV_s20_r1.0_L4: effect -2.12 pts/event [-2.91, -1.35] (MDE 1.13; EFFECT LARGER than MDE, i.e. a real negative); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REV_s20_r1.0_L7: effect -2.12 pts/event [-2.91, -1.35] (MDE 1.13; EFFECT LARGER than MDE, i.e. a real negative); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REV_s20_r1.5_L4: effect -2.40 pts/event [-3.37, -1.50] (MDE 1.33; EFFECT LARGER than MDE, i.e. a real negative); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REV_s20_r1.5_L7: effect -2.40 pts/event [-3.37, -1.50] (MDE 1.33; EFFECT LARGER than MDE, i.e. a real negative); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REV_s30_r1.0_L4: effect -2.06 pts/event [-3.23, -0.97] (MDE 1.67; EFFECT LARGER than MDE, i.e. a real negative); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REV_s30_r1.0_L7: effect -2.06 pts/event [-3.23, -0.97] (MDE 1.67; EFFECT LARGER than MDE, i.e. a real negative); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REV_s30_r1.5_L4: effect -2.37 pts/event [-3.69, -1.05] (MDE 1.94; EFFECT LARGER than MDE, i.e. a real negative); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REV_s30_r1.5_L7: effect -2.37 pts/event [-3.69, -1.05] (MDE 1.94; EFFECT LARGER than MDE, i.e. a real negative); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REV_s40_r1.0_L4: effect -1.72 pts/event [-3.26, -0.18] (MDE 2.18; null: could not have seen a smaller effect than MDE); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REV_s40_r1.0_L7: effect -1.72 pts/event [-3.26, -0.18] (MDE 2.18; null: could not have seen a smaller effect than MDE); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REV_s40_r1.5_L4: effect -2.63 pts/event [-4.34, -1.01] (MDE 2.47; EFFECT LARGER than MDE, i.e. a real negative); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REV_s40_r1.5_L7: effect -2.63 pts/event [-4.34, -1.01] (MDE 2.47; EFFECT LARGER than MDE, i.e. a real negative); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_VWAP_k1.5_L4: effect -0.91 pts/event [-2.54, +0.61] (MDE 2.25; null: could not have seen a smaller effect than MDE); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign
- HB_VWAP_k1.5_L7: effect -0.91 pts/event [-2.54, +0.61] (MDE 2.25; null: could not have seen a smaller effect than MDE); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_VWAP_k1.25_L4_NB (NB): effect -1.00 pts/event [-2.61, +0.49] (MDE 2.17; null: could not have seen a smaller effect than MDE); fails: mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_VWAP_k2.0_L4_NB (NB): effect -1.37 pts/event [-3.13, +0.28] (MDE 2.49; null: could not have seen a smaller effect than MDE); fails: mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_OR_s30_L4: effect +0.36 pts/event [-0.28, +1.04] (MDE 0.97; null: could not have seen a smaller effect than MDE); fails: holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign
- HB_OR_s30_L7: effect +0.36 pts/event [-0.28, +1.04] (MDE 0.97; null: could not have seen a smaller effect than MDE); fails: holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, year_share>60%
- HB_OR_s20_L4_NB (NB): effect +0.14 pts/event [-0.30, +0.56] (MDE 0.62; null: could not have seen a smaller effect than MDE); fails: holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_OR_s40_L4_NB (NB): effect +0.52 pts/event [-0.26, +1.32] (MDE 1.15; null: could not have seen a smaller effect than MDE); fails: neighbours_agree, paired_CI_excludes0&maxDD_not_worse, year_share>60%
- HB_PV_s30_L4: effect +0.02 pts/event [-0.46, +0.58] (MDE 0.74; null: could not have seen a smaller effect than MDE); fails: placebo>=0.90, neighbours_agree, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_PV_s30_L7: effect +0.02 pts/event [-0.46, +0.58] (MDE 0.74; null: could not have seen a smaller effect than MDE); fails: placebo>=0.90, neighbours_agree, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_PV_s20_L4_NB (NB): effect +0.05 pts/event [-0.29, +0.40] (MDE 0.50; null: could not have seen a smaller effect than MDE); fails: placebo>=0.90, neighbours_agree, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_PV_s40_L4_NB (NB): effect -0.24 pts/event [-0.83, +0.46] (MDE 0.93; null: could not have seen a smaller effect than MDE); fails: mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REB_w15_L4: effect -0.66 pts/event [-2.29, +0.96] (MDE 2.33; null: could not have seen a smaller effect than MDE); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REB_w15_L7: effect -0.66 pts/event [-2.29, +0.96] (MDE 2.33; null: could not have seen a smaller effect than MDE); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REB_w30_L4: effect -0.96 pts/event [-2.68, +0.73] (MDE 2.43; null: could not have seen a smaller effect than MDE); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%
- HB_REB_w30_L7: effect -0.96 pts/event [-2.68, +0.73] (MDE 2.43; null: could not have seen a smaller effect than MDE); fails: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, 2x_cost_sign, year_share>60%

## Look-ahead audit (hb_audit.py, truncation invariance, failpred2/trunctest approach)
300 sampled WF-PRE/IS events x 11 rules, two passes (cuts 2 s..3 h; cuts 2 s..25 min after the stop fill); data, bars, prefix sums and the next-stop time after the cut replaced by NaN or noise; every entry before the cut and every trade closed before the cut must be identical: REV, VWAP, ZONE OR, ZONE PV, REBREAK w15/w30 0 mismatches in both passes; planted look-ahead positive controls caught (hindsight reversal 7 and 21; future-bar VWAP 1 and 2; hindsight re-break 5 and 15 mismatches). The planted 'OR with future bars' control produced no entry before its cut (not exercised); the real OR/PV rules had 23 and 15 entries before the cut in the short pass with 0 mismatches. Files hb/out/HB_audit.json, HB_audit_short.json.

## Rules actually used (frozen) and caveats
- Event = Set A stop exit, uncut by locks (kS = 1-s index of the stop fill re-derived with firmlib.sim_rrt; level = natural stop incl. the gap rule). Chain rule: trade closed at market at the level of the next stop-out in the session. Opposite-side filter: skip when a Set A row of the opposite side is open at the fill second (skips shown as the bracketed number in the table; 366 of 1,918 tradable REV events); the 50-contract limit never binds (max 28 Set A + 7 = 35). Session end = last bar before 15:00 ET for NY (D2 itself holds longer; conservative).
- Fills: 1-s tape, thr 0.25, stop-join 1.01, market 0.995, $4.84 RT/contract, no size credit for 4/7 lots (credit=False), engine slip not applied twice. Entries of (b), (c) are market orders in the second after the decision; (a) is a pre-placed stop-and-reverse at the D2 level (fill level -/+ 1.01); (d) is a stop order at the nominal level (filled at max(level, last print) -/+ 1.01).
- Interpretation of the directive: (a) 'reverse' = opposite to the stopped trade (continuation of the stop-run); (b), (c), (d) are the reversion bets; the prereg says so and notes that at most one family can be right. Prior-day 'value area' is computed from 1-min bar volume at the typical price (70% rule), not from tick data. The neighbour cells ((b) k=1.25/2.0, (c) stop 20/40) were added to the 22 primary cells to evaluate neighbours-agree; total 28 <= 30. QUESTION for MORNING.md: were neighbour-only cells meant to be inside the 'cells (c) <= 4' limit?
- year-share is not informative where the total gain is about 0 (values > 1); DSR column in the main table is that of the full-sequence series (dominated by Set A); the book's own DSR is in the additive table (<= 0.0x for the negative books).
- Correction to the pre-holdout text: it says 9 of 12 REV cells had a WF-PRE CI excluding zero on the negative side; all 12 did.

## Files
l2vast/struct48/prereg/HB_prereg.md (+ .sha256), autopilot/REPORT_STRUCT48_HB_PREHOLD.md, rows/HB_pre.json, rows/HB_final.json, hb/out/{HB_events.parquet,sim.pkl,pre_cells.pkl,final_cells.pkl,add_final.pkl,gross_pre.json,gross_final.json,HB_audit*.json,pre_table.md,final_table.md}, code/hb_{sim,lib,run,pre,final,audit,gross,text,report,report_final,prereg_gen,prehold_text,events}.py, ledger/trials.jsonl (HB, 28 cells), ledger/holdout_looks.jsonl (HB).
