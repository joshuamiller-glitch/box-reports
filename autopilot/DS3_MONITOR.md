# DS3_MONITOR - how fast can the user tell the edge is gone? Alarm rules for the live stack and its six books (DIS-Z3M, Z3, 2026-11-05)
Operating-rule measurement; nothing about the engine changes; no PASS claims; nothing live. Prereg l2vast/ds3/prereg/DIS_Z3M_prereg.md sha256 5e0760a100dda3f9d201717f00dc135d86c4e8af7812d035d450975deca98051 (DECISIONS.md, before any number; registered in MORNING.md first after dead_lookup + grep). Code l2vast/ds3/code/dis_z3m/ (z3m_run.py, z3m_ro.py); data l2vast/ds3/out/dis_z3m/ (z3m_grid.csv, z3m_hist.csv, series.pkl). Series: BASE-4 run_v13t_ts2 (Q1-A, live lock) weekly P&L 2023-04..2026-10 (187 weeks): stack and KB, PE, SM, HM, MV, PB. Simulation: 20,000 healthy paths of 156 weeks (stationary block bootstrap of days, mean block 10); degraded paths = 52 healthy weeks, then the weekly mean multiplied by m in {0.5, 0, -0.5} for 104 weeks. Rules are STATE conditions evaluated at each week end; 'detect within k weeks' = the first week after the change with the condition true.

## Plain sentences
1. A year of the live stack's own P&L cannot tell a halved edge from bad luck quickly: at a false-alarm rate of 3-10% per year, the best rule (a CUSUM with threshold 8 weekly SD) detects a halved edge within 26 weeks in 30% of cases (median delay 37 weeks, 56% within 52 weeks), a vanished edge within 26 weeks in 63% (median 21 weeks), and an edge that has turned to minus half in 88% (median 13 weeks); drawdown-from-high ($200k) and time-under-water (26 weeks) rules are 2-3x slower (half edge: median 47 weeks, only 13% within 26 weeks).
2. By the time any of these alarms fires after the edge has vanished, the stack is typically already $154k below its high (CUSUM) to $208k (drawdown rule) and has run 21-34 weeks (median) after the change.
3. On the real 2023-26 record none of the three equal-false-alarm rules (CUSUM 8 SD, drawdown $200k, 26 weeks under water) ever fired, including through the HOLD episode ($122k, peak 2026 W05, trough W08): that drawdown, the deepest observed, would NOT have triggered a drawdown alarm set at $150k-$200k; the CUSUM at 5 SD (38% false alarms per year) fires first in 2023 W35 and is not a usable rule.
4. Per book the same rule thresholds do not transfer: with the CUSUM at 8 SD the healthy false-alarm rate per year is 8.5% for the stack but 12-23% for KB, SM, HM, PB, PE, and 46% for MV (a weak edge), so each book needs its own threshold (a book-level alarm must be calibrated on that book's own mean / SD); drawdown rules scaled to each book's own maxDD are conservative (false alarms 0-1.5% per year, median half-edge delay 56-81 weeks).
5. A rolling-origin choice (rule picked on a bootstrap fitted to 2023-04..2024-12 at equal false-alarm rate) selects the $150k drawdown rule (half-edge median delay 40 weeks), which did not fire in 2025-26.

## 1. False-alarm rates of the grid on healthy stack paths (156 weeks; P(at least one alarm in the first 52 weeks))
| rule | description | P(false alarm in a year) | alarms per year |
|---|---|---|---|
| A1|13|0.0 | trailing 13-week mean t < 0.0 | 59.7% | 1.27 |
| A1|13|-1.0 | trailing 13-week mean t < -1.0 | 14.3% | 0.22 |
| A1|13|-2.0 | trailing 13-week mean t < -2.0 | 1.6% | 0.02 |
| A1|26|0.0 | trailing 26-week mean t < 0.0 | 13.2% | 0.30 |
| A1|26|-1.0 | trailing 26-week mean t < -1.0 | 1.4% | 0.03 |
| A1|26|-2.0 | trailing 26-week mean t < -2.0 | 0.0% | 0.00 |
| A1|52|0.0 | trailing 52-week mean t < 0.0 | 0.3% | 0.02 |
| A1|52|-1.0 | trailing 52-week mean t < -1.0 | 0.0% | 0.00 |
| A1|52|-2.0 | trailing 52-week mean t < -2.0 | 0.0% | 0.00 |
| A2|1.0|None | drawdown from high >= $100k | 49.3% | 0.91 |
| A2|1.5|None | drawdown from high >= $150k | 13.8% | 0.23 |
| A2|2.0|None | drawdown from high >= $200k | 3.5% | 0.06 |
| A3|20|None | under water >= 20 weeks | 10.8% | 0.14 |
| A3|26|None | under water >= 26 weeks | 4.3% | 0.06 |
| A3|39|None | under water >= 39 weeks | 0.6% | 0.01 |
| A4|3.0|None | CUSUM h = 3.0 x weekly SD | 83.2% | 2.07 |
| A4|5.0|None | CUSUM h = 5.0 x weekly SD | 38.3% | 0.88 |
| A4|8.0|None | CUSUM h = 8.0 x weekly SD | 8.5% | 0.24 |
The three rules at 3-10% per year: drawdown $200k (3.5%), time under water 26 weeks (4.3%), CUSUM 8 SD (8.5%); the trailing t-statistic rules fall at 14% and 13% (13 weeks, c = -1; 26 weeks, c = 0) or 1.6% and 1.4% (13 weeks, c = -2; 26 weeks, c = -1).

## 2. Detection at equal false-alarm rate (3-10% per year), stack
Edge halved (m = 0.5), vanished (m = 0), reversed to minus half (m = -0.5) after 52 healthy weeks. Columns: false-alarm rate per year, P(detect within 13 / 26 / 52 weeks of the change), median delay among detected paths (weeks), mean drawdown depth at the alarm, mean cumulative P&L given up vs the healthy mean at the alarm is not shown separately (see the last column = mean cumulative P&L of the degraded path at the alarm, negative = loss).
m = 0.5:
| rule | false alarm / yr | 13 w | 26 w | 52 w | median delay | drawdown at alarm | cumulative P&L at alarm (neg = loss) |
|---|---|---|---|---|---|---|---|
| drawdown from high >= $200k | 3.5% | 5% | 13% | 28% | 47 | $208k | $-153k |
| under water >= 26 weeks | 4.3% | 4% | 13% | 35% | 47 | $127k | $-188k |
| CUSUM h = 8.0 x weekly SD | 8.5% | 14% | 30% | 56% | 37 | $141k | $-186k |
m = 0 (edge vanished):
| rule | false alarm / yr | 13 w | 26 w | 52 w | median delay | drawdown at alarm | cumulative P&L at alarm (neg = loss) |
|---|---|---|---|---|---|---|---|
| drawdown from high >= $200k | 3.5% | 17% | 43% | 74% | 29 | $208k | $34k |
| under water >= 26 weeks | 4.3% | 5% | 27% | 73% | 34 | $193k | $28k |
| CUSUM h = 8.0 x weekly SD | 8.5% | 28% | 63% | 91% | 21 | $154k | $5k |
m = -0.5 (edge reversed):
| rule | false alarm / yr | 13 w | 26 w | 52 w | median delay | drawdown at alarm | cumulative P&L at alarm (neg = loss) |
|---|---|---|---|---|---|---|---|
| drawdown from high >= $200k | 3.5% | 40% | 77% | 97% | 16 | $205k | $131k |
| under water >= 26 weeks | 4.3% | 5% | 45% | 93% | 27 | $282k | $206k |
| CUSUM h = 8.0 x weekly SD | 8.5% | 50% | 88% | 99% | 13 | $168k | $102k |
Trailing t-statistic rules, vanished edge (outside the 3-10% band; a faster rule at a higher false-alarm rate):
| rule | false alarm / yr | 13 w | 26 w | 52 w | median delay |
|---|---|---|---|---|---|
| trailing 13-week mean t < 0.0 | 59.7% | 70% | 93% | 100% | 10 |
| trailing 13-week mean t < -1.0 | 14.3% | 33% | 63% | 89% | 20 |
| trailing 13-week mean t < -2.0 | 1.6% | 9% | 25% | 49% | 40 |
| trailing 26-week mean t < 0.0 | 13.2% | 26% | 67% | 93% | 21 |
| trailing 26-week mean t < -1.0 | 1.4% | 5% | 30% | 62% | 36 |
| trailing 26-week mean t < -2.0 | 0.0% | 1% | 7% | 23% | 53 |
| trailing 52-week mean t < 0.0 | 0.3% | 3% | 14% | 63% | 45 |
| trailing 52-week mean t < -1.0 | 0.0% | 0% | 2% | 26% | 56 |
| trailing 52-week mean t < -2.0 | 0.0% | 0% | 0% | 6% | 67 |
(the 13-week t < 0 rule detects a vanished edge in a median of 10 weeks but false-alarms on 60% of healthy years.)

## 3. Per book (same three rules; drawdown thresholds scaled to the book's own maxDD)
Columns: false-alarm rate per year; P(detect within 26 weeks) / median delay for half edge, vanished edge, reversed edge; first alarm on the actual 2023-26 record.
| rule | series | false alarm / yr | half edge | vanished | reversed | actual record |
|---|---|---|---|---|---|---|
| CUSUM h = 8.0 x weekly SD | STACK | 8.5% | 30% / 37 | 63% / 21 | 88% / 13 | none |
| CUSUM h = 8.0 x weekly SD | KB | 22.9% | 38% / 30 | 50% / 24 | 64% / 19 | week 202637 (1 weeks in alarm) |
| CUSUM h = 8.0 x weekly SD | PE | 11.7% | 31% / 36 | 59% / 22 | 83% / 14 | none |
| CUSUM h = 8.0 x weekly SD | SM | 17.6% | 33% / 33 | 51% / 25 | 71% / 17 | week 202426 (1 weeks in alarm) |
| CUSUM h = 8.0 x weekly SD | HM | 12.7% | 31% / 36 | 53% / 24 | 75% / 17 | week 202352 (16 weeks in alarm) |
| CUSUM h = 8.0 x weekly SD | MV | 46.4% | 55% / 13 | 54% / 13 | 53% / 13 | week 202516 (48 weeks in alarm) |
| CUSUM h = 8.0 x weekly SD | PB | 14.9% | 30% / 35 | 44% / 28 | 60% / 21 | none |
| drawdown from high >= $200k | STACK | 3.5% | 13% / 47 | 43% / 29 | 77% / 16 | none |
| drawdown from high >= $200k | KB | 0.2% | 1% / 67 | 2% / 68 | 4% / 62 | none |
| drawdown from high >= $200k | PE | 0.6% | 3% / 57 | 14% / 49 | 39% / 31 | none |
| drawdown from high >= $200k | SM | 0.8% | 2% / 60 | 6% / 58 | 16% / 47 | none |
| drawdown from high >= $200k | HM | 1.1% | 5% / 57 | 16% / 47 | 36% / 33 | none |
| drawdown from high >= $200k | MV | 0.0% | 0% / 81 | 0% / 84 | 0% / 80 | none |
| drawdown from high >= $200k | PB | 1.5% | 4% / 56 | 9% / 53 | 19% / 45 | none |
| under water >= 26 weeks | STACK | 4.3% | 13% / 47 | 27% / 34 | 45% / 27 | none |
| under water >= 26 weeks | KB | 28.4% | 40% / 29 | 48% / 27 | 55% / 25 | week 202343 (30 weeks in alarm) |
| under water >= 26 weeks | PE | 7.5% | 17% / 45 | 30% / 34 | 46% / 27 | none |
| under water >= 26 weeks | SM | 14.3% | 25% / 39 | 35% / 32 | 46% / 27 | none |
| under water >= 26 weeks | HM | 16.0% | 27% / 38 | 38% / 31 | 50% / 27 | week 202342 (33 weeks in alarm) |
| under water >= 26 weeks | MV | 66.8% | 79% / 1 | 79% / 1 | 78% / 1 | week 202347 (83 weeks in alarm) |
| under water >= 26 weeks | PB | 21.7% | 34% / 33 | 42% / 29 | 50% / 27 | none |

## 4. Reading and limits
For a dashboard the usable statement is: with the live stack's own history, an alarm that rarely fires on a healthy stack is also slow: roughly nine to eleven months (median 37-47 weeks) for a halved edge and five to eight months (21-34 weeks) for a vanished edge, and by then the drawdown is already $150k-$210k (1.2-1.7x the HOLD episode). Faster detection needs the signal-level monitor (fills vs engine, rule fire counts, slippage) that DS3_OUTAGE and the forward register can provide rather than P&L alone. Limits: one 3.5-year record bootstrapped; the failure model is a pure mean shift with the same variance (a stop outage or a data bug is a sudden jump that the drawdown rule would catch within the week if it exceeds the threshold, but is not simulated here); the per-book thresholds are not calibrated to a common false-alarm rate (section 3 shows the spread); six books x many rules is a multiplicity problem the false-alarm column does not cover.
