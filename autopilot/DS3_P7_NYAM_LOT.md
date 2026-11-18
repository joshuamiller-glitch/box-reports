# DS3_P7_NYAM_LOT - P7 NY AM lots on JL3, all layers on (W-P7L, order 11-17 23:30Z)
VERDICT (data ends 2026-11-13; FIRST PASS; updated 2026-11-18 06:39Z): best L6M ulcer cell = HP (NY AM 7, only 11:00-12:00); tiers: {'L0': "NOT FINISHED (fewer than 10 valid controls in L6M/L3M: {'L6M': 0, 'L3M': 0, 'HOLD': 0})"}

Five-line summary: (1) pick window end 2026-11-13 (trailing 6M 2026-05-14..2026-11-13, 3M beside, 1M also). (2) refit date 2026-11-18, then every 2 weeks (walk-forward refit dates every 14 days from 2023-10-02). (3) data end 2026-11-13 (202611 base-lot store months via W-DATA). (4) rule: P7 NY AM lots 7 live = base 4 vs base 3 / 2 / 1 / 0 (live 5 / 4 / 2 / 0; live 3 is not reachable with x1.75) and the two halves at 7 live (HA 09:30-11:00 only, HP 11:00-12:00 only); walk-forward rule R6 = cut when trailing-6M P7 NY AM P&L is negative. (5) prior-year % vs live: see the per-year table (AMBER 15-30%, RED >30% worse on ulcer / max DD / mean).

> VALIDATION (desk standard, FIRST PASS): trials counted = 6 real engine cells + 2 walk-forward rules (levels L0/L2 and L1/L3 reported), no best-of selection beyond the per-cell table; correction = percentile among 30 persistent-draw engine controls (staged: controls run for the leading cells only) + week-clustered bootstrap (2,000) + calibrated ulcer-primary tiers (cutoffs_ulc TUNED); PBO not applicable (no fitted parameters; the cut level is a fixed table); in-sample on all 44 months, walk-forward section is the out-of-sample judge; prereg PREREG_P7L.md sha in DECISIONS.md.

Identity (TL3_P7L_ID vs TL3_EV_JL3, trade for trade): 202504: 637 trades net 41239.76 vs JL3 637 / 41239.76 -> IDENTICAL; 202610: 691 trades net 37159.82 vs JL3 691 / 37159.82 -> IDENTICAL
Months landed: L0 16/44, L2 16/44, L1 15/44, L3 15/44, HA 15/44, HP 15/44; JL3 base months 44.

## P7 NY AM in JL3 (anatomy; $4.84 RT, base lots)
| window | trades | net $ | $/wk | 09:30-11:00 n / net | 11:00-12:00 n / net |
|--|--|--|--|--|--|
| L6M | 43 | 7,195 | 274 | 23 / 3,098 | 20 / 4,097 |
| L3M | 22 | 4,282 | 326 | 10 / 948 | 12 / 3,334 |
| HOLD | 27 | 14,516 | 561 | 12 / 10,843 | 15 / 3,673 |
| PRE | 71 | -18,794 | -482 | 40 / -14,091 | 31 / -4,703 |
| X' | 89 | 10,555 | 135 | 44 / 3,754 | 45 / 6,801 |
| POOLED | 252 | 17,479 | 92 | 132 / 5,038 | 120 / 12,441 |

## Table A - every cell vs JL3 live (lots 7), all windows (ulcer first; $4.84 RT base lots; x1.75 live lots at $4.84 beside)

### L0: NY AM 0 (live 0; base 0) label BEST-AVAILABLE-NOT-PROVEN
| window | ulcer chg | mean $/wk base -> cell (x1.75 live) | max DD base -> cell | worst wk base -> cell | boot P(ulcer lower) | worse vs live (ulc/DD/mean %%) | flag |
|--|--|--|--|--|--|--|--|
| L1M | +0.4% | 8,554 -> 8,413 (14,988 -> 14,706) | -24,916 -> -24,916 | -12,597 -> -12,597 | 0.00 | +0.4 / +0.0 / +1.7 | ok |
| L3M | -3.3% | 14,008 -> 13,443 (25,234 -> 24,104) | -31,112 -> -29,256 | -15,728 -> -15,100 | 0.69 | -3.3 / -6.0 / +4.0 | ok |
| L6M | -2.3% | 19,147 -> 18,715 (35,593 -> 34,770) | -31,112 -> -29,256 | -15,728 -> -15,100 | 0.75 | -2.3 / -6.0 / +2.3 | ok |
| HOLD | -0.3% | 9,332 -> 8,770 (18,112 -> 17,035) | -83,755 -> -82,309 | -37,321 -> -35,059 | 0.45 | -0.3 / -1.7 / +6.0 | ok |
| Y2026 | +1.0% | 16,759 -> 16,186 (31,420 -> 30,326) | -58,717 -> -59,397 | -19,813 -> -21,008 | 0.34 | +1.0 / +1.2 / +3.4 | ok |

### L2: NY AM 4 live (base 2) (live 4; base 2) label BEST-AVAILABLE-NOT-PROVEN
| window | ulcer chg | mean $/wk base -> cell (x1.75 live) | max DD base -> cell | worst wk base -> cell | boot P(ulcer lower) | worse vs live (ulc/DD/mean %%) | flag |
|--|--|--|--|--|--|--|--|
| L1M | +0.0% | 8,554 -> 8,554 (14,988 -> 14,988) | -24,916 -> -24,916 | -12,597 -> -12,597 | 0.00 | +0.0 / +0.0 / +0.0 | ok |
| L3M | -1.3% | 14,008 -> 13,912 (25,234 -> 25,041) | -31,112 -> -30,185 | -15,728 -> -15,728 | 0.60 | -1.3 / -3.0 / +0.7 | ok |
| L6M | -1.0% | 19,147 -> 19,044 (35,593 -> 35,429) | -31,112 -> -30,185 | -15,728 -> -15,728 | 0.63 | -1.0 / -3.0 / +0.5 | ok |
| HOLD | -1.6% | 9,332 -> 9,229 (18,112 -> 17,952) | -83,755 -> -82,361 | -37,321 -> -35,927 | 0.64 | -1.6 / -1.7 / +1.1 | ok |
| Y2026 | -0.2% | 16,759 -> 16,623 (31,420 -> 31,200) | -58,717 -> -58,717 | -19,813 -> -19,813 | 0.72 | -0.2 / +0.0 / +0.8 | ok |

### L1: NY AM 2 live (base 1) (live 2; base 1) label BEST-AVAILABLE-NOT-PROVEN
| window | ulcer chg | mean $/wk base -> cell (x1.75 live) | max DD base -> cell | worst wk base -> cell | boot P(ulcer lower) | worse vs live (ulc/DD/mean %%) | flag |
|--|--|--|--|--|--|--|--|
| L1M | +0.0% | 8,554 -> 8,554 (14,988 -> 14,988) | -24,916 -> -24,916 | -12,597 -> -12,597 | 0.00 | +0.0 / +0.0 / +0.0 | ok |
| L3M | -1.3% | 14,008 -> 13,912 (25,234 -> 25,041) | -31,112 -> -30,185 | -15,728 -> -15,728 | 0.60 | -1.3 / -3.0 / +0.7 | ok |
| L6M | -1.0% | 19,147 -> 19,026 (35,593 -> 35,393) | -31,112 -> -30,185 | -15,728 -> -15,728 | 0.64 | -1.0 / -3.0 / +0.6 | ok |
| HOLD | -1.6% | 9,332 -> 9,139 (18,112 -> 17,773) | -83,755 -> -82,361 | -37,321 -> -35,927 | 0.65 | -1.6 / -1.7 / +2.1 | ok |
| Y2026 | -0.2% | 16,759 -> 16,562 (31,420 -> 31,077) | -58,717 -> -58,717 | -19,813 -> -19,813 | 0.72 | -0.2 / +0.0 / +1.2 | ok |

### L3: NY AM 5 live (base 3) (live 5; base 3) label BEST-AVAILABLE-NOT-PROVEN
| window | ulcer chg | mean $/wk base -> cell (x1.75 live) | max DD base -> cell | worst wk base -> cell | boot P(ulcer lower) | worse vs live (ulc/DD/mean %%) | flag |
|--|--|--|--|--|--|--|--|
| L1M | +0.0% | 8,554 -> 8,554 (14,988 -> 14,988) | -24,916 -> -24,916 | -12,597 -> -12,597 | 0.00 | +0.0 / +0.0 / +0.0 | ok |
| L3M | +0.0% | 14,008 -> 14,008 (25,234 -> 25,234) | -31,112 -> -31,112 | -15,728 -> -15,728 | 0.00 | +0.0 / +0.0 / +0.0 | ok |
| L6M | +0.0% | 19,147 -> 19,103 (35,593 -> 35,506) | -31,112 -> -31,112 | -15,728 -> -15,728 | 0.01 | +0.0 / +0.0 / +0.2 | ok |
| HOLD | +0.0% | 9,332 -> 9,285 (18,112 -> 18,019) | -83,755 -> -83,755 | -37,321 -> -37,321 | 0.03 | +0.0 / +0.0 / +0.5 | ok |
| Y2026 | +0.0% | 16,759 -> 16,707 (31,420 -> 31,317) | -58,717 -> -58,717 | -19,813 -> -19,813 | 0.04 | +0.0 / +0.0 / +0.3 | ok |

### HA: NY AM 7, only 09:30-11:00 (live 7; base 4) label BEST-AVAILABLE-NOT-PROVEN
| window | ulcer chg | mean $/wk base -> cell (x1.75 live) | max DD base -> cell | worst wk base -> cell | boot P(ulcer lower) | worse vs live (ulc/DD/mean %%) | flag |
|--|--|--|--|--|--|--|--|
| L1M | +0.4% | 8,554 -> 8,413 (14,988 -> 14,706) | -24,916 -> -24,916 | -12,597 -> -12,597 | 0.00 | +0.4 / +0.0 / +1.7 | ok |
| L3M | +0.4% | 14,008 -> 13,505 (25,234 -> 24,228) | -31,112 -> -31,112 | -15,728 -> -15,100 | 0.48 | +0.4 / +0.0 / +3.6 | ok |
| L6M | +0.3% | 19,147 -> 18,874 (35,593 -> 35,047) | -31,112 -> -31,112 | -15,728 -> -15,100 | 0.49 | +0.3 / +0.0 / +1.4 | ok |
| HOLD | -1.7% | 9,332 -> 9,190 (18,112 -> 17,828) | -83,755 -> -81,245 | -37,321 -> -36,295 | 0.36 | -1.7 / -3.0 / +1.5 | ok |
| Y2026 | +1.4% | 16,759 -> 16,457 (31,420 -> 30,816) | -58,717 -> -59,397 | -19,813 -> -21,008 | 0.13 | +1.4 / +1.2 / +1.8 | ok |

### HP: NY AM 7, only 11:00-12:00 (live 7; base 4) label BEST-AVAILABLE-NOT-PROVEN
| window | ulcer chg | mean $/wk base -> cell (x1.75 live) | max DD base -> cell | worst wk base -> cell | boot P(ulcer lower) | worse vs live (ulc/DD/mean %%) | flag |
|--|--|--|--|--|--|--|--|
| L1M | +0.0% | 8,554 -> 8,554 (14,988 -> 14,988) | -24,916 -> -24,916 | -12,597 -> -12,597 | 0.00 | +0.0 / +0.0 / +0.0 | ok |
| L3M | -3.0% | 14,008 -> 13,577 (25,234 -> 24,371) | -31,112 -> -29,256 | -15,728 -> -15,728 | 0.57 | -3.0 / -6.0 / +3.1 | ok |
| L6M | -2.3% | 19,147 -> 18,817 (35,593 -> 34,999) | -31,112 -> -29,256 | -15,728 -> -15,728 | 0.65 | -2.3 / -6.0 / +1.7 | ok |
| HOLD | +2.2% | 9,332 -> 9,027 (18,112 -> 17,459) | -83,755 -> -85,435 | -37,321 -> -36,085 | 0.54 | +2.2 / +2.0 / +3.3 | ok |
| Y2026 | -0.4% | 16,759 -> 16,454 (31,420 -> 30,825) | -58,717 -> -58,712 | -19,813 -> -19,813 | 0.73 | -0.4 / -0.0 / +1.8 | ok |

## Table B - freed-book effects (net $ change vs JL3, base lots $1.18, by book; P7 NY AM = own cell, others = what the freed stack room did)
| cell | window | P7 NY AM | P7 other sessions | K7 | M7 | U7 | H7 | A7 | O7 | stack |
|--|--|--|--|--|--|--|--|--|--|--|
| L0 | L6M | -7,386 | -1,224 | -3,106 | 172 | 0 | 0 | 0 | 0 | -11,545 |
| L0 | HOLD | -14,637 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | -14,637 |
| L2 | L6M | -1,846 | 0 | -887 | 0 | 0 | 0 | 0 | 0 | -2,734 |
| L2 | HOLD | -3,406 | 0 | 0 | 717 | 0 | 0 | 0 | 0 | -2,689 |
| L1 | L6M | -2,323 | 0 | -887 | 0 | 0 | 0 | 0 | 0 | -3,210 |
| L1 | HOLD | -5,719 | 0 | 0 | 717 | 0 | 0 | 0 | 0 | -5,001 |
| L3 | L6M | -1,159 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | -1,159 |
| L3 | HOLD | -1,204 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | -1,204 |
| HA | L6M | -4,178 | 0 | -3,076 | 0 | 0 | 0 | 0 | 0 | -7,254 |
| HA | HOLD | -3,732 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | -3,732 |
| HP | L6M | -4,919 | 0 | -4,016 | 172 | 0 | 0 | 0 | 0 | -8,763 |
| HP | HOLD | -7,931 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | -7,931 |

## Table C - rolling 2-week refit walk-forward of the lot choice (rule R6: cut P7 NY AM to the cell level when trailing-6M P7 NY AM P&L (JL3, base lots) < 0, else live 7; arithmetic splice of the cell and JL3 daily P&L, no boundary path effects; $4.84 base lots)
walk-forward not run yet (needs the cell for all months).

## Table D - persistent random controls and calibrated tier

L0: tier **NOT FINISHED (fewer than 10 valid controls in L6M/L3M: {'L6M': 0, 'L3M': 0, 'HOLD': 0})**; draws landed 0, valid 0; p 0.0611 (target removed share 0.0611, generation 0)
| window | valid controls (landed) | pct ulcer | pct mean | pct max DD | pct worst week |
|--|--|--|--|--|--|
| L6M | 0 (0) | nan | nan | nan | nan |
| L3M | 0 (0) | nan | nan | nan | nan |
| HOLD | 0 (0) | nan | nan | nan | nan |

## Bar swap vs lot cut (W-SWB, 36 TL3_SWB sets for P7 NY AM)
Swap page line: - Engine: hook identity (live 1-min bar through the hook = JL3 trade for trade): P7 NY AM and O7 exact on 202504 and 202610 (hook v1); P7 London and H7 NY AM exact on 202504 with hook v2 (swb_inject2; 202610 and the other cells in section 4 as they land); sets TL3_SWB_* queued per cell: top 5 naked (6M), top 5 naked (3M), best row per bar family, 30 random-clock controls on the primary pick; verdi | the lot-cut result is in Table A; compare on ulcer first.

Live DS7 need: panel setting only (P7 lots by session 12,7,0,7,0,0 -> 12,7,0,N,0,0 with N = live lots in the table); the half-session variants need a time-of-day lot window (new code: lots 0 for P7 in 09:30-11:00 or 11:00-12:00).
