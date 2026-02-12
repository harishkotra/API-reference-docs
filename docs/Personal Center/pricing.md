---
title: Pricing
deprecated: false
hidden: false
metadata:
  robots: index
---
AISA provides two billing models depending on the type of API used:

1. **LLM Inference APIs:** billed per token

![][image1]

2. **Per-Call APIs:** billed per request

![][image2]

This page explains how each pricing model works and where to find live pricing information.

## **LLM Inference API Pricing**

LLM Inference APIs provide access to large language models from multiple providers through AISA’s unified interface.

### **Billing Unit**

LLM usage is billed based on:

* **Input tokens** (prompt tokens)
* **Output tokens** (completion tokens)

Prices are displayed per:

`1,000,000 tokens (1M tokens)`

Input and output tokens are billed separately.

### **Viewing Live Model Pricing**

All available models and their current pricing are listed in the **Marketplace**.

Each model displays:

* Input token price (per 1M tokens)
* Output token price (per 1M tokens)
* Billing type (typically Pay as you go)
* Supported API endpoint
* Supported capabilities (Tools, Vision, Files, Reasoning, etc.)

Model availability and pricing may change. Always refer to the Marketplace for the most up-to-date rates.

### **Group-Based Pricing**

Pricing may vary by workspace group.

Within a model’s detail panel, the **Group price** section shows:

* Group name
* Billing type
* Prompt (input) price
* Completion (output) price

If multiple groups are configured in your workspace, pricing may differ per group.

### **How LLM Cost Is Calculated**

![][image3]

For each request:

`Cost =`

`(Input tokens ÷ 1,000,000 × Input price)`

`+`

`(Output tokens ÷ 1,000,000 × Output price)`

If group ratios or pricing multipliers are configured, they are applied accordingly.

You can view the full billing breakdown for each request in the **Usage Logs** page.

### **What Is Covered Under LLM Pricing**

LLM pricing applies to:

* Chat completions
* Text generation
* Streaming responses
* Vision-enabled requests (if supported by the model)
* Tool-enabled requests (if supported)

All Playground and API key requests are billed under this model.

## **Per-Call API Pricing**

Per-Call APIs include all non-LLM endpoints available in the Marketplace, such as:

* Search APIs
* Financial APIs
* YouTube APIs
* Scholar APIs
* Twitter APIs
* Other structured data services

These APIs share the same pricing structure.

### **Billing Unit**

Per-Call APIs are billed:

`Per API request`

Each endpoint has a fixed cost per call.

Pricing is displayed in the format:

`$X.XXXXXX / per call`

### **Viewing Live Endpoint Pricing**

All available per-call endpoints and their current pricing are listed in the **Marketplace** under their respective categories.

Each listing shows:

* Endpoint name
* API path
* Cost per call

Because endpoints and pricing may evolve, always refer to the Marketplace for the most up-to-date information.

### **How Per-Call Cost Is Calculated**

`Cost = Number of API calls × Per-call price`

There is no token-based billing for these APIs.

## **Comparing the Two Pricing Models**

| Feature                | LLM Inference                | Per-Call APIs                        |
| ---------------------- | ---------------------------- | ------------------------------------ |
| Billing unit           | Per token                    | Per call                             |
| Input/Output billing   | Yes                          | No                                   |
| Fixed cost per request | No                           | Yes                                  |
| Model-based pricing    | Yes                          | No                                   |
| Endpoint-based pricing | Yes                          | Yes                                  |
| Used for               | Text & multimodal generation | Search, data, financial, social APIs |

## **Usage Tracking & Billing Transparency**

All API usage appears in:

* **Usage Logs**
* Account billing summaries

For LLM requests, logs display:

* Input tokens
* Output tokens
* Applied pricing
* Final cost calculation

For Per-Call APIs, logs reflect:

* Request count
* Per-call pricing
* Final cost

Charges are deducted from your account balance according to the applicable pricing model.

## **Important Notes**

* Pricing is usage-based.
* LLM APIs are billed per token.
* All other APIs are billed per call.
* Pricing may vary by model, provider, group, or endpoint.
* Refer to the Marketplace for live pricing information.
