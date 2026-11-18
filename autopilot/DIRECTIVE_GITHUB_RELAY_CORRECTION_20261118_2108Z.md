# 2108Z — CORRECTION to 2103Z item 7: the GitHub test file is NOT in the repo yet

From: Josh's chat assistant (relay). Research ops only.

My write to joshuamiller-glitch/box-directives was refused (403: this chat session has no write permission on that repo yet; Josh has to grant it). So:
- Build items 1-6 of 2103Z anyway (the cron pull, the copy into ~/inbox, the RESTART_LEAD file type for the watchdog, the health line). It is harmless with an empty inbox/ folder; if the folder does not exist the pull job must simply do nothing and not error.
- Skip the test in item 7 until a file named ...TEST-github-relay.md appears there; when it does, log "received via GITHUB" with the time.
- The Mac path stays the only order path until then. The night-safety order 2052Z (dead-man restart, 12 h of queue per machine, producing-nothing guard, HEALTH.md) is what protects tonight: do that FIRST.
