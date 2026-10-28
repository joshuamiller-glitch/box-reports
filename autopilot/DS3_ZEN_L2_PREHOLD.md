# DS3_ZEN_L2_PREHOLD - holdout protocol for the L2 family (D3ZL2, text hashed before HOLD / X are read)

PRE screen done (items_PRE.csv, prereg ZEN_L2_B1 sha256 d08d5e70233882b770cd4a434f0cea44aa3e1db5317882eff16014205db56c52, N=495, reality-check best-of-N p over the valid items printed in the report).
Selection (rule of the prereg): top 30 items with mode != ctrl, sequenced PRE n >= 100, ranked by PRE effect vs random-in-regime WITH THE SAME TRIGGER; plus the B3 items whose PRE high-vs-low label difference CI excludes 0 (3 items).
HOLD = 2025-07-01..2026-02-06 read ONCE for exactly these 33 items (features for HOLD bars built after this hash; thresholds pull p90 11.586, ABSQ95 51, ABSQ99 81 and B3 medians FIXED from PRE). Then X = 2023-04-01..2024-01-31 read ONCE for the same 33.
Gates: G6 HOLD effect>0 and week-block CI lower>0 vs random-in-regime with the same trigger (pool expectation; 100-draw rank reported); G7 X effect>=0; G8 reality-check p<=0.05 over N=495 (PRE); G9 positive net in >=2 of 2024/2025/2026 and no year >60% of WF trades-net; G10 NOT run (no replay). B3 items: HOLD difference same sign and CI excludes 0.

Items (cell | mode | trigger | PRE n | PRE effect):
BARS|renko_38|E2|TMA_377_close|ctl|c60|955 | filter | DF15 | 123 | 14.324
BARS|renko_38|E2|TMA_377_close|ctl|c60|955 | filter | DF30 | 129 | 14.041
BARS|renko_38|E2|TMA_377_close|ctl|c60|955 | filter | DF5 | 120 | 12.906
BARS|renko_38|E2|TMA_377_close|ctl|c60|955 | filter | NOPULL | 147 | 12.823
BARS|kagi_32|E3|SMMA_377_close|x5|c60|955 | filter | DF15 | 164 | 12.487
BARS|kagi_32|E3|SMMA_377_close|x5|c60|955 | filter | DF5 | 154 | 12.309
BARS|kagi_32|E3|SMMA_377_close|x5|c60|955 | filter | DF30 | 167 | 10.979
BARS|kagi_32|E3|SMMA_377_close|x5|c60|955 | filter | NOPULL | 176 | 9.209
S3|E4|cap60|prev_day_extreme+0t|swing_4h_nearest_high | filter | REF2 | 102 | 5.977
S3|E4|cap60|prev_day_extreme+0t|swing_4h_nearest_high | filter | NOPULL | 145 | 5.069
S3|E4|cap60|prev_day_extreme+0t|swing_4h_nearest_high | filter | DF15 | 128 | 3.122
S3|E4|cap60|prev_day_extreme+0t|swing_4h_nearest_high | filter | DF5 | 127 | 2.936
S3|E4|cap60|prev_day_extreme+0t|swing_4h_nearest_high | filter | DF30 | 131 | 2.527
E2 | alone | DIV | 251 | 2.096
E4 | alone | DIV | 294 | 1.994
E2 | hold | DIV | 174 | 1.676
E3 | hold | DIV | 128 | 1.592
E5 | alone | IMB5_20 | 180 | 1.505
E1 | alone | DIV | 315 | 1.188
E3 | alone | DF5 | 876 | 0.986
E3 | alone | DIV | 149 | 0.976
E1 | hold | DIV | 240 | 0.845
E3 | hold | DF5 | 916 | 0.840
E3 | alone | DF15 | 910 | 0.790
E3 | hold | REF2 | 654 | 0.676
E1 | hold | ABSQ95 | 216 | 0.645
E3 | hold | DF15 | 948 | 0.600
E3 | hold | IMB5_15 | 180 | 0.518
E4 | hold | REF2 | 1280 | 0.513
E3 | alone | DF30 | 914 | 0.498
B3 items:
S3|E2|cap20|session_extreme+5t|pivot_R1 | B3 | B3_depth | diff 19.48 [4.61, 30.67]
S3|E2|cap20|session_extreme+5t|pivot_R1 | B3 | B3_through | diff -22.46 [-32.99, -6.73]
S3|E4|cap60|prev_day_extreme+0t|swing_4h_nearest_high | B3 | B3_imbpersist | diff -14.65 [-31.91, -3.78]
