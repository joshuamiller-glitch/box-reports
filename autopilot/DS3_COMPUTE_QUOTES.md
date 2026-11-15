# DS3_COMPUTE_QUOTES (ALPHA part C, quote only, no purchase, no signup; the user decides)

**VERDICT: this box is a Latitude.sh bare-metal f4.metal.medium (AMD EPYC 4564P, 16 cores / 32 threads, 128 GB, $555/month, London). Adding a second identical box is the cheapest +32 threads ($555/month); the full present queue (955 cell-months) is about 35 h on this box and would be about 18 h / 9 h / 4.5 h on 64 / 128 / 256 threads, at roughly $158 / $315 / $631 for a 48 h hourly rental. The exact engine cannot use GPUs; do not buy a GPU for it. Nothing was bought or signed up for.**

## Who hosts this box
hostname f4-metal-medium-lon-1; dmidecode/sysfs: Supermicro AS-3015MR-H10TNR, AMD EPYC 4564P 16C/32T; cloud metadata endpoints (169.254.169.254, AWS/GCP/Azure paths) return 404, so it is not a hyperscaler VM. The name matches Latitude.sh's plan f4.metal.medium, whose public pricing page lists AMD 4564P, 16 cores @ 4.5 GHz, 128 GB, $0.76/h, $555/month (hostname inference; the provider itself is not stated on the box, so say plainly: very likely Latitude.sh). Memory: 187 GB reported by free (the plan page says 128 GB, so the box may be a bigger-RAM variant), 17 GB free, 79 GB cache.

## Unit used
"Cores" in the order = hardware threads (the box is called 32 cores = 32 threads = 16 physical). Sizes below are 64 / 128 / 256 threads (AWS vCPU = thread). Memory need: 1.2-2.2 GB RSS per worker, ~4 GB peaks, so plan 2.5-3 GB per worker plus the page cache: >= about 2 GB per thread is the floor; below that workers must be capped. Month = 730 h.

## Quotes (public pages, fetched today)
| size | Latitude.sh (current provider) | Hetzner dedicated (AX line, EUR ex VAT) | AWS on-demand / 1-yr reserved (c7a, us-east-1, Linux) |
|---|---|---|---|
| ~64 threads | 2 x f4.metal.medium (32T, 256 GB total) = $1,110/mo ($1.52/h); or 1 x rs4.metal.large (32c/64T, 768 GB) $2,351/mo ($3.22/h) | 2 x AX102 (16C/32T, 128 GB) = EUR 318-518/mo + EUR 258 setup | c7a.16xlarge (64 vCPU, 128 GB): $3.284/h = $2,397/mo; 1-yr RI $2.173/h = $1,586/mo |
| ~128 threads | 4 x f4.metal.medium = $2,220/mo (128T, 512 GB); or 1 x c4.metal.large (AMD 9655P 96c/192T, 384 GB) $2,920/mo ($4.00/h); or rs4.metal.xlarge (64c/128T, 1.5 TB) $3,971/mo | 1 x AX162 (EPYC 9454P 48C/96T) + 1 x AX102 (=128T) = EUR 478-873/mo + EUR 433 setup; AX162 alone EUR 319 (128 GB) to 614 (512 GB) | 2 x c7a.16xlarge (128 vCPU, 256 GB) $6.57/h = $4,795/mo; 1-yr RI $4.35/h = $3,172/mo |
| ~256 threads | 8 x f4.metal.medium = $4,440/mo (256T, 1 TB); or 2 x c4.metal.large (384T, 768 GB) $5,840/mo ($8.00/h) | 3 x AX162 (288T) = EUR 957-1,842/mo + EUR 912 setup; RAM tier matters (128 GB tier = 1.3 GB/thread, too small) | c7a.48xlarge (192 vCPU, 384 GB) $9.853/h + c7a.16xlarge $3.284/h = $13.14/h = $9,593/mo; 1-yr RI $6,344/mo; spot c7a.48xl $2.457/h (about 75 pct off, can be reclaimed) |
Notes: Latitude monthly = listed monthly price; hourly billing exists, so a burst is cheap (48 h on 1 x c4.metal.large = $192; on 2 x c4 = $384). Hetzner prices are ranges because RAM tiers are priced inside the range and I could not map RAM to price with certainty; setup fees apply. AWS has no local-NVMe on c7a (EBS only), which slows cache-heavy workloads; add EBS cost (not quoted). Hetzner EX/RX/GEX lines not shown on the page I could read.

## Hours cut from the present queue (arithmetic)
Queue now = 955 cell-month lines in /mnt/l2/l2vast/*/pending.txt (362 CH, 96 CONFL, 95 EXPAND_C, 94 NEARTARGET, 53 LONDONRANGE, 45 TRENDEVENT, 42 DIAL9, 29 DIAL10, 28 EXPAND_B, rest < 25 each). Each line = one set x one month = one cell-month. Measured throughput ~0.45 cell-months/min at ~30 workers (box load 47 on 32 threads, saturated). So now: 955 / 0.45 = 2,122 min = 35.4 h.
| threads | speed-up (linear in workers) | queue hours | hours cut | note |
|---|---|---|---|---|
| 32 (now) | 1x | 35.4 | 0 | |
| 64 | 2x | 17.7 | 17.7 | |
| 128 | 4x | 8.8 | 26.5 | |
| 256 | 8x | 4.4 | 31.0 | |
Caveats: linear scaling assumes memory per worker holds and the month cache read (223 GB, NVMe) is not the bottleneck; on 256 threads the cache must be local NVMe or in page cache (223 GB fits in 768 GB-RAM machines). Each tag is also limited by dependency stages (admission/priority, single-writer files, the per-set sequential months), so the realised speed-up is likely 70-90 pct of linear: add 10-30 pct to the hours. The queue regrows as hypotheses are registered, so the benefit is throughput (more survivors tested per day), not a fixed saving. Also the box itself is 93 pct full on /mnt/l2 (271 GB free of 3.5 TB), unrelated to compute but a second machine avoids it.

## GPU
- Exact engine (CPU numpy/numba book-walk): no. It is a sequential event-by-event walk with data-dependent branching per second; a GPU gives little without a rewrite, and a rewrite would break identity with the verified engine. Throughput scales with CPU workers.
- Forecast training: ridge and tree GBM on a few hundred thousand rows are fast on CPU (minutes); GPU helps only a neural net (LSTM/transformer/MLP) or very large GBM. Not needed for the current feature tables.
- If wanted anyway: AWS g6.xlarge (1 x NVIDIA L4 24 GB, 4 vCPU, 16 GB) $0.805/h ($588/mo), spot $0.569/h, 1-yr RI $0.524/h, 3-yr $0.369/h. Latitude.sh g3.h100.small (1 x H100 80 GB) $1.68/h, $1,230/mo (CPU/RAM of that plan not shown). A10/A100 prices not quoted (not on the pages fetched).

## Data to copy and transfer time
du -sh: /mnt/l2/l2vast/_th_tp/cache 223 GB (shared month cache); ds3_all_ea 9.6 GB (sealed manifests, must be read-only and sha-checked, 759f2258daac9d28); uwbooks 13 GB (NQ/ES/RTY/YM 1m, books); plus engine sets/ code (small, < 1 GB) and the DECISIONS/PRIORITY files. Needed total about 250 GB. I assumed the exact engine reads the cache and price stores only, not the 3.2 TB raw L2; confirm with W-D10/W-EV before moving. Transfer time = 250 GB x 8 / link: 1 Gbps at line rate 33 min (realistically 500 Mbps: 67 min); 10 Gbps about 4-7 min if the source can push it (this box's NIC speed not measured). Add rsync checksum pass (~10 min). Raw L2 3.2 TB would be 7-14 h at 1 Gbps and is not needed.

## Risks / not verified
Latitude plan stock/location (page shows only location counts), Hetzner RAM-to-price mapping, AWS EBS and transfer charges, tax/VAT; no vendor was contacted. Fidelity: the second machine must reproduce the identity proof (JN05W2 202610 = 598 trades, net 25,943.82) before any result is used.
