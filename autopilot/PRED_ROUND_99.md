# PRED ROUND 99 - block X1 round 8 - X33-X36

Best HOLDOUT F-R AUC: +15 POOLED 0.528 [0.49,0.57] | ASIA 0.578 [0.53,0.63] | LONDON 0.553 [0.49,0.61] | NY 0.530 [0.47,0.59]
Best HOLDOUT F-R AUC: +30 POOLED 0.505 [0.47,0.54] | ASIA 0.556 [0.50,0.61] | LONDON 0.506 [0.44,0.57] | NY 0.490 [0.42,0.56]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.082 AUC, 5 of 5 economic conditions short.
not found - short by 0.082 AUC and 5 of 5 economic conditions

prereg 1b2abd3bd0fd800642df193d9d8d3773e9a616cf0ff561c19b6b82a1e5cf5a43 ; trials added 900 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X4u_round5.parquet', 'l2vast/pred/store/X5u_round5.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X34-stop-regime | +15 | ASIA | X8:logit2 | 0.549 [0.50,0.59] | 0.578 [0.53,0.63] | - | 0.575 | 0.578 | ok | - | - | - | - | stack | short by 0.082 AUC, 5 of 5 econ |
| X34-stop-regime | +20 | LONDON | X8:gbt3 | 0.548 [0.51,0.59] | 0.574 [0.53,0.63] | - | 0.575 | 0.548 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +10 | NY | gh_logit2 | 0.538 [0.50,0.58] | 0.567 [0.50,0.64] | - | 0.567 | 0.558 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +45 | ASIA | X8:logit2 | 0.538 [0.49,0.58] | 0.563 [0.50,0.63] | - | 0.561 | 0.567 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +45 | ASIA | X89:logit2 | 0.536 [0.49,0.58] | 0.563 [0.50,0.63] | - | 0.561 | 0.567 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +10 | NY | X8:rf | 0.540 [0.50,0.59] | 0.556 [0.49,0.62] | - | 0.565 | 0.551 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +30 | ASIA | qr_p | 0.537 [0.49,0.58] | 0.556 [0.50,0.61] | - | 0.543 | 0.545 | ok | - | - | - | - |  | short by 0.104 AUC, 5 of 5 econ |
| X34X35-stack | +30 | ASIA | X89:logit2 | 0.553 [0.51,0.60] | 0.556 [0.50,0.61] | - | 0.547 | 0.557 | ok | - | - | - | - | stack | short by 0.104 AUC, 5 of 5 econ |
| X33-ghost-supervision | +10 | POOLED | gh_logit2 | 0.526 [0.50,0.55] | 0.555 [0.52,0.60] | - | 0.555 | 0.547 | N | - | - | - | - |  | promising: short by 0.125 AUC, 5 of 5 econ |
| X33-ghost-supervision | +15 | LONDON | gh_pair | 0.509 [0.47,0.55] | 0.553 [0.49,0.61] | - | 0.562 | 0.556 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +5 | ASIA | X9:gbt3 | 0.546 [0.50,0.59] | 0.547 [0.49,0.60] | - | 0.538 | 0.546 | ok | - | - | - | - | stack | short by 0.113 AUC, 5 of 5 econ |
| X34X35-stack | +10 | NY | X89:rf | 0.540 [0.50,0.59] | 0.546 [0.49,0.61] | - | 0.556 | 0.541 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +45 | LONDON | gh_logit2 | 0.496 [0.45,0.54] | 0.544 [0.49,0.61] | - | 0.549 | 0.532 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +30 | ASIA | X8:logit2 | 0.544 [0.50,0.59] | 0.544 [0.48,0.60] | - | 0.536 | 0.544 | ok | - | - | - | - | stack | short by 0.116 AUC, 5 of 5 econ |
| X34-stop-regime | +5 | ASIA | X8:gbt3 | 0.545 [0.50,0.59] | 0.543 [0.48,0.61] | - | 0.533 | 0.541 | ok | - | - | - | - | stack | short by 0.117 AUC, 5 of 5 econ |
| X35-orderflow-runs | pre | NY | X9:rf | 0.530 [0.49,0.57] | 0.542 [0.48,0.60] | - | 0.551 | 0.541 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | pre | ASIA | X9:rf | 0.540 [0.50,0.58] | 0.541 [0.48,0.60] | - | 0.531 | 0.542 | ok | - | - | - | - | stack | short by 0.119 AUC, 5 of 5 econ |
| X34X35-stack | +5 | ASIA | X89:gbt3 | 0.547 [0.50,0.59] | 0.540 [0.47,0.60] | - | 0.530 | 0.541 | ok | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| X33-ghost-supervision | +60 | POOLED | gh_logit2 | 0.511 [0.49,0.53] | 0.540 [0.50,0.57] | - | 0.538 | 0.547 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +45 | ASIA | qr_p | 0.543 [0.50,0.58] | 0.538 [0.48,0.59] | - | 0.518 | 0.523 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +30 | ASIA | X9:logit2 | 0.543 [0.50,0.59] | 0.537 [0.48,0.60] | - | 0.532 | 0.541 | ok | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| X34X35-stack | pre | NY | X89:rf | 0.528 [0.48,0.57] | 0.536 [0.47,0.60] | - | 0.534 | 0.536 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +45 | ASIA | gh_pair | 0.526 [0.48,0.57] | 0.534 [0.48,0.60] | - | 0.530 | 0.519 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +20 | ASIA | X89:stack | 0.538 [0.50,0.58] | 0.534 [0.48,0.58] | - | 0.525 | 0.539 | ok | - | - | - | - | stack | short by 0.126 AUC, 5 of 5 econ |
| X35-orderflow-runs | +60 | NY | X9:gbt3 | 0.500 [0.46,0.54] | 0.534 [0.47,0.60] | - | 0.528 | 0.534 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +60 | ASIA | gh_logit2 | 0.516 [0.47,0.56] | 0.534 [0.47,0.60] | - | 0.532 | 0.549 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +45 | ASIA | qr_lam | 0.556 [0.52,0.60] | 0.533 [0.47,0.59] | - | 0.517 | 0.502 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | pre | NY | X8:rf | 0.532 [0.48,0.58] | 0.533 [0.46,0.60] | - | 0.537 | 0.532 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +60 | NY | X89:gbt3 | 0.496 [0.45,0.54] | 0.532 [0.47,0.60] | - | 0.528 | 0.532 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +10 | LONDON | gh_logit2 | 0.513 [0.47,0.56] | 0.532 [0.47,0.60] | - | 0.529 | 0.519 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +15 | NY | gh_logit2 | 0.524 [0.49,0.56] | 0.530 [0.47,0.59] | - | 0.522 | 0.529 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +5 | ASIA | qr_p | 0.524 [0.48,0.57] | 0.529 [0.47,0.58] | - | 0.516 | 0.531 | ok | - | - | - | - |  | short by 0.131 AUC, 5 of 5 econ |
| X35-orderflow-runs | +60 | POOLED | X9:gbt3 | 0.513 [0.49,0.54] | 0.529 [0.49,0.57] | - | 0.527 | 0.522 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +60 | POOLED | X89:gbt3 | 0.512 [0.49,0.54] | 0.529 [0.49,0.57] | - | 0.527 | 0.522 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +15 | POOLED | gh_pair | 0.520 [0.50,0.54] | 0.528 [0.49,0.57] | - | 0.528 | 0.527 | N | - | - | - | - |  | short by 0.152 AUC, 5 of 5 econ |
| X36-quantile-count | +10 | LONDON | qr_p | 0.512 [0.47,0.55] | 0.527 [0.47,0.59] | - | 0.531 | 0.515 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +5 | POOLED | X8:gbt3 | 0.516 [0.49,0.54] | 0.527 [0.49,0.57] | - | 0.526 | 0.520 | ok | - | - | - | - | stack | short by 0.153 AUC, 5 of 5 econ |
| X33-ghost-supervision | +10 | ASIA | gh_pair | 0.538 [0.50,0.58] | 0.527 [0.47,0.58] | - | 0.518 | 0.522 | N | - | - | - | - |  | short by 0.133 AUC, 5 of 5 econ |
| X34-stop-regime | +60 | POOLED | X8:gbt3 | 0.507 [0.48,0.53] | 0.525 [0.49,0.56] | - | 0.523 | 0.516 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +45 | LONDON | X8:gbt3 | 0.521 [0.47,0.57] | 0.525 [0.46,0.60] | - | 0.516 | 0.503 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +20 | ASIA | qr_p | 0.538 [0.50,0.58] | 0.525 [0.47,0.57] | - | 0.508 | 0.519 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X34-stop-regime | +10 | POOLED | X8:rf | 0.526 [0.50,0.55] | 0.524 [0.49,0.56] | - | 0.524 | 0.518 | ok | - | - | - | - | stack | short by 0.156 AUC, 5 of 5 econ |
| X33-ghost-supervision | +20 | ASIA | gh_pair | 0.521 [0.47,0.57] | 0.523 [0.46,0.58] | - | 0.517 | 0.514 | N | - | - | - | - |  | dead (no gain over baseline) |
| X34X35-stack | +10 | POOLED | X89:rf | 0.526 [0.50,0.55] | 0.522 [0.49,0.56] | - | 0.523 | 0.517 | ok | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| X34-stop-regime | +60 | ASIA | X8:logit2 | 0.513 [0.47,0.56] | 0.522 [0.46,0.59] | - | 0.518 | 0.519 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | pre | POOLED | X89:rf | 0.521 [0.50,0.55] | 0.522 [0.49,0.56] | - | 0.519 | 0.518 | ok | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| X35-orderflow-runs | +10 | LONDON | X9:rf | 0.527 [0.49,0.57] | 0.521 [0.46,0.59] | - | 0.518 | 0.510 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +60 | ASIA | qr_lam | 0.547 [0.50,0.59] | 0.521 [0.46,0.58] | - | 0.499 | 0.483 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +5 | NY | X89:gbt3 | 0.508 [0.47,0.55] | 0.520 [0.47,0.57] | - | 0.530 | 0.516 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +20 | LONDON | X89:gbt3 | 0.514 [0.47,0.56] | 0.520 [0.47,0.57] | - | 0.518 | 0.500 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +60 | ASIA | X89:logit2 | 0.513 [0.47,0.55] | 0.520 [0.46,0.59] | - | 0.516 | 0.517 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +60 | ASIA | X9:logit2 | 0.513 [0.47,0.56] | 0.520 [0.46,0.59] | - | 0.516 | 0.517 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +20 | LONDON | X9:gbt3 | 0.515 [0.48,0.56] | 0.520 [0.46,0.58] | - | 0.517 | 0.491 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +45 | POOLED | X9:rf | 0.507 [0.48,0.53] | 0.520 [0.48,0.56] | - | 0.517 | 0.508 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +20 | ASIA | qr_lam | 0.545 [0.51,0.58] | 0.519 [0.47,0.57] | - | 0.498 | 0.508 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X35-orderflow-runs | +10 | POOLED | X9:rf | 0.523 [0.50,0.55] | 0.518 [0.48,0.56] | - | 0.519 | 0.513 | ok | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| X35-orderflow-runs | +45 | LONDON | X9:gbt3 | 0.510 [0.47,0.56] | 0.518 [0.46,0.58] | - | 0.509 | 0.496 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +10 | ASIA | X89:gbt3 | 0.529 [0.49,0.57] | 0.517 [0.45,0.58] | - | 0.501 | 0.510 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X34X35-stack | +20 | POOLED | X89:stack | 0.524 [0.50,0.55] | 0.517 [0.47,0.56] | - | 0.514 | 0.513 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X35-orderflow-runs | pre | POOLED | X9:rf | 0.516 [0.49,0.54] | 0.516 [0.48,0.55] | - | 0.516 | 0.512 | ok | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X34-stop-regime | pre | ASIA | X8:gbt3 | 0.536 [0.49,0.58] | 0.516 [0.45,0.58] | - | 0.506 | 0.515 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X33-ghost-supervision | +60 | NY | gh_gbt3 | 0.485 [0.44,0.53] | 0.515 [0.46,0.57] | - | 0.511 | 0.508 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +10 | LONDON | X8:rf | 0.520 [0.48,0.57] | 0.515 [0.45,0.58] | - | 0.512 | 0.501 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | pre | POOLED | X8:rf | 0.517 [0.49,0.54] | 0.514 [0.48,0.55] | - | 0.511 | 0.511 | ok | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| X34X35-stack | +5 | POOLED | X89:rf | 0.513 [0.49,0.54] | 0.514 [0.47,0.56] | - | 0.511 | 0.505 | ok | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| X35-orderflow-runs | +5 | POOLED | X9:rf | 0.512 [0.48,0.54] | 0.513 [0.47,0.56] | - | 0.511 | 0.503 | ok | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X36-qr-lambda-diag | +15 | ASIA | qr_lam | 0.534 [0.50,0.57] | 0.513 [0.46,0.56] | - | 0.486 | 0.503 | ok | - | - | - | - |  | short by 0.147 AUC, 5 of 5 econ |
| X34X35-stack | +10 | LONDON | X89:rf | 0.521 [0.48,0.56] | 0.512 [0.45,0.57] | - | 0.505 | 0.503 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +20 | ASIA | X8:stack | 0.543 [0.50,0.58] | 0.511 [0.45,0.56] | - | 0.500 | 0.516 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X34-stop-regime | +45 | POOLED | X8:rf | 0.508 [0.48,0.54] | 0.511 [0.48,0.55] | - | 0.511 | 0.499 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +45 | POOLED | X89:rf | 0.504 [0.48,0.53] | 0.511 [0.48,0.55] | - | 0.509 | 0.499 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +45 | NY | gh_gbt3 | 0.493 [0.45,0.53] | 0.510 [0.44,0.58] | - | 0.505 | 0.511 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +15 | ASIA | X89:stack | 0.536 [0.50,0.57] | 0.510 [0.44,0.58] | - | 0.497 | 0.504 | ok | - | - | - | - | stack | short by 0.150 AUC, 5 of 5 econ |
| X33-ghost-supervision | +45 | POOLED | gh_gbt3 | 0.497 [0.47,0.52] | 0.510 [0.47,0.55] | - | 0.507 | 0.498 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +10 | NY | X9:rf | 0.519 [0.48,0.57] | 0.509 [0.44,0.58] | - | 0.515 | 0.507 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +60 | LONDON | gh_gbt3 | 0.505 [0.46,0.55] | 0.509 [0.45,0.57] | - | 0.514 | 0.495 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +5 | ASIA | gh_pair | 0.518 [0.48,0.56] | 0.509 [0.45,0.57] | - | 0.499 | 0.506 | N | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| X36-qr-lambda-diag | +30 | ASIA | qr_lam | 0.546 [0.50,0.59] | 0.509 [0.45,0.57] | - | 0.485 | 0.490 | ok | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| X36-quantile-count | +20 | LONDON | qr_p | 0.504 [0.46,0.54] | 0.508 [0.45,0.57] | - | 0.506 | 0.508 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +10 | POOLED | qr_p | 0.502 [0.48,0.52] | 0.507 [0.47,0.54] | - | 0.504 | 0.506 | ok | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| X33-ghost-supervision | +30 | ASIA | gh_logit2 | 0.487 [0.44,0.53] | 0.507 [0.45,0.56] | - | 0.501 | 0.505 | N | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| X33-ghost-supervision | +30 | LONDON | gh_gbt3 | 0.511 [0.47,0.56] | 0.506 [0.44,0.57] | - | 0.498 | 0.490 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +5 | POOLED | qr_p | 0.512 [0.49,0.54] | 0.506 [0.47,0.54] | - | 0.502 | 0.503 | ok | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| X36-quantile-count | +30 | POOLED | qr_p | 0.498 [0.47,0.52] | 0.505 [0.47,0.54] | - | 0.505 | 0.500 | ok | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| X35-orderflow-runs | +10 | ASIA | X9:stack | 0.537 [0.50,0.58] | 0.505 [0.43,0.58] | - | 0.493 | 0.498 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X36-quantile-count | pre | LONDON | qr_p | 0.495 [0.45,0.54] | 0.505 [0.45,0.57] | - | 0.501 | 0.504 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +5 | NY | X9:gbt3 | 0.500 [0.46,0.54] | 0.505 [0.45,0.55] | - | 0.516 | 0.498 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +30 | POOLED | gh_logit2 | 0.494 [0.47,0.52] | 0.504 [0.47,0.54] | - | 0.503 | 0.501 | N | - | - | - | - |  | short by 0.176 AUC, 5 of 5 econ |
| X33-ghost-supervision | +15 | ASIA | gh_pair | 0.528 [0.49,0.57] | 0.503 [0.45,0.56] | - | 0.491 | 0.500 | N | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| X34X35-stack | +15 | NY | X89:logit2 | 0.511 [0.47,0.56] | 0.503 [0.44,0.57] | - | 0.504 | 0.494 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +60 | LONDON | X9:rf | 0.523 [0.47,0.57] | 0.503 [0.43,0.57] | - | 0.501 | 0.494 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | pre | ASIA | X89:stack | 0.540 [0.51,0.57] | 0.502 [0.44,0.56] | - | 0.478 | 0.502 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X33-ghost-supervision | +5 | NY | gh_logit2 | 0.495 [0.45,0.54] | 0.502 [0.44,0.56] | - | 0.499 | 0.495 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | pre | POOLED | gh_logit2 | 0.503 [0.48,0.53] | 0.502 [0.46,0.54] | - | 0.505 | 0.502 | N | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| X34X35-stack | +60 | LONDON | X89:rf | 0.521 [0.47,0.57] | 0.502 [0.43,0.57] | - | 0.502 | 0.493 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +10 | NY | qr_p | 0.483 [0.43,0.53] | 0.502 [0.43,0.57] | - | 0.504 | 0.508 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +5 | POOLED | gh_pair | 0.499 [0.47,0.53] | 0.502 [0.46,0.54] | - | 0.500 | 0.499 | N | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| X34-stop-regime | +20 | POOLED | X8:stack | 0.518 [0.49,0.54] | 0.499 [0.46,0.54] | - | 0.494 | 0.494 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X36-quantile-count | +20 | POOLED | qr_p | 0.511 [0.49,0.53] | 0.499 [0.46,0.53] | - | 0.497 | 0.498 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X35-orderflow-runs | +20 | ASIA | X9:stack | 0.532 [0.49,0.57] | 0.498 [0.44,0.56] | - | 0.483 | 0.498 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X36-quantile-count | +5 | NY | qr_p | 0.502 [0.46,0.55] | 0.498 [0.42,0.57] | - | 0.489 | 0.504 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +15 | NY | X8:logit2 | 0.513 [0.47,0.56] | 0.498 [0.43,0.57] | - | 0.502 | 0.490 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +5 | ASIA | qr_lam | 0.534 [0.49,0.57] | 0.498 [0.45,0.55] | - | 0.474 | 0.497 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X34X35-stack | +45 | LONDON | X89:rf | 0.503 [0.45,0.55] | 0.498 [0.42,0.57] | - | 0.485 | 0.476 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +60 | NY | qr_lam | 0.496 [0.45,0.54] | 0.497 [0.43,0.56] | - | 0.487 | 0.476 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +20 | NY | X89:stack | 0.536 [0.50,0.58] | 0.496 [0.42,0.56] | - | 0.504 | 0.494 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +45 | NY | X9:rf | 0.486 [0.44,0.53] | 0.495 [0.44,0.56] | - | 0.499 | 0.491 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +30 | LONDON | qr_lam | 0.513 [0.47,0.56] | 0.495 [0.43,0.56] | - | 0.497 | 0.452 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +10 | ASIA | qr_lam | 0.540 [0.50,0.58] | 0.495 [0.44,0.55] | - | 0.469 | 0.488 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X35-orderflow-runs | +15 | NY | X9:logit2 | 0.505 [0.46,0.55] | 0.494 [0.43,0.56] | - | 0.497 | 0.485 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +5 | LONDON | X89:stack | 0.515 [0.47,0.56] | 0.494 [0.43,0.57] | - | 0.485 | 0.478 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +10 | ASIA | qr_p | 0.511 [0.47,0.55] | 0.494 [0.43,0.56] | - | 0.480 | 0.495 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X34-stop-regime | +20 | NY | X8:stack | 0.528 [0.49,0.57] | 0.493 [0.42,0.56] | - | 0.500 | 0.489 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +45 | LONDON | qr_p | 0.489 [0.45,0.53] | 0.492 [0.44,0.55] | - | 0.486 | 0.486 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +30 | LONDON | qr_p | 0.466 [0.42,0.51] | 0.492 [0.44,0.55] | - | 0.488 | 0.491 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +60 | ASIA | qr_p | 0.530 [0.48,0.58] | 0.491 [0.42,0.56] | - | 0.477 | 0.462 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +45 | POOLED | qr_lam | 0.511 [0.49,0.54] | 0.491 [0.46,0.53] | - | 0.485 | 0.462 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +10 | ASIA | X8:stack | 0.542 [0.50,0.58] | 0.491 [0.43,0.56] | - | 0.481 | 0.487 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X34X35-stack | +45 | NY | X89:rf | 0.489 [0.45,0.53] | 0.490 [0.43,0.56] | - | 0.493 | 0.485 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +30 | NY | gh_pair | 0.508 [0.46,0.56] | 0.490 [0.42,0.56] | - | 0.488 | 0.495 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | pre | LONDON | gh_logit2 | 0.474 [0.43,0.52] | 0.490 [0.42,0.56] | - | 0.498 | 0.499 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +5 | LONDON | qr_p | 0.510 [0.47,0.55] | 0.490 [0.43,0.56] | - | 0.489 | 0.475 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +45 | POOLED | qr_p | 0.502 [0.48,0.53] | 0.489 [0.46,0.52] | - | 0.488 | 0.477 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +15 | LONDON | qr_p | 0.490 [0.44,0.54] | 0.489 [0.42,0.56] | - | 0.486 | 0.487 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +15 | ASIA | qr_p | 0.507 [0.46,0.55] | 0.489 [0.42,0.55] | - | 0.476 | 0.483 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X36-qr-lambda-diag | +60 | POOLED | qr_lam | 0.505 [0.48,0.53] | 0.489 [0.45,0.53] | - | 0.483 | 0.455 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +45 | NY | X8:rf | 0.490 [0.45,0.53] | 0.488 [0.42,0.55] | - | 0.487 | 0.483 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +45 | LONDON | qr_lam | 0.510 [0.46,0.56] | 0.488 [0.43,0.55] | - | 0.487 | 0.447 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +30 | POOLED | qr_lam | 0.514 [0.49,0.54] | 0.487 [0.46,0.52] | - | 0.473 | 0.463 | ok | - | - | - | - |  | short by 0.193 AUC, 5 of 5 econ |
| X36-quantile-count | +15 | POOLED | qr_p | 0.492 [0.47,0.52] | 0.487 [0.45,0.52] | - | 0.482 | 0.487 | ok | - | - | - | - |  | short by 0.193 AUC, 5 of 5 econ |
| X36-qr-lambda-diag | pre | ASIA | qr_lam | 0.538 [0.50,0.57] | 0.487 [0.43,0.54] | - | 0.452 | 0.486 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X36-qr-lambda-diag | +15 | LONDON | qr_lam | 0.511 [0.47,0.56] | 0.487 [0.43,0.55] | - | 0.473 | 0.448 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +5 | LONDON | qr_lam | 0.514 [0.47,0.56] | 0.486 [0.43,0.55] | - | 0.481 | 0.451 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | pre | POOLED | qr_p | 0.511 [0.48,0.54] | 0.486 [0.45,0.53] | - | 0.486 | 0.485 | ok | - | - | - | - |  | WF-only (dead) |
| X34-stop-regime | +15 | LONDON | X8:stack | 0.513 [0.47,0.56] | 0.486 [0.43,0.55] | - | 0.478 | 0.465 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +15 | NY | qr_p | 0.479 [0.43,0.52] | 0.486 [0.42,0.55] | - | 0.479 | 0.488 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +15 | LONDON | X89:stack | 0.520 [0.48,0.57] | 0.485 [0.42,0.55] | - | 0.473 | 0.463 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +45 | ASIA | X9:stack | 0.516 [0.47,0.56] | 0.485 [0.42,0.55] | - | 0.478 | 0.468 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +10 | LONDON | qr_lam | 0.511 [0.47,0.56] | 0.485 [0.42,0.55] | - | 0.481 | 0.448 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +20 | POOLED | X9:stack | 0.507 [0.48,0.53] | 0.484 [0.44,0.52] | - | 0.479 | 0.480 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X33-ghost-supervision | +20 | POOLED | gh_pair | 0.495 [0.47,0.52] | 0.484 [0.45,0.52] | - | 0.478 | 0.476 | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-ghost-supervision | pre | NY | gh_logit2 | 0.514 [0.47,0.56] | 0.483 [0.40,0.56] | - | 0.478 | 0.480 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +15 | POOLED | qr_lam | 0.509 [0.48,0.53] | 0.482 [0.45,0.52] | - | 0.469 | 0.464 | ok | - | - | - | - |  | short by 0.198 AUC, 5 of 5 econ |
| X36-qr-lambda-diag | +20 | LONDON | qr_lam | 0.512 [0.47,0.56] | 0.482 [0.42,0.55] | - | 0.476 | 0.443 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +60 | LONDON | qr_lam | 0.501 [0.45,0.55] | 0.482 [0.42,0.54] | - | 0.482 | 0.439 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +5 | LONDON | gh_pair | 0.495 [0.45,0.54] | 0.481 [0.41,0.55] | - | 0.478 | 0.480 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +60 | LONDON | qr_p | 0.493 [0.45,0.54] | 0.481 [0.42,0.54] | - | 0.475 | 0.467 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +20 | POOLED | qr_lam | 0.509 [0.49,0.53] | 0.480 [0.45,0.52] | - | 0.463 | 0.461 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X36-quantile-count | pre | NY | qr_p | 0.519 [0.48,0.56] | 0.480 [0.42,0.55] | - | 0.491 | 0.482 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | pre | LONDON | X89:stack | 0.501 [0.46,0.55] | 0.479 [0.42,0.54] | - | 0.472 | 0.459 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | pre | LONDON | X8:stack | 0.492 [0.45,0.54] | 0.479 [0.42,0.54] | - | 0.471 | 0.462 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +60 | POOLED | qr_p | 0.508 [0.48,0.53] | 0.479 [0.44,0.52] | - | 0.477 | 0.461 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +5 | POOLED | qr_lam | 0.509 [0.48,0.54] | 0.479 [0.44,0.52] | - | 0.468 | 0.464 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X35-orderflow-runs | +15 | ASIA | X9:stack | 0.525 [0.49,0.56] | 0.478 [0.41,0.54] | - | 0.463 | 0.470 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X33-ghost-supervision | pre | ASIA | gh_gbt3 | 0.504 [0.46,0.54] | 0.477 [0.41,0.54] | - | 0.460 | 0.476 | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-stop-regime | +5 | LONDON | X8:stack | 0.503 [0.46,0.55] | 0.476 [0.41,0.54] | - | 0.469 | 0.457 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +45 | NY | qr_lam | 0.492 [0.45,0.54] | 0.471 [0.41,0.54] | - | 0.469 | 0.455 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +15 | POOLED | X89:stack | 0.514 [0.49,0.54] | 0.470 [0.43,0.52] | - | 0.463 | 0.460 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X35-orderflow-runs | +5 | LONDON | X9:stack | 0.505 [0.45,0.56] | 0.469 [0.40,0.54] | - | 0.454 | 0.455 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +10 | POOLED | qr_lam | 0.504 [0.48,0.53] | 0.469 [0.43,0.51] | - | 0.460 | 0.452 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X36-qr-lambda-diag | pre | LONDON | qr_lam | 0.508 [0.47,0.55] | 0.468 [0.41,0.54] | - | 0.442 | 0.433 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +20 | LONDON | gh_pair | 0.483 [0.44,0.53] | 0.465 [0.40,0.53] | - | 0.447 | 0.459 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +30 | NY | qr_p | 0.487 [0.44,0.53] | 0.465 [0.40,0.53] | - | 0.459 | 0.459 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +15 | POOLED | X8:stack | 0.506 [0.48,0.53] | 0.465 [0.42,0.51] | - | 0.457 | 0.455 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X36-quantile-count | pre | ASIA | qr_p | 0.513 [0.47,0.55] | 0.464 [0.41,0.52] | - | 0.459 | 0.463 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X34-stop-regime | +60 | LONDON | X8:stack | 0.515 [0.47,0.56] | 0.463 [0.40,0.53] | - | 0.463 | 0.440 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | pre | POOLED | qr_lam | 0.503 [0.48,0.53] | 0.462 [0.43,0.50] | - | 0.439 | 0.448 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X36-quantile-count | +20 | NY | qr_p | 0.492 [0.45,0.53] | 0.461 [0.40,0.53] | - | 0.462 | 0.462 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +15 | POOLED | X9:stack | 0.505 [0.48,0.53] | 0.458 [0.42,0.51] | - | 0.452 | 0.446 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X35-orderflow-runs | +20 | NY | X9:stack | 0.506 [0.47,0.55] | 0.456 [0.40,0.52] | - | 0.461 | 0.454 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +30 | NY | qr_lam | 0.495 [0.45,0.54] | 0.456 [0.40,0.52] | - | 0.443 | 0.441 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +60 | NY | X8:stack | 0.477 [0.43,0.52] | 0.455 [0.38,0.53] | - | 0.452 | 0.451 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +30 | LONDON | X8:stack | 0.506 [0.46,0.55] | 0.454 [0.39,0.52] | - | 0.456 | 0.451 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +15 | LONDON | X9:stack | 0.511 [0.47,0.56] | 0.454 [0.39,0.51] | - | 0.447 | 0.432 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +5 | NY | qr_lam | 0.476 [0.43,0.52] | 0.450 [0.39,0.51] | - | 0.465 | 0.441 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | pre | LONDON | X9:stack | 0.495 [0.45,0.54] | 0.447 [0.38,0.51] | - | 0.443 | 0.431 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +30 | POOLED | X8:stack | 0.494 [0.47,0.52] | 0.445 [0.41,0.48] | - | 0.442 | 0.442 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X36-qr-lambda-diag | +15 | NY | qr_lam | 0.481 [0.44,0.53] | 0.444 [0.38,0.51] | - | 0.468 | 0.436 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +20 | NY | qr_lam | 0.477 [0.44,0.52] | 0.443 [0.39,0.51] | - | 0.444 | 0.435 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | +10 | NY | qr_lam | 0.476 [0.43,0.52] | 0.443 [0.39,0.50] | - | 0.460 | 0.434 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33-ghost-supervision | +20 | NY | gh_pair | 0.471 [0.43,0.51] | 0.443 [0.39,0.50] | - | 0.450 | 0.438 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +30 | LONDON | X89:stack | 0.500 [0.45,0.54] | 0.438 [0.38,0.49] | - | 0.437 | 0.436 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-quantile-count | +60 | NY | qr_p | 0.484 [0.44,0.53] | 0.433 [0.37,0.50] | - | 0.441 | 0.423 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +30 | POOLED | X9:stack | 0.485 [0.46,0.51] | 0.433 [0.40,0.47] | - | 0.432 | 0.438 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X36-quantile-count | +45 | NY | qr_p | 0.469 [0.42,0.51] | 0.431 [0.38,0.49] | - | 0.432 | 0.418 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36-qr-lambda-diag | pre | NY | qr_lam | 0.461 [0.42,0.51] | 0.431 [0.36,0.50] | - | 0.428 | 0.421 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +30 | POOLED | X89:stack | 0.488 [0.46,0.51] | 0.429 [0.39,0.47] | - | 0.425 | 0.430 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X35-orderflow-runs | +30 | LONDON | X9:stack | 0.488 [0.44,0.54] | 0.423 [0.36,0.49] | - | 0.429 | 0.427 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35-orderflow-runs | +30 | NY | X9:stack | 0.469 [0.42,0.52] | 0.423 [0.35,0.50] | - | 0.433 | 0.426 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +5 | NY | X8:stack | 0.467 [0.42,0.51] | 0.417 [0.36,0.48] | - | 0.423 | 0.414 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34-stop-regime | +30 | NY | X8:stack | 0.475 [0.42,0.52] | 0.403 [0.34,0.47] | - | 0.412 | 0.401 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34X35-stack | +30 | NY | X89:stack | 0.467 [0.41,0.51] | 0.399 [0.33,0.47] | - | 0.406 | 0.396 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |

One-sentence notes:
- X33-ghost-supervision 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X33-ghost-supervision 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34-stop-regime 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X34X35-stack 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X35-orderflow-runs 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-qr-lambda-diag 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X36-quantile-count 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
