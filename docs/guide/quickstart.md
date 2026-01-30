# Quick Start

Get started with Ramclouds API in minutes.

## Prerequisites

- A Ramclouds account ([Sign up here](https://ramclouds.me))
- An API key from your dashboard

## Base URL

```
https://ramclouds.me/v1
```

## Your First API Call

### Using cURL

```bash
curl https://ramclouds.me/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "model": "gpt-5",
    "messages": [
      {"role": "user", "content": "Hello!"}
    ]
  }'
```

### Using Python

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://ramclouds.me/v1"
)

response = client.chat.completions.create(
    model="gpt-5",
    messages=[
        {"role": "user", "content": "Hello!"}
    ]
)

print(response.choices[0].message.content)
```

### Using JavaScript/Node.js

```javascript
import OpenAI from 'openai';

const client = new OpenAI({
  apiKey: 'YOUR_API_KEY',
  baseURL: 'https://ramclouds.me/v1'
});

const response = await client.chat.completions.create({
  model: 'gpt-5',
  messages: [
    { role: 'user', content: 'Hello!' }
  ]
});

console.log(response.choices[0].message.content);
```

## List Available Models

```bash
curl https://ramclouds.me/v1/models \
  -H "Authorization: Bearer YOUR_API_KEY"
```

## Using Different Models

Simply change the `model` parameter to use different AI models:

```python
# Use Claude Opus 4.5
response = client.chat.completions.create(
    model="claude-opus-4-5",
    messages=[{"role": "user", "content": "Hello!"}]
)

# Use Gemini 2.5 Pro
response = client.chat.completions.create(
    model="gemini-2.5-pro",
    messages=[{"role": "user", "content": "Hello!"}]
)

# Use DeepSeek V3.2
response = client.chat.completions.create(
    model="deepseek-v3.2",
    messages=[{"role": "user", "content": "Hello!"}]
)
```

## Next Steps

- [Learn about Authentication](authentication.md)
- [Explore the API Reference](../api/overview.md)
- [Set up Integrations](../integrations/cherry-studio.md)
