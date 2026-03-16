# Quick Start

## Base URL
```
https://ramclouds.me/v1
```

## Authentication
```
Authorization: Bearer YOUR_API_KEY
```

## Claude `v1/messages` Model ID Note

When using the `v1/messages` endpoint with Claude models, the model ID must use the canonical format **without** the `-CL` suffix.

- Correct (`v1/messages`): `claude-sonnet-4.6`
- Incorrect (`v1/messages`): `claude-sonnet-4.6-CL`

Scope note: this requirement is specific to `v1/messages`. For other endpoints, follow each endpoint's own model-format documentation. In OpenAI-compatible flows, use the model suffix expected by that adapter (for Claude models, typically `-CL`) and do not reuse that suffix on `v1/messages`.

Security note: endpoint/model mismatch is a common source of request failures. Add endpoint-aware input validation so invalid model IDs are rejected before sending requests.

## cURL
```bash
curl https://ramclouds.me/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model": "gpt-5", "messages": [{"role": "user", "content": "Hello!"}]}'
```

## Python
```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://ramclouds.me/v1"
)

response = client.chat.completions.create(
    model="gpt-5",
    messages=[{"role": "user", "content": "Hello!"}]
)
print(response.choices[0].message.content)
```

## Node.js
```javascript
import OpenAI from 'openai';

const client = new OpenAI({
  apiKey: 'YOUR_API_KEY',
  baseURL: 'https://ramclouds.me/v1'
});

const response = await client.chat.completions.create({
  model: 'gpt-5',
  messages: [{ role: 'user', content: 'Hello!' }]
});
console.log(response.choices[0].message.content);
```

## List Models
```bash
curl https://ramclouds.me/v1/models -H "Authorization: Bearer YOUR_API_KEY"
```
