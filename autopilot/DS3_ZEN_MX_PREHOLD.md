# DS3_ZEN_MX_PREHOLD - frozen HOLD/X set of family MX (D3ZMX, 2026-10-28)

Written after the PRE screen (prereg ZEN_MX sha256 b07d3887920e24ce7aa84c8bd368d49f29a3e412e8518f99cca31ff954f3a1a4) and BEFORE any HOLD / X bar of an MX cell is read.
Rule (prereg section 4): the 15 base cells + the top 30 other scored rows by PRE effect vs random-in-regime (100-draw placebo), n >= 100 sequenced trades, R_PYR rows excluded, exact duplicates of a higher-ranked trade list removed. Eligible rows before de-duplication: 276, after: 263. HOLD = 2025-07-01..2026-02-06, X = 2023-04-01..2024-01-31; one look each, logged in DECISIONS.md and out/zen/mx/looks.jsonl.

```json
[
{
"row": 1,
"cell": "E1",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 2465,
"pre_effect": -0.317,
"pre_net1": -1.827
},
{
"row": 34,
"cell": "E2",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 2096,
"pre_effect": -0.207,
"pre_net1": -1.712
},
{
"row": 67,
"cell": "E3",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 1117,
"pre_effect": 0.135,
"pre_net1": -1.252
},
{
"row": 100,
"cell": "E4",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 2397,
"pre_effect": -0.02,
"pre_net1": -1.524
},
{
"row": 132,
"cell": "E5",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 4018,
"pre_effect": 0.014,
"pre_net1": -1.5
},
{
"row": 165,
"cell": "T1",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 151,
"pre_effect": 2.814,
"pre_net1": 0.947
},
{
"row": 197,
"cell": "T2",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 136,
"pre_effect": 1.877,
"pre_net1": 1.305
},
{
"row": 230,
"cell": "T3",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 100,
"pre_effect": 9.082,
"pre_net1": 8.312
},
{
"row": 262,
"cell": "T4",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 101,
"pre_effect": 6.479,
"pre_net1": 6.633
},
{
"row": 294,
"cell": "T5",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 81,
"pre_effect": 8.655,
"pre_net1": 10.468
},
{
"row": 326,
"cell": "T6",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 97,
"pre_effect": 8.09,
"pre_net1": 6.585
},
{
"row": 359,
"cell": "T7",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 136,
"pre_effect": 6.397,
"pre_net1": 6.015
},
{
"row": 392,
"cell": "T8",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 107,
"pre_effect": 3.442,
"pre_net1": 4.742
},
{
"row": 425,
"cell": "T9",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 182,
"pre_effect": 3.382,
"pre_net1": 2.52
},
{
"row": 457,
"cell": "T10",
"item": "BASE",
"label": "BASE",
"var": {},
"role": "base",
"pre_n": 111,
"pre_effect": 0.168,
"pre_net1": -0.555
},
{
"row": 371,
"cell": "T7",
"item": "M5",
"label": "G_first",
"var": {
"gate": "G_first"
},
"role": "top30",
"pre_n": 117,
"pre_effect": 11.599,
"pre_net1": 12.221
},
{
"row": 249,
"cell": "T3",
"item": "M6",
"label": "R_MAX2",
"var": {
"rule": "R_MAX2"
},
"role": "top30",
"pre_n": 100,
"pre_effect": 9.104,
"pre_net1": 8.312
},
{
"row": 382,
"cell": "T7",
"item": "M6",
"label": "R_FIRST",
"var": {
"rule": "R_FIRST"
},
"role": "top30",
"pre_n": 114,
"pre_effect": 7.683,
"pre_net1": 8.318
},
{
"row": 376,
"cell": "T7",
"item": "M6",
"label": "R_DONE",
"var": {
"rule": "R_DONE"
},
"role": "top30",
"pre_n": 120,
"pre_effect": 7.527,
"pre_net1": 6.908
},
{
"row": 325,
"cell": "T5",
"item": "M7",
"label": "X_SESHI",
"var": {
"exit": "X_SESHI"
},
"role": "top30",
"pre_n": 106,
"pre_effect": 7.225,
"pre_net1": 8.47
},
{
"row": 288,
"cell": "T4",
"item": "M7",
"label": "X_T30",
"var": {
"exit": "X_T30"
},
"role": "top30",
"pre_n": 125,
"pre_effect": 7.106,
"pre_net1": 6.21
},
{
"row": 377,
"cell": "T7",
"item": "M6",
"label": "R_SP5",
"var": {
"rule": "R_SP5"
},
"role": "top30",
"pre_n": 135,
"pre_effect": 6.847,
"pre_net1": 6.506
},
{
"row": 378,
"cell": "T7",
"item": "M6",
"label": "R_SP15",
"var": {
"rule": "R_SP15"
},
"role": "top30",
"pre_n": 135,
"pre_effect": 6.772,
"pre_net1": 6.474
},
{
"row": 379,
"cell": "T7",
"item": "M6",
"label": "R_MAX2",
"var": {
"rule": "R_MAX2"
},
"role": "top30",
"pre_n": 133,
"pre_effect": 6.769,
"pre_net1": 6.352
},
{
"row": 283,
"cell": "T4",
"item": "M6",
"label": "R_MAX5",
"var": {
"rule": "R_MAX5"
},
"role": "top30",
"pre_n": 101,
"pre_effect": 6.479,
"pre_net1": 6.633
},
{
"row": 380,
"cell": "T7",
"item": "M6",
"label": "R_MAX3",
"var": {
"rule": "R_MAX3"
},
"role": "top30",
"pre_n": 136,
"pre_effect": 6.399,
"pre_net1": 6.015
},
{
"row": 229,
"cell": "T2",
"item": "M7",
"label": "X_SESHI",
"var": {
"exit": "X_SESHI"
},
"role": "top30",
"pre_n": 129,
"pre_effect": 6.22,
"pre_net1": 5.963
},
{
"row": 357,
"cell": "T6",
"item": "M7",
"label": "X_VWAP1",
"var": {
"exit": "X_VWAP1"
},
"role": "top30",
"pre_n": 100,
"pre_effect": 6.209,
"pre_net1": 7.292
},
{
"row": 360,
"cell": "T7",
"item": "M4",
"label": "LINE_rth",
"var": {
"line": "rth"
},
"role": "top30",
"pre_n": 131,
"pre_effect": 6.172,
"pre_net1": 5.962
},
{
"row": 391,
"cell": "T7",
"item": "M7",
"label": "X_SESHI",
"var": {
"exit": "X_SESHI"
},
"role": "top30",
"pre_n": 158,
"pre_effect": 6.154,
"pre_net1": 4.055
},
{
"row": 439,
"cell": "T9",
"item": "M6",
"label": "R_ATT2",
"var": {
"rule": "R_ATT2"
},
"role": "top30",
"pre_n": 116,
"pre_effect": 5.736,
"pre_net1": 5.376
},
{
"row": 327,
"cell": "T6",
"item": "M4",
"label": "LINE_rth",
"var": {
"line": "rth"
},
"role": "top30",
"pre_n": 112,
"pre_effect": 5.104,
"pre_net1": 4.047
},
{
"row": 370,
"cell": "T7",
"item": "M5",
"label": "G_roompd",
"var": {
"gate": "G_roompd"
},
"role": "top30",
"pre_n": 100,
"pre_effect": 4.963,
"pre_net1": 3.709
},
{
"row": 446,
"cell": "T9",
"item": "M6",
"label": "R_MAX5",
"var": {
"rule": "R_MAX5"
},
"role": "top30",
"pre_n": 126,
"pre_effect": 4.83,
"pre_net1": 4.311
},
{
"row": 287,
"cell": "T4",
"item": "M7",
"label": "X_T20",
"var": {
"exit": "X_T20"
},
"role": "top30",
"pre_n": 138,
"pre_effect": 4.797,
"pre_net1": 4.049
},
{
"row": 435,
"cell": "T9",
"item": "M5",
"label": "G_roompd",
"var": {
"gate": "G_roompd"
},
"role": "top30",
"pre_n": 135,
"pre_effect": 4.642,
"pre_net1": 3.933
},
{
"row": 440,
"cell": "T9",
"item": "M6",
"label": "R_ATT3",
"var": {
"rule": "R_ATT3"
},
"role": "top30",
"pre_n": 138,
"pre_effect": 4.429,
"pre_net1": 3.888
},
{
"row": 355,
"cell": "T6",
"item": "M7",
"label": "X_EMA20",
"var": {
"exit": "X_EMA20"
},
"role": "top30",
"pre_n": 110,
"pre_effect": 4.218,
"pre_net1": 2.983
},
{
"row": 361,
"cell": "T7",
"item": "M4",
"label": "LINE_anch",
"var": {
"line": "anch"
},
"role": "top30",
"pre_n": 130,
"pre_effect": 4.213,
"pre_net1": 3.952
},
{
"row": 292,
"cell": "T4",
"item": "M7",
"label": "X_VWAP1",
"var": {
"exit": "X_VWAP1"
},
"role": "top30",
"pre_n": 120,
"pre_effect": 4.036,
"pre_net1": 6.394
},
{
"row": 434,
"cell": "T9",
"item": "M5",
"label": "G_room4h",
"var": {
"gate": "G_room4h"
},
"role": "top30",
"pre_n": 147,
"pre_effect": 3.894,
"pre_net1": 3.116
},
{
"row": 178,
"cell": "T1",
"item": "M6",
"label": "R_ATT1",
"var": {
"rule": "R_ATT1"
},
"role": "top30",
"pre_n": 106,
"pre_effect": 3.807,
"pre_net1": 3.256
},
{
"row": 353,
"cell": "T6",
"item": "M7",
"label": "X_T30",
"var": {
"exit": "X_T30"
},
"role": "top30",
"pre_n": 112,
"pre_effect": 3.738,
"pre_net1": 2.723
},
{
"row": 175,
"cell": "T1",
"item": "M5",
"label": "G_roompd",
"var": {
"gate": "G_roompd"
},
"role": "top30",
"pre_n": 133,
"pre_effect": 3.669,
"pre_net1": -0.312
},
{
"row": 179,
"cell": "T1",
"item": "M6",
"label": "R_ATT2",
"var": {
"rule": "R_ATT2"
},
"role": "top30",
"pre_n": 122,
"pre_effect": 3.571,
"pre_net1": 2.359
}
]
```
