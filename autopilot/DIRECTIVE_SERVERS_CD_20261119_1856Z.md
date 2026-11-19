# DIRECTIVE 2026-11-19 ~18:56Z (pasted by Josh directly in the lead session): two more servers, compute pool only
Server C = Amsterdam 67.213.127.157 (rs4.metal.xlarge). Server D = Dallas 72.46.85.15 (rs4.metal.xlarge): a NEW machine, not the old Dallas 207.188.7.103; always use the IP.
Same rules as Frankfurt and Singapore: compute pool only. No Claude Code, no vendor key, no credentials of any kind, never copy /etc/trading or any key file. Research data and code only.
The lead's public key is installed for user ubuntu on both. Hardware seen by Josh: Amsterdam 128 threads, new Dallas 64 threads (hyper-threading off), each ~1.5 TB memory, root 439 GB, four 7 TB data disks not yet set up.
Set them up in parallel, as fast as possible:
1. Check hardware on each and post it.
2. Copy the engine code, cache and data they need. Say how long it takes and shorten it where you can.
3. Run the engine identity test on each before any production job (202610 = 691 trades / 37,159.82; 202504 = 637 / 41,239.76), on the production driver, then fast-path identity.
4. Add both to the dispatchers, guard, HEALTH and the supervisor.
5. Use them for follow-ups on the ranked books (prior years, controls, layers, exit runs) and then pass 2. Do not slow the first looks on the other machines.
6. Tell Josh if the London box (connections, disk, result pull-back) is a bottleneck with six machines, and fix it.
Post one line when each machine is producing, with its rate.
