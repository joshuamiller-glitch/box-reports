# PRED ROUND 33 - block X5 round 1 - X23-counterfactual-skip+X22-trade-level-stop-gap

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.629 [0.56,0.70]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 96fffac8e39a980ac50ec195e834009394c1c81e9502d1f3bbbda6fc9018f848 ; trials added 260 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False, 'note': 'X22 GEO: 360 decisions x48 features 0 mismatches; X23 label locality: effect on single stream index'} ; holdout scored True ; feature store ['l2vast/pred/store/X22_geo_sig.parquet', 'l2vast/pred/store/X5/x23_labels.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X22-trade-level-stop-gap+base | sig | LONDON/ST | X22V2R:stack | 0.633 [0.59,0.67] | 0.629 [0.56,0.70] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X22-trade-level-stop-gap+base | sig | NY/ST | X22V2R:stack | 0.602 [0.55,0.64] | 0.620 [0.55,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X22-trade-level-stop-gap+base | sig | POOLED/ST | X22V2R:stack | 0.597 [0.57,0.62] | 0.612 [0.58,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X22-trade-level-stop-gap+base | sig | NY | X22V2R:stack | 0.604 [0.57,0.64] | 0.611 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X22-trade-level-stop-gap+base | sig | LONDON | X22V2R:stack | 0.616 [0.58,0.65] | 0.609 [0.56,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X22-trade-level-stop-gap+base | sig | ASIA/HM | X22V2R:stack | 0.587 [0.56,0.62] | 0.609 [0.58,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X22-trade-level-stop-gap+base | sig | POOLED | X22V2R:stack | 0.594 [0.58,0.61] | 0.606 [0.58,0.63] | - | - | - | ok | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| X22-trade-level-stop-gap+base | sig | ASIA | X22V2R:stack | 0.576 [0.55,0.60] | 0.602 [0.58,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X22-trade-level-stop-gap+base | sig | POOLED/HM | X22V2R:stack | 0.592 [0.57,0.61] | 0.601 [0.57,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X22-trade-level-stop-gap+base | sig | ASIA/ST | X22V2R:stack | 0.566 [0.54,0.60] | 0.598 [0.57,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X22-trade-level-stop-gap+base | sig | NY/HM | X22V2R:stack | 0.604 [0.56,0.65] | 0.597 [0.53,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X22-trade-level-stop-gap+base | sig | LONDON/HM | X22V2R:stack | 0.599 [0.56,0.64] | 0.594 [0.53,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X23-counterfactual-skip | sig | NY/HM | X23M1:stack | 0.554 [0.50,0.60] | 0.589 [0.50,0.67] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | NY | X23M1:stack | 0.529 [0.49,0.57] | 0.551 [0.49,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X22-trade-level-stop-gap | sig | LONDON/HM | X22V1T:stack | 0.486 [0.44,0.53] | 0.541 [0.49,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | LONDON/ST | X23M1:stack | 0.509 [0.47,0.55] | 0.538 [0.48,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | NY/HM | X23M1:stack | 0.526 [0.47,0.58] | 0.535 [0.45,0.62] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X22-trade-level-stop-gap | sig | NY/ST | X22V1T:stack | 0.555 [0.50,0.61] | 0.535 [0.47,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X22-trade-level-stop-gap | sig | LONDON | X22V1T:stack | 0.498 [0.46,0.53] | 0.533 [0.49,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | LONDON/ST | X23M1:stack | 0.499 [0.45,0.54] | 0.531 [0.47,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | LONDON | X23M1:stack | 0.491 [0.46,0.53] | 0.530 [0.48,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X22-trade-level-stop-gap | sig | LONDON/ST | X22V1T:stack | 0.510 [0.47,0.55] | 0.526 [0.46,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | LONDON | X23M1:stack | 0.485 [0.45,0.52] | 0.526 [0.48,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | NY/ST | X23M1:stack | 0.506 [0.46,0.56] | 0.521 [0.45,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | LONDON/HM | X23M1:stack | 0.473 [0.43,0.52] | 0.520 [0.46,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | LONDON/HM | X23M1:stack | 0.472 [0.42,0.52] | 0.519 [0.45,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X22-trade-level-stop-gap | sig | POOLED/HM | X22V1T:stack | 0.490 [0.46,0.52] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X22-trade-level-stop-gap | sig | NY | X22V1T:stack | 0.509 [0.47,0.54] | 0.512 [0.46,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X22-trade-level-stop-gap | sig | POOLED | X22V1T:stack | 0.502 [0.48,0.52] | 0.509 [0.48,0.53] | - | - | - | N | 2278 | -21836 | - | 2/5 |  | locked label (reference only) |
| X22-trade-level-stop-gap | sig | ASIA/HM | X22V1T:stack | 0.505 [0.47,0.54] | 0.508 [0.45,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X22-trade-level-stop-gap | sig | POOLED/ST | X22V1T:stack | 0.513 [0.49,0.54] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | NY | X23M1:stack | 0.499 [0.46,0.54] | 0.502 [0.44,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X22-trade-level-stop-gap | sig | ASIA | X22V1T:stack | 0.501 [0.47,0.53] | 0.496 [0.46,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | POOLED/HM | X23M1:stack | 0.490 [0.46,0.51] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | POOLED/ST | X23M1:stack | 0.497 [0.47,0.52] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | POOLED | X23M1:stack | 0.494 [0.47,0.51] | 0.495 [0.47,0.52] | - | - | - | N | 2264 | 109739 | - | 1/5 |  | locked label (reference only) |
| X22-trade-level-stop-gap | sig | ASIA/ST | X22V1T:stack | 0.498 [0.47,0.53] | 0.485 [0.44,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | POOLED/HM | X23M1:stack | 0.481 [0.45,0.50] | 0.483 [0.45,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | POOLED | X23M1:stack | 0.483 [0.46,0.50] | 0.483 [0.46,0.51] | - | - | - | N | 2264 | 109739 | - | 1/5 |  | locked label (reference only) |
| X23-counterfactual-skip | sig | POOLED/ST | X23M1:stack | 0.485 [0.46,0.51] | 0.482 [0.45,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X22-trade-level-stop-gap | sig | NY/HM | X22V1T:stack | 0.457 [0.41,0.50] | 0.480 [0.42,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | NY/ST | X23M1:stack | 0.475 [0.43,0.53] | 0.478 [0.40,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | ASIA/ST | X23M1:stack | 0.480 [0.44,0.52] | 0.465 [0.42,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | ASIA/ST | X23M1:stack | 0.479 [0.44,0.52] | 0.462 [0.42,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | ASIA | X23M1:stack | 0.473 [0.44,0.50] | 0.457 [0.42,0.50] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | ASIA | X23M1:stack | 0.474 [0.44,0.50] | 0.456 [0.42,0.50] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | ASIA/HM | X23M1:stack | 0.467 [0.43,0.50] | 0.449 [0.40,0.50] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X23-counterfactual-skip | sig | ASIA/HM | X23M1:stack | 0.465 [0.43,0.50] | 0.448 [0.40,0.50] | - | - | - | N | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- X23-counterfactual-skip -1 POOLED: P(harmful by R11 marginal) vs stop_vs_target; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 ASIA: P(harmful by R11 marginal) vs stop_vs_target; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 LONDON: P(harmful by R11 marginal) vs stop_vs_target; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 NY: P(harmful by R11 marginal) vs stop_vs_target; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 POOLED: P(harmful by R11 marginal) vs stop_vs_target; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 ASIA: P(harmful by R11 marginal) vs stop_vs_target; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 LONDON: P(harmful by R11 marginal) vs stop_vs_target; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 NY: P(harmful by R11 marginal) vs stop_vs_target; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 POOLED: P(harmful by R11 marginal) vs stop_vs_target; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 ASIA: P(harmful by R11 marginal) vs stop_vs_target; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 LONDON: P(harmful by R11 marginal) vs stop_vs_target; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 NY: P(harmful by R11 marginal) vs stop_vs_target; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 POOLED: P(harmful by R11 marginal) vs stop_vs_rest; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 ASIA: P(harmful by R11 marginal) vs stop_vs_rest; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 LONDON: P(harmful by R11 marginal) vs stop_vs_rest; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 NY: P(harmful by R11 marginal) vs stop_vs_rest; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 POOLED: P(harmful by R11 marginal) vs stop_vs_rest; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 ASIA: P(harmful by R11 marginal) vs stop_vs_rest; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 LONDON: P(harmful by R11 marginal) vs stop_vs_rest; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 NY: P(harmful by R11 marginal) vs stop_vs_rest; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 POOLED: P(harmful by R11 marginal) vs stop_vs_rest; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 ASIA: P(harmful by R11 marginal) vs stop_vs_rest; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 LONDON: P(harmful by R11 marginal) vs stop_vs_rest; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X23-counterfactual-skip -1 NY: P(harmful by R11 marginal) vs stop_vs_rest; counterfactual label m_i<0 (45% harmful, corr with net 0.34); holdout AUC ~0.5; oracle ceilings gate m<0 +$120796/wk vs gate net<0 +$125104/wk (info)
- X22-trade-level-stop-gap -1 POOLED: GEO-only G label stop_vs_target; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap -1 ASIA: GEO-only G label stop_vs_target; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap -1 LONDON: GEO-only G label stop_vs_target; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap -1 NY: GEO-only G label stop_vs_target; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap -1 POOLED: GEO-only G label stop_vs_target; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap -1 ASIA: GEO-only G label stop_vs_target; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap -1 LONDON: GEO-only G label stop_vs_target; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap -1 NY: GEO-only G label stop_vs_target; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap -1 POOLED: GEO-only G label stop_vs_target; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap -1 ASIA: GEO-only G label stop_vs_target; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap -1 LONDON: GEO-only G label stop_vs_target; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap -1 NY: GEO-only G label stop_vs_target; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap+base -1 POOLED: GEO+R0 G matrix label stop_vs_rest; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap+base -1 ASIA: GEO+R0 G matrix label stop_vs_rest; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap+base -1 LONDON: GEO+R0 G matrix label stop_vs_rest; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap+base -1 NY: GEO+R0 G matrix label stop_vs_rest; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap+base -1 POOLED: GEO+R0 G matrix label stop_vs_rest; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap+base -1 ASIA: GEO+R0 G matrix label stop_vs_rest; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap+base -1 LONDON: GEO+R0 G matrix label stop_vs_rest; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap+base -1 NY: GEO+R0 G matrix label stop_vs_rest; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap+base -1 POOLED: GEO+R0 G matrix label stop_vs_rest; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap+base -1 ASIA: GEO+R0 G matrix label stop_vs_rest; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap+base -1 LONDON: GEO+R0 G matrix label stop_vs_rest; geometry features carry no stop-vs-target information (holdout ~0.5); dead
- X22-trade-level-stop-gap+base -1 NY: GEO+R0 G matrix label stop_vs_rest; geometry features carry no stop-vs-target information (holdout ~0.5); dead
