# MIX3_EDIT_PROPOSAL (W-NYENG, order 1534Z item 2): enforce 70% first looks / 30% follow-ups on the remote dispatchers. NOT APPLIED to QUEUES.txt (the lead applies; same procedure as the 59/41 split).
Why: the dispatchers ignore tag quotas and take the first runnable line in QUEUES.txt order; today follow-up files sit AHEAD of the first-look mix (QUEUES lines 4 _exiteng, 5 _asi/first.txt, 6 _nye/pending_l.txt, 8 _layers/pending_rest.txt) so they take ~94% of the slots (measured last 60 min at 15:36Z: started: follow-ups 2,143 layers/prior-years + 981 controls vs NY AM first looks 236, Asia first looks 0; DONE: first looks 6% of all).
## Mix (code/th_nyeng/ny_mix3.py, cron */5 flock, builds /mnt/l2/l2vast/_split/pending_mix3.txt; already running, harmless until QUEUES.txt points at it)
- Streams: FOLLOW-UPS (_asi/first.txt, _layers/first.txt, _nye/pending_l.txt, _layers/pending_rest.txt, _exiteng/pending.txt + the controls / prior-year lines found in _asi/pending.txt and _nye/pending_r5.txt) = 30%; ASIA first looks 41.3% (70% x 59%); NY AM first looks 28.7% (70% x 41%). Weighted round robin (largest deficit), so the shares hold line by line, not only per 20-line block; an empty stream hands its share to the others.
- Inside the 30%: K7 / A7 slot rows first (names with xK7, xA7, _RK7, _RA7), other-slot rows (xP7, xM7, xH7, _RP7, _RM7, _RH7) after (stable).
- NY AM first looks: REPLACE-K7 lines first, other-book a2 rows after.
## Tests (copies in <tmp> then the real sources)
- Multiset: mix == union of the streams after dropping exact duplicates (245) and DONE lines (2,568 on the real run): PASS. Order inside every stream unchanged: PASS. Real run: follow-ups 20,968 (18,967 K7/A7 slot class first), Asia first looks 19,978, NY AM first looks 34,024 -> 74,970 lines. First 2,000 lines: Asia 826 (41%), follow-ups 600 (30%), NY AM 574 (29%): first looks 70%, Asia : NY AM = 59 : 41.
- Locks: sources read under ql_ASI, ql_NYR, ql_NYL builder locks (ms), never written; runtime 1 s.
## Exact edit (the lead applies)
1. cp /mnt/l2/l2vast/_s2/QUEUES.txt /mnt/l2/l2vast/_s2/QUEUES.txt.bak_mix3_ROLLBACK
2. python3 - <<'PY'
   q='/mnt/l2/l2vast/_s2/QUEUES.txt'; L=open(q).read().split('\n')
   drop=('/mnt/l2/l2vast/_exiteng/pending.txt','/mnt/l2/l2vast/_asi/first.txt','/mnt/l2/l2vast/_nye/pending_l.txt','/mnt/l2/l2vast/_split/pending_mix.txt','/mnt/l2/l2vast/_layers/pending_rest.txt')
   i=[k for k,l in enumerate(L) if l.startswith('/mnt/l2/l2vast/_exiteng/pending.txt')][0]
   L=[l for k,l in enumerate(L) if not l.startswith(drop) or k==i]
   L[[k for k,l in enumerate(L) if l.startswith('/mnt/l2/l2vast/_exiteng/pending.txt')][0]]='/mnt/l2/l2vast/_split/pending_mix3.txt   # W-NYENG mix3: 70% first looks (Asia 59 : NY AM 41) / 30% follow-ups, K7/A7 slot rows first inside the 30%'
   open(q+'.tmp','w').write('\n'.join(L)); import os; os.replace(q+'.tmp',q)
   PY
   (_nt/first, _nt/pf, _orb stay ahead of it; _nt2, _nye/pending_f, _fr, _nye/pending, _nye/pending_w, _lon, _nt, _data lines unchanged behind it.)
3. The old */5 ny_mix.py (mix v2) cron becomes unused: remove it after the edit.
4. Box-1 local fillers (ql_driver ASI / NYR / NYL / LAY) keep reading their own source files: a cap on them is by PRIORITY.txt quotas (NYL 36 -> 10, EXE 24 -> 4, ASI 16, NYR 11; the remote hosts are governed by the mix).
## ROLLBACK
cp /mnt/l2/l2vast/_s2/QUEUES.txt.bak_mix3_ROLLBACK /mnt/l2/l2vast/_s2/QUEUES.txt; remove the */5 ny_mix3.py cron line (sources are untouched).
## Caveat
The follow-up share is a CEILING of 30% of the lines the dispatchers pick; if first looks are not runnable on a host (month inputs / deps missing) the remaining slots flow to follow-ups (lines skipped as not runnable are skipped, not waited for).
