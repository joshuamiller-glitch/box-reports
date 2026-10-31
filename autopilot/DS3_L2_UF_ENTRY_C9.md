# DS3_L2_UF_ENTRY_C9 - L2-UNTIL-FOUND cycle 9, ENTRY: the add decision per book at integer live lots (agent UF-ENTRY, 2026-10-31)
Research only; UNTOUCHED never read; no live data. Prereg autopilot/UF_ENTRY_C9_prereg.md sha256 342eab1c38f2ca111bd103c71cb94bd55f4c133ad40199d49bccfb6812ced415 (before any cycle-9 statistic); PRE+X' selection out/uf/entry_c9/pre_sel.json (copy autopilot/UF_ENTRY_C9_PRESEL.json) sha256 e861cb4912a52c8277ef08becf7326d413a4334046fd41c8735ded49e800d0a7 logged before the one recent look. Each option is the split at integer lots (F = (L - a)/L, a add contracts, 1-of-8 gate + veto as live, dip X 3/5/8) with the cycle-7 modelled add slippage (1-lot slices @2 s, d=2 s; x1, x1.8 = live-exit calibration; x0 = sim); score = lock-engine P&L of THAT book alone (research lots, c=1) minus the plain-market-entry P&L of the same book. Deviations from the prereg (stated in DECISIONS.md): 58 option cells instead of 55 (S6 a up to 5); the K6 random-assignment placebo is replaced by the day-block bootstrap MDE (the add is a deterministic rule on every signal); for HM the 'no add' row is the whole HM book at plain market.

## Page 1 - per-book recommendation table (N basis, modelled slippage; 'default' = the live integer 70/30 at 3 pt)
| book (live lots) | split cells (contracts market/add) | no add (plain market) | live default option | PRE-selected option | decision |
|--|--|--|--|--|--|
| H6 (4) | 3/1 (default), selected 4/0 X=3 | 0 vs market | N x1: L6M +0.8k, HOLD +1.4k, PRE +0.2k; x1.8: L6M +0.9k, HOLD +1.5k | no add selected | **NEUTRAL (no add option eligible on PRE+X; default effect inside MDE)** |
| H6 NY-AM (2) | 1/1 (default), selected 2/0 X=3 | 0 vs market | N x1: L6M +0.8k, HOLD +1.4k, PRE +0.2k; x1.8: L6M +0.9k, HOLD +1.5k | no add selected | **NEUTRAL (no add option eligible on PRE+X; default effect inside MDE)** |
| K6 (2 lots) | 1/1 (default), selected 2/0 X=3 | 0 vs market | N x1: L6M -3.0k, HOLD -2.4k, PRE -3.1k; x1.8: L6M -3.4k, HOLD -2.8k | no add selected | **DROP THE ADD (plain market)** |
| P6 (7) | 5/2 (default), selected 5/2 X=3 | 0 vs market | N x1: L6M +0.8k, HOLD +0.2k, PRE +1.5k; x1.8: L6M +0.2k, HOLD -0.0k | 5/2 X=3: L6M +0.8k, HOLD +0.2k, PRE +1.5k, X' +2.7k | **NEUTRAL** |
| U6 (4) | 3/1 (default), selected 4/0 X=3 | 0 vs market | N x1: L6M +3.0k, HOLD +3.3k, PRE +0.2k; x1.8: L6M +2.9k, HOLD +3.2k | no add selected | **NEUTRAL (no add option eligible on PRE+X; default effect inside MDE)** |
| S6 (research 10) | 7/3 (default), selected 9/1 X=5 | 0 vs market | N x1: L6M +3.3k, HOLD +4.1k, PRE -0.1k; x1.8: L6M +5.2k, HOLD +5.6k | 9/1 X=5: L6M +7.2k, HOLD +6.6k, PRE +1.6k, X' +0.7k | **KEEP THE ADD** |
| W6 (research 7) | 5/2 (default), selected 4/3 X=5 | 0 vs market | N x1: L6M +3.7k, HOLD +3.8k, PRE +1.7k; x1.8: L6M +4.0k, HOLD +3.9k | 4/3 X=5: L6M +1.8k, HOLD +3.3k, PRE +3.2k, X' +2.4k | **KEEP THE ADD** |

Decision rule (prereg): KEEP if the PRE-selected option and the default are >= 0 vs market in L6M and HOLD at x1 and x1.8 and the default beats no-add in SEL; DROP if no add beats the default in SEL and the default is < 0 in L6M and HOLD; else NEUTRAL.
Plain sentences: H6 (4): NEUTRAL (no add option eligible on PRE+X; default effect inside MDE); H6 NY-AM (2): NEUTRAL (no add option eligible on PRE+X; default effect inside MDE); K6 (2 lots): DROP THE ADD (plain market); P6 (7): NEUTRAL; U6 (4): NEUTRAL (no add option eligible on PRE+X; default effect inside MDE); S6 (research 10): KEEP THE ADD; W6 (research 7): KEEP THE ADD.

## 1. Option tables

### H6 (4) - all options, delta vs the plain-market book P&L (\$/wk, research lots, N basis, c=1; MDE in parentheses)
| option (market/add, dip X) | cost | 2026 | L6M | HOLD | PRE | X' | SEL t |
|--|--|--|--|--|--|--|--|
| 3/1 @ 3 (default) | x0 | +6.2k (22.9k) | +2.2k (7.4k) | +2.6k (6.8k) | +0.8k (5.0k) | -0.0k (3.5k) |  |
| 3/1 @ 3 (default) | x1 | +3.8k (24.2k) | +0.8k (7.4k) | +1.4k (6.9k) | +0.2k (4.8k) | -0.1k (3.5k) | 0.05475276394521007 |
| 3/1 @ 3 (default) | x1.8 | +3.6k (24.1k) | +0.9k (7.7k) | +1.5k (7.1k) | +0.4k (5.0k) | -0.1k (3.5k) |  |
| 3/1 @ 3 | LIVE-CAL x1.8 | +5.6k (23.0k) | +1.7k (7.4k) | +2.2k (6.9k) | -0.5k (5.6k) | -0.2k (3.5k) | |
| 3/1 @ 3 | N x1, ONE 1-lot order instead of 1-lot slices | +3.8k (24.2k) | +0.8k (7.4k) | +1.4k (6.9k) | +0.2k (4.8k) | -0.1k (3.5k) | |
| 3/1 @ 5 | x1 | +8.2k (25.2k) | +1.2k (7.9k) | +2.0k (7.3k) | -1.5k (5.8k) | +1.2k (4.9k) | -0.36817303088555864 |
| 3/1 @ 5 | x1.8 | +7.6k (25.1k) | +1.4k (8.0k) | +2.1k (7.4k) | -2.6k (5.3k) | +1.1k (4.9k) |  |
| 3/1 @ 8 | x1 | +19.6k (30.8k) | +3.3k (9.5k) | +3.0k (9.1k) | -3.0k (6.9k) | -0.2k (6.0k) | -1.1396228915309548 |
| 3/1 @ 8 | x1.8 | +19.5k (31.0k) | +2.6k (9.7k) | +2.4k (9.3k) | -3.3k (7.0k) | +0.6k (7.0k) |  |
| 2/2 @ 3 | x1 | +13.3k (35.2k) | +2.9k (10.2k) | +3.3k (9.1k) | -0.3k (6.1k) | +0.6k (4.4k) | -0.0038778604431574013 |
| 2/2 @ 3 | x1.8 | +13.4k (35.3k) | +2.8k (10.1k) | +3.1k (9.1k) | -1.0k (6.1k) | +0.4k (4.5k) |  |
| 2/2 @ 5 | x1 | +17.6k (34.4k) | +0.3k (11.8k) | +1.3k (10.6k) | -2.4k (7.9k) | +0.1k (6.5k) | -0.7398423472858072 |
| 2/2 @ 5 | x1.8 | +19.3k (38.5k) | +0.6k (12.6k) | +1.5k (11.2k) | -3.4k (8.0k) | +1.2k (7.2k) |  |
| 2/2 @ 8 | x1 | +28.8k (35.5k) | +0.8k (13.1k) | +0.3k (11.8k) | -3.3k (9.4k) | +2.3k (7.4k) | -0.5314765533141553 |
| 2/2 @ 8 | x1.8 | +34.0k (35.0k) | +1.4k (13.9k) | +0.9k (12.4k) | -4.4k (9.7k) | +3.0k (8.3k) |  |

### H6 NY-AM (2) - all options, delta vs the plain-market book P&L (\$/wk, research lots, N basis, c=1; MDE in parentheses)
| option (market/add, dip X) | cost | 2026 | L6M | HOLD | PRE | X' | SEL t |
|--|--|--|--|--|--|--|--|
| 1/1 @ 3 (default) | x0 | +6.2k (22.9k) | +2.2k (7.4k) | +2.6k (6.8k) | +0.8k (5.0k) | -0.0k (3.5k) |  |
| 1/1 @ 3 (default) | x1 | +3.8k (24.2k) | +0.8k (7.4k) | +1.4k (6.9k) | +0.2k (4.8k) | -0.1k (3.5k) | 0.05475276394521007 |
| 1/1 @ 3 (default) | x1.8 | +3.6k (24.1k) | +0.9k (7.7k) | +1.5k (7.1k) | +0.4k (5.0k) | -0.1k (3.5k) |  |
| 1/1 @ 3 | LIVE-CAL x1.8 | +5.6k (23.0k) | +1.7k (7.4k) | +2.2k (6.9k) | -0.5k (5.6k) | -0.2k (3.5k) | |
| 1/1 @ 3 | N x1, ONE 1-lot order instead of 1-lot slices | +3.8k (24.2k) | +0.8k (7.4k) | +1.4k (6.9k) | +0.2k (4.8k) | -0.1k (3.5k) | |
| 1/1 @ 5 | x1 | +8.2k (25.2k) | +1.2k (7.9k) | +2.0k (7.3k) | -1.5k (5.8k) | +1.2k (4.9k) | -0.36817303088555864 |
| 1/1 @ 5 | x1.8 | +7.6k (25.1k) | +1.4k (8.0k) | +2.1k (7.4k) | -2.6k (5.3k) | +1.1k (4.9k) |  |
| 1/1 @ 8 | x1 | +19.6k (30.8k) | +3.3k (9.5k) | +3.0k (9.1k) | -3.0k (6.9k) | -0.2k (6.0k) | -1.1396228915309548 |
| 1/1 @ 8 | x1.8 | +19.5k (31.0k) | +2.6k (9.7k) | +2.4k (9.3k) | -3.3k (7.0k) | +0.6k (7.0k) |  |

### K6 (2 lots) - all options, delta vs the plain-market book P&L (\$/wk, research lots, N basis, c=1; MDE in parentheses)
| option (market/add, dip X) | cost | 2026 | L6M | HOLD | PRE | X' | SEL t |
|--|--|--|--|--|--|--|--|
| 1/1 @ 3 (default) | x0 | -1.1k (17.8k) | -1.8k (8.0k) | -1.2k (7.1k) | -3.1k (3.7k) | +0.8k (3.9k) |  |
| 1/1 @ 3 (default) | x1 | -1.5k (18.0k) | -3.0k (7.6k) | -2.4k (6.8k) | -3.1k (3.8k) | +1.3k (3.8k) | -1.486783307750399 |
| 1/1 @ 3 (default) | x1.8 | -1.9k (18.1k) | -3.4k (7.6k) | -2.8k (6.8k) | -2.9k (3.8k) | +1.5k (4.0k) |  |
| 1/1 @ 3 | LIVE-CAL x1.8 | -1.1k (15.2k) | -2.7k (7.2k) | -2.1k (6.4k) | -3.3k (3.8k) | +1.2k (3.6k) | |
| 1/1 @ 3 | N x1, ONE 1-lot order instead of 1-lot slices | -1.5k (18.0k) | -3.0k (7.6k) | -2.4k (6.8k) | -3.1k (3.8k) | +1.3k (3.8k) | |
| 1/1 @ 5 | x1 | +1.6k (23.1k) | -2.2k (8.9k) | -1.0k (8.1k) | -3.0k (4.3k) | +2.1k (4.7k) | -0.9583539888529542 |
| 1/1 @ 5 | x1.8 | +1.9k (21.3k) | -2.3k (8.8k) | -1.5k (7.9k) | -2.8k (4.5k) | +1.8k (4.4k) |  |
| 1/1 @ 8 | x1 | +1.0k (25.1k) | -1.8k (9.8k) | -1.6k (8.8k) | -1.9k (5.0k) | +2.1k (5.2k) | -0.33306760242087335 |
| 1/1 @ 8 | x1.8 | -1.4k (21.5k) | -3.3k (9.8k) | -2.9k (8.9k) | -3.3k (5.2k) | +2.3k (5.1k) |  |

### P6 (7) - all options, delta vs the plain-market book P&L (\$/wk, research lots, N basis, c=1; MDE in parentheses)
| option (market/add, dip X) | cost | 2026 | L6M | HOLD | PRE | X' | SEL t |
|--|--|--|--|--|--|--|--|
| 6/1 @ 3 | x1 | +6.0k (11.8k) | +3.4k (4.9k) | +2.9k (4.4k) | +1.2k (2.3k) | +0.6k (2.1k) | 1.6833228751320337 |
| 6/1 @ 3 | x1.8 | +5.9k (11.8k) | +3.4k (4.9k) | +2.9k (4.3k) | +0.8k (2.2k) | +0.6k (2.1k) |  |
| 6/1 @ 5 | x1 | -2.9k (13.6k) | +1.0k (5.6k) | +0.3k (5.2k) | -0.4k (2.7k) | +2.6k (3.0k) | 0.9347998800844809 |
| 6/1 @ 5 | x1.8 | -2.9k (13.6k) | +1.0k (5.5k) | +0.3k (5.2k) | -0.8k (2.6k) | +2.6k (3.0k) |  |
| 6/1 @ 8 | x1 | +5.2k (20.8k) | +3.1k (6.2k) | +2.6k (5.5k) | -0.1k (3.5k) | +3.1k (3.4k) | 1.2122784983130257 |
| 6/1 @ 8 | x1.8 | +5.2k (20.9k) | +3.0k (6.2k) | +2.4k (5.5k) | +0.0k (3.5k) | +3.1k (3.4k) |  |
| 5/2 @ 3 (default) (PRE-selected) | x0 | -1.0k (16.2k) | +0.9k (6.0k) | +0.3k (5.6k) | +1.3k (3.2k) | +2.7k (2.9k) |  |
| 5/2 @ 3 (default) (PRE-selected) | x1 | -3.2k (23.5k) | +0.8k (6.9k) | +0.2k (6.3k) | +1.5k (3.3k) | +2.7k (2.9k) | 2.3195728066837846 |
| 5/2 @ 3 (default) (PRE-selected) | x1.8 | -4.1k (23.0k) | +0.2k (6.4k) | -0.0k (5.6k) | +1.6k (3.3k) | +2.5k (2.9k) |  |
| 5/2 @ 3 | LIVE-CAL x1.8 | -6.8k (17.2k) | -0.3k (5.8k) | -0.5k (5.1k) | +1.1k (3.2k) | +3.1k (3.0k) | |
| 5/2 @ 3 | N x1, ONE 2-lot order instead of 1-lot slices | -4.3k (21.8k) | +0.6k (6.7k) | -0.0k (6.1k) | +1.3k (3.3k) | +2.7k (2.9k) | |
| 5/2 @ 5 | x1 | +0.8k (17.0k) | +1.0k (5.9k) | +0.2k (5.6k) | -0.4k (3.5k) | +2.9k (3.2k) | 0.8938083223197959 |
| 5/2 @ 5 | x1.8 | +0.7k (17.0k) | +0.7k (5.9k) | -0.3k (5.6k) | +0.2k (3.5k) | +2.4k (2.9k) |  |
| 5/2 @ 8 | x1 | +0.7k (16.8k) | +1.3k (6.5k) | +0.8k (5.8k) | -2.2k (4.5k) | +3.8k (3.7k) | 0.009330195669641782 |
| 5/2 @ 8 | x1.8 | +0.6k (16.8k) | +1.9k (6.8k) | +1.0k (6.1k) | -2.2k (4.6k) | +4.1k (4.0k) |  |
| 4/3 @ 3 | x1 | +4.2k (32.8k) | +2.5k (8.4k) | +1.6k (7.6k) | +0.3k (3.5k) | +2.2k (2.9k) | 1.1759641646040502 |
| 4/3 @ 3 | x1.8 | +0.5k (29.6k) | +1.5k (7.9k) | +0.6k (7.2k) | +0.5k (3.6k) | +2.1k (3.0k) |  |
| 4/3 @ 5 | x1 | -4.5k (21.7k) | -0.0k (7.0k) | -0.9k (6.2k) | -0.8k (3.9k) | +3.8k (4.1k) | 0.8962934916518496 |
| 4/3 @ 5 | x1.8 | -4.7k (21.3k) | -0.8k (7.1k) | -1.8k (6.2k) | -1.2k (3.9k) | +4.4k (4.7k) |  |
| 4/3 @ 8 | x1 | -6.9k (26.2k) | +1.8k (9.2k) | +0.4k (8.0k) | -2.3k (4.9k) | +4.8k (5.1k) | 0.267336385175984 |
| 4/3 @ 8 | x1.8 | -7.0k (26.2k) | +1.3k (9.0k) | +0.2k (7.9k) | -2.4k (4.6k) | +4.5k (5.2k) |  |

### U6 (4) - all options, delta vs the plain-market book P&L (\$/wk, research lots, N basis, c=1; MDE in parentheses)
| option (market/add, dip X) | cost | 2026 | L6M | HOLD | PRE | X' | SEL t |
|--|--|--|--|--|--|--|--|
| 3/1 @ 3 (default) | x0 | +1.8k (7.3k) | +3.0k (4.7k) | +3.4k (4.6k) | +0.4k (1.7k) | -0.9k (1.3k) |  |
| 3/1 @ 3 (default) | x1 | +1.8k (7.3k) | +3.0k (4.7k) | +3.3k (4.6k) | +0.2k (1.7k) | -0.9k (1.3k) | -0.44226952824091836 |
| 3/1 @ 3 (default) | x1.8 | +1.7k (7.4k) | +2.9k (4.9k) | +3.2k (4.7k) | +0.2k (1.7k) | -0.9k (1.3k) |  |
| 3/1 @ 3 | LIVE-CAL x1.8 | +1.7k (7.5k) | +2.9k (4.7k) | +3.3k (4.6k) | +0.2k (1.7k) | -0.9k (1.3k) | |
| 3/1 @ 3 | N x1, ONE 1-lot order instead of 1-lot slices | +1.8k (7.3k) | +3.0k (4.7k) | +3.3k (4.6k) | +0.2k (1.7k) | -0.9k (1.3k) | |
| 3/1 @ 5 | x1 | +0.5k (6.8k) | +4.1k (5.5k) | +4.0k (4.9k) | -1.0k (2.1k) | -0.5k (1.9k) | -1.5473957433351273 |
| 3/1 @ 5 | x1.8 | +0.4k (6.8k) | +4.0k (5.7k) | +3.9k (5.0k) | -0.9k (2.0k) | -0.5k (1.9k) |  |
| 3/1 @ 8 | x1 | +6.3k (12.2k) | +5.7k (5.6k) | +4.9k (5.1k) | -0.5k (2.7k) | -1.1k (1.9k) | -1.149102391824568 |
| 3/1 @ 8 | x1.8 | +6.2k (12.2k) | +5.3k (5.7k) | +4.3k (5.3k) | -0.5k (2.6k) | -1.3k (2.0k) |  |
| 2/2 @ 3 | x1 | +0.5k (6.8k) | +2.5k (5.0k) | +2.8k (4.8k) | -0.6k (2.6k) | -0.5k (2.6k) | -0.8055970931319011 |
| 2/2 @ 3 | x1.8 | +1.1k (7.6k) | +2.6k (5.1k) | +2.8k (4.9k) | -0.6k (2.6k) | -0.6k (2.7k) |  |
| 2/2 @ 5 | x1 | +0.9k (10.0k) | +5.4k (6.1k) | +4.9k (5.4k) | -2.1k (2.9k) | -1.0k (2.8k) | -2.2253981518942614 |
| 2/2 @ 5 | x1.8 | +0.7k (10.3k) | +5.4k (6.1k) | +4.9k (5.4k) | -2.2k (2.9k) | -1.0k (2.8k) |  |
| 2/2 @ 8 | x1 | +3.1k (14.0k) | +4.9k (6.1k) | +3.2k (6.0k) | -2.6k (3.4k) | -0.8k (3.3k) | -2.2049950868725117 |
| 2/2 @ 8 | x1.8 | +3.0k (13.9k) | +4.7k (6.2k) | +3.1k (6.1k) | -2.8k (3.6k) | -1.3k (3.6k) |  |

### S6 (research 10) - all options, delta vs the plain-market book P&L (\$/wk, research lots, N basis, c=1; MDE in parentheses)
| option (market/add, dip X) | cost | 2026 | L6M | HOLD | PRE | X' | SEL t |
|--|--|--|--|--|--|--|--|
| 9/1 @ 3 | x1 | +14.0k (24.9k) | +5.8k (7.4k) | +4.3k (7.0k) | +0.7k (3.4k) | +0.8k (3.0k) | 0.8460553208146057 |
| 9/1 @ 3 | x1.8 | +11.9k (22.1k) | +5.0k (7.1k) | +3.5k (6.7k) | +0.4k (3.5k) | +0.8k (3.0k) |  |
| 9/1 @ 5 (PRE-selected) | x1 | +8.0k (25.5k) | +7.2k (8.4k) | +6.6k (8.5k) | +1.6k (4.0k) | +0.7k (3.6k) | 1.235314226847176 |
| 9/1 @ 5 (PRE-selected) | x1.8 | +7.9k (25.5k) | +7.1k (8.4k) | +6.5k (8.5k) | +0.9k (3.9k) | +0.7k (3.6k) |  |
| 9/1 @ 5 | LIVE-CAL x1.8 | -5.8k (8.0k) | +5.0k (7.7k) | +4.4k (8.1k) | +2.3k (4.3k) | +0.6k (3.6k) | |
| 9/1 @ 5 | N x1, ONE 1-lot order instead of 1-lot slices | +8.0k (25.5k) | +7.2k (8.4k) | +6.6k (8.5k) | +1.6k (4.0k) | +0.7k (3.6k) | |
| 9/1 @ 8 | x1 | +9.7k (23.3k) | +6.6k (8.4k) | +5.7k (8.2k) | +2.0k (5.0k) | +0.1k (5.2k) | 0.9884591473186134 |
| 9/1 @ 8 | x1.8 | +9.6k (23.2k) | +6.5k (8.4k) | +5.5k (8.2k) | +1.5k (4.8k) | +0.1k (5.2k) |  |
| 8/2 @ 3 | x1 | +14.3k (25.9k) | +5.7k (8.8k) | +5.5k (8.6k) | +1.1k (4.8k) | +1.0k (4.1k) | 0.9111609110638768 |
| 8/2 @ 3 | x1.8 | +12.2k (17.2k) | +5.3k (7.7k) | +5.1k (7.7k) | -0.1k (4.4k) | +1.0k (4.1k) |  |
| 8/2 @ 5 | x1 | +9.6k (23.4k) | +8.5k (9.7k) | +7.6k (9.4k) | +1.2k (5.0k) | +0.3k (4.3k) | 0.717654132208188 |
| 8/2 @ 5 | x1.8 | +9.7k (23.9k) | +7.7k (10.0k) | +6.9k (9.5k) | -0.1k (5.1k) | +0.3k (4.3k) |  |
| 8/2 @ 8 | x1 | +14.6k (27.4k) | +6.8k (8.9k) | +6.5k (8.5k) | +1.4k (6.2k) | -0.4k (5.8k) | 0.4454175986810683 |
| 8/2 @ 8 | x1.8 | +6.4k (21.5k) | +4.0k (8.3k) | +3.9k (8.1k) | +1.0k (6.2k) | -0.5k (5.8k) |  |
| 7/3 @ 3 (default) | x0 | +9.2k (32.0k) | +8.0k (10.3k) | +8.2k (9.7k) | +1.1k (6.3k) | +0.7k (4.6k) |  |
| 7/3 @ 3 (default) | x1 | +7.2k (23.0k) | +3.3k (8.5k) | +4.1k (8.3k) | -0.1k (6.1k) | +0.7k (4.6k) | 0.13907154385355178 |
| 7/3 @ 3 (default) | x1.8 | +16.6k (37.5k) | +5.2k (10.8k) | +5.6k (10.1k) | -1.5k (6.6k) | +1.0k (4.7k) |  |
| 7/3 @ 3 | LIVE-CAL x1.8 | +8.3k (15.0k) | +4.4k (8.0k) | +4.6k (7.9k) | -1.4k (7.0k) | +0.8k (4.5k) | |
| 7/3 @ 3 | N x1, ONE 3-lot order instead of 1-lot slices | +11.1k (22.8k) | +4.6k (8.5k) | +5.2k (8.3k) | -0.3k (6.1k) | +0.6k (4.6k) | |
| 7/3 @ 5 | x1 | +5.7k (20.6k) | +6.9k (10.4k) | +6.9k (9.7k) | +1.2k (7.1k) | +0.2k (5.3k) | 0.47877894268443116 |
| 7/3 @ 5 | x1.8 | +5.7k (21.2k) | +6.7k (10.6k) | +6.7k (9.9k) | -0.4k (7.7k) | -0.7k (5.5k) |  |
| 7/3 @ 8 | x1 | +18.1k (36.5k) | +4.2k (12.2k) | +4.1k (11.1k) | -1.5k (7.6k) | -2.8k (7.1k) | -1.0088351337662809 |
| 7/3 @ 8 | x1.8 | +17.5k (36.6k) | +3.3k (12.3k) | +3.1k (11.2k) | -2.0k (8.4k) | -2.8k (7.0k) |  |
| 6/4 @ 3 | x1 | +16.6k (46.4k) | +6.2k (12.3k) | +6.5k (11.2k) | -0.9k (7.4k) | -0.2k (5.3k) | -0.3598440479497601 |
| 6/4 @ 3 | x1.8 | +18.0k (43.9k) | +5.0k (12.0k) | +5.7k (10.9k) | +0.8k (7.6k) | -0.8k (5.5k) |  |
| 6/4 @ 5 | x1 | +3.0k (27.4k) | +4.8k (11.7k) | +5.0k (10.7k) | -1.0k (8.6k) | -3.0k (7.7k) | -0.7969239662464971 |
| 6/4 @ 5 | x1.8 | +2.7k (27.6k) | +4.0k (11.5k) | +4.1k (10.5k) | -2.2k (8.6k) | -2.2k (8.0k) |  |
| 6/4 @ 8 | x1 | +9.5k (41.4k) | +0.2k (14.1k) | +0.5k (12.7k) | -3.8k (9.6k) | -3.0k (8.8k) | -1.4405452861275656 |
| 6/4 @ 8 | x1.8 | +8.8k (41.3k) | -0.8k (14.2k) | +0.6k (12.8k) | -3.6k (9.9k) | -3.0k (9.2k) |  |
| 5/5 @ 3 | x1 | +15.9k (47.6k) | +8.2k (13.1k) | +8.1k (11.8k) | +0.8k (7.8k) | -1.7k (6.2k) | -0.05994392738591179 |
| 5/5 @ 3 | x1.8 | +25.4k (46.5k) | +8.6k (13.5k) | +8.7k (12.3k) | +0.6k (7.5k) | -2.3k (6.6k) |  |
| 5/5 @ 5 | x1 | +13.1k (36.3k) | +6.0k (13.5k) | +5.9k (12.1k) | -1.4k (9.4k) | -3.6k (8.9k) | -0.9275742451423901 |
| 5/5 @ 5 | x1.8 | +12.5k (36.3k) | +5.9k (13.1k) | +5.7k (11.8k) | -1.3k (9.4k) | -4.2k (8.9k) |  |
| 5/5 @ 8 | x1 | +7.6k (35.0k) | +0.2k (14.3k) | +1.3k (12.8k) | -3.0k (10.8k) | -4.4k (9.3k) | -1.2857391716591324 |
| 5/5 @ 8 | x1.8 | +7.0k (34.7k) | -1.3k (14.3k) | -0.3k (12.8k) | -4.6k (10.3k) | -4.8k (9.5k) |  |

### W6 (research 7) - all options, delta vs the plain-market book P&L (\$/wk, research lots, N basis, c=1; MDE in parentheses)
| option (market/add, dip X) | cost | 2026 | L6M | HOLD | PRE | X' | SEL t |
|--|--|--|--|--|--|--|--|
| 6/1 @ 3 | x1 | -0.3k (3.9k) | +1.5k (3.1k) | +1.9k (3.3k) | +1.2k (3.1k) | -1.6k (2.5k) | 0.17037686760135348 |
| 6/1 @ 3 | x1.8 | -0.4k (3.9k) | +1.8k (2.7k) | +2.1k (3.1k) | +0.7k (3.0k) | -1.6k (2.5k) |  |
| 6/1 @ 5 | x1 | +1.9k (6.4k) | +1.5k (3.8k) | +1.8k (3.8k) | +2.4k (3.6k) | -1.3k (3.1k) | 1.1253422068942394 |
| 6/1 @ 5 | x1.8 | +1.7k (6.3k) | +1.6k (3.8k) | +1.9k (3.8k) | +2.3k (3.6k) | -1.3k (3.1k) |  |
| 6/1 @ 8 | x1 | +7.5k (13.0k) | +1.7k (4.6k) | +1.8k (4.4k) | +1.5k (3.7k) | +2.0k (4.7k) | 1.6261390500414166 |
| 6/1 @ 8 | x1.8 | +7.5k (12.9k) | +1.6k (4.6k) | +1.7k (4.4k) | +0.5k (4.1k) | +2.0k (4.7k) |  |
| 5/2 @ 3 (default) | x0 | +3.0k (10.2k) | +4.1k (5.6k) | +4.1k (5.2k) | +1.6k (4.1k) | -1.7k (2.3k) |  |
| 5/2 @ 3 (default) | x1 | +2.3k (10.7k) | +3.7k (5.7k) | +3.8k (5.3k) | +1.7k (3.9k) | -1.8k (2.3k) | 0.43298778492778056 |
| 5/2 @ 3 (default) | x1.8 | +4.1k (16.4k) | +4.0k (6.2k) | +3.9k (5.7k) | +1.3k (3.6k) | -2.1k (2.6k) |  |
| 5/2 @ 3 | LIVE-CAL x1.8 | -0.5k (8.5k) | +2.4k (4.0k) | +2.6k (4.0k) | +1.5k (3.6k) | -2.3k (2.5k) | |
| 5/2 @ 3 | N x1, ONE 2-lot order instead of 1-lot slices | +2.4k (10.7k) | +3.8k (5.7k) | +3.8k (5.3k) | +1.7k (3.9k) | -1.7k (2.5k) | |
| 5/2 @ 5 | x1 | +8.5k (13.8k) | +3.4k (4.3k) | +3.9k (4.0k) | +1.4k (4.3k) | +0.2k (4.2k) | 0.8572630935519691 |
| 5/2 @ 5 | x1.8 | +7.8k (13.8k) | +3.1k (4.3k) | +3.6k (4.1k) | +1.9k (4.9k) | -0.4k (4.0k) |  |
| 5/2 @ 8 | x1 | +1.8k (15.0k) | +5.6k (6.9k) | +5.9k (6.5k) | +1.4k (5.5k) | +2.4k (5.0k) | 1.2657714364445771 |
| 5/2 @ 8 | x1.8 | +1.6k (14.7k) | +4.6k (6.7k) | +5.0k (6.4k) | +1.2k (5.4k) | +2.1k (4.9k) |  |
| 4/3 @ 3 | x1 | +5.4k (16.2k) | +5.0k (6.0k) | +4.7k (5.6k) | +1.6k (4.4k) | -0.8k (4.2k) | 0.6324035338896989 |
| 4/3 @ 3 | x1.8 | +5.9k (14.8k) | +4.7k (6.0k) | +4.3k (5.6k) | +1.9k (4.0k) | -1.0k (4.1k) |  |
| 4/3 @ 5 (PRE-selected) | x1 | +5.6k (15.3k) | +1.8k (5.4k) | +3.3k (5.3k) | +3.2k (5.7k) | +2.4k (5.2k) | 1.9726224330793576 |
| 4/3 @ 5 (PRE-selected) | x1.8 | +4.1k (15.5k) | +1.7k (5.6k) | +3.2k (5.5k) | +3.7k (5.3k) | +1.3k (5.1k) |  |
| 4/3 @ 5 | LIVE-CAL x1.8 | +5.9k (13.9k) | +2.0k (5.3k) | +2.7k (4.9k) | +1.9k (5.2k) | -0.1k (4.8k) | |
| 4/3 @ 5 | N x1, ONE 3-lot order instead of 1-lot slices | +5.3k (15.2k) | +2.3k (5.3k) | +2.9k (4.9k) | +2.9k (6.1k) | +2.0k (5.3k) | |
| 4/3 @ 8 | x1 | +0.8k (15.7k) | +7.3k (9.8k) | +7.3k (9.0k) | +1.4k (6.1k) | +1.5k (5.2k) | 0.9616898874510077 |
| 4/3 @ 8 | x1.8 | -0.0k (15.7k) | +5.3k (8.8k) | +5.5k (8.3k) | +2.2k (5.8k) | +1.1k (5.1k) |  |

## 2. Notes
* The 'default' row for HM-4 and HM-NYAM is the same series when the other group is at its default (the whole HM book at 3/1 and 1/1). * Selection used SEL only; the recent windows were read once. * MDE is 2.8 x the weekly paired SE. * Single order vs 1-lot slices: the single-order model walks the displayed best size (extra half-tick per additional best-size multiple), so it is a rough bound. * Sweep costs not netted at c=1. * ST and WT are not live (research lots).
