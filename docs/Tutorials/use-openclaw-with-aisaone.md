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

<Tabs>
  <Tab title="Manual">
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
            "baseUrl": "https://api.aisa.one/v1",
            "apiKey": "${AISA_API_KEY}",
            "api": "openai-completions",
            "models": [
              { "id": "gpt-4.1", "name": "GPT 4.1" },
              { "id": "kimi-k2.5", "name": "Kimi K2.5" },
              { "id": "claude-3-7-sonnet-20250219", "name": "Claude 3.7 Sonnet" },
              { "id": "gemini-2.5-flash", "name": "Gemini 2.5 Flash" },
              { "id": "deepseek-v3", "name": "DeepSeek V3" },
              { "id": "qwen3-max", "name": "Qwen3 Max" }
            ]
          }
        }
      },
      "agents": {
        "defaults": {
          "model": {
            "primary": "aisa/kimi-k2.5"
          },
          "models": {
            "aisa/kimi-k2.5": {}
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

    Update the  `primary`  model and add it to the  `models`  list. Let’s use  `kimi-k2.5` for this setup. You can find all the models supported by [AIsa.one](http://AIsa.one) here: [https://marketplace.aisa.one/pricing](https://marketplace.aisa.one/pricing)

    **AIsa GPT 4.1:**

    ```json
    "model": {
      "primary": "aisa/kimi-k2.5"
    },
    "models": {
      "aisa/kimi-k2.5": {}
    }
    ```

    ### Step 4: Start OpenClaw

    After updating your configuration, start or restart OpenClaw:

    ```bash
    openclaw gateway restart
    ```

    Your agents will now use AIsa.one to route requests to your chosen model.

    ## Model Format

    OpenClaw uses the format  `aisa/<model-id>`  for AIsa.one models. For example:`aisa/kimi-k2.5`

    You can use any model ID supported by the AIsa.one API by adding it to the  `models`  array in your `openclaw.json`  configuration.

    ## Multiple Models with Fallbacks

    OpenClaw supports model fallbacks. If the primary model is unavailable, it will try the fallback models in order. You can define multiple models in your AIsa config:

    ```json
    {
      "models": {
        "providers": {
          "aisa": {
            "models": [
              { "id": "kimi-k2.5", "name": "Kimi K2.5" },
              { "id": "gpt-4.1", "name": "GPT 4.1" },
            ]
          }
        }
      },
      "agents": {
        "defaults": {
          "model": {
            "primary": "aisa/kimi-k2.5",
            "fallbacks": [
              "aisa/gpt-4.1"
            ]
          },
          "models": {
            "aisa/kimi-k2.5": {},
            "aisa/gpt-4.1": {}
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
    openclaw auth set aisa:default --key "$AISA_API_KEY"
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

      2. Check your `openclaw.json`  refers to  `${AISA_API_KEY}`  correctly.

      3. Or hardcode the key (not recommended) to verify.

    ### Authentication errors (401/403)

    * If you see authentication errors:

      **Fix:**

      1. Verify your API key is valid.
      2. Ensure you are using the correct Base URL: `https://api.aisa.one/v1`.
    * Model not working

      If a specific model isn't working:

      **Fix:**

      1. Verify the model ID (e.g., `kimi-k2.5`) is correct.

      2. Ensure the model is defined in the `models` array in `openclaw.json`.

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
              "primary": "aisa/kimi-k2.5"
            }
          }
        }
      },
      "discord": {
        "agents": {
          "defaults": {
            "model": {
              "primary": "aisa/kimi-k2.5"
            }
          }
        }
      }
    }

    ```

    ## Resources

    * [OpenClaw Documentation](https://docs.openclaw.ai/)

    ## Video Tutorial

    <Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=mlSivxqRPTI" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FmlSivxqRPTI%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DmlSivxqRPTI%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FmlSivxqRPTI%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=mlSivxqRPTI" providerUrl="https://www.youtube.com/" providerName="YouTube" />
  </Tab>

  <Tab title="Automatic">
    # Configure OpenClaw with AISA's Unified API

    Use [AISA](https://marketplace.aisa.one/) as your unified LLM backend for [OpenClaw](https://github.com/openclaw/openclaw). One API key gives you access to **50+ models** across 8 providers (OpenAI, Anthropic, Google, DeepSeek, xAI, Moonshot, Alibaba, ByteDance).

    ### Option 1: Fresh Install (No existing models)

    > Please install OpenClaw by running the following command first and skip the model selection:

    ```bash
    curl -fsSL https://openclaw.ai/install.sh | bash
    ```

    Run this single command to set everything up automatically:

    ```bash
    curl -fsSL https://raw.githubusercontent.com/AIsa-team/Configuring-OpenClaw-with-AIsa-API/main/setup-aisa-llm.sh | bash
    ```

    Then just:

    1. Paste your AISA API Key when prompted (get one at [https://marketplace.aisa.one/](https://marketplace.aisa.one/) - new users receive **$5 free credit**)
    2. Press Enter through the prompts to accept defaults

    That's it! Your OpenClaw is now configured with AISA LLM.

    > **Tip:** You can also pass arguments non-interactively:
    >
    > ```bash
    > curl -fsSL https://raw.githubusercontent.com/AIsa-team/Configuring-OpenClaw-with-AIsa-API/main/setup-aisa-llm.sh | bash -s -- --key sk-xxxx --model 1
    > ```
    
    #### Video Tutorial
		<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=LiH1rTO3_ZI" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FLiH1rTO3_ZI%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DLiH1rTO3_ZI%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FLiH1rTO3_ZI%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=LiH1rTO3_ZI" providerUrl="https://www.youtube.com/" providerName="YouTube" />


    ### Option 2: Replace models in an existing OpenClaw bot

    If you already have OpenClaw installed with other model providers, use the built-in guide to switch over. In your OpenClaw session, run:

    ```
    use https://raw.githubusercontent.com/AIsa-team/Configuring-OpenClaw-with-AIsa-API/main/aisa-llm-guide.md to change my llm
    ```

    Then just:

    1. Paste your AISA API Key when prompted (get one at [https://marketplace.aisa.one/](https://marketplace.aisa.one/) - new users receive **$5 free credit**)
    2. Press Enter through the prompts to accept defaults

    OpenClaw's AI assistant will read the guide and walk you through replacing your current model provider with AISA.

    ## Available Models (56 total)

    | Provider  | Count | Featured Models                  |
    | --------- | ----- | -------------------------------- |
    | OpenAI    | 10    | gpt-5, gpt-5.2, gpt-4.1          |
    | Anthropic | 13    | opus-4.6, sonnet-4.5, haiku-4.5  |
    | Google    | 6     | gemini-3-pro, 2.5-pro, 2.5-flash |
    | DeepSeek  | 4     | deepseek-r1, v3.1, v3            |
    | xAI       | 2     | grok-4, grok-3                   |
    | Moonshot  | 2     | kimi-k2.5, kimi-k2-thinking      |
    | Alibaba   | 15    | qwen3-max, qwen3-coder, vl-plus  |
    | ByteDance | 4     | seedream-4-5-251128              |

    ## Switching Models After Setup

    Once configured, switch models in any OpenClaw session:

    ```
    /model aisa/gpt-5
    /model aisa/claude-opus-4-1-20250805
    /model aisa/qwen3-max
    /model aisa/deepseek-r1
    ```
  </Tab>
</Tabs>
