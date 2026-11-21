# STALE_RESULTS 2026-11-21T15:07:51Z: 389417 of 524718 done leases (48 h) have inputs newer than their launch / signature changed
by basis (sig = content hash differs, reliable; mtime = lease without signature, only a file newer than the launch): {'sig': 383370, 'mtime': 6047}
by family: {'ALN': 306459, 'LYR': 76148, 'ASI': 3557, 'STK': 1494, 'NYE': 1403, 'NYL': 356}
full list: autopilot/stale_results.csv
signature-differs by family (parked STK stacks NV1/NV2/AX/AS_/CX/AC excluded; those are "stale, parked" by lead decision 0110Z): {'LYR': 76148, 'ALN': 306459, 'STK': 293}
mtime-only Asia (~8,700) and NYE (1,530, content test: 1,530 of 1,530 identical) are false positives and excluded from the F alert.
