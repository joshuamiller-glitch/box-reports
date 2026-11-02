# DS3_ZONES_3_V13T_LIVE - zone layer on V13T_LIVE (layers, leads); walk-forward and survivors follow

Shadow only. No PASS claims. Z3. Cap 2026-10-31. Base V13T_LIVE (V13Z lines empty, lock none, xcost 0.80, stopcost 2.45, tshort 0, lockfix legs). Band = DS3_ZONES_3_NOISE_V13T_FINAL.md (n=100, PA9).
Sign convention: "cut" = (maxDD_ref - maxDD_variant)/maxDD_ref, positive = variant has smaller drawdown. Script l2vast/ds3/code/zones3_s3/tl_an.py; data out/zones3/s3_v13tl/{layers_tl_*.pkl,leads_tl.pkl,leads_tl_table.csv}.

## 1. Shipped layer vs none vs 100 random same-size half-lot layers (PA over 5 week shifts)
Cut of the layer relative to NO layer (negative = layer is worse than none):
| window | shipped | random mean | random SD | shipped rank among random | rank on ulcer | rank on CVaR-10% |
|---|---|---|---|---|---|---|
| L3M | -0.043 | -0.124 | 0.191 | 0.64 | 0.77 | 0.12 |
| L6M | -0.017 | +0.041 | 0.185 | 0.37 | 0.40 | 0.20 |
| HOLD | -0.017 | +0.026 | 0.167 | 0.37 | 0.31 | 0.23 |
| MID | -0.111 | +0.009 | 0.274 | 0.32 | 0.24 | 0.32 |
| PRE | +0.107 | +0.036 | 0.083 | 0.79 | 0.84 | 0.88 |
| X' | -0.028 | +0.050 | 0.133 | 0.23 | 0.29 | 0.62 |
Reading: on V13T_LIVE the shipped layer is not distinguishable from a random half layer of the same size in any window (all ranks below 0.95; L6M/HOLD/MID/X' it is nominally worse than the random mean; only PRE is nominally better: +0.107 vs band 0.078, rank 0.79). The layer is not shown to reduce drawdown versus no layer in L6M/HOLD/MID/X'.
NONE vs shipped (lead-table row NONE): L6M +0.024, HOLD +0.024, MID +0.030, PRE -0.128, X' +0.009: none is worse in PRE only, outside-noise (band PRE 0.078).

Equal-risk (lot scale searched so ALL-window worst-20 equals shipped): NONE needs scale 0.907 (gap -1.4%); random layers need 1.008 +-0.034. At equal risk maxDD ($): L6M/HOLD shipped 150.7k vs none 135.7k vs random mean 151.0k (SD 33k, rank 0.51); MID 43.7k / 49.2k / 49.6k (rank 0.69); PRE 166.2k / 171.5k / 172.1k (rank 0.75); X' 92.5k / 78.8k / 74.2k (rank 0.10, shipped worse). No equal-risk edge for the shipped layer beyond noise.

## 2. Leads on V13T_LIVE (PA over 9 shifts, cut vs shipped layer; band for the 2% flip in brackets: L6M .188, PRE .078, X' .145, MID .212)
| lead | L3M | L6M | HOLD | MID | PRE | X' | ulcer L6M | CVaR L6M | L6M>b2 | PRE or X'>b2 | no-harm PRE/MID |
|---|---|---|---|---|---|---|---|---|---|---|---|
| NONE (layer off) | .032 | .024 | .024 | .030 | -.128 | .009 | +2308 | +1192 | no | no | no |
| BT swing flip D40 skip (ZL-1 mask) | .097 | .142 | .132 | -.089 | .066 | .082 | -3215 | -5681 | no | no | yes |
| LP_AGAINST natural skip | -.080 | -.005 | -.005 | -.035 | .012 | -.175 | -1358 | -2148 | no | no | yes |
| LP any-side A40 TLP p25 4h | -.064 | .130 | .121 | -.084 | .030 | -.150 | -8448 | -793 | no | no | yes |
| EQL_tight 5m D40 skip | -.020 | .385 | .242 | -.076 | .051 | -.184 | -22571 | -1480 | yes | no | yes |
| camH3 40 fw8 any | .020 | .036 | .036 | .003 | -.053 | -.094 | -186 | -442 | no | no | yes |
| PDmid 40 fw1 stk | -.040 | -.038 | -.038 | -.001 | .015 | .093 | +2476 | +375 | no | no | yes |
| S5 sopen40 half | -.347 | .192 | .157 | -.200 | .348 | -.160 | -28972 | +22292 | yes | yes | yes |
| S5 sA40>=1 skip | .126 | .502 | .502 | -.323 | .219 | -.585 | -45585 | -4802 | yes | yes | no |
| S5 nA60>=1 skip | .132 | .504 | .504 | -.377 | .126 | -.595 | -44821 | -3805 | yes | yes | no |
| S5 rho60>=2 skip | .181 | .469 | .469 | -.176 | -.045 | .025 | -38956 | -7146 | yes | no | yes |
| ZL-3 G2 TVP-confirmed skip Dl60 | .135 | .525 | .394 | .214 | -.071 | .092 | -46603 | -3063 | yes | no | yes |
| SWG f3L 15s D40 half | .018 | .239 | .169 | -.041 | -.001 | -.089 | -24261 | +19641 | yes | no | yes |
| ARR iplFVG 15s D20 skip | -.207 | .337 | .298 | -.562 | -.340 | .039 | -40200 | -12046 | yes | no | no |
| DEV on_L D20 half | .037 | .187 | .184 | .260 | -.130 | .299 | -16853 | +12981 | no | yes | no |
| ALL7 skip (HALF->SKIP) | .059 | .142 | .121 | -.694 | .059 | -.197 | -8813 | -588 | no | no | no |
(no-harm = PRE and MID cuts not below minus the 2%-flip band.)

Reading:
- The BT swing flip (ZL-1 mask) gives +0.142 in L6M, below the 0.188 band, and is negative in MID (-0.089): it does not pass.
- No lead passes the full rule (L6M and PRE-or-X' above band, same sign) together with no-harm. sopen40 passes the three numeric gates but is the volume-resolved lead (55% of rows halved, CVaR worse by +22k, L3M -0.35); it needs the size-matched placebo, which resolved it as volume on V13Y and has not been re-run on V13T_LIVE. sA40/nA60 fail no-harm (MID -0.32/-0.38, X' -0.59). DEV on_L fails no-harm (PRE -0.13).
- Large L6M cuts (EQL_tight .385, G2 .525, rho60 .469, SWG .239, ARR .337) have no PRE or X' support, which is the carrying-episode pattern seen on V13Y. Not survivors.
- Volume-matched placebos, equal-risk and episode-drop for these leads on V13T_LIVE are not yet run; do not treat any row as confirmed.
