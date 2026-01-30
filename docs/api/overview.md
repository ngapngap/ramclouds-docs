# API Overview

Ramclouds API is fully compatible with the OpenAI API format. If you're familiar with OpenAI's API, you can use Ramclouds with minimal changes.

## Base URL

```
https://ramclouds.me/v1
```

## Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/v1/chat/completions` | POST | Create chat completions |
| `/v1/models` | GET | List available models |
| `/v1/images/generations` | POST | Generate images |
| `/v1/embeddings` | POST | Create embeddings |

## Request Format

All requests should:
- Use `Content-Type: application/json`
- Include `Authorization: Bearer YOUR_API_KEY` header
- Send JSON body for POST requests

### Example Request

```bash
curl https://ramclouds.me/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "model": "gpt-5",
    "messages": [
      {"role": "system", "content": "You are a helpful assistant."},
      {"role": "user", "content": "Hello!"}
    ]
  }'
```

## Response Format

Responses follow the OpenAI format:

```json
{
  "id": "chatcmpl-xxx",
  "object": "chat.completion",
  "created": 1234567890,
  "model": "gpt-5",
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "Hello! How can I help you today?"
      },
      "finish_reason": "stop"
    }
  ],
  "usage": {
    "prompt_tokens": 20,
    "completion_tokens": 10,
    "total_tokens": 30
  }
}
```

## Error Handling

Errors return appropriate HTTP status codes with JSON body:

```json
{
  "error": {
    "message": "Invalid API key",
    "type": "authentication_error",
    "code": "invalid_api_key"
  }
}
```

### Common Error Codes

| Status | Description |
|--------|-------------|
| 400 | Bad Request - Invalid parameters |
| 401 | Unauthorized - Invalid API key |
| 403 | Forbidden - Insufficient credits |
| 404 | Not Found - Model not found |
| 429 | Too Many Requests - Rate limited |
| 500 | Server Error |

## Streaming

Enable streaming responses with `stream: true`:

```bash
curl https://ramclouds.me/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "model": "gpt-5",
    "messages": [{"role": "user", "content": "Hello!"}],
    "stream": true
  }'
```

Streaming responses use Server-Sent Events (SSE) format.
