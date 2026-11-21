# Shiller U.S. stock market data

- File: `ie_data.xls`, downloaded 2026-11-21 from https://shillerdata.com/ (link "ie_data (xls)"). The file was last
  saved on 2026-11-16 (file properties).
- Content: monthly S&P composite price, dividends, earnings, CPI, the long interest rate and CAPE, from 1871.
- Source: Robert J. Shiller, the data of "Irrational Exuberance" and "Market Volatility", as updated.
- Terms: the page offers the file for download and states no license. Its disclaimer: "The user of this information
  assumes the entire risk of any use made of the information provided herein." If the author asks, this copy is removed.
- Cite as: Robert J. Shiller, U.S. stock market data, https://shillerdata.com/.

## `shiller_monthly.csv` (made from `ie_data.xls`, sheet "Data")
- One row a month, 1871-01 to 2026-11. Columns: `month` (YYYY-MM), `price` (P, nominal S&P composite), `dividend` (D,
  annual rate), `earnings` (E, annual rate), `cpi`, `gs10` (percent), `cape` (empty where the sheet has NA),
  `estimate` (true for the months that the note line below the table names), `note` (that line).
- Raw values only: no fill, no real values. The columns were agreed with the Head of Economics and the Head of
  Fundamental Research (2026-11-21).
- Trap: the sheet keeps the date as a decimal number, so "2026.1" is October. The conversion reads the digits after
  the point as the month ("1" is "10").
- How it was made: `soffice --headless --convert-to csv` for each sheet, then a one-time script that keeps the eight
  columns (it is not in the repo). The latest rows have no dividend and no earnings yet.
