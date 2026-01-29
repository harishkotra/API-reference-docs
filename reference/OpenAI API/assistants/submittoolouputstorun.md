---
title: Submit tool outputs to run
excerpt: >
  When a run has the `status: "requires_action"` and `required_action.type` is
  `submit_tool_outputs`, this endpoint can be used to submit the outputs from
  the tool calls once they're all completed. All outputs must be submitted in a
  single request.
api:
  file: openai-openapi.json
  operationId: submitToolOuputsToRun
hidden: false
---