# U.S. Treasury HQM corporate bond yield curve (spot rates)

- Files: `hqm_<yy>_<yy>.xls`, one for each 5 years from 1984; `meta.json` (address, fetch date, size).
- Source: U.S. Department of the Treasury, "Treasury Coupon Issues and Corporate Bond Yield Curve",
  home.treasury.gov/data/treasury-coupon-issues-and-corporate-bond-yield-curve/corporate-bond-yield-curve.
  A U.S. government work (public domain).
- Monthly averages. A month is used only from the first weekday after the 5th of the next month
  (`hqm_24_28.xls` with October 2026 had Last-Modified 2026-11-04; see A-203).
- Command: `fa bonds hqm get --cache data/raw` (also in `fa sync`, key `hqm`).
