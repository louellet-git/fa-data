# fa-data

The one data store of the repo `louellet-git/FinancialAnalysis`. It contains a copy of
the data cache (`data/raw`), so that each session gets the data with one command and
sends no request to the sources.

## Rules

1. Only the Head of Technology writes this repo. A different head asks that head for
   new data.
2. Do not start a bulk download from the sources. Get the data from this repo.
3. The layout is the layout of `data/raw`. The `fa` and `mapcheck` commands read it with
   no change.
4. No key and no secret is in this repo.

## How to get the data

In a cloud session, attach the repo first (the tool `add_repo`, owner `louellet-git`,
repo `fa-data`, read access). Then, in the folder of the main repo:

```bash
git clone --depth 1 https://github.com/louellet-git/fa-data data/raw
```

The folder `data/raw` must not exist or must be empty. If it has files, move it first.
To get a newer copy later:

```bash
git -C data/raw pull --depth 1
```

## What is in it

| Data | Files | Source |
|---|---|---|
| SEC company facts | `<TICKER>/company_facts.json.gz` | SEC EDGAR |
| SEC list of earnings reports, SIC code (read with `mapcheck::sec::company_sic`) | `<TICKER>/sec_8k_earnings.json` | SEC EDGAR |
| 10-K filing files | `<TICKER>/filings/` | SEC EDGAR |
| SEC ticker list | `_sec/company_tickers.json` | SEC EDGAR |
| Daily prices | `<TICKER>/prices.json`, `<TICKER>/prices.meta.json` (the source of each file) | Nasdaq site; some files from Yahoo |
| Estimates, price targets, surprises, earnings dates | `<TICKER>/estimates/`, `<TICKER>/earnings_dates.json`, `_calendar/` | Nasdaq site |
| Option chain copies | `<TICKER>/options/` | Cboe delayed quotes |
| Rate curves, inflation, daily bill rates | `rates/` | Federal Reserve Board (GSW), Treasury, BLS |
| FedInvest end-of-day Treasury prices | `prices/` | TreasuryDirect (FedInvest) |
| Futures and the VIX history | `futures/`, `vix/` | Cboe, CFTC, Atlanta Fed |
| Corporate bond series | `bonds/` | FRED |
| Bars of the option bots | `trading/` | Yahoo |
| FRED monthly series: the 3-month bill (from 1934) and the NBER commercial paper rate (1857-1971) | `macro/fred/` | FRED (Federal Reserve Bank of St. Louis), with the citation of each series |
| Shiller monthly stock market data (price, dividends, earnings, CPI, long rate, CAPE, from 1871) | `macro/shiller/` | shillerdata.com (Robert J. Shiller) |

The dates of the data and the number of tickers are in `SNAPSHOT.md`.

The SEC, Federal Reserve, Treasury and BLS data are public data of the United States
government. The price, estimate and option data come from sites that have their own terms
of use. The owner decided on 2026-11-20 that this repo is public for now. If a source
asks, the owner makes the repo private or removes that data.

## How the Head of Technology updates the store

1. On one machine with the main repo built, bring the cache up to date: `fa sync` for the
   data sets, or `fa prices get --tickers-file <list> --source nasdaq` for the prices. A
   ticker that has a price file gets only the new days.
2. Copy the changed files from `data/raw` into the clone of this repo. Do not copy
   `company_facts.json` when `company_facts.json.gz` exists.
3. Scan the new files for a key or a token before the push.
4. Change the dates in `SNAPSHOT.md`.
5. Commit and push in parts: less than 40 MB for compressed files, less than 70 MB for
   text files.
6. Tell the other heads that a newer copy is available.

Git keeps each old version. When this repo is larger than about 1 GB, the owner decides
if it starts again from one commit.

## Traps

- A clone gives each file the time of the clone. Thus `fa sync --status` shows the data
  as new. The real date of the data is in `SNAPSHOT.md`.
- Files that a command writes in `data/raw` on your machine are not in this repo. Do not
  push from your machine.
