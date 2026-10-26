# PRED ROUND 77 - block K round 8 - K8-unlocked-latefusion

Best HOLDOUT F-R AUC: +15 POOLED 0.454 [0.41,0.50] | ASIA 0.483 [0.42,0.54] | LONDON 0.486 [0.42,0.55] | NY 0.392 [0.32,0.46]
Best HOLDOUT F-R AUC: +30 POOLED 0.472 [0.43,0.51] | ASIA 0.505 [0.44,0.57] | LONDON 0.491 [0.43,0.55] | NY 0.423 [0.36,0.48]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.149 AUC, 5 of 5 economic conditions short.
not found - short by 0.149 AUC and 5 of 5 economic conditions

prereg d430f130ee5cdf43788720333b64abeea705d72143910580ac5a1196dd8e9b34 ; trials added 700 ; truncation audit {'decisions': 0, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K8-unlocked-latefusion-top10 | pre | ASIA | AVGtop10(+R0u_B) | 0.541 [0.51,0.58] | 0.511 [0.46,0.56] | - | 0.513 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K8-unlocked-latefusion-top10 | +30 | ASIA | AVGtop10(+R0u_B) | 0.549 [0.51,0.59] | 0.505 [0.44,0.57] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| K8-unlocked-latefusion-top10 | +45 | ASIA | AVGtop10(+R0u_B) | 0.534 [0.49,0.57] | 0.499 [0.43,0.56] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +20 | ASIA | AVGtop10(+R0u_B) | 0.545 [0.51,0.58] | 0.493 [0.43,0.55] | - | 0.479 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K8-unlocked-latefusion-top10 | +30 | LONDON | AVGtop10(+R0u_B) | 0.520 [0.47,0.57] | 0.491 [0.43,0.55] | - | 0.484 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +10 | ASIA | AVGtop10(+R0u_B) | 0.544 [0.51,0.58] | 0.488 [0.43,0.55] | - | 0.474 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K8-unlocked-latefusion-top10 | +5 | ASIA | AVGtop10(+R0u_B) | 0.525 [0.49,0.56] | 0.488 [0.43,0.54] | - | 0.490 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K8-unlocked-latefusion-top10 | +15 | LONDON | AVGtop10(+R0u_B) | 0.521 [0.48,0.57] | 0.486 [0.42,0.55] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +15 | ASIA | AVGtop10(+R0u_B) | 0.537 [0.50,0.57] | 0.483 [0.42,0.54] | - | 0.476 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K8-unlocked-latefusion-top10 | +60 | ASIA | AVGtop10(+R0u_B) | 0.548 [0.50,0.59] | 0.476 [0.40,0.55] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +20 | LONDON | AVGtop10(+R0u_B) | 0.508 [0.46,0.56] | 0.475 [0.42,0.53] | - | 0.462 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +30 | POOLED | AVGtop10(+R0u_B) | 0.519 [0.49,0.55] | 0.472 [0.43,0.51] | - | 0.466 | - | - | - | - | - | - | stack | short by 0.208 AUC, 5 of 5 econ |
| K8-unlocked-latefusion-top10 | +20 | POOLED | AVGtop10(+R0u_B) | 0.514 [0.49,0.54] | 0.467 [0.43,0.51] | - | 0.461 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K8-unlocked-latefusion-top10 | pre | POOLED | AVGtop10(+R0u_B) | 0.504 [0.48,0.53] | 0.456 [0.42,0.49] | - | 0.456 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K8-unlocked-latefusion-top10 | +15 | POOLED | AVGtop10(+R0u_B) | 0.510 [0.48,0.54] | 0.454 [0.41,0.50] | - | 0.452 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K8-unlocked-latefusion-top10 | +45 | POOLED | AVGtop10(+R0u_B) | 0.507 [0.48,0.54] | 0.446 [0.41,0.48] | - | 0.439 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | pre | LONDON | AVGtop10(+R0u_B) | 0.508 [0.46,0.56] | 0.446 [0.38,0.51] | - | 0.440 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +5 | POOLED | AVGtop10(+R0u_B) | 0.498 [0.47,0.52] | 0.446 [0.40,0.49] | - | 0.442 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K8-unlocked-latefusion-top10 | +5 | LONDON | AVGtop10(+R0u_B) | 0.505 [0.46,0.55] | 0.443 [0.38,0.50] | - | 0.439 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +10 | LONDON | AVGtop10(+R0u_B) | 0.511 [0.46,0.56] | 0.443 [0.38,0.50] | - | 0.427 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +60 | POOLED | AVGtop10(+R0u_B) | 0.520 [0.49,0.55] | 0.442 [0.39,0.49] | - | 0.434 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +10 | POOLED | AVGtop10(+R0u_B) | 0.506 [0.48,0.53] | 0.441 [0.40,0.48] | - | 0.433 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K8-unlocked-latefusion-top10 | +60 | NY | AVGtop10(+R0u_B) | 0.495 [0.45,0.54] | 0.432 [0.36,0.50] | - | 0.418 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +45 | LONDON | AVGtop10(+R0u_B) | 0.508 [0.46,0.56] | 0.428 [0.37,0.48] | - | 0.412 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +20 | NY | AVGtop10(+R0u_B) | 0.488 [0.44,0.53] | 0.428 [0.37,0.49] | - | 0.436 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +30 | NY | AVGtop10(+R0u_B) | 0.489 [0.44,0.53] | 0.423 [0.36,0.48] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +60 | LONDON | AVGtop10(+R0u_B) | 0.512 [0.46,0.56] | 0.408 [0.35,0.47] | - | 0.388 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +5 | NY | AVGtop10(+R0u_B) | 0.466 [0.42,0.51] | 0.407 [0.35,0.47] | - | 0.410 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +45 | NY | AVGtop10(+R0u_B) | 0.477 [0.43,0.52] | 0.406 [0.34,0.47] | - | 0.393 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | pre | NY | AVGtop10(+R0u_B) | 0.462 [0.42,0.51] | 0.404 [0.35,0.47] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +15 | NY | AVGtop10(+R0u_B) | 0.473 [0.43,0.52] | 0.392 [0.32,0.46] | - | 0.401 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K8-unlocked-latefusion-top10 | +10 | NY | AVGtop10(+R0u_B) | 0.461 [0.42,0.50] | 0.391 [0.33,0.46] | - | 0.390 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |

One-sentence notes:
- K8-unlocked-latefusion-top10 0 POOLED: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 5 POOLED: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 10 POOLED: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 15 POOLED: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 20 POOLED: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 30 POOLED: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 45 POOLED: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 60 POOLED: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 0 ASIA: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 5 ASIA: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 10 ASIA: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 15 ASIA: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 20 ASIA: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 30 ASIA: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 45 ASIA: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 60 ASIA: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 0 LONDON: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 5 LONDON: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 10 LONDON: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 15 LONDON: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 20 LONDON: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 30 LONDON: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 45 LONDON: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 60 LONDON: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 0 NY: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 5 NY: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 10 NY: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 15 NY: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 20 NY: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 30 NY: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 45 NY: top-10 source selection on WF-PRE overfits: holdout below chance
- K8-unlocked-latefusion-top10 60 NY: top-10 source selection on WF-PRE overfits: holdout below chance
