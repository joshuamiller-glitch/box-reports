# DS3_ZONES_3_B5_MANCINI - Mancini / reaction frame as zone streams on the REDO cap (ZL-1, B5), V13X (exact D7 v1.3), both lock frames (headline lock=None), written 2026-11-02 07:39Z
Everything post-hoc, Shadow only, no PASS claim. Base maxDD $k: lock 12R L6M 73.9, PRE 252.4, X' 173.7, HOLD 119.2, MID 78.5; lock None L6M 132.6, PRE 178.4, X' 134.8, HOLD 132.6, MID 62.6. Prereg for the B5 streams: the B1/B3 prereg family (ZL1_B1B3_prereg.md sha256 06bbf141...b1cf) plus the definitions stated here (written before the scoring runs of these streams).

## 0. What exists and what is new
* S4b built and scored 24 Mancini streams (MNA failed breakdown A(F=6, W=15 min), MNB back-test B(break 3, pull back within 3, hold); sources SWG f5 15m/1h, PDX day/rth H/L/M, SES on_H/on_L): 96 cells on V13X, lock 12 and lock None, S median +0.01, best +0.20, nothing eligible (autopilot S4b section; /mnt/l2/l2vast/ds3_zones3_new/s4b/screen_table13x*.pkl). Cited, not rescored. My failed-breakdown streams (the SWP family, section ZL-1 above) are DEAD in both frames and agree.
* New here: (1) BT = flip levels: a prior-day, session or 5-min fractal swing level that price has BROKEN by >= F pts (F 5 and 10) becomes a support (broken up) or resistance (broken down); 18 streams (type x F x keep 1/4/24 h). (2) RXL = the price-memory map: density bands (every 5m/15m/1h fractal-5 reversal weighted by the move it reversed, triangular +-4 pt kernel, 10-day half-life, hourly snapshots, bands above the 90th / 95th percentile of the snapshot density) and composite HVN / LVN of the previous 5 / 20 / 60 label days (per-second mean-price volume profile).
* Streams in /mnt/l2/l2vast/ds3_zones3_new/zl1/streams_book/ (BT*, RXL*), POI format, end = first touch (density snapshots: end = never, valid 1 h), ek = first print second >= the knowable second.
* Causal audits: BT/events: global ek check and the SWP-family kernel audit (97/97 style, same state machine); RXL density bands: path truncated at 2025-03-14, 205,874 hourly band rows compared, 78 not reproduced (0.04%, snapshot-grid float ties); RXL composite profile rows 13,821 compared, 0 differences.

## 1. BT flip levels (swing level broken by >= 10 pts, between entry and target within D, 4 h keep): the only new candidate
V13X cells, lock 12R (first block) and lock None (second block): maxDD cut vs the frame's base; dmean_HOLD in $ per week.
| stream           | frame   |   D | act   |   nflag |    L3M |    L6M |   HOLD |    MID |    PRE |    X' |   dmean_HOLD |
|:-----------------|:--------|----:|:------|--------:|-------:|-------:|-------:|-------:|-------:|------:|-------------:|
| BT|pd_F10|24h    | AH      |  20 | half  |     134 |  0     |  0     | -0     |  0     |  0.018 | 0.006 |        3.997 |
| BT|pd_F10|24h    | AH      |  40 | half  |     293 | -0.012 | -0.006 | -0     |  0     |  0.026 | 0.006 |       -5.019 |
| BT|pd_F10|24h    | AH      |  20 | skip  |     134 |  0     |  0     | -0.004 |  0     |  0.03  | 0.015 |      -46.283 |
| BT|pd_F10|24h    | AH      |  40 | skip  |     293 | -0.024 | -0.013 | -0.036 |  0     |  0.048 | 0.001 |     -112.68  |
| BT|pd_F10|4h     | AH      |  20 | half  |      38 |  0     |  0     | -0     |  0     |  0.018 | 0.001 |        3.997 |
| BT|pd_F10|4h     | AH      |  40 | half  |      61 |  0.038 |  0.02  | -0     |  0     |  0.026 | 0.001 |       33.034 |
| BT|pd_F10|4h     | AH      |  20 | skip  |      38 |  0     |  0     | -0.004 |  0     |  0.034 | 0.005 |      -21.712 |
| BT|pd_F10|4h     | AH      |  40 | skip  |      61 |  0.068 |  0.037 | -0.036 |  0     |  0.052 | 0.005 |      -24.197 |
| BT|pd_F5|24h     | AH      |  20 | half  |      88 |  0     |  0     |  0     |  0     |  0.018 | 0.008 |        4.511 |
| BT|pd_F5|24h     | AH      |  40 | half  |     204 |  0     |  0     |  0     |  0     |  0.026 | 0.007 |        4.511 |
| BT|pd_F5|24h     | AH      |  20 | skip  |      88 |  0     |  0     |  0     |  0     |  0.034 | 0.015 |      -12.332 |
| BT|pd_F5|24h     | AH      |  40 | skip  |     204 |  0     |  0     | -0.029 |  0     |  0.052 | 0.001 |      -52.468 |
| BT|pd_F5|4h      | AH      |  20 | half  |      27 |  0     |  0     |  0     |  0     |  0.018 | 0.001 |        4.511 |
| BT|pd_F5|4h      | AH      |  40 | half  |      42 |  0     |  0     |  0     |  0     |  0.026 | 0.001 |        4.511 |
| BT|pd_F5|4h      | AH      |  20 | skip  |      27 |  0     |  0     |  0     |  0     |  0.034 | 0.002 |      -12.332 |
| BT|pd_F5|4h      | AH      |  40 | skip  |      42 |  0     |  0     | -0.029 |  0     |  0.052 | 0.002 |      -64.662 |
| BT|sess_F10|24h  | AH      |  20 | half  |     971 |  0.068 |  0.075 |  0.322 |  0.021 | -0.06  | 0.086 |      938.036 |
| BT|sess_F10|24h  | AH      |  40 | half  |    2042 |  0.12  |  0.1   |  0.341 |  0.078 | -0.164 | 0.071 |      685.913 |
| BT|sess_F10|24h  | AH      |  20 | skip  |     971 |  0.068 |  0.038 |  0.34  |  0.009 |  0.028 | 0.155 |      741.174 |
| BT|sess_F10|24h  | AH      |  40 | skip  |    2042 |  0.146 |  0.064 |  0.42  |  0.12  | -0.296 | 0.163 |     1987.23  |
| BT|sess_F10|4h   | AH      |  20 | half  |     299 |  0.068 |  0.057 |  0.304 |  0     |  0.031 | 0.075 |     1106.73  |
| BT|sess_F10|4h   | AH      |  40 | half  |     521 |  0.068 |  0.053 |  0.302 | -0.003 | -0.037 | 0.059 |     1526.98  |
| BT|sess_F10|4h   | AH      |  20 | skip  |     299 |  0.068 |  0.037 |  0.304 |  0     |  0.056 | 0.096 |     1257.41  |
| BT|sess_F10|4h   | AH      |  40 | skip  |     521 |  0.068 |  0.032 |  0.273 | -0.004 |  0.088 | 0.089 |      139.263 |
| BT|sess_F5|24h   | AH      |  20 | half  |     542 |  0     |  0.046 |  0.322 |  0.021 | -0.015 | 0.064 |      875.567 |
| BT|sess_F5|24h   | AH      |  40 | half  |    1152 |  0.052 |  0.071 |  0.341 |  0.078 | -0.128 | 0.044 |     1258.43  |
| BT|sess_F5|24h   | AH      |  20 | skip  |     542 |  0     |  0.015 |  0.343 |  0.009 |  0.1   | 0.129 |      683.593 |
| BT|sess_F5|24h   | AH      |  40 | skip  |    1152 |  0.119 |  0.058 |  0.416 |  0.12  |  0.027 | 0.094 |     2203.16  |
| BT|sess_F5|4h    | AH      |  20 | half  |     176 |  0     |  0.02  |  0.304 |  0     |  0.028 | 0.049 |      978.705 |
| BT|sess_F5|4h    | AH      |  40 | half  |     315 |  0     |  0.017 |  0.302 | -0.003 | -0.04  | 0.044 |      951.553 |
| BT|sess_F5|4h    | AH      |  20 | skip  |     176 |  0     |  0     |  0.305 |  0     |  0.056 | 0.063 |     1029.47  |
| BT|sess_F5|4h    | AH      |  40 | skip  |     315 |  0     | -0.004 |  0.273 | -0.004 |  0.088 | 0.068 |     -108.442 |
| BT|swing_F10|24h | AH      |  20 | half  |    4701 |  0.15  |  0.066 |  0.373 |  0.048 |  0.261 | 0.159 |     1208.43  |
| BT|swing_F10|24h | AH      |  40 | half  |    8593 |  0.203 |  0.112 |  0.418 |  0.116 |  0.133 | 0.225 |     1743.62  |
| BT|swing_F10|24h | AH      |  20 | skip  |    4701 |  0.277 |  0.133 |  0.383 |  0.063 |  0.25  | 0.225 |     1143.14  |
| BT|swing_F10|24h | AH      |  40 | skip  |    8593 |  0.193 |  0.049 |  0.411 |  0.315 | -0.145 | 0.225 |     3255.53  |
| BT|swing_F10|4h  | AH      |  20 | half  |    1840 |  0.136 |  0.052 |  0.368 |  0.04  |  0.067 | 0.138 |     2805.98  |
| BT|swing_F10|4h  | AH      |  40 | half  |    2819 |  0.22  |  0.111 |  0.412 |  0.106 |  0.064 | 0.128 |     2788.23  |
| BT|swing_F10|4h  | AH      |  20 | skip  |    1840 |  0.22  |  0.126 |  0.345 |  0.005 |  0.148 | 0.225 |     3117.57  |
| BT|swing_F10|4h  | AH      |  40 | skip  |    2819 |  0.303 |  0.166 |  0.483 |  0.287 |  0.141 | 0.225 |     5338.5   |
| BT|swing_F5|24h  | AH      |  20 | half  |    3216 |  0.136 |  0.065 |  0.347 |  0.008 |  0.143 | 0.056 |     1540.4   |
| BT|swing_F5|24h  | AH      |  40 | half  |    6021 |  0.229 |  0.133 |  0.346 |  0.006 |  0.06  | 0.2   |     1855.71  |
| BT|swing_F5|24h  | AH      |  20 | skip  |    3216 |  0.235 |  0.114 |  0.317 | -0.037 |  0.259 | 0.174 |     1704.87  |
| BT|swing_F5|24h  | AH      |  40 | skip  |    6021 |  0.269 |  0.082 |  0.377 |  0.054 | -0.061 | 0.225 |     2922.18  |
| BT|swing_F5|4h   | AH      |  20 | half  |    1305 |  0.136 |  0.052 |  0.341 |  0     |  0.04  | 0.051 |     2713.05  |
| BT|swing_F5|4h   | AH      |  40 | half  |    1988 |  0.22  |  0.111 |  0.344 |  0.003 | -0.051 | 0.067 |     3157.82  |
| BT|swing_F5|4h   | AH      |  20 | skip  |    1305 |  0.22  |  0.117 |  0.279 | -0.095 |  0.151 | 0.121 |     2919.49  |
| BT|swing_F5|4h   | AH      |  40 | skip  |    1988 |  0.263 | -0.123 |  0.304 |  0.053 |  0.16  | 0.184 |     4571.62  |

| stream           | frame   |   D | act   |   nflag |    L3M |    L6M |   HOLD |    MID |    PRE |     X' |   dmean_HOLD |
|:-----------------|:--------|----:|:------|--------:|-------:|-------:|-------:|-------:|-------:|-------:|-------------:|
| BT|pd_F10|24h    | AH      |  20 | half  |     134 |  0     |  0     |  0     |  0     |  0     | -0.002 |       98.811 |
| BT|pd_F10|24h    | AH      |  40 | half  |     293 |  0     |  0.013 |  0.013 |  0     |  0.007 | -0.002 |      164.961 |
| BT|pd_F10|24h    | AH      |  20 | skip  |     134 |  0     |  0     |  0     |  0     |  0     | -0.007 |      171.842 |
| BT|pd_F10|24h    | AH      |  40 | skip  |     293 |  0     |  0.025 |  0.025 |  0     |  0.013 | -0.007 |      166.742 |
| BT|pd_F10|4h     | AH      |  20 | half  |      38 |  0     |  0     |  0     |  0     |  0     |  0     |       13.943 |
| BT|pd_F10|4h     | AH      |  40 | half  |      61 |  0     |  0.013 |  0.013 |  0     |  0.007 |  0     |       74.95  |
| BT|pd_F10|4h     | AH      |  20 | skip  |      38 |  0     |  0     |  0     |  0     |  0     |  0     |       -2.815 |
| BT|pd_F10|4h     | AH      |  40 | skip  |      61 |  0     |  0.025 |  0.025 |  0     |  0.014 |  0     |       58.639 |
| BT|pd_F5|24h     | AH      |  20 | half  |      88 |  0     |  0     |  0     |  0     |  0     |  0     |       66.216 |
| BT|pd_F5|24h     | AH      |  40 | half  |     204 |  0     |  0.013 |  0.013 |  0     |  0.007 |  0     |      141.382 |
| BT|pd_F5|24h     | AH      |  20 | skip  |      88 |  0     |  0     |  0     |  0     |  0     | -0.003 |      117.628 |
| BT|pd_F5|24h     | AH      |  40 | skip  |     204 |  0     |  0.025 |  0.025 |  0     |  0.014 | -0.003 |      138.789 |
| BT|pd_F5|4h      | AH      |  20 | half  |      27 |  0     |  0     |  0     |  0     |  0     |  0     |      -18.651 |
| BT|pd_F5|4h      | AH      |  40 | half  |      42 |  0     |  0.013 |  0.013 |  0     |  0.007 |  0     |       13.318 |
| BT|pd_F5|4h      | AH      |  20 | skip  |      27 |  0     |  0     |  0     |  0     |  0     |  0     |      -81.6   |
| BT|pd_F5|4h      | AH      |  40 | skip  |      42 |  0     |  0.025 |  0.025 |  0     |  0.014 |  0     |      -69.99  |
| BT|sess_F10|24h  | AH      |  20 | half  |     971 | -0.01  | -0.103 | -0.103 |  0.027 | -0.072 |  0.019 |      -98.132 |
| BT|sess_F10|24h  | AH      |  40 | half  |    2042 |  0.031 | -0.06  | -0.06  |  0.155 | -0.069 |  0.028 |      546.974 |
| BT|sess_F10|24h  | AH      |  20 | skip  |     971 | -0.02  | -0.004 | -0.004 |  0.018 | -0.162 |  0.052 |     -113.79  |
| BT|sess_F10|24h  | AH      |  40 | skip  |    2042 |  0.077 |  0.102 |  0.102 |  0.193 | -0.161 |  0.079 |     1643.74  |
| BT|sess_F10|4h   | AH      |  20 | half  |     299 |  0     |  0.002 |  0.002 |  0     |  0.01  |  0.006 |      -11.811 |
| BT|sess_F10|4h   | AH      |  40 | half  |     521 |  0     |  0.029 |  0.029 | -0     |  0.017 |  0.006 |      -56.127 |
| BT|sess_F10|4h   | AH      |  20 | skip  |     299 |  0     | -0.051 | -0.051 |  0     | -0.001 |  0.041 |     -102.237 |
| BT|sess_F10|4h   | AH      |  40 | skip  |     521 |  0     |  0.018 |  0.018 |  0.002 | -0.023 |  0.041 |      150.917 |
| BT|sess_F5|24h   | AH      |  20 | half  |     542 |  0     |  0.016 |  0.016 |  0.027 | -0.065 |  0.019 |      181.228 |
| BT|sess_F5|24h   | AH      |  40 | half  |    1152 |  0.042 |  0.054 |  0.054 |  0.155 | -0.047 |  0.026 |      725.954 |
| BT|sess_F5|24h   | AH      |  20 | skip  |     542 |  0     | -0.043 | -0.043 |  0.018 | -0.142 |  0.053 |     -181.095 |
| BT|sess_F5|24h   | AH      |  40 | skip  |    1152 |  0.122 |  0.058 |  0.034 |  0.193 | -0.107 |  0.063 |     1664.04  |
| BT|sess_F5|4h    | AH      |  20 | half  |     176 |  0     |  0.002 |  0.002 |  0     |  0.01  |  0.006 |     -179.33  |
| BT|sess_F5|4h    | AH      |  40 | half  |     315 |  0     |  0.024 |  0.024 | -0     |  0.017 |  0.006 |     -109.687 |
| BT|sess_F5|4h    | AH      |  20 | skip  |     176 |  0     | -0.051 | -0.051 |  0     |  0.014 |  0.041 |     -434.417 |
| BT|sess_F5|4h    | AH      |  40 | skip  |     315 |  0     |  0.004 |  0.004 |  0.002 | -0.008 |  0.041 |     -243.269 |
| BT|swing_F10|24h | AH      |  20 | half  |    4701 |  0.025 | -0.005 | -0.005 |  0.104 | -0.093 | -0.007 |      569.821 |
| BT|swing_F10|24h | AH      |  40 | half  |    8593 |  0.156 |  0.081 |  0.081 |  0.057 | -0.081 |  0.065 |     1245.46  |
| BT|swing_F10|24h | AH      |  20 | skip  |    4701 |  0.23  |  0.075 |  0.075 |  0.21  | -0.099 | -0.091 |      536.406 |
| BT|swing_F10|24h | AH      |  40 | skip  |    8593 |  0.291 |  0.163 |  0.086 |  0.178 | -0.083 |  0.073 |     3281.78  |
| BT|swing_F10|4h  | AH      |  20 | half  |    1840 |  0.067 | -0.004 | -0.004 |  0.01  |  0.014 |  0.031 |      488.524 |
| BT|swing_F10|4h  | AH      |  40 | half  |    2819 |  0.185 |  0.081 |  0.081 |  0.031 | -0.016 |  0.03  |      896.558 |
| BT|swing_F10|4h  | AH      |  20 | skip  |    1840 |  0.189 |  0.029 |  0.029 |  0.028 |  0.066 | -0.056 |     1695.23  |
| BT|swing_F10|4h  | AH      |  40 | skip  |    2819 |  0.212 |  0.138 |  0.138 |  0.157 | -0.017 | -0.09  |     3310.99  |
| BT|swing_F5|24h  | AH      |  20 | half  |    3216 |  0.023 | -0.002 | -0.002 |  0.087 | -0.061 |  0.026 |      810.358 |
| BT|swing_F5|24h  | AH      |  40 | half  |    6021 |  0.158 |  0.058 |  0.058 |  0.013 | -0.044 |  0.119 |     1058.9   |
| BT|swing_F5|24h  | AH      |  20 | skip  |    3216 |  0.206 |  0.054 |  0.034 |  0.163 | -0.068 | -0.074 |      678.161 |
| BT|swing_F5|24h  | AH      |  40 | skip  |    6021 |  0.223 |  0.092 | -0.033 | -0.021 |  0.04  |  0.17  |     1176.57  |
| BT|swing_F5|4h   | AH      |  20 | half  |    1305 |  0.067 | -0     | -0     | -0.007 |  0.006 |  0.019 |      456.087 |
| BT|swing_F5|4h   | AH      |  40 | half  |    1988 |  0.157 |  0.046 |  0.046 | -0.013 | -0.003 |  0.018 |      796.732 |
| BT|swing_F5|4h   | AH      |  20 | skip  |    1305 |  0.178 |  0.007 |  0.007 | -0.019 |  0.034 | -0.128 |     1304.91  |
| BT|swing_F5|4h   | AH      |  40 | skip  |    1988 |  0.213 |  0.06  |  0.06  | -0.031 | -0.021 | -0.138 |     2140.43  |

Best cell BT swing F10 4h D40 skip (2,819 flagged of 88,490 rows) in detail:

### BT swing F10 4h D40 skip, lock 12R
L3M: cut +0.30 (maxDD week 202637, without it +0.25, LOO-month [+0.00,+0.30], boot90 [-0.03,+0.33]); $ delta +25.3k: Asia +5.1 London +22.5 NY-AM -6.2 NY-PM +3.9
L6M: cut +0.17 (maxDD week 202637, without it +0.13, LOO-month [+0.10,+0.41], boot90 [-0.06,+0.43]); $ delta +130.5k: Asia +74.8 London +53.0 NY-AM -2.3 NY-PM +5.1
HOLD: cut +0.48 (maxDD week 202613, without it +0.35, LOO-month [+0.29,+0.53], boot90 [+0.03,+0.47]); $ delta +277.6k: Asia +160.6 London +98.4 NY-AM +19.0 NY-PM -0.4
MID: cut +0.29 (maxDD week 202613, without it +0.10, LOO-month [+0.09,+0.29], boot90 [+0.09,+0.37]); $ delta +56.6k: Asia +36.1 London +32.6 NY-AM -7.0 NY-PM -5.1
PRE: cut +0.14 (maxDD week 202516, without it +0.16, LOO-month [+0.02,+0.19], boot90 [-0.10,+0.48]); $ delta +198.8k: Asia +102.1 London +38.0 NY-AM +57.5 NY-PM +1.2
X': cut +0.23 (maxDD week 202405, without it +0.17, LOO-month [+0.00,+0.32], boot90 [-0.02,+0.43]); $ delta +60.1k: Asia +52.3 London +49.1 NY-AM -39.5 NY-PM -1.8
| window   | vol T1        | vol T2         | vol T3         |
|:---------|:--------------|:---------------|:---------------|
| L6M      | +10.9k (2d)   | +47.2k (36d)   | +72.5k (93d)   |
| HOLD     | +18.6k (17d)  | +121.9k (76d)  | +137.2k (165d) |
| PRE      | +38.9k (121d) | +104.5k (122d) | +55.4k (121d)  |
| X'       | -3.1k (137d)  | +67.3k (72d)   | -4.1k (7d)     |
month chain: 43 months, positive 30, negative 9, zero 4; total +476.4k, best 2026-01 +105.2k, worst 2025-10 -42.7k, ex-best total +371.2k

### BT swing F10 4h D40 skip, lock None
L3M: cut +0.21 (maxDD week 202634, without it +0.06, LOO-month [-0.07,+0.30], boot90 [-0.15,+0.40]); $ delta +28.8k: Asia +12.1 London +20.9 NY-AM -6.7 NY-PM +2.4
L6M: cut +0.14 (maxDD week 202634, without it +0.08, LOO-month [+0.07,+0.21], boot90 [-0.08,+0.38]); $ delta +86.0k: Asia +34.1 London +43.9 NY-AM +1.1 NY-PM +6.8
HOLD: cut +0.14 (maxDD week 202634, without it +0.08, LOO-month [+0.11,+0.29], boot90 [+0.04,+0.34]); $ delta +172.2k: Asia +59.4 London +68.2 NY-AM +34.9 NY-PM +9.6
MID: cut +0.16 (maxDD week 202613, without it +0.31, LOO-month [+0.16,+0.31], boot90 [+0.16,+0.31]); $ delta +66.7k: Asia +31.3 London +23.9 NY-AM +10.4 NY-PM +1.1
PRE: cut -0.02 (maxDD week 202516, without it -0.12, LOO-month [-0.12,+0.18], boot90 [-0.08,+0.22]); $ delta +63.9k: Asia +63.3 London -11.1 NY-AM +10.0 NY-PM +1.7
X': cut -0.09 (maxDD week 202337, without it -0.15, LOO-month [-0.18,+0.01], boot90 [-0.60,+0.27]); $ delta +12.2k: Asia +63.2 London -6.7 NY-AM -43.1 NY-PM -1.3
| window   | vol T1        | vol T2        | vol T3         |
|:---------|:--------------|:--------------|:---------------|
| L6M      | +10.9k (2d)   | +15.2k (36d)  | +59.9k (93d)   |
| HOLD     | +31.1k (17d)  | +26.9k (76d)  | +114.1k (165d) |
| PRE      | -6.6k (121d)  | +41.6k (122d) | +28.8k (121d)  |
| X'       | +34.0k (137d) | -12.6k (72d)  | -9.2k (7d)     |
month chain: 43 months, positive 26, negative 13, zero 4; total +233.2k, best 2026-02 +35.8k, worst 2023-09 -45.4k, ex-best total +197.4k


Placebos (40 draws per kind; kinds A same-volume stratified skip, B random rows same count per day, C other-day same book x session; rank = share of placebo draws >= the cell, floor 1/41 = 0.024). cut = maxDD cut; dmean = weekly mean $k delta vs base:
| lock   | kind   |   draws | window   |   cell_cut |   placebo_mean_cut |   corrected |   rank_cut |   cell_dmean_k |   placebo_dmean_k |   rank_dmean |
|:-------|:-------|--------:|:---------|-----------:|-------------------:|------------:|-----------:|---------------:|------------------:|-------------:|
| 12R    | A      |      40 | L3M      |      0.303 |             -0.162 |       0.465 |      0.073 |          1.948 |            -2.044 |        0.146 |
| 12R    | A      |      40 | L6M      |      0.166 |             -0.163 |       0.33  |      0.195 |          4.834 |            -1.404 |        0.024 |
| 12R    | A      |      40 | HOLD     |      0.483 |              0.105 |       0.379 |      0.024 |          5.338 |            -0.791 |        0.024 |
| 12R    | A      |      40 | MID      |      0.287 |              0.075 |       0.212 |      0.146 |          4.717 |             1.888 |        0.22  |
| 12R    | A      |      40 | PRE      |      0.141 |              0.086 |       0.055 |      0.415 |          2.65  |             0.021 |        0.073 |
| 12R    | A      |      40 | X'       |      0.225 |             -0.065 |       0.29  |      0.122 |          1.365 |            -0.03  |        0.098 |
| 12R    | B      |      40 | L3M      |      0.303 |             -0.045 |       0.348 |      0.122 |          1.948 |            -1.439 |        0.049 |
| 12R    | B      |      40 | L6M      |      0.166 |             -0.085 |       0.252 |      0.098 |          4.834 |            -0.617 |        0.024 |
| 12R    | B      |      40 | HOLD     |      0.483 |              0.175 |       0.308 |      0.049 |          5.338 |             0.592 |        0.024 |
| 12R    | B      |      40 | MID      |      0.287 |              0.053 |       0.234 |      0.073 |          4.717 |             1.976 |        0.195 |
| 12R    | B      |      40 | PRE      |      0.141 |              0.074 |       0.067 |      0.39  |          2.65  |             0.515 |        0.098 |
| 12R    | B      |      40 | X'       |      0.225 |              0.01  |       0.215 |      0.073 |          1.365 |             0.458 |        0.22  |
| 12R    | C      |      40 | L3M      |      0.303 |             -0.125 |       0.429 |      0.122 |          1.948 |            -1.858 |        0.073 |
| 12R    | C      |      40 | L6M      |      0.166 |             -0.092 |       0.258 |      0.22  |          4.834 |            -1.102 |        0.024 |
| 12R    | C      |      40 | HOLD     |      0.483 |              0.144 |       0.339 |      0.024 |          5.338 |            -0.474 |        0.049 |
| 12R    | C      |      40 | MID      |      0.287 |              0.079 |       0.208 |      0.195 |          4.717 |             1.963 |        0.22  |
| 12R    | C      |      40 | PRE      |      0.141 |              0.082 |       0.058 |      0.39  |          2.65  |             0.04  |        0.122 |
| 12R    | C      |      40 | X'       |      0.225 |              0.061 |       0.165 |      0.293 |          1.365 |             0.547 |        0.341 |
| none   | A      |      40 | L3M      |      0.212 |             -0.138 |       0.35  |      0.146 |          2.212 |            -1.189 |        0.146 |
| none   | A      |      40 | L6M      |      0.138 |              0.044 |       0.094 |      0.439 |          3.184 |            -0.935 |        0.098 |
| none   | A      |      40 | HOLD     |      0.138 |             -0.065 |       0.203 |      0.146 |          3.311 |            -0.94  |        0.024 |
| none   | A      |      40 | MID      |      0.157 |             -0.019 |       0.176 |      0.244 |          5.557 |            -0.101 |        0.049 |
| none   | A      |      40 | PRE      |     -0.017 |             -0.134 |       0.117 |      0.317 |          0.851 |            -0.633 |        0.098 |
| none   | A      |      40 | X'       |     -0.09  |             -0.007 |      -0.084 |      0.561 |          0.276 |             0.023 |        0.366 |
| none   | B      |      40 | L3M      |      0.212 |             -0.02  |       0.232 |      0.122 |          2.212 |            -1.141 |        0.049 |
| none   | B      |      40 | L6M      |      0.138 |              0.026 |       0.112 |      0.195 |          3.184 |            -0.285 |        0.024 |
| none   | B      |      40 | HOLD     |      0.138 |             -0.005 |       0.143 |      0.098 |          3.311 |             0.08  |        0.024 |
| none   | B      |      40 | MID      |      0.157 |              0.124 |       0.032 |      0.415 |          5.557 |             1.536 |        0.049 |
| none   | B      |      40 | PRE      |     -0.017 |              0.022 |      -0.039 |      0.659 |          0.851 |             0.081 |        0.146 |
| none   | B      |      40 | X'       |     -0.09  |              0.067 |      -0.157 |      0.878 |          0.276 |             0.445 |        0.561 |
| none   | C      |      40 | L3M      |      0.212 |             -0.121 |       0.333 |      0.098 |          2.212 |            -1.436 |        0.073 |
| none   | C      |      40 | L6M      |      0.138 |              0.042 |       0.096 |      0.244 |          3.184 |            -1.046 |        0.024 |
| none   | C      |      40 | HOLD     |      0.138 |             -0.064 |       0.202 |      0.049 |          3.311 |            -0.95  |        0.024 |
| none   | C      |      40 | MID      |      0.157 |             -0.021 |       0.177 |      0.244 |          5.557 |             0.1   |        0.122 |
| none   | C      |      40 | PRE      |     -0.017 |             -0.101 |       0.085 |      0.39  |          0.851 |            -0.684 |        0.122 |
| none   | C      |      40 | X'       |     -0.09  |             -0.002 |      -0.088 |      0.659 |          0.276 |             0.17  |        0.512 |

Reading: the dollars are the strongest part: the cell's weekly mean beats its placebos at the rank floor in L6M and HOLD under 12R (0.024 on all three kinds) and in L6M / HOLD / MID under lock None (0.024-0.12), the monthly dollar chain is +476k with 30 positive / 9 negative months (lock 12R) and +233k with 26 / 13 (lock None), and neither depends on one month (ex-best month +371k / +197k). The maxDD cut is real but not extreme: lock 12R L3M +30%, L6M +17%, HOLD +48%, MID +29%, PRE +14%, X' +23% (placebo-corrected +21..+47% in the recent windows, ranks 0.02-0.22 there, 0.07-0.42 in PRE/X'); lock None L3M +21%, L6M +14%, HOLD +14%, MID +16%, PRE -2%, X' -9% (cut ranks 0.05-0.44), the maxDD week is 2026-W34/W37 and without it the lock-None cut falls to +6..+8% (L3M/L6M/HOLD), i.e. ONE-WEEK on the drawdown, while the dollar gain does not. Asia carries +60% of the dollars and London +40% in L6M/HOLD (lock 12R); NY-AM is flat. Vol terciles: the dollars come from the middle and top terciles. Definition sensitivity: F5 is weaker (lock None L6M +1..+9%), the 24 h keep similar, D20 positive in most windows; half instead of skip gives the same sign with about half the size; BEHIND/AT are not useful. **Label: LEAD (recent mean-positive and drawdown-positive in both lock frames; PRE/X' only positive with the 12R lock; the lock-None drawdown cut is ONE-WEEK; not RISK-KEEP).**

LIVE definition (what D7 computes): from its own tape keep 5-min bars (clock aligned); a swing high / low is a 5-bar fractal (bar higher / lower than the 2 bars either side), knowable at the close of the second bar after it; keep the last 3 swing highs and 3 swing lows; a swing high L is BROKEN when price trades >= L + 10 pts (a swing low: <= L - 10), at that second a flip level is created at L (support after an up-break, resistance after a down-break), kept 4 h, fresh until price returns to L after leaving it by 0.5 pt. Signal rule: at the entry second skip the base entry if a fresh flip level lies between entry and target within 40 pts (lines with p equal to entry count as 0). Prior-day and session lines are not used (the swing set alone carries it). No daily file needed. Forward shadow log: same fields as the PUL spec with flag_BT40, nearest flip level price / age / break size (see FORWARD_SHADOW_ZONES_SPEC.md; to be extended).

## 2. RXL reaction levels (density bands and composite HVN / LVN)
The density bands flag 25-55k of 88k rows and the HVN/LVN sets 4-22k, so their skip / half cells are mostly volume effects. Top cells by min(L6M, PRE, X' cut), lock 12R and lock None:
| stream          | frame   |   D | act   |   nflag |    L3M |    L6M |   HOLD |    MID |    PRE |     X' |   dmean_HOLD |
|:----------------|:--------|----:|:------|--------:|-------:|-------:|-------:|-------:|-------:|-------:|-------------:|
| RXL|lvn_5d|1d   | AH      |  40 | half  |   22309 | -0.167 |  0.211 |  0.395 |  0.081 |  0.563 |  0.054 |     -398.471 |
| RXL|hvn_60d|1d  | AT      |   2 | up    |    4045 | -0.075 |  0.031 |  0.083 |  0.105 |  0.082 |  0.023 |     -405.767 |
| RXL|lvn_5d|1d   | AH      |  20 | half  |   15943 | -0.134 |  0.002 |  0.307 |  0.086 |  0.176 |  0.123 |      204.178 |
| RXL|dens_p95|1h | AH      |  20 | half  |   25297 | -0.149 | -0.002 |  0.379 |  0.172 |  0.186 |  0.143 |     -729.148 |
| RXL|dens_p95|1h | AH      |  20 | skip  |   25297 | -0.489 |  0.196 |  0.453 |  0.25  | -0.01  |  0.117 |    -6346.34  |
| RXL|hvn_60d|1d  | AH      |  20 | skip  |   11397 | -0.108 | -0.013 |  0.372 |  0.29  |  0.263 |  0.025 |       -9.713 |
| RXL|hvn_60d|1d  | AH      |  40 | skip  |   16300 |  0.045 |  0.211 |  0.303 |  0.196 |  0.06  | -0.03  |    -3487.92  |
| RXL|hvn_60d|1d  | BH      |  20 | half  |   12992 | -0.089 | -0.043 |  0.353 |  0.305 |  0.064 |  0.183 |    -2358.17  |
| RXL|hvn_20d|1d  | AT      |   2 | up    |    4098 |  0.061 |  0.207 |  0.222 |  0.128 |  0.067 | -0.052 |     1485.69  |
| RXL|hvn_5d|1d   | AH      |  40 | half  |   16735 | -0.067 | -0.086 |  0.304 |  0.135 |  0.079 |  0.638 |    -4910.83  |
| RXL|lvn_20d|1d  | BH      |  20 | skip  |   16403 | -0.38  | -0.028 |  0.168 |  0.233 | -0.075 | -0.095 |    -3026.88  |
| RXL|hvn_5d|1d   | AT      |   2 | up    |    4077 |  0.037 |  0.074 |  0.283 | -0.054 | -0.044 | -0.099 |     2603.15  |

| stream          | frame   |   D | act   |   nflag |    L3M |    L6M |   HOLD |    MID |    PRE |     X' |   dmean_HOLD |
|:----------------|:--------|----:|:------|--------:|-------:|-------:|-------:|-------:|-------:|-------:|-------------:|
| RXL|lvn_20d|1d  | AH      |  40 | half  |   22230 |  0.133 |  0.196 |  0.196 | -0.116 |  0.18  |  0.156 |     -123.71  |
| RXL|dens_p90|1h | AH      |  40 | half  |   54723 | -0.502 |  0.26  |  0.26  |  0.309 |  0.184 |  0.138 |    -3301.83  |
| RXL|dens_p90|1h | AH      |  40 | skip  |   54723 | -1.002 |  0.128 |  0.128 |  0.476 |  0.292 |  0.372 |   -10836.4   |
| RXL|lvn_20d|1d  | AH      |  20 | skip  |   15982 | -0.037 |  0.265 | -0.483 | -1.002 |  0.083 |  0.481 |    -3413.34  |
| RXL|lvn_20d|1d  | AH      |  40 | skip  |   22230 |  0.374 |  0.249 | -0.301 | -0.589 |  0.048 |  0.114 |    -3291.17  |
| RXL|hvn_20d|1d  | BH      |  20 | half  |   13444 | -0.351 |  0.113 |  0.113 | -0.033 |  0.098 | -0.009 |    -4251.53  |
| RXL|lvn_5d|1d   | AT      |   2 | up    |    5800 | -0.301 | -0.024 | -0.024 |  0.125 |  0.052 | -0.017 |     1379.59  |
| RXL|lvn_60d|1d  | AH      |  20 | skip  |   15750 | -0.679 | -0.025 | -0.025 | -0.479 |  0.152 |  0.48  |    -1173.08  |
| RXL|hvn_60d|1d  | AH      |  20 | half  |   11397 | -0.052 | -0.031 | -0.031 | -0.249 |  0.016 |  0.083 |     -650.912 |
| RXL|dens_p95|1h | AH      |  40 | half  |   40481 | -0.03  |  0.414 |  0.414 |  0.184 | -0.056 |  0.128 |     -570.782 |
| RXL|hvn_60d|1d  | BH      |  20 | half  |   12992 | -0.115 | -0.061 | -0.061 |  0.138 |  0.184 |  0.011 |    -2390.75  |
| RXL|lvn_5d|1d   | AH      |  20 | half  |   15943 | -0.1   | -0.074 | -0.074 | -0.168 |  0.223 | -0.059 |    -1496.45  |

Placebos for the best RXL cell, RXL lvn_20d (composite low-volume nodes of the previous 20 days) AHEAD D40 HALF (25% of rows flagged; 30 draws per kind; rank floor 0.032):
| lock   | kind   |   draws | window   |   cell_cut |   placebo_mean |   corrected |   rank_cut |   rank_dmean |
|:-------|:-------|--------:|:---------|-----------:|---------------:|------------:|-----------:|-------------:|
| 12R    | A      |      30 | L3M      |      0.036 |          0.014 |       0.022 |      0.516 |        0.097 |
| 12R    | A      |      30 | L6M      |      0.122 |         -0.104 |       0.226 |      0.355 |        0.032 |
| 12R    | A      |      30 | HOLD     |      0.225 |          0.241 |      -0.017 |      0.677 |        0.387 |
| 12R    | A      |      30 | MID      |      0.061 |          0.245 |      -0.184 |      0.806 |        0.903 |
| 12R    | A      |      30 | PRE      |      0.416 |          0.023 |       0.393 |      0.032 |        0.71  |
| 12R    | A      |      30 | X'       |     -0.315 |          0.128 |      -0.443 |      0.935 |        0.935 |
| 12R    | B      |      30 | L3M      |      0.036 |         -0.12  |       0.156 |      0.323 |        0.097 |
| 12R    | B      |      30 | L6M      |      0.122 |         -0.159 |       0.281 |      0.129 |        0.032 |
| 12R    | B      |      30 | HOLD     |      0.225 |          0.245 |      -0.02  |      0.548 |        0.677 |
| 12R    | B      |      30 | MID      |      0.061 |          0.157 |      -0.095 |      0.71  |        0.935 |
| 12R    | B      |      30 | PRE      |      0.416 |          0.293 |       0.123 |      0.194 |        0.968 |
| 12R    | B      |      30 | X'       |     -0.315 |          0.041 |      -0.355 |      0.903 |        0.935 |
| 12R    | C      |      30 | L3M      |      0.036 |          0.02  |       0.016 |      0.548 |        0.097 |
| 12R    | C      |      30 | L6M      |      0.122 |         -0.102 |       0.224 |      0.161 |        0.065 |
| 12R    | C      |      30 | HOLD     |      0.225 |          0.289 |      -0.064 |      0.645 |        0.484 |
| 12R    | C      |      30 | MID      |      0.061 |          0.3   |      -0.238 |      0.935 |        0.935 |
| 12R    | C      |      30 | PRE      |      0.416 |          0.054 |       0.361 |      0.129 |        0.548 |
| 12R    | C      |      30 | X'       |     -0.315 |          0.115 |      -0.43  |      0.903 |        0.903 |
| none   | A      |      30 | L3M      |      0.133 |         -0.139 |       0.272 |      0.194 |        0.032 |
| none   | A      |      30 | L6M      |      0.196 |          0.069 |       0.127 |      0.258 |        0.065 |
| none   | A      |      30 | HOLD     |      0.196 |          0.033 |       0.163 |      0.161 |        0.032 |
| none   | A      |      30 | MID      |     -0.116 |          0.015 |      -0.131 |      0.71  |        0.645 |
| none   | A      |      30 | PRE      |      0.18  |         -0.099 |       0.279 |      0.065 |        0.065 |
| none   | A      |      30 | X'       |      0.156 |          0.095 |       0.061 |      0.355 |        0.774 |
| none   | B      |      30 | L3M      |      0.133 |         -0.113 |       0.246 |      0.097 |        0.032 |
| none   | B      |      30 | L6M      |      0.196 |         -0.071 |       0.266 |      0.129 |        0.097 |
| none   | B      |      30 | HOLD     |      0.196 |         -0.092 |       0.287 |      0.065 |        0.226 |
| none   | B      |      30 | MID      |     -0.116 |          0.032 |      -0.148 |      0.742 |        0.774 |
| none   | B      |      30 | PRE      |      0.18  |          0.064 |       0.116 |      0.355 |        0.548 |
| none   | B      |      30 | X'       |      0.156 |          0.278 |      -0.122 |      0.71  |        1     |
| none   | C      |      30 | L3M      |      0.133 |         -0.085 |       0.218 |      0.129 |        0.065 |
| none   | C      |      30 | L6M      |      0.196 |          0.099 |       0.097 |      0.323 |        0.097 |
| none   | C      |      30 | HOLD     |      0.196 |          0.058 |       0.138 |      0.226 |        0.129 |
| none   | C      |      30 | MID      |     -0.116 |          0.075 |      -0.191 |      0.774 |        0.839 |
| none   | C      |      30 | PRE      |      0.18  |         -0.089 |       0.269 |      0.097 |        0.097 |
| none   | C      |      30 | X'       |      0.156 |          0.062 |       0.094 |      0.323 |        0.871 |

Reading: with the lock off the RXL lvn_20d half cell cuts L3M +13%, L6M +20%, HOLD +20%, PRE +18%, X' +16% but MID -12%; placebo-corrected +10..+29% with cut ranks 0.06-0.36 (not significant) and weekly-dollar ranks 0.03-0.10 in L3M/L6M/HOLD; with the 12R lock the signs flip in X' (-32%) and MID. Label: FRAGILE / VOLUME (a quarter of all rows halved; lock-dependent). The density bands (flagging 55k rows) and HVN sets are DEAD (cuts are volume effects or sign-unstable across windows).

## Verdict (V13X, lock None headline)
* Mancini failed breakdown / back-test (S4b's 24 streams + the SWP failed-breakdown family): DEAD.
* BT flip levels (swing level broken by >= 10 pts, skip ahead within 40 pts, 4 h): LEAD - recent windows L3M/L6M/HOLD/MID all +14..+21% maxDD, +233k dollars over the 43 months (26 positive / 13 negative months), weekly-mean placebo ranks 0.024-0.12; PRE/X' about 0 with the lock off (+14% / +23% with the 12R lock); the lock-None drawdown cut is ONE-WEEK (W34), the dollar gain is not. Needs: 100-draw placebos, the noise-band rule, a purged walk-forward on D (Z3), and the forward shadow log.
* RXL density bands / HVN / LVN: DEAD or FRAGILE.


## 3. BT swing flip: ROW-LEVEL (mean / dollar) tests, immune to the lock phase (ZL-1, lock None headline, V13X taken trades, first-order dollars = -sum of the flagged rows' base net)
Base taken-trade tables: /mnt/l2/l2vast/ds3_zones3_new/zl1/base_rows_none.pkl and base_rows_lock12.pkl (drow, net $, ld, book, sess). Placebos (200 draws): A same count per book x session over the sample, B same count per day, C each flagged row replaced by a random row of the same book x session on a different day; rank = share of placebo sums at least as negative as the flagged sum (low = good).

### lock None: BT|swing_F10|4h AHEAD D40 skip; taken trades 18716, flagged 1032 (5.5%)

| window   |   n_flag |   flag_sum_k |   flag_mean |   unflag_mean |   flag_hit |   unflag_hit |   flag_ci_lo_k |   flag_ci_hi_k |   rank_A |   rank_B |   rank_C |   plcA_mean_k |   plcB_mean_k |   plcC_mean_k |
|:---------|---------:|-------------:|------------:|--------------:|-----------:|-------------:|---------------:|---------------:|---------:|---------:|---------:|--------------:|--------------:|--------------:|
| L3M      |       94 |      -38.45  |    -409.048 |       137.087 |      0.372 |        0.47  |        -79.359 |          0.141 |    0.045 |    0.03  |    0.075 |        17.688 |        16.445 |        12.447 |
| L6M      |      203 |      -86.234 |    -424.798 |       192.203 |      0.355 |        0.465 |       -142.207 |        -31.156 |    0.005 |    0.02  |    0.005 |        47.443 |        29.846 |        45.206 |
| HOLD     |      359 |      -99.631 |    -277.524 |       182.324 |      0.373 |        0.464 |       -182.691 |        -19.467 |    0.01  |    0.01  |    0.01  |        72.082 |        53.596 |        75.304 |
| MID      |       84 |      -29.867 |    -355.565 |       105.412 |      0.405 |        0.453 |        -73.902 |         14.005 |    0.179 |    0.109 |    0.144 |         2.224 |         9.383 |         6.672 |
| PRE      |      413 |      -89.363 |    -216.375 |       129.902 |      0.438 |        0.476 |       -192.92  |         12.364 |    0.045 |    0.149 |    0.025 |        20.352 |        -9.519 |        17.089 |
| X'       |      156 |      -40.829 |    -261.726 |        -5.069 |      0.487 |        0.495 |       -112.066 |         28.157 |    0.164 |    0.423 |    0.174 |        -7.693 |       -33.252 |        -5.457 |

flagged rows by book|session in HOLD (sum $k, n, mean $):
| key   |   size |   sum |    mean |
|:------|-------:|------:|--------:|
| HM|0  |     33 |   5.6 |   169.8 |
| HM|3  |      4 |   0.3 |    65.4 |
| KB|0  |     82 |  -6.3 |   -76.7 |
| KB|1  |     66 | -22.6 |  -341.7 |
| KB|3  |     15 |  -6.4 |  -429.2 |
| KB|4  |      9 |  -3.4 |  -379.1 |
| MV|1  |     37 |  -1.1 |   -28.8 |
| MV|3  |      5 |  -1   |  -208.9 |
| PB|0  |      5 |  -2.2 |  -436.3 |
| PE|0  |     38 | -15.4 |  -404   |
| PE|1  |     31 | -26.4 |  -850.5 |
| PE|3  |      2 |   8.2 |  4100.1 |
| SM|0  |     10 |  -6.2 |  -622   |
| SM|1  |     22 | -22.8 | -1035.3 |

flagged rows by book|session in PRE (sum $k, n, mean $):
| key   |   size |   sum |    mean |
|:------|-------:|------:|--------:|
| HM|0  |     34 | -12.6 |  -371.8 |
| HM|3  |     14 |  -4.8 |  -339.6 |
| KB|0  |     76 | -18.4 |  -241.6 |
| KB|1  |     72 |   8.8 |   121.7 |
| KB|3  |     30 |   4.5 |   151   |
| KB|4  |     23 |  -2.9 |  -126.7 |
| MV|1  |     18 |  -5.1 |  -280.8 |
| MV|3  |      7 |  -4.1 |  -591.7 |
| PB|0  |      4 |   3.5 |   867.3 |
| PE|0  |     53 | -40.1 |  -756.6 |
| PE|1  |     31 | -10.9 |  -350.6 |
| PE|3  |      9 | -10.6 | -1176.5 |
| SM|0  |     14 |  -2.3 |  -161   |
| SM|1  |     28 |   5.6 |   198.4 |

### lock 12R: BT|swing_F10|4h AHEAD D40 skip; taken trades 12193, flagged 677 (5.6%)

| window   |   n_flag |   flag_sum_k |   flag_mean |   unflag_mean |   flag_hit |   unflag_hit |   flag_ci_lo_k |   flag_ci_hi_k |   rank_A |   rank_B |   rank_C |   plcA_mean_k |   plcB_mean_k |   plcC_mean_k |
|:---------|---------:|-------------:|------------:|--------------:|-----------:|-------------:|---------------:|---------------:|---------:|---------:|---------:|--------------:|--------------:|--------------:|
| L3M      |       57 |      -40.98  |    -718.949 |       232.495 |      0.281 |        0.491 |        -78.166 |         -8.176 |    0.025 |    0.02  |    0.025 |        12.16  |         5.143 |        10.06  |
| L6M      |      127 |      -99.343 |    -782.228 |       267.734 |      0.276 |        0.473 |       -145.961 |        -56.023 |    0.005 |    0.005 |    0.005 |        38.204 |         7.339 |        36.899 |
| HOLD     |      239 |     -129.881 |    -543.435 |       238.402 |      0.326 |        0.47  |       -199.686 |        -59.673 |    0.005 |    0.01  |    0.01  |        55.679 |        24.95  |        57.836 |
| MID      |       62 |      -44.33  |    -715.003 |        95.38  |      0.355 |        0.453 |        -79.193 |        -10.59  |    0.06  |    0.04  |    0.085 |        -3.019 |         7.322 |         0.534 |
| PRE      |      239 |     -104.799 |    -438.488 |       102.479 |      0.402 |        0.466 |       -178.509 |        -34.868 |    0.015 |    0.095 |    0.03  |         4.194 |       -40.559 |         5.673 |
| X'       |      108 |      -67.131 |    -621.582 |       -68.191 |      0.463 |        0.493 |       -119.634 |        -18.466 |    0.035 |    0.159 |    0.04  |       -14.473 |       -38.366 |       -12.629 |

flagged rows by book|session in HOLD (sum $k, n, mean $):
| key   |   size |   sum |    mean |
|:------|-------:|------:|--------:|
| HM|0  |     17 |   1.2 |    67.7 |
| HM|3  |      3 |   1   |   337.9 |
| KB|0  |     52 |   0.5 |     9   |
| KB|1  |     48 | -19.6 |  -407.4 |
| KB|3  |     10 |  -4   |  -395.2 |
| KB|4  |      7 |  -3.5 |  -497.6 |
| MV|1  |     22 |  -7.5 |  -340.5 |
| MV|3  |      3 |  -0.4 |  -130.4 |
| PB|0  |      4 |  -4.6 | -1142.9 |
| PE|0  |     27 | -22.9 |  -847.1 |
| PE|1  |     20 | -40.1 | -2006.7 |
| PE|3  |      2 |   8.2 |  4100.1 |
| SM|0  |      7 |  -9   | -1281.7 |
| SM|1  |     17 | -29.3 | -1723.3 |

flagged rows by book|session in PRE (sum $k, n, mean $):
| key   |   size |   sum |    mean |
|:------|-------:|------:|--------:|
| HM|0  |     22 | -17.1 |  -776.4 |
| HM|3  |      9 |  -4.8 |  -529.4 |
| KB|0  |     46 | -16.1 |  -350.1 |
| KB|1  |     39 |  -2.2 |   -56.1 |
| KB|3  |     21 |   1.2 |    55   |
| KB|4  |     12 |   4.7 |   388.8 |
| MV|1  |     11 |  -5.5 |  -500.2 |
| MV|3  |      4 |  -1.7 |  -418.8 |
| PB|0  |      2 |  -0   |   -17.6 |
| PE|0  |     33 | -22.1 |  -670.9 |
| PE|1  |     14 | -19.3 | -1376.4 |
| PE|3  |      4 |  -6   | -1507.7 |
| SM|0  |      5 | -10.5 | -2090.9 |
| SM|1  |     17 |  -5.4 |  -316   |

## 4. Plateau and purged walk-forward of the DEFINITION (swing 5m/15m/1h x break 5/10/15/20 x keep 1h/4h/24h x reach 20/30/40/60 = 144 configs; streams BTC|<tf>_F<F>|<keep>)
### lock None: parameter plateau of the flip-level skip (saved $k = -sum of the flagged rows' base net; 144 configs = swing ['5m', '15m', '1h'] x break [5, 10, 15, 20] x keep ['1h', '4h', '24h'] x reach [20, 30, 40, 60])

share of configs with positive saved dollars: L6M 80%, HOLD 89%, MID 94%, PRE 60%, X' 86%; all four of L6M/HOLD/PRE/X': 41%

median saved $k by swing timeframe:
| TF   |   L6M |   HOLD |   PRE |   X' |
|:-----|------:|-------:|------:|-----:|
| 15m  |  14   |   24.9 |  13.5 |  8.6 |
| 1h   |   0   |    6.6 |  -1.7 |  8.5 |
| 5m   |  44.2 |   37.3 |  30.4 | 22   |

median saved $k by F:
|   F |   L6M |   HOLD |   PRE |   X' |
|----:|------:|-------:|------:|-----:|
|   5 |  12.7 |   14.3 |   6   |  7.5 |
|  10 |  12   |   10   |  15.1 |  8.9 |
|  15 |  13.8 |   25.2 |   7.2 |  9.2 |
|  20 |  11.6 |   19.4 |  -1.1 | 13   |

median saved $k by keep:
| keep   |   L6M |   HOLD |   PRE |   X' |
|:-------|------:|-------:|------:|-----:|
| 1h     |   6.9 |    8.3 |   6.2 |  6.2 |
| 24h    |  21   |   36.7 | -29.8 | 20.8 |
| 4h     |  17.6 |   27.8 |  26.3 |  9.6 |

median saved $k by D:
|   D |   L6M |   HOLD |   PRE |   X' |
|----:|------:|-------:|------:|-----:|
|  20 |   7.4 |    5.6 |  12.4 | 10.5 |
|  30 |  12   |   10.7 |   1.4 |  8.5 |
|  40 |  12.1 |   32   |   0.2 | 10.4 |
|  60 |  16.2 |   18.9 |   7.6 |  8.4 |

reference config (5m, break 10, 4h, reach 40):
| TF   |   F | keep   |   D |   n_flag |   L6M |   HOLD |   MID |   PRE |   X' |   hit_all |
|:-----|----:|:-------|----:|---------:|------:|-------:|------:|------:|-----:|----------:|
| 5m   |  10 | 4h     |  40 |     1101 |  88.8 |  102.2 |  29.4 |  84.1 | 24.4 |     190.5 |

**Walk-forward (12-month trailing choice of the whole configuration, apply to next month; 2024-01..2026-10; saved $k):**

|                                                  |   L6M |   HOLD |   MID |   2024-25 |   all |
|:-------------------------------------------------|------:|-------:|------:|----------:|------:|
| walk-forward (skips only if trailing saving > 0) |  36.5 |   47   |  23.1 |      18.1 |  77.5 |
| fixed reference config                           |  88.8 |  102.2 |  29.4 |      29.9 | 153.1 |
| mean of all 144 configs (random choice)          |  23.1 |   30.3 |  13.7 |       6.2 |  34.1 |
| best config in hindsight each month              | 222.4 |  428.7 | 129.7 |     627.6 | 994.2 |

months with positive walk-forward saving: 15 / 31 active; fixed-config positive months 19 / 31

most-chosen configs: ('5m', np.int64(20), '4h', np.int64(60)) x7; ('5m', np.int64(10), '1h', np.int64(20)) x5; ('5m', np.int64(10), '4h', np.int64(20)) x4; ('15m', np.int64(20), '24h', np.int64(40)) x4

**Walk-forward (6-month trailing choice of the whole configuration, apply to next month; 2024-01..2026-10; saved $k):**

|                                                  |   L6M |   HOLD |   MID |   2024-25 |    all |
|:-------------------------------------------------|------:|-------:|------:|----------:|-------:|
| walk-forward (skips only if trailing saving > 0) |  15.6 |   79.3 |  59.3 |     -39.2 |    9.9 |
| fixed reference config                           |  88.8 |  102.2 |  29.4 |      33.3 |  156.5 |
| mean of all 144 configs (random choice)          |  23.1 |   30.3 |  13.7 |      -5.5 |   22.4 |
| best config in hindsight each month              | 222.4 |  428.7 | 129.7 |     677.7 | 1044.3 |

months with positive walk-forward saving: 14 / 34 active; fixed-config positive months 20 / 34

most-chosen configs: ('5m', np.int64(15), '4h', np.int64(60)) x4; ('5m', np.int64(20), '4h', np.int64(60)) x4; ('15m', np.int64(15), '24h', np.int64(40)) x3; ('5m', np.int64(15), '24h', np.int64(40)) x2

### lock 12R: parameter plateau of the flip-level skip (saved $k = -sum of the flagged rows' base net; 144 configs = swing ['5m', '15m', '1h'] x break [5, 10, 15, 20] x keep ['1h', '4h', '24h'] x reach [20, 30, 40, 60])

share of configs with positive saved dollars: L6M 88%, HOLD 88%, MID 94%, PRE 60%, X' 97%; all four of L6M/HOLD/PRE/X': 45%

median saved $k by swing timeframe:
| TF   |   L6M |   HOLD |   PRE |   X' |
|:-----|------:|-------:|------:|-----:|
| 15m  |  11.2 |   24   |  11.2 | 11.8 |
| 1h   |   2.7 |    7.8 |  -0.2 |  2.9 |
| 5m   |  43.5 |   44.4 |  42.8 | 37.1 |

median saved $k by F:
|   F |   L6M |   HOLD |   PRE |   X' |
|----:|------:|-------:|------:|-----:|
|   5 |   9.6 |   11.8 |  11.7 | 13.3 |
|  10 |  10.3 |   10.1 |  21.2 | 32.5 |
|  15 |  14.3 |   21.6 |  11.6 | 29.4 |
|  20 |  11.4 |   15   |   2.6 | 19.4 |

median saved $k by keep:
| keep   |   L6M |   HOLD |   PRE |   X' |
|:-------|------:|-------:|------:|-----:|
| 1h     |   7.2 |    6.1 |  -0.2 |  5.2 |
| 24h    |  14.9 |   24.3 |  -2.8 | 44.5 |
| 4h     |  25.5 |   29.7 |  48.5 | 10.7 |

median saved $k by D:
|   D |   L6M |   HOLD |   PRE |   X' |
|----:|------:|-------:|------:|-----:|
|  20 |   7.7 |    4.7 |  12   | 17.8 |
|  30 |   8.1 |    9   |   0.8 | 12.7 |
|  40 |  12.3 |   21   |   0.5 | 18.9 |
|  60 |  19.4 |   19.3 |  15.8 | 22   |

reference config (5m, break 10, 4h, reach 40):
| TF   |   F | keep   |   D |   n_flag |   L6M |   HOLD |   MID |   PRE |   X' |   hit_all |
|:-----|----:|:-------|----:|---------:|------:|-------:|------:|------:|-----:|----------:|
| 5m   |  10 | 4h     |  40 |      721 | 101.9 |  132.4 |  40.9 |  99.5 | 58.6 |     287.1 |

**Walk-forward (12-month trailing choice of the whole configuration, apply to next month; 2024-01..2026-10; saved $k):**

|                                                  |   L6M |   HOLD |   MID |   2024-25 |   all |
|:-------------------------------------------------|------:|-------:|------:|----------:|------:|
| walk-forward (skips only if trailing saving > 0) |  30.8 |   68.1 |  48.3 |      55.2 | 134.5 |
| fixed reference config                           | 101.9 |  132.4 |  40.9 |      50.5 | 204.7 |
| mean of all 144 configs (random choice)          |  23.5 |   28.2 |  14.4 |      12.7 |  42.7 |
| best config in hindsight each month              | 196.3 |  365.7 | 111   |     545.2 | 864.3 |

months with positive walk-forward saving: 20 / 31 active; fixed-config positive months 22 / 31

most-chosen configs: ('5m', np.int64(10), '4h', np.int64(60)) x6; ('5m', np.int64(10), '4h', np.int64(20)) x5; ('5m', np.int64(20), '4h', np.int64(60)) x5; ('5m', np.int64(15), '4h', np.int64(60)) x4

**Walk-forward (6-month trailing choice of the whole configuration, apply to next month; 2024-01..2026-10; saved $k):**

|                                                  |   L6M |   HOLD |   MID |   2024-25 |   all |
|:-------------------------------------------------|------:|-------:|------:|----------:|------:|
| walk-forward (skips only if trailing saving > 0) | 101.5 |  147   |  56.8 |       2.1 | 126.8 |
| fixed reference config                           | 101.9 |  132.4 |  40.9 |      73.6 | 227.8 |
| mean of all 144 configs (random choice)          |  23.5 |   28.2 |  14.4 |       7.1 |  37.1 |
| best config in hindsight each month              | 196.3 |  365.7 | 111   |     593.1 | 912.2 |

months with positive walk-forward saving: 22 / 34 active; fixed-config positive months 24 / 34

most-chosen configs: ('5m', np.int64(10), '4h', np.int64(20)) x4; ('5m', np.int64(10), '24h', np.int64(60)) x4; ('5m', np.int64(20), '4h', np.int64(60)) x3; ('5m', np.int64(15), '4h', np.int64(60)) x3

## 5. Separate causal audit of the BT stream: 100 random rows (BT swing F10 4h/24h and F5 4h) recomputed from raw 1-s rows truncated at the end of the event bin with a 4-day warm-up: 100 / 100 reproduced, max level diff 0.


## 6. Phase-averaged maxDD (Z3 estimator) for BT swing F10 4h D40 skip
### Phase-averaged maxDD (Z3 estimator: lock-reset week key shifted -2..+2 label days, 5 phases; V13X) for BT swing F10 4h D40 skip, with 8 same-volume random-layer placebos (kind A) per phase

**lock None**
| window   |   cut_mean |   cut_min |   cut_max |   phases_pos |   placebo_mean |   placebo_sd_of_draw_means |   placebo_draws |   corrected |   rank |
|:---------|-----------:|----------:|----------:|-------------:|---------------:|---------------------------:|----------------:|------------:|-------:|
| L3M      |      0.232 |     0.19  |     0.267 |            5 |         -0.133 |                      0.176 |               8 |       0.365 |  0.111 |
| L6M      |      0.013 |    -0.089 |     0.138 |            2 |          0.031 |                      0.225 |               8 |      -0.018 |  0.667 |
| HOLD     |      0.013 |    -0.089 |     0.138 |            2 |         -0.013 |                      0.176 |               8 |       0.025 |  0.667 |
| MID      |      0.131 |     0.041 |     0.168 |            5 |         -0.145 |                      0.26  |               8 |       0.277 |  0.333 |
| PRE      |     -0.026 |    -0.042 |    -0.014 |            0 |         -0.053 |                      0.12  |               8 |       0.026 |  0.444 |
| X'       |     -0.058 |    -0.172 |     0.057 |            2 |         -0.011 |                      0.24  |               8 |      -0.047 |  0.444 |

**lock 12R**
| window   |   cut_mean |   cut_min |   cut_max |   phases_pos |   placebo_mean |   placebo_sd_of_draw_means |   placebo_draws |   corrected |   rank |
|:---------|-----------:|----------:|----------:|-------------:|---------------:|---------------------------:|----------------:|------------:|-------:|
| L3M      |      0.17  |    -0.113 |     0.319 |            4 |         -0.032 |                      0.16  |               8 |       0.202 |  0.111 |
| L6M      |     -0.004 |    -0.385 |     0.236 |            3 |         -0.046 |                      0.19  |               8 |       0.042 |  0.444 |
| HOLD     |     -0.02  |    -0.385 |     0.483 |            3 |         -0.017 |                      0.1   |               8 |      -0.004 |  0.667 |
| MID      |      0.016 |    -0.392 |     0.287 |            4 |         -0.073 |                      0.155 |               8 |       0.09  |  0.556 |
| PRE      |     -0.068 |    -0.31  |     0.141 |            2 |         -0.086 |                      0.093 |               8 |       0.018 |  0.556 |
| X'       |     -0.009 |    -0.193 |     0.225 |            2 |          0.012 |                      0.107 |               8 |      -0.02  |  0.556 |

Reading: averaged over the 5 lock-reset phases the maxDD cut of the flip-level skip is +23% in L3M and +13% in MID (5 of 5 phases positive, lock None) but only +1% in L6M/HOLD, -3% in PRE and -6% in X': the lock-None L6M cut in section 1 (+14%) was one phase of the lock. With 12R the phases disagree in sign. The flip-level skip is therefore a DOLLAR / expectancy effect (section 3: flagged rows lose $277 per trade against +$182 for the rest in HOLD, saved dollars rank 0.005-0.02 in L6M and 0.01 in HOLD against 200-draw row-level placebos, positive in PRE and X' but with ranks 0.025-0.15 and 0.16-0.42), not a robust drawdown cut. Walk-forward (section 4): choosing the whole definition on the trailing 12 months keeps +77.5k (lock None) / +134.5k (12R) out of sample 2024-01..2026-10, above a random configuration (+34k / +43k) and below the in-sample reference (+153k / +205k); on the trailing 6 months it is +9.9k / +126.8k. Verdict: LEAD as a mean effect (candidate size modifier / skip for D7), not RISK-KEEP.


## 7. Per-period consistency of the BT swing flip (saved $k = minus the flagged taken trades' base net)
### lock None: saved dollars $k (= minus the flagged rows' base net) by calendar period; n flagged

**year** (positive 4 / 4):
| period   |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:---------|---------:|----------:|------------:|--------------:|
| (2023,)  |      123 |      50.4 |      -410   |          -4.6 |
| (2024,)  |      301 |      24.7 |       -82.1 |         141.6 |
| (2025,)  |      288 |      13.8 |       -48.1 |         159.6 |
| (2026,)  |      320 |     120.7 |      -377.1 |         168.5 |

**half-year** (positive 5 / 8):
| period    |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:----------|---------:|----------:|------------:|--------------:|
| (2023, 1) |        0 |      -0   |       nan   |         -67.1 |
| (2023, 2) |      123 |      50.4 |      -410   |          26.6 |
| (2024, 1) |      156 |      40.7 |      -260.7 |         127.8 |
| (2024, 2) |      145 |     -16   |       110.1 |         150.9 |
| (2025, 1) |      145 |      55.1 |      -379.7 |         100.6 |
| (2025, 2) |      143 |     -41.2 |       288.2 |         230.7 |
| (2026, 1) |      190 |      72.2 |      -379.8 |         227.5 |
| (2026, 2) |      130 |      48.5 |      -373.2 |          90.6 |

**quarter** (positive 11 / 15):
| period    |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:----------|---------:|----------:|------------:|--------------:|
| (2023, 2) |        0 |      -0   |       nan   |         -67.1 |
| (2023, 3) |       51 |       1.3 |       -25.6 |         -62.4 |
| (2023, 4) |       72 |      49.1 |      -682.3 |         129.4 |
| (2024, 1) |       80 |       3.4 |       -42.5 |         101.9 |
| (2024, 2) |       76 |      37.3 |      -490.4 |         153.2 |
| (2024, 3) |       75 |      11.5 |      -153.8 |         174.1 |
| (2024, 4) |       70 |     -27.5 |       392.8 |         122   |
| (2025, 1) |       73 |      16.4 |      -224.5 |          12.7 |
| (2025, 2) |       72 |      38.7 |      -537   |         171.7 |
| (2025, 3) |       82 |      -7.7 |        93.3 |         224.6 |
| (2025, 4) |       61 |     -33.6 |       550.1 |         234.7 |
| (2026, 1) |       84 |      31.8 |      -379   |          72.4 |
| (2026, 2) |      106 |      40.3 |      -380.3 |         354.9 |
| (2026, 3) |       92 |      44.6 |      -484.4 |          71.3 |
| (2026, 4) |       38 |       4   |      -104   |         148.1 |

### lock 12R: saved dollars $k (= minus the flagged rows' base net) by calendar period; n flagged

**year** (positive 4 / 4):
| period   |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:---------|---------:|----------:|------------:|--------------:|
| (2023,)  |       86 |      67.8 |      -788.8 |         -53.5 |
| (2024,)  |      175 |      65.5 |      -374.5 |          71.5 |
| (2025,)  |      208 |      13.3 |       -63.9 |         191.8 |
| (2026,)  |      208 |     151.7 |      -729.1 |         214.2 |

**half-year** (positive 6 / 8):
| period    |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:----------|---------:|----------:|------------:|--------------:|
| (2023, 1) |        0 |      -0   |       nan   |        -250.8 |
| (2023, 2) |       86 |      67.8 |      -788.8 |          25.6 |
| (2024, 1) |       87 |      41.9 |      -481.3 |         111.8 |
| (2024, 2) |       88 |      23.7 |      -268.8 |          43.9 |
| (2025, 1) |       86 |      38.6 |      -448.3 |         110.9 |
| (2025, 2) |      122 |     -25.3 |       207   |         272.6 |
| (2026, 1) |      136 |     106.3 |      -781.7 |         227.5 |
| (2026, 2) |       72 |      45.3 |      -629.8 |         191.5 |

**quarter** (positive 12 / 15):
| period    |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:----------|---------:|----------:|------------:|--------------:|
| (2023, 2) |        0 |      -0   |       nan   |        -250.8 |
| (2023, 3) |       26 |      20.7 |      -797.4 |         -61.8 |
| (2023, 4) |       60 |      47.1 |      -785.1 |         101.1 |
| (2024, 1) |       45 |      23.1 |      -512.9 |          60.5 |
| (2024, 2) |       42 |      18.8 |      -447.5 |         167.9 |
| (2024, 3) |       39 |      21.3 |      -546.3 |          48.2 |
| (2024, 4) |       49 |       2.4 |       -48   |          40   |
| (2025, 1) |       44 |      26.5 |      -601.7 |        -140.6 |
| (2025, 2) |       42 |      12.1 |      -287.6 |         278.9 |
| (2025, 3) |       74 |      -7.3 |        98.8 |         268.6 |
| (2025, 4) |       48 |     -17.9 |       373.8 |         275.2 |
| (2026, 1) |       50 |      51.6 |     -1031.9 |          53.5 |
| (2026, 2) |       86 |      54.7 |      -636.3 |         334.8 |
| (2026, 3) |       54 |      37.5 |      -694.3 |         141.3 |
| (2026, 4) |       18 |       7.9 |      -436.3 |         352.8 |


## 7. Is the flagged-row loss an artefact of the exit model? Library bracket 60/60 outcome of the 2,819 flagged candidate rows vs the rest (all 88,490 rows, net pts per contract = pts_lib - fill cost; hit = pts_lib > 0)
| window   |   n_flag |   flag_mean_pts |   rest_mean_pts |   diff |   ci_lo |   ci_hi |   flag_hit |   rest_hit |   plc_mean |   rank |
|:---------|---------:|----------------:|----------------:|-------:|--------:|--------:|-----------:|-----------:|-----------:|-------:|
| L3M      |      249 |          -5.685 |          -1.515 | -4.169 | -12.513 |   4.264 |      0.482 |      0.519 |     -3.044 |  0.219 |
| L6M      |      523 |          -5.278 |          -1.335 | -3.943 |  -9.393 |   1.791 |      0.486 |      0.521 |     -3.071 |  0.189 |
| HOLD     |      983 |          -2.929 |          -1.12  | -1.809 |  -5.844 |   2.392 |      0.507 |      0.523 |     -2.016 |  0.309 |
| MID      |      234 |           0.862 |          -1.911 |  2.772 |  -5.848 |  11.42  |      0.543 |      0.516 |     -2.069 |  0.787 |
| PRE      |     1168 |          -3.464 |           0.489 | -3.953 |  -8.421 |   0.66  |      0.492 |      0.529 |     -2.862 |  0.369 |
| X'       |      424 |          -7.426 |           1.099 | -8.524 | -15.817 |  -0.849 |      0.458 |      0.525 |     -3.23  |  0.033 |
(rank = share of 300 same-count-per-day random row sets whose mean is at least as low as the flagged rows'; low = the flagged rows are worse than random rows in the library bracket too.)

## 8. Overlap with the other mean-type lines (88,490 candidate rows): Jaccard of the flagged sets, share of BT rows inside the other set
|                              |   BT swing flip  |   large print >= |   TCD TCD_ext D4 |   TCD TCD_div D4 |   TCD TCD_burst  |   Keltner upper  |
|:-----------------------------|-----------------:|-----------------:|-----------------:|-----------------:|-----------------:|-----------------:|
| BT swing flip D40            |            1     |            0.038 |            0.018 |            0.003 |            0.013 |            0.008 |
| large print >=25 lots 4h D40 |            0.038 |            1     |            0.05  |            0.03  |            0.017 |            0.011 |
| TCD TCD_ext D40              |            0.018 |            0.05  |            1     |            0.006 |            0.01  |            0.011 |
| TCD TCD_div D40              |            0.003 |            0.03  |            0.006 |            1     |            0.004 |            0.008 |
| TCD TCD_burst D40            |            0.013 |            0.017 |            0.01  |            0.004 |            1     |            0.004 |
| Keltner upper 4h D20 (coded) |            0.008 |            0.011 |            0.011 |            0.008 |            0.004 |            1     |
rows flagged: BT swing flip D40 2819, large print >=25 lots 4h D40 5110, TCD TCD_ext D40 15965, TCD TCD_div D40 3318, TCD TCD_burst D40 695, Keltner upper 4h D20 (coded) 1177
share of BT rows also flagged by: large print >=25 lots 4h D40 10.3%, TCD TCD_ext D40 11.8%, TCD TCD_div D40 0.6%, TCD TCD_burst D40 1.6%, Keltner upper 4h D20 (coded) 1.1%

### saved $k on V13X taken trades, lock None
| other                        | set            |   L6M |   HOLD |    PRE |    X' |    n |
|:-----------------------------|:---------------|------:|-------:|-------:|------:|-----:|
| large print >=25 lots 4h D40 | BT alone       |  86.2 |   99.6 |   89.4 |  40.8 | 1032 |
| large print >=25 lots 4h D40 | other alone    |  90.2 |  103.4 |   16.8 | -53.5 | 1198 |
| large print >=25 lots 4h D40 | union          | 181.1 |  213.4 |   96.3 | -28.4 | 2114 |
| large print >=25 lots 4h D40 | BT minus other |  91   |  110.1 |   79.5 |  25.1 |  916 |
| large print >=25 lots 4h D40 | other minus BT |  94.9 |  113.8 |    6.9 | -69.2 | 1082 |
| TCD TCD_ext D40              | BT alone       |  86.2 |   99.6 |   89.4 |  40.8 | 1032 |
| TCD TCD_ext D40              | other alone    |  55.4 | -113.5 | -448.6 | 173.1 | 3569 |
| TCD TCD_ext D40              | union          | 142.6 |  -17.2 | -353.4 | 209.6 | 4506 |
| TCD TCD_ext D40              | BT minus other |  87.2 |   96.3 |   95.2 |  36.5 |  937 |
| TCD TCD_ext D40              | other minus BT |  56.3 | -116.8 | -442.8 | 168.8 | 3474 |
| TCD TCD_div D40              | BT alone       |  86.2 |   99.6 |   89.4 |  40.8 | 1032 |
| TCD TCD_div D40              | other alone    | -57.6 |  -88.8 |  -20.1 |  22   |  627 |
| TCD TCD_div D40              | union          |  28.6 |   10.8 |   66.4 |  61.9 | 1651 |
| TCD TCD_div D40              | BT minus other |  86.2 |   99.6 |   86.5 |  39.9 | 1024 |
| TCD TCD_div D40              | other minus BT | -57.6 |  -88.8 |  -23   |  21.1 |  619 |
| TCD TCD_burst D40            | BT alone       |  86.2 |   99.6 |   89.4 |  40.8 | 1032 |
| TCD TCD_burst D40            | other alone    |  -2.4 |  -12.8 |   11.5 | -44   |  161 |
| TCD TCD_burst D40            | union          |  83.8 |   88   |  101.8 |  -3.9 | 1177 |
| TCD TCD_burst D40            | BT minus other |  86.2 |  100.9 |   90.3 |  40.1 | 1016 |
| TCD TCD_burst D40            | other minus BT |  -2.4 |  -11.6 |   12.4 | -44.8 |  145 |
| Keltner upper 4h D20 (coded) | BT alone       |  86.2 |   99.6 |   89.4 |  40.8 | 1032 |
| Keltner upper 4h D20 (coded) | other alone    |  13.4 |   19.8 |    0.7 |  -3.8 |  189 |
| Keltner upper 4h D20 (coded) | union          |  96.4 |  116.2 |   84.7 |  28.8 | 1211 |
| Keltner upper 4h D20 (coded) | BT minus other |  83   |   96.4 |   84   |  32.6 | 1022 |
| Keltner upper 4h D20 (coded) | other minus BT |  10.1 |   16.6 |   -4.7 | -12   |  179 |

### saved $k on V13X taken trades, lock 12R
| other                        | set            |   L6M |   HOLD |    PRE |    X' |    n |
|:-----------------------------|:---------------|------:|-------:|-------:|------:|-----:|
| large print >=25 lots 4h D40 | BT alone       |  99.3 |  129.9 |  104.8 |  67.1 |  677 |
| large print >=25 lots 4h D40 | other alone    |  37.4 |   43.5 |   98.3 | -39   |  757 |
| large print >=25 lots 4h D40 | union          | 136.1 |  176.6 |  186.3 |  15.6 | 1357 |
| large print >=25 lots 4h D40 | BT minus other |  98.7 |  133   |   88   |  54.6 |  600 |
| large print >=25 lots 4h D40 | other minus BT |  36.8 |   46.7 |   81.5 | -51.5 |  680 |
| TCD TCD_ext D40              | BT alone       |  99.3 |  129.9 |  104.8 |  67.1 |  677 |
| TCD TCD_ext D40              | other alone    |  -6.9 | -136.3 | -159.3 | 138.2 | 2261 |
| TCD TCD_ext D40              | union          |  93.6 |   -8.2 |  -77.4 | 197.7 | 2879 |
| TCD TCD_ext D40              | BT minus other | 100.6 |  128.2 |   81.9 |  59.5 |  618 |
| TCD TCD_ext D40              | other minus BT |  -5.7 | -138   | -182.2 | 130.6 | 2202 |
| TCD TCD_div D40              | BT alone       |  99.3 |  129.9 |  104.8 |  67.1 |  677 |
| TCD TCD_div D40              | other alone    | -32.7 |  -52.3 |   19.7 |  24.1 |  383 |
| TCD TCD_div D40              | union          |  66.6 |   77.6 |  124.5 |  90.3 | 1056 |
| TCD TCD_div D40              | BT minus other |  99.3 |  129.9 |  104.8 |  66.2 |  673 |
| TCD TCD_div D40              | other minus BT | -32.7 |  -52.3 |   19.7 |  23.2 |  379 |
| TCD TCD_burst D40            | BT alone       |  99.3 |  129.9 |  104.8 |  67.1 |  677 |
| TCD TCD_burst D40            | other alone    |  -6.9 |   -7.4 |   12   | -23.3 |  124 |
| TCD TCD_burst D40            | union          |  92.4 |  125.5 |  117.8 |  42.4 |  789 |
| TCD TCD_burst D40            | BT minus other |  99.3 |  132.9 |  105.8 |  65.7 |  665 |
| TCD TCD_burst D40            | other minus BT |  -6.9 |   -4.4 |   13   | -24.8 |  112 |
| Keltner upper 4h D20 (coded) | BT alone       |  99.3 |  129.9 |  104.8 |  67.1 |  677 |
| Keltner upper 4h D20 (coded) | other alone    |   6.5 |   10.3 |   17.5 |   7.6 |  127 |
| Keltner upper 4h D20 (coded) | union          | 105.9 |  140.2 |  119.9 |  66.4 |  797 |
| Keltner upper 4h D20 (coded) | BT minus other |  99.3 |  129.9 |  102.4 |  58.9 |  670 |
| Keltner upper 4h D20 (coded) | other minus BT |   6.5 |   10.3 |   15.1 |  -0.7 |  120 |

Reading of 7: the library bracket (60/60, all 88,490 candidate rows) has the same sign as the V13X realised result in 5 of 6 windows (flagged minus rest: L3M -4.2, L6M -3.9, HOLD -1.8, PRE -4.0, X' -8.5 pts per contract after fill cost; MID +2.8) but the 90% day-clustered CIs include zero in the recent windows (X' [-15.8,-0.8], rank 0.033, is the only one that excludes 0), so the flagged-row loss is NOT purely an artefact of the exit model but the library test alone would not detect it; the V13X realised dollars (with the TH-L2 cut, take lines and sizing) show it more strongly (-$277..-$425 per taken trade).
Reading of 8: the flagged row sets barely overlap (Jaccard <= 0.04; 10% of BT rows are also large-print rows, 12% TCD_ext), and the saved dollars are close to additive with large prints (union L6M 181k, HOLD 213k; but large prints are negative in X', union X' -28k) and with the Keltner upper line (+10..+17k extra).


# V13Y (fixed base) RE-RUN of the BT swing flip and PUL k3 (all sections above are the V13X defect base)
Base tables: base_rows_ynone.pkl / base_rows_ylock12.pkl (taken trades 18,827 lock None). 

## Row level, V13Y
### lock None: BT|swing_F10|4h AHEAD D40 skip; taken trades 18827, flagged 1035 (5.5%)

| window   |   n_flag |   flag_sum_k |   flag_mean |   unflag_mean |   flag_hit |   unflag_hit |   flag_ci_lo_k |   flag_ci_hi_k |   rank_A |   rank_B |   rank_C |   plcA_mean_k |   plcB_mean_k |   plcC_mean_k |
|:---------|---------:|-------------:|------------:|--------------:|-----------:|-------------:|---------------:|---------------:|---------:|---------:|---------:|--------------:|--------------:|--------------:|
| L3M      |       94 |      -30.431 |    -323.73  |       156.466 |      0.394 |        0.479 |        -63.253 |          4.034 |    0.07  |    0.1   |    0.1   |        16.372 |         9.127 |        12.592 |
| L6M      |      204 |      -69.777 |    -342.046 |       197.606 |      0.377 |        0.472 |       -116.996 |        -19.764 |    0.005 |    0.025 |    0.015 |        50.401 |        17.798 |        46.929 |
| HOLD     |      359 |      -74.915 |    -208.677 |       182.225 |      0.398 |        0.471 |       -145.72  |         -4.258 |    0.005 |    0.015 |    0.035 |        74.045 |        36.414 |        75.391 |
| MID      |       84 |      -17.872 |    -212.763 |       139.821 |      0.44  |        0.461 |        -59.154 |         25.516 |    0.204 |    0.224 |    0.204 |         7.216 |         9.674 |        11.09  |
| PRE      |      416 |     -103.432 |    -248.636 |       156.288 |      0.438 |        0.484 |       -200.759 |         -3.825 |    0.04  |    0.08  |    0.03  |        21.227 |       -20.687 |        14.264 |
| X'       |      155 |      -50.13  |    -323.417 |        48.724 |      0.477 |        0.51  |       -123.346 |         16.541 |    0.075 |    0.274 |    0.055 |         0.498 |       -30.094 |         2.917 |

flagged rows by book|session in HOLD (sum $k, n, mean $):
| key   |   size |   sum |    mean |
|:------|-------:|------:|--------:|
| HM|0  |     33 |   8.4 |   255.2 |
| HM|3  |      4 |  -0.8 |  -190.8 |
| KB|0  |     82 |  -1.9 |   -22.8 |
| KB|1  |     66 | -21.1 |  -320.1 |
| KB|3  |     15 |  -6.4 |  -429.2 |
| KB|4  |      9 |  -4.9 |  -541.7 |
| MV|1  |     37 |   2.3 |    61.3 |
| MV|3  |      5 |  -1   |  -208.9 |
| PB|0  |      5 |  -2.2 |  -436.3 |
| PE|0  |     38 | -16.5 |  -434.7 |
| PE|1  |     32 | -13.9 |  -435   |
| PE|3  |      1 |  11.5 | 11479.6 |
| SM|0  |     10 |  -6.2 |  -622   |
| SM|1  |     22 | -22.1 | -1005.9 |

flagged rows by book|session in PRE (sum $k, n, mean $):
| key   |   size |   sum |    mean |
|:------|-------:|------:|--------:|
| HM|0  |     34 | -12.6 |  -371.8 |
| HM|3  |     15 |  -4.6 |  -303.6 |
| KB|0  |     76 | -19.9 |  -261.5 |
| KB|1  |     72 |   8.8 |   121.7 |
| KB|3  |     30 |   4.5 |   151   |
| KB|4  |     24 |  -4   |  -164.7 |
| MV|1  |     18 |  -5.1 |  -280.8 |
| MV|3  |      7 |  -4.1 |  -591.7 |
| PB|0  |      4 |   3.5 |   867.3 |
| PE|0  |     53 | -45.3 |  -855.4 |
| PE|1  |     32 | -14.5 |  -453   |
| PE|3  |      9 | -10.6 | -1176.5 |
| SM|0  |     14 |  -2.3 |  -161   |
| SM|1  |     28 |   2.7 |    96.5 |

### lock 12R: BT|swing_F10|4h AHEAD D40 skip; taken trades 12835, flagged 704 (5.5%)

| window   |   n_flag |   flag_sum_k |   flag_mean |   unflag_mean |   flag_hit |   unflag_hit |   flag_ci_lo_k |   flag_ci_hi_k |   rank_A |   rank_B |   rank_C |   plcA_mean_k |   plcB_mean_k |   plcC_mean_k |
|:---------|---------:|-------------:|------------:|--------------:|-----------:|-------------:|---------------:|---------------:|---------:|---------:|---------:|--------------:|--------------:|--------------:|
| L3M      |       65 |      -24.762 |    -380.958 |       155.428 |      0.369 |        0.484 |        -55.411 |          2.924 |    0.1   |    0.109 |    0.095 |         9.213 |         5.417 |         8.704 |
| L6M      |      136 |      -70.142 |    -515.748 |       220.721 |      0.338 |        0.474 |       -114.064 |        -29.249 |    0.02  |    0.005 |    0.005 |        36.674 |        11.555 |        35.123 |
| HOLD     |      237 |     -107.054 |    -451.706 |       188.261 |      0.363 |        0.471 |       -165.481 |        -48.797 |    0.005 |    0.01  |    0.01  |        51.258 |        19.494 |        48.242 |
| MID      |       57 |      -47.301 |    -829.84  |       109.608 |      0.351 |        0.462 |        -75.501 |        -21.122 |    0.04  |    0.06  |    0.05  |         1.104 |         3.604 |         0     |
| PRE      |      260 |     -123.118 |    -473.532 |       134.178 |      0.404 |        0.476 |       -200.509 |        -51.553 |    0.01  |    0.03  |    0.005 |         9.968 |       -25.14  |        12.193 |
| X'       |      116 |      -66.28  |    -571.383 |        10.188 |      0.44  |        0.507 |       -118.271 |        -18.791 |    0.03  |    0.184 |    0.005 |        -8.141 |       -39.707 |        -4.927 |

flagged rows by book|session in HOLD (sum $k, n, mean $):
| key   |   size |   sum |    mean |
|:------|-------:|------:|--------:|
| HM|0  |     17 |  -1.1 |   -64.3 |
| HM|3  |      2 |  -0.2 |  -115.1 |
| KB|0  |     53 |  -1   |   -19.7 |
| KB|1  |     50 | -18.4 |  -369   |
| KB|3  |      8 |  -3.9 |  -486.2 |
| KB|4  |      8 |  -6.1 |  -762.1 |
| MV|1  |     22 |  -2.7 |  -123.3 |
| MV|3  |      3 |  -0.4 |  -130.4 |
| PB|0  |      4 |  -4.6 | -1142.9 |
| PE|0  |     25 | -28.6 | -1143   |
| PE|1  |     21 | -22.1 | -1051.7 |
| PE|3  |      1 |  11.5 | 11479.6 |
| SM|0  |      7 |  -9.2 | -1312.8 |
| SM|1  |     16 | -20.2 | -1262.9 |

flagged rows by book|session in PRE (sum $k, n, mean $):
| key   |   size |   sum |    mean |
|:------|-------:|------:|--------:|
| HM|0  |     26 | -11.4 |  -439.2 |
| HM|3  |     10 |  -4.6 |  -456.4 |
| KB|0  |     51 | -19.3 |  -378.1 |
| KB|1  |     42 |  -1   |   -23.4 |
| KB|3  |     20 |  -0   |    -2   |
| KB|4  |     12 |   4.1 |   341.1 |
| MV|1  |     12 |  -6.7 |  -561.3 |
| MV|3  |      4 |  -1.7 |  -418.8 |
| PB|0  |      2 |  -0   |   -17.6 |
| PE|0  |     37

## Per-period, V13Y
### V13Y lock None: saved $k by calendar period

**year** (positive 4 / 4 with flags):
| period   |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:---------|---------:|----------:|------------:|--------------:|
| (2023,)  |      122 |      56.9 |      -466.1 |          46.5 |
| (2024,)  |      304 |      29.3 |       -96.3 |         155.2 |
| (2025,)  |      288 |      28   |       -97.1 |         174.4 |
| (2026,)  |      321 |      89.2 |      -277.7 |         178.1 |

**half-year** (positive 5 / 7 with flags):
| period    |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:----------|---------:|----------:|------------:|--------------:|
| (2023, 1) |        0 |      -0   |       nan   |         -19.4 |
| (2023, 2) |      122 |      56.9 |      -466.1 |          79.2 |
| (2024, 1) |      157 |      37.4 |      -238.1 |         140.5 |
| (2024, 2) |      147 |      -8.1 |        55.2 |         165.1 |
| (2025, 1) |      145 |      67.4 |      -465   |         149.1 |
| (2025, 2) |      143 |     -39.5 |       276.1 |         204.9 |
| (2026, 1) |      191 |      51.6 |      -270.3 |         232.8 |
| (2026, 2) |      130 |      37.5 |      -288.7 |         106.4 |

**quarter** (positive 11 / 14 with flags):
| period    |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:----------|---------:|----------:|------------:|--------------:|
| (2023, 2) |        0 |      -0   |       nan   |         -19.4 |
| (2023, 3) |       50 |       6.2 |      -123.1 |           8.6 |
| (2023, 4) |       72 |      50.7 |      -704.3 |         160.2 |
| (2024, 1) |       80 |       6.3 |       -78.3 |         114.9 |
| (2024, 2) |       77 |      31.1 |      -404.1 |         165.6 |
| (2024, 3) |       77 |      19   |      -246.3 |         180.8 |
| (2024, 4) |       70 |     -27.1 |       386.9 |         145.7 |
| (2025, 1) |       73 |      12.3 |      -168.9 |          20.6 |
| (2025, 2) |       72 |      55.1 |      -765.3 |         254.3 |
| (2025, 3) |       82 |      -7.7 |        93.3 |         225.6 |
| (2025, 4) |       61 |     -31.8 |       521.7 |         191.6 |
| (2026, 1) |       84 |      21.2 |      -252.4 |          91.7 |
| (2026, 2) |      107 |      30.4 |      -284.3 |         347.7 |
| (2026, 3) |       92 |      32.5 |      -353.4 |          88.4 |
| (2026, 4) |       38 |       5   |      -132   |         160.1 |

### V13Y lock 12R: saved $k by calendar period

**year** (positive 4 / 4 with flags):
| period   |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:---------|---------:|----------:|------------:|--------------:|
| (2023,)  |       94 |      64.1 |      -682.2 |          18.6 |
| (2024,)  |      189 |      83.9 |      -443.9 |         111.9 |
| (2025,)  |      212 |      16.8 |       -79.2 |         180.3 |
| (2026,)  |      209 |     122.4 |      -585.9 |         178.8 |

**half-year** (positive 6 / 7 with flags):
| period    |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:----------|---------:|----------:|------------:|--------------:|
| (2023, 1) |        0 |      -0   |       nan   |        -234.3 |
| (2023, 2) |       94 |      64.1 |      -682.2 |         109.8 |
| (2024, 1) |       92 |      50.8 |      -552.6 |          62.4 |
| (2024, 2) |       97 |      33.1 |      -340.8 |         145.4 |
| (2025, 1) |       93 |      41.4 |      -445   |         143.1 |
| (2025, 2) |      119 |     -24.6 |       206.7 |         220   |
| (2026, 1) |      129 |      96.3 |      -746.4 |         204.6 |
| (2026, 2) |       80 |      26.2 |      -327.1 |         140.7 |

**quarter** (positive 11 / 14 with flags):
| period    |   n_flag |   saved_k |   flag_mean |   unflag_mean |
|:----------|---------:|----------:|------------:|--------------:|
| (2023, 2) |        0 |      -0   |       nan   |        -234.3 |
| (2023, 3) |       33 |      18.4 |      -557.4 |          17.9 |
| (2023, 4) |       61 |      45.7 |      -749.7 |         195.9 |
| (2024, 1) |       47 |      30.6 |      -650.1 |          61.3 |
| (2024, 2) |       45 |      20.3 |      -450.8 |          63.5 |
| (2024, 3) |       51 |      22.3 |      -438   |         280.2 |
| (2024, 4) |       46 |      10.7 |      -233   |         -33.7 |
| (2025, 1) |       51 |      12.9 |      -252.2 |        -110.8 |
| (2025, 2) |       42 |      28.5 |      -679   |         327.1 |
| (2025, 3) |       74 |      -7.3 |        98.8 |         262.2 |
| (2025, 4) |       45 |     -17.3 |       384.1 |         191.3 |
| (2026, 1) |       48 |      40.7 |      -848.1 |          22.3 |
| (2026, 2) |       81 |      55.6 |      -686.1 |         313.7 |
| (2026, 3) |       55 |      28.9 |      -525.2 |         159.9 |
| (2026, 4) |       25 |      -2.7 |       108.9 |          93.2 |


## Plateau and walk-forward, V13Y
### lock None: parameter plateau of the flip-level skip (saved $k = -sum of the flagged rows' base net; 144 configs = swing ['5m', '15m', '1h'] x break [5, 10, 15, 20] x keep ['1h', '4h', '24h'] x reach [20, 30, 40, 60])

share of configs with positive saved dollars: L6M 76%, HOLD 85%, MID 90%, PRE 66%, X' 87%; all four of L6M/HOLD/PRE/X': 42%

median saved $k by swing timeframe:
| TF   |   L6M |   HOLD |   PRE |   X' |
|:-----|------:|-------:|------:|-----:|
| 15m  |  14.1 |   15.2 |  26   | 10.6 |
| 1h   |   1.7 |    8.4 |  -0.6 |  8.5 |
| 5m   |  35.3 |   28   |  28.9 | 15.9 |

median saved $k by F:
|   F |   L6M |   HOLD |   PRE |   X' |
|----:|------:|-------:|------:|-----:|
|   5 |  11.9 |   11.4 |   6.3 |  7.5 |
|  10 |  10.9 |    8.4 |  28.8 |  8.9 |
|  15 |  12   |   22.6 |   8.8 | 15.1 |
|  20 |  10.7 |   19.4 |   2.9 | 14.4 |

median saved $k by keep:
| keep   |   L6M |   HOLD |   PRE |   X' |
|:-------|------:|-------:|------:|-----:|
| 1h     |   5.1 |    8.3 |  19   |  6.8 |
| 24h    |  18.1 |   32.4 | -33.5 | 21.5 |
| 4h     |  20.4 |   21.3 |  41.4 | 10.7 |

median saved $k by D:
|   D |   L6M |   HOLD |   PRE |   X' |
|----:|------:|-------:|------:|-----:|
|  20 |   7.4 |    5.6 |   8.8 | 10.5 |
|  30 |   9   |    9.3 |   6.7 | 10.7 |
|  40 |  11.8 |   25.1 |   1.9 | 11   |
|  60 |  12.8 |   20   |  22.8 |  8   |

reference config (5m, break 10, 4h, reach 40):
| TF   |   F | keep   |   D |   n_flag |   L6M |   HOLD |   MID |   PRE |   X' |   hit_all |
|:-----|----:|:-------|----:|---------:|------:|-------:|------:|------:|-----:|----------:|
| 5m   |  10 | 4h     |  40 |     1104 |  72.3 |   77.5 |  17.4 |  98.2 | 33.7 |     184.1 |

**Walk-forward (12-month trailing choice of the whole configuration, apply to next month; 2024-01..2026-10; saved $k):**

|                                                  |   L6M |   HOLD |   MID |   2024-25 |   all |
|:-------------------------------------------------|------:|-------:|------:|----------:|------:|
| walk-forward (skips only if trailing saving > 0) |  46.1 |   56.2 |   6.6 |       2.1 |  54.2 |
| fixed reference config                           |  72.3 |   77.5 |  17.4 |      45.7 | 137.4 |
| mean of all 144 configs (random choice)          |  18.7 |   26.1 |  10.1 |      12.8 |  33.1 |
| best config in hindsight each month              | 205.5 |  393.2 | 109.4 |     601.9 | 928.2 |

months with positive walk-forward saving: 15 / 31 active; fixed-config positive months 18 / 31

most-chosen configs: ('5m', np.int64(15), '4h', np.int64(60)) x7; ('5m', np.int64(10), '4h', np.int64(30)) x4; ('15m', np.int64(15), '4h', np.int64(60)) x4; ('15m', np.int64(20), '24h', np.int64(40)) x4

**Walk-forward (6-month trailing choice of the whole configuration, apply to next month; 2024-01..2026-10; saved $k):**

|                                                  |   L6M |   HOLD |   MID |   2024-25 |   all |
|:-------------------------------------------------|------:|-------:|------:|----------:|------:|
| walk-forward (skips only if trailing saving > 0) |  23.8 |   54.6 |   4.2 |      52.8 |  51.4 |
| fixed reference config                           |  72.3 |   77.5 |  17.4 |      52   | 143.7 |
| mean of all 144 configs (random choice)          |  18.7 |   26.1 |  10.1 |       1   |  21.4 |
| best config in hindsight each month              | 205.5 |  393.2 | 109.4 |     661.3 | 987.7 |

months with positive walk-forward saving: 18 / 34 active; fixed-config positive months 19 / 34

most-chosen configs: ('5m', np.int64(15), '4h', np.int64(60)) x5; ('15m', np.int64(20), '24h', np.int64(40)) x5; ('5m', np.int64(20), '4h', np.int64(60)) x3; ('5m', np.int64(15), '4h', np.int64(20)) x2

### lock 12R: parameter plateau of the flip-level skip (saved $k = -sum of the flagged rows' base net; 144 configs = swing ['5m', '15m', '1h'] x break [5, 10, 15, 20] x keep ['1h', '4h', '24h'] x reach [20, 30, 40, 60])

share of configs with positive saved dollars: L6M 83%, HOLD 90%, MID 85%, PRE 77%, X' 99%; all four of L6M/HOLD/PRE/X': 64%

median saved $k by swing timeframe:
| TF   |   L6M |   HOLD |   PRE |   X' |
|:-----|------:|-------:|------:|-----:|
| 15m  |  17.3 |   24.2 |  19.9 | 15.4 |
| 1h   |   1.6 |    6.1 |  -0.2 |  5.8 |
| 5m   |  28.5 |   48.5 |  49.2 | 34.4 |

median saved $k by F:
|   F |   L6M |   HOLD |   PRE |   X' |
|----:|------:|-------:|------:|-----:|
|   5 |  12.6 |   12.3 |  21   | 15.3 |
|  10 |  11.1 |   14.2 |  33   | 34.7 |
|  15 |  13.6 |   22.6 |  17.5 | 30.8 |
|  20 |  14.5 |   21.7 |  17   | 16.2 |

median saved $k by keep:
| keep   |   L6M |   HOLD |   PRE |   X' |
|:-------|------:|-------:|------:|-----:|
| 1h     |   9.1 |   11.7 |  14.7 |  4.8 |
| 24h    |  13.4 |   29.7 |   7.3 | 39.2 |
| 4h     |  25   |   30.7 |  69.7 | 14.7 |

median saved $k by D:
|   D |   L6M |   HOLD |   PRE |   X' |
|----:|------:|-------:|------:|-----:|
|  20 |  11.1 |   13.1 |  20.7 | 21   |
|  30 |   8.3 |   12.9 |  18.9 | 16.7 |
|  40 |  13.6 |   19   |  17.6 | 18.9 |
|  60 |  18.6 |   24.2 |  22.5 | 20.9 |

reference config (5m, break 10, 4h, reach 40):
| TF   |   F | keep   |   D |   n_flag |   L6M |   HOLD |   MID |   PRE |   X' |   hit_all |
|:-----|----:|:-------|----:|---------:|------:|-------:|------:|------:|-----:|----------:|
| 5m   |  10 | 4h     |  40 |      750 |  72.7 |  109.6 |  43.9 | 117.9 | 58.1 |     276.4 |

**Walk-forward (12-month trailing choice of the whole configuration, apply to next month; 2024-01..2026-10; saved $k):**

|                                                  |   L6M |   HOLD |   MID |   2024-25 |   all |
|:-------------------------------------------------|------:|-------:|------:|----------:|------:|
| walk-forward (skips only if trailing saving > 0) |  25   |   44.2 |  37.3 |      86   | 134.2 |
| fixed reference config                           |  72.7 |  109.6 |  43.9 |      64.9 | 189.9 |
| mean of all 144 configs (random choice)          |  18.9 |   31.7 |  13.2 |      22.2 |  51.9 |
| best config in hindsight each month              | 175.2 |  331.1 |  91.4 |     532.4 | 808.1 |

months with positive walk-forward saving: 19 / 31 active; fixed-config positive months 22 / 31

most-chosen configs: ('5m', np.int64(10), '4h', np.int64(60)) x9; ('5m', np.int64(15), '4h', np.int64(60)) x5; ('15m', np.int64(15), '24h', np.int64(60)) x4; ('15m', np.int64(20), '24h', np.int64(40)) x3

**Walk-forward (6-month trailing choice of the whole configuration, apply to next month; 2024-01..2026-10; saved $k):**

|                                                  |   L6M |   HOLD |   MID |   2024-25 |   all |
|:-------------------------------------------------|------:|-------:|------:|----------:|------:|
| walk-forward (skips only if trailing saving > 0) |  83.8 |  125.5 |  34.9 |      81.7 | 179.6 |
| fixed reference config                           |  72.7 |  109.6 |  43.9 |      95.4 | 220.4 |
| mean of all 144 configs (random choice)          |  18.9 |   31.7 |  13.2 |      20.2 |  50   |
| best config in hindsight each month              | 175.2 |  331.1 |  91.4 |     591.2 | 866.9 |

months with positive walk-forward saving: 23 / 34 active; fixed-config positive months 25 / 34

most-chosen configs: ('5m', np.int64(15), '4h', np.int64(60)) x5; ('5m', np.int64(10), '4h', np.int64(20)) x3; ('5m', np.int64(20), '4h', np.int64(60)) x3; ('15m', np.int64(20), '24h', np.int64(40)) x3

## Best-of-N null, V13Y
V13Y best-of-N null: families 1980 (offset 990 , shuffled-day 990 ); flagged taken trades null mean 600 vs BT 1035
| frame   | stat                |    BT_k |   null_median |   null_p99 |   null_max |   rank |
|:--------|:--------------------|--------:|--------------:|-----------:|-----------:|-------:|
| none    | L3M                 |  30.431 |         0.688 |     31.637 |     55.382 |  0.014 |
| none    | L6M                 |  69.777 |       -11.394 |     37.597 |     68.464 |  0.001 |
| none    | HOLD                |  74.915 |       -14.522 |     58.264 |     94.38  |  0.003 |
| none    | MID                 |  17.872 |         4.684 |     41.101 |     53.861 |  0.19  |
| none    | PRE                 | 103.432 |        -5.005 |     73.671 |    102.55  |  0.001 |
| none    | X                   |  50.13  |       -19.985 |     28.435 |     50.628 |  0.001 |
| none    | min(L6M,HOLD,PRE)   |  69.777 |       -29.481 |     16.19  |     37.365 |  0.001 |
| none    | min(L6M,HOLD,PRE,X) |  50.13  |       -37.205 |      0.265 |     17.166 |  0.001 |
| lock12  | L3M                 |  24.762 |         0.319 |     26.611 |     35.034 |  0.014 |
| lock12  | L6M                 |  70.142 |       -10.199 |     29.262 |     46.443 |  0.001 |
| lock12  | HOLD                | 107.054 |        -4.116 |     48.753 |     78.477 |  0.001 |
| lock12  | MID                 |  47.301 |        10.561 |     41.008 |     59.21  |  0.002 |
| lock12  | PRE                 | 123.118 |        -1.459 |     70.731 |     97.196 |  0.001 |
| lock12  | X                   |  66.28  |        -0.205 |     41.772 |     67.912 |  0.001 |
| lock12  | min(L6M,HOLD,PRE)   |  70.142 |       -21.019 |     14.643 |     27.022 |  0.001 |
| lock12  | min(L6M,HOLD,PRE,X) |  66.28  |       -23.617 |      6.969 |     15.397 |  0.001 |


## Engine cells on V13Y (maxDD cut vs the V13Y base; V13Y base maxDD $k lock12 L3M 26.5, L6M 52.8, HOLD 90.4, MID 52.3, PRE 282, X' 131; lock None L3M 31.1, L6M 96.2, HOLD 103, MID 30.2, PRE 129.7, X' 69.7)
BT swing F10 4h D40 skip: lock12 L3M +15%, L6M +8%, HOLD +36%, MID +20%, PRE +24%, X' 0% (BT events start 2023-08; the X' maxDD episode is before it); lock None +10%, +5%, +8%, +29%, +1%, -10%. Mean delta HOLD +4.5k/wk (12R, MDE 5.9k) and +2.4k/wk (lock None, MDE 3.0k). PUL k3 4h D20 skip on V13Y: lock12 L3M -8% L6M +1% HOLD 0 MID -1% PRE +6%; lock None L3M +1% L6M -6% MID -27% PRE -6%: DEAD on the fixed base (V13X LEAD(weak) -> V13Y DEAD).
Verdict V13Y: BT swing flip stays LEAD as a MEAN-type effect (saved dollars beat every one of 1,980 same-density null families on the joint statistic: lock None 50k vs null max 17k, lock 12R 66k vs 15k; per-year 4/4, quarters 11/14; flagged taken trades -$209 vs +$182; walk-forward OOS +54k/+51k lock None); its drawdown cut is small and base-dependent (not RISK-KEEP). PUL k3 is withdrawn.
