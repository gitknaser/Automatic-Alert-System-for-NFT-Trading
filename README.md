# Automatic Alert System for NFT Trading
 
## Overview
 
A Python-based automated pipeline that scrapes upcoming Solana NFT drops from [HowRare.is](https://howrare.is/drops), filters projects by Twitter community size (10K+ followers), and sends real-time price alerts via a Telegram bot when a collection's floor price crosses a user-defined threshold.
 
Built as a personal project to explore web scraping, API integration, and automation with Python.
 
---
 
## Features
 
- **NFT project scraper** — Collects upcoming Solana NFT drops from HowRare.is, including project name, mint price, and supply
- **Community filter** — Automatically retrieves the Twitter follower count for each project and filters those with 10,000+ followers
- **CSV export** — Outputs two structured datasets: all scraped projects, and filtered high-community projects only
- **Real-time price monitoring** — Queries the Magic Eden API to track floor price fluctuations for a chosen collection
- **Telegram alerts** — Sends instant notifications via a Telegram bot when the price hits the configured threshold
---
 
## Technologies Used
 
- **Python 3**
- **BeautifulSoup4** — HTML parsing and web scraping
- **Requests** — HTTP requests
- **Telegram Bot API** — Automated messaging
- **Magic Eden API (Solana v2)** — NFT collection floor price data
- **CSV** — Structured data export
---
 
## Project Architecture
 
```
HowRare.is (scraping)
        │
        ▼
Project data extraction (name, price, supply, Twitter handle)
        │
        ▼
Twitter follower count retrieval
        │
        ▼
Filtering: projects with 10K+ followers
        │
        ▼
CSV export (all projects + filtered projects)
        │
        ▼
User selects a collection → Magic Eden API monitors floor price
        │
        ▼
Telegram bot sends alert when threshold is reached
```
 
---
 
## Installation
 
1. Clone the repository:
    ```bash
    git clone https://github.com/gitknaser/Automatic-Alert-System-for-NFT-Trading.git
    cd Automatic-Alert-System-for-NFT-Trading
    ```
 
2. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```
 
3. Configure your credentials in `config.py` (see below):
    ```python
    BOT_KEY = "your_telegram_bot_token"
    CHAT_ID  = "your_telegram_chat_id"
    ```
 
4. Run the script:
    ```bash
    python script.py
    ```
 
---
 
## Configuration
 
Before running, create a `config.py` file with your own credentials:
 
```python
# config.py
BOT_KEY = "your_telegram_bot_token_here"
CHAT_ID  = "your_telegram_chat_id_here"
PRICE_LIMIT = 42       # Alert threshold in SOL
TIME_INTERVAL = 5      # Check interval in seconds
```
 
To get a Telegram bot token, create a bot via [@BotFather](https://core.telegram.org/bots#botfather) on Telegram.
 
---
 
## ⚠️ Known Limitations
 
This project was built in 2023. Some components may no longer work as-is due to external changes:
 
- **Twitter follower scraping (via Bing)** — No longer functional. Twitter blocked public scraping in 2023 and Bing's HTML structure has changed. The script handles this gracefully by leaving the field empty.
- **Magic Eden API v2** — Still operational as of early 2026 but Magic Eden has announced platform changes. The endpoint may become unreliable.
Despite these limitations, the core logic (scraping, filtering, CSV export, and Telegram alerting) remains valid as a demonstration of the pipeline architecture.
 
---
 
## Skills Demonstrated
 
- Web scraping with BeautifulSoup and Requests
- REST API integration (Magic Eden, Telegram)
- Data filtering and CSV pipeline
- Bot automation with the Telegram Bot API
- Error handling with nested try/except blocks
---
 
## License
 
MIT
