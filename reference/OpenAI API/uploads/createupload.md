---
title: Create upload
excerpt: >
  Creates an intermediate
  [Upload](https://platform.openai.com/docs/api-reference/uploads/object) object

  that you can add
  [Parts](https://platform.openai.com/docs/api-reference/uploads/part-object)
  to.

  Currently, an Upload can accept at most 8 GB in total and expires after an

  hour after you create it.


  Once you complete the Upload, we will create a

  [File](https://platform.openai.com/docs/api-reference/files/object) object
  that contains all the parts

  you uploaded. This File is usable in the rest of our platform as a regular

  File object.


  For certain `purpose` values, the correct `mime_type` must be specified. 

  Please refer to documentation for the 

  [supported MIME types for your use
  case](https://platform.openai.com/docs/assistants/tools/file-search#supported-files).


  For guidance on the proper filename extensions for each purpose, please

  follow the documentation on [creating a

  File](https://platform.openai.com/docs/api-reference/files/create).
api:
  file: openai-openapi.json
  operationId: createUpload
hidden: false
---