# ZL_S4A_PREREG_S1_EQUAL_MEAN_LOTS (S4a, logged before any equal-mean-lots statistic)
Post-hoc, Shadow only, no PASS claims. Ts base (run_v13t_ts: sequential rounding, lock R scaled only when mult>1), reference = live binary ER(20)5m 0.30 ladder (x1.5/x0.5). New windows only (L6M, HOLD, MID, PRE, X'; cap 2026-10-31).

## Cells (the 11 distinct multiplier vectors of the S1 flag-rule cells, ts base, from SIZER_DRILL_S1_TS.csv)
1. ('g13', 'ers_15m_20', 1, 'SIG', 'A')
2. ('g12', 'er_3m_100', 'L3', 'D')
3. ('g13', 'ers_15m_20', 1, 'L3', 'A')
4. ('g12', 'er_10m_30', 'L3', 'D')
5. ('g13', 'ers_15m_20', 1, 'SIG', 'D')
6. ('g12', 'er_30m_10', 'LIN', 'B')
7. ('g12', 'er_15m_20', 'L3', 'A')
8. ('g12', 'er_15m_20', 'LIVE', 'A')
9. ('g13', 'ers_10m_20', 1, 'LIN', 'B')
10. ('g12', 'er_10m_30', 'LIN', 'B')
11. ('g12', 'er_15m_20', 'LIN', 'B')

## Procedure
1. For each vector m, find the scalar s such that the mean traded lots of s*m equals the live ladder's mean traded lots (3.01, engine), sequential rounding. Bisection on the formula lots (session lots x zone factor x multiplier, half-up min 1), then one-to-two secant corrections on engine mean lots from exposure_table; accept |mean lots - ladder| < 0.5%.
2. Score s*m on the ts base: per window mean/wk, maxDD, worst-20, cut vs the ladder, mean delta, carrying-week-dropped cut. PA9 = genuine: one engine run, SCORING week key shifted -4..+4 (the engine week key is inert on ts), band flip-5 (L6M .219 HOLD .205 MID .322 PRE .099 X' .182).
3. Placebos at the same mean lots: 100 draws each of perm (within book x session), dayshuf, ar1 applied to s*m, each draw re-scaled to the same formula mean lots; rank = share of draws below the real cut / mean.
4. Decomposition of the extra mean at equal lots: by book x session x ER-rank bucket (rank terciles of the cell's own ER feature; and the live ladder's two buckets): lots delta, net_flat P&L per lot, contribution = sum(delta lots x net_flat). Quality-ranking test: P&L per lot by ER-rank decile vs by the 0.30 threshold buckets, Spearman.
5. FLAG rule: a cell with lower maxDD than the ladder at equal mean lots on L6M AND PRE, carrying week dropped at same-or-better mean, and no-harm in HOLD/MID/X' (flip-5 band), is flagged in MORNING_FLAGS.md.
6. Gap fixes: S1 hysteresis, S2 and ADD mean lots (scatter file); S1B top cells re-run on ts.
No cell is a lead on one week or one month.
