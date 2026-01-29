---
title: Upload file
excerpt: |
  Upload a file that can be used across various endpoints. Individual files
  can be up to 512 MB, and the size of all files uploaded by one organization
  can be up to 1 TB.

  - The Assistants API supports files up to 2 million tokens and of specific
    file types. See the [Assistants Tools guide](https://platform.openai.com/docs/assistants/tools) for
    details.
  - The Fine-tuning API only supports `.jsonl` files. The input also has
    certain required formats for fine-tuning
    [chat](https://platform.openai.com/docs/api-reference/fine-tuning/chat-input) or
    [completions](https://platform.openai.com/docs/api-reference/fine-tuning/completions-input) models.
  - The Batch API only supports `.jsonl` files up to 200 MB in size. The input
    also has a specific required
    [format](https://platform.openai.com/docs/api-reference/batch/request-input).

  Please [contact us](https://help.openai.com/) if you need to increase these
  storage limits.
api:
  file: openai-openapi.json
  operationId: createFile
hidden: false
---