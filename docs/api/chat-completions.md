# Chat Completions

## Endpoint
```
POST https://ramclouds.me/v1/chat/completions
```

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| model | string | Yes | Model ID |
| messages | array | Yes | Messages array |
| temperature | number | No | 0-2, default 1 |
| max_tokens | integer | No | Max output tokens |
| stream | boolean | No | Enable streaming |

## Example

```bash
curl https://ramclouds.me/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "claude-opus-4-5",
    "messages": [
      {"role": "system", "content": "You are helpful."},
      {"role": "user", "content": "Hello!"}
    ]
  }'
```

## Streaming

```python
stream = client.chat.completions.create(
    model="gpt-5",
    messages=[{"role": "user", "content": "Hello"}],
    stream=True
)
for chunk in stream:
    print(chunk.choices[0].delta.content, end="")
```
