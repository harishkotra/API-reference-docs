---
title: Cancel batch
excerpt: >-
  Cancels an in-progress batch. The batch will be in status `cancelling` for up
  to 10 minutes, before changing to `cancelled`, where it will have partial
  results (if any) available in the output file.
api:
  file: openai-openapi.json
  operationId: cancelBatch
hidden: false
---