# DS3_SDISC_1_PREHOLD - D3SD1 PREHOLD list (PRE only; written before any HOLD/X statistic was computed)
Rule: per family x parent session, cells with n_PRE>=100 and STORED PRE mean>0, ranked by MEASURED effect t vs random-in-session; flat S/R duplicates collapsed (higher t kept), max 2 cells per build, top 10; plus the three seed cells explicitly. Screened F per family-session printed in the stage-1 table.
415 cells
BOS|ASIA|tf-10|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -10, "tmode": "SO", "typ": "B"}|none|B50/50|S
BOS|ASIA|tf-10|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -10, "tmode": "SO", "typ": "B"}|none|B60/60|R
BOS|ASIA|tf-15|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -15, "tmode": "SO", "typ": "B"}|none|B60/60|S
BOS|ASIA|tf-30|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -30, "tmode": "SO", "typ": "B"}|none|B60/60|S
BOS|ASIA|tf-30|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -30, "tmode": "SO", "typ": "B"}|none|B30/30|S
BOS|ASIA|tf-30|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -30, "tmode": "SO", "typ": "B"}|none|STR|R
BOS|ASIA|tf-9500|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -9500, "tmode": "SO", "typ": "B"}|none|B30/30|S
BOS|ASIA|tf-9500|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -9500, "tmode": "SO", "typ": "B"}|none|B60/60|S
BOS|ASIA|tf2|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "B"}|none|B30/30|R
BOS|ASIA|tf2|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "B"}|none|B60/60|S
BOS|CLOSE|tf-10|{"L": 3, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -10, "tmode": "T1"}|none|B40/40|R
BOS|CLOSE|tf-10|{"L": 3, "W": 30, "buf": 0, "entry": "stop", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -10, "tmode": "T1"}|none|B40/40|R
BOS|CLOSE|tf-10|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -10, "tmode": "T1"}|none|B20/20|S
BOS|CLOSE|tf-10|{"L": 5, "W": 30, "buf": 0, "entry": "stop", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -10, "tmode": "T1"}|none|B20/20|S
BOS|CLOSE|tf-15|{"L": 3, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -15, "tmode": "T1"}|none|B60/60|S
BOS|CLOSE|tf-15|{"L": 3, "box": "on", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -15, "tmode": "SO", "typ": "B"}|none|B30/30|S
BOS|CLOSE|tf-15|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -15, "tmode": "T1"}|none|B30/30|R
BOS|CLOSE|tf-15|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -15, "tmode": "T1"}|none|B60/60|R
BOS|CLOSE|tf-5|{"L": 3, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -5, "tmode": "T1"}|none|B60/60|R
BOS|CLOSE|tf-5|{"L": 3, "W": 30, "buf": 0, "entry": "stop", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -5, "tmode": "T1"}|none|B60/60|R
BOS|LONDON|tf-10|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -10, "tmode": "T1"}|none|B60/60|S
BOS|LONDON|tf-15|{"L": 5, "W": 30, "buf": 0, "entry": "stop", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -15, "tmode": "T1"}|none|B60/60|S
BOS|LONDON|tf-15|{"L": 5, "W": 30, "buf": 0, "entry": "stop", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -15, "tmode": "T1"}|none|B60/60|S
BOS|LONDON|tf-30|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -30, "tmode": "SO", "typ": "B"}|none|B40/40|R
BOS|LONDON|tf-30|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -30, "tmode": "T1"}|none|B60/60|S
BOS|LONDON|tf-30|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -30, "tmode": "T1"}|none|B60/60|S
BOS|LONDON|tf-30|{"L": 5, "W": 30, "buf": 0, "entry": "stop", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -30, "tmode": "T1"}|none|B60/60|S
BOS|LONDON|tf-30|{"L": 5, "W": 30, "buf": 0, "entry": "stop", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -30, "tmode": "T1"}|none|B60/60|S
BOS|LONDON|tf-9500|{"L": 3, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -9500, "tmode": "T1"}|none|B60/60|S
BOS|LONDON|tf-9500|{"L": 3, "W": 30, "buf": 0, "entry": "stop", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -9500, "tmode": "T1"}|none|B60/60|S
BOS|NYAM|tf-15|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -15, "tmode": "SO", "typ": "B"}|none|B50/50|R
BOS|NYAM|tf-15|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -15, "tmode": "SO", "typ": "B"}|none|B60/60|R
BOS|NYAM|tf-30|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -30, "tmode": "SO", "typ": "B"}|none|B50/50|R
BOS|NYAM|tf-5|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -5, "tmode": "SO", "typ": "B"}|none|B60/60|R
BOS|NYAM|tf1|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 1, "tmode": "SO", "typ": "B"}|none|B50/50|R
BOS|NYAM|tf1|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 1, "tmode": "SO", "typ": "B"}|none|B60/60|R
BOS|NYAM|tf1|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": 1, "tmode": "T1"}|none|B60/60|R
BOS|NYAM|tf2|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "B"}|none|B50/50|R
BOS|NYAM|tf2|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "B"}|none|B60/60|R
BOS|NYAM|tf2|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "B"}|none|B60/60|R
BOS|NYPM|tf-10|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -10, "tmode": "SO", "typ": "B"}|none|B20/20|R
BOS|NYPM|tf-10|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -10, "tmode": "SO", "typ": "B"}|none|B40/40|R
BOS|NYPM|tf-15|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -15, "tmode": "SO", "typ": "B"}|none|STR|R
BOS|NYPM|tf-15|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -15, "tmode": "T1"}|none|B20/20|R
BOS|NYPM|tf-15|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -15, "tmode": "T1"}|none|B30/30|R
BOS|NYPM|tf-30|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -30, "tmode": "SO", "typ": "B"}|none|B20/20|R
BOS|NYPM|tf-5|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -5, "tmode": "SO", "typ": "B"}|none|B20/20|R
BOS|NYPM|tf-5|{"L": 3, "box": "on", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -5, "tmode": "SO", "typ": "B"}|none|B60/60|R
BOS|NYPM|tf-9500|{"L": 3, "box": "on", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -9500, "tmode": "SO", "typ": "B"}|none|B60/60|R
BOS|NYPM|tf1|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 1, "tmode": "SO", "typ": "B"}|none|B20/20|R
BOS|PRE|tf-10|{"L": 3, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -10, "tmode": "T1"}|none|B20/20|R
BOS|PRE|tf-10|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -10, "tmode": "T1"}|none|B30/30|R
BOS|PRE|tf-10|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -10, "tmode": "T1"}|none|B20/20|R
BOS|PRE|tf-15|{"L": 3, "W": 30, "buf": 0, "entry": "stop", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": -15, "tmode": "T1"}|none|B60/60|R
BOS|PRE|tf-30|{"L": 3, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -30, "tmode": "T1"}|none|B20/20|R
BOS|PRE|tf-30|{"L": 3, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -30, "tmode": "T1"}|none|B60/60|S
BOS|PRE|tf-5|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -5, "tmode": "SO", "typ": "B"}|none|B20/20|R
BOS|PRE|tf-5|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "c", "s": 1, "stop": "s", "tf": -5, "tmode": "T1"}|none|B50/50|R
BOS|PRE|tf1|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": 1, "tmode": "T1"}|none|B20/20|S
BOS|PRE|tf1|{"L": 5, "W": 30, "buf": 0, "entry": "mkt", "nb": 3, "p3": 1, "ref": "sig", "resp": "b", "s": 1, "stop": "s", "tf": 1, "tmode": "T1"}|none|B40/40|R
CRT|ASIA|tf-10|{"L": 3, "buf": 0, "etf": -10, "etype": "csd", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R
CRT|ASIA|tf-15|{"L": 3, "buf": 0, "etf": -15, "etype": "close", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|STR|R
CRT|ASIA|tf-30|{"L": 3, "buf": 0, "etf": -30, "etype": "lim50", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B20/20|R
CRT|ASIA|tf-5|{"L": 3, "buf": 0, "etf": -5, "etype": "csd", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|STR|S
CRT|ASIA|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|STR|R
CRT|ASIA|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|STR|S
CRT|ASIA|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "csd", "htf": 15, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B60/60|R
CRT|ASIA|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "lim50", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|R
CRT|ASIA|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "csd", "htf": 30, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|STR|S
CRT|ASIA|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "csd", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|STR|R
CRT|CLOSE|tf-10|{"L": 3, "buf": 0, "etf": -10, "etype": "lim50", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|R
CRT|CLOSE|tf-15|{"L": 3, "buf": 0, "etf": -15, "etype": "lim50", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|R
CRT|CLOSE|tf-30|{"L": 3, "buf": 0, "etf": -30, "etype": "lim50", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|R
CRT|CLOSE|tf-5|{"L": 3, "buf": 0, "etf": -5, "etype": "lim50", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|R
CRT|CLOSE|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "lim50", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B20/20|S
CRT|CLOSE|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "lim50", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|S
CRT|CLOSE|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "lim50", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|R
CRT|CLOSE|tf2|{"L": 3, "buf": 0, "etf": 2, "etype": "lim50", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B20/20|S
CRT|CLOSE|tf2|{"L": 3, "buf": 0, "etf": 2, "etype": "lim50", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|S
CRT|CLOSE|tf2|{"L": 3, "buf": 0, "etf": 2, "etype": "lim50", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|R
CRT|LONDON|tf-15|{"L": 3, "buf": 0, "etf": -15, "etype": "close", "htf": 60, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|S
CRT|LONDON|tf-15|{"L": 3, "buf": 0, "etf": -15, "etype": "csd", "htf": 15, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R
CRT|LONDON|tf-5|{"L": 3, "buf": 0, "etf": -5, "etype": "close", "htf": 15, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B60/60|R
CRT|LONDON|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 240, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|STR|S
CRT|LONDON|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "csd", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B20/20|S
CRT|LONDON|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "csd", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|S
CRT|LONDON|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "csd", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B20/20|R
CRT|LONDON|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "csd", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|R
CRT|LONDON|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "close", "htf": 15, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|STR|R
CRT|LONDON|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "close", "htf": 15, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|STR|S
CRT|LONDON|tf2|{"L": 3, "buf": 0, "etf": 2, "etype": "close", "htf": 60, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B20/20|S
CRT|NYAM|tf-30|{"L": 3, "buf": 0, "etf": -30, "etype": "csd", "htf": 15, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B60/60|S
CRT|NYAM|tf-5|{"L": 3, "buf": 0, "etf": -5, "etype": "close", "htf": 15, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B20/20|S
CRT|NYAM|tf-5|{"L": 3, "buf": 0, "etf": -5, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B20/20|S
CRT|NYAM|tf-5|{"L": 3, "buf": 0, "etf": -5, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R
CRT|NYAM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|S
CRT|NYAM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|S
CRT|NYAM|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "csd", "htf": 15, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B60/60|S
CRT|NYAM|tf2|{"L": 3, "buf": 0, "etf": 2, "etype": "csd", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|S
CRT|NYAM|tf2|{"L": 3, "buf": 0, "etf": 2, "etype": "csd", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B60/60|S
CRT|NYAM|tf2|{"L": 3, "buf": 0, "etf": 2, "etype": "csd", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B60/60|S
CRT|NYPM|tf-10|{"L": 3, "buf": 0, "etf": -10, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R
CRT|NYPM|tf-30|{"L": 3, "buf": 0, "etf": -30, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R
CRT|NYPM|tf-5|{"L": 3, "buf": 0, "etf": -5, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R
CRT|NYPM|tf-5|{"L": 3, "buf": 0, "etf": -5, "etype": "close", "htf": 60, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R
CRT|NYPM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R
CRT|NYPM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R
CRT|NYPM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "csd", "htf": 30, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B20/20|R
CRT|NYPM|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R
CRT|NYPM|tf2|{"L": 3, "buf": 0, "etf": 2, "etype": "close", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B20/20|R
CRT|NYPM|tf2|{"L": 3, "buf": 0, "etf": 2, "etype": "close", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R
CRT|PRE|tf-10|{"L": 3, "buf": 0, "etf": -10, "etype": "close", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R
CRT|PRE|tf-10|{"L": 3, "buf": 0, "etf": -10, "etype": "csd", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|S
CRT|PRE|tf-10|{"L": 3, "buf": 0, "etf": -10, "etype": "csd", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B60/60|R
CRT|PRE|tf-30|{"L": 3, "buf": 0, "etf": -30, "etype": "close", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R
CRT|PRE|tf-5|{"L": 3, "buf": 0, "etf": -5, "etype": "close", "htf": 240, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R
CRT|PRE|tf-5|{"L": 3, "buf": 0, "etf": -5, "etype": "csd", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B20/20|R
CRT|PRE|tf-5|{"L": 3, "buf": 0, "etf": -5, "etype": "csd", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B60/60|R
CRT|PRE|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R
CRT|PRE|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B30/30|R
CRT|PRE|tf1|{"L": 3, "buf": 0, "etf": 1, "etype": "close", "htf": 60, "inside": 0, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|S
FV|ASIA|tf-15|{"entry": "d", "sing": 10, "size": 8, "tf": -15}|deliv|B60/60|R
FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 16, "tf": -9500}|deliv|B60/60|R
FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 16, "tf": -9500}|none|B60/60|R
FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 4, "tf": -9500}|none|B60/60|S
FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 8, "tf": -9500}|none|B50/50|S
FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 8, "tf": -9500}|none|B60/60|S
FV|ASIA|tf-9500|{"entry": "c", "sing": 10, "size": 16, "tf": -9500}|none|B60/60|R
FV|ASIA|tf-9500|{"entry": "c", "sing": 10, "size": 8, "tf": -9500}|none|B50/50|S
FV|ASIA|tf1|{"entry": "a", "sing": 10, "size": 8, "tf": 1}|none|B60/60|R
FV|ASIA|tf2|{"entry": "b", "sing": 10, "size": 16, "tf": 2}|mom|B40/40|R
FV|CLOSE|tf-10|{"entry": "a", "sing": 10, "size": 8, "tf": -10}|none|B20/20|R
FV|CLOSE|tf-10|{"entry": "b", "sing": 0, "size": 4, "tf": -10}|mom|B20/20|R
FV|CLOSE|tf-10|{"entry": "b", "sing": 0, "size": 8, "tf": -10}|mom|B20/20|R
FV|CLOSE|tf-10|{"entry": "b", "sing": 0, "size": 8, "tf": -10}|none|B20/20|S
FV|CLOSE|tf-10|{"entry": "b", "sing": 10, "size": 8, "tf": -10}|mom|B20/20|S
FV|CLOSE|tf-15|{"entry": "a", "sing": 10, "size": 16, "tf": -15}|pd|B20/20|R
FV|CLOSE|tf-15|{"entry": "a", "sing": 10, "size": 16, "tf": -15}|sweep15|B20/20|R
FV|CLOSE|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|none|B20/20|R
FV|CLOSE|tf-5|{"entry": "a", "sing": 10, "size": 4, "tf": -5}|none|B30/30|S
FV|CLOSE|tf-5|{"entry": "b", "sing": 0, "size": 4, "tf": -5}|none|B30/30|S
FV|LONDON|tf2|{"entry": "a", "sing": 0, "size": 8, "tf": 2}|sweep15|B40/40|S
FV|LONDON|tf2|{"entry": "b", "sing": 10, "size": 16, "tf": 2}|pd|B20/20|S
FV|LONDON|tf2|{"entry": "c", "sing": 0, "size": 16, "tf": 2}|sweep15|B40/40|S
FV|LONDON|tf2|{"entry": "c", "sing": 0, "size": 16, "tf": 2}|sweep15|B50/50|S
FV|LONDON|tf2|{"entry": "c", "sing": 0, "size": 4, "tf": 2}|sweep15|B40/40|S
FV|LONDON|tf2|{"entry": "c", "sing": 0, "size": 8, "tf": 2}|sweep15|B40/40|S
FV|LONDON|tf2|{"entry": "c", "sing": 0, "size": 8, "tf": 2}|sweep15|B50/50|S
FV|LONDON|tf2|{"entry": "c", "sing": 10, "size": 16, "tf": 2}|sweep15|B40/40|S
FV|LONDON|tf2|{"entry": "c", "sing": 10, "size": 16, "tf": 2}|sweep15|B60/60|S
FV|LONDON|tf2|{"entry": "c", "sing": 10, "size": 4, "tf": 2}|sweep15|B40/40|S
FV|NYAM|tf-10|{"entry": "b", "sing": 0, "size": 4, "tf": -10}|deliv|B20/20|R
FV|NYAM|tf-10|{"entry": "b", "sing": 0, "size": 4, "tf": -10}|none|B20/20|R
FV|NYAM|tf-10|{"entry": "b", "sing": 0, "size": 8, "tf": -10}|deliv|B20/20|R
FV|NYAM|tf-10|{"entry": "b", "sing": 10, "size": 4, "tf": -10}|deliv|B20/20|R
FV|NYAM|tf-10|{"entry": "b", "sing": 10, "size": 8, "tf": -10}|deliv|B20/20|R
FV|NYAM|tf-15|{"entry": "b", "sing": 0, "size": 4, "tf": -15}|deliv|B20/20|R
FV|NYAM|tf-5|{"entry": "b", "sing": 10, "size": 8, "tf": -5}|deliv|B20/20|R
FV|NYAM|tf-9500|{"entry": "b", "sing": 0, "size": 16, "tf": -9500}|mom|B40/40|R
FV|NYAM|tf-9500|{"entry": "b", "sing": 0, "size": 4, "tf": -9500}|mom|B40/40|R
FV|NYAM|tf-9500|{"entry": "b", "sing": 0, "size": 8, "tf": -9500}|mom|B40/40|R
FV|NYPM|tf1|{"entry": "a", "sing": 10, "size": 16, "tf": 1}|mom|B60/60|S
FV|NYPM|tf1|{"entry": "b", "sing": 10, "size": 16, "tf": 1}|mom|B50/50|R
FV|NYPM|tf2|{"entry": "a", "sing": 0, "size": 16, "tf": 2}|mom|B40/40|S
FV|NYPM|tf2|{"entry": "a", "sing": 0, "size": 4, "tf": 2}|mom|B40/40|S
FV|NYPM|tf2|{"entry": "a", "sing": 0, "size": 4, "tf": 2}|mom|B50/50|S
FV|NYPM|tf2|{"entry": "a", "sing": 0, "size": 8, "tf": 2}|mom|B40/40|S
FV|NYPM|tf2|{"entry": "a", "sing": 0, "size": 8, "tf": 2}|mom|B50/50|S
FV|NYPM|tf2|{"entry": "a", "sing": 10, "size": 16, "tf": 2}|mom|B40/40|S
FV|NYPM|tf2|{"entry": "b", "sing": 0, "size": 4, "tf": 2}|mom|B60/60|R
FV|NYPM|tf2|{"entry": "b", "sing": 0, "size": 8, "tf": 2}|mom|B60/60|R
FV|PRE|tf-10|{"entry": "a", "sing": 10, "size": 4, "tf": -10}|mom|B30/30|S
FV|PRE|tf-10|{"entry": "a", "sing": 10, "size": 4, "tf": -10}|none|B60/60|S
FV|PRE|tf-10|{"entry": "b", "sing": 10, "size": 4, "tf": -10}|mom|B50/50|S
FV|PRE|tf-10|{"entry": "b", "sing": 10, "size": 4, "tf": -10}|none|B50/50|S
FV|PRE|tf-15|{"entry": "a", "sing": 0, "size": 4, "tf": -15}|none|B40/40|R
FV|PRE|tf-30|{"entry": "b", "sing": 10, "size": 4, "tf": -30}|deliv|B40/40|S
FV|PRE|tf-30|{"entry": "b", "sing": 10, "size": 4, "tf": -30}|deliv|B60/60|S
FV|PRE|tf-30|{"entry": "b", "sing": 10, "size": 8, "tf": -30}|deliv|B50/50|S
FV|PRE|tf-5|{"entry": "c", "sing": 10, "size": 16, "tf": -5}|sweep15|B20/20|R
FV|PRE|tf-9500|{"entry": "b", "sing": 0, "size": 16, "tf": -9500}|pd|STR|S
IF|ASIA|tf-10|{"entry": "a", "sing": 0, "size": 16, "tf": -10}|none|B40/40|R
IF|ASIA|tf-10|{"entry": "a", "sing": 10, "size": 16, "tf": -10}|deliv|B60/60|R
IF|ASIA|tf-10|{"entry": "a", "sing": 10, "size": 16, "tf": -10}|none|B40/40|R
IF|ASIA|tf-10|{"entry": "b", "sing": 10, "size": 16, "tf": -10}|deliv|B60/60|R
IF|ASIA|tf-15|{"entry": "a", "sing": 10, "size": 16, "tf": -15}|deliv|B40/40|R
IF|ASIA|tf-15|{"entry": "a", "sing": 10, "size": 8, "tf": -15}|deliv|B60/60|R
IF|ASIA|tf-15|{"entry": "b", "sing": 10, "size": 16, "tf": -15}|deliv|B50/50|S
IF|ASIA|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|deliv|B60/60|R
IF|ASIA|tf-30|{"entry": "b", "sing": 10, "size": 8, "tf": -30}|none|STR|R
IF|ASIA|tf-30|{"entry": "b", "sing": 10, "size": 8, "tf": -30}|none|STR|S
IF|ASIA|tf-30|{"entry": "c", "sing": 0, "size": 8, "tf": -30}|deliv|B40/40|R
IF|ASIA|tf1|{"entry": "a", "sing": 0, "size": 4, "tf": 1}|deliv|B30/30|S
IF|CLOSE|tf-15|{"entry": "a", "sing": 0, "size": 4, "tf": -15}|mom|B20/20|R
IF|CLOSE|tf-15|{"entry": "a", "sing": 10, "size": 4, "tf": -15}|mom|B20/20|R
IF|CLOSE|tf-15|{"entry": "b", "sing": 0, "size": 4, "tf": -15}|mom|B20/20|R
IF|CLOSE|tf-15|{"entry": "b", "sing": 10, "size": 4, "tf": -15}|mom|B20/20|S
IF|CLOSE|tf-15|{"entry": "b", "sing": 10, "size": 4, "tf": -15}|pd|B20/20|R
IF|CLOSE|tf-30|{"entry": "a", "sing": 0, "size": 8, "tf": -30}|none|B20/20|S
IF|CLOSE|tf-30|{"entry": "b", "sing": 0, "size": 8, "tf": -30}|none|B20/20|R
IF|CLOSE|tf-30|{"entry": "b", "sing": 10, "size": 4, "tf": -30}|deliv|B20/20|S
IF|CLOSE|tf1|{"entry": "b", "sing": 0, "size": 8, "tf": 1}|none|B20/20|R
IF|CLOSE|tf1|{"entry": "d", "sing": 10, "size": 8, "tf": 1}|deliv|B20/20|S
IF|LONDON|tf-10|{"entry": "b", "sing": 10, "size": 16, "tf": -10}|sweep15|STR|S
IF|LONDON|tf-10|{"entry": "c", "sing": 0, "size": 16, "tf": -10}|sweep15|B30/30|S
IF|LONDON|tf-10|{"entry": "c", "sing": 0, "size": 16, "tf": -10}|sweep15|B40/40|S
IF|LONDON|tf-5|{"entry": "b", "sing": 10, "size": 4, "tf": -5}|deliv|B60/60|R
IF|LONDON|tf-5|{"entry": "d", "sing": 10, "size": 16, "tf": -5}|sweep15|B40/40|S
IF|LONDON|tf-9500|{"entry": "b", "sing": 0, "size": 8, "tf": -9500}|none|B30/30|R
IF|LONDON|tf-9500|{"entry": "c", "sing": 0, "size": 4, "tf": -9500}|sweep15|B20/20|S
IF|LONDON|tf1|{"entry": "b", "sing": 0, "size": 16, "tf": 1}|mom|B40/40|R
IF|LONDON|tf1|{"entry": "c", "sing": 0, "size": 4, "tf": 1}|sweep15|STR|S
IF|LONDON|tf2|{"entry": "b", "sing": 0, "size": 4, "tf": 2}|deliv|STR|S
IF|NYAM|tf-10|{"entry": "b", "sing": 0, "size": 16, "tf": -10}|deliv|B40/40|R
IF|NYAM|tf-15|{"entry": "b", "sing": 10, "size": 4, "tf": -15}|deliv|STR|R
IF|NYAM|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|none|STR|R
IF|NYAM|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|none|STR|S
IF|NYAM|tf-15|{"entry": "c", "sing": 0, "size": 4, "tf": -15}|deliv|B60/60|R
IF|NYAM|tf-15|{"entry": "c", "sing": 10, "size": 4, "tf": -15}|deliv|B60/60|R
IF|NYAM|tf-30|{"entry": "a", "sing": 0, "size": 4, "tf": -30}|mom|B60/60|R
IF|NYAM|tf-30|{"entry": "a", "sing": 0, "size": 8, "tf": -30}|mom|B60/60|R
IF|NYAM|tf-5|{"entry": "b", "sing": 0, "size": 4, "tf": -5}|mom|B20/20|R
IF|NYAM|tf-5|{"entry": "b", "sing": 0, "size": 4, "tf": -5}|none|B20/20|R
IF|NYAM|tf-5|{"entry": "c", "sing": 10, "size": 16, "tf": -5}|deliv|B40/40|R
IF|NYAM|tf2|{"entry": "d", "sing": 10, "size": 16, "tf": 2}|deliv|B40/40|R
IF|NYPM|tf-15|{"entry": "a", "sing": 0, "size": 8, "tf": -15}|mom|B20/20|R
IF|NYPM|tf-15|{"entry": "b", "sing": 0, "size": 16, "tf": -15}|none|B60/60|R
IF|NYPM|tf-15|{"entry": "b", "sing": 10, "size": 16, "tf": -15}|none|B60/60|R
IF|NYPM|tf-15|{"entry": "b", "sing": 10, "size": 4, "tf": -15}|none|B60/60|R
IF|NYPM|tf1|{"entry": "b", "sing": 0, "size": 4, "tf": 1}|none|B30/30|R
IF|NYPM|tf1|{"entry": "b", "sing": 0, "size": 8, "tf": 1}|none|B30/30|R
IF|NYPM|tf1|{"entry": "b", "sing": 10, "size": 4, "tf": 1}|none|B30/30|S
IF|NYPM|tf2|{"entry": "a", "sing": 0, "size": 4, "tf": 2}|none|B60/60|R
IF|NYPM|tf2|{"entry": "a", "sing": 10, "size": 4, "tf": 2}|none|B60/60|R
IF|NYPM|tf2|{"entry": "c", "sing": 0, "size": 8, "tf": 2}|mom|B60/60|R
IF|PRE|tf-30|{"entry": "b", "sing": 10, "size": 16, "tf": -30}|pd|STR|R
IF|PRE|tf-9500|{"entry": "b", "sing": 0, "size": 16, "tf": -9500}|none|B20/20|R
IF|PRE|tf-9500|{"entry": "b", "sing": 0, "size": 16, "tf": -9500}|pd|B20/20|R
IF|PRE|tf-9500|{"entry": "b", "sing": 0, "size": 4, "tf": -9500}|mom|B20/20|S
IF|PRE|tf-9500|{"entry": "b", "sing": 0, "size": 4, "tf": -9500}|pd|B20/20|S
IF|PRE|tf-9500|{"entry": "b", "sing": 0, "size": 8, "tf": -9500}|none|B20/20|S
IF|PRE|tf-9500|{"entry": "b", "sing": 0, "size": 8, "tf": -9500}|pd|B20/20|S
IF|PRE|tf-9500|{"entry": "b", "sing": 10, "size": 16, "tf": -9500}|pd|B20/20|R
IF|PRE|tf-9500|{"entry": "b", "sing": 10, "size": 8, "tf": -9500}|pd|B20/20|S
IF|PRE|tf1|{"entry": "b", "sing": 10, "size": 4, "tf": 1}|mom|B20/20|S
OB|ASIA|tf-15|{"entry": "a", "kbrk": 0.5, "kimp": 1.5, "tf": -15}|none|B50/50|S
OB|ASIA|tf-5|{"entry": "b", "kbrk": 0.5, "kimp": 1.0, "tf": -5}|mom|B60/60|R
OB|ASIA|tf-9500|{"entry": "b", "kbrk": 0.5, "kimp": 1.0, "tf": -9500}|pd|B20/20|S
OB|ASIA|tf1|{"entry": "b", "kbrk": 0.5, "kimp": 1.0, "tf": 1}|mom|B50/50|R
OB|ASIA|tf1|{"entry": "b", "kbrk": 0.5, "kimp": 1.0, "tf": 1}|sweep15|B20/20|R
OB|ASIA|tf1|{"entry": "b", "kbrk": 1.0, "kimp": 1.0, "tf": 1}|sweep15|B60/60|R
OB|ASIA|tf2|{"entry": "b", "kbrk": 0.5, "kimp": 1.5, "tf": 2}|none|STR|S
OB|ASIA|tf2|{"entry": "b", "kbrk": 1.0, "kimp": 1.5, "tf": 2}|none|STR|S
OB|ASIA|tf2|{"entry": "b", "kbrk": 1.0, "kimp": 1.5, "tf": 2}|pd|STR|R
OB|ASIA|tf2|{"entry": "c", "kbrk": 0.5, "kimp": 1.0, "tf": 2}|pd|STR|R
OB|CLOSE|tf-10|{"entry": "a", "kbrk": 0.5, "kimp": 1.0, "tf": -10}|pd|B20/20|R
OB|CLOSE|tf-10|{"entry": "b", "kbrk": 0.5, "kimp": 1.0, "tf": -10}|pd|B20/20|S
OB|CLOSE|tf-10|{"entry": "b", "kbrk": 0.5, "kimp": 1.5, "tf": -10}|none|B20/20|S
OB|CLOSE|tf-10|{"entry": "b", "kbrk": 1.0, "kimp": 1.0, "tf": -10}|pd|B20/20|R
OB|CLOSE|tf-10|{"entry": "b", "kbrk": 1.0, "kimp": 1.5, "tf": -10}|mom|B20/20|S
OB|CLOSE|tf-15|{"entry": "b", "kbrk": 0.5, "kimp": 1.5, "tf": -15}|mom|B20/20|R
OB|CLOSE|tf-5|{"entry": "b", "kbrk": 1.0, "kimp": 1.0, "tf": -5}|none|B30/30|S
OB|CLOSE|tf-9500|{"entry": "b", "kbrk": 0.5, "kimp": 1.5, "tf": -9500}|none|B20/20|R
OB|CLOSE|tf-9500|{"entry": "b", "kbrk": 0.5, "kimp": 1.5, "tf": -9500}|pd|B20/20|R
OB|CLOSE|tf2|{"entry": "b", "kbrk": 0.5, "kimp": 1.5, "tf": 2}|none|B20/20|R
OB|LONDON|tf-9500|{"entry": "a", "kbrk": 1.0, "kimp": 1.0, "tf": -9500}|pd|B20/20|R
OB|LONDON|tf1|{"entry": "a", "kbrk": 1.0, "kimp": 1.5, "tf": 1}|sweep15|B50/50|S
OB|LONDON|tf1|{"entry": "b", "kbrk": 0.5, "kimp": 1.5, "tf": 1}|sweep15|B60/60|S
OB|LONDON|tf1|{"entry": "b", "kbrk": 1.0, "kimp": 1.5, "tf": 1}|sweep15|B60/60|S
OB|LONDON|tf2|{"entry": "a", "kbrk": 0.5, "kimp": 2.0, "tf": 2}|mom|B20/20|S
OB|LONDON|tf2|{"entry": "a", "kbrk": 1.0, "kimp": 2.0, "tf": 2}|mom|B20/20|S
OB|LONDON|tf2|{"entry": "a", "kbrk": 1.0, "kimp": 2.0, "tf": 2}|none|B20/20|S
OB|LONDON|tf2|{"entry": "b", "kbrk": 1.0, "kimp": 2.0, "tf": 2}|none|B20/20|S
OB|LONDON|tf2|{"entry": "c", "kbrk": 0.5, "kimp": 2.0, "tf": 2}|none|B30/30|S
OB|LONDON|tf2|{"entry": "c", "kbrk": 1.0, "kimp": 2.0, "tf": 2}|none|B30/30|S
OB|NYAM|tf-5|{"entry": "a", "kbrk": 0.5, "kimp": 2.0, "tf": -5}|none|B60/60|R
OB|NYAM|tf-5|{"entry": "a", "kbrk": 1.0, "kimp": 2.0, "tf": -5}|none|B60/60|R
OB|NYAM|tf-5|{"entry": "b", "kbrk": 0.5, "kimp": 2.0, "tf": -5}|mom|B60/60|R
OB|NYAM|tf-9500|{"entry": "a", "kbrk": 1.0, "kimp": 1.0, "tf": -9500}|mom|B30/30|R
OB|NYAM|tf1|{"entry": "b", "kbrk": 1.0, "kimp": 1.5, "tf": 1}|none|STR|R
OB|NYAM|tf2|{"entry": "a", "kbrk": 1.0, "kimp": 1.0, "tf": 2}|pd|B40/40|R
OB|NYAM|tf2|{"entry": "b", "kbrk": 0.5, "kimp": 1.0, "tf": 2}|mom|STR|S
OB|NYAM|tf2|{"entry": "b", "kbrk": 0.5, "kimp": 1.0, "tf": 2}|none|STR|R
OB|NYAM|tf2|{"entry": "c", "kbrk": 0.5, "kimp": 1.5, "tf": 2}|pd|B40/40|S
OB|NYAM|tf2|{"entry": "c", "kbrk": 0.5, "kimp": 1.5, "tf": 2}|pd|B50/50|S
OB|NYPM|tf-10|{"entry": "a", "kbrk": 1.0, "kimp": 2.0, "tf": -10}|mom|STR|S
OB|NYPM|tf-10|{"entry": "c", "kbrk": 0.5, "kimp": 1.0, "tf": -10}|mom|B60/60|S
OB|NYPM|tf-10|{"entry": "c", "kbrk": 1.0, "kimp": 2.0, "tf": -10}|mom|STR|S
OB|NYPM|tf-15|{"entry": "b", "kbrk": 0.5, "kimp": 1.5, "tf": -15}|mom|B50/50|S
OB|NYPM|tf-15|{"entry": "b", "kbrk": 1.0, "kimp": 2.0, "tf": -15}|mom|B50/50|S
OB|NYPM|tf-30|{"entry": "b", "kbrk": 1.0, "kimp": 1.0, "tf": -30}|none|B60/60|R
OB|NYPM|tf-5|{"entry": "a", "kbrk": 1.0, "kimp": 1.0, "tf": -5}|none|B50/50|R
OB|NYPM|tf-5|{"entry": "c", "kbrk": 1.0, "kimp": 2.0, "tf": -5}|mom|B60/60|S
OB|NYPM|tf1|{"entry": "a", "kbrk": 1.0, "kimp": 1.0, "tf": 1}|mom|B50/50|R
OB|NYPM|tf1|{"entry": "a", "kbrk": 1.0, "kimp": 1.5, "tf": 1}|mom|B50/50|R
OB|PRE|tf-10|{"entry": "b", "kbrk": 0.5, "kimp": 2.0, "tf": -10}|sweep15|B30/30|R
OB|PRE|tf-10|{"entry": "b", "kbrk": 1.0, "kimp": 2.0, "tf": -10}|sweep15|B30/30|R
OB|PRE|tf-30|{"entry": "b", "kbrk": 1.0, "kimp": 1.0, "tf": -30}|none|STR|S
OB|PRE|tf-30|{"entry": "b", "kbrk": 1.0, "kimp": 1.0, "tf": -30}|pd|STR|S
OB|PRE|tf-5|{"entry": "a", "kbrk": 0.5, "kimp": 1.0, "tf": -5}|none|B50/50|R
OB|PRE|tf-5|{"entry": "a", "kbrk": 0.5, "kimp": 1.0, "tf": -5}|none|B60/60|S
OB|PRE|tf-5|{"entry": "b", "kbrk": 1.0, "kimp": 1.0, "tf": -5}|none|STR|S
OB|PRE|tf1|{"entry": "a", "kbrk": 0.5, "kimp": 1.5, "tf": 1}|pd|STR|R
OB|PRE|tf1|{"entry": "b", "kbrk": 0.5, "kimp": 1.0, "tf": 1}|sweep15|B20/20|S
OB|PRE|tf1|{"entry": "b", "kbrk": 0.5, "kimp": 1.0, "tf": 1}|sweep15|STR|S
SB|KZ_ASIA|tf-10|{"entry": "b", "sing": 10, "size": 8, "tf": -10}|none|B20/20|R
SB|KZ_ASIA|tf-10|{"entry": "b", "sing": 10, "size": 8, "tf": -10}|none|STR|R
SB|KZ_ASIA|tf-10|{"entry": "c", "sing": 10, "size": 8, "tf": -10}|none|B60/60|R
SB|KZ_ASIA|tf-10|{"entry": "d", "sing": 10, "size": 8, "tf": -10}|none|B60/60|R
SB|KZ_ASIA|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|none|B50/50|R
SB|KZ_ASIA|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|none|B60/60|R
SB|KZ_ASIA|tf-15|{"entry": "c", "sing": 10, "size": 8, "tf": -15}|none|B60/60|R
SB|KZ_ASIA|tf-5|{"entry": "a", "sing": 10, "size": 8, "tf": -5}|none|B40/40|R
SB|KZ_ASIA|tf-9500|{"entry": "b", "sing": 10, "size": 8, "tf": -9500}|none|B40/40|R
SB|KZ_ASIA|tf2|{"entry": "a", "sing": 10, "size": 8, "tf": 2}|none|B20/20|R
SB|KZ_LON|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|none|B50/50|R
SB|KZ_LON|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|none|B60/60|R
SB|KZ_LON|tf1|{"entry": "b", "sing": 10, "size": 8, "tf": 1}|none|B40/40|R
SB|KZ_LON|tf2|{"entry": "d", "sing": 10, "size": 8, "tf": 2}|none|B60/60|R
SB|KZ_NY_AM|tf-10|{"entry": "b", "sing": 10, "size": 8, "tf": -10}|none|B20/20|S
SB|KZ_NY_AM|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|none|STR|S
SB|KZ_NY_AM|tf-30|{"entry": "a", "sing": 10, "size": 8, "tf": -30}|none|B60/60|R
SB|KZ_NY_AM|tf-5|{"entry": "b", "sing": 10, "size": 8, "tf": -5}|none|B40/40|R
SB|KZ_NY_AM|tf-5|{"entry": "b", "sing": 10, "size": 8, "tf": -5}|none|B60/60|R
SB|KZ_NY_AM|tf2|{"entry": "a", "sing": 10, "size": 8, "tf": 2}|none|B40/40|R
SB|KZ_NY_AM|tf2|{"entry": "b", "sing": 10, "size": 8, "tf": 2}|none|B40/40|R
SB|KZ_NY_AM|tf2|{"entry": "b", "sing": 10, "size": 8, "tf": 2}|none|B50/50|S
SB|KZ_NY_AM|tf2|{"entry": "c", "sing": 10, "size": 8, "tf": 2}|none|B60/60|S
SB|KZ_NY_AM|tf2|{"entry": "d", "sing": 10, "size": 8, "tf": 2}|none|B60/60|S
SB|KZ_NY_PRE|tf-10|{"entry": "b", "sing": 10, "size": 8, "tf": -10}|none|B30/30|S
SB|KZ_NY_PRE|tf-10|{"entry": "b", "sing": 10, "size": 8, "tf": -10}|none|B50/50|S
SB|KZ_NY_PRE|tf-15|{"entry": "a", "sing": 10, "size": 8, "tf": -15}|none|B20/20|S
SB|KZ_NY_PRE|tf-30|{"entry": "b", "sing": 10, "size": 8, "tf": -30}|none|B20/20|R
SB|KZ_NY_PRE|tf-30|{"entry": "b", "sing": 10, "size": 8, "tf": -30}|none|STR|R
SB|KZ_NY_PRE|tf-9500|{"entry": "b", "sing": 10, "size": 8, "tf": -9500}|none|B20/20|S
SB|KZ_NY_PRE|tf-9500|{"entry": "b", "sing": 10, "size": 8, "tf": -9500}|none|B40/40|S
SB|KZ_NY_PRE|tf1|{"entry": "b", "sing": 10, "size": 8, "tf": 1}|none|B20/20|S
SB|KZ_NY_PRE|tf1|{"entry": "b", "sing": 10, "size": 8, "tf": 1}|none|STR|R
SB|KZ_NY_PRE|tf2|{"entry": "b", "sing": 10, "size": 8, "tf": 2}|none|STR|S
SB|KZ_PM|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|none|B40/40|R
SB|KZ_PM|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|none|STR|R
SB|KZ_PM|tf-30|{"entry": "b", "sing": 10, "size": 8, "tf": -30}|none|B30/30|S
SB|KZ_PM|tf-30|{"entry": "b", "sing": 10, "size": 8, "tf": -30}|none|STR|S
SB|KZ_PM|tf1|{"entry": "a", "sing": 10, "size": 8, "tf": 1}|none|B30/30|S
SB|KZ_PM|tf1|{"entry": "b", "sing": 10, "size": 8, "tf": 1}|none|B30/30|S
SB|KZ_PM|tf2|{"entry": "a", "sing": 10, "size": 8, "tf": 2}|none|B60/60|R
SB|SB_LON|tf-10|{"entry": "c", "sing": 10, "size": 8, "tf": -10}|none|B60/60|R
SB|SB_LON|tf-15|{"entry": "a", "sing": 10, "size": 8, "tf": -15}|none|B60/60|S
SB|SB_LON|tf-15|{"entry": "b", "sing": 10, "size": 8, "tf": -15}|none|B50/50|R
SB|SB_LON|tf-5|{"entry": "b", "sing": 10, "size": 8, "tf": -5}|none|B50/50|R
SB|SB_LON|tf-9500|{"entry": "c", "sing": 10, "size": 8, "tf": -9500}|none|B20/20|S
SB|SB_LON|tf1|{"entry": "b", "sing": 10, "size": 8, "tf": 1}|none|B30/30|R
SB|SB_PM|tf-15|{"entry": "a", "sing": 10, "size": 8, "tf": -15}|none|B60/60|R
SB|SB_PM|tf1|{"entry": "a", "sing": 10, "size": 8, "tf": 1}|none|STR|S
SB|SB_PM|tf1|{"entry": "b", "sing": 10, "size": 8, "tf": 1}|none|STR|S
SWEEP|ASIA|tf-10|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -10, "tmode": "SO", "typ": "A"}|none|B50/50|S
SWEEP|ASIA|tf-10|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -10, "tmode": "SO", "typ": "A"}|none|STR|S
SWEEP|ASIA|tf-15|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -15, "tmode": "SO", "typ": "A"}|none|STR|S
SWEEP|ASIA|tf-30|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -30, "tmode": "SO", "typ": "A"}|none|B50/50|S
SWEEP|ASIA|tf-30|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -30, "tmode": "SO", "typ": "A"}|none|STR|S
SWEEP|ASIA|tf-5|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -5, "tmode": "SO", "typ": "A"}|none|STR|S
SWEEP|ASIA|tf-9500|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -9500, "tmode": "SO", "typ": "A"}|none|STR|S
SWEEP|ASIA|tf1|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 1, "tmode": "SO", "typ": "A"}|none|STR|S
SWEEP|ASIA|tf1|{"L": 3, "bracket": "struct", "nb": 3, "s": 3, "tf": 1}|none|STR|R
SWEEP|ASIA|tf2|{"L": 3, "bracket": "struct", "nb": 1, "s": 3, "tf": 2}|none|STR|R
SWEEP|CLOSE|tf-30|{"L": 3, "bracket": "struct", "nb": 3, "s": 3, "tf": -30}|none|B30/30|S
SWEEP|CLOSE|tf-30|{"L": 8, "bracket": "struct", "nb": 3, "s": 1, "tf": -30}|none|B40/40|S
SWEEP|CLOSE|tf1|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 1, "tmode": "SO", "typ": "A"}|none|B20/20|R
SWEEP|CLOSE|tf1|{"L": 5, "bracket": "struct", "nb": 3, "s": 1, "tf": 1}|none|B20/20|R
SWEEP|CLOSE|tf1|{"L": 5, "bracket": "struct", "nb": 3, "s": 3, "tf": 1}|none|B20/20|R
SWEEP|CLOSE|tf1|{"L": 5, "bracket": "struct", "nb": 3, "s": 3, "tf": 1}|none|STR|R
SWEEP|CLOSE|tf1|{"L": 8, "bracket": "struct", "nb": 3, "s": 3, "tf": 1}|none|B20/20|R
SWEEP|CLOSE|tf2|{"L": 3, "bracket": "struct", "nb": 3, "s": 1, "tf": 2}|none|B20/20|R
SWEEP|CLOSE|tf2|{"L": 3, "bracket": "struct", "nb": 3, "s": 1, "tf": 2}|none|STR|S
SWEEP|CLOSE|tf2|{"L": 3, "bracket": "struct", "nb": 3, "s": 3, "tf": 2}|none|B20/20|R
SWEEP|LONDON|tf-30|{"L": 3, "bracket": "struct", "nb": 3, "s": 1, "tf": -30}|none|STR|R
SWEEP|LONDON|tf-30|{"L": 5, "bracket": "struct", "nb": 3, "s": 3, "tf": -30}|none|STR|R
SWEEP|LONDON|tf-30|{"L": 8, "bracket": "struct", "nb": 3, "s": 3, "tf": -30}|none|STR|S
SWEEP|LONDON|tf-9500|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -9500, "tmode": "SO", "typ": "A"}|none|B20/20|S
SWEEP|LONDON|tf-9500|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -9500, "tmode": "SO", "typ": "A"}|none|B30/30|S
SWEEP|LONDON|tf-9500|{"L": 8, "bracket": "struct", "nb": 1, "s": 1, "tf": -9500}|none|B40/40|R
SWEEP|LONDON|tf-9500|{"L": 8, "bracket": "struct", "nb": 1, "s": 3, "tf": -9500}|none|B40/40|R
SWEEP|LONDON|tf1|{"L": 3, "bracket": "struct", "nb": 1, "s": 3, "tf": 1}|none|STR|R
SWEEP|LONDON|tf1|{"L": 8, "bracket": "struct", "nb": 3, "s": 1, "tf": 1}|none|STR|R
SWEEP|LONDON|tf1|{"L": 8, "bracket": "struct", "nb": 3, "s": 3, "tf": 1}|none|STR|S
SWEEP|NYAM|tf-10|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -10, "tmode": "SO", "typ": "A"}|none|B60/60|R
SWEEP|NYAM|tf-10|{"L": 8, "bracket": "struct", "nb": 1, "s": 3, "tf": -10}|none|STR|S
SWEEP|NYAM|tf-15|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -15, "tmode": "SO", "typ": "A"}|none|B40/40|R
SWEEP|NYAM|tf-15|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -15, "tmode": "SO", "typ": "A"}|none|B60/60|R
SWEEP|NYAM|tf-5|{"L": 8, "bracket": "struct", "nb": 3, "s": 3, "tf": -5}|none|B20/20|R
SWEEP|NYAM|tf-9500|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -9500, "tmode": "SO", "typ": "A"}|none|B60/60|R
SWEEP|NYAM|tf1|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 1, "tmode": "SO", "typ": "A"}|none|B20/20|R
SWEEP|NYAM|tf1|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 1, "tmode": "SO", "typ": "A"}|none|B30/30|R
SWEEP|NYAM|tf2|{"L": 3, "box": "on", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "A"}|none|B20/20|S
SWEEP|NYAM|tf2|{"L": 3, "box": "prior", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "A"}|none|B50/50|R
SWEEP|NYPM|tf-9500|{"L": 8, "bracket": "struct", "nb": 1, "s": 1, "tf": -9500}|none|B20/20|R
SWEEP|NYPM|tf-9500|{"L": 8, "bracket": "struct", "nb": 1, "s": 1, "tf": -9500}|none|B60/60|R
SWEEP|NYPM|tf-9500|{"L": 8, "bracket": "struct", "nb": 3, "s": 1, "tf": -9500}|none|B20/20|R
SWEEP|NYPM|tf-9500|{"L": 8, "bracket": "struct", "nb": 3, "s": 3, "tf": -9500}|none|B20/20|R
SWEEP|NYPM|tf1|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 1, "tmode": "SO", "typ": "A"}|none|B20/20|R
SWEEP|NYPM|tf1|{"L": 8, "bracket": "struct", "nb": 1, "s": 1, "tf": 1}|none|B40/40|R
SWEEP|NYPM|tf2|{"L": 3, "box": "N12", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": 2, "tmode": "SO", "typ": "A"}|none|B20/20|R
SWEEP|NYPM|tf2|{"L": 3, "bracket": "struct", "nb": 3, "s": 1, "tf": 2}|none|B20/20|R
SWEEP|NYPM|tf2|{"L": 3, "bracket": "struct", "nb": 3, "s": 3, "tf": 2}|none|B20/20|R
SWEEP|NYPM|tf2|{"L": 8, "bracket": "struct", "nb": 3, "s": 1, "tf": 2}|none|B40/40|R
SWEEP|PRE|tf-30|{"L": 3, "box": "dev", "buf": 1, "nb": 3, "par": 15, "s": 1, "tf": -30, "tmode": "SO", "typ": "A"}|none|STR|R
SWEEP|PRE|tf-30|{"L": 5, "bracket": "struct", "nb": 1, "s": 3, "tf": -30}|none|STR|S
SWEEP|PRE|tf-30|{"L": 5, "bracket": "struct", "nb": 3, "s": 1, "tf": -30}|none|STR|R
SWEEP|PRE|tf-30|{"L": 5, "bracket": "struct", "nb": 3, "s": 3, "tf": -30}|none|B60/60|R
SWEEP|PRE|tf-30|{"L": 5, "bracket": "struct", "nb": 3, "s": 3, "tf": -30}|none|STR|S
SWEEP|PRE|tf-9500|{"L": 5, "bracket": "struct", "nb": 1, "s": 1, "tf": -9500}|none|B30/30|R
SWEEP|PRE|tf1|{"L": 3, "bracket": "struct", "nb": 3, "s": 1, "tf": 1}|none|STR|S
SWEEP|PRE|tf1|{"L": 8, "bracket": "struct", "nb": 1, "s": 1, "tf": 1}|none|B40/40|R
SWEEP|PRE|tf1|{"L": 8, "bracket": "struct", "nb": 3, "s": 1, "tf": 1}|none|B40/40|R
SWEEP|PRE|tf1|{"L": 8, "bracket": "struct", "nb": 3, "s": 3, "tf": 1}|none|B40/40|R
