---
title: Crypto Sentiment Trader
description: Build an automated crypto trading agent using AIsa Financial APIs and gpt-4o.
hidden: false
recipe:
  color: '#018FF4'
  icon: 📈
---
```python Python
import os
import requests
from openai import OpenAI

API_KEY = os.getenv("AISA_API_KEY")

LLM_BASE_URL = "https://api.aisa.one/v1"
API_BASE_URL = "https://api.aisa.one/apis/v1"

client = OpenAI(api_key=API_KEY, base_url=LLM_BASE_URL)
HEADERS = {"Authorization": f"Bearer {API_KEY}"}

price_resp = requests.get(
    f"{API_BASE_URL}/financial/crypto/prices/snapshot",
    headers=HEADERS,
    params={"ticker": ticker}
)

price_data = price_resp.json()

news_resp = requests.get(
    f"{API_BASE_URL}/financial/news",
    headers=HEADERS,
    params={"ticker": ticker, "limit": 5}
)

news_data = news_resp.json().get("news", [])

news_context = ""
for n in news_data[:5]:
    title = n.get("title", "Headline")
    snippet = n.get("snippet", "No details.")
    news_context += f"- {title}: {snippet}\n"

if __name__ == "__main__":
    execute_crypto_trade("BTC")
```

# Configure the Environment

<!-- python@1-11 -->

We’ll set up authentication and base URLs for both the LLM Gateway and Financial APIs.

# Fetch Real-Time Crypto Prices

<!-- python@13-19 -->

Call the crypto snapshot endpoint to retrieve live market data.

# Fetch Breaking News

<!-- python@21-27 -->

Retrieve recent headlines related to the ticker.

# Format Context for the LLM

<!-- python@29-33 -->

We prepare structured market + news input for GPT-4o.

# Execute the Agent

<!-- python@35-36 -->