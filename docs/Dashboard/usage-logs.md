---
title: Usage Logs
deprecated: false
hidden: false
metadata:
  robots: index
---
![](https://files.readme.io/a0a0b58fa4b201ff1d728ba87141458d167e75f05ed3e1de9fa2c4ea26ba352b-image.png)

The Usage Logs page provides detailed records of all API requests made under your account. It allows you to monitor token usage, track spending, inspect request metadata, and review billing calculations.

This page is useful for:

* Monitoring API consumption
* Debugging request behavior
* Auditing token usage
* Verifying billing calculations
* Reviewing per-model spend

## **Overview Metrics**

At the top of the page, summary metrics are displayed for the selected time range.

### **Used Quota**

Shows the total quota consumed during the selected period.

### **RPM**

Requests per minute.

### **TPM**

Tokens per minute.

These metrics help monitor short-term traffic intensity and usage spikes.

## **Filtering and Search**

Usage logs can be filtered to narrow down results.

Available filters include:

* **Date and time range**
* **Group**
* **Token Name**
* **Model Name**

Click **Query** to apply filters and **Reset** to clear them.

Column visibility can be adjusted using **Column settings**.

## **Log Table Columns**

Each row in the table represents a single API request.

### **Time**

The timestamp when the request was processed.

### **Tokens**

Indicates the API key used for the request.

### **Group**

The workspace group associated with the API key.

### **Type**

Indicates the request type.

For example:

**Consume** – A standard API request consuming tokens

### **Model**

The model used to process the request.

### **Time / First Word**

Shows timing information related to the request:

* Total request duration
* Time to first response token (if applicable)
* Indicates whether the response was streamed

### **Input**

Number of input tokens consumed.

### **Output**

Number of output tokens generated.

### **Spend**

The total cost associated with the request.

### **IP**

Displays the source IP address associated with the request (if available).

### **Details**

Shows pricing multipliers or model-related ratios applied to the request.

## **Viewing Log Details**

Click on a log entry to expand detailed information.

The expanded view includes:

### **Model Ratio and Cache Ratio**

Displays model-specific billing multipliers applied to the request.

Example fields may include:

* Model ratio
* Cache ratio
* Completion ratio
* Group ratio

### **Billing Process**

The billing breakdown shows how the cost is calculated.

This includes:

* Input token price per 1M tokens
* Output token price per 1M tokens
* Multipliers applied
* Final calculated spend

The detailed formula is shown for transparency. Actual account deduction reflects the final calculated amount.

### **Request Path**

Displays the internal API route used to process the request.

Example:

`/pg/chat/completions`

This helps identify which endpoint was used.

## **How Billing Is Calculated**

Usage cost is determined based on:

* Number of input tokens
* Number of output tokens
* Per-million token pricing
* Model-specific multipliers
* Group ratios (if applicable)

The breakdown is shown per request for full transparency.

## **Practical Use Cases**

The Usage Logs page is helpful for:

* Verifying token consumption per request
* Tracking which models are being used
* Auditing cost distribution across groups
* Debugging unexpected billing behavior
* Reviewing request latency and streaming performance

## **Notes**

* All Playground requests appear in Usage Logs.
* All API key requests appear in Usage Logs.
* Billing reflected here contributes to account balance deductions.
