# SPLIT_EDIT_PROPOSAL (W-NYENG, order 1430Z): Asia 59% / NY AM 41% first-look share on the existing dispatchers. NOT APPLIED; the lead applies after OK.
Tested 14:35Z on copies (<tmp>): code/th_nyeng/ny_mix.py 0.41 --test DIR.
## Tests
- Multiset: mix == Asia pending (61,349 after drops) + NY AM pending (94,749) - excluded - DONE - exact duplicates, nothing lost or duplicated, order inside each source unchanged (checked): PASS (156,580 lines).
- Excluded from the mix, staying first in QUEUES.txt ahead of it: _asi/first.txt (W-ASIA passer controls) and _nye/pending_l.txt (layer fits); the NY AM candidates' own follow-up lines (482 lines of the PICK cells in D8_CANDIDATES) are put FIRST in the mix file, unmixed (moved to the front of the NY part).
- Concurrency: each source is read while holding its own builder lock (ql_ASI/.pend_lock, ql_NYR/.pend_lock; the same locks the builders use); a stress test (appender adding 5 lines per source 300 times under the lock while ny_mix ran 3 times): 0 malformed lines, multiset PASS each run. The sources are never written.
## Share on the existing dispatchers (simulation, 1 hour, steady state; slot frees -> takes the first unstarted runnable line in file order, as s2_dispatch / s3_dispatch do; service time exponential, mean 560 s = measured lease->DONE of both families)
| ladder slots | BEFORE (Asia file ahead of NY AM file) | AFTER (mix, blocks of 8 NY AM + 12 Asia) |
|---|---|---|
| 40 | Asia 243 / NY AM 0 (NY AM 0%) | Asia 129 / NY AM 92 (NY AM 42%) |
| 100 | Asia 567 / NY AM 0 | Asia 377 / NY AM 240 (NY AM 39%) |
| 200 | Asia 1,178 / NY AM 0 | Asia 715 / NY AM 477 (NY AM 40%) |
| 100, 30% of Asia lines skipped as not runnable on the host | - | Asia 312 / NY AM 296 (NY AM 49%): skipped lines shift share TOWARDS NY AM |
So the interleave gives ~40% NY AM (target 41%), not 100/0: slot completions consume the file in order, so the completed-line share equals the file share (block of 20 = 8 NY AM + 12 Asia); bursts inside a block do not matter over more than ~20 lines. Measured today: in the last hour the A/B/Dallas dispatchers finished 3,770 set-months of which 3,658 were W-LAYERS fit sets (TL3_NYL_, ahead in the queue), ASIA 112, NY AM ladder 0 (NY AM ladder lines come after Asia in QUEUES.txt and after the layer work): the split only governs what is left after layers / candidates, which is intended.
## Exact edit (QUEUES.txt lines 9 and 12 today; the lead applies)
1. cp /mnt/l2/l2vast/_s2/QUEUES.txt /mnt/l2/l2vast/_s2/QUEUES.txt.bak_split_ROLLBACK
2. python3 - <<'PY'
   q='/mnt/l2/l2vast/_s2/QUEUES.txt'; L=open(q).read().split('\n')
   i=[k for k,l in enumerate(L) if l.startswith('/mnt/l2/l2vast/_asi/pending.txt')][0]
   L=[l for l in L if not l.startswith('/mnt/l2/l2vast/_nye/pending_r5.txt')]
   L[i]='/mnt/l2/l2vast/_split/pending_mix.txt   # W-NYENG split: Asia ladder 59% / NY AM ladder 41% (sources _asi/pending.txt and _nye/pending_r5.txt, read-only)'
   open(q+'.tmp','w').write('\n'.join(L)); import os; os.replace(q+'.tmp',q)
   PY
3. crontab (box 1): */15 * * * * <repo>/.venv/bin/python3 -I code/th_nyeng/ny_mix.py 0.41 >> <tmp> 2>&1   (run it once by hand BEFORE step 2 so the file exists)
4. PRIORITY.txt (box 1 local fillers, cap not guarantee): NYR quota 16 -> 11 (keep ASI 16): cp PRIORITY.txt PRIORITY.txt.bak_split_ROLLBACK; sed -i 's/^NYR @ 16 @/NYR @ 11 @/' PRIORITY.txt. The box-1 fillers keep reading their own source files (leases prevent double runs).
## ROLLBACK
cp /mnt/l2/l2vast/_s2/QUEUES.txt.bak_split_ROLLBACK /mnt/l2/l2vast/_s2/QUEUES.txt; cp /mnt/l2/l2vast/_th_tp/PRIORITY.txt.bak_split_ROLLBACK /mnt/l2/l2vast/_th_tp/PRIORITY.txt; remove the */15 ny_mix.py cron line. Sources are untouched, so nothing else to restore.
## Caveats
- The mix is rebuilt every 15 min, so lines appended or re-ordered between rebuilds appear with a delay up to 15 min; leases make double starts impossible.
- Each dispatcher round scans the mix file from the top (156k lines, same cost as scanning the two files today).
- Asia re-orders (reorder_pending.py :10/:25/:40/:55) and my order script run under the same locks the mix takes; a mix rebuild waits for them, never reads a half-written file.
