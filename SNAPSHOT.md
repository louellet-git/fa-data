# Snapshot

The date that each data set was downloaded from its source.

| Data | Tickers or files | Date of the download |
|---|---|---|
| SEC company facts | 1,249 tickers | 2026-11-19 |
| SEC list of earnings reports, SIC code and its description | 1,249 tickers (ARCC and PDI have no SIC code at the SEC) | 2026-11-20 |
| 10-K filing files | 126 tickers | 2026-11-19 |
| Daily prices, `sp500.txt` and SPY | 505 tickers, 10 years | 2026-11-19 |
| Daily prices, `next500.txt` | 494 of 500 tickers, 10 years or the full history; the Nasdaq site does not have CFR, DDS, ET, MOG-A, SUN | 2026-11-20 |
| Estimates, price targets, earnings dates | 503 tickers | 2026-11-19 |
| Option chain copies | IBM, JNJ (2026-11-19); SPX and SPXW with bid and ask (Alpaca, indicative feed, 32,046 quotes) | 2026-11-20 |
| Rate curves (GSW, Treasury), CPI | `rates/` | 2026-11-19 |
| Corporate bond series (FRED) | `bonds/`, 26 series | 2026-11-20 |
| Bars of the option bots | `trading/` | 2026-11-19 |
| Treasury daily bill rates | `rates/treasury_bill_rates_2026.csv` | 2026-11-20 |
| FedInvest end-of-day Treasury prices | `prices/fedinvest_<date>.csv`: 58 days, 2026-08-27 to 2026-11-19 (no prices on the bond holidays 2026-10-12 and 2026-11-11) | 2026-11-20 |
| Futures: Cboe VX settlements, CFTC positions (12 roots), Atlanta Fed policy path | `futures/` (the Yahoo futures series are not in it: Yahoo answers 429 to the cloud) | 2026-11-20 |
| Cboe VIX history | `vix/VIX_History.csv` | 2026-11-20 |
