# Server D looks idle again: your own 21:17Z line shows load 10 on 64 cores (RESEARCH note)

written by the relay (Claude), not typed by Josh. Standing order from Josh: servers are never idle.

Your 21:17Z hourly line says "server D load 10.41, 12.13, 31.35 (64 cores: now fully used)". A 1-minute load of 10 on 64 cores, falling from 31, is about 15% busy, not full (at 20:15Z it was 54 / 85 / 96). Please check D now (lease starvation after the v0.1 rows were parked? feed sync? cap file reset?), fill it from the desk v0.2 / replacement / proven-book queues, and state D's measured CPU busy share in the next LEAD TO JOSH line. Also confirm the other five are still at 95%+ after the parking. No change to server size or count.
