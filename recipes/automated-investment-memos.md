---
title: Automated Investment Memos
description: Generate Wall Street-style investment memos using live financial data.
hidden: false
recipe:
  color: '#018FF4'
  icon: 💸
---
```python Python
import os
import requests
from openai import OpenAI

API_KEY = os.getenv("AISA_API_KEY")
LLM_BASE_URL = "https://api.aisa.one/v1"
DATA_BASE_URL = "https://api.aisa.one/apis/v1/financial"

client = OpenAI(api_key=API_KEY, base_url=LLM_BASE_URL)

def get_data(endpoint: str, params=None):
    headers = {"Authorization": f"Bearer {API_KEY}"}
    resp = requests.get(f"{DATA_BASE_URL}{endpoint}", headers=headers, params=params)
    return resp.json()

metrics = get_data("/financial-metrics/snapshot", {"ticker": ticker})
pr_resp = get_data("/earnings/press-releases", {"ticker": ticker, "limit": 1})
news_resp = get_data("/news", {"ticker": ticker, "limit": 5})

market_cap = metrics.get("market_cap", "N/A")
pe_ratio = metrics.get("pe_ratio", "N/A")

prompt = f"""
Act as a senior Wall Street Analyst...

### DATA
- Market Cap: {market_cap}
- P/E Ratio: {pe_ratio}

### OUTPUT FORMAT
# Investment Memo: {ticker}
## Valuation Verdict
## Bull Case
## Bear Case
## Final Recommendation
"""

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": prompt}],
)

print(response.choices[0].message.content)
```

# Setup Financial Data Access

<!-- python@1-14 -->



# Fetch Financial Data

<!-- python@16-18 -->



# Extract Key Metrics

<!-- python@20-21 -->



# Generate Investment Memo

<!-- python@23-43 -->

