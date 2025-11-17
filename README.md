# Analyzing Tesla and GameStop Stock Revenue Trends with Python Web-Scraping and Dashboards

## Project Overview

This project uses Python to analyse the stock price and revenue trends of two companies: **TSLA** (Tesla) and **GME** (GameStop).
It retrieves historical stock data using the `yfinance` library, scrapes quarterly revenue data from public web sources, cleans and prepares the datasets, and then creates visualisations (using Plotly) that compare stock price movements with revenue over time.

## Technologies Used

- Python
- `yfinance` (for downloading stock price history)
- `requests` + `BeautifulSoup` (for web-scraping revenue data)
- `pandas` (for data manipulation and cleaning)
- `plotly.graph_objects` and `plotly.subplots` (for interactive visualisations)
- Jupyter Notebook (the code is provided as a `.ipynb` file)

## File Structure

- `Final Assignment.ipynb` — the Jupyter Notebook containing all code, analysis & visualisations.
- (Other supporting files or data extracts may exist depending on updates.)

## Steps / Workflow

1. **Import Required Libraries**

   ```python
   import yfinance as yf
   import pandas as pd
   import requests
   from bs4 import BeautifulSoup
   import plotly.graph_objects as go
   from plotly.subplots import make_subplots
   ```

2. **Extract Stock Data**

   - Use `yf.Ticker("TSLA")` and `yf.Ticker("GME")` to get stock data objects.
   - Use `.history(period="max")` (or a defined interval) to fetch available historical data.
   - Reset index so “Date” becomes a column—makes plotting easier.

3. **Scrape Quarterly Revenue Data**

   - For Tesla: scrape from a site like MacroTrends (e.g., “tesla/revenue”).
   - For GameStop: scrape from an appropriate public source listing quarterly revenue.
   - Use `pandas.read_html()` or `BeautifulSoup` to parse HTML tables.
   - Clean the data: remove commas, dollar signs; drop rows with missing values.

4. **Clean & Prepare Data**

   - Convert “Date” strings to `datetime` objects.
   - Convert revenue values to numeric type (after stripping symbols).
   - Align or restrict time ranges if needed (e.g., only overlap where both stock & revenue exist).

5. **Visualisation / Dashboard**

   - Define a function (e.g., `make_graph(stock_data, revenue_data, stock_name)`) that:

     - Creates a two-row subplot: top row for share price, bottom row for revenue.
     - Shares x-axis to view trends over time.
     - Adds Plotly `Scatter` traces for the price and for revenue.
     - Sets axis titles (e.g., “Price (US$)” vs “Revenue (US$ Millions)”).
     - Enables a date range slider for the x-axis for interactive zooming.

   - Call this function separately for Tesla and GameStop to produce side-by-side dashboards.
   - Inspect trends: how revenue growth correlates (or doesn’t) with stock price movements.

## Usage

To use this project:

1. Clone or download the repository.
2. Install required Python packages:

   ```bash
   pip install yfinance pandas requests beautifulsoup4 plotly
   ```

3. Open `Final Assignment.ipynb` in Jupyter (or VSCode Notebook, Google Colab, etc.).
4. Run through cells in order, from data extraction → cleaning → visualization.
5. Explore the dashboards/plots to compare stock price vs revenue trends for TSLA and GME.

## Insights & Observations

- This analysis gives you a visual comparison of how a company’s **revenue momentum** aligns with its **stock market performance**.
- For example, you might observe periods where revenue steadily increases while the stock price remains volatile — this can spark questions about investor sentiment, external market factors, or valuation mismatches.
- Useful for educational purposes: beginners in data science, finance students, analysts wanting to marry fundamental data with market behaviour.

## Limitations & Notes

- The revenue data is scraped from publicly available sources; completeness and accuracy depend on that source’s formatting and availability.
- Stock history may cover many years, but revenue data may be limited to fewer quarters — alignment may thus exclude earlier periods.
- The analysis is **exploratory** — it does _not_ establish causality between revenue trends and stock price. Use caution if interpreting results for investment decisions.
- Web-scraping is subject to the target site’s structure; if layouts change, scraping may require updates.
- Please check for any licensing or usage restrictions on scraped data.

## About the Author / Contributor

**Sayad Uddin Tahsin** (GitHub username: `sayad1711`) is a passionate software developer specializing in Python. With a focus on building data-driven applications and visualisations, Sayad brings together web-scraping, data processing, and dashboard creation to make financial and business insights accessible. If you appreciate this work and want to explore more of his projects, check his GitHub profile: [GitHub → Sayad-Uddin-Tahsin](https://github.com/Sayad-Uddin-Tahsin) ([github.com][1])

## License & Credits

This repository is intended for educational and demonstration purposes. Please review the repository files for any LICENSE information before reuse or distribution.
