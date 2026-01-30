# Chat Completions

Create AI-powered chat completions.

## Endpoint

```
POST https://ramclouds.me/v1/chat/completions
```

## Request Body

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `model` | string | Yes | Model ID to use |
| `messages` | array | Yes | Array of message objects |
| `temperature` | number | No | Sampling temperature (0-2). Default: 1 |
| `max_tokens` | integer | No | Maximum tokens to generate |
| `stream` | boolean | No | Enable streaming. Default: false |
| `top_p` | number | No | Nucleus sampling parameter |
| `frequency_penalty` | number | No | Frequency penalty (-2 to 2) |
| `presence_penalty` | number | No | Presence penalty (-2 to 2) |
| `stop` | string/array | No | Stop sequences |

### Message Object

| Field | Type | Description |
|-------|------|-------------|
| `role` | string | `system`, `user`, `assistant` |
| `content` | string | Message content |

## Examples

### Basic Request

```bash
curl https://ramclouds.me/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "model": "gpt-5",
    "messages": [
      {"role": "user", "content": "What is the capital of France?"}
    ]
  }'
```

### With System Message

```bash
curl https://ramclouds.me/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "model": "claude-opus-4-5",
    "messages": [
      {"role": "system", "content": "You are a helpful coding assistant."},
      {"role": "user", "content": "Write a Python function to reverse a string"}
    ]
  }'
```

### Multi-turn Conversation

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://ramclouds.me/v1"
)

response = client.chat.completions.create(
    model="gemini-2.5-pro",
    messages=[
        {"role": "system", "content": "You are a math tutor."},
        {"role": "user", "content": "What is 2 + 2?"},
        {"role": "assistant", "content": "2 + 2 equals 4."},
        {"role": "user", "content": "And if we multiply that by 3?"}
    ]
)

print(response.choices[0].message.content)
```

### Streaming Response

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://ramclouds.me/v1"
)

stream = client.chat.completions.create(
    model="gpt-5",
    messages=[{"role": "user", "content": "Tell me a story"}],
    stream=True
)

for chunk in stream:
    if chunk.choices[0].delta.content:
        print(chunk.choices[0].delta.content, end="")
```

## Response

```json
{
  "id": "chatcmpl-abc123",
  "object": "chat.completion",
  "created": 1706486400,
  "model": "gpt-5",
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "The capital of France is Paris."
      },
      "finish_reason": "stop"
    }
  ],
  "usage": {
    "prompt_tokens": 12,
    "completion_tokens": 8,
    "total_tokens": 20
  }
}
```

## Supported Models

All chat models support this endpoint:

- `gpt-5`, `gpt-5.1`, `gpt-5.2`
- `gpt-5-codex`, `gpt-5-codex-mini`
- `claude-opus-4-5`, `claude-sonnet-4-5`, `claude-haiku-4-5`
- `gemini-2.5-pro`, `gemini-2.5-flash`
- `gemini-3-pro-preview`, `gemini-3-flash-preview`
- `deepseek-v3.1`, `deepseek-v3.2`
- `qwen3-max`, `qwen3-coder-plus`, `qwen3-coder-flash`
- `kimi-k2-thinking`
- `glm-4.6`, `glm-4.7`
- `minimax-m2.1`
