# Models

List and retrieve available AI models.

## List Models

Get a list of all available models.

### Endpoint

```
GET https://ramclouds.me/v1/models
```

### Request

```bash
curl https://ramclouds.me/v1/models \
  -H "Authorization: Bearer YOUR_API_KEY"
```

### Response

```json
{
  "object": "list",
  "data": [
    {
      "id": "gpt-5",
      "object": "model",
      "created": 1626777600,
      "owned_by": "codex",
      "supported_endpoint_types": ["openai"]
    },
    {
      "id": "claude-opus-4-5",
      "object": "model",
      "created": 1626777600,
      "owned_by": "custom",
      "supported_endpoint_types": ["openai"]
    }
  ],
  "success": true
}
```

## Available Models

### OpenAI Models

| Model ID | Description |
|----------|-------------|
| `gpt-5` | GPT-5 base model |
| `gpt-5.1` | GPT-5.1 improved model |
| `gpt-5.2` | GPT-5.2 latest |
| `gpt-5-codex` | GPT-5 optimized for code |
| `gpt-5-codex-mini` | GPT-5 Codex smaller variant |
| `gpt-5.1-codex` | GPT-5.1 code model |
| `gpt-5.1-codex-mini` | GPT-5.1 Codex mini |
| `gpt-5.1-codex-max` | GPT-5.1 Codex max |
| `gpt-5.2-codex` | GPT-5.2 code model |

### Anthropic Models

| Model ID | Description |
|----------|-------------|
| `claude-opus-4-5` | Claude Opus 4.5 - Most capable |
| `claude-sonnet-4-5` | Claude Sonnet 4.5 - Balanced |
| `claude-sonnet-4-5-agentic` | Claude Sonnet for agentic tasks |
| `claude-haiku-4-5` | Claude Haiku 4.5 - Fast & efficient |

### Google Models

| Model ID | Description |
|----------|-------------|
| `gemini-2.5-pro` | Gemini 2.5 Pro |
| `gemini-2.5-flash` | Gemini 2.5 Flash - Fast |
| `gemini-2.5-flash-lite` | Gemini 2.5 Flash Lite |
| `gemini-3-pro-preview` | Gemini 3 Pro Preview |
| `gemini-3-flash-preview` | Gemini 3 Flash Preview |
| `gemini-3-pro-image-preview` | Gemini 3 Pro with image support |

### DeepSeek Models

| Model ID | Description |
|----------|-------------|
| `deepseek-v3.1` | DeepSeek V3.1 |
| `deepseek-v3.2` | DeepSeek V3.2 latest |

### Alibaba Qwen Models

| Model ID | Description |
|----------|-------------|
| `qwen3-max` | Qwen3 Max - Most capable |
| `qwen3-coder-plus` | Qwen3 Coder Plus |
| `qwen3-coder-flash` | Qwen3 Coder Flash - Fast |

### Other Models

| Model ID | Description |
|----------|-------------|
| `kimi-k2-thinking` | Moonshot Kimi K2 with reasoning |
| `glm-4.6` | Zhipu GLM-4.6 |
| `glm-4.7` | Zhipu GLM-4.7 |
| `minimax-m2.1` | MiniMax M2.1 |

## Python Example

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://ramclouds.me/v1"
)

models = client.models.list()

for model in models.data:
    print(model.id)
```

## JavaScript Example

```javascript
import OpenAI from 'openai';

const client = new OpenAI({
  apiKey: 'YOUR_API_KEY',
  baseURL: 'https://ramclouds.me/v1'
});

const models = await client.models.list();
models.data.forEach(model => console.log(model.id));
```
