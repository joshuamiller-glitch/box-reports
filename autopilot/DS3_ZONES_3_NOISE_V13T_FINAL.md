# DS3_ZONES_3_NOISE_V13T_FINAL - phase-averaged noise band on V13T_LIVE (n=100)

Shadow only. No PASS claims. Z3. Cap 2026-10-31. Supersedes the partial DS3_ZONES_3_NOISE_V13T.md (n about 45), which is left untouched.
Base V13T_LIVE: V13Z lines empty, lock none, xcost 0.80, stopcost 2.45, tshort 0, lockfix legs. Shipped layer = 8-line set (HALF D20 on 7 lines, OTE-62 B73 D30).
Method as in the partial doc: random flip of p% of live rows to half lots, real engine composites at 9 week-key shifts (xcost 0.80) plus cost phases (0,0.58),(0,1.02), paired with base per phase; band = 95th pct |maxDD cut|. 100 draws per flip size.

| flip | window | n | single (phase 0) | PA9 (headline) | PA11 |
|---|---|---|---|---|---|
| 2% | L3M | 100 | 0.104 | 0.190 | 0.164 |
| 2% | L6M | 100 | 0.195 | 0.188 | 0.189 |
| 2% | HOLD | 100 | 0.172 | 0.182 | 0.177 |
| 2% | MID | 100 | 0.229 | 0.212 | 0.196 |
| 2% | PRE | 100 | 0.054 | 0.078 | 0.068 |
| 2% | X' | 100 | 0.207 | 0.145 | 0.125 |
| 5% | L3M | 100 | 0.184 | 0.165 | 0.164 |
| 5% | L6M | 100 | 0.291 | 0.219 | 0.227 |
| 5% | HOLD | 100 | 0.213 | 0.205 | 0.200 |
| 5% | MID | 100 | 0.561 | 0.322 | 0.316 |
| 5% | PRE | 100 | 0.095 | 0.099 | 0.097 |
| 5% | X' | 100 | 0.266 | 0.182 | 0.171 |

Change vs partial (n about 45): L6M 5% fell from 0.257 to 0.219, L6M 2% rose from 0.179 to 0.188; other cells moved by 0.02 or less. Base maxDD by phase unchanged (L6M 172k +-14k; xcost 0.58/1.02: 134k/166k).
Files: out/zones3/s3_v13tl/tl_band_final.csv; code l2vast/ds3/code/zones3_s3/tl_band_final.py.
