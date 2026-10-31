# FILLS_CSV_SCHEMA - fills.csv supplied after each session (SH-2)

One row per executed fill slice (or per order event, see below). No account, login, token, key or free-text columns: the joiner keeps only the columns below, drops any column named like account/acct/login/passw/token/secret/key/user (warns with a count, never writes it), and `--strict-cols` refuses the file instead.

| column | type | rule |
|---|---|---|
| trade_id | str | = `signal_id` of signals.csv (`book\|epoch_ms\|side`). Trades never taken have no rows. |
| book | str | D6 tag (K6 P6 U6 H6 S6 W6 M6 A6 O6 ...); must equal the signal's book. |
| side | BUY/SELL or +1/-1 | direction of the FILL itself (+1 BUY, -1 SELL), NOT of the trade. The trade's side comes from signals.csv. Entry-type rows must equal the trade side, exit-type rows the opposite (else the trade is reported as an anomaly and left unscored). |
| qty | int | contracts, positive. Exception: a `stop_join` row with qty 0 = join placed, not filled. Blank allowed only when reject=1. |
| price | float | fill price (blank allowed on reject=1 and qty-0 join rows). |
| time | int | epoch ms UTC of the fill (join/reject rows: time of the order event). Seconds are refused. |
| order_type | closed vocabulary | `entry_market, entry_limit, add, target, stop_native, stop_join, stop_fallback, flatten, cut, other` (case/space/hyphen tolerant; unknown -> `other`, counted). `add` = the 30% leg of a 70/30 split. `stop_native` = stop-market; `stop_join` = the B-arm join limit; `stop_fallback` = the market order after a join timed out/was rejected. `other`: classified by side only (same side as trade = entry, opposite = exit). |
| fee_usd | float, optional | TOTAL fee in USD for that row. If absent: 0.242 pts per contract per fill. If present: fee_usd/20 pts for the row. |
| reject | 0/1, optional | 1 = the order was rejected (own outcome; no P&L, no fee; `stop_join` + reject=1 sets join_rejected). |
| synthetic | 0/1, optional | test only; real signals refuse synthetic fills and vice versa. |

## Join rules (fills_join.py)
- `live_pts_ppl` = (side * (exit VWAP - entry VWAP) * filled qty - fees in pts) / `lots_live` (planned lots). Entry VWAP spans entry_market/entry_limit/add; exit VWAP spans all exit slices. Under-filled lots earn proportionally (per PLANNED lot).
- Complete round trip = exit qty == entry qty > 0. Less exit than entry -> open (blank, counted). More exit than entry, wrong-direction fills, book mismatch, lots_live 0 -> anomaly (blank, counted).
- `live_exit_type`: class of the exit order types with the most quantity (ties: stop > cut > flat > target > other); stop_native/join/fallback -> `stop`. `live_close_ts` = last exit fill time.
- Reported (never silent): unmatched fills (trade_id not in signals), fills on taken=0 signals, taken=1 signals with no fills, open trades, anomalies, exact-duplicate rows dropped, rejected rows.
- Floor: real signals before 2026-11-01 23:00Z (epoch ms 1793574000000) or real fills before it are refused; synthetic and real never pair. Re-running on the output file gives byte-identical output (live_* columns are recomputed from the fills each run; the joiner owns them).
- stops.csv (from stop-type rows): `stop_level` = signal_px - side*stop_d unless the optional D6 stops file (`--d6-stops`: signal_id, ts_trigger_ms, stop_level, run_past_stop_pts) supplies it; arm by trade date of the ENTRY (ET clock +6h; ordinal parity: odd -> A native, even -> B join; Monday 2026-11-02 = B); `order_type_actual` native/join/mixed/fallback_only (anything but the arm's type = deviation=1); `slip_pts` = side*(stop_level - fill VWAP) (+ = adverse); `ts_trigger_ms` = first stop-type row unless D6 supplies it; join_filled/join_rejected/join_placed_ms/fallback_* from the stop_join and stop_fallback rows (blank when no join was used); `run_past_stop_pts` only from the D6 file. Extra columns for the tables: trade_date, stop_dist, deviation, stop_level_src, trigger_src.
- Constants (one place, top of fills_join.py): FEE_PTS_PER_LOT_FILL 0.242, DOLLAR_PT 20, ARM_PARITY, STOP_BUCKETS.

Run: `fills_join.py --signals signals.csv --fills fills.csv --out signals.csv --stops-out stops.csv [--d6-stops d6.csv]`, then `stop_ab_tables.py --stops stops.csv --outdir DIR`, then `shadow_score.py --signals signals.csv --stops stops.csv ...`.
