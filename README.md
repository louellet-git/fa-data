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
| SEC list of earnings reports | `<TICKER>/sec_8k_earnings.json` | SEC EDGAR |
| 10-K filing files | `<TICKER>/filings/` | SEC EDGAR |
| SEC ticker list | `_sec/company_tickers.json` | SEC EDGAR |
| Daily prices | `<TICKER>/prices.json`, `<TICKER>/prices.meta.json` (the source of each file) | Nasdaq site; some files from Yahoo |
| Estimates, price targets, surprises, earnings dates | `<TICKER>/estimates/`, `<TICKER>/earnings_dates.json`, `_calendar/` | Nasdaq site |
| Option chain copies | `<TICKER>/options/` | Cboe delayed quotes |
| Rate curves and inflation | `rates/` | Federal Reserve Board (GSW), Treasury, BLS |
| Corporate bond series | `bonds/` | FRED |
| Bars of the option bots | `trading/` | Yahoo |

The dates of the data and the number of tickers are in `SNAPSHOT.md`.

The SEC, Federal Reserve, Treasury and BLS data are public data of the United States
government. The price, estimate and option data come from sites that have their own terms
of use. The owner decided on 2026-11-20 that this repo is public for now. If a source
asks, the owner makes the repo private or removes that data.

## Traps

- A clone gives each file the time of the clone. Thus `fa sync --status` shows the data
  as new. The real date of the data is in `SNAPSHOT.md`.
- Files that a command writes in `data/raw` on your machine are not in this repo. Do not
  push from your machine.
