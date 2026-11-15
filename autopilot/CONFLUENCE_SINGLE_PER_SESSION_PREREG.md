# T-CONFLUENCE single conditions per session as SIZE / TARGET, exact engine - PREREGISTRATION (W-CF3), 2026-11-15, written BEFORE any exact scoring

Order: autopilot/PRIORITY_CONFLUENCE_SINGLE_PER_SESSION_20261115.md. Base JN05W2 (all layers ON, measured fills, engine fee 1.18), hook cf_hooks (additive, identity TL3_CF_ID 598 / 25,943.82; re-proven after the target-scale edit by TL3_CF_ID2). Each condition acts in its own session only (sess 0 Asia, 1 London, 3 NY AM, 4 NY PM, ALL = every session), all books of the session.

## Conditions, column map, direction
Direction = the user label (go: size up when the condition is true; against: size up when it is FALSE). Directions were checked on data BEFORE the test windows (signals with ld <= 2025-04-30, the data before L6M/HOLD/L3M start; PRE, X' and GAP windows overlap this data, so for them the direction check is in-sample and they are labelled so). Lift = per-lot $ yes minus no in the session, pre-window.

| id | session | label | data direction | agree | lift per lot | t | n yes / no | column (block|name) | mapping note |
|--|--|--|--|--|--|--|--|--|--|
| A1 | Asia | go | go | yes | 15 | 0.30 | 2481 / 578 | A|c_A_supertrend_5m | NQ 5-min Supertrend with the trade |
| A2 | Asia | go | go | yes | 99 | 2.54 | 1791 / 1268 | 2B5|c_B5_NQ_5m_adx_di_with | NQ 5-min ADX/DI with the trade (B5 NQ column) |
| A3 | Asia | go | go | yes | 138 | 3.18 | 2255 / 804 | 2B5|c_B5_NQ_5m_sqz_mom_with | NQ 5-min squeeze momentum with the trade |
| A4 | Asia | go | go | yes | 48 | 1.17 | 1745 / 1075 | 2B5|c_B5_NQ_15m_hold21_with | NQ 15-min price holding the 21 with the trade |
| A5 | Asia | go | go | yes | 5 | 0.13 | 1513 / 1307 | 2B5|c_B5_RTY_15m_supertrend_with | RTY 15-min Supertrend with the trade |
| A6 | Asia | go | go | yes | 50 | 1.30 | 1495 / 1564 | A|c_A_emaorder_5m | NQ 5-min EMA stack (20/50 order) with the trade |
| L1 | London | go | go | yes | 71 | 1.67 | 1046 / 1374 | 2I|c_I_ZN_with60 | ZN moving with the trade over 60 min (as defined in CF2: ZN with60) |
| L2 | London | against | against | yes | -113 | -2.70 | 803 / 2188 | 2B5|c_B5_ALL_15m_adx_di_ge3of4 | 3 of 4 indexes (ES RTY YM MEGA) ADX/DI with the trade on 15-min |
| L3 | London | against | go | NO | 48 | 1.28 | 1521 / 1470 | 2B5|c_B5_ES_1m_supertrend_with | ES 1-min Supertrend with the trade |
| L4 | London | against | against | yes | -100 | -1.60 | 307 / 2684 | 2FG|c_G_imb1_ge0.35 | top-of-book imbalance >= 0.35 with the trade |
| N1 | NY AM | go | go | yes | 95 | 2.37 | 1702 / 1243 | 2B5|c_B5_RTY_15m_macd_rising_with | RTY 15-min MACD histogram rising with the trade |
| N2 | NY AM | go | go | yes | 41 | 0.91 | 2108 / 837 | 2B5|c_B5_ES_1m_hold21_with | ES 1-min price holding the 21 with the trade |
| N3 | NY AM | against | go | NO | 4 | 0.06 | 392 / 2553 | 2FG|c_G_imb1_ge0.35 | book imbalance (top level >= 0.35) with the trade (threshold not given by the order: same as London) |
| P1 | NY PM | go | go | yes | 100 | 1.36 | 304 / 394 | 2I|c_I_NQ_leads_ES15 | NQ leading ES over 15 min |
| P2 | NY PM | go | go | yes | 29 | 0.14 | 189 / 28 | 2J|c_J_flip_far50_SPX_oi | far (>= 50 pts) from the SPX gamma flip (OI-based; closest of far25/50/100) |
| P3 | NY PM | against | against | yes | -50 | -0.20 | 683 / 15 | 2B5|c_B5_corr_NQ_ES_60_ge0.8 | NQ-ES 60-min correlation >= 0.8 |
| P4 | NY PM | against | against | yes | -136 | -1.65 | 184 / 514 | 2B5|c_B5_NQ_5m_sqz_on | NQ 5-min squeeze on |
| Z1 | ALL | against | against | yes | -36 | -1.35 | 1901 / 7792 | 2B5|c_B5_NQ_5m_sqz_on | squeeze on at entry (NQ 5-min), all sessions |
| Z2 | ALL | go | go | yes | 59 | 2.34 | 6467 / 2359 | 2I|c_I_ratio_trend240_pos | NQ/ES ratio 240-min trend with the trade |

Disagreements with the label: L3 (ES 1-min Supertrend, label against, pre-window data go with t 1.28) and N3 (NY AM book imbalance, label against, data lift 4 per lot t 0.06). Neither is significant on the earlier data; the label direction is the registered primary and the reversed direction is also run (sets L3r, N3r, size 1.5/0.5 only) so nothing is flipped silently. P2 and P3 have almost no "no" rows before 2025-05 (the gamma-flip and correlation columns start late / are nearly constant), so their direction cannot be checked on earlier data; reported as such. Asia "at least k of 6" (A1..A6 count, k = 3, 4, 5) is a separate wave.

## Actions (each separately; total stack risk held constant where size moves)
S15: size x1.5 when favourable, x0.5 when unfavourable; S125: x1.25 / x0.75; T: target distance x1.25 favourable / x0.75 unfavourable, size 1; SK: skip the unfavourable signals (comparison only). Favourable = condition TRUE for go, FALSE for against; unknown condition = untouched. Size multipliers are normalised so the lot-weighted mean multiplier over the session in the pre-window data is 1; integer lots (floor(l*m+0.5), min 1) mean the realised lots/week are reported next to the result.

## Controls and windows
Shifted: the same action with the condition value of the latest signal in the same session at least 11 / 23 / 37 calendar days earlier (SH11/SH23/SH37). Random: the same number of favourable/unfavourable assignments given to random trades of the same book/session/month (RND1-3). W44-removed DD. Windows L3M, L6M first, then HOLD, PRE, X', GAP; a lead must hold in recent AND older windows; tolerant programme gate; drawdown first then mean; best-5 weeks kept; winning weeks turned losing. Controls are run for conditions whose first wave (S15, T) improves drawdown and mean in L3M and L6M.

## Wave order
Wave 1: S15 and T for all conditions, L3M + L6M; then S125, SK, controls for survivors, then HOLD/PRE/X'/GAP for survivors, then per-book splits and the per-session score (one condition per cluster, three bands). Sets are named TL3_CF_SP_<id>[r]_<ACT>[_<CTRL>]; tables in /mnt/l2/l2vast/_confl/cf3/sp/.

No PASS claim. Selection of survivors uses the exact engine in the recent windows only; the older windows then test them.
