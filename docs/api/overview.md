# API Overview

## Base URL
```
https://ramclouds.me/v1
```

## Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/v1/chat/completions` | POST | Chat completions |
| `/v1/models` | GET | List models |
| `/v1/embeddings` | POST | Embeddings |

## Request Example

```bash
curl https://ramclouds.me/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-5",
    "messages": [{"role": "user", "content": "Hello!"}]
  }'
```

## Response

```json
{
  "id": "chatcmpl-xxx",
  "model": "gpt-5",
  "choices": [{
    "message": {"role": "assistant", "content": "Hello!"},
    "finish_reason": "stop"
  }],
  "usage": {"prompt_tokens": 10, "completion_tokens": 5, "total_tokens": 15}
}
```

## Errors

| Status | Description |
|--------|-------------|
| 401 | Invalid API key |
| 403 | Insufficient credits |
| 429 | Rate limited |
