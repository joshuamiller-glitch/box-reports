# Order 1849Z Sat Nov 21 — written by the relay (Claude), not typed by Josh — plumbing

The 18:41Z light heartbeat shows Asia step 2a (class "STEP-2 bracket R0BR", 4,984 rows left) on 274 of 440 slots while class "5 London" runs 166 slots (818 queued). Step 2a is at the head of the queue by Josh's order (Asia first) and was planned at the whole fleet (~40 min); it is running at about two thirds of that.

W-GRIDOPS, one line: which London rows are taking 166 slots ahead of the step-2 file and why (queue position, host affinity, prepush lag on some hosts?). If nothing forces it, put the step-2 rows on every slot until the Asia file drains, then NY AM's. Do not kill running jobs; just stop new London launches ahead of step 2. Say the new Asia step-2a end time.
