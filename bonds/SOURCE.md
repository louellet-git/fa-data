# Bonds

- `treasury_hqm/`: the U.S. Treasury HQM corporate curve (public domain). `fa bonds` reads it.
- The FRED copies of the ICE BofA indexes, the Moody's yields and the HQM series were removed on
  2026-11-21. The terms of FRED, ICE and Moody's do not permit a stored copy, and no code reads them
  now (the cost of debt is HQM + a Damodaran step: `docs/models/cost-of-debt.md` of the main repo).
