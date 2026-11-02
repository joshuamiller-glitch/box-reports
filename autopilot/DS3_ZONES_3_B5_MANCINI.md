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
