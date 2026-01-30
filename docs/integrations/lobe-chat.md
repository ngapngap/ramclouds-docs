# Lobe Chat

## Quick Setup

```
https://chat-preview.lobehub.com/?settings={"keyVaults":{"openai":{"apiKey":"YOUR_KEY","baseURL":"https://ramclouds.me/v1"}}}
```

## Manual Setup

1. **Settings** → **Language Model** → **OpenAI**
2. Nhập:
   - API Key: `sk-your-api-key`
   - API Proxy URL: `https://ramclouds.me/v1`
3. Enable "Use custom endpoint"

## Docker

```bash
docker run -d -p 3210:3210 \
  -e OPENAI_API_KEY=sk-your-key \
  -e OPENAI_PROXY_URL=https://ramclouds.me/v1 \
  lobehub/lobe-chat
```
