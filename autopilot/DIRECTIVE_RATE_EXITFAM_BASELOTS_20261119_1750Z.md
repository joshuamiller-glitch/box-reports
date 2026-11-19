# ORDER 20261119_1750Z - rate dip, HEALTH probes, remaining exit families, one date, base-lots definition

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

1. RATE. HEALTH's 30-min fleet rate fell from 4,860 (16:15Z) to 3,592 (17:35Z) with fast share 97-100%; Singapore shows 80-82 engine jobs against a cap of 102. Say why (idle slots, heavier jobs in the 30% follow-up stream, result pull-back lag, the null-file move to Dallas, calibration / stage-A workers taking CPU) with per-host slots, CPU per engine process and set-months per hour. Fix so every host sits at its cap. The W-SHORT stage-A and null-move jobs carry a -5% engine-rate guard: confirm it is measuring against the right baseline and cut them back if they are the cause.

2. HEALTH PROBES. The Dallas row has been "?" since 15:05Z and Singapore was "?" at 17:25Z. A blank row hides real trouble. Make the probe robust (retry, last good value with its age) so each row always shows numbers.

3. EXIT FAMILIES. Josh's rule: nothing enters D8 without the non-fixed exit run. Built and identity-passed: chandelier trail, N adverse bars, latch, clock (+ per-entry vol stop / R target / time exit). NOT built: staged (partial off), swing / line trails, stop-and-reverse, opposite-signal exit, order-flow exits. There has been no build line for these since the morning. Post for each: status, who builds it, date it passes identity. The exit screen already picks a staged exit for at least one Asia cell, so "engine pending" blocks a verdict. These builds need a builder, not engine slots: run them now.

4. ONE DATE. Post a single line: first looks done (Asia, NY AM), other-book REPLACE rows done, follow-ups of strict passers done (controls, layers, exit run incl. the unbuilt families), combination stage done = stage 1 complete. Use today's measured rates and say which part is the long pole.

5. BASE LOTS. Josh asked what "base lots" means on the tables. State precisely on D8_SPEC_STATUS.md and in the LEAD NOTE: the lot sizes per live book and session that the engine baseline (JL3) runs with, the lots a new book runs with in REPLACE / ADD sets (1 lot?), how that compares to his live panel (earlier note said a "x1.75 live-lot view"), and that sizing of the final combination is a separate last step.

One LEAD NOTE answering 1-5.
