# DS3_WORKS_Q - W-Q (family Q ranker + JOINT STAGE), page 0, 2026-11-11 19:20Z (date -u). Shadow only, post-hoc, no PASS claim.
Prereg autopilot/WORKS_Q_PREREG.md (sha256 bc9d2cde..., DECISIONS.md 19:14Z). Code outputs/code/th_works_q/q_rank.py and q_registry.py; outputs /mnt/l2/l2vast/_th_works/q/.

## Status in plain sentences
1. The ranker harness is built and ran once on the features that exist today (22 causal columns of the C1 table: ER, ATR, atr_rel, ADX, session move, TWAP slope/dev, P7 order/gap/last pnl, K/U/M same/opp side, calmar10, lots, session, side). It is a purged expanding walk-forward, refit every 2 label-weeks from 2024-04-01, label = the P7 trade ended in Target, a 12-leaf monotone LightGBM (3 seeds) and a 6-leaf tree (3 seeds), and a 20-shuffle family null (labels shuffled within month, same pipeline). Out-of-fold AUC is 0.534-0.538 for the GBDT and 0.509 for the tree.
2. Result today (first-order, trade level, equal-lot removal, NOT exact): skipping the bottom decile changes P7 by +$739 per week in L6M (null mean -$1,320, null 95th percentile +$732), +$197 in HOLD (null 95th +$648), +$431 in PRE (null 95th +$444); skipping the bottom quintile and halving the next gives +$470 L6M, -$349 HOLD, -$78 PRE. The 6-leaf tree is negative in every window (-$1.6k to -$4.9k per week). So on the current features the ranker is at the family-null edge, not above it: no lead. The null mean is negative because skipping random trades from a positive-mean book costs money, so the honest comparison is the null 95th percentile.
3. Top features by gain (GBDT mean over seeds): lots, p7_gap_min (minutes since the last P7 exit), atr_rel, p7_last_pnl, twap_dev, atr5, adx5, session move. Nothing yet is expressible as 2-3 plain conditions beyond what C1 already said (lots, re-entry gap, vol state). The X' window (2023-04..2024-01) has no out-of-fold scores because the first fold is 2024-04: X' is empty for Q by construction until a shorter warm-up is tried.
4. Not done: the E/F/G/H/I/J/K/L/M/N/O/P feature tables have not landed (shared table p7_signal_features.parquet and p7_feat_*.parquet are absent; the _th_works/e and /i directories exist but are empty at 19:17Z). q_rank.py joins them automatically on sig_ts / utc_epoch_s when they appear, and the ranker must be re-run then, including untaken signals if W-E supplies them (today it ranks taken trades only, so it cannot see signals the live blackout or caps already skipped).
5. Joint registry: /mnt/l2/l2vast/_th_works/q/joint_registry.tsv, rebuilt by `python3 -I code/th_works_q/q_registry.py` (read-only on others' files). It holds 18 exact rows today (W-A A1 3, A2 5, A-composites 2, W-C C3/C4 6, others 2) with windows done, L6M/HOLD/PRE maxDD cut and mean; top3 flag per family and reference. W-B rows are in its DS3 page and drive logs, not yet in a score csv, so they are not in the registry: to be added when W-B publishes one.
6. The joint stage has NOT started. Budget stated honestly: exact throughput is about 35-40 cell-months per worker per hour with a shared cap, and MemAvail was 34 GB at 19:17Z (below the 40 GB guard), so no exact worker was launched by W-Q. 2,000 exact stacks x even one window (6 months) = 12,000 cell-months = about 300 worker-hours, impossible. Plan once families land: (1) full factorial of the six top-1s = 64 stacks, pre-screened first-order, the top 8 exact on L6M then HOLD, PRE, X'; (2) coordinate descent from LPB/JN04RM and from 10 random stacks, exact only for the final 5 stacks; (3) 2,000 random stacks first-order only (labelled first-order, never a result) to pick 6-10 stacks for exact L6M; (4) interaction table from first-order pair-drops, confirmed exact for the top pairs; (5) the minimal 2-3 rule set exact on L6M + HOLD, then repeated unchanged on K7/M7/U7. Dial pairs already suspected duplicate from W-A/W-B: SIGQ vs day cap, LOT vs 7/4/4.
7. Known inputs for the joint (from the other pages, exact, JN04RM base): W-C 30-min blackout -5.2 % L6M (not an earner on the dressed stack), hot-only 60-min same-side blackout +4.1 % (inside noise); W-B never-cut P7 +19.1 / +10.4 / +27.4 % L6M/PRE/X', -19.1 % HOLD on LPB_BASE; W-A A2_18 first-order L6M overstated vs exact (-24.4 %). These are registry candidates, not joint results.

## Next
Page 03:00Z will carry: ranker re-run on the landed feature tables with untaken signals, registry with top-3 per family, factorial pre-screen, first exact joint rows, and the budget actually spent.

## Auto section (chain, rebuilt 2026-11-11T19:29:42Z)
Inputs seen: 31 watched files; feature tables landed: ['p7_feat_I.parquet', 'p7_feat_I_v2.parquet', 'p7_signal_features.parquet']. Cycle log: ranker re-run (feature tables: ['p7_feat_I.parquet', 'p7_feat_I_v2.parquet', 'p7_signal_features.parquet']).
Registry rows by family: {'A-comp': 2, 'A1': 3, 'A2': 5, 'C3': 4, 'C4': 2, 'other': 2}. launch gate MemAvail 51 GB (need 62): CLOSED; no joint set is defined yet (needs the families top-3 specs), so nothing launched.
Ranker (first-order, GBDT mean over 3 seeds vs null 95th percentile, dollars per week):
action  win    gbdt  null95
   dec HOLD  6527.0  3526.0
   dec  L1M  4457.0  4843.0
   dec  L3M  4649.0  5014.0
   dec  L6M  5687.0  4350.0
   dec  PRE  6079.0  3269.0
   dec   X'     0.0     0.0
  quin HOLD 22226.0  7645.0
  quin  L1M 25847.0 10883.0
  quin  L3M 21528.0  9788.0
  quin  L6M 22451.0  8132.0
  quin  PRE 16756.0  6193.0
  quin   X'     0.0     0.0
First-order P7-only rule interaction on the six rules R1 gap<30 min skip, R2 atr_rel>=1.3 half, R3 chasing 3rd+ skip, R4 LOT cold half, R5 Asia 7-lot short half, R6 same-side stack>=5 half (trade-level, week-level P7 drawdown, NOT stack, NOT exact; top 6 of the 64-cell factorial by L6M drawdown cut; k = rule count; removed_w20 / removed_other = pnl removed in the worst-20 weeks vs other weeks):
      rules  k  ddcut_L6M  dmean_L6M  ddcut_HOLD  dmean_HOLD  ddcut_PRE  dmean_PRE  ddcut_X'  dmean_X'  removed_w20  removed_other
   R1+R2+R5  3       60.2    -3366.3        26.5     -6136.0       46.3    -1458.4      -7.8    -947.2    -331787.2       881706.7
   R2+R4+R5  3       58.8    -2874.6        57.8     -4544.6       33.4    -2023.6      54.8      70.2    -322498.0       756219.8
      R1+R5  2       53.5    -2957.4        -5.5     -5715.8       32.7     -999.2     -40.1   -1389.9    -275708.8       772993.8
R1+R2+R4+R5  4       52.8    -5885.2         0.7     -7986.3       67.7    -2120.6      36.1    -637.2    -422370.3      1101324.4
R2+R3+R4+R5  4       51.5    -5999.0        51.5     -6927.5       46.7    -2397.5      54.5      86.5    -369540.7       951206.9
R1+R2+R5+R6  4       49.9    -3775.1        24.9     -6286.8       47.7    -1673.4      -6.3    -953.6    -331459.5       908276.6
Pairs (jaccard = overlap of flagged trades; L6M columns = P7 drawdown cut percent, pair vs each alone; additive pairs with small jaccard do not duplicate, big jaccard with pair < sum duplicates):
                 a                  b  n_a  n_b  jaccard  L6M_pair  L6M_i  L6M_j
     R1_gap30_skip      R2_hot13_half 2350 2390     0.28     47.16  39.44  20.67
     R1_gap30_skip      R3_chase_skip 2350  931     0.26     11.96  39.44   2.09
     R1_gap30_skip       R4_cold_half 2350 3000     0.36     28.93  39.44  22.60
     R1_gap30_skip R5_asia7short_half 2350  404     0.08     53.55  39.44  25.79
     R1_gap30_skip     R6_stack5_half 2350  356     0.10     22.36  39.44  -0.00
     R2_hot13_half      R3_chase_skip 2390  931     0.17     24.72  20.67   2.09
     R2_hot13_half       R4_cold_half 2390 3000     0.35     49.35  20.67  22.60
     R2_hot13_half R5_asia7short_half 2390  404     0.06     39.71  20.67  25.79
     R2_hot13_half     R6_stack5_half 2390  356     0.02     23.38  20.67  -0.00
     R3_chase_skip       R4_cold_half  931 3000     0.16     18.53   2.09  22.60
     R3_chase_skip R5_asia7short_half  931  404     0.11     27.30   2.09  25.79
     R3_chase_skip     R6_stack5_half  931  356     0.06      5.42   2.09  -0.00
      R4_cold_half R5_asia7short_half 3000  404     0.08     36.41  22.60  25.79
      R4_cold_half     R6_stack5_half 3000  356     0.07      6.13  22.60  -0.00
R5_asia7short_half     R6_stack5_half  404  356     0.07     25.79  25.79  -0.00
