# Lobe Chat Integration

[Lobe Chat](https://lobehub.com) is an open-source AI chat interface.

## Quick Setup

Click to auto-configure:

```
https://chat-preview.lobehub.com/?settings={"keyVaults":{"openai":{"apiKey":"YOUR_API_KEY","baseURL":"https://ramclouds.me/v1"}}}
```

Replace `YOUR_API_KEY` with your actual API key.

## Manual Setup

### Step 1: Open Settings

1. Go to [Lobe Chat](https://chat-preview.lobehub.com)
2. Click the **Settings** icon (gear)

### Step 2: Configure OpenAI Provider

1. Navigate to **Language Model** > **OpenAI**
2. Enter the following:

| Field | Value |
|-------|-------|
| API Key | Your Ramclouds API key |
| API Proxy URL | `https://ramclouds.me/v1` |

### Step 3: Enable Custom Endpoint

Make sure "Use custom endpoint" is enabled.

### Step 4: Select Model

Choose from available models or add custom ones.

## Self-Hosted Lobe Chat

If you're running Lobe Chat locally or self-hosted:

### Docker

```bash
docker run -d \
  -p 3210:3210 \
  -e OPENAI_API_KEY=YOUR_RAMCLOUDS_KEY \
  -e OPENAI_PROXY_URL=https://ramclouds.me/v1 \
  lobehub/lobe-chat
```

### Environment Variables

```env
OPENAI_API_KEY=sk-your-ramclouds-key
OPENAI_PROXY_URL=https://ramclouds.me/v1
```

## Features with Ramclouds

- Access all 28+ models through Lobe Chat
- Vision capabilities with supported models
- File uploads and analysis
- Streaming responses

## Troubleshooting

### API Key Invalid

- Double-check your API key
- Ensure no extra spaces or characters

### Models Not Loading

- Verify the proxy URL is correct
- Try refreshing the page

### Slow Responses

- Try a faster model like `gemini-2.5-flash`
- Check your network connection
