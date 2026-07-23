# Web Scraping Projects

A collection of Selenium-based web scrapers that collect data from IMDb and Wuzzuf, saving the results to CSV files for further analysis.

> **GitHub "About" description (one-liner):**
> Selenium web scrapers collecting IMDb anime & TV show ratings and Wuzzuf job listings, exported to CSV.

## Projects

### 1. Anime Scraper (`Anime.ipynb` → `anime.csv`)
Scrapes an IMDb anime list ([`ls057577566`](https://www.imdb.com/list/ls057577566)) and collects:

| Column  | Description                          |
|---------|---------------------------------------|
| `name`  | Anime title                           |
| `start` | Start year                            |
| `end`   | End year (same as start if one-shot)  |
| `type`  | Content rating (e.g. TV-14, TV-MA)    |
| `rate`  | IMDb rating                           |
| `votes` | Number of votes                       |

**Output:** 100 titles.

### 2. TV Shows Scraper (`ws_tvshows.ipynb` → `tv_showss.csv`)
Scrapes IMDb's [Top TV Shows chart](https://www.imdb.com/chart/toptv/) and collects:

| Column    | Description                     |
|-----------|----------------------------------|
| `ranking` | Position on the IMDb chart      |
| `name`    | Show title                      |
| `start`   | Start year                      |
| `end`     | End year (`Null` if still airing/unspecified) |
| `type`    | Content rating                  |
| `rate`    | IMDb rating                     |

**Output:** 250 shows.

### 3. Wuzzuf Job Scraper (`wuzzuf.ipynb` → `wuzzuf_jobs.csv`)
Searches [Wuzzuf](https://wuzzuf.net/jobs/egypt) for "Data Engineer" jobs in Egypt, paginating through results, and collects:

| Column     | Description                        |
|------------|--------------------------------------|
| `Title`    | Job title                            |
| `Company`  | Hiring company                       |
| `Location` | Job location                         |
| `Type`     | Employment type / work setting (e.g. Full Time, Hybrid) |

**Output:** 556 job listings.

## Tech Stack

- **Python 3**
- **Selenium** – browser automation (Edge WebDriver)
- **pandas** – data storage and export to CSV

## Setup

1. Install dependencies:
   ```bash
   pip install selenium pandas
   ```
2. Download [Microsoft Edge WebDriver](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/) matching your installed Edge version, and make sure it's on your system `PATH`.
3. Open the desired notebook (`Anime.ipynb`, `ws_tvshows.ipynb`, or `wuzzuf.ipynb`) in Jupyter and run all cells.

## Repository Structure

```
web-scrapping/
├── Anime/
│   ├── Anime.ipynb       # IMDb anime list scraper
│   └── anime.csv         # Scraped anime data
├── Tv_shows/
│   ├── ws_tvshows.ipynb  # IMDb top TV shows scraper
│   └── tv_showss.csv     # Scraped TV show data
├── wuzzuf/
│   ├── wuzzuf.ipynb      # Wuzzuf job listings scraper
│   └── wuzzuf_jobs.csv   # Scraped job listing data
└── README.md
```

## Notes

- These scripts use Selenium to render JavaScript-heavy pages, so a working Edge browser + matching WebDriver is required.
- CSS selectors and class names are tied to the sites' current layout (as of scraping time) and may need updating if IMDb or Wuzzuf changes their page structure.
- Scraped data is provided for personal/educational analysis; please review the target sites' terms of service before reusing these scripts.

## License

This project is open source and available under the [MIT License](LICENSE).
