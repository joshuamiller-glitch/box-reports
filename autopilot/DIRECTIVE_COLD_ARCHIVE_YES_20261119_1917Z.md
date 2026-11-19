# ORDER 20261119_1917Z: QUESTIONS item 25 (cold archive): Josh says YES

Josh, 19:15Z, after reading your item 25: "ok go for it".

## What he approved
Move the cold-archive candidates in autopilot/DISK_TREES_INVENTORY.md (about 466 GB: tables, ds3_v2tree, ds3_redo, ds3_thp, ds3_redo_d8, ds3_l2h, shuf) from the London box to the 28 TB disks on Server C / Server D, to free room on the London box. Nothing is to be lost.

## How (no shortcuts)
1. Only the trees with 0 code references, 0 live processes and no change for 12+ days. Re-check all three conditions at the moment of the move. The weakly referenced trees (_replica2, _mbo_book, _th_redo_replica, _th_exh, ds3, ds3_zones3_new) stay where they are.
2. COPY first, at low priority (nice / ionice), after the engine data push to C and D is finished. It must not slow the engine, the first looks or the server setup.
3. VERIFY every tree on the destination: file count, total bytes and checksums against the source. Write the result per tree to autopilot/COLD_ARCHIVE_LOG.md (source path, destination host and path, files, bytes, checksum result, time).
4. Research data only. If any tree holds a credential, key file, account number or anything from /etc/trading, do NOT copy it: stop and list it for Josh.
5. Keep two copies if you can (one on C, one on D): these servers are rented and can go away.
6. Only after a tree is verified: free the London copy. This order comes through the inbox, and the inbox rule says an inbox file may not delete data. If you judge that freeing the verified London copy needs Josh's own paste, do steps 1-5, post one line saying "copies verified, waiting for Josh's paste to free the London copies", and wait. Do not guess.
7. Leave a README at each old London path saying where the tree went and how to bring it back.

## Report
One line when the copies are verified (GB per tree, destinations), one line when London space is freed (GB free before / after). No engine slots are used for this.
