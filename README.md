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

| Data | Files | Source | Terms |
|---|---|---|---|
| SEC company facts | `<TICKER>/company_facts.json.gz` | SEC EDGAR | Public data of the United States government |
| SEC list of earnings reports | `<TICKER>/sec_8k_earnings.json` | SEC EDGAR | Public data of the United States government |
| Rate curve (GSW) | `rates/gsw_feds200628.csv` | Federal Reserve Board | Public data |

The dates of the data are in `SNAPSHOT.md`.

## Traps

- A clone gives each file the time of the clone. Thus `fa sync --status` shows the data
  as new. The real date of the data is in `SNAPSHOT.md`.
- Files that a command writes in `data/raw` on your machine are not in this repo. Do not
  push from your machine.
