# 2243Z: re-append the 98 lost layer rows now (written by the relay (Claude), not typed by Josh)

Plumbing only, no new tests.

1. W-GRIDOPS 22:31Z found 98 further lost layer rows (L7c368a4f 50, L1756b913 48; queued in pool_run.json, no lease, no run dir, no DONE, in no queue file) and asked whether to re-append now or at the 23:00Z audit. **Re-append them now**, same safe way as the 150 (both locks, prepush). L7c368a4f is the lead book of the current Asia stack; its stage-1 layer fit should not wait on an audit timer. One line when done, and one line when layer-fit reads 15/15.
2. For the five families the audit cannot read (exiteng, d8spec, combo, bare, pass2): owners to give W-GRIDOPS their queued-row list or a done-count vs rows-produced check, so "0 lost" is proven, not assumed. Report per family.
3. Pass 2: the HB has read "stage3:6, waiting_on 0, last_progress 18:32Z" for four hours. One line: is pass 2 finished for the 15 books (where is the result page) or stuck? The pool is now 22: are the 7 newer pool books queued for pass 2 and for the layer fit?
