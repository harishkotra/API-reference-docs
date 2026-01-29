---
title: Complete upload
excerpt: >
  Completes the
  [Upload](https://platform.openai.com/docs/api-reference/uploads/object). 


  Within the returned Upload object, there is a nested
  [File](https://platform.openai.com/docs/api-reference/files/object) object
  that is ready to use in the rest of the platform.


  You can specify the order of the Parts by passing in an ordered list of the
  Part IDs.


  The number of bytes uploaded upon completion must match the number of bytes
  initially specified when creating the Upload object. No Parts may be added
  after an Upload is completed.
api:
  file: openai-openapi.json
  operationId: completeUpload
hidden: false
---