# WATCH_NQ_PDL_SPEC companion note (ZL-2, 2026-11-06; the spec file WATCH_NQ_PDL_SPEC.md is untouched, sha256 8f7faa58137c... stays enforced by the register)
Reason: CHAR-C's bad-print repair (cc_audit v1, REPAIRED_BARS_PATHS.md) changes the plugin's history figures. The definition, thresholds and kill rules of the spec do not change.
## Repaired history (bar-based variant m1.0_t1.0, label days 2023-08 .. 2026-10-16, plugin nq_pdl.py)
| | spec / original bars | repaired bars |
|--|--|--|
| trades | 551 | 553 (9 only in the original run, 11 only in the repaired run; 156 of the 542 common trades change net) |
| mean net per NQ lot | -$8.93 | -$9.90 |
| mean net per MNQ lot | -$1.69 | -$1.79 |
| total at 1 MNQ | -$930.5 | -$987.6 |
| sd of net per MNQ trade | 12.92 | 12.90 |
The kill constant 12.91 (kill (i): n >= 20 and cum <= -2.0 x 12.91 x sqrt(n)) is UNCHANGED (12.92 -> 12.90 rounds to the same constant); the sign and conclusions are unchanged.
## Approximation (state it with the numbers)
The cc_audit rule is defined on 1-minute bars (60-s neighbours). The spec's data are 1-second bars, which were NOT scanned with their own rule. The repaired figures clamp the 1-s bars (o, c into the band; h to at most the band top; l to at least the band bottom) inside each of the 265 NQ minutes flagged by cc_audit v1 on feed instr1m since 2023-08 (1,258 flagged since 2013); in all 265 the 1-s data held prints outside the repaired 1-min band. A native 1-s bad-print rule would be needed for a final history figure; until then the original -$8.93 / -$9.90 pair is the bracket.
## Forward procedure (unchanged rule, same as the other watches)
Each register run applies the flag-only bad-print check to the 1-min feed it can see; for NQ_PDL (1-s forward bars from the weekly top-up) the check is the 1-s analogue: after each new top-up week the NQ 1-min cc_audit rule is run on the same week's 1-min bars (ohlcv-1m top-up, if pulled) and any flagged minute is listed in out/watch/BADPRINTS_NQ_PDL.csv with the trades whose entry, exit or prior-day level it touches. Nothing is repaired or dropped silently; raw files are kept; the Monday review reports each trade touched by a flagged minute both ways (as logged and clamped). The pass/kill decision uses the logged (unrepaired) trades unless the review shows the flagged minute set the prior-day level, an entry, or an exit, in which case both versions are reported and the kill/pass call needs the lead.
Source of the numbers: README_WATCH.md and REPAIRED_BARS_RERUN.md blocks of 2026-11-06 (ZL-2 rerun); spec sha 8f7faa58137c unchanged.
