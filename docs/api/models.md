# Models

## Endpoint
```
GET https://ramclouds.me/v1/models
```

## Available Models

### OpenAI
| Model | Description |
|-------|-------------|
| gpt-5 | GPT-5 base |
| gpt-5.1 | GPT-5.1 |
| gpt-5.2 | GPT-5.2 |
| gpt-5-codex | Code optimized |

### Anthropic
| Model | Description |
|-------|-------------|
| claude-opus-4-5 | Most capable |
| claude-sonnet-4-5 | Balanced |
| claude-haiku-4-5 | Fast |

### Google
| Model | Description |
|-------|-------------|
| gemini-2.5-pro | Pro model |
| gemini-2.5-flash | Fast |
| gemini-3-pro-preview | Preview |

### Others
| Model | Description |
|-------|-------------|
| deepseek-v3.2 | DeepSeek |
| qwen3-max | Alibaba Qwen |
| kimi-k2-thinking | Moonshot |
| glm-4.7 | Zhipu |

## Example
```bash
curl https://ramclouds.me/v1/models -H "Authorization: Bearer YOUR_API_KEY"
```
