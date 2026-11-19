# DISK TREES INVENTORY (W-GRIDOPS 19:05Z, inventory only: nothing moved, nothing deleted; decision due at box-1 /mnt/l2 < 150 GB free or root < 30 GB)

Box 1 /mnt/l2: 3.5 TB, 290 GB free (92%%), fill 0.8 GB/h; root fs 439 GB, 59 GB free, fill 0.33 GB/h.

| tree under /mnt/l2/l2vast | size | code files mentioning it | live processes holding/naming it now | newest top-level entry age (days) |
|---|---|---|---|---|
| raw | 873G | 57 | 1 | 4.6 |
| _th_state | 242G | 272 | 3 | 1.9 |
| _th_tp | 224G | 36 | 7 | 0.0 |
| tables | 187G | 0 | 0 | 13.6 |
| ds3_v2tree | 128G | 0 | 0 | 12.9 |
| _replica2 | 86G | 1 | 0 | 12.0 |
| _bars | 76G | 84 | 5 | 1.6 |
| _major_sw | 61G | 26 | 3 | 0.0 |
| ds3_redo | 45G | 0 | 0 | 18.1 |
| _hist_replica | 43G | 37 | 2 | 0.0 |
| ds3 | 43G | 70 | 0 | 13.9 |
| _confl | 43G | 252 | 0 | 1.8 |
| _mbo_book | 41G | 7 | 0 | 11.1 |
| ds3_thp | 38G | 1 | 0 | 18.1 |
| _th_redo_replica | 28G | 44 | 0 | 11.2 |
| _th_exh | 27G | 97 | 0 | 9.8 |
| ds3_zones3_new | 26G | 1 | 2 | 14.8 |
| ds3_redo_d8 | 26G | 0 | 0 | 17.9 |
| ds3_l2h | 24G | 0 | 0 | 20.9 |
| _grid | 20G | 85 | 6 | 0.0 |
| _reread | 19G | 7 | 2 | 1.8 |
| _th_sz | 18G | 579 | 7 | 0.0 |
| shuf | 18G | 0 | 0 | 30.6 |

Root fs (outputs/l2vast/ds3 239 GB = old research tree; autopilot 43 GB; outputs/b10 15 GB; /tmp/claude-1000 18 GB): see MORNING.md 19:03Z.

Reading: "live processes" = any running process on box 1 with an open file or command line under the tree at 19:05Z; trees with 0 code files and 0 live processes and old newest-entry age are the cold-archive candidates (copy to the 28 TB disks of the compute servers, md5-checked, delete only after Josh says so).
