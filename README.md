This project demonstrates web scraping of non-COVID-19 data from publicly available websites. The aim is to collect, clean, analyze, and visualize data to generate actionable insights. The project emphasizes modular, reusable code for scraping, data preprocessing, and visualization.
The project is ideal for anyone learning Python for data extraction and analysis.

Features

Scrape data from static and dynamic websites.
Extract and parse HTML using BeautifulSoup.
Handle HTTP requests using requests.
Store data in CSV and JSON formats.
Clean and preprocess raw data using pandas.
Visualize trends and patterns with matplotlib and seaborn.
Modular scripts for easy customization and reuse.



Key Libraries & Their Roles
1. Requests
Purpose: Fetch HTML content from websites.
Handles HTTP GET/POST requests, headers, cookies, and session management.

Example:

import requests

url = "https://example.com/products"
headers = {"User-Agent": "Mozilla/5.0"}
response = requests.get(url, headers=headers)

if response.status_code == 200:
    html_content = response.text
else:
    print("Failed to retrieve data")


Best Practices:
Use headers to mimic browser requests.
Implement retries and exception handling.
Respect server rate limits.


2. BeautifulSoup
Purpose: Parse HTML content and extract information.
Key Functions: find(), find_all(), select(), get_text().

Example:
from bs4 import BeautifulSoup
soup = BeautifulSoup(html_content, "html.parser")
titles = soup.find_all("h2", class_="product-title")

for t in titles:
    print(t.get_text(strip=True))


Supports CSS selectors, tags, attributes, and nested extraction.



3. Pandas
Purpose: Clean, transform, and structure scraped data.
Handles missing values, duplicates, type conversions, and filtering.

Example:

import pandas as pd
data = [{"title": "Product A", "price": "$100"},
        {"title": "Product B", "price": "$200"}]

df = pd.DataFrame(data)
df['price'] = df['price'].str.replace('$','').astype(float)
df.drop_duplicates(inplace=True)
df.to_csv("data/products.csv", index=False)

Enables ready-to-use datasets for analysis and visualization.

4. Visualization (Matplotlib & Seaborn)
Purpose: Visualize trends, patterns, and insights from scraped data.

Example:

import matplotlib.pyplot as plt
import seaborn as sns

sns.barplot(x="title", y="price", data=df)
plt.title("Product Prices")
plt.xlabel("Product")
plt.ylabel("Price ($)")
plt.show()


Helps identify top products, trends, or outliers visually.

Project Structure
web-scraping-non-covid/
│
├── data/                     # CSV/JSON output files
├── scripts/                  # Python scripts
│   ├── scraper_static.py     # Scrape static websites using Requests & BS
│   ├── scraper_dynamic.py    # Scrape dynamic websites using Selenium
│   ├── data_cleaning.py      # Clean & preprocess scraped data
│   └── visualization.py      # Generate visualizations
├── README.md                 # P




Key Takeaways
Modular scraping for static and dynamic websites.
Clean and structured datasets ready for analysis.
Visualizations to gain actionable insights.
Easy to expand and adapt for other domains or websites.


GitHub: https://github.com/sai15235

LinkedIn: https://www.linkedin.com/in/saikiran-reddy-2b6842298

Email: saikiranr717@gmail.com


If you have any questions, suggestions, or want to collaborate, feel free to DM me or reach out via GitHub/LinkedIn. I’d be happy to help!
