---
title: Use OpenClaw with AIsa.one
excerpt: >-
  This tutorial outlines how you can make AIsa as your default model provider in
  OpenClaw.
deprecated: false
hidden: false
icon: 🦞
metadata:
  robots: index
---
## What is OpenClaw?

[OpenClaw](https://github.com/openclaw/openclaw)  is an open-source AI agent platform that brings conversational AI to multiple messaging channels including Telegram, Discord, Slack, Signal, iMessage, and WhatsApp. It supports multiple LLM providers and allows you to run AI agents that can interact across all these platforms.

## Setup

### Manual Configuration

Because AIsa.one is a custom provider, you must configure it manually in your `openclaw.json`  file.

### Step 1: Get Your AIsa.one API Key

1. Log in to your [AIsa.one dashboard](https://marketplace.aisa.one/?aff=GzQx).
2. Navigate to your [API Keys](https://marketplace.aisa.one/console/token) section.
3. Create a new API key.
4. Copy your key (starts with `sk-...`).

### Step 2: Set Your API Key

Add your AIsa.one API key to your  `~/.openclaw/openclaw.json`  (or set it as an environment variable):

```json
{
  "env": {
    "AISA_API_KEY": "sk-..."
  },
  "models": {
    "mode": "merge",
    "providers": {
      "aisa": {
        "baseUrl": "<https://api.aisa.one/v1>",
        "apiKey": "${AISA_API_KEY}",
        "api": "openai-completions",
        "models": [
          { "id": "gpt-4.1", "name": "GPT 4.1" },
          { "id": "gpt-4.1-mini", "name": "GPT 4.1 Mini" },
          { "id": "claude-3-7-sonnet-20250219", "name": "Claude 3.7 Sonnet" },
          { "id": "gemini-2.5-flash", "name": "Gemini 2.5 Flash" },
          { "id": "deepseek-v3", "name": "DeepSeek V3" },
          { "id": "qwen3-max", "name": "Qwen3 Max" }
          // Add other models here...
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "aisa/gpt-4.1"
      },
      "models": {
        "aisa/gpt-4.1": {}
      }
    }
  }
}
```

Or set it as an environment variable in your shell profile:

```bash
export  AISA_API_KEY="sk-..."
```

That's it! OpenClaw now knows about the `aisa` provider. You configure it in `models.providers` with the Base URL `https://api.aisa.one/v1` and then reference models with the `aisa/` format.

### Step 3: Choose Your Model

Update the  `primary`  model and add it to the  `models`  list. The recommended model for AIsa.one is  `gpt-4.1`.

**AIsa GPT 4.1:**

```json
"model": {
  "primary": "aisa/gpt-4.1"
},
"models": {
  "aisa/gpt-4.1": {}
}
```

### Step 4: Start OpenClaw

After updating your configuration, start or restart OpenClaw:

```bash
openclaw gateway restart
```

Your agents will now use AIsa.one to route requests to your chosen model.

## Model Format

OpenClaw uses the format  `aisa/<model-id>`  for AIsa.one models. For example:

* `aisa/gpt-4.1`

You can use any model ID supported by the AIsa.one API by adding it to the  `models`  array in your `openclaw.json`  configuration.

## Multiple Models with Fallbacks

OpenClaw supports model fallbacks. If the primary model is unavailable, it will try the fallback models in order. You can define multiple models in your AIsa config:

```json
{
  "models": {
    "providers": {
      "aisa": {
        "models": [
          { "id": "gpt-4.1", "name": "GPT 4.1" },
          { "id": "gpt-3.5-turbo", "name": "GPT 3.5 Turbo" }
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "aisa/gpt-4.1",
        "fallbacks": [
          "aisa/gpt-3.5-turbo"
        ]
      },
      "models": {
        "aisa/gpt-4.1": {},
        "aisa/gpt-3.5-turbo": {}
      }
    }
  }
}
```

This provides an additional layer of reliability.

## Using Auth Profiles

For more secure credential management, you can use OpenClaw's auth profiles instead of environment variables.

To manually create an auth profile, add this to your `openclaw.json`:

```json
{
  "auth": {
    "profiles": {
      "aisa:default": {
        "provider": "aisa",
        "mode": "api_key"
      }
    }
  }
}
```

Then use the OpenClaw CLI to set the key in your system keychain:

```bash
openclaw  auth  set  aisa:default  --key  "$AISA_API_KEY"
```

This keeps your API key out of your config file and stores it securely in your system keychain. Then update your provider config to reference the profile:

```json
"providers": {
  "aisa": {
    "apiKey": "auth:aisa:default",
    ...
  }
}
```

## Monitoring Usage

Track your AIsa.one usage in real-time on your AIsa dashboard.

## Common Errors

* "No API key found for provider 'aisa'"

  OpenClaw can't find your AIsa.one API key.

  **Fix:**

  1. Ensure the `AISA_API_KEY` environment variable is set: `echo $AISA_API_KEY`

  2. Check your

     openclaw.json  refers to  `${AISA_API_KEY}`  correctly.

  3. Or hardcode the key (not recommended) to verify.

### Authentication errors (401/403)

* If you see authentication errors:

  **Fix:**

  1. Verify your API key is valid.
  2. Ensure you are using the correct Base URL: `https://api.aisa.one/v1`.
* Model not working

  If a specific model isn't working:

  **Fix:**

  1. Verify the model ID (e.g., `gpt-4.1`) is correct.

  2. Ensure the model is defined in the `models` array in

     openclaw.json.

  3. Use the format `aisa/<model-id>`.

## Advanced Configuration

### Per-Channel Models

Configure different models for different messaging channels:

```json
{
  "telegram": {
    "agents": {
      "defaults": {
        "model": {
          "primary": "aisa/gpt-4.1"
        }
      }
    }
  },
  "discord": {
    "agents": {
      "defaults": {
        "model": {
          "primary": "aisa/gpt-4.1"
        }
      }
    }
  }
}

```

## Resources

* [OpenClaw Documentation](https://docs.openclaw.ai/)