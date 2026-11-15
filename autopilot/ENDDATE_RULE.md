# ENDDATE RULE (user order, T-RECENTS item 0): every page verdict line states the data end date.
After each page rebuild run:
  python3 code/th_recents/stamp_enddate.py <page.md> <YYYY-MM-DD of your last data day>
or in python: sys.path.insert(0,'code/th_recents'); from stamp_enddate import stamp; stamp(path,'2026-10-30')
Idempotent; needs a VERDICT line in the first 60 lines. Audit: ENDDATE_AUDIT.csv (hourly). Engine runs currently end 2026-10-30.
