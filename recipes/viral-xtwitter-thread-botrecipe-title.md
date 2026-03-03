---
title: Viral X/Twitter Thread Bot
description: Generate a viral 5-part X thread using live web search + gpt-4o.
hidden: true
recipe:
  color: '#018FF4'
  icon: 🐦
---
```python Python
import os
import requests
from openai import OpenAI

API_KEY = os.environ.get("AISA_API_KEY")
LLM_BASE_URL = "https://api.aisa.one/v1"
API_BASE_URL = "https://api.aisa.one/apis/v1"

client = OpenAI(api_key=API_KEY, base_url=LLM_BASE_URL)

HEADERS = {
    "Authorization": f"Bearer {API_KEY}",
    "Content-Type": "application/json",
    }

def search_web(query, max_results=5):
    resp = requests.post(
        f"{API_BASE_URL}/tavily/search",
        headers=HEADERS,
        json={
            "query": query,
            "search_depth": "advanced",
            "max_results": max_results,
            "include_answer": True,
        },
    )
    return resp.json()
    
def generate_viral_thread(topic):
    results = search_web(f"latest news {topic} interesting facts", max_results=5)
    sources = results.get("results", [])

    context = ""
    for s in sources:
        context += f"Fact: {s.get('title', '')} - {s.get('content', '')}\n"

    prompt = f"""You are a master X ghostwriter...

### SOURCE MATERIAL
{context}

### INSTRUCTIONS
- Write exactly 5 tweets
- Tweet 1 must be a scroll-stopping hook
- Tweets 2–4 deliver insights
- Tweet 5 strong CTA
- Separate tweets with "---"
"""
    
    response = client.chat.completions.create(
        model="gpt-4o",
        messages=[{"role": "user", "content": prompt}],
    )

    print(response.choices[0].message.content)

if __name__ == "__main__":
    generate_viral_thread("Artificial Intelligence in Healthcare")
```

# Initialize API Clients

<!-- python@1-14 -->



# Search the Web for Fresh Context

<!-- python@16-27 -->



# Generate a Viral Thread

<!-- python@29-48 -->



# Run GPT-4o

<!-- python@50-58 -->

