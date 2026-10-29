# DS3_DIPENTRY_D6LIVE - one page: D6-LIVE named cell (part 1) and the joint rule cell (part 4)
Source: DS3_DIPENTRY.md sections 1 and 4. Proxies for gates; per-10-s tick; measured fills; stack Delta $/wk vs market entry, k$ (MDE). 2026 alone is ~5 weeks.
| cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| D6L | -61.1 (142.2) | -57.1 (95.4) | -35.9 (101.0) | -30.3 (58.6) | -22.2 (52.9) |
| D6L_dip5 | -29.7 (127.0) | -38.3 (86.6) | -21.8 (86.9) | -31.6 (51.5) | -12.3 (45.2) |
| D6L_2of8 | -32.0 (115.5) | -36.5 (85.8) | -20.3 (88.3) | -22.3 (54.3) | -14.7 (46.4) |
| ENGINE D6-LIVE entry alone | 64.1 (121.8) | -13.0 (58.2) | -8.5 (56.2) | -29.9 (32.9) | -16.0 (35.8) |
| ENGINE profit rule alone (base entries) | 28.1 (108.7) | -16.3 (38.5) | -16.5 (37.6) | -9.5 (22.5) | -1.0 (23.9) |
| ENGINE loss rule 3x alone | -2.3 (91.6) | -33.3 (42.4) | -28.4 (38.9) | -35.1 (28.6) | 0.7 (33.1) |
| ENGINE loss rule 10x alone | -2.3 (91.7) | -32.3 (41.8) | -27.7 (38.3) | -34.2 (28.6) | 0.9 (32.9) |
| ENGINE loss rule 20x alone | -3.3 (92.3) | -32.1 (41.5) | -27.2 (37.6) | -35.1 (28.6) | 1.0 (32.8) |
| ENGINE JOINT entry+profit+loss 3x | 40.5 (122.6) | -28.0 (58.9) | -21.8 (62.0) | -40.9 (37.7) | -10.7 (38.5) |
| ENGINE JOINT entry+profit+loss 10x | 40.4 (122.6) | -28.2 (59.0) | -22.0 (62.1) | -40.9 (37.7) | -10.4 (38.5) |
| ENGINE JOINT entry+profit+loss 20x | 39.7 (122.6) | -28.7 (59.4) | -22.8 (62.3) | -38.6 (36.8) | -8.8 (38.5) |

D6-LIVE fills 69% of HOLD signals, P(target | fill, target from fill) 0.432 (the same trades under the market entry reach the library target 0.371); it is negative in every window: skipping the 31% of signals that never dip 10 pts (mostly winners) costs more than the 10-pt better price earns. Verdict DEAD; joint profit+loss rules do not rescue it on the lock engine (stack as is HOLD SD 162.5, maxDD 696.2; joint 10x: SD 98.5, maxDD 763.0, Delta mean HOLD -22.0).