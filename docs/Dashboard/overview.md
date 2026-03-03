---
title: Overview
deprecated: false
hidden: false
metadata:
  robots: index
---
The **Overview** dashboard gives you a consolidated view of your AIsa workspace. It shows your available balance, API activity, resource consumption, and model usage in real time, allowing you to quickly assess whether your integration is working as expected and how your usage is evolving.

<Image align="center" src="https://files.readme.io/182b273da55206380d1aa5bb518f5d3ca44af92142421fc948e65aaf544f0acd-Screenshot_2026-01-29_184007.png" />

<br />

This page is typically the first place to check after setting up an API key, sending test requests, or monitoring ongoing usage in production.

## **Account Data**

The Account Data section reflects the current financial state of your account.

![](https://files.readme.io/553e65150ffdd696f2f3c6ae359093c2c6f23a371427e8e755e9014c8586a4f9-image.png)

**Current Balance** shows the amount of credit available for API usage. New accounts start with **$5.00 in free credits**, which are deducted automatically as requests are processed.

**Used** represents the total amount consumed so far across all API calls.

If your balance runs low, you can add credits using the **Top Up** action. All values update automatically as usage occurs.

## **Usage Statistics**

Usage Statistics provide a quick confirmation that requests are reaching AIsa.

![](https://files.readme.io/a19eb45debbea6919029c5aa387cb17e5dd6471e96fe5889e8046b0e5fedd423-image.png)

**Number of Requests** shows how many API calls have been received within the selected time window.

**Statistical Count** is an internal aggregation metric used for usage tracking and reporting.

Together, these indicators help you verify activity before inspecting detailed request logs.

## **Resource Consumption**

The Resource Consumption panel tracks how much of your account quota is being used.

![](https://files.readme.io/5d30037868eaf02a30fb40fea7d86ead5aa21ac2e830371090c0c8ffd9a95980-image.png)

**Statistical Quota** represents total usage in monetary terms.

**Statistical Tokens** shows the total number of tokens processed across all requests.

When no traffic has been generated, these values remain at zero. As usage grows, this section becomes the primary reference for cost visibility.

## **Performance Indicators**

Performance Indicators describe how your requests are being processed over time.

![](https://files.readme.io/2baef9087cd753f058d613b2da6bfb84af292ec7a066b2ed4e8002ae2ef80f34-image.png)

**Average RPM (Requests Per Minute)** shows the average request throughput.

**Average TPM (Tokens Per Minute)** shows the average token processing rate.

These metrics are useful for understanding traffic patterns and identifying spikes or sustained load.

## **Model Data Analysis**

Model Data Analysis breaks down usage by model.

<Image align="center" src="https://files.readme.io/cffe84fee7911a234c4263227277bfec4ff0e041eca767ab6ca231fe760441c2-image.png" />

The **Consumption Distribution** view visualizes total usage and spend over time, grouped by model, helping you understand which models are driving cost and volume.

Additional views allow you to analyze usage trends, compare call distribution across models, and rank models by activity. These charts populate once sufficient traffic is available.

## **API Information**

The API Information panel displays configuration details related to API access.

If this section shows **No API information**, it usually means no API keys have been created yet or API configuration has not been completed. API keys can be created and managed from the **API Keys** section in the sidebar.

## **System Notice**

System Notice displays platform-level announcements or operational messages relevant to your workspace. If no notices are configured, this section remains empty.

## **Service Status**

Service Status shows uptime and monitoring information for AIsa services associated with your account. If monitoring is not configured, this section will not display any data.
