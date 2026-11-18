# 1306Z — NEVER IDLE AGAIN: wake yourself when an order arrives (research ops only)

From: Josh's chat assistant (relay). Research orders only; nothing here touches the execution server, a live chart, credentials or spend.

WHAT HAPPENED: you finished a turn at 05:35Z and sat at the prompt until Josh typed at 13:04Z. Seven and a half hours: grid 0 jobs/h (about 82,000 pass-1 jobs left), near-target engine 0 set-months/h (214 total), server 2 at about 42% busy for 84 readings. Orders 0602Z, 0616Z and 0633Z were auto-acked by inbox_watch.sh but nobody read them, because an auto-ack does not start a turn for you.

DO THESE IN ORDER:

1. FIRST, unblock the machines (you are already on it): find what the grid loop is blocked on (the 05:27-05:35Z non-blocking publisher with 8 background scorers is my suspect; workers are "waiting on pipes"), fix or revert it, and get BOTH machines to 90%+ busy. Log the cause in one line in MORNING.md as a real lead note.

2. THEN make this impossible to repeat. Build a small watchdog on box 1 (cron or a nohup loop, your choice) that types into your own tmux pane when you are needed:
   - trigger A: a new file appears in ~/inbox that is newer than your last real lead note;
   - trigger B: CORES.md shows either machine below 85% busy for 3 readings in a row with jobs pending;
   - trigger C: no real lead note in MORNING.md for 40 minutes.
   On any trigger: `tmux send-keys -t b5 "WATCHDOG: read ~/inbox, check CORES.md, act on the newest orders" Enter`, at most once every 10 minutes, and write one line to MORNING.md ("WATCHDOG fired: A/B/C"). Test it once and log that the test worked. It must only send keys to tmux session b5 on this box; nothing else.

3. THEN the work that was waiting, in this order (all already in ~/inbox):
   a. 0400Z near-target: K7 lock rows on older windows + the 30 controls, half-off rows, persist-fix rows (reserved engine slots);
   b. 0602Z level cells positive every year: deep test, P&F look-ahead check, engine sets for the best six NY AM level cells;
   c. 0424Z exit families: first table on the cells that show life;
   d. pass-2 top cells + nulls (45 jobs), pass-1 level modules (3,360), then the rest of pass 1;
   e. W-ORB identity; MORNING_SUMMARY.md (new time: 15:00Z).

4. Reply in MORNING.md with: the cause, the fix, watchdog test result, and ETA for 3a and 3b.

Do NOT run /restart for the Claude Code update until both machines are full and the watchdog is tested.
