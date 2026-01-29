---
title: Create transcription session
excerpt: >
  Create an ephemeral API token for use in client-side applications with the

  Realtime API specifically for realtime transcriptions. 

  Can be configured with the same session parameters as the
  `transcription_session.update` client event.


  It responds with a session object, plus a `client_secret` key which contains

  a usable ephemeral API token that can be used to authenticate browser clients

  for the Realtime API.
api:
  file: openai-openapi.json
  operationId: create-realtime-transcription-session
hidden: false
---