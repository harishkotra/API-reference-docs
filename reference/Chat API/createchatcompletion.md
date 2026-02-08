---
title: OpenAI Chat
excerpt: >-
  **Starting a new project?** We recommend trying
  [Responses](https://platform.openai.com/docs/api-reference/responses) to take
  advantage of the latest OpenAI platform features. Compare [Chat Completions
  with
  Responses](https://platform.openai.com/docs/guides/responses-vs-chat-completions?api-mode=responses)
api:
  file: openai-chat.json
  operationId: createChatCompletion
hidden: false
---
Creates a model response for the given chat conversation. Learn more in the
[text generation](https://platform.openai.com/docs/guides/text-generation), [vision](https://platform.openai.com/docs/guides/vision),
and [audio](https://platform.openai.com/docs/guides/audio) guides.

Parameter support can differ depending on the model used to generate the
response, particularly for newer reasoning models. Parameters that are only
supported for reasoning models are noted below. For the current state of
unsupported parameters in reasoning models,
[refer to the reasoning guide](https://platform.openai.com/docs/guides/reasoning).