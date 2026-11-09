# EX-LDEF PREREG (families D price-path, E conditioners, F actions), 2026-11-09 ~03:10Z, before any cell is scored
Trigger form (all D rules): decision at second k (k>=1, k<br_k) when -unreal(mid vs fill_avg) >= X pts AND rule condition; exit leg executes at k+1 (E.market_exit, 0.80 pt); technique label D<n>_<rule>. X lattice 10..55 step 5 (10 values). Entry-match label PRE-PROOF. Side = loss. State/price quantities only (1-s mid, high, low from the universe paths).
D1 mom: against-move over w s: side*(mid[k]-mid[k-w]) <= -m; w in {10,30,60,120,300}, m in {3,5,8,12,20} (w=30 is also vel30) x X = 250
D2 stall: seconds since last new favourable extreme (MFE incl. entry) >= s in {30,60,120,300,600,1200} x X = 60
D3 pullback: MFE - unreal >= pb in {10,20,30,40,50} x X = 50
D4 efficiency: against net/sum|dmid| over w in {60,120,300} >= thr in {.3,.5,.7} x X = 90
D5 votes (ThRequired): voters {mom(60,8), stall>=120, pullback>=20, eff(120)>=.4}; require r in 1..4 x X = 40
D7 time-in-trade: k >= 60*m, m in {1,2,3,5,10,20,30,60} x X = 80 (also the F time-stop at -X)
D8 adverse-extreme age: fresh (extreme set within the last a s, a in {5,15,30,60}) and stale (>= a in {30,60,120,300}) x X = 80
D9 recovery failure: bounced >= b in {3,5,8,12,20} pts above the adverse extreme, then a new adverse extreme x X = 50
D10 ATR-adaptive arm: arm = c * ATR14(1-min) at entry, c in {1.5,2,3,4,6,8,12} (no X) = 7
D11 chandelier-against: fire when price falls c*ATR14(1m, entry) below the favourable extreme (entry counts), c in {2,3,4,6}, floor X = 40
D12 structure break: mid breaks the min/max of the window [k-2w,k-w] against, w in {60,300} x X = 20 (path-only, needs k>=2w)
D15 bar-close: n consecutive epoch-1-min closes with -unreal >= X, n in {1,2,3} x X = 30
D16 N-bar failure to reclaim entry: N consecutive 1-min closes adverse (N in {3,5,10,15}) and -unreal >= r in {0,5,10,20} = 16
D13 flip-level (no BT flip data in the universe: not scored, reported as no data), D14 Kijun/EMA cross: scored in an addendum on months where EX-FEAT panels exist (labelled partial coverage).
Plain references: ARM-only cut (X 10..55) = D0, 10 cells.
F actions (same trigger as D0 plain X, then addendum to the 6 best D cells): F2 half cut (floor(lots/2) at trigger) + re-arm of the rest at X+d, d in {5,10,15}: 30; F3 stop moved to adverse extreme-at-trigger - k pts beyond (k in {0,2,5,10}, stop at level via walk_to_bracket): 40; F4 fixed stop at -X from entry (level): 10; F5 time-stop = D7; F6 stop-and-reverse REPORT row only (not for live).
E conditioners (filter = the rule may fire only inside the context; unfired trades hold to bracket): hour block (3-h ET blocks, 8), ER20 5-min at entry (<0.30 / 0.30-0.45 / >=0.45), lots (1 / 2-4 / >=5), time since entry window (<120 s / 120-600 / >600, as kmin,kmax), day P&L state (realised never-cut P&L of the label day before entry ahead / behind), other books open same side (0 / 1 / >=2), B02 quiet flag (1/0), first N min of the entry session (N in {15,30,60}: in / out), ATR regime (1m ATR14 at entry / day median TR terciles), blackout after a prior fired cut of the same book (same side / both sides; 15/30/60 min; the blacked-out entries are skipped = zero P&L). Entry session is already a scope in the ledger (86 scopes). Tested on: live line (45/10x/W2/P3/V2 state cell), D0 at X=30,40,50, and the 5 best D cells (pooled drawdown-first key) = 9 base cells x 35 levels.
Finalist rule: per book and pooled, drawdown-first key (L6M maxDD reduction, then PRE maxDD not worse than 1.05x, worst-20, Ulcer, Calmar, mean) with nfire>=20, L6M mean delta >=0; <=12 finalists to Stage 2. Every cell scored is registered through score_cell (agent EX-LDEF); no cell is dropped. Addenda only as labelled lines in DECISIONS.md before first score.
