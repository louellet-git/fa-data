# Philadelphia Fed Survey of Professional Forecasters (SPF)

- File: `medianLevel_<download date>.xlsx` (median levels of all variables) and
  `spf-release-dates_<download date>.txt` (the release date of each survey), with a `.meta.json`
  for each (address, date, bytes, SHA-256).
- Source: Federal Reserve Bank of Philadelphia, Real-Time Data Research Center, SPF
  (philadelphiafed.org). Cite: "Survey of Professional Forecasters, Federal Reserve Bank of Philadelphia".
- Terms: the site has no terms page; the footer says "All rights reserved". The owner decided on
  2026-11-21 to keep a private copy only, with only results in the public repo.
- Not a vintage file: a later download can revise old values. Each download keeps its date.
- Command: `fa spf get --cache data/raw`; `fa spf show --cache data/raw`.
