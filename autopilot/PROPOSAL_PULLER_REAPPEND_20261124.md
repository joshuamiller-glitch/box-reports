# PROPOSAL (not applied): re-append a row when the puller removes a failed lease
W-GRIDOPS 2026-11-24 06:20Z (LEAD ruling: diff proposal + toy-queue test plan, applied only in a quiet window the lead picks). Research queue plumbing only: no engine edit, nothing deleted.

## The hole (found 06:00Z on the XF carry rows)
1. `sr_mover.py` keeps a row in `_split/pending_sr_fit.txt` only while it is NOT started: `rows = [l for l in cur + new if not started(*l.split())]` (line 29): the moment a lease file exists, the row is pruned from the source. The stack head (`meter_shares.py`) also drops started rows from its head file.
2. `th_s3/s3_pull.py` EXIT branch (line ~56-62): a worker that exits without DONE gets its attempt counter bumped and, up to 3 times, `os.remove(f)` (the lease is deleted so the dispatcher can retry the row). But the row is no longer in any queue file (step 1), so the retry never happens. After the 4th failure the lease stays `failed`.
3. Result: a TL3_SR_ row that fails once at the worker vanishes from every queue; `lostrow_audit.py` only covers owners whose state files it knows (the xsess carry plan was not one), so it reported 0 lost.

## Proposed change (3 lines in `th_s3/s3_pull.py`, EXIT branch)
Replace
```python
            if n > (12 if pushed else 3) + 0 and not pushed: v['state'] = 'failed'; json.dump(v, open(f, 'w')); log('GAVE UP %s %s' % (s, m))
            else: os.remove(f)
```
with
```python
            if n > (12 if pushed else 3) + 0 and not pushed: v['state'] = 'failed'; json.dump(v, open(f, 'w')); log('GAVE UP %s %s' % (s, m))
            else:
                os.remove(f)
                if s.startswith('TL3_SR_'): reappend_sr(s, m)      # the retry only works if the row is queued again
```
and add next to `drop_line`:
```python
def reappend_sr(s, m):
    # idempotent: append '<set> <month>' to the stack-fit source unless the row is already there or already landed
    try:
        import queuelock; Q = '/mnt/l2/l2vast/_split/pending_sr_fit.txt'
        if os.path.exists(EX + 'runs_rf/%s/%s/DONE' % (s, m)): return
        with queuelock.Locks(queuelock.lock_paths(Q)):
            cur = open(Q).read().split('\n')
            if any(l.split() == [s, m] for l in cur): return
            open(Q + '.s2tmp', 'w').write('\n'.join([l for l in cur if l.strip()] + ['%s %s' % (s, m)]) + '\n'); os.replace(Q + '.s2tmp', Q)
        log('REAPPENDED %s %s' % (s, m))
    except Exception as e: log('reappend fail %s %s %r' % (s, m, e))
```
(`EX` is the puller's exact-engine root; names as in the file.) The GAVE UP branch is unchanged: a row that fails 4 times stays a visible `failed` lease for the owner (no infinite loop).

## Why it is safe
- Append-only and idempotent (the `any(...)` check, DONE check); same lock helper the pullers already use.
- Only `TL3_SR_` rows (the sr_fit route); other families keep their current routing.
- Cannot loop: the existing attempt counter still stops at 4.
- One residual race: the row is re-appended before the dispatcher re-launches it; `sr_mover` prunes it again only once a new lease exists (correct).

## Toy-queue test plan (no production files)
1. Copy `s3_pull.py` + `queuelock.py` to a scratch dir; point `LD`, `EX`, `D` and the sr_fit path at a scratch tree (`/tmp/toy/leases`, `/tmp/toy/runs_rf`, `/tmp/toy/_split/pending_sr_fit.txt`).
2. Seed a lease `TL3_SR_TOY_a_2026XX.json` in state `launched` with a fake `.exit` result 'exit 0 without DONE' (stub the ssh call to return the fixture).
3. Run one `once()` pass: expect (a) lease file removed, (b) the toy `pending_sr_fit.txt` contains exactly one `TL3_SR_TOY_a 2026XX` line, (c) log has `REAPPENDED`.
4. Run it again with the same fixture: expect still exactly ONE line (idempotent); then pre-create `runs_rf/TL3_SR_TOY_a/2026XX/DONE`: expect NO append.
5. Attempt counter: repeat failures 1-3 re-append (lease removed each time), the 4th sets `failed` and does NOT append.
6. Non-SR row (`TL3_ALN_TOY`): expect no append (unchanged behaviour).
7. Concurrency: run two `reappend_sr` calls in parallel on the same row: expect one line.
Apply window: when the lead picks a quiet moment (restart of the 4 pull loops by explicit pid, backup `s3_pull.py.bak_*`).

## Until then
External idempotent audit loop (this ruling): `sr_plan_audit.py`, every 15 min under nice: appends only rows missing against an owner's PLAN FILE (today the xsess carry plans); sibling-mode inferences are written to `<tmp>` for the owners to confirm (never appended on inference alone).
