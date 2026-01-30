# Image Generation

Generate images using AI models.

## Endpoint

```
POST https://ramclouds.me/v1/images/generations
```

## Request Body

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `prompt` | string | Yes | Image description |
| `model` | string | No | Model to use (e.g., `dall-e-3`) |
| `n` | integer | No | Number of images (1-10). Default: 1 |
| `size` | string | No | Image size. Default: `1024x1024` |
| `quality` | string | No | `standard` or `hd` |
| `style` | string | No | `vivid` or `natural` |
| `response_format` | string | No | `url` or `b64_json` |

## Sizes

- `256x256`
- `512x512`
- `1024x1024`
- `1024x1792` (portrait)
- `1792x1024` (landscape)

## Example Request

### cURL

```bash
curl https://ramclouds.me/v1/images/generations \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "model": "dall-e-3",
    "prompt": "A cute robot coding on a laptop",
    "n": 1,
    "size": "1024x1024",
    "quality": "hd"
  }'
```

### Python

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://ramclouds.me/v1"
)

response = client.images.generate(
    model="dall-e-3",
    prompt="A futuristic city with flying cars",
    size="1024x1024",
    quality="hd",
    n=1
)

print(response.data[0].url)
```

### JavaScript

```javascript
import OpenAI from 'openai';

const client = new OpenAI({
  apiKey: 'YOUR_API_KEY',
  baseURL: 'https://ramclouds.me/v1'
});

const response = await client.images.generate({
  model: 'dall-e-3',
  prompt: 'A serene mountain landscape at sunset',
  n: 1,
  size: '1024x1024'
});

console.log(response.data[0].url);
```

## Response

```json
{
  "created": 1706486400,
  "data": [
    {
      "url": "https://...",
      "revised_prompt": "A cute, friendly robot sitting at a modern desk..."
    }
  ]
}
```

## Supported Models

- DALL-E 3
- Midjourney (if available)
- Stable Diffusion (if available)

> **Note**: Image generation model availability may vary. Check `/v1/models` for current availability.
