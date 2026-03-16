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

## Claude `v1/messages` Model ID Note

When calling the `v1/messages` endpoint with Claude models, use the canonical model ID **without** the `-CL` suffix.

- Correct (`v1/messages`): `claude-sonnet-4.6`
- Incorrect (`v1/messages`): `claude-sonnet-4.6-CL`

Scope note: this rule applies to `v1/messages`. If you use other endpoints, follow the model format documented for those endpoints. In OpenAI-compatible flows, use the model suffix expected by that adapter (for Claude models, typically `-CL`) and do not reuse that suffix on `v1/messages`.

Security note: endpoint/model mismatch can cause request failures and hard-to-debug integration issues. Add endpoint-aware input validation before sending requests.

## Models

| Provider | Models |
|----------|--------|
| OpenAI | gpt-5, gpt-5.1, gpt-5.2, gpt-5-codex |
| Anthropic | claude-opus-4.6, claude-sonnet-4.6, claude-haiku-4.6 |
| Google | gemini-2.5-pro, gemini-2.5-flash, gemini-3-pro-preview |
| DeepSeek | deepseek-v3.1, deepseek-v3.2 |
| Alibaba | qwen3-max, qwen3-coder-plus |

## Links

- [Quick Start](guide/quickstart.md)
- [API Reference](api/overview.md)
- [IDE Integrations](integrations/ide.md)
- [Telegram Bot](https://t.me/ramclouds_bot)
