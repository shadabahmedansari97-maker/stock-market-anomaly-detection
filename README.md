# Stock Market Anomaly Detection

## Overview
This project detects unusual/anomalous days in the stock market using daily price and volume data.
It uses rule based detection, K-Means clustering and DBSCAN clustering to flag weird market days.
This is for educational purposes only — not investment advice.

## Dataset
- Source : https://www.kaggle.com/datasets/jacksoncrow/stock-market-dataset
- Daily OHLCV data ending April 2020
- Columns : Date, Open, High, Low, Close, Adj Close, Volume

## Tickers Used
- QQQ (ETF — tracks top 100 NASDAQ stocks)
- AAPL, MSFT, AMZN, NVDA, GOOGL, TSLA, NFLX

## Methods Used
1. **Rule Based Detection** — flags days where ret_z, vol_z or range_pct cross thresholds
2. **K-Means Clustering** — flags days that are too far from their nearest cluster center
3. **DBSCAN Clustering** — flags days that are isolated with no nearby neighbors

## Train / Val / Test Split
- Train = 2018
- Validation = 2019
- Test = Jan-Mar 2020 (COVID crash period)

## Features
- **ret_z** — return z-score using rolling 63 days
- **vol_z** — volume z-score using rolling 21 days
- **range_pct** — intraday range percentile using rolling 63 days

## Output Files
- **outputs/anomaly_cards.csv** — per stock per day anomaly flags and types
- **outputs/market_days.csv** — per day market level stress indicators

## How To Run
1. Open Jupyter Notebook
2. Run all cells in order
3. For date query — run the date query cell and enter date in YYYY-MM-DD format
4. For monthly report — run the monthly report cell and enter month in YYYY-MM format

## Results
- Flag rate kept between 2-8% across all splits
- COVID crash in Feb-March 2020 successfully detected by all 3 methods