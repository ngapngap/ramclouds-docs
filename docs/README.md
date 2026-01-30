# Ramclouds API

> Unified AI Gateway - Truy cập 28+ AI models qua một API

## Base URL

```
https://ramclouds.me/v1
```

## Quick Start

```bash
curl https://ramclouds.me/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model": "gpt-5", "messages": [{"role": "user", "content": "Hello!"}]}'
```

## Models

| Provider | Models |
|----------|--------|
| OpenAI | gpt-5, gpt-5.1, gpt-5.2, gpt-5-codex |
| Anthropic | claude-opus-4-5, claude-sonnet-4-5, claude-haiku-4-5 |
| Google | gemini-2.5-pro, gemini-2.5-flash, gemini-3-pro-preview |
| DeepSeek | deepseek-v3.1, deepseek-v3.2 |
| Alibaba | qwen3-max, qwen3-coder-plus |

## Links

- [Quick Start](guide/quickstart.md)
- [API Reference](api/overview.md)
- [IDE Integrations](integrations/ide.md)
- [Telegram Bot](https://t.me/ramclouds_bot)
