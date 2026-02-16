---
title: Marketplace
deprecated: false
hidden: false
metadata:
  robots: index
---
AISA uses a usage-based billing system. Charges are applied based on the type of API you use.

There are two distinct pricing models:

1. **AI Model (LLM) Pricing:** billed per token
2. **Per-Call API Pricing:** billed per request

This page provides a high-level overview of both models and links to their detailed pricing pages.

## **1. AI Model (LLM) Pricing**

AI model APIs are billed based on token usage.

![](https://files.readme.io/8975f2d6f9f0ea4e8d62ea652886ff880f51286be7ea0d75408e439c76a27e1f-image.png)

Each request is charged separately for:

* **Input tokens** (prompt tokens)
* **Output tokens** (generated tokens)

Prices are defined per **1 million tokens (1M tokens)**, and input and output tokens are billed independently.

This pricing model applies to:

* Chat completions
* Text generation
* Vision-enabled models
* Tool-enabled models
* Streaming responses

For the full model pricing table and detailed billing explanation, see **AI Model Pricing**

## **2. Per-Call API Pricing**

All non-LLM APIs use a fixed per-request billing model.

![](https://files.readme.io/a991d244f6416f6b1e5b39782769957cf4a9b4ed6c63451ee885aa239b4dc6ae-image.png)

Each successful request to an endpoint incurs a predefined charge, regardless of response size.

This pricing model applies to APIs such as:

* Search APIs
* Financial APIs
* YouTube APIs
* Scholar APIs
* Twitter APIs
* Other structured data and retrieval services

For endpoint-level pricing details and billing behavior, see **Per-Call API Pricing**

## **Choosing the Correct Pricing Model**

If your API request:

* Uses a language model to generate text → **Token-based pricing applies**
* Retrieves structured data or performs a search → **Per-call pricing applies**

The Marketplace displays the billing type for each model or endpoint.

## **Usage Tracking and Transparency**

All API activity, whether token-based or per-call, is recorded in:

* **Usage Logs**
* Account billing summaries

You can review:

* Tokens consumed (for AI models)
* Number of requests (for per-call APIs)
* Final cost per request
* Applied pricing rules or group ratios

Charges are deducted from your account balance based on the applicable pricing model.

## **Additional Notes**

* Pricing is usage-based; no fixed monthly platform fees.
* Pricing may vary by model, provider, group, or endpoint.
* Always refer to the Marketplace for the most up-to-date rates.
* Detailed billing breakdowns are available in Usage Logs.