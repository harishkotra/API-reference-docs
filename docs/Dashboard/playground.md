---
title: Playground
deprecated: false
hidden: false
metadata:
  robots: index
---
<Image border={false} src="https://files.readme.io/932fbca752907f324939ccc887ca08f92aa69895c5345e61a30455f082ef9c63-image.png" />

<br />

The **Playground** is an interactive environment for testing models available through AIsa before integrating them into your application. It allows you to send requests, adjust model parameters, inspect responses, and validate behavior in real time using the same APIs and configuration that power production requests.

This page is typically used to experiment with different models, tune generation parameters, and verify outputs during development.

## **Model Configuration**

The left panel contains all configuration options that control how requests are sent to the selected model.

<Image align="center" border={false} width="30% " src="https://files.readme.io/23facb9b655990907ef0713813b0ba8c2f787f6615579e51e4720caa66b36d5d-image.png" />

### **Group**

The **Group** selector determines which workspace group the request is associated with. Groups are used to organize usage, permissions, and billing across teams or projects.

If no custom groups are configured, requests are sent under the default group.

### **Model**

The **Model** selector allows you to choose which model will handle the request. This includes models from different providers, all accessed through the same unified API.

Changing the model does not require modifying the request format. Only the model identifier changes.

### **Custom Request Body Mode**

When enabled, **Custom Request Body Mode** allows you to manually define the full JSON request body. This is useful for advanced use cases where you want direct control over parameters not exposed through the UI controls.

When disabled, requests are generated automatically based on the selected parameters.

### **Image URLs**

The **Image URLs** option enables multimodal input by allowing you to attach image URLs to the request. This is used with models that support image understanding or vision-language capabilities.

When enabled, you can provide one or more image URLs that will be included alongside the text prompt.

## **Generation Parameters**

These controls adjust how the model generates responses. Changes take effect immediately for new requests.

### **Temperature**

**Temperature** controls randomness in the model’s output.

Lower values produce more deterministic and focused responses, while higher values increase creativity and variation.

### **Top P**

**Top P** (nucleus sampling) limits token selection to the smallest possible set whose cumulative probability meets the specified threshold. This affects how diverse the model’s vocabulary choices are during generation.

Top P is commonly used instead of temperature, or in combination with lower temperature values.

### **Frequency Penalty**

**Frequency Penalty** reduces the likelihood of repeated words or phrases appearing in the response. Higher values encourage less repetition across the generated output.

### **Presence Penalty**

**Presence Penalty** encourages the model to introduce new concepts rather than continuing existing ones. Increasing this value makes the model more likely to explore new topics in longer responses.

### **Max Tokens**

**Max Tokens** sets the maximum number of tokens the model is allowed to generate in the response. This helps control response length and cost.

If not explicitly set, the model’s default limits apply.

## **Chat Panel**

The main panel on the right is where you interact with the model.

* Enter your prompt in the input field at the bottom
* Submit the request to receive a response from the selected model
* View the generated output in the conversation view

Responses appear exactly as they would when using the API, making this view useful for validating prompt behavior and output quality.

## **Debug Mode**

The **Show debug** option reveals additional request and response details. This includes raw payloads and internal metadata, which can be useful when troubleshooting unexpected behavior or validating request structure.

## **Import and Export**

The Playground supports **Import** and **Export** actions to save or reuse configurations.

* **Export** allows you to download the current configuration and request setup
* **Import** allows you to load a previously saved configuration

This is useful for sharing setups across teams or reusing test scenarios.

## **What the Playground Is Best Used For**

The Playground is intended for:

* Comparing outputs across different models
* Tuning generation parameters before production use
* Testing multimodal inputs
* Debugging prompt behavior
* Validating request configuration without writing code

All requests made in the Playground count toward usage and billing, just like API requests.
