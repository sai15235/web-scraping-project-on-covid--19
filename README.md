#  COVID-19 Global Data Scraper & Analyzer

A Python-based web scraping and data analysis project that extracts real-time COVID-19 statistics from [Worldometers](https://www.worldometers.info/coronavirus/) and produces country- and continent-level insights through data cleaning and visualizations.

---

##  Overview

This project demonstrates an end-to-end data pipeline:

1. **Scraping** — Fetches live HTML from Worldometers using `requests` with browser-mimicking headers
2. **Parsing** — Extracts the COVID-19 country table using `BeautifulSoup`
3. **Structuring** — Builds a `pandas` DataFrame with 22 columns and ~230 country rows
4. **Cleaning** — Removes commas from numeric strings, handles missing values, and drops summary/footer rows
5. **Analyzing** — Groups data by continent, filters by case thresholds, and computes descriptive statistics
6. **Visualizing** — Produces univariate and multivariate charts using `matplotlib` and `seaborn`

---

##  Dataset

Data is scraped live from `worldometers.info/coronavirus` and includes the following fields per country:

| Column | Description |
|---|---|
| `Country,Other` | Country or territory name |
| `TotalCases` | Cumulative confirmed cases |
| `TotalDeaths` | Cumulative deaths |
| `TotalRecovered` | Cumulative recoveries |
| `ActiveCases` | Currently active cases |
| `Serious,Critical` | Patients in serious/critical condition |
| `TotalTests` | Total tests conducted |
| `Population` | Country population |
| `Continent` | Continent classification |
| `Deaths/1M pop` | Deaths per million population |
| `Tot Cases/1M pop` | Cases per million population |
| … | + additional per-capita and ratio columns |

The scraped data is saved locally as `covid_data.csv`.

---

##  Visualizations

- **Histogram** — Distribution of total cases across countries
- **Bar Chart** — Top countries by total cases
- **Stacked Bar Chart** — Cases, deaths, and recoveries grouped by continent

---

##  Tech Stack

| Library | Purpose |
|---|---|
| `requests` | HTTP requests to fetch web pages |
| `BeautifulSoup` (`bs4`) | HTML parsing and table extraction |
| `pandas` | Data manipulation and CSV export |
| `matplotlib` | Base plotting |
| `seaborn` | Statistical visualizations |
| `re` | Regular expressions for text cleaning |

---

##  Getting Started

### Prerequisites

```bash
pip install requests beautifulsoup4 pandas matplotlib seaborn
```

### Run the Notebook

```bash
jupyter notebook web_scraping_final_project.ipynb
```

The notebook will:
1. Fetch the latest COVID-19 data from Worldometers
2. Parse and clean the HTML table
3. Save a `covid_data.csv` file in the working directory
4. Render all analysis and visualizations inline

---

##  Project Structure

```
├── web_scraping_final_project.ipynb   # Main notebook
├── covid_data.csv                     # Exported dataset (generated on run)
└── README.md
```

---

##  Notes

- The scraper sends a `User-Agent` header to avoid being blocked by the website's bot detection.
- Some columns (e.g., `NewCases`, `NewDeaths`) are sparsely populated because Worldometers only updates them during active reporting periods.
- Summary rows (World total, continent totals) are dropped during cleaning to keep only country-level records.

---

## 📄 License

This project is for educational purposes. Data belongs to [Worldometers](https://www.worldometers.info/coronavirus/).
